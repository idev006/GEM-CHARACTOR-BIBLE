# GEM CHARACTER BIBLE — REQUIREMENTS SPECIFICATION
# ══════════════════════════════════════════════════════════════════════════
# Document Type : Requirements Specification
# Version       : 2.0
# Date          : 2026-05-06
# Status        : APPROVED — Design Driven
# Changes from v1.0:
#   + VISUAL_STYLE parameter (70 styles, default=Ultra Realistic)
#   + command: helpme
#   + command: params
#   + command: showstyle
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
          → ใช้ DEFAULT §7 สำหรับ fields ที่ขาด รวมถึง VISUAL_STYLE = "Ultra Realistic"
Output  : SECTION A (DNA card) + SECTION B (text prompt) + SECTION C (footer)
Edge Cases: UC-1a/b/c/d (ดู 00_REQUIREMENTS.md v1.0)
```

### UC-2: Image + Description
```
Input   : ภาพ + คำบรรยาย (Thai/English)
          คำบรรยายอาจระบุ style เช่น "style: Studio Ghibli Style"
Process : ถ้าระบุ style → ใช้ style นั้น
          ถ้าไม่ระบุ → default "Ultra Realistic"
```

### UC-3: Description Only
```
Input   : คำบรรยาย อาจมี / ไม่มี style parameter
Process : ถ้าระบุ style → ใช้ style นั้น
          ถ้าไม่ระบุ → default "Ultra Realistic"
```

### UC-6: helpme Command [NEW]
```
Actor   : ผู้ใช้
Input   : "helpme" (case-insensitive)
Output  : Usage guide ภาษาไทย ครอบคลุม:
          - วิธีใช้งาน (3 input modes)
          - ตัวอย่าง input แต่ละ mode
          - รายการ commands ทั้งหมด
          - tips สำหรับผลลัพธ์ที่ดีที่สุด
          - วิธีระบุ style
          - วิธี restore face lock
```

### UC-7: params Command [NEW]
```
Actor   : ผู้ใช้
Input   : "params" (case-insensitive)
Output  : Parameter reference ภาษาไทย ครอบคลุม:
          - MUST parameters (6 ตัว) พร้อมคำอธิบายและตัวอย่าง
          - DERIVE parameters (8 ตัว) พร้อมคำอธิบาย
          - VISUAL_STYLE parameter (ดู showstyle)
          - รูปแบบการระบุ parameter ใน brief
```

### UC-8: showstyle Command [NEW]
```
Actor   : ผู้ใช้
Input   : "showstyle" (case-insensitive)
Output  : รายการ 70 styles พร้อม:
          - ลำดับและชื่อ style
          - ลักษณะเด่นสั้น ๆ
          - วิธีเลือก style
          - default style ที่ใช้ถ้าไม่ระบุ
```

---

## R2 — FUNCTIONAL REQUIREMENTS

*(รับช่วงต่อจาก v1.0 — เพิ่มเติม)*

### FR-09: VISUAL_STYLE PARAMETER [NEW]
```
MUST: รองรับ VISUAL_STYLE parameter จากรายการ 70 styles (image-style.md)
MUST: default = "Ultra Realistic" ถ้าไม่ระบุ
MUST: แสดงใน SECTION A ว่า style ใดถูกใช้ (DEFAULT หรือ USER-SPECIFIED)
MUST: translate style name → English art direction prompt ใน SECTION B
MUST: style ส่งผลต่อ RENDERING SPECIFICATION และ ART DIRECTION ใน §5 template
MUST NOT: เปลี่ยน document layout หรือ 18 zones เมื่อ style เปลี่ยน
           (layout = คงที่, style = เปลี่ยนวิธีวาดตัวละครในแต่ละ panel เท่านั้น)
```

### FR-10: helpme COMMAND [NEW]
```
TRIGGER: ผู้ใช้พิมพ์ "helpme" (ไม่ case-sensitive)
MUST: output usage guide ทันที ไม่ต้องรอ input อื่น
MUST: ครอบคลุมทุก input mode (A/B/C)
MUST: แสดง command list ทั้งหมด
MUST: แสดงวิธีระบุ style parameter
MUST: แสดงวิธี restore face lock
MUST: เขียนภาษาไทยเป็นหลัก (ศัพท์เทคนิคใช้ English ได้)
```

### FR-11: params COMMAND [NEW]
```
TRIGGER: ผู้ใช้พิมพ์ "params"
MUST: แสดง parameter reference ครบถ้วน
MUST: แยก MUST vs DERIVE parameters ชัดเจน
MUST: มีตัวอย่างการใช้งานต่อ parameter
MUST: ระบุ VISUAL_STYLE parameter และ default value
```

### FR-12: showstyle COMMAND [NEW]
```
TRIGGER: ผู้ใช้พิมพ์ "showstyle"
MUST: แสดงรายการ 70 styles ครบถ้วน
MUST: มีลำดับ + ชื่อ + ลักษณะเด่น
MUST: ระบุ default style (Ultra Realistic = style #2)
MUST: แสดงวิธีเลือก style
```

---

## R3 — NON-FUNCTIONAL REQUIREMENTS (unchanged from v1.0)

*(ดู 00_REQUIREMENTS.md v1.0)*

---

## R4 — WORLD-CLASS CHARACTER BIBLE STANDARDS

### เพิ่มเติม: VISUAL_STYLE dimension
```
Style ที่เลือกต้องส่งผลต่อ output image อย่างสม่ำเสมอทุก panel:
  - ทุก illustration panel ใช้ style เดียวกัน
  - style ไม่ conflict กับ document layout (ยังต้องเป็น A3 document)
  - style เปลี่ยนได้ใน MODE D (ไม่ถือว่าเป็น face descriptor)
```

---

## R5 — ACCEPTANCE CRITERIA (เพิ่มเติม)

### AC-06: VISUAL_STYLE Parameter
```
GIVEN: ผู้ใช้ระบุ "style: Watercolor" ใน brief
WHEN:  GEM processes
THEN:  SECTION B มี watercolor art direction keywords
AND:   SECTION A แสดง style = "Watercolor (user-specified)"
PASS:  style keyword ปรากฏใน RENDERING SPECIFICATION

GIVEN: ผู้ใช้ไม่ระบุ style
WHEN:  GEM processes
THEN:  SECTION A แสดง style = "Ultra Realistic (DEFAULT)"
AND:   SECTION B มี ultra-realistic art direction
PASS:  default correctly applied
```

### AC-07: Commands
```
GIVEN: ผู้ใช้พิมพ์ "helpme"
THEN:  output usage guide (not DNA card / not prompt)
PASS:  guide ครอบคลุม input modes + commands + style usage

GIVEN: ผู้ใช้พิมพ์ "params"
THEN:  output parameter reference
PASS:  แสดง MUST + DERIVE + VISUAL_STYLE ครบ

GIVEN: ผู้ใช้พิมพ์ "showstyle"
THEN:  output style list
PASS:  70 styles แสดงครบพร้อม default indicator
```

---

*Requirements v2.0 — APPROVED*
*Next: 05_DESIGN_v10_0_ADDENDUM.md (design for new requirements)*
