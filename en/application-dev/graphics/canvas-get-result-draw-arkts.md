# Obtaining a Canvas and Displaying Drawing Results (ArkTS)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->


## Scenario Introduction

Canvas provides the capability of drawing basic graphics, which is used to draw and process graphics on the screen. You can use Canvas to implement custom drawing effects and enhance user experience.


Canvas is the core of graphics drawing. All drawing operations mentioned in this chapter (including drawing basic graphics, text, and images, and transforming graphics) are based on Canvas.


Currently, ArkTS provides two methods for obtaining a canvas: obtaining a canvas that can be directly displayed (see [RenderNode](../reference/apis-arkui/js-apis-arkui-renderNode.md)) and obtaining an offscreen canvas (see [NodeController](../reference/apis-arkui/js-apis-arkui-nodeController.md)). The former enables you to display the drawing result on the screen without additional operations after calling the drawing API, while the latter requires existing display methods to display the drawing result.


## Obtaining a Canvas That Can Be Directly Displayed

Obtain a canvas that can be directly displayed on the screen through [RenderNode](../reference/apis-arkui/js-apis-arkui-renderNode.md).

1. Add a custom RenderNode.

2. Add a custom [NodeController](../reference/apis-arkui/js-apis-arkui-nodeController.md).

3. Override the [draw()](../reference//apis-arkui/js-apis-arkui-renderNode.md#draw) function of the custom RenderNode to obtain the canvas for custom drawing operations.

4. Display the custom NodeController.

```ts
import { UIContext, NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

// 1. Customize RenderNode.
export class MyRenderNode extends RenderNode {
  async draw(context: DrawContext) {
    const canvas = context.canvas;
    // 3. Customize rendering-related operations.
    const brush = new drawing.Brush();
    brush.setColor({red: 255, blue: 0, green: 0, alpha: 255});
    canvas.attachBrush(brush);
    canvas.drawRect({left: 0, right: 300, top: 0, bottom: 300});
  }
}

// 2. Customize NodeController.
export class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  myRenderNode = new MyRenderNode();

  makeNode(uiContext: UIContext): FrameNode {
    this.rootNode = new FrameNode(uiContext);
    if (this.rootNode === null) {
      return this.rootNode;
    }

    const renderNode = this.rootNode.getRenderNode();
    if (renderNode !== null) {
      this.myRenderNode.backgroundColor = 0xffffffff;
      this.myRenderNode.frame = { x: 0, y: 0, width: 4800, height: 4800 };
      this.myRenderNode.pivot = { x: 0.2, y: 0.8 };
      this.myRenderNode.scale = { x: 1, y: 1 };
      renderNode.appendChild(this.myRenderNode);
      renderNode.clipToFrame = true;
    }
    return this.rootNode;
  }
}

@Entry
@Component
struct RenderTest {
  @State message: string = 'hello'
  build() {
    Row() {
      Column() {
        // 4. Display the custom NodeController.
        NodeContainer(new MyNodeController())
          .width('100%')
      }
      .width('100%')
      .height('80%')
    }
    .height('100%')
  }
}
```
<!-- [arkts_graphics_draw_direct_canvas_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->


## Obtaining and Displaying the Off-Screen Canvas

1. Add a custom RenderNode.

2. Add a custom [NodeController](../reference/apis-arkui/js-apis-arkui-nodeController.md).

3. Create a PixelMap in the aboutToAppear() function of MyNodeController.

4. Override the [draw()](../reference//apis-arkui/js-apis-arkui-renderNode.md#draw) function of the custom RenderNode to obtain the off-screen canvas for drawing.

   1. Use the PixelMap created in 3 to construct the off-screen canvas.
   2. Perform custom drawing operations on the off-screen canvas.
   3. Pass the drawing result of the off-screen canvas to the RenderNode.

5. Display the custom NodeController.

```ts
import { UIContext, NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';
import { taskpool } from '@kit.ArkTS';
import { drawing } from '@kit.ArkGraphics2D';

// 1. Customize RenderNode.
export class MyRenderNode extends RenderNode {
  pixelMap: image.PixelMap | null = null;
  setPixelMap(pixelMap: image.PixelMap) {
    this.pixelMap = pixelMap;
  }

  async draw(context: DrawContext) {
    const canvas = context.canvas;
    if (this.pixelMap != null) {
      // 4.1 Use the PixelMap created in step 3 to construct an offscreen canvas.
      const canvas_ = new drawing.Canvas(this.pixelMap);

      // 4.2 Perform offscreen drawing.
      const brush = new drawing.Brush();
      brush.setColor({ alpha: 255, red: 255, green: 0, blue: 0 });
      canvas_.attachBrush(brush);
      canvas_.drawRect({left:0,right:100,top:0,bottom:100});

      // 4.3 Deliver the drawing result of the offscreen canvas to RenderNode.
      canvas.drawImage(this.pixelMap, 0, 0);
    }
  }
}

@Concurrent
async function CreatePixelMapAsync() {
  const color : ArrayBuffer = new ArrayBuffer(4000000); // 4000000 indicates the size of the pixel buffer to be created. The value is height x width x 4.
  let opts : image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 1000, width: 1000 } };
  const pixel = await image.createPixelMap(color, opts);
  return pixel;
}

// 2. Customize NodeController.
export class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  myRenderNode = new MyRenderNode();

  // 3. Create a PixelMap object in aboutToAppear of MyNodeController.
  aboutToAppear(): void {
    let task = new taskpool.Task(CreatePixelMapAsync);
    taskpool.execute(task).then((pixel:Object)=>{
      this.myRenderNode.setPixelMap(pixel as image.PixelMap);
      this.myRenderNode.invalidate();
    })
  }

  makeNode(uiContext: UIContext): FrameNode {
    this.rootNode = new FrameNode(uiContext);
    if (this.rootNode === null) {
      return this.rootNode;
    }

    const renderNode = this.rootNode.getRenderNode();
    if (renderNode !== null) {
      this.myRenderNode.backgroundColor = 0xffffffff;
      this.myRenderNode.frame = { x: 0, y: 0, width: 4800, height: 4800 };
      this.myRenderNode.pivot = { x: 0.2, y: 0.8 };
      this.myRenderNode.scale = { x: 1, y: 1 };
      renderNode.appendChild(this.myRenderNode);
      renderNode.clipToFrame = true;
    }
    return this.rootNode;
  }
}
```
<!-- [arkts_graphics_draw_indirect_canvas_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->

```
@Entry
@Component
struct RenderTest {
  @State message: string = 'hello'
  nodeController = new MyNodeController()

  build() {
    Row() {
      Column() {
        // 5. Display the custom NodeController.
        NodeContainer(this.nodeController)
          .width('100%')
      }
      .width('100%')
      .height('80%')
    }
    .height('100%')
  }
}
```
<!-- [arkts_graphics_draw_direct_and_indirect_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->

<!--RP1-->
## Samples

The following samples can be used as references for Drawing (ArkTS) development:

- [ArkTSGraphicsDraw (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Drawing/ArkTSGraphicsDraw)
<!--RP1End-->
