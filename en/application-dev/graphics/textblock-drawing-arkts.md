# Drawing TextBlobs (ArkTS)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

A TextBlob is a set of texts. You can draw a single text or a large text block by using text blobs.

In addition to basic text blob drawing, you can also add various drawing effects to texts. Common text blob drawing scenarios include text stroke (see #Text Stroke) and text gradient (see #Text Gradient). For more effects, see Drawing Effects (drawing-effect-overview.md).

This section does not involve text measurement and layout. For details about how to handle text drawing requirements during development, see Text Development Overview (text-overview.md). This document describes the layout policies and usage guide.

## Basic Text Blob Drawing

Canvas draws text blobs by using drawTextBlob(). The function accepts three parameters: text blob object, and the x and y coordinates of the left end of the text baseline.

For details about the canvas object, see Obtaining a Canvas and Displaying the Drawing Result (ArkTS) (canvas-get-result-draw-arkts.md).

A text blob object can be created in multiple ways. For details about how to create a text blob and use APIs, see [TextBlob](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-TextBlob.md).

The following uses the makeFromString() API as an example to create a text blob. The API accepts three parameters:

- text: character string to be displayed.

- font: font object. font is used to set and obtain various attributes of a font, such as the font size, text style, font alignment mode, font rendering mode, and font stroke mode. For details about the API, see [Font](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md).

- textEncoding: text encoding mode. Currently, the following text encoding modes are supported:
  - TEXT_ENCODING_UTF8: UTF-8 or ASCII is represented by one byte.
  - TEXT_ENCODING_UTF16: uses two bytes to represent most Unicode characters.
  - TEXT_ENCODING_UTF32: uses four bytes to represent all Unicode characters.
  - TEXT_ENCODING_GLYPH_ID: uses two bytes to represent glyph indexes.

The sample code and effect of the basic text drawing are as follows:

<!-- @[arkts_graphics_draw_base_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// Create a font object.
const font = new drawing.Font();
// Set the font size.
font.setSize(100);
// Create a text block object.
const textBlob = drawing.TextBlob.makeFromString('Hello world', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// Draw the text block.
canvas.drawTextBlob(textBlob, VALUE_200, VALUE_300);
```

![Screenshot_20241225151030139](figures/Screenshot_20241225151030139.jpg)

## Text Outline

You can also use a paint object to draw text outlines. For details about the outline effect, please refer to basic-drawing-effect-arkts.md# Outline Effect.

The following provides an example of drawing English and Chinese text outlines.

### English Text Outline

The following figure shows how to draw an English text outline.

<!-- @[arkts_graphics_draw_stroke_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// Create a pen.
let pen = new drawing.Pen();
// Set anti-aliasing.
pen.setAntiAlias(true);
// Set the outline width.
pen.setStrokeWidth(3.0);
// Set the outline color.
pen.setColor(0xFF, 0xFF, 0x00, 0x00);
// Create a font object.
const font = new drawing.Font();
// Set the font size.
font.setSize(100);
// Add the stroke effect.
canvas.attachPen(pen);
// Create a text block object.
const textBlob = drawing.TextBlob.makeFromString('Hello world', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// Draw the text block.
canvas.drawTextBlob(textBlob, VALUE_200, VALUE_300);
// Remove the stroke effect.
canvas.detachPen();
```

![Screenshot_20241225152446749](figures/Screenshot_20241225152446749.jpg)

### Stroke for Chinese Text

You need to first add the stroke effect using a paint brush, and then call the brush to fill the internal color to remove the impurities and overlapping parts in the middle of the font to implement the stroke effect for Chinese text.

The following figure shows a brief example of the stroke effect for Chinese text.

<!-- @[arkts_graphics_draw_chinese_stroke_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript

// Create a brush.
let brush = new drawing.Brush();
// Create a pen.
let pen = new drawing.Pen();
// Set anti-aliasing.
brush.setAntiAlias(true);
// Set the stroke color.
brush.setColor(0xFF, 0xFF, 0xFF, 0xFF);

pen.setAntiAlias(true);
// Set the outline width.
pen.setStrokeWidth(3.0);
// Set the outline color.
pen.setColor(0xFF, 0xFF, 0x00, 0x00);

// Create a font object.
const font = new drawing.Font();
// Set the font size.
font.setSize(100);
// Add the stroke effect.
canvas.attachPen(pen);
// Create a text block object.
const textBlob = drawing.TextBlob.makeFromString(STROKE_SAMPLE, font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// Draw the text block.
canvas.drawTextBlob(textBlob, VALUE_200,  VALUE_300);
// Remove the stroke effect.
canvas.detachPen(); 

canvas.attachBrush(brush);
canvas.drawTextBlob(textBlob, VALUE_200, VALUE_300);
canvas.detachBrush();
```

![chinese_stroke_text_ark](figures/chinese_stroke_text_ark.png)

## Text Gradient

You can also use a shader to implement the text gradient effect based on basic text blocks. For details about shaders, please refer to complex-drawing-effect-arkts.md# Shader Effects.

The following is a brief example of adding a linear gradient shader effect to text.

<!-- @[arkts_graphics_draw_gradient_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
let startPt: common2D.Point = { x: VALUE_100, y: VALUE_100 };
let endPt: common2D.Point = { x: VALUE_900, y: VALUE_900 };
let colors = [0xFFFFFF00, 0xFFFF0000, 0xFF0000FF];
// Create a linear gradient shader.
let shaderEffect = drawing.ShaderEffect.createLinearGradient(startPt, endPt, colors, drawing.TileMode.CLAMP);
// Create a brush.
let brush = new drawing.Brush();
// Set the shader.
brush.setShaderEffect(shaderEffect);
// Add the brush fill effect.
canvas.attachBrush(brush);
// Create a font.
const font = new drawing.Font();
// Set the font size.
font.setSize(VALUE_200);
// Create a text block.
const textBlob = drawing.TextBlob.makeFromString('Hello world', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// Draw the text block.
canvas.drawTextBlob(textBlob, VALUE_100, VALUE_300);
// Remove the fill effect.
canvas.detachBrush();
```

![Screenshot_20241225155707415](figures/Screenshot_20241225155707415.jpg)

## Theme font

Theme fonts are special custom fonts that can be used in **theme applications**. For details about text measurement and layout, see Using Theme Fonts (ArkTS).

The following shows sample code and the effect of setting theme fonts:

<!-- @[arkts_graphics_draw_theme_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// Create a linear gradient shader.
const font = new drawing.Font();
// Set the font size.
font.setSize(100);
// Set the theme font.
font.setThemeFontFollowed(true);
// Create a text block object.
const textBlob = drawing.TextBlob.makeFromString('Hello World', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
// Draw the text block.
canvas.drawTextBlob(textBlob, VALUE_200, VALUE_300);
```

| Effect of not following the theme font| Effect of following the theme font (The effect varies according to the theme font.)|
| -------- | -------- |
| ![Snapshot_setThemeFontFollowed_sys](figures/Snapshot_setThemeFontFollowed_sys.jpg) | ![Snapshot_setThemeFontFollowed](figures/Snapshot_setThemeFontFollowed.jpg) |

> **Description**
>
> You need to override the onConfigurationUpdate function in the application entry file (EntryAbility.ets in the default project) to respond to the theme font switching operation. This ensures that the page can be refreshed and take effect in a timely manner after the switching. For details, see Using Theme Fonts (ArkTS).

## Single Character Drawing

Single character drawing is a refined control technology for text rendering in graphics rendering. Compared with text block drawing, the core advantage of single character drawing is that the font degradation mechanism can be used. When a character cannot be displayed in the current font, the character is automatically degraded to the system font, improving the compatibility with special characters and avoiding character loss. In addition, single character drawing supports character-by-character configuration of font features (such as ligatures and alternative glyphs) to meet complex typesetting requirements and enhance user experience. For details about the APIs, please refer to [drawing.Canvas](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Canvas.md#drawsinglecharacter12).

Basic Scenario: Drawing Characters Without Font Features 
In the scenario where you need to render regular text without font features, you can use drawSingleCharacter to draw a single character and measureSingleCharacter to measure the width of a single character. The sample code and effect are as follows:

<!-- @[arkts_graphics_draw_single_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// Create a font object.
const font = new drawing.Font();
// Set the font size.
font.setSize(100);
let startX = 100;
let startY = 100;
let text = ['H', 'e', 'l', 'l', 'o'];
for (let s of text) {
  // Draw a single character.
  canvas.drawSingleCharacter(s, font, startX, startY);
  // Measure the width of a single character.
  let textWidth = font.measureSingleCharacter(s);
  startX += textWidth;
}
```

![Snapshot_drawSingleCharacter](figures/Snapshot_drawSingleCharacter.jpg)

Advanced Scenario: Drawing Characters with Font Features 
In the scenario where you need to render text with font features, you can use drawSingleCharacterWithFeatures to draw a single character and measureSingleCharacterWithFeatures to measure the width of a single character. The sample code and effect are as follows:

<!-- @[arkts_graphics_draw_feature_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/TextBlockDrawing.ets) -->

``` TypeScript
// Create a font object.
const font = new drawing.Font();
// Set the font size.
font.setSize(100);
let startX = 100;
let startY = 100;
let text = ['a', '2', '+', 'b', '2'];
// Create an array of font feature objects.
let fontFeatures: drawing.FontFeature[] = [{name: 'frac', value: 1}];
for (let s of text) {
  // Draw a single character.
  canvas.drawSingleCharacterWithFeatures(s, font, startX, startY, fontFeatures);
  // Measure the width of a single character.
  let textWidth = font.measureSingleCharacterWithFeatures(s, fontFeatures);
  startX += textWidth;
}
```

![Snapshot_drawSingleCharacter](figures/Snapshot_drawSingleCharacterWithFeatures.png)

> **Description**
>
> If `drawSingleCharacterWithFeatures` and `measureSingleCharacter` are used together, or `drawSingleCharacter` and `measureSingleCharacterWithFeatures` are used together, the font drawing may overlap.

<!--RP1-->
## Samples

The following figures show how to develop Drawing (ArkTS).

- [ArkTSGraphicsDraw (API20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/ArkTSGraphicsDraw)
<!--RP1End-->
