# Text Measurement (ArkTS)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

## Overview

Text measurement refers to the process of evaluating the size and layout of text and calculating the space (such as the width, height, and other related information) occupied by the text in a given font and style during graphics drawing. Text measurement is used in scenarios such as text typesetting, layout, rendering, and adjustment of the text display position and size. This helps you better control and adjust the layout and presentation of the UI to meet the design expectations.

Currently, the following text measurement capabilities are supported:


- **Text width**: measures the horizontal length of the given text in a specific font, size, and style.

- **Text height**: measures the vertical height of the given text, which usually involves the ascender and descender of the text.

- **Line spacing**: measures the vertical distance between multiple lines of text, which is usually related to the line spacing of the text.

- **Character spacing**: measures the horizontal distance between characters, which is usually related to the glyph and font design.


## Available APIs

The following table lists the APIs commonly used for text measurement. For details about the APIs, see @ohos.graphics.text (../reference/apis-arkgraphics2d/js-apis-graphics-text.md#paragraph).

| Name| Description| 
| -------- | -------- |
| getLongestLine(): number | Obtains the width of the longest line in the current paragraph. You are advised to round up the returned value.| 
| getLongestLineWithIndent(): number | Obtains the width of the longest line in the current paragraph (the width includes the indentation width of the current line). You are advised to round up the returned value.| 
| getTextLines(): Array&lt;TextLine&gt; | Obtains the array of text line objects in the current paragraph.| 
| getLineMetrics(): Array&lt;LineMetrics&gt; | Obtains the measurement information about all lines in a paragraph. The measurement information includes the height, width, and start coordinates of a line.| 
| getLineMetrics(lineNumber: number): LineMetrics \| undefined | Obtains the measurement information of a specified line in a paragraph, including the height, width, and start coordinates of the line. If the number of lines exceeds the maximum number of lines in the paragraph, undefined is returned.| 


## How to Develop

1. Import the required modules.

   ```ts
   import { text } from '@kit.ArkGraphics2D';
   ```

2. Create a paragraph style and use the paragraph generator ParagraphBuilder to generate a paragraph instance.

   ```ts
   // Set the text style.
   let myTextStyle: text.TextStyle = {
       color: { alpha: 255, red: 255, green: 0, blue: 0 },
       fontSize: 100
   };
   // Create a paragraph style object to set the layout style.
   let myParagraphStyle: text.ParagraphStyle = {
       textStyle: myTextStyle,
       wordBreak:text.WordBreak.NORMAL
   }
   // Create a paragraph generator.
   let paragraphBuilder: text.ParagraphBuilder = new text.ParagraphBuilder(myParagraphStyle, new text.FontCollection());
   ```

3. Set the text style, add text content, and generate paragraph text for subsequent text drawing and display.

   ```ts
   // Set the text style in the paragraph generator.
   paragraphBuilder.pushStyle(myTextStyle);
   // Set the text content in the paragraph generator.
   paragraphBuilder.addText ("Text measurement test");
   // Generate a paragraph through the paragraph generator.
   let paragraph = paragraphBuilder.build();
   ```

4. Call the measurement API to obtain the specified measurement information.

   ```ts
   // Case 1: Obtain the width of the longest line after layout.
   let longestLineWidth = paragraph.getLongestLine();
   // Case 2: Obtain the width of the longest line after layout (including indentation).
   let longestLineWithIndentWidth = paragraph.getLongestLineWithIndent()
   // Case 3: Obtain all line objects after layout.
   let textLines = paragraph.getTextLines();
   // Case 4: Obtain the measurement information of a specified line after layout.
   let lineCnt = paragraph.getLineCount();
   for (let index = 0; index < lineCnt; index++) {
       let lineMetrics = paragraph.getLineMetrics(index);
   }
   // Case 5: Obtain the measurement information array of all lines after layout.
   let allLineMetrics = paragraph.getLineMetrics();
   ```

## Complete Sample Code

The following is a complete example of text measurement.

   <!-- @[ts_text_metrics_total](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics2D/TextMetrics/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI';
   import { UIContext } from '@kit.ArkUI';
   import { text } from '@kit.ArkGraphics2D';

   // Create a custom rendering node class to draw text.
   class MyRenderNode extends RenderNode {
   async draw(context: DrawContext) {
      // Obtain the canvas object.
      const canvas = context.canvas;
      // Configure the text style (red, 100 px).
      let myTextStyle: text.TextStyle = {
         color: {
         alpha: 255,
         red: 255,
         green: 0,
         blue: 0
         },
         fontSize: 100
      };
      // Create a paragraph style object to set the layout style.
      let myParagraphStyle: text.ParagraphStyle = {
         textStyle: myTextStyle,
         wordBreak: text.WordBreak.NORMAL
      };
      // Create a paragraph generator.
      let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, new text.FontCollection());
      // Set the text style in the paragraph generator.
      paragraphBuilder.pushStyle(myTextStyle);
      // Set the text content in the paragraph generator.
      paragraphBuilder.addText ("Text measurement test");
      // Generate a paragraph through the paragraph generator.
      let paragraph = paragraphBuilder.build();
      // Layout
      paragraph.layoutSync(1000);
      //Case 1: Obtain the width of the longest line after typesetting.
      let longestLineWidth = paragraph.getLongestLine();
      console.info("longestLineWidth = " + longestLineWidth);

      //Case 2: Obtain the width of the longest line after typesetting (including indentation).
      let longestLineWithIndentWidth = paragraph.getLongestLineWithIndent();
      console.info("longestLineWithIndentWidth = " + longestLineWithIndentWidth);

      //Case 3: Obtain all line objects after typesetting.
      let textLines = paragraph.getTextLines();
      for (let index = 0; index < textLines.length; index++) {
         const textline = textLines[index];
         let curLineRange = textline.getTextRange();
         let curLineGlyCnt = textline.getGlyphCount();
         console.info("MetricsMSG: The TextRange start: " + curLineRange.start + " TextRange end: " + curLineRange.end) of line " + (index + 1) + " is as follows:");
         console.info("MetricsMSG: The number of glyphs in line " + (index + 1) + " is " + curLineGlyCnt);
      }

      //Case 4: Obtain the measurement information of a specified line after typesetting.
      let lineCnt = paragraph.getLineCount();
      for (let index = 0; index < lineCnt; index++) {
         let lineMetrics = paragraph.getLineMetrics(index);
         if (lineMetrics) {
         console.info("MetricsMSG: Row " + (index + 1) + "lineMetrics width: " + lineMetrics.width);
         console.info("MetricsMSG: Row " + (index + 1) + "lineMetrics start index: " + lineMetrics.startIndex + ", end index: " +
         lineMetrics.endIndex);
         }
      }

      // Case 5: Obtain the array of all line measurement information after layout.
      let allLineMetrics = paragraph.getLineMetrics();
      console.info("MetricsMSG: Line 1 lineMetrics width: " + allLineMetrics[0].width);
      paragraph.paint(canvas, 0, 800);
   }
   }

   // Create a text rendering node instance.
   const textNode = new MyRenderNode();
   // Define the size and position of newNode.
   textNode.frame = { x: 0, y: 0, width: 400, height: 600 };

   class MyNodeController extends NodeController {
   private rootNode: FrameNode | null = null;

   makeNode(uiContext: UIContext): FrameNode {
      this.rootNode = new FrameNode(uiContext);
      if (this.rootNode == null) {
         return this.rootNode;
      }
      const renderNode = this.rootNode.getRenderNode();
      if (renderNode != null) {
         renderNode.frame = {
         x: 0,
         y: 0,
         width: 300,
         height: 50
         };
         renderNode.pivot = { x: 0, y: 0 };
      }
      return this.rootNode;
   }

   addNode(node: RenderNode): void {
      if (this.rootNode == null) {
         return;
      }
      const renderNode = this.rootNode.getRenderNode();
      if (renderNode != null) {
         renderNode.appendChild(node);
      }
   }

   clearNodes(): void {
      if (this.rootNode == null) {
         return;
      }
      const renderNode = this.rootNode.getRenderNode();
      if (renderNode != null) {
         renderNode.clearChildren();
      }
   }
   }

   @Entry
   @Component
   struct RenderTest {
   private myNodeController: MyNodeController = new MyNodeController();

   build() {
      Column() {
         Row() {
         NodeContainer(this.myNodeController)
            .height('100%')
            .position({x : 30, y: 25})

         Button($r("app.string.Button_label"))
            .fontSize('16fp')
            .fontWeight(500)
            .margin({ bottom: 24, right: 12 })
            .onClick(() => {
               this.myNodeController.clearNodes();
               this.myNodeController.addNode(textNode);
            })
            .width('50%')
            .height(40)
         }
         .width('100%')
         .justifyContent(FlexAlign.Center) // Aligns the child elements in the current Row container to the center of the main axis.
         .alignItems(VerticalAlign.Bottom) // Aligns the child elements in the current Row container to the bottom of the cross axis (vertical direction).
         .layoutWeight(1) // Set the layout weight of the current Row in the parent Column container to 1.
      }
   }
   }
   ```
