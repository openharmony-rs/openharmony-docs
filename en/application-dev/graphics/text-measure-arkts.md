# Text Measurement (ArkTS)
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

- **Measurement of text height**: measures the vertical height of the given text, which usually involves the ascender and descender of the text.

- **Measurement of line spacing**: measures the vertical distance between multiple lines of text, which is usually related to the line spacing of the text.

- **Measurement of character spacing**: measures the horizontal distance between individual characters, which is usually related to the glyph and font design.


## Available APIs

The following table lists the APIs used for text measurement. For details about the APIs, see [@ohos.graphics.text (Text)](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#paragraph).

| Name| Description| 
| -------- | -------- |
| getLongestLine(): number | Obtains the width of the longest line of a paragraph. You are advised to round up the return value in actual use.| 
| getLongestLineWithIndent(): number | Obtains the width of the longest line of a paragraph, including its indentation. You are advised to round up the return value in actual use.| 
| getTextLines(): Array&lt;TextLine&gt; | Obtains the array of text line objects of a paragraph.| 
| getLineMetrics(): Array&lt;LineMetrics&gt; | Obtains the metrics about all lines in a paragraph, including the height, width, and start coordinates of a line.| 
| getLineMetrics(lineNumber: number): LineMetrics \| undefined | Obtains the metrics about a certain line in a paragraph, including the height, width, and start coordinates of a line. It returns **undefined** when the input line number goes beyond the maximum number of lines that the current paragraph has after typography.| 


## How to Develop

1. Import the required module.

   <!-- @[ts_text_metrics_include](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/TextMetrics/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { text } from '@kit.ArkGraphics2D';
   ```

2. Create a paragraph style and use **ParagraphBuilder** to generate a paragraph instance.

   <!-- @[ts_text_metrics_create_paragraphBuilder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/TextMetrics/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Set the text style.
   let myTextStyle: text.TextStyle = {
     color: {
       alpha: 255,
       red: 255,
       green: 0,
       blue: 0
     },
     fontSize: 100
   };
   // Create a paragraph style object to set the typography style.
   let myParagraphStyle: text.ParagraphStyle = {
     textStyle: myTextStyle,
     wordBreak: text.WordBreak.NORMAL
   };
   // Create a paragraph generator.
   let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, new text.FontCollection());
   ```

3. Set the text style, add text content, and generate paragraph text for subsequent text drawing and display.

   <!-- @[ts_text_metrics_create_paragraph](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/TextMetrics/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Set the text style in the paragraph generator.
   paragraphBuilder.pushStyle(myTextStyle);
   // Set the text content in the paragraph generator.
   paragraphBuilder.addText("Text measurement test");
   // Generate a paragraph using the paragraph generator.
   let paragraph = paragraphBuilder.build();
   ```

4. Call the measurement APIs to obtain the desired information.

   <!-- @[ts_text_metrics_get_all_case](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkGraphics2D/TextEngine/TextMetrics/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Shape the paragraph and set the width to 1000.
   paragraph.layoutSync(1000);
   // Case 1: Obtain the width of the longest line after typography.
   let longestLineWidth = paragraph.getLongestLine();
   console.info("longestLineWidth = " + longestLineWidth);
   
   // Case 2: Obtain the width of the longest line after typography (including indentation).
   let longestLineWithIndentWidth = paragraph.getLongestLineWithIndent();
   console.info("longestLineWithIndentWidth = " + longestLineWithIndentWidth);
   
   // Case 3: Obtain all line objects after typography.
   let textLines = paragraph.getTextLines();
   for (let index = 0; index < textLines.length; index++) {
     const textline = textLines[index];
     let curLineRange = textline.getTextRange();
     let curLineGlyCnt = textline.getGlyphCount();
     console.info("MetricsMSG: line " + (index + 1) + "TextRange start: " + curLineRange.start + " TextRange end: " + curLineRange.end);
     console.info("MetricsMSG: line" + (index + 1) + "glyph count: " + curLineGlyCnt);
   }
   
   // Case 4: Obtain the metrics of a certain line after typography.
   let lineCnt = paragraph.getLineCount();
   for (let index = 0; index < lineCnt; index++) {
     let lineMetrics = paragraph.getLineMetrics(index);
     if (lineMetrics) {
       console.info("MetricsMSG: line" + (index + 1) + "lineMetrics width: " + lineMetrics.width);
       console.info("MetricsMSG: line" + (index + 1) + "lineMetrics start index: " + lineMetrics.startIndex + ", end index: " +
       lineMetrics.endIndex);
     }
   }
   
   // Case 5: Obtain the metrics array of all lines after typography.
   let allLineMetrics = paragraph.getLineMetrics();
   console.info("MetricsMSG: line 1 lineMetrics width: " + allLineMetrics[0].width);
   ```
