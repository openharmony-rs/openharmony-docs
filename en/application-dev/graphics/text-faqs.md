# Text Development FAQs

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

## How Do I Optimize the Display of Characters That Cannot Be Found?

Currently, characters that cannot be found are displayed as blanks by default, which may confuse users.

The system provides a switch. After the switch is turned on, characters that are not found will be displayed as tofu blocks.

- In the ArkTS environment, you can use the setTextUndefinedGlyphDisplay API to enable the function. Characters whose fonts cannot be found are forcibly displayed as tofu blocks.

  ```ts
  import { text } from "@kit.ArkGraphics2D";

  text.setTextUndefinedGlyphDisplay(text.TextUndefinedGlyphDisplay.USE_TOFU);
  ```

  

- In the C/C++ environment, you can use the OH_Drawing_SetTextUndefinedGlyphDisplay API to enable the function. Characters that cannot be found are forcibly displayed as tofu blocks.

  ```c
  #include "drawing/drawing_text_global.h"

  OH_Drawing_SetTextUndefinedGlyphDisplay(TEXT_NO_GLYPH_USE_TOFU);
  ```


The preceding two APIs control the same switch. You can use either of them.

Take the `"\uffffHello World\uffff"` text as an example. `\uffff` indicates a character that cannot be found.

The following figure shows the effect.

| Display Optimization Enabled or Not| Effect                                                    |
| ---------------- | ------------------------------------------------------------ |
| Disabled          | ![image_undefined_off_ts](figures/image_undefined_off_ts.png)|
| Enabled            | ![image_undefined_on_ts](figures/image_undefined_on_ts.png)|
