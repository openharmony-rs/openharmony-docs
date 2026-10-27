# Text Development FAQs

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk-->
<!--Designer: @KejiePeng-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=5284e30f06236fe06b1ce39618ec19c1d67b8d4a translatedAt=2026-10-19T01:34:17.657Z pushedAt=2026-10-19T10:24:01.987Z -->

## How Do I Optimize the Display of Text with an Undefined Glyph?

Currently, the undefined glyphs are displayed as blanks by default, which may confuse users.

The system provides a switch, which can display undefined glyphs as tofu blocks once enabled.

- In ArkTS, you can use the **setTextUndefinedGlyphDisplay** API to enable the display of undefined glyphs as tofu blocks.

  ```ts
  import { text } from "@kit.ArkGraphics2D";

  text.setTextUndefinedGlyphDisplay(text.TextUndefinedGlyphDisplay.USE_TOFU);
  ```

  

- In C/C++, you can use the **OH_Drawing_SetTextUndefinedGlyphDisplay** API to enable the display of undefined glyphs as tofu blocks.

  ```c
  #include "drawing/drawing_text_global.h"

  OH_Drawing_SetTextUndefinedGlyphDisplay(TEXT_NO_GLYPH_USE_TOFU);
  ```


The preceding two APIs control the same switch. You can use either of them.

Take the text `"\uffffHello World\uffff"` as an example, where `\uffff` represents a character with a missing glyph.

The following figures show the comparison.

| Display Optimization Enabled or Not| Effect                                                    |
| ---------------- | ------------------------------------------------------------ |
| Not enabled           | ![undefined-off-ts](figures/undefined-off-ts.png) |
| Enabled             | ![undefined-on-ts](figures/undefined-on-ts.png) |