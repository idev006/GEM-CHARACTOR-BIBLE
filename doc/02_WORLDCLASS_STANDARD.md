# CHARACTER BIBLE — WORLD-CLASS STANDARD DEFINITION
# ══════════════════════════════════════════════════════════════════════════
# Document Type : Standard Reference
# Version       : 1.0
# Date          : 2026-05-06
# Purpose       : กำหนดมาตรฐานขั้นต่ำของ Character Bible ระดับ world-class
#                 ใช้เป็น quality bar สำหรับ GEM output validation
# ══════════════════════════════════════════════════════════════════════════

---

## S0 — DEFINITION

**Character Bible ระดับ world-class** คือเอกสารเดียวที่ทำให้ศิลปิน นักแอนิเมต
นักพากย์ หรือ AI model ใด ๆ ทั่วโลก สามารถสร้างตัวละครได้ **ผลลัพธ์เหมือนกัน 100%**
โดยไม่ต้องถามเพิ่ม ไม่ต้องตีความ และไม่มีโอกาสผิดพลาดเรื่องความสม่ำเสมอ

```
BENCHMARK STUDIOS (production standard referenced):
  - Studio Ghibli (Hayao Miyazaki production bible format)
  - Production I.G (Ghost in the Shell / Psycho-Pass character sheets)
  - Trigger (Kill la Kill / Promare design bible)
  - Disney Animation (official character model sheet standard)
  - Pixar (RenderMan-ready character spec)
  - Marvel Studios (Visual Development character packet)
```

---

## S1 — 8 DIMENSION STANDARD

---

### DIMENSION 1 — VISUAL IDENTITY

**Purpose:** ทุกคนสร้างตัวละครหน้าเดียวกันจากทุกมุม

```
MINIMUM (Standard grade):
  □ 1 reference illustration (front only)

GOOD grade:
  □ front + side views
  □ basic color palette

WORLD-CLASS requirements:
  ✅ TURNAROUND SHEET — 5 views mandatory
     → FRONT      : faces viewer, arms at sides, feet together
     → 3/4 FRONT  : 45° right, face toward viewer, weight shifted
     → SIDE L     : pure profile, gaze forward
     → 3/4 BACK   : 45° away, face glances back over shoulder
     → BACK        : fully away, hair/outfit back detail shown
     → ALL: full-body HEAD TO SOLE — zero cropping — feet visible
     → ALL: figure on baseline rule, 85% panel height

  ✅ EXPRESSION SHEET — 6 states minimum
     → NEUTRAL    : baseline resting state
     → HAPPY      : genuine positive affect (Duchenne marker required)
     → FOCUSED    : cognitive engagement
     → CONFIDENT  : assured social state
     → EMPATHETIC : concerned attunement
     → FIRM       : resolved boundary-setting
     → Each state: FACS Action Unit (AU) code notation mandatory
       NOT "happy face" — MUST BE "AU6+AU12 strong, crow's feet"

  ✅ IDENTITY LOCK RULE
     → Same face across ALL 11+ illustration panels
     → Zero face drift, zero outfit variation
     → face_descriptor ≥ 22 anchors in 7 anatomical groups

QUALITY GATE: Can a stranger recreate the exact same face from the descriptor?
```

---

### DIMENSION 2 — TECHNICAL PRECISION

**Purpose:** Zero ambiguity in color, light, and camera — reproducible by machine or human

```
MINIMUM:
  □ "green dress" (descriptive words only)

GOOD:
  □ color swatches (approximate)

WORLD-CLASS:
  ✅ COLOR MODEL (4-tier)
     → FLAT colors    : HEX code per element (#2D6A3F not "dark green")
     → SHADOW colors  : HEX + temperature shift direction
     → HIGHLIGHT colors: HEX + intensity ratio (e.g. 60% opacity overlay)
     → FORBIDDEN colors: explicit colors that create visual conflict
     → COLOR ARC      : 3-stage narrative temperature
                        START (opening/dawn) → MID (mastery/noon) → END (legacy/dusk)
                        Each: HEX + Kelvin + narrative label

  ✅ LIGHTING DNA (7 parameters)
     → KEY   : type (Rembrandt/Fresnel/softbox) + direction + Kelvin + ratio
     → FILL  : key-to-fill ratio + color HEX + Kelvin
     → RIM   : spec + position + intensity
     → SSS   : subsurface scatter color for skin (HEX)
     → SHADOW: hardness (soft/hard) + penumbra angle (degrees)
     → BOUNCE: floor/environment bounce spec
     → AMBIENT: fill color HEX + Kelvin

  ✅ CAMERA SPECIFICATION (6 parameters)
     → focal_length: mm (85mm portrait standard)
     → aperture    : f-stop (f/2.0 subject focus)
     → DOF         : depth of field narrative description
     → framing     : crop type + eye-level/high/low
     → cam_angle   : degrees from neutral
     → distance    : subject distance in meters

QUALITY GATE: Can a cinematographer set up the exact same lighting from this spec?
```

---

### DIMENSION 3 — MATERIAL & COSTUME

**Purpose:** Fabric behaves consistently. Props look identical in every scene.

```
WORLD-CLASS:
  ✅ COSTUME CONSTRUCTION
     → Multi-view: front construction · side · back · detail callouts
     → Layer order: innermost to outermost documented
     → Closure, seam, trim, hem details specified
     → Scale reference: human body proportions noted

  ✅ FABRIC PHYSICS (7 parameters)
     → WEAVE       : fabric structure (plain/twill/satin/brocade)
     → WEIGHT      : light/medium/heavy (gsm if precise)
     → DRAPE       : how fabric falls (structured/fluid/stiff/flowing)
     → SHEEN       : matte/low-satin/satin/metallic
     → WEAR STATE  : new/broken-in/worn/battle-damaged
     → TENSION PTS : where fabric pulls (shoulder seam, waist, elbow)
     → COMPOSITION : fiber content (80% silk, 20% brocade)

  ✅ PROP STUDY (per signature prop)
     → 3 angle views: FRONT · SIDE · BACK
     → Material labels with annotation arrows
     → Scale reference (next to known object)
     → Symbolic meaning statement
     → Detail callout: zoom circle on key feature
     → Carried/worn position on character

  ✅ ACCESSORY HERO
     → Single magnified illustration of primary accessory
     → 3 material annotation arrows minimum
     → Caption: name · material · meaning

QUALITY GATE: Can a costume designer build the outfit without seeing the character?
```

---

### DIMENSION 4 — PSYCHOLOGICAL ARCHITECTURE

**Purpose:** Every design choice has narrative logic. Character is coherent from inside out.

```
WORLD-CLASS:
  ✅ CORE PSYCHOLOGY (6 elements)
     → DESIRES      : deepest want (conscious) — drives behavior toward
     → FEARS        : deepest fear (unconscious) — drives behavior away from
     → WOUND        : formative past injury — 1 sentence, specific event
     → CORE BELIEF  : internal philosophy that drives all decisions
                      ("People who plan ahead show love" not "she's organized")
     → BLIND SPOT   : flaw the character cannot see in themselves
     → DECISION STYLE: how they process choices (systematic/intuitive/emotional/
                        consensus-seeking/avoidant)

  ✅ CHARACTER ARC (3 elements)
     → FROM state : who they are at story opening (specific, not generic)
     → TO state   : who they become at story close (transformation, not just change)
     → THEME      : the arc's thematic meaning in 3–5 words
                    ("fear into legacy" not "grows as a person")

  ✅ RELATIONSHIP MAP
     → Minimum 2 other characters
     → Each: CHAR_ID · relationship type · dynamic (1 sentence that reveals both chars)
     → Dynamic must reveal power/emotional balance between the two

QUALITY GATE: Does the visual design REFLECT the psychology? (not decorative, narrative)
```

---

### DIMENSION 5 — VOICE & SOUND DNA

**Purpose:** Dialogue writer and voice director have zero ambiguity about how this character speaks.

```
WORLD-CLASS:
  ✅ VOICE FINGERPRINT (4 acoustic parameters)
     → PITCH   : range descriptor (medium-low / high / shifting)
     → TEMPO   : pace of speech (steady / variable / rapid / deliberate)
     → TEXTURE : quality (velvety / raspy / crisp / breathy)
     → VOLUME  : default output level + range

  ✅ SPEECH PATTERNS (4 behavioral parameters)
     → HABIT        : physical or vocal tic (breathes before key words / fingers prop)
     → TONE         : emotional default (serious / warm / ironic / earnest)
     → PATTERN      : sentence structure preference (short declarative / extended clause)
     → CATCHPHRASE  : signature phrase that reveals worldview
     → NEVER SAYS   : forbidden vocabulary (reveals character by absence)

  ✅ STATE VOICES (4 emotional variations)
     → HAPPY   : how voice changes when genuinely pleased
     → ANXIOUS : how voice changes under stress (counterintuitive = world-class)
     → FIRM    : how voice changes when setting boundaries
     → COMFORT : how voice changes when soothing someone

  ✅ LEITMOTIF (musical identity)
     → Instrument + mood description + BPM
     → Trigger: specific narrative moment when it plays

QUALITY GATE: Can a voice director audition actors using only this sheet?
```

---

### DIMENSION 6 — BODY LANGUAGE SYSTEM

**Purpose:** Director and animator have exact physical vocabulary for every emotional state.

```
WORLD-CLASS:
  ✅ BEHAVIORAL STATES (6 behavioral modes)
     → RESTING STANCE   : default standing position (measurable, specific)
     → LISTENING        : physical behavior when receiving information
     → THINKING         : physical behavior during internal processing
     → EXPLAINING       : gesture vocabulary when communicating
     → STRESS           : physical tells under pressure
     → WALK             : gait signature (not "walks confidently" — HOW)

  ✅ MICRO-EXPRESSIONS (3 masked states)
     → GENUINE EMOTION  : the tell that escapes before the mask goes up
     → POLITE MASK      : social face (different from genuine)
     → DISAGREEMENT     : physical tell when they disagree but won't say

  ✅ BLOCKING CARD (director's reference — 6 emotional staging positions)
     → DISTRUST  : specific body configuration + distance behavior
     → ANGER     : specific body configuration (often counterintuitive = world-class)
     → JOY       : specific body configuration + weight distribution
     → FEAR      : specific body configuration + spatial behavior
     → THINKING  : specific staging position relative to others
     → HIDING    : how they conceal emotional state physically

QUALITY GATE: Can a stage director block a scene using only this card?
```

---

### DIMENSION 7 — PRODUCTION LOCK

**Purpose:** Artist hired tomorrow can match existing work without briefing.

```
WORLD-CLASS:
  ✅ DO / DON'T REFERENCE TABLE
     → 4 ALWAYS rules : specific visual rules (not generic "stay in character")
     → 4 NEVER rules  : specific errors to avoid
     → Organized: visual face · outfit/prop · body/style · color/light

  ✅ FACS EXPRESSION LOCK TABLE
     → All 6 expression states with AU codes
     → Short descriptor per state
     → Use to generate new expressions consistently

  ✅ LIGHTING LOCK TABLE
     → All 7 lighting parameters (KEY/FILL/RIM/SSS/SHADOW/BOUNCE/AMBIENT)
     → "Apply verbatim to all renders"
     → Deviation = face inconsistency (why: stated explicitly)

  ✅ FOOTER STRIP
     → Char ID · name · role · version
     → Arc summary: FROM → TO
     → Color swatches strip (4 primary flats)

QUALITY GATE: Zero briefing needed for a new team member who reads this document.
```

---

### DIMENSION 8 — DOCUMENT DESIGN

**Purpose:** The physical document itself is production-grade — not a notes file.

```
WORLD-CLASS:
  ✅ FORMAT & RESOLUTION
     → A3 portrait: 297mm × 420mm — aspect ratio 2:3 STRICT
     → Minimum 300 dpi
     → 4K–8K output (min 3508 × 4961 px)
     → Every panel sharp at 100% zoom
     → Every text label legible at 100% zoom

  ✅ LAYOUT ARCHITECTURE (18 zones)
     → PAGE HEADER STRIP         (rows 0–4%)
     → ZONE 1: TURNAROUND        (rows 4–28%)    — 5 panels
     → ZONE 2A: EXPRESSION       (rows 28–50%, L) — 6 panels (3×2)
     → ZONE 2B: PROPS/MATERIAL   (rows 28–50%, R) — 3 sub-zones
     → ZONE 3A: COLOR+LIGHTING   (rows 50–63%, L) — palette + diagram
     → ZONE 3B: CONSTRUCTION+CAM (rows 50–63%, R) — proportion + table
     → ZONE 4A: VOICE DNA        (rows 63–80%, L)
     → ZONE 4B: BODY LANGUAGE    (rows 63–80%, C)
     → ZONE 4C: PSYCHOLOGY+ARC   (rows 63–80%, R)
     → ZONE 4D: LIGHTING LOCK    (rows 80–88%, L)
     → ZONE 4E: FACS SPEC LOCK   (rows 80–88%, R)
     → ZONE 5: DO/DON'T TABLE    (rows 88–95%)
     → PAGE FOOTER STRIP         (rows 95–100%)

  ✅ AESTHETIC STANDARD
     → Background: deep charcoal #0D0D1A throughout
     → Zone borders: white #FFFFFF 0.5pt ruled lines
     → Typography: Helvetica Neue · white
       → Zone headers: BOLD 9pt
       → Data text: REGULAR 7pt
       → Captions: LIGHT 6pt
     → Information density: every centimeter utilized
     → Visual density grade: Ghibli / Production I.G / Trigger studio binders
     → Registration corner crop marks at all 4 corners
     → Studio stamp: lower-right corner

  ✅ VIEWING FORMAT
     → Page viewed top-down orthographic (flat on desk)
     → Zero perspective distortion
     → Photographed straight down — viewer sees the DOCUMENT

QUALITY GATE: Would this page pass QC at Production I.G or Trigger?
```

---

## S2 — QUALITY TIER COMPARISON

```
TIER          SCORE   CHARACTERISTICS
───────────────────────────────────────────────────────────────────
World-Class   8/8     All 8 dimensions complete · Zero ambiguity
                      Any artist anywhere = consistent output
                      Production-ready without briefing

Professional  6/8     Missing psychology depth or body language
                      Requires briefing for new team members
                      Good for small productions

Standard      4/8     Visual identity + basic color only
                      Artist interpretation required
                      Inconsistency risk across scenes

Basic         2/8     Reference image(s) + description
                      High inconsistency risk
                      Not suitable for multi-artist production

Sketch        0-1/8   Rough notes
                      Character will drift between artists
```

---

## S3 — GEM v10.0 TARGET SCORE

```
DIMENSION                   v9.0 CONTENT   v10.0 TARGET
───────────────────────────────────────────────────────
D1: Visual Identity         ✅ complete    ✅ unchanged
D2: Technical Precision     ✅ complete    ✅ unchanged
D3: Material & Costume      ✅ complete    ✅ unchanged
D4: Psychological Arch.     ✅ complete    ✅ expanded defaults
D5: Voice & Sound DNA       ✅ complete    ✅ expanded defaults
D6: Body Language System    ✅ complete    ✅ expanded defaults
D7: Production Lock         ✅ complete    ✅ unchanged
D8: Document Design         ✅ complete    ✅ negative prompt moved

Content Score: 8/8 ✅ (v9.0 content is already world-class)

EXECUTION Score (can GEM actually produce this?):
  v9.0: ❌ GEM generates image instead of text prompt
  v10.0 target: ✅ GEM reliably outputs text prompt

CONCLUSION:
  The CHARACTER BIBLE STANDARD is already world-class in v9.0.
  The problem is not WHAT to produce — the problem is HOW the GEM behaves.
  v10.0 fixes the execution layer only.
```

---

*World-Class Standard Definition v1.0 — REFERENCE DOCUMENT*
*Used for: quality validation of GEM output · acceptance testing · feature scoping*
