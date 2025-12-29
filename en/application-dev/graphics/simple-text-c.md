# Drawing and Displaying Simple Text (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

## Overview

In a simple user interface, only a few lines of static text need to be displayed, such as the text on a label, button, menu item, or status bar. In this case, you only need to select a proper font, size, and color to complete the rendering.


## Available APIs

| API Definition| Description| 
| -------- | -------- |
| OH_Drawing_TextStyle\* OH_Drawing_CreateTextStyle(void) | Creates an **OH_Drawing_TextStyle** object.| 
| void OH_Drawing_SetTextStyleFontSize(OH_Drawing_TextStyle\* style, double fontSize) | Sets the font size for a text style.| 
| void OH_Drawing_SetTextStyleFontWeight(OH_Drawing_TextStyle\* style, int fontWeight) | Sets the font weight for a text style. Currently, only the default system font supports font weight adjustment. For other fonts, if the weight is less than semi-bold, there is no variation in stroke thickness. If the weight is greater than or equal to semi-bold, it might result in a fake bold effect.| 


## How to Develop

For details about the **Canvas** object, see [Obtaining a Canvas and Displaying Drawing Results](canvas-get-result-draw-c.md).

<!-- @[ndk_drawing_simple_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/NDKGraphics2D/NDKDrawingSimpleText/entry/src/main/cpp/samples/sample_bitmap.cpp) -->

``` C++
// Create a TypographyStyle object, which is required for creating Typography.
OH_Drawing_TypographyStyle *typoStyle = OH_Drawing_CreateTypographyStyle();
// Set the text alignment mode to center.
OH_Drawing_SetTypographyTextAlign(typoStyle, TEXT_ALIGN_CENTER);

// Set the text color, size, and weight. If TextStyle is not set, the default TextStyle in TypographyStyle is used.
OH_Drawing_TextStyle *txtStyle = OH_Drawing_CreateTextStyle();
OH_Drawing_SetTextStyleColor(txtStyle, OH_Drawing_ColorSetArgb(0xFF, 0x00, 0x00, 0x00));
OH_Drawing_SetTextStyleFontSize(txtStyle, 60);
OH_Drawing_SetTextStyleFontWeight(txtStyle, FONT_WEIGHT_400);

// Create a FontCollection object to manage the font matching logic.
OH_Drawing_FontCollection *fc = OH_Drawing_CreateFontCollection();
// Use the FontCollection object and the created TypographyStyle object to create a TypographyCreate object, which is used to create a Typography object.
OH_Drawing_TypographyCreate *handler = OH_Drawing_CreateTypographyHandler(typoStyle, fc);

// Add the created TextStyle object to handler.
OH_Drawing_TypographyHandlerPushTextStyle(handler, txtStyle);
// Add text to handler.
const char *text = "Hello World Drawing\n";
OH_Drawing_TypographyHandlerAddText(handler, text);

OH_Drawing_Typography *typography = OH_Drawing_CreateTypography(handler);
// Set the maximum width.
double maxWidth = width_;
OH_Drawing_TypographyLayout(typography, maxWidth);
// Draw the text on the canvas.
OH_Drawing_TypographyPaint(typography, cCanvas_, 0, 100);

// Release the memory.
OH_Drawing_DestroyTypographyStyle(typoStyle);
OH_Drawing_DestroyTextStyle(txtStyle);
OH_Drawing_DestroyFontCollection(fc);
OH_Drawing_DestroyTypographyHandler(handler);
OH_Drawing_DestroyTypography(typography);
```


## Effect

![image_0000002211443916](figures/image_0000002211443916.png)
