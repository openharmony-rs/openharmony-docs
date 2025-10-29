# Text Development FAQs

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

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

Take the `"\uffffHello World\uffff"` text as an example. `\uffff` indicates text with an undefined glyph.

The following figures show the comparison.

| Display Optimization Enabled or Not| Effect                                                    |
| ---------------- | ------------------------------------------------------------ |
| Disabled          | ![image_undefined_off_ts](figures/image_undefined_off_ts.png)|
| Enabled            | ![image_undefined_on_ts](figures/image_undefined_on_ts.png)|
