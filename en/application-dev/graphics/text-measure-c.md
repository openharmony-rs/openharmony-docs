# Text Measurement (C/C++)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## Overview

Text measurement refers to the process of evaluating the size and layout of text and calculating the space (such as the width, height, and other related information) occupied by the text in a given font and style during graphics drawing. Text measurement helps manage typography, layout, rendering, and adjustments for text position and size. It ensures precise UI layouts and presentations align with design goals.

The following text measurement capabilities are supported:

- **Measurement of text width**: measures the horizontal length of the given text in a specific font, size, and style.

- **Measurement of text height**: measures the vertical height of the given text, which usually involves the ascender and descender of the font.

- **Measurement of line spacing**: measures the vertical distance between multiple lines of text, which is usually related to the line spacing of the font.

- **Measurement of character spacing**: measures the horizontal distance between individual characters, which is usually related to the glyph and font design.


## Available APIs

The following table lists the common APIs for text measurement. For details, see [drawing_text_typography.h](../reference/apis-arkgraphics2d/capi-drawing-text-typography-h.md).

| Name| Description| 
| -------- | -------- |
| double OH_Drawing_TypographyGetLongestLine(OH_Drawing_Typography\*) | Obtains the width of the longest line. You are advised to round up the return value in actual use.| 
| double OH_Drawing_TypographyGetLongestLineWithIndent(OH_Drawing_Typography\*) | Obtains the width of the longest line, including its indentation. You are advised to round up the return value in actual use.| 
| size_t OH_Drawing_TypographyGetLineCount (OH_Drawing_Typography\* ) | Obtains the number of lines.| 
| OH_Drawing_LineMetrics\* OH_Drawing_TypographyGetLineMetrics (OH_Drawing_Typography\* ) | Obtains the metrics about a certain line in a paragraph, including the height, width, and start coordinates of a line.| 
| double OH_Drawing_TextStyleGetLetterSpacing (OH_Drawing_TextStyle \*) | Obtains the letter spacing of a text style.| 


## How to Develop

1. Add the following library to the `src/main/cpp/CMakeLists.txt` file of the project.
   ```c++
   libnative_drawing.so
   ```

2. Import the required header files.

   <!-- @[c_text_metrics_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/NDKTextMeasurement/entry/src/main/cpp/samples/sample_bitmap.cpp) -->
   
   ``` C++
   #include <native_drawing/drawing_font_collection.h>
   #include <native_drawing/drawing_text_typography.h>
   #include <native_drawing/drawing_text_declaration.h>
   ```

3. Create a paragraph generator **ParagraphBuilder** and set the paragraph style.

   <!-- @[c_text_metrics_create_paragraph](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/NDKTextMeasurement/entry/src/main/cpp/samples/sample_bitmap.cpp) -->
   
   ``` C++
   // Create a text style and set the font size to 50.
   OH_Drawing_SetTextStyleColor(myTextStyle, OH_Drawing_ColorSetArgb(0xFF, 0x00, 0x00, 0x00));
   OH_Drawing_SetTextStyleFontSize(myTextStyle, 50.0);
   // Create a paragraph style object to set the typography style.
   OH_Drawing_TypographyStyle *typographyStyle = OH_Drawing_CreateTypographyStyle();
   // Set the alignment mode of the paragraph style to left alignment.
   OH_Drawing_SetTypographyTextAlign(typographyStyle, TEXT_ALIGN_LEFT);
   // Create a paragraph generator.
   OH_Drawing_TypographyCreate *handler = OH_Drawing_CreateTypographyHandler(typographyStyle, fontCollection);
   // Set the text style in the paragraph generator.
   OH_Drawing_TypographyHandlerPushTextStyle(handler, myTextStyle);
   // Add the text content to the paragraph generator.
   const char *text = "Text metrics for typography measurement";
   OH_Drawing_TypographyHandlerAddText(handler, text);
   // Generate a paragraph using the paragraph generator.
   OH_Drawing_Typography *typography = OH_Drawing_CreateTypography(handler);
   ```

4. Call the typography API and set the paragraph width.

   <!-- @[c_text_metrics_layout](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/NDKTextMeasurement/entry/src/main/cpp/samples/sample_bitmap.cpp) -->
   
   ``` C++
   // Shape the paragraph and set the width to maxWidth.
   OH_Drawing_TypographyLayout(typography, maxWidth);
   ```

5. Call the paragraph measurement API to obtain the desired data.

   <!-- @[c_text_metrics_get_all_case](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/NDKTextMeasurement/entry/src/main/cpp/samples/sample_bitmap.cpp) -->
   
   ``` C++
   // Case 1: Obtain the width of the longest line after typography.
   double longestLine = OH_Drawing_TypographyGetLongestLine(typography);
   DRAWING_LOGI("Line %{public}d longestLine: %{public}f", longestLine);
   
   // Case 2: Obtain the number of lines in the paragraph after typography.
   size_t lineCnt = OH_Drawing_TypographyGetLineCount(typography);
   DRAWING_LOGI("lineCnt: %{public}zu", lineCnt);
   
   // Case 3: Obtain the metrics of each line in the paragraph.
   OH_Drawing_LineMetrics *lineMetrics = OH_Drawing_TypographyGetLineMetrics(typography);
   int lineMetricsSize = OH_Drawing_LineMetricsGetSize(lineMetrics);
   for (int i = 0; i < lineMetricsSize; ++i) {
   // lineMetrics is the text metrics measured after typography.
   double curLineAscender = -lineMetrics[i].ascender;
   double curLineWidth = lineMetrics[i].width;
       DRAWING_LOGI("Line %{public}d lineMetrics ascender: %{public}f", i + 1, curLineAscender);
       DRAWING_LOGI("Line %{public}d lineMetrics width: %{public}f", i + 1, curLineWidth);
   }
   
   // Case 4: Obtain the width of the longest line in the paragraph and the width of the longest line with indentation.
   double longestLineWithIndent = OH_Drawing_TypographyGetLongestLineWithIndent(typography);
   DRAWING_LOGI("longestLineWithIndent: %{public}f", longestLineWithIndent);
   
   OH_Drawing_Font_Metrics fontMetrics;
   // Obtain the font metrics of a text style.
   bool result = OH_Drawing_TextStyleGetFontMetrics(typography, myTextStyle, &fontMetrics);
   DRAWING_LOGI("result: %{public}zu, fontMetrics ascent: %{public}f" , result, fontMetrics.ascent);
   // Obtain the line metrics in a typography object. This API must be called after OH_Drawing_TypographyLayout is called.
   OH_Drawing_LineMetrics lineMetric;
   OH_Drawing_TypographyGetLineMetricsAt(typography, 0, &lineMetric);
   DRAWING_LOGI("Line 1 lineMetrics ascender: %{public}f", -lineMetric.ascender);
   ```
