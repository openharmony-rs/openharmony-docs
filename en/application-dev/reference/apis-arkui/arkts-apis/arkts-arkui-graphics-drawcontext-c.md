# DrawContext

```TypeScript
export class DrawContext
```

Graphics drawing context, which provides the canvas used for drawing and its width and height.

**Since:** 11

<!--Device-unnamed-export class DrawContext--><!--Device-unnamed-export class DrawContext-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canvas

```TypeScript
get canvas(): drawing.Canvas
```

Obtains the canvas used for drawing.

**Type:** [drawing.Canvas](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-canvas-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DrawContext-get canvas(): drawing.Canvas--><!--Device-DrawContext-get canvas(): drawing.Canvas-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { RenderNode, FrameNode, NodeController, DrawContext } from '@kit.ArkUI';

class MyRenderNode extends RenderNode {

  draw(context: DrawContext) {
    const size = context.size;
    const canvas = context.canvas;
    const sizeInPixel = context.sizeInPixel;
  }
}

const renderNode = new MyRenderNode();
renderNode.frame = { x: 0, y: 0, width: 100, height: 100 };
renderNode.backgroundColor = 0xff519db4;

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.appendChild(renderNode);
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }
  }
}
```

## size

```TypeScript
get size(): Size
```

Obtains the width and height of the canvas.

**Type:** Size

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DrawContext-get size(): Size--><!--Device-DrawContext-get size(): Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## sizeInPixel

```TypeScript
get sizeInPixel(): Size
```

Obtains the width and height of the canvas in px.

**Type:** Size

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DrawContext-get sizeInPixel(): Size--><!--Device-DrawContext-get sizeInPixel(): Size-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
