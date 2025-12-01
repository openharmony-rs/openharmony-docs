# 简单文本绘制与显示（ArkTS）
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## 场景介绍

在一个简单的用户界面中，可能只需要展示几行静态文本，例如标签、按钮上的文字、菜单项或状态栏中的提示信息。此时，开发者只需要选择合适的字体、大小和颜色即可完成渲染。

## 相关属性

此场景示例，涉及到的文本样式属性如下，具体及更多文本样式可参考[TextStyle](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#textstyle)。

- color：字体颜色，默认为白色。请注意与画布颜色进行区分，以保证文本的正常显示。

- fontSize：字体大小，浮点数，默认为14.0，单位为物理像素px。


## 开发步骤

1. 通过context获取到Canvas画布对象。

   ```ts
   let canvas = context.canvas;
   ```

2. 初始化文本样式，此处设置字体颜色为红色，字体大小为50。

   ```ts
   let myTextStyle: text.TextStyle = {
     // 文本颜色
     color: {
       alpha: 255,
       red: 255,
       green: 0,
       blue: 0
     },
     // 文本大小
     fontSize: 100
   };
   ```

3. 初始化段落样式。

   ```ts
   // 设置段落样式
   let myParagraphStyle: text.ParagraphStyle = {
     textStyle: myTextStyle,
   };
   ```

4. 初始化段落对象，并添加文本。

   ```ts
   let fontCollection = text.FontCollection.getGlobalInstance();
   let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
   // 更新文本样式
   paragraphBuilder.pushStyle(myTextStyle);
   // 添加文本
   paragraphBuilder.addText('Hello World');
   ```

5. 排版段落并进行文本绘制。

   ```ts
   // 生成段落
   let paragraph = paragraphBuilder.build();
   // 布局
   paragraph.layoutSync(1250);
   // 绘制文本
   paragraph.paint(canvas, 10, 0);
   ```


## 完整示例

<!-- @[arkts_drawing_simple_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics2D/SimpleTextDrawing/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI'
import { UIContext } from '@kit.ArkUI'
import { text } from '@kit.ArkGraphics2D'

// 创建一个自定义的渲染节点类，用于绘制文本
class MyRenderNode extends RenderNode {
  async draw(context: DrawContext) {

    // 获取画布对象
    let canvas = context.canvas;
    // 获取文本样式
    let myTextStyle: text.TextStyle = {
      // 文本颜色
      color: {
        alpha: 255,
        red: 255,
        green: 0,
        blue: 0
      },
      // 文本大小
      fontSize: 100
    };

    let myParagraphStyle: text.ParagraphStyle = {
      textStyle: myTextStyle,
    };
    let fontCollection = text.FontCollection.getGlobalInstance();
    let ParagraphGraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
    // 更新文本样式
    ParagraphGraphBuilder.pushStyle(myTextStyle);
    // 添加文本
    ParagraphGraphBuilder.addText("Hello World");

    // 生成段落
    let paragraph = ParagraphGraphBuilder.build();
    // 布局
    paragraph.layoutSync(1250);
    // 绘制文本
    paragraph.paint(canvas, 0, 100);
  }
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
        width: 10,
        height: 500
      }
      renderNode.pivot = { x: 50, y: 50 }
    }
    return this.rootNode
  }

  addNode(node: RenderNode): void {
    if (this.rootNode == null) {
      return
    }
    const renderNode = this.rootNode.getRenderNode()
    if (renderNode != null) {
      renderNode.appendChild(node)
    }
  }

  clearNodes(): void {
    if (this.rootNode == null) {
      return
    }
    const renderNode = this.rootNode.getRenderNode()
    if (renderNode != null) {
      renderNode.clearChildren()
    }
  }
}

// 创建一个新的 MyRenderNode 对象实例
const newNode = new MyRenderNode();
// 定义 newNode 的帧信息（位置和大小）
newNode.frame = { x: 0, y: 0, width: 400, height: 600 };

@Entry
@Component
struct RenderTest {
  private myNodeController: MyNodeController = new MyNodeController()
  build() {
    Column() {
      Row(){
        NodeContainer(this.myNodeController)
          .height('100%')
          .position({x : 50, y: 25})
        Button($r("app.string.Button_label"))
          .fontSize('16fp')
          .fontWeight(500)
          .margin({ bottom: 24, right: 12 })
          .onClick(() => {
            this.myNodeController.clearNodes()
            this.myNodeController.addNode(newNode)
          })
          .width('50%')
          .height(40)
          .shadow(ShadowStyle.OUTER_DEFAULT_LG)
      }
      .width('100%')
      .justifyContent(FlexAlign.Center) // 设置当前Row容器内子元素在主轴上居中对齐
      .shadow(ShadowStyle.OUTER_DEFAULT_SM) // 设置Row容器外阴影效果
      .alignItems(VerticalAlign.Bottom) // 设置当前Row容器内子元素在交叉轴（垂直方向）上的对齐方式为底部对齐
      .layoutWeight(1) // 设置当前Row在父容器Column中的布局权重为1
    }
  }
}
```

## 效果展示

![zh-cn_image_0000002246603717](figures/simpleText.PNG)
