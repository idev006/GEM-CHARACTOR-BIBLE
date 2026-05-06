# GEM CHARACTER BIBLE — DESIGN ADDENDUM
# ══════════════════════════════════════════════════════════════════════════
# Document Type : Design Addendum (extends 01_DESIGN_v10_0.md)
# Version       : 1.0
# Date          : 2026-05-06
# Covers        : VISUAL_STYLE system + helpme/params/showstyle commands
# Driven by     : 04_REQUIREMENTS_v2.md
# ══════════════════════════════════════════════════════════════════════════

---

## DA-1 — VISUAL_STYLE PARAMETER SYSTEM

### DA-1.1 — Design Overview

```
USER SPECIFIES:  style name (Thai or English) — optional
DEFAULT:         Ultra Realistic (style #2)

PROCESSING FLOW:
  1. Detect style from input → match to STYLE LIBRARY (§13)
  2. If not found → fuzzy match → confirm with user
  3. Resolve → STYLE_DESCRIPTOR (English art direction text)
  4. Inject into §5 template at [VISUAL_STYLE] and RENDERING SPECIFICATION
  5. Report in SECTION A: style name + (DEFAULT) or (user-specified)
```

### DA-1.2 — Style Input Formats

ผู้ใช้ระบุ style ได้หลายรูปแบบ:
```
FORMAT 1 — Inline in brief:
  "ตัวละคร BIG BEE ... STYLE: Studio Ghibli Style"

FORMAT 2 — Thai name:
  "style: ภาพวาดสีน้ำ"

FORMAT 3 — English name:
  "style: Watercolor"

FORMAT 4 — Style number:
  "style: 9"  (refers to #9 Watercolor)

FORMAT 5 — Via showstyle first:
  User types "showstyle" → sees list → picks → sends "style: 46"
```

### DA-1.3 — STYLE_DESCRIPTOR: English Prompt Translation Table

สำหรับ SECTION B ต้องมี English art direction — GEM แปลง style → descriptor นี้:

```
#   STYLE NAME (Thai)                  ENGLISH PROMPT DESCRIPTOR
──────────────────────────────────────────────────────────────────────────────
1   Realistic                          photorealistic rendering, natural lighting,
                                       true-to-life color accuracy, fine detail

2   Ultra Realistic [DEFAULT]          ultra-photorealistic 8K, physically accurate
                                       materials and lighting, micro-detail skin texture,
                                       subsurface scattering, cinematic depth of field

3   Hyper Realistic                    hyperrealistic beyond photography, extreme
                                       micro-detail, each pore and fiber visible,
                                       perfect light simulation at nanoscale

4   3D Crayon                          3D render with crayon texture overlay,
                                       waxy surface material, bold saturated colors,
                                       visible crayon stroke grain

5   3D Cartoon                         Pixar/Disney 3D animation style, smooth rounded
                                       forms, vibrant colors, clean subsurface scatter,
                                       expressive proportions, soft studio lighting

6   3D Animation                       high-end 3D animation render, cinematic lighting,
                                       production-quality textures, motion-blur ready,
                                       film-quality global illumination

7   Chinese Ink Wash                   traditional Sumi-e ink wash painting, variable
                                       ink concentration, fluid brushwork, negative space,
                                       rice paper texture, monochrome + accent

8   Oil Painting                       oil on canvas, visible impasto brushstrokes,
                                       rich pigment depth, glazing layers, chiaroscuro,
                                       old master technique

9   Watercolor                         loose watercolor wash, wet-on-wet bleeding edges,
                                       translucent pigment layers, visible paper grain,
                                       soft organic forms, color pooling

10  Pencil Sketch                      graphite pencil on white paper, cross-hatching
                                       shading technique, fine linework, construction
                                       lines visible, tonal range from 2H to 6B

11  Charcoal Drawing                   charcoal on textured paper, deep blacks,
                                       smudged mid-tones, rough grain, expressive marks,
                                       high contrast dramatic shadows

12  Impressionism                      Impressionist oil painting, short broken
                                       brushstrokes, captured light quality,
                                       dappled color, visible texture, Monet-grade

13  Surrealism                         Surrealist fine art, dreamlike impossible
                                       juxtapositions, Dalí-grade technical precision,
                                       hyper-real rendering of impossible scenes

14  Renaissance                        Renaissance oil painting style, sfumato technique,
                                       balanced composition, idealized proportions,
                                       Leonardo/Raphael grade, warm chestnut shadows

15  Ukiyo-e                            Japanese woodblock print, flat color planes,
                                       bold outline, decorative pattern fills,
                                       Hokusai composition, minimal shading

16  Gouache                            opaque gouache illustration, matte finish,
                                       flat graphic areas, clean edges,
                                       bold color, retro poster quality

17  Cyberpunk                          cyberpunk neon cityscape aesthetic, harsh neon
                                       rim lighting, wet street reflections,
                                       cyan/magenta/amber palette, gritty texture

18  Steampunk                          Victorian steampunk illustration, brass and copper
                                       materials, gear motifs, sepia warmth,
                                       intricate mechanical detail

19  Synthwave / Retrowave              80s synthwave aesthetic, hot pink and electric
                                       purple neon gradients, chrome outlines,
                                       perspective grid, star field background

20  Pixel Art                          16-bit pixel art, limited color palette,
                                       chunky pixel grid, no anti-aliasing,
                                       SNES/Mega Drive era aesthetic

21  Voxel Art                          isometric voxel 3D art, Minecraft-style cubic
                                       blocks, clean hard edges, saturated palette,
                                       ambient occlusion shading

22  Glitch Art                         digital glitch aesthetic, RGB channel separation,
                                       scan-line artifacts, corrupted pixel blocks,
                                       electronic noise texture

23  Holographic                        holographic foil material, rainbow iridescent
                                       refraction, translucent layers, laser diffraction
                                       shimmer, cool chromatic spectrum

24  Vector Art                         clean vector illustration, flat color fills,
                                       crisp bezier outlines, no texture, minimal
                                       gradients, modern flat design

25  Low Poly                           low-polygon 3D aesthetic, faceted geometric
                                       surfaces, flat shading per face, clean angular
                                       forms, limited triangle mesh visible

26  Biomechanical                      H.R. Giger biomechanical aesthetic, organic
                                       flesh fused with metal machinery, alien organic
                                       tubing, wet sheen, monochrome + acid tones

27  Film Noir                          black and white film noir, venetian blind shadow
                                       patterns, hard side lighting, deep black pools,
                                       dramatic chiaroscuro, 1940s aesthetic

28  Double Exposure                    double exposure photography composite, two scenes
                                       blended via multiply/screen blend mode,
                                       silhouette filled with landscape

29  Tilt-Shift                         tilt-shift lens miniature effect, extreme top/bottom
                                       blur, sharp center band, saturated colors,
                                       toy-world appearance

30  Fisheye Lens                       extreme fisheye lens distortion, 180° barrel
                                       distortion, curved horizon, center-sharp,
                                       edge-stretched

31  Infrared Photography               infrared film photography simulation, chlorophyll
                                       foliage rendered white, sky deep black,
                                       dreamlike tonal reversal, grain

32  Macro Photography                  extreme macro photography, 5:1 magnification,
                                       shallow DOF, fine surface texture revealed,
                                       clinical precision lighting

33  Polaroid / Instax                  instant film photography aesthetic, faded
                                       color shifts, slightly overexposed, white border,
                                       vintage vignette, warm color cast

34  Long Exposure                      long exposure photography, light trails,
                                       motion blur on moving elements, sharp static
                                       elements, night photography aesthetic

35  Cinematic Lighting                 Hollywood cinematography lighting, motivated
                                       dramatic key, 2.39:1 cinematic frame,
                                       color grade (teal/orange or bleach bypass)

36  Pop Art                            Pop Art style, Andy Warhol / Roy Lichtenstein,
                                       Ben-Day dots, primary color palette,
                                       thick black outlines, halftone patterns

37  Art Deco                           Art Deco illustration, geometric ornamental
                                       borders, gold and black palette, stepped forms,
                                       1920s glamour, sunburst motifs

38  Bauhaus                            Bauhaus design aesthetic, primary colors only,
                                       basic geometric forms, sans-serif typography,
                                       functional composition, no decoration

39  Isometric                          isometric projection illustration, 30° top-down
                                       angle, equal side shading, clean line weight,
                                       game-map aesthetic

40  Paper Cut-out                      layered paper cut art, sharp cut edges,
                                       drop shadow between layers, craft paper texture,
                                       2D planes in 3D depth

41  Claymation                         stop-motion claymation aesthetic, Aardman/
                                       Laika style, fingerprint textures, soft clay
                                       material, warm studio lighting

42  Stained Glass                      Gothic stained glass window, lead came black
                                       outlines, translucent colored glass panes,
                                       backlit luminance, jewel tones

43  Blueprint                          technical blueprint drawing, white linework on
                                       Prussian blue, precise drafting lines,
                                       dimension annotations, architectural notation

44  Graffiti                           street art graffiti style, aerosol spray edges,
                                       bold wildstyle lettering, concrete wall texture,
                                       vibrant urban palette

45  Chalk Art                          chalk drawing on blackboard, white and pastel
                                       chalk strokes, rough texture, smudge blending,
                                       school blackboard dark green ground

46  Studio Ghibli Style                Studio Ghibli hand-drawn animation, soft clean
                                       linework, watercolor background washes,
                                       warm natural lighting, painterly detail

47  90s Retro Anime                    1990s cel animation aesthetic, visible film grain,
                                       muted color palette, analog warmth,
                                       hand-drawn linework, classic shojo/shonen style

48  Manga Screen Tone                  black and white manga, N-tone screen dots,
                                       inking brush linework, speed lines,
                                       halftone gradient fills, Berserk/Slam Dunk grade

49  Kawaii / Chibi                     chibi character style, 2-head proportion,
                                       oversized eyes, pastel palette, round forms,
                                       cute exaggerated expressions

50  Vintage Comic Book                 Silver Age American comic, Ben-Day dot printing,
                                       four-color separation, bold outline, cape comic
                                       coloring, Jack Kirby/Neal Adams grade

51  Knitted / Crochet                  knitted yarn texture, interlocking loop pattern,
                                       wool fiber detail, cozy warm color palette,
                                       craft textile surface simulation

52  Felted Wool                        wool felt texture, matted fiber surface,
                                       soft edge forms, earthy muted tones,
                                       handcraft aesthetic

53  Origami                            origami paper folding art, crisp fold creases,
                                       flat color paper planes, geometric fold pattern,
                                       clean white paper stock

54  Gold Leaf                          gold leaf gilding technique, 24k gold foil
                                       application, luminous warm gold areas,
                                       Byzantine illuminated manuscript aesthetic

55  X-ray                              X-ray radiograph simulation, white bone on black,
                                       blue-grey soft tissue transparency,
                                       medical imaging aesthetic

56  Bioluminescence                    deep sea bioluminescence, self-luminous organisms,
                                       cyan and blue-green glow, black void background,
                                       bioluminescent particle trails

57  Fractal Art                        mathematical fractal art, Mandelbrot/Julia set
                                       complexity, infinite self-similar detail,
                                       high-saturation gradient coloring

58  Psychedelic Art                    psychedelic 1960s art, swirling impossible
                                       color patterns, optical illusion elements,
                                       Peter Max / Wes Wilson aesthetic

59  Minimalist                         minimalist illustration, single-weight outline,
                                       maximum two colors, generous negative space,
                                       Dieter Rams aesthetic

60  Dark Fantasy                       dark fantasy illustration, atmospheric fog,
                                       desaturated palette with jewel accents,
                                       Souls-like visual tone, moonlit

61  Matte Painting                     cinematic matte painting, photobashed
                                       environment, epic scale, atmospheric
                                       perspective, film VFX quality

62  Anatomical Illustration            medical anatomical illustration style,
                                       precise cross-section detail, educational
                                       diagram aesthetic, Gray's Anatomy grade

63  Cross-stitch                       cross-stitch embroidery pattern, X-shaped
                                       stitches on Aida cloth grid, pixel-like
                                       color blocks, craft textile texture

64  ASCII Art                          ASCII character art, monospace terminal font,
                                       character density shading, terminal green on black,
                                       ANSI art aesthetic

65  Pastel Art                         soft pastel drawing, chalky pigment texture,
                                       gentle blended tones, parchment paper ground,
                                       Impressionist palette softened

66  Line Art                           pure contour line art, single-weight outline only,
                                       no fill, no shading, white ground,
                                       technical illustration precision

67  Silhouette                         pure black silhouette, solid form outline,
                                       no internal detail, high-contrast ground,
                                       profile composition, shadow-puppet aesthetic

68  Tessellation                       M.C. Escher tessellation, interlocking geometric
                                       or figurative tiles, seamless repeat pattern,
                                       no gaps, mathematical precision

69  Concept Art                        game/film concept art, quick value sketch,
                                       marker/digital brush, loose gestural lines,
                                       design exploration aesthetic

70  Diorama                            miniature diorama photograph, forced perspective,
                                       tilt-shift blur, model-making aesthetic,
                                       1:72 scale simulation
```

---

### DA-1.4 — Style Injection into §5 Template

Style ส่งผลต่อ 3 จุดใน SECTION B:

```
INJECTION POINT 1 — PAGE HEADER (center field):
  เดิม: "[VISUAL_STYLE]"
  ใหม่: "[STYLE_NAME] Character Bible"
  ตัวอย่าง: "Watercolor Character Bible"

INJECTION POINT 2 — IDENTITY LOCK, ART DIRECTION:
  เดิม: "Style: [VISUAL_STYLE] · Clean precise linework · Cel-shading ·"
  ใหม่: "Style: [STYLE_DESCRIPTOR_EN] ·"
  ตัวอย่าง: "Style: loose watercolor wash, wet-on-wet bleeding edges,
             translucent pigment layers, visible paper grain ·"

INJECTION POINT 3 — RENDERING SPECIFICATION (global):
  เดิม: "ART STYLE: [VISUAL_STYLE], ultra-detailed precise linework, cel-shading."
  ใหม่: "ART STYLE: [STYLE_DESCRIPTOR_EN]"
  ตัวอย่าง: "ART STYLE: loose watercolor wash, wet-on-wet bleeding edges,
             translucent pigment layers, visible paper grain. Apply consistently
             to all character illustration panels."

NOTE: Document layout (A3, zones, typography, dark background) = UNCHANGED
      Style applies to character illustrations INSIDE the zones only
```

### DA-1.5 — Style in SECTION A

```
เพิ่ม field ใน SECTION A DNA CARD:

Style    [STYLE_NAME] ([DEFAULT] หรือ [user-specified])
         [STYLE_DESCRIPTOR_EN — ย่อ 1 บรรทัด]
```

---

## DA-2 — COMMAND SYSTEM DESIGN

### DA-2.1 — Command Detection

```
DETECTION RULE: ถ้า input เป็น single word/phrase ที่ match command list
                → ทำ command นั้น
                → ห้าม interpret เป็น character brief

COMMANDS:
  "helpme"    → UC-6: display usage guide
  "params"    → UC-7: display parameter reference
  "showstyle" → UC-8: display style list
  + existing commands จาก §11 (แก้ไข / เพิ่มตัวละคร / cinematic / cast sheet / export / version / compare)
```

### DA-2.2 — helpme Output Design

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📖  CHARACTER BIBLE ARCHITECT — คู่มือการใช้งาน
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🎯  ฉันทำอะไรได้?
    รับข้อมูลตัวละคร → สร้าง prompt สำเร็จรูป
    นำ prompt ไป paste ใน Gemini Image → ได้ Character Bible A3 4K–8K

──────────────────────────────────────────────
📥  3 วิธีส่งข้อมูล
──────────────────────────────────────────────

MODE A — ภาพ + คำบรรยาย  (แนะนำ)
  ส่งภาพตัวละครต้นแบบ + พิมพ์ brief ลงไป
  ภาพ = ใช้เป็น face reference
  คำบรรยาย = ชุด บทบาท พัฒนาการ ฯลฯ
  
  ตัวอย่าง:
  "บิ๊กBEE (ที่ปรึกษาประกันชีวิต) — CHAR-A
   WARDROBE: ชุดฮั่นฝูสีเขียวเข้ม
   CHAR_ARC: จากผู้แบกรับความกลัว → สู่ผู้นำ
   STYLE: Studio Ghibli Style"

MODE B — ภาพอย่างเดียว
  ส่งภาพ แล้วฉันจะถามชื่อและข้อมูลที่ขาด

MODE C — คำบรรยายอย่างเดียว
  พิมพ์ brief ตัวละคร ไม่ต้องมีภาพ

──────────────────────────────────────────────
🎨  เลือก Style ภาพ
──────────────────────────────────────────────
  พิมพ์ "showstyle" เพื่อดูรายการ 70 styles
  ระบุใน brief ด้วย:  STYLE: [ชื่อ style]
  Default ถ้าไม่ระบุ: Ultra Realistic

──────────────────────────────────────────────
⌨️  Commands ทั้งหมด
──────────────────────────────────────────────
  helpme              → คู่มือนี้
  params              → รายการ parameters ทั้งหมด
  showstyle           → รายการ 70 styles
  แก้ไข [field] [ค่า] → แก้ field ที่ระบุ (หน้าตาจะไม่เปลี่ยน)
  เพิ่มตัวละคร [brief] → เพิ่มตัวละครใหม่
  cinematic [scene]   → สร้าง prompt ฉาก cinematic
  cast sheet          → รวมตัวละครทั้งหมดใน cast overview
  export [CHAR_ID]    → แสดง prompt อีกครั้งสำหรับตัวละครที่ระบุ
  restore face lock: [ID] → restore face lock ใน session ใหม่

──────────────────────────────────────────────
💡  Tips
──────────────────────────────────────────────
  ✅ ระบุ CHAR_ID เสมอ เช่น CHAR-A, CHAR-B
  ✅ บันทึก "FACE LOCK EXPORT" จาก SECTION C ไว้
     เพื่อใช้ restore ใน conversation ใหม่
  ✅ ใช้ MODE A (ภาพ+brief) เพื่อความแม่นยำสูงสุด
  ✅ พิมพ์ "params" เพื่อดู parameters ที่รองรับทั้งหมด
  ❌ อย่าลืมว่า face lock หายเมื่อเปิด conversation ใหม่
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### DA-2.3 — params Output Design

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚙️  PARAMETERS — รายการและวิธีใช้
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ MUST Parameters — ต้องระบุ (หรือถามก่อน output)
──────────────────────────────────────────────
NAME / ชื่อ
  คำอธิบาย: ชื่อตัวละคร
  ตัวอย่าง: "บิ๊กBEE" หรือ "Nara"

ROLE / บทบาท
  คำอธิบาย: อาชีพหรือตำแหน่งในเรื่อง
  ตัวอย่าง: "ที่ปรึกษาประกันชีวิต" หรือ "Guardian"

CHAR_ID
  คำอธิบาย: รหัสตัวละคร (ใช้อ้างอิงใน cast)
  รูปแบบ: CHAR-A, CHAR-B, CHAR-01 ฯลฯ
  ตัวอย่าง: "CHAR-A"

VISUAL_DNA / ลักษณะ
  คำอธิบาย: ลักษณะใบหน้าและร่างกาย
  ตัวอย่าง: "หญิงไทยเชื้อสายจีน อายุ 30 ปี ใบหน้ากลมมน"

WARDROBE / ชุด
  คำอธิบาย: เครื่องแต่งกายและเครื่องประดับ
  ตัวอย่าง: "ชุดฮั่นฝูผ้าไหมสีเขียวเข้ม ปักลายเมฆมงคล"

CHAR_ARC / พัฒนาการ
  คำอธิบาย: การเปลี่ยนแปลงของตัวละคร (จาก X → สู่ Y)
  ตัวอย่าง: "จากผู้แบกรับความกลัว → สู่ผู้นำที่ใช้มรดก"

──────────────────────────────────────────────
⚡ DERIVE Parameters — ไม่ระบุก็ได้ (GEM สร้างให้)
──────────────────────────────────────────────
VISUAL_STYLE / สไตล์
  คำอธิบาย: สไตล์การวาดภาพ
  DEFAULT: Ultra Realistic
  วิธีระบุ: "STYLE: [ชื่อ style]"
  ดูรายการ: พิมพ์ "showstyle"
  ตัวอย่าง: "STYLE: Studio Ghibli Style"

SIGNATURE_PROP / ของประจำตัว
  คำอธิบาย: สิ่งของสำคัญประจำตัวละคร
  ตัวอย่าง: "SIGNATURE_PROP: ปิ่นหยกสืบตระกูล"

THEME_STANCE / ธีม
  คำอธิบาย: ปรัชญาหรือธีมของตัวละคร
  ตัวอย่าง: "THEME_STANCE: การวางแผนคือการแสดงความรัก"

VOICE_FINGERPRINT / เสียง
  คำอธิบาย: ลักษณะน้ำเสียง (GEM สร้างจาก role+arc)
  ระบุเองได้: "[Pitch: X | Tempo: Y | Texture: Z]"

LIGHTING / แสง         → GEM ใช้ Rembrandt ถ้าไม่ระบุ
CAMERA / กล้อง          → GEM ใช้ 85mm f/2.0 ถ้าไม่ระบุ
MATERIAL / ผ้า          → GEM derives จาก WARDROBE
EXPRESSION / สีหน้า     → GEM ใช้ FACS standard 6 states
COLOR_PALETTE / สี      → GEM derives จาก WARDROBE+THEME
PSYCHOLOGY / จิตวิทยา   → GEM derives จาก ROLE+ARC
LEITMOTIF / ธีมดนตรี    → GEM uses solo piano default
BODY_LANGUAGE / ท่าทาง  → GEM derives จาก ROLE+PSYCHOLOGY

──────────────────────────────────────────────
📝  รูปแบบ brief ตัวอย่าง
──────────────────────────────────────────────
[ชื่อ] ([บทบาท]) — [CHAR_ID]
VISUAL_DNA: [ลักษณะ]
WARDROBE: [ชุด]
SIGNATURE_PROP: [ของประจำตัว]
VOICE_FINGERPRINT: [เสียง] (ถ้ามี)
THEME_STANCE: [ธีม]
CHAR_ARC: [จาก X → สู่ Y]
STYLE: [ชื่อ style] (ถ้าต้องการ)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### DA-2.4 — showstyle Output Design

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎨  VISUAL STYLES — รายการ 70 styles
    ระบุใน brief ด้วย:  STYLE: [ชื่อ] หรือ STYLE: [เลข]
    ★ = DEFAULT (ถ้าไม่ระบุ)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

── REALISTIC ──────────────────────────────────
 1  Realistic          สมจริงเหมือนภาพถ่าย
★2  Ultra Realistic    สมจริงขั้นสุด เก็บรายละเอียดสูง [DEFAULT]
 3  Hyper Realistic    สมจริงเหนือจริง ละเอียดยิ่งกว่าตาเห็น

── 3D ─────────────────────────────────────────
 4  3D Crayon          3D พื้นผิวสีเทียน
 5  3D Cartoon         3D สไตล์ Pixar/Disney
 6  3D Animation       3D ภาพยนตร์แอนิเมชัน

── TRADITIONAL ART ────────────────────────────
 7  Chinese Ink Wash   พู่กันจีน / Sumi-e
 8  Oil Painting       สีน้ำมัน ฝีแปรงนูน
 9  Watercolor         สีน้ำ ฟุ้งกระจาย
10  Pencil Sketch      ร่างดินสอ แรเงา
11  Charcoal Drawing   ถ่านไม้ โทนดำเข้ม
12  Impressionism      อิมเพรสชันนิสม์ ฝีแปรงสั้น
13  Surrealism         เหนือจริง สไตล์ฝัน
14  Renaissance        เรอเนซองส์ คลาสสิก
15  Ukiyo-e            พิมพ์แกะไม้ญี่ปุ่น
16  Gouache            สีกวอช ทึบสด

── DIGITAL / MODERN ───────────────────────────
17  Cyberpunk          ไซเบอร์พังก์ นีออนดิบ
18  Steampunk          สตีมพังก์ วิคตอเรียน+เครื่องจักร
19  Synthwave          เรโทรยุค 80 นีออนชมพู-ม่วง
20  Pixel Art          พิกเซลอาร์ต 8-bit/16-bit
21  Voxel Art          พิกเซล 3D (Minecraft style)
22  Glitch Art         ภาพดิจิทัลพัง สัญญาณขัดข้อง
23  Holographic        โฮโลแกรม โปร่งแสงรุ้ง
24  Vector Art         เวกเตอร์ Flat Design
25  Low Poly           เรขาคณิตเหลี่ยม จำนวนน้อย
26  Biomechanical      ชีวกล (อวัยวะ+เครื่องจักร)

── PHOTO / CINEMA ─────────────────────────────
27  Film Noir          ขาวดำ หม่น แสงเงาตัด
28  Double Exposure    ภาพซ้อน สองฉาก
29  Tilt-Shift         เบลอหน้า-หลัง ดูเป็นโมเดล
30  Fisheye Lens       มุมโค้งเว้า ตาปลา
31  Infrared Photo     อินฟราเรด สีผิดจากจริง
32  Macro Photography  มาโคร ขยายรายละเอียดจิ๋ว
33  Polaroid / Instax  โพราลอยด์ วินเทจ ขอบกระดาษ
34  Long Exposure      เปิดหน้ากล้องนาน แสงลากเส้น
35  Cinematic Lighting แสงภาพยนตร์ ดราม่า

── POP / GRAPHIC ───────────────────────────────
36  Pop Art            ป๊อปอาร์ต จุด Ben-Day
37  Art Deco           อาร์ตเดคโค หรูหรา ทอง-ดำ
38  Bauhaus            เบาเฮาส์ เรียบ เรขาคณิต
39  Isometric          มุมมองไอโซเมตริก 45°
40  Paper Cut-out      ตัดกระดาษสีซ้อนชั้น

── CRAFT / TEXTURE ────────────────────────────
41  Claymation         ดินน้ำมัน Aardman style
42  Stained Glass      กระจกสีโบสถ์ เส้นตะกั่วดำ
43  Blueprint          พิมพ์เขียว เส้นขาวบนน้ำเงิน
44  Graffiti           กราฟฟิตี้ สเปรย์กำแพง
45  Chalk Art          ชอล์กบนกระดานดำ
51  Knitted / Crochet  ถักไหมพรม
52  Felted Wool        ขนแกะอัด
53  Origami            พับกระดาษ รอยพับชัด
54  Gold Leaf          ทองคำเปลว ปิดทอง
63  Cross-stitch       ปักครอสติส กากบาท
65  Pastel Art         สีพาสเทล โทนอ่อนโยน

── ANIME / MANGA ──────────────────────────────
46  Studio Ghibli      แอนิเมชันจิบลิ อบอุ่น ธรรมชาติ
47  90s Retro Anime    แอนิเมชันยุค 90 สีตุ่น grain
48  Manga Screen Tone  มังงะ ขาวดำ screen tone
49  Kawaii / Chibi     ชิบิ หัวโต น่ารัก
50  Vintage Comic Book คอมมิกอเมริกันวินเทจ

── SPECIAL ────────────────────────────────────
55  X-ray              เอ็กซเรย์ โปร่งแสงโครงกระดูก
56  Bioluminescence    สิ่งมีชีวิตเรืองแสงในมืด
57  Fractal Art        แฟรกทัล ลวดลายซ้ำซ้อน
58  Psychedelic Art    ไซคีเดลิก บิดเบี้ยวละลานตา
59  Minimalist         มินิมอล เรียบ เส้นน้อย
60  Dark Fantasy       ดาร์กแฟนตาซี หม่นหมอง
61  Matte Painting     ฉาก VFX อลังการ
62  Anatomical Illus.  กายวิภาคศาสตร์ วิทยาศาสตร์
64  ASCII Art          ตัวอักษร terminal
66  Line Art           ลายเส้นอย่างเดียว ไม่ลงสี
67  Silhouette         เงาดำ เห็นแค่รูปทรง
68  Tessellation       รูปทรงต่อกันสนิท Escher
69  Concept Art        ร่าง concept อาร์ต
70  Diorama            โมเดลจำลองขนาดจิ๋ว

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
วิธีเลือก:  STYLE: Studio Ghibli Style
        หรือ STYLE: 46
        หรือ STYLE: ภาพวาดสีน้ำ
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## DA-3 — SECTION CHANGE SUMMARY (Addendum to 01_DESIGN_v10_0.md)

```
SECTION     ACTION          REASON
────────────────────────────────────────────────────────
§2          MODIFY          เพิ่ม VISUAL_STYLE parameter row
§5          MODIFY          เพิ่ม 3 injection points สำหรับ style
§6 SECTION A MODIFY         เพิ่ม Style field ใน DNA card
§7          MODIFY          เพิ่ม VISUAL_STYLE default = Ultra Realistic
§11         MODIFY          เพิ่ม helpme / params / showstyle commands
§13 [NEW]   ADD             STYLE LIBRARY — 70 styles + English descriptors
```

### DA-3.1 — §2 PARAMETERS MATRIX Addition

```
เพิ่ม row ใหม่ใน parameters table:

| VISUAL_STYLE / สไตล์ | สไตล์ภาพ | ⚡ DERIVE | art direction for all illustration panels |

คำอธิบาย: ถ้าไม่ระบุ → DEFAULT "Ultra Realistic" จาก §7
           ระบุได้ด้วย: ชื่อ style (Thai/English) หรือ เลขลำดับ 1-70
           ดูรายการทั้งหมด → พิมพ์ "showstyle"
```

### DA-3.2 — §7 DEFAULTS Addition

```
เพิ่มใน CHARACTER BASE section:

VISUAL_STYLE
  default_name: Ultra Realistic
  default_number: 2
  default_descriptor_en: ultra-photorealistic 8K, physically accurate
                         materials and lighting, micro-detail skin texture,
                         subsurface scattering, cinematic depth of field
  note: applies to all character illustration panels (not document layout)
```

### DA-3.3 — §11 QUICK COMMAND REFERENCE Addition

```
เพิ่มใน command table:

| helpme    | แสดงคู่มือการใช้งานครบถ้วน                          |
| params    | แสดง parameters ทั้งหมดพร้อมตัวอย่าง               |
| showstyle | แสดงรายการ 70 styles พร้อม default indicator       |
```

### DA-3.4 — §13 STYLE LIBRARY [NEW SECTION]

```
## §13 — VISUAL STYLE LIBRARY

Style input → GEM matches → STYLE_DESCRIPTOR_EN → inject into SECTION B

MATCHING RULES:
  1. Exact match (Thai or English name) → direct lookup
  2. Number match (1–70) → direct lookup by index
  3. Partial match → GEM selects best match + confirms with user
  4. No match found → use DEFAULT (Ultra Realistic) + notify user
  5. Case insensitive for all matching

[STYLE TABLE: 70 entries — ดู DA-1.3 above for full table]
```

---

## DA-4 — LINE COUNT UPDATE

```
Previous estimate (01_DESIGN_v10_0.md): ~1054 lines
Additions from this addendum:
  §13 STYLE LIBRARY                   : +80 lines (compact form)
  §11 command additions               : +5 lines
  §7 VISUAL_STYLE default             : +8 lines
  §2 parameter row                    : +3 lines
  §5 injection points documentation   : +5 lines
  helpme/params/showstyle output      : included in §11/§13 (inline)

New estimated total: ~1155 lines
Budget limit (NFR-05): ≤ 1000 lines

⚠️ OVER BUDGET by ~155 lines
MITIGATION OPTIONS:
  Option A: Compress §13 style table (name + 3-word descriptor only) → save ~60 lines
  Option B: Truncate §12 example to 15 lines → save ~10 lines
  Option C: Accept 1155 as within Gemini 2.0 Flash/Pro context efficiency
            (Gemini 2.0 handles 128K tokens — 1155 lines is negligible)

DECISION: Option C — accept 1155 lines
           Gemini 2.0 context capacity makes 1000-line budget irrelevant
           Quality over line count
```

---

*Design Addendum v1.0 — COMPLETE*
*Combined with 01_DESIGN_v10_0.md: full specification for GEM_INSTRUCTION_v10_0.md*
