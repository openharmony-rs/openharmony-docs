# 自定义文本绘制与显示（ArkTS）
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @KejiePeng-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

在复杂的文本排版场景中，开发者常常需要在不依赖系统排版的前提下，获取文本的字形信息、宽度、方向等底层数据，以便实现自定义的排版逻辑。系统提供了独立的文本塑形能力，允许开发者通过API获取文字的测量信息，从而支持自定义排版、绘制、断行等操作。

这种能力特别适用于以下场景：

- 自定义富文本渲染（如社交媒体、新闻客户端）

- 跨平台一致性排版需求应用

- 精细化排版管理（如艺术排版、动态文字布局）

## 独立塑形

### 接口说明
独立塑形中常用接口如下表所示，详细接口说明参考[@ohos.graphics.text (文本模块)](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#paragraph)和[@ohos.graphics.drawing (drawing TextBlob)](../reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-TextBlob.md)。

| 接口名 | 描述 | 
| -------- | -------- |
| buildLineTypeset(): LineTypeset | 构建行排版器。 | 
| createLine(startIndex: number, count: number): TextLine | 根据指定的排版区间生成文本行对象。 | 
| getGlyphRuns(): Array<Run> | 获取文本行的排版单元数组。 | 
| getGlyphs(): Array<number> | 获取该排版单元中每个字符的字形序号。 | 
| getFont(): drawing.Font | 获取排版单元的字体属性对象。 | 
| getAdvances(range: Range): Array<common2D.Point> | 获取该排版单元指定范围内每个字形的字形宽度数组。 | 
| static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob | 基于RunBuffer信息创建TextBlob对象。 | 
| static makeFromRunBuffer(pos: Array<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob | 基于RunBuffer信息创建TextBlob对象。 | 
| drawTextBlob(blob: TextBlob, x: number, y: number): void | 绘制一段文字。若构造blob的字体不支持待绘制字符，则该部分字符无法绘制。 | 


### 开发步骤

1. 导入依赖的相关模块。

   ```ts
   import { text } from '@kit.ArkGraphics2D'
   import { drawing } from '@kit.ArkGraphics2D'
   import { common2D } from '@kit.ArkGraphics2D'
   ```

2. 创建段落样式，并使用构造段落生成器ParagraphBuilder生成段落实例。

   ```ts
   // 设置文本样式
   let myTextStyle: text.TextStyle = {
       fontSize: 100
   };
   // 创建一个段落样式对象，以设置排版风格
   let myParagraphStyle: text.ParagraphStyle = {
       textStyle: myTextStyle,
   }
   // 创建一个段落生成器
   let paragraphBuilder: text.ParagraphBuilder = new text.ParagraphBuilder(myParagraphStyle, new text.FontCollection());
   ```

3. 设置文本样式，添加文本内容。

   ```ts
   let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
   // 添加文本
   paragraphBuilder.addText("Hello World");
   ```
   
4. 创建行对象。获取行中所有文字的塑形结果。

   ```ts
   // 从第0个字符开始，获取11个字符，正好是“Hello World”这几个字符的结果。
   let textLine: text.TextLine = lineTypeSet.createLine(0, 11);
   // 获取塑形结果
   let runs: Array<text.Run> = textLine.getGlyphRuns();
   ```

5. 遍历所有字形，创建textBlob对象并重新定义字形位置，通过drawTextBlob接口进行自定义绘制。

   ```ts
   for (let index = 0; index < runs.length; index++) {
     const run = runs[index];
     // 绘制字形
     let glyphs: Array<number> = run.getGlyphs();
     let font: drawing.Font = run.getFont();
     let advances: Array<common2D.Point> = run.getAdvances({ start: 0, end: 0 });

     // 创建字形buffer，通过drawing接口进行字形独立绘制
     let runBuffer: Array<drawing.TextBlobRunBuffer> = [];
     for (let i = 0; i < glyphs.length; i++) {
       runBuffer.push({ glyph: glyphs[i], positionX: x, positionY: y });
       x += advances[i].x + 10;
       y += advances[i].y + 30
       0;
     }
     let textBlob: drawing.TextBlob = drawing.TextBlob.makeFromRunBuffer(runBuffer, font, null);
     // 自定义绘制一串具有相同属性的一系列连续字形
     canvas.drawTextBlob(textBlob, 20, 100);
   }
   ```

### 完整示例

完整的独立塑形示例如下。
<!-- @[arkts_independent_shaping_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics2D/ComplexTextDrawing/entry/src/main/ets/pages/shape/IndependentShaping.ets) -->

### 效果展示
![ts_independent_shaping.png](figures/ts_independent_shaping.png)
