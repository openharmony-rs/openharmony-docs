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
     // Text size
     fontSize: 50
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
   paragraphBuilder.addText("Hello World");
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

```ts
import { NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI'
import { UIContext } from '@kit.ArkUI'
import { text } from '@kit.ArkGraphics2D'

// Create a MyRenderNode class and draw the text.
class MyRenderNode extends RenderNode {
  async draw(context: DrawContext) {
    
    // Add the drawing logic here.
    let canvas = context.canvas;
    
    let myTextStyle: text.TextStyle = {
      // Text color.
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
    let paragraphBuilder = new text.ParagraphBuilder(myParagraphStyle, fontCollection);
    // Update the text style.
    paragraphBuilder.pushStyle(myTextStyle);
    // Add text.
    paragraphBuilder.addText("Hello World");

    // Generate a paragraph.
    let paragraph = paragraphBuilder.build();
    // Layout
    paragraph.layoutSync(1250);
    // Draw text.
    paragraph.paint(canvas, 10, 800);
  }
}

// Create a MyRenderNode object.
const textNode = new MyRenderNode()
// Define the pixel format of MyRenderNode.
textNode.frame = {
  x: 0,
  y: 100,
  width: 1250,
  height: 800
}
textNode.pivot = { x: 0.2, y: 0.8 }
textNode.scale = { x: 1, y: 1 }

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

let myNodeController: MyNodeController = new MyNodeController()

async function performTask() {
  myNodeController.clearNodes()
  myNodeController.addNode(textNode)
}

@Entry
@Component
struct Font08 {
  @State src: Resource = $r('app.media.startIcon')
  build() {
    Column() {
      Row() {
        NodeContainer(myNodeController)
          .height('100%')
          .width('100%')
        Image(this.src)
          .width('0%').height('0%')
          .onComplete(
            () => {
              performTask();
            })
      }
      .width('100%')
    }
  }
}
```

## Effect

![image_0000002246603717](figures/simpleText.PNG)
