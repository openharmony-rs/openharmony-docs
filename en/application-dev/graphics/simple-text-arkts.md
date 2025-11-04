# Drawing and Displaying Simple Text (ArkTS)
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @gmiao522; @Lem0nC-->
<!--Designer: @liumingxiang-->
<!--Tester: @yhl0101-->
<!--Adviser: @ge-yafang-->
## Scenario Introduction

In a simple user interface, only a few lines of static text may need to be displayed, such as the text on labels, buttons, menu items, or status bar. In this case, you only need to select a proper font, size, and color to complete rendering.

## Related Attribute

The following table describes the text style properties involved in this scenario. For details about more text styles, see [TextStyle](../reference/apis-arkgraphics2d/js-apis-graphics-text.md#textstyle).

- color: font color. The default value is white. Note that the canvas color must be distinguished from the text color to ensure that the text can be properly displayed.

- fontSize: font size. The value is a floating point number. The default value is 14.0, in physical pixels.


## How to Develop

1. Obtain the canvas object through context.

   ```ts
   let canvas = context.canvas;
   ```

2. Initialize the text style. Here, set the font color to red and the font size to 50.

   ```ts
   let myTextStyle: text.TextStyle = {
     // Text color
     color: {
       alpha: 255,
       red: 255,
       green: 0,
       blue: 0
     },
     // Text size.
     fontSize: 100
   };
   ```

3. Initialize the paragraph style.

   ```ts
   // Set the paragraph style.
   let myParagraphStyle: text.ParagraphStyle = {
     textStyle: myTextStyle,
   };
   ```

4. Initialize the paragraph object and add text.

   ```ts
   let fontCollection = text.FontCollection.getGlobalInstance();
   let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
   // Update the text style.
   paragraphBuilder.pushStyle(myTextStyle);
   // Add text.
   paragraphBuilder.addText('Hello World');
   ```

5. Format the paragraph and draw the text.

   ```ts
   // Generate a paragraph.
   let paragraph = paragraphBuilder.build();
   // Layout
   paragraph.layoutSync(1250);
   // Draw the text.
   paragraph.paint(canvas, 10, 0);
   ```


## Complete Sample Code

<!-- @[arkts_drawing_simple_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/graphic/ArkGraphics2D/SimpleTextDrawing/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI'
import { UIContext } from '@kit.ArkUI'
import { text } from '@kit.ArkGraphics2D'

// Create a custom rendering node class for drawing text.
class MyRenderNode extends RenderNode {
  async draw(context: DrawContext) {

    // Obtain the canvas object.
    let canvas = context.canvas;
    // Obtain the text style.
    let myTextStyle: text.TextStyle = {
      // Text color
      color: {
        alpha: 255,
        red: 255,
        green: 0,
        blue: 0
      },
      // Text size.
      fontSize: 100
    };

    let myParagraphStyle: text.ParagraphStyle = {
      textStyle: myTextStyle,
    };
    let fontCollection = text.FontCollection.getGlobalInstance();
    let ParagraphGraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
    // Update the text style.
    ParagraphGraphBuilder.pushStyle(myTextStyle);
    // Add text.
    ParagraphGraphBuilder.addText("Hello World");

    // Generate a paragraph.
    let paragraph = ParagraphGraphBuilder.build();
    // Layout
    paragraph.layoutSync(1250);
    // Draw the text.
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

// Create a new MyRenderNode object instance.
const newNode = new MyRenderNode();
// Define the frame information (position and size) of newNode.
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
      .justifyContent(FlexAlign.Center) // Center aligns child elements in the current row container on the main axis.
      .shadow(ShadowStyle.OUTER_DEFAULT_SM) // Sets the shadow effect outside the row container.
      .alignItems(VerticalAlign.Bottom) // Sets the alignment mode of child elements in the current row container to bottom alignment on the cross axis (vertical direction).
      .layoutWeight(1) // Set the layout weight of the current row in the parent container column to 1.
    }
  }
}
```

## Effect

![image_0000002246603717](figures/simpleText.PNG)
