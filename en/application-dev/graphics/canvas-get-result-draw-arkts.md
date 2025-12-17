# Obtaining a Canvas and Displaying Drawing Results (ArkTS)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->


## Overview

Canvas provides the capability of drawing basic graphics, which is used to draw and process graphics on the screen. You can use Canvas to implement custom drawing effects and enhance user experience.


Canvas is the core of graphics drawing. All drawing operations mentioned in this chapter (including drawing basic graphics, text, and images, and transforming graphics) are based on Canvas.


Currently, ArkTS provides two methods for obtaining a canvas: obtaining a canvas that can be directly displayed (see [RenderNode](../reference/apis-arkui/js-apis-arkui-renderNode.md)) and obtaining an offscreen canvas (see [NodeController](../reference/apis-arkui/js-apis-arkui-nodeController.md)). The former enables you to display the drawing result on the screen without additional operations after calling the drawing API, while the latter requires existing display methods to display the drawing result.


## Obtaining a Canvas That Can Be Directly Displayed

Obtain a canvas that can be directly displayed on the screen through [RenderNode](../reference/apis-arkui/js-apis-arkui-renderNode.md).

1. Import the required files.
   ```ts
   // CanvasGetResult.ets
   import { UIContext, NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI';
   ```
   <!-- [arkts_graphics_draw_import_ui](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->

   ```ts
   // CanvasGetResult.ets
   import { drawing } from '@kit.ArkGraphics2D';
   ```
   <!-- [arkts_graphics_draw_import_graphics2d](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->

2. Add a custom RenderNode.
   ```ts
   // CanvasGetResult.ets
   // 2. Custom RenderNode
   class MyRenderNodeDirectDisplay extends RenderNode {
     async draw(context: DrawContext) {
       const canvas = context.canvas;
       if (canvas === null) {
         console.error('Canvas is null.');
         return;
       }
       // 4. Custom drawing operations
       const brush = new drawing.Brush();
       if (brush === null) {
         console.error('Brush is null.');
         return;
       } else {
         brush.setColor({red: 255, blue: 0, green: 0, alpha: 255});
         canvas.attachBrush(brush);
         canvas.drawRect({left: 0, right: 300, top: 0, bottom: 300});
       }
     }
   }
   ```
  <!-- [arkts_graphics_draw_direct_canvas_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->

3. Add a custom [NodeController](../reference/apis-arkui/js-apis-arkui-nodeController.md).
   ```ts
   // CanvasGetResult.ets
   // 3. Customize NodeController.
   class MyNodeControllerDirectDisplay extends NodeController {
     private rootNode: FrameNode | null = null;
     private myRenderNode = new MyRenderNodeDirectDisplay();

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
   <!-- [arkts_graphics_draw_direct_canvas_api_node_control](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->

4. Override the [draw()](../reference//apis-arkui/js-apis-arkui-renderNode.md#draw) function of the custom RenderNode to obtain the canvas for custom drawing operations.
   ```ts
   // CanvasGetResult.ets
   // 2. Custom RenderNode
   async draw(context: DrawContext) {
     const canvas = context.canvas;
     if (canvas === null) {
       console.error('Canvas is null.');
       return;
     }
     // 4. Custom drawing operations
     const brush = new drawing.Brush();
     if (brush === null) {
       console.error('Brush is null.');
       return;
     } else {
       brush.setColor({red: 255, blue: 0, green: 0, alpha: 255});
       canvas.attachBrush(brush);
       canvas.drawRect({left: 0, right: 300, top: 0, bottom: 300});
     }
   }
   ```
  <!-- [arkts_graphics_draw_direct_canvas_api_rewrite](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->

5. Display the custom NodeController.

   ```ts
   // CanvasGetResult.ets
   @Entry
   @Component
   struct RenderTest {
     @State message: string = 'hello';
     myNodeController_1 = new MyNodeControllerDirectDisplay();
     myNodeController_2 = new MyNodeControllerIndirectDisplay();

     build() {
       Row() {
         Column() {
           Column(){
             Text($r('app.string.DirectCanvas'))
             // Display the canvas on the screen.
             NodeContainer(this.myNodeController_1)
               .width('100%')
               .height('40%')
           }
           Column(){
             Text($r('app.string.OffScreenCanvas'))
             // Offscreen canvas
             NodeContainer(this.myNodeController_2)
               .width('100%')
               .height('40%')
               .margin({ top: 20 })
           }
         }
       }
     }
   }
   ```
   <!-- [arkts_graphics_draw_direct_and_indirect_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->


## Obtaining and Displaying the Off-Screen Canvas

1. Import the required file.
   ```ts
   // CanvasGetResult.ets
   import { UIContext, NodeController, FrameNode, RenderNode, DrawContext } from '@kit.ArkUI';
   import { image } from '@kit.ImageKit';
   import { taskpool } from '@kit.ArkTS';
   import { drawing } from '@kit.ArkGraphics2D';
   ```
   <!-- [arkts_graphics_draw_import_ui_and_graphics2d](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->

2. Add a custom RenderNode.

3. Add a custom [NodeController](../reference/apis-arkui/js-apis-arkui-nodeController.md).

4. Create a PixelMap in the aboutToAppear() function of MyNodeController.

5. Override the [draw()](../reference//apis-arkui/js-apis-arkui-renderNode.md#draw) function of the custom RenderNode to obtain the off-screen canvas for drawing.

   1. Use the PixelMap created in step 4 to construct the offscreen canvas.
   2. Perform custom drawing operations on the off-screen canvas.
   3. Pass the drawing result of the off-screen canvas to the RenderNode.

   ```ts
   // CanvasGetResult.ets
   // 2. Custom RenderNode
   export class MyRenderNodeIndirectDisplay extends RenderNode {
     private pixelMap: image.PixelMap | null = null;
     setPixelMap(pixelMap: image.PixelMap) {
       this.pixelMap = pixelMap;
     }

     async draw(context: DrawContext) {
       const canvas = context.canvas;
       if (this.pixelMap != null) {
         // 5.1 Use the pixel map created in step 4 to construct an off-screen canvas.
         const canvas_ = new drawing.Canvas(this.pixelMap);

         // 5.2 Off-screen drawing
         const brush = new drawing.Brush();
         brush.setColor({ alpha: 255, red: 0, green: 0, blue: 255 });
         canvas_.attachBrush(brush);
         canvas_.drawRect({ left: 150, right: 575, top: 0, bottom: 600 });

         // 5.3 Deliver the drawing result of the off-screen canvas to the render node.
         canvas.drawImage(this.pixelMap, 0, 0);
       }
     }
   }

   @Concurrent
   async function createPixelMapAsync() {
     // 4000000 indicates the size of the pixel buffer to be created. The value is height x width x 4.
     const color : ArrayBuffer = new ArrayBuffer(4000000);  
     let opts : image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 1000, width: 1000 } };
     const pixel = await image.createPixelMap(color, opts);
     return pixel;
   }

   // 3. Customize a NodeController.
   export class MyNodeControllerIndirectDisplay extends NodeController {
     private rootNode: FrameNode | null = null;
     private myRenderNode = new MyRenderNodeIndirectDisplay();

     // 4. Create a PixeMap in aboutToAppear of MyNodeController.
     aboutToAppear(): void {
       let task = new taskpool.Task(createPixelMapAsync);
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

6. Display the custom NodeController.
   ```ts
   // CanvasGetResult.ets
   @Entry
   @Component
   struct RenderTest {
     @State message: string = 'hello';
     myNodeController_1 = new MyNodeControllerDirectDisplay();
     myNodeController_2 = new MyNodeControllerIndirectDisplay();

     build() {
       Row() {
         Column() {
           Column(){
             Text($r('app.string.DirectCanvas'))
             // Display the canvas on the screen.
             NodeContainer(this.myNodeController_1)
               .width('100%')
               .height('40%')
           }
           Column(){
             Text($r('app.string.OffScreenCanvas'))
             // Off-screen canvas
             NodeContainer(this.myNodeController_2)
               .width('100%')
               .height('40%')
               .margin({ top: 20 })
           }
         }
       }
     }
   }
   ```
   <!-- [arkts_graphics_draw_direct_and_indirect_canvas](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Drawing/ArkTSGraphicsDraw/entry/src/main/ets/drawing/pages/CanvasGetResult.ets) -->

<!--RP1-->
## Samples

The following samples can be used as references for Drawing (ArkTS) development:

- [ArkTSGraphicsDraw (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Drawing/ArkTSGraphicsDraw)
<!--RP1End-->
