# GEM CHARACTER BIBLE — REQUIREMENTS SPECIFICATION
# ══════════════════════════════════════════════════════════════════════════
# Document Type : Requirements Specification
# Version       : 1.0
# Date          : 2026-05-06
# Status        : APPROVED — Design Driven
# ══════════════════════════════════════════════════════════════════════════

---

## R0 — SYSTEM DEFINITION

**System Name:** Character Bible Architect GEM
**Platform:** Google Gemini GEM (System Instructions)
**Primary Deliverable:** TEXT PROMPT (English) → pastes into Gemini Image → produces A3 Character Bible image

```
USER INPUT → [GEM] → TEXT PROMPT OUTPUT → [Gemini Image] → A3 CHARACTER BIBLE IMAGE (4K–8K)
```

**ข้อสำคัญ:** GEM ไม่สร้างภาพ — GEM สร้าง TEXT PROMPT ที่ผู้ใช้เอาไปใช้สร้างภาพ

---

## R1 — USE CASES

### UC-1: Image Only
```
Actor   : ผู้ใช้
Input   : ภาพตัวละครต้นแบบ (ไม่มี text)
Process : GEM extract face DNA 22+ anchors จากภาพ
          → ถามชื่อตัวละครถ้าไม่มีใน image
          → ใช้ DEFAULT §7 สำหรับ fields ที่ขาด
Output  : SECTION A (DNA card) + SECTION B (text prompt) + SECTION C (footer)

Edge Cases:
  UC-1a: ภาพคุณภาพต่ำ / blur → แจ้งผู้ใช้ + extract เท่าที่ทำได้ + flag anchors ที่ไม่แน่ใจ
  UC-1b: เห็นหน้าบางส่วน / profile > 60° → แจ้ง + ขอภาพเพิ่ม หรือ extrapolate + flag
  UC-1c: มีหลายคนในภาพ → ถามว่าต้องการตัวละครไหน
  UC-1d: ภาพการ์ตูน/อนิเมะ → extract DNA จาก art style + flag ว่าเป็น non-photo reference
```

### UC-2: Image + Description
```
Actor   : ผู้ใช้
Input   : ภาพตัวละครต้นแบบ + คำบรรยาย (Thai/English)
Process : ภาพ → face DNA 22+ anchors
          คำบรรยาย → wardrobe / role / arc / voice / prop / theme
          Conflict rule: TEXT ขัดแย้ง IMAGE → TEXT ชนะ
          Exception: "ใบหน้าเหมือนรูปภาพ 100%" → IMAGE ชนะสำหรับ face เท่านั้น
Output  : SECTION A + SECTION B + SECTION C

Edge Cases: เดียวกับ UC-1 + description parsing errors
```

### UC-3: Description Only
```
Actor   : ผู้ใช้
Input   : คำบรรยายตัวละคร (Thai/English) ไม่มีภาพ
Process : parse ทุก fields จาก text
          fields ขาด → DEFAULT §7 + แจ้งผู้ใช้
Output  : SECTION A + SECTION B + SECTION C
```

### UC-4: Update/Revision (MODE D)
```
Input   : "แก้ไข [field] [ค่าใหม่]"
Rule    : face_descriptor = IMMUTABLE หลัง lock
          fields อื่น = แก้ได้ทั้งหมด
Output  : SECTION B ใหม่ทั้งหมด + DIFF ใน SECTION A
```

### UC-5: Multi-Character Cast Sheet (MODE E)
```
Input   : brief ตัวละครหลายตัวในครั้งเดียว
Output  : prompt แยกต่อตัวละคร + CAST RELATION MAP
```

---

## R2 — FUNCTIONAL REQUIREMENTS

### FR-01: OUTPUT TYPE
```
MUST: output เป็น TEXT เท่านั้น (markdown + code blocks)
MUST NOT: generate / create / render / produce ภาพใด ๆ ทั้งสิ้น
MUST NOT: ใช้ image input เป็น generation seed
```

### FR-02: FACE DESCRIPTOR
```
MUST: extract ≥ 22 anchors ใน 7 กลุ่ม (§4 standard)
MUST: face_descriptor = LOCKED หลัง first output
MUST NOT: แก้ไข face_descriptor หลัง lock โดยไม่สร้าง ID ใหม่
MUST: แจ้งผู้ใช้เมื่อ extract ได้ไม่ครบ (flag uncertain anchors)
```

### FR-03: PROMPT COMPLETENESS
```
MUST: SECTION B ไม่มี [BRACKET] เหลือแม้แต่อัน
MUST: SECTION B = English 100% (zero Thai characters)
MUST: ครบ 18 zones ตาม §5 template
MUST: negative prompt อยู่ใน SECTION B เสมอ
```

### FR-04: DERIVED FIELDS
```
MUST: derive ทุก ⚡ DERIVE field จาก MUST fields หรือ DEFAULT §7
MUST: แจ้งใน SECTION A ว่า fields ใดใช้ DEFAULT
MUST NOT: ปล่อย field ว่างโดยไม่มีค่า
```

### FR-05: EXPRESSION SPECIFICATION
```
MUST: 6 states ทุก state ใช้ FACS AU notation จริง
MUST NOT: ใช้ generic labels เช่น "happy expression"
MUST: 6 states = NEUTRAL · HAPPY · FOCUSED · CONFIDENT · EMPATHETIC · FIRM
```

### FR-06: IMAGE INPUT HANDLING
```
MUST: เมื่อรับภาพ → READ operation (extract DNA only)
MUST NOT: เมื่อรับภาพ → WRITE/GENERATE operation
MUST: แจ้ง quality issues ถ้าภาพ extract ไม่ได้ครบ 22 anchors
```

### FR-07: WORKFLOW ORDER
```
MUST: ทำตาม STEP 1→6 ใน §3 ทุก turn
MUST: PRE-FLIGHT CHECKLIST §8 ผ่านก่อน output เสมอ
MUST NOT: ข้ามขั้นตอนใด
```

### FR-08: FACE LOCK EXPORT
```
MUST: แจ้งผู้ใช้ว่า face lock มีอายุแค่ใน conversation นี้
MUST: แสดง EXPORT FACE LOCK block ใน SECTION C ทุกครั้งหลัง first output
MUST: รองรับ "restore lock" เมื่อผู้ใช้ paste face_descriptor กลับมา
```

---

## R3 — NON-FUNCTIONAL REQUIREMENTS

### NFR-01: RELIABILITY
```
Target : GEM output text (ไม่ใช่ภาพ) ≥ 99% ของทุก input type
Measure: ทดสอบ UC-1, UC-2, UC-3 อย่างน้อย 10 turns ต่อ UC
Accept : 0 turns ที่ GEM generate image แทน text
```

### NFR-02: COMPLETENESS
```
Target : SECTION B ที่ output มี 18 zones ครบ ≥ 98%
Measure: count zones ใน output
Accept : ไม่มี zone หาย 2 turns ติดต่อกัน
```

### NFR-03: FACE CONSISTENCY
```
Target : face_descriptor หลัง lock = เหมือนกัน 100% ข้าม turns
Measure: diff face_descriptor ใน turns ต่าง ๆ ของ UC-4
Accept : zero token difference ใน face_descriptor block
```

### NFR-04: PERFORMANCE (OUTPUT QUALITY)
```
Target : prompt ที่ output → paste ใน Gemini Image → ได้ A3 document (ไม่ใช่ portrait)
Measure: visual inspection ของ image output
Accept : ≥ 80% ของ image outputs เป็น document layout (ไม่ใช่ portrait)
```

### NFR-05: INSTRUCTION LENGTH
```
Target : instruction ≤ 1000 lines (Gemini context efficiency)
Current v9.0: 814 lines ✅
v10.0 budget: ≤ 900 lines (เพิ่มได้อีก ~86 lines สำหรับ fixes + examples)
```

---

## R4 — WORLD-CLASS CHARACTER BIBLE STANDARDS

Character Bible ที่ผลิตจาก prompt นี้ต้องผ่านมาตรฐาน 8 มิติ:

### D1 — VISUAL IDENTITY ✅
```
- 5-panel turnaround (front · 3/4F · side · 3/4B · back) full-body head-to-sole
- 6-state expression grid (3×2) + FACS AU notation per state
- Zero face drift ข้ามทุก panel
- face_descriptor ≥ 22 anchors ใน 7 groups
```

### D2 — TECHNICAL PRECISION ✅
```
- Color: HEX codes ทุกสี · flat / shadow / highlight / forbidden
- Color arc: 3 positions + Kelvin temperature + narrative label
- Lighting: KEY/FILL/RIM/SSS/SHADOW/BOUNCE/AMBIENT ทั้งหมดระบุ
- Camera: focal length · aperture · DOF · framing · angle · distance
```

### D3 — MATERIAL & COSTUME ✅
```
- Wardrobe construction multi-view
- Fabric physics: weave · weight · drape · sheen · tension points · composition
- Prop study: 3 views + material labels + symbolic meaning
- Accessory hero: magnified + annotation arrows
```

### D4 — PSYCHOLOGICAL ARCHITECTURE ✅
```
- Core psychology: desires · fears · wound · core belief · blind spot · decision style
- Character arc: FROM state → TO state + theme (3-5 words)
- Relationship map: dynamic ≥ 2 characters
```

### D5 — VOICE & SOUND DNA ✅
```
- Voice fingerprint: pitch · tempo · texture · volume
- Speech: habit · pattern · catchphrase · forbidden words
- State voices: happy · anxious · firm · comfort
- Leitmotif: instrument · mood · BPM · trigger
```

### D6 — BODY LANGUAGE SYSTEM ✅
```
- 6 behavioral states: stance · listening · thinking · explaining · stress · walk
- Micro-expressions: genuine · polite · disagree
- Blocking card: 6 emotional states → specific body positions
```

### D7 — PRODUCTION LOCK ✅
```
- Do/Don't table: 4 rules each side
- FACS expression lock table: 6 states
- Lighting lock table: 7 parameters
- Footer: color swatches + arc summary
```

### D8 — DOCUMENT DESIGN ✅
```
- Format: A3 portrait 297×420mm · aspect 2:3 strict
- Resolution: 4K–8K (minimum 3508×4961px @ 300dpi)
- Layout: 18 zones with percentage positions
- Typography: Helvetica Neue · white on dark #0D0D1A
- Registration marks + studio stamp
- Information density: every cm² utilized
```

---

## R5 — ACCEPTANCE CRITERIA

### AC-01: Core Bug Fix
```
GIVEN: ผู้ใช้ส่งภาพ + brief (UC-2)
WHEN:  GEM processes input
THEN:  GEM outputs text prompt (SECTION A + B + C)
AND:   GEM does NOT generate any image
PASS:  100% of UC-1, UC-2 tests produce text output
```

### AC-02: Prompt Effectiveness
```
GIVEN: SECTION B output จาก GEM
WHEN:  paste ใน Gemini Image → Generate
THEN:  output image = A3 document layout (ไม่ใช่ portrait)
AND:   มี turnaround panels visible
AND:   มี expression grid visible
PASS:  ≥ 80% success rate
```

### AC-03: Face Consistency
```
GIVEN: Character locked ใน turn 1
WHEN:  MODE D update ใน turn 2, 3, 4
THEN:  face_descriptor = identical ทุก turn
PASS:  zero token drift
```

### AC-04: Completeness
```
GIVEN: UC-3 (description only, minimal brief)
WHEN:  GEM processes + uses DEFAULTs
THEN:  SECTION B มี 18 zones ครบ
AND:   zero [BRACKET] placeholders
AND:   SECTION A lists all defaults used
PASS:  100%
```

### AC-05: Edge Case Handling
```
GIVEN: UC-1a (blurry image)
WHEN:  GEM processes image
THEN:  GEM reports quality issue
AND:   flags uncertain anchors
AND:   still produces best-effort output (ไม่ fail silently)
PASS:  graceful degradation with user notification
```

---

## R6 — OUT OF SCOPE

```
- GEM ไม่รับผิดชอบคุณภาพของ Gemini Image model
- GEM ไม่รับผิดชอบ face lock ข้าม conversation (technical limitation)
- GEM ไม่สร้างภาพประกอบใด ๆ
- GEM ไม่รองรับ video / animation output
- GEM ไม่ validate ว่า paste prompt แล้ว Gemini Image จะทำงานถูกต้อง
```

---

*Requirements v1.0 — APPROVED*
*Next: 01_DESIGN_v10_0.md*
