# Drawing and Displaying Custom Text (ArkTS)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @KejiePeng-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

In complex text layout scenarios, when the standard text components provided by the system cannot meet specific visual or interaction requirements, you can use the underlying text drawing capability provided by ArkGraphics 2D to directly control the canvas and text style to implement refined control over the text appearance and layout. This capability applies to scenarios that require highly customized text rendering effects, such as artistic fonts, complex rich text orchestration, or special dynamic text effects.

As a core component of the graphics system, the font engine is responsible for converting character codes into visual glyphs and accurately calculating the layout and position of each glyph, providing underlying support for custom text drawing. Through the text measurement API, you can obtain the accurate size of the text, which is the basis for precise layout (such as center display).

## Text shaping

### Overview
Text shaping is a key capability provided by the font engine. It allows you to directly obtain the underlying glyph information (such as width and direction measurement information) of the text without going through the default text layout process. This enables you to implement completely customized layout logic, drawing operations, and line break policies based on the raw data.

This capability applies to the following scenarios:

- Custom rich text rendering: For example, in applications such as social media and news clients, image and text mixed layout and multi-style text mixed display need to be implemented.

- Cross-platform consistent layout requirements: Ensure that the text is displayed with the same visual effect on different platforms or devices.

- Refined layout management: For example, implement artistic layout and dynamic text layout, which are difficult to achieve using standard text components.

### Available APIs
The following table lists the common APIs used in text shaping. For details about the APIs, see [@ohos.graphics.text (Text module)](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#paragraph) and [@ohos.graphics.drawing (drawing TextBlob)](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-TextBlob.md).

| API| Description| 
| -------- | -------- |
| buildLineTypeset(): LineTypeset | Creates a text layout.| 
| createLine(startIndex: number, count: number): TextLine | Generates a text line object based on the specified layout range.| 
| getGlyphRuns(): Array&lt;Run&gt; | Obtains the layout unit array of a text line.| 
| getGlyphs(): Array&lt;number&gt; | Obtains the glyph sequence number of each character in the layout unit.| 
| getFont(): drawing.Font | Obtains the font attribute object of the layout unit.| 
| getAdvances(range: Range): Array&lt;common2D.Point&gt; | Obtains the glyph width array of each glyph in the specified range of the layout unit.| 
| static makeFromRunBuffer(pos: Array&lt;TextBlobRunBuffer&gt;, font: Font, bounds?: common2D.Rect): TextBlob | Creates a TextBlob object based on the RunBuffer information.| 
| static makeFromRunBuffer(pos: Array&lt;TextBlobRunBuffer&gt;, font: Font, bounds?: common2D.Rect): TextBlob | Creates a TextBlob object based on the RunBuffer information.| 
| drawTextBlob(blob: TextBlob, x: number, y: number): void | Draws a text blob. If the font used to construct the blob does not support the characters to be drawn, the characters cannot be drawn.| 


### How to Develop
From API version 18 onwards, the text shaping result can be obtained. From API version 20 onwards, the text layout direction and glyph width can be obtained. Sample code:

1. Import the required module.

   ```ts
   import { text } from '@kit.ArkGraphics2D'
   import { drawing } from '@kit.ArkGraphics2D'
   import { common2D } from '@kit.ArkGraphics2D'
   ```

2. Creates a paragraph style and uses ParagraphBuilder to generate a paragraph instance.

   ```ts
   // Set the text style.
   let myTextStyle: text.TextStyle = {
       fontSize: 100
   };
   // Create a paragraph style object to set the typography style.
   let myParagraphStyle: text.ParagraphStyle = {
       textStyle: myTextStyle,
   }
   // Create a paragraph generator.
   let paragraphBuilder: text.ParagraphBuilder = new text.ParagraphBuilder(myParagraphStyle, new text.FontCollection());
   ```

3. Set the text style and add text content.

   ```ts
   let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
   // Add text.
   paragraphBuilder.addText("Hello World");
   ```
   
4. Create a line object. Obtain the shaping result of all characters in a line. 
Use the createLine() method to create a single-line object and use the getGlyphRuns() method of the line object to obtain the text units with the same style.

   ```ts
   // Obtain 11 characters from the 0th character, which is exactly the result of "Hello World".
   let textLine: text.TextLine = lineTypeSet.createLine(0, 11);
   // Obtain the shaping result.
   let runs: Array<text.Run> = textLine.getGlyphRuns();
   ```

5. This step is the custom drawing step in the text shaping process. You can call the getGlyphs() method to obtain the glyph sequence number of each character in the text, and then use the font object obtained by calling the getFont() method to determine the specific glyph information of each character. 
From API version 20 onwards, the getAdvances() method is added to return an array that contains the recommended width and height of each glyph during drawing. Based on these accurate measurement data, you can freely calculate and define the drawing position of each glyph to implement complex text layout effects, such as custom character spacing, vertical offset, or special typesetting.

   ```ts
   for (let index = 0; index < runs.length; index++) {
     const run = runs[index];
     // Draw a glyph.
     let glyphs: Array<number> = run.getGlyphs();
     let font: drawing.Font = run.getFont();
     let advances: Array<common2D.Point> = run.getAdvances({ start: 0, end: 0 });

     // Create a glyph buffer and draw the glyph independently through the drawing API.
     let runBuffer: Array<drawing.TextBlobRunBuffer> = [];
     for (let i = 0; i < glyphs.length; i++) {
       runBuffer.push({ glyph: glyphs[i], positionX: x, positionY: y });
       x += advances[i].x + 10;
       y += advances[i].y + 30;
     }
     let textBlob: drawing.TextBlob = drawing.TextBlob.makeFromRunBuffer(runBuffer, font, null);
     // Draw a series of consecutive glyphs with the same attributes.
     canvas.drawTextBlob(textBlob, 20, 100);
   }
   ```

### Sample Code

The following is a complete example of text shaping.
<!-- @[arkts_independent_shaping_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics2D/ComplexTextDrawing/entry/src/main/ets/pages/shape/IndependentShaping.ets) -->

``` TypeScript
import { NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI'
import { UIContext } from '@kit.ArkUI'
import { text } from '@kit.ArkGraphics2D'
import { drawing } from '@kit.ArkGraphics2D'
import { common2D } from '@kit.ArkGraphics2D'

@Builder
export function PageBuilder(_: string) {
  Index();
}


@Entry
@Component
export default struct Index {
  @State message: string = 'Hello World';
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    NavDestination() {
      Column() {
        Row() {
          NodeContainer(this.myNodeController)
            .height('100%')
            .width('100%')
        }
        .width('100%')
      }
    }
  }
}

// Draw the code logic here.
function drawText(canvas: drawing.Canvas) {
  let myTextStyle: text.TextStyle = {
    // Text size.
    fontSize: 60
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
  };
  let fontCollection = text.FontCollection.getGlobalInstance();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  // Add text.
  paragraphBuilder.addText('Hello World');
  // Generate a line.
  let lineTypeSet: text.LineTypeset = paragraphBuilder.buildLineTypeset()
  let textLine: text.TextLine = lineTypeSet.createLine(0, 11);

  // Obtain the shaping result.
  let runs: text.Run[] = textLine.getGlyphRuns();
  let x: number = 0;
  let y: number = 0;
  for (let index = 0; index < runs.length; index++) {
    const run = runs[index];
    // Draw a glyph.
    let glyphs: number[] = run.getGlyphs();
    let font: drawing.Font = run.getFont();
    let advances: common2D.Point[] = run.getAdvances({ start: 0, end: 0 });

    // Create a glyph buffer and draw glyphs independently through the drawing API.
    let runBuffer: drawing.TextBlobRunBuffer[] = [];
    for (let i = 0; i < glyphs.length; i++) {
      runBuffer.push({ glyph: glyphs[i], positionX: x, positionY: y });
      x += advances[i].x + 10;
      y += advances[i].y + 30;
    }
    let textBlob: drawing.TextBlob = drawing.TextBlob.makeFromRunBuffer(runBuffer, font, null);
    // Draw a series of consecutive glyphs with the same attributes.
    canvas.drawTextBlob(textBlob, 20, 100);
  }
```

Effect: 
![ts_independent_shaping.png](figures/ts_independent_shaping.png)
