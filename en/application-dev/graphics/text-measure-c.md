# Text Measurement (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## Scenario Introduction

Text measurement is the process of evaluating the size and layout of text during graphics drawing, and calculating the space (such as the width, height, and other related information) occupied by the text under a given font and style. Text measurement is used in scenarios such as text typesetting, layout, rendering, and adjustment of the text display position and size, to better control and adjust the layout and presentation of the UI to meet the design expectations.

Currently, the following text measurement capabilities are supported:

- **Text width**: measures the horizontal length of the given text in a specific font, size, and style.

- **Text height**: measures the vertical height of the given text, which usually involves the ascent and descent of the font.

- **Line spacing**: measures the vertical distance between multiple lines of text, which is usually related to the line spacing of the font.

- **Character spacing**: measures the horizontal distance between characters, which is usually related to the glyph and font design.


## Available APIs

The following table lists the APIs commonly used for text measurement. For details about the APIs, see [drawing_text_typography.h](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md).

| Name| Description| 
| -------- | -------- |
| double OH_Drawing_TypographyGetLongestLine(OH_Drawing_Typography\*) | Obtains the width of the longest line. You are advised to round up the returned value.| 
| double OH_Drawing_TypographyGetLongestLineWithIndent(OH_Drawing_Typography\*) | Obtains the width of the longest line (including the width of the current line indentation). You are advised to round up the returned value.| 
| size_t OH_Drawing_TypographyGetLineCount (OH_Drawing_Typography\* ) | Obtains the number of lines.| 
| OH_Drawing_LineMetrics\* OH_Drawing_TypographyGetLineMetrics (OH_Drawing_Typography\* ) | Obtains the measurement information of a paragraph line, including the height, width, and start coordinates of the line.| 
| double OH_Drawing_TextStyleGetLetterSpacing (OH_Drawing_TextStyle \*) | Obtains the letter spacing of a text style.| 


## How to Develop

1. Add the following library to the `src/main/cpp/CMakeLists.txt` file of the project:
   ```c++
   libnative_drawing.so
   ```

2. Import the required header files.

   ```c++
   #include <native_drawing/drawing_font_collection.h>
   #include <native_drawing/drawing_text_declaration.h>
   #include <native_drawing/drawing_text_typography.h>
   ```

3. Create a paragraph generator ParagraphBuilder and set the paragraph style.

   ```c++
   // Create a paragraph style.
   OH_Drawing_TypographyStyle *typoStyle = OH_Drawing_CreateTypographyStyle();
   // Create a paragraph generator.
   OH_Drawing_TypographyCreate *handler = OH_Drawing_CreateTypographyHandler(typoStyle, OH_Drawing_CreateFontCollection());
   // Create a text style and set the font size to 50.
   OH_Drawing_TextStyle *txtStyle = OH_Drawing_CreateTextStyle();
   OH_Drawing_SetTextStyleFontSize(txtStyle, 50);
   OH_Drawing_TypographyHandlerPushTextStyle(handler, txtStyle);
   // Add text to the generator.
   const char *text = "Text measurement information for typesetting";
   OH_Drawing_TypographyHandlerAddText(handler, text);
   // Construct a paragraph through the generator.
   OH_Drawing_Typography *typography = OH_Drawing_CreateTypography(handler);
   ```

4. Call the typesetting API and set the paragraph width.

   ```c++
   // Set the paragraph width to 1000.
   OH_Drawing_TypographyLayout(typography, 1000);
   ```

5. Call the API for obtaining paragraph measurement information to obtain the specified data.

   ```c++
   // Case 1: Obtain the width of the longest line after typesetting.
   double longestLine = OH_Drawing_TypographyGetLongestLine(typography);
   
   // Case 2: Obtain the number of lines in a paragraph after typesetting.
   size_t lineCnt = OH_Drawing_TypographyGetLineCount(typography);
   
   // Case 3: Obtain the measurement information of each line in a paragraph.
   OH_Drawing_LineMetrics* lineMetrics = OH_Drawing_TypographyGetLineMetrics(typography);
   int lineMetricsSize = OH_Drawing_LineMetricsGetSize(lineMetrics);
   for (int i = 0; i < lineMetricsSize; ++i) {
       // lineMetrics is the text measurement information after typesetting.
       double curLineAscender = lineMetrics[i].ascender;
       double curLineWidth = lineMetrics[i].width;
   }
   
   // Case 4: Obtain the width of the longest line with indentation in a paragraph.
   double longestLineWithIndent = OH_Drawing_TypographyGetLongestLineWithIndent(typography);
   ```
