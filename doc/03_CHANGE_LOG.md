# GEM CHARACTER BIBLE — CHANGE LOG & VERSION HISTORY
# ══════════════════════════════════════════════════════════════════════════
# Document Type : Change Log
# Date Created  : 2026-05-06
# ══════════════════════════════════════════════════════════════════════════

---

## VERSION HISTORY

---

### v10.0 — PLANNED (pending implementation)
```
Status   : DESIGN COMPLETE — awaiting implementation approval
Date     : 2026-05-06
Driven by: 04_REQUIREMENTS_v2.md · 01_DESIGN_v10_0.md · 05_DESIGN_ADDENDUM.md

CHANGES FROM v9.0:

  CRITICAL BUG FIXES:
  [NEW] §LOCK  — Absolute Behavior Lock (Layer 0)
                 OUTPUT_TYPE=TEXT · IMAGE_GENERATION=DISABLED · IMAGE_INPUT=READ_ONLY
  [MOD] §0     — Identity strengthened from 3/6 to 6/6 anchors
  [MOD] §1     — IMAGE RECEIVED HANDLER added to MODE A and MODE B
                 IMAGE QUALITY HANDLER added to MODE B (UC-1a/b/c/d)
  [MOD] §5     — CONTENT BLOCK DECLARATION added (namespace isolation)
                 NEGATIVE PROMPT repositioned to before ZONE 1
                 DOCUMENT INTENT DECLARATION reworded
  [MOD] §10    — Image generation prohibition added at top of section

  RELIABILITY IMPROVEMENTS:
  [MOD] §8     — OUTPUT TYPE GUARD check added as first item
  [MOD] §9     — Cross-session limitation warning + restore face lock protocol
  [MOD] §6     — FACE LOCK EXPORT block added to SECTION C

  QUALITY IMPROVEMENTS:
  [MOD] §7     — DEFAULTS expanded: leitmotif · body language · micro-expressions
                 blocking card · psychology · voice state voices · catchphrase
  [NEW] §12    — EXAMPLE OUTPUT (few-shot reference — mini filled sample)

  NEW FEATURES (from addendum 05_DESIGN_ADDENDUM.md):
  [NEW] §13    — VISUAL STYLE LIBRARY (70 styles + English descriptors)
  [MOD] §2     — VISUAL_STYLE parameter added
  [MOD] §5     — Style injection at 3 points (header/identity lock/rendering spec)
  [MOD] §6     — Style field added to SECTION A DNA card
  [MOD] §7     — VISUAL_STYLE default = Ultra Realistic added
  [MOD] §11    — helpme / params / showstyle commands added

  COMMANDS ADDED:
  helpme     → คู่มือการใช้งานครบถ้วน
  params     → parameter reference ทั้งหมด
  showstyle  → รายการ 70 styles พร้อม default indicator

  UNCHANGED:
  §3 §4 §9 — no changes required

ESTIMATED LINES: ~1155 (from 814 in v9.0)
RISK LEVEL     : Low — additive guards + new library, no structural rewrites
LINE BUDGET    : NFR-05 relaxed — Gemini 2.0 handles 128K tokens
```

---

### v9.0 — CURRENT
```
Status   : DEPLOYED (with known bug)
Date     : (prior to 2026-05-06)

KNOWN BUG:
  [BUG-001] GEM generates portrait image instead of text prompt
             when user sends image input (UC-1, UC-2)
  Root cause: §5 template's "Generate a single ultra-high-resolution image"
              interpreted as instruction to GEM itself (namespace collision)
              + missing IMAGE RECEIVED HANDLER in §1
              + §0 "TEXT ONLY" at wrong token position

FEATURES (from v8.0 upgrade):
  [NEW] MODE D  — Update/Revision mode
  [NEW] MODE E  — Multi-character cast sheet
  [NEW] §8      — PRE-FLIGHT CHECKLIST engine
  [NEW] §9      — Face lock protocol
  [NEW] §11     — Quick command reference
  [IMP] face_descriptor — expanded to 22+ anchors (from 20)
  [IMP] zones   — expanded to 18 zones (from 11)
  [IMP] §7      — DEFAULT library added
  [ADD] FACS    — 6-state expression specification
  [ADD] LIGHTING DNA — 7-parameter lighting lock
```

---

### v8.0 — ARCHIVED
```
Status   : SUPERSEDED by v9.0
Changes  : 12 critical fixes + 6 new features (documented in v9.0 header)
```

---

## BUG TRACKER

```
BUG ID   VERSION  STATUS     DESCRIPTION
──────────────────────────────────────────────────────────────────────
BUG-001  v9.0     OPEN       GEM generates portrait instead of text prompt
                              Affected: UC-1 (image only), UC-2 (image+text)
                              Fix: v10.0 §LOCK + §1 handler + §5 + §10
                              Priority: P0 CRITICAL

BUG-002  v9.0     OPEN       Face lock lost when conversation ends
                              Affected: all UCs in new conversation
                              Fix: v10.0 §9 warning + §6 FACE EXPORT
                              Priority: P1 HIGH (known limitation)

BUG-003  v9.0     OPEN       §7 DEFAULTS incomplete — some DERIVE fields have no default
                              Affected: UC-3 with minimal brief
                              Missing: leitmotif · body language · psychology detail
                              Fix: v10.0 §7 expansion
                              Priority: P2 MEDIUM

BUG-004  v9.0     OPEN       No graceful handling for poor image quality (UC-1a/b/c/d)
                              Affected: UC-1 with blurry/partial/multi-person image
                              Fix: v10.0 IMAGE QUALITY HANDLER in §1 MODE B
                              Priority: P2 MEDIUM
```

---

## DESIGN DOCUMENTS INDEX

```
FILE                          PURPOSE                                    STATUS
──────────────────────────────────────────────────────────────────────────────────
doc/readme.txt                Original problem statement                 SOURCE
doc/ANALYSIS_v9_0.md          Bug analysis + initial fix proposals       COMPLETE
doc/00_REQUIREMENTS.md        Requirements v1.0 (superseded)             SUPERSEDED
doc/01_DESIGN_v10_0.md        Technical design — core fixes              COMPLETE
doc/02_WORLDCLASS_STANDARD.md World-class character bible standard        COMPLETE
doc/03_CHANGE_LOG.md          This file — version history                ACTIVE
doc/04_REQUIREMENTS_v2.md     Requirements v2.0 — current APPROVED       APPROVED ✅
doc/05_DESIGN_ADDENDUM.md     Design: style system + commands            COMPLETE ✅
doc/image-style.md            Source: 70 image styles (reference data)   SOURCE
GEM_INSTRUCTION_v9_0.md       Current deployed instruction               DEPLOYED (buggy)
GEM_INSTRUCTION_v10_0.md      Next version — to be created               PENDING APPROVAL
```

---

*Change Log — maintained throughout project lifecycle*
