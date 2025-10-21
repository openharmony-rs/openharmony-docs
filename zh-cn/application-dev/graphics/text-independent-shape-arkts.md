# 独立塑形（ArkTS）
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @KejiePeng-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->

## 场景介绍

在复杂的文本排版场景中，开发者常常需要在不依赖系统排班的前提下，获取文本的字形信息、宽度、方向等底层数据，以便实现自定义的排版逻辑。系统提供了独立的文本塑形能力，允许开发者通过API获取文字的测量信息，从而支持自定义排版、绘制、断行等操作。

这种能力特别适用于以下场景：

- 自定义富文本渲染（如社交媒体、新闻客户端）

- 跨平台一致性排版需求应用

- 精细化排版管理（如艺术排版、动态文字布局）

## 接口说明

独立塑形中常用接口如下表所示，详细接口说明参考[@ohos.graphics.text (文本模块)](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#paragraph)。

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


## 开发步骤

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

## 完整示例

完整的文本测量示例如下。
```ts
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

// 绘制代码逻辑写在这里
function drawText(canvas: drawing.Canvas) {
  let myTextStyle: text.TextStyle = {
    // 文本大小
    fontSize: 100
  };
  let myParagraphStyle: text.ParagraphStyle = {
    textStyle: myTextStyle,
  };
  let fontCollection = text.FontCollection.getGlobalInstance();
  let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
  // 添加文本
  paragraphBuilder.addText("Hello World");
  // 生成行
  let lineTypeSet: text.LineTypeset = paragraphBuilder.buildLineTypeset()
  let textLine: text.TextLine = lineTypeSet.createLine(0, 11);

  // 获取塑形结果
  let runs: Array<text.Run> = textLine.getGlyphRuns();
  let x: number = 0;
  let y: number = 0;
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
}

// 创建一个MyRenderNode类，并绘制文本。
class MyRenderNode extends RenderNode {
  async draw(context: DrawContext) {
    drawText(context.canvas);
  }
}

// 创建一个MyRenderNode对象
const textNode = new MyRenderNode()
// 定义newNode的像素格式
textNode.frame = {
  x: 0,
  y: 0,
  width: 300,
  height: 300
}

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode {
    this.rootNode = new FrameNode(uiContext)
    if (this.rootNode == null) {
      return this.rootNode
    }
    const renderNode = this.rootNode.getRenderNode()
    if (renderNode != null) {
      renderNode.frame = {
        x: 0,
        y: 0,
        width: 500,
        height: 500
      }
      renderNode.appendChild(textNode);
    }
    return this.rootNode
  }
}
```

### 效果展示
![ts_independent_shaping.png](figures/ts_independent_shaping.png)
