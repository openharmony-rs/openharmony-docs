# ArkTS1.1使用ArkTS1.2对象

## 概述

从API version 20开始，[RenderNode](../reference/apis-arkui/js-apis-arkui-renderNode.md)，[FrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md)，[UIContext](../reference/apis-arkui/js-apis-arkui-UIContext.md)，[Resource](../reference/apis-arkui/arkui-ts/ts-types.md)，[ShapeClip](../reference/apis-arkui/js-apis-arkui-graphics.md#shapeclip12)，[LengthMetrics](../reference/apis-arkui/js-apis-arkui-graphics.md#lengthmetrics12)，[ColorMetrics](../reference/apis-arkui/js-apis-arkui-graphics.md#colormetrics12)，[ShapeMask](../reference/apis-arkui/js-apis-arkui-graphics.md#shapemask12) 对象互操作适用于[ArkTS1.2互操作](../quick-start/arkts-interop-overview.md)中使用。

**限制条件**

- 遵循语言[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)的规范。

## 项目架构

```text
project/
├── entry/          # ArkTS1.1主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
└── library2/         # ArkTS1.2子模块
    └── src/
       ├── main/
       │     └── ets/
       │        └── components/
       │          └── MainPage.ets
       └── Index.ets
```

- 创建ArkTS1.2子模块`library2`，在`library/src/main/ets/components`目录创提创建ArkTS1.2对象并转换为ArkTS1.1对象返回。

  ```TypeScript
  'use static'
  // library2/src/main/ets/components/MainPage.ets

  import transfer from '@ohos.transfer';

  export function xxxObjectTrans():Object {
    // todo 创建ArkTS1.1对象
    let staticObject:XXXObject = new XXXObject();
     //通过互操作接口转换为对应的ArkTS1.2对象 转换的参数类型
    let xxxObjectDynamic = transfer.transferDynamic(xxxObject, 'ArkUI.XXXobject');
     // 返回 ArkTS1.1对象
     return xxxObjectDynamic!;
  }
  ```
- 导出MainPage.ets中定义的方法。

  ```TypeScript
  'use static'
  // library2/Index.ets

  export { xxxObjectTrans } from './src/main/ets/components/MainPage';
  ```


- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
    "library2": "file:../library2"
  }
  ```

- 在ArkTS1.1主模块中引入ArkTS1.2模块创建的对象对象。

  ```TypeScript
  // entry/src/main/ets/pages/Index.ets

  import { xxxObjectTrans } from 'library2';

  function xxxObjectTransTest(): XXXobject{
    let xxxObject = xxxObjectTrans();
    // 转换为ArKTS1.1对象
    let xxxObjectDynamic = xxxObject as XXXobject;
    return xxxObjectDynamic;
  }
  ```
## 对象类型

### ArkTS1.1中使用ArkTS1.2FrameNode对象类型

通过在ArkTS1.1中引用ArkTS1.1创建的FrameNode对象显示蓝色正方形。


- 创建ArkTS1.2子模块`library`，在`library2/src/main/ets/components`目录创提创建ArkTS1.1FrameNode的方法。

  ```TypeScript
  'use static'
  // library2/src/main/ets/components/MainPage.ets

  import { typeNode, FrameNode } from '@ohos.arkui.node';
  import { UIContext } from '@ohos.arkui.UIContext';
  import transfer from '@ohos.transfer';

  export function createFrameNode(context:Object): Object {
    let uiContextStatic =transfer.transferStatic(context, 'ArkUI.UIContext');
    let uiContext:UIContext = uiContextStatic as UIContext;
    let rootNode = new FrameNode(uiContext);
    rootNode.commonAttribute.backgroundColor('#ff0000ff');
    rootNode.commonAttribute.size({width:100,height:100});
    let rootNodeDynamic =transfer.transferDynamic(rootNode, 'ArkUI.FrameNode');
    return rootNodeDynamic! as Object;
  }
  ```

- 在ArkTS1.1主模块中引入ArkTS1.2创建的FrameNode对象。

  ```TypeScript
  import {NodeController ,FrameNode, typeNode } from '@kit.ArkUI';
  import { createFrameNode } from 'library2';
  
  export function FrameNodeTrans(uiContext:UIContext):FrameNode {
    let rootNode = createFrameNode(uiContext);
    return rootNode as FrameNode;
  }
  
  class TestNodeController extends NodeController {
    makeNode(uiContext:UIContext):FrameNode|null {
      let rootNode = new FrameNode(uiContext);
      rootNode.commonAttribute.width(100);
      rootNode.commonAttribute.height(100);
      let child1 = FrameNodeTrans(uiContext);
      rootNode.appendChild(child1);
      return rootNode;
    }
  }
  
  @Entry
  @Component
  struct MyStateSample {
    nodeController: TestNodeController = new TestNodeController();
    build() {
      Column(undefined) {
        NodeContainer(this.nodeController).width(100).height(100).border({width:1}).margin(10)
      }
    }
  }
  ```
  ![image](figures/frameNodeTransferDynamic.png)
  
### ArkTS1.2中使用ArkTS1.1RenderNode对象类型

- 创建ArkTS1.2子模块`library2`，在`library/src/main/ets/components`目录创提创建ArkTS1.1RenderNode的方法。

  ```TypeScript
  'use static'
  // library/src/main/ets/components/MainPage.ets

  import { RenderNode } from '@ohos.arkui.node';
  import transfer from '@ohos.transfer';

  export function renderNodeTest(): Object {
    let renderNodeTest =new RenderNode();
    renderNodeTest.position = { x: 0, y: 0 };
    renderNodeTest.size = { width: 80, height: 80 }
    renderNodeTest.backgroundColor = 0xff0000ff;
    let renderNodeDynamic = transfer.transferDynamic(renderNodeTest, 'ArkUI.RenderNode');
    let ret = renderNodeDynamic! as Object;
    return ret;
  }
  ```

- 在ArkTS1.1主模块中引入ArkTS1.1 RenderNode对象。

  ```TypeScript
  // entry/src/main/ets/pages/Index.ets
  
  import { FrameNode, RenderNode, NodeController } from '@kit.ArkUI';
  import { renderNodeTest } from 'library2';
  
  function renderNodeTrans(): RenderNode{
    let renderNode = renderNodeTest();
    let renderNodeDynamic = renderNode as RenderNode;
    return renderNodeDynamic;
  }
  
  class TestNodeController extends NodeController {
    makeNode(uiContext: UIContext): FrameNode | null {
      let rootNode = new FrameNode(uiContext);
      rootNode.commonAttribute.width(100);
      rootNode.commonAttribute.height(100);
  
      const rootRenderNode = rootNode?.getRenderNode();
      if (rootRenderNode !== null) {
        rootRenderNode?.appendChild(renderNodeTrans());
      }
      return rootNode;
    }
  }
  
  @Entry
  @Component
  struct MyStateSample {
    nodeController: TestNodeController = new TestNodeController();
  
    build() {
      Column(undefined) {
        NodeContainer(this.nodeController).width(100).height(100)
      }
    }
  }
  ```
  ![image](figures/renderNodeTransfer.png) 

### ArkTS1.2中使用ArkTS1.1LengthMetrics、ColorMetrics、ShapeMask、ShapeClip对象类型

- 创建ArkTS1.2子模块`library2`，在`library2/src/main/ets/components`目录创提创建ArkTS1.1LengthMetrics、ColorMetrics、shapeMask、shapeClip的方法。

  ```TypeScript
  // library2/src/main/ets/components/MainPage.ets
  'use static'
  
  import { ShapeClip, ColorMetrics, ShapeMask, LengthMetrics, RenderNode, RoundRect } from '@ohos.arkui.node';
  import transfer from '@ohos.transfer';
  
  export function shapeMaskTest(): Object {
    const mask = new ShapeMask();
    const roundRect: RoundRect = {
      rect: {
        left: 0,
        top: 0,
        right: 100,
        bottom: 100
      },
      corners: {
        topLeft: { x: 50, y: 50 },
        topRight: { x: 50, y: 50 },
        bottomLeft: { x: 50, y: 50 },
        bottomRight: { x: 50, y: 50 }
      }
    }
    mask.setRoundRectShape(roundRect);
    mask.fillColor = 0X50FF0000;
    let maskDynamic = transfer.transferDynamic(mask, 'ArkUI.ShapeMask');
    return mask! as Object;
  }
  
  export function shapeClipTest(): Object {
    let shapeClip = new ShapeClip();
    shapeClip.setCommandPath({ commands: "M100 0 L0 100 L50 200 L150 200 L200 100 Z" });
    let shapeClipDynamic = transfer.transferDynamic(shapeClip, 'ArkUI.ShapeClip');
    return shapeClipDynamic! as Object;
  }
  
  export function colorMetricsTest(): Object {
    let ret = ColorMetrics.numeric(10);
    let colorMetrics = transfer.transferDynamic(ret, 'ArkUI.ColorMetrics');
    return colorMetrics! as Object;
  }
  
  export function lengthMetricsTest(): Object {
    let ret = LengthMetrics.px(30);
    let lengthMetrics = transfer.transferDynamic(ret, 'ArkUI.LengthMetrics');
    return lengthMetrics! as Object;
  }
  ```

- 在ArkTS1.2主模块中引入ArkTS1.1导出的方法创建对象并转换为ArkTS1.2对象。

  ```TypeScript
   // entry/src/main/ets/pages/Index.ets

   import {NodeController, FrameNode, LengthUnit, ShapeClip, ColorMetrics, ShapeMask, RenderNode, LengthMetrics, RoundRect } from '@kit.ArkUI';
   import { lengthMetricsTest, colorMetricsTest, shapeMaskTest, shapeClipTest } from 'library2';
  
  
    const shapeClipTestNode: RenderNode = new RenderNode()
    // 初始化RenderNode
    shapeClipTestNode.position = { x: 0, y: 80 };
    shapeClipTestNode.size = { width: 80, height: 80 }
    shapeClipTestNode.backgroundColor = 0xff0000ff;
  
   const shapeMaskTestNode: RenderNode = new RenderNode()
   // 初始化RenderNode
   shapeMaskTestNode.position = { x: 0, y: 0 };
   shapeMaskTestNode.size = { width: 80, height: 80 }
   shapeMaskTestNode.backgroundColor = 0xff0000ff;
  
    // ShapeMask ShapeClip 对象转换
    export function shapeTrans(rootNode: FrameNode) {
      // 调用ArkTS1.1方法获取ShapeMask对象
      let shapeMask = shapeMaskTest();
      // 调用ArkTS1.1方法获取ShapeClip对象
      let shapeClip = shapeClipTest();
      let shapeClipStatic = shapeClip as ShapeClip;
      let shapeMaskStatic = shapeMask as ShapeMask;
      const rootRenderNode = rootNode?.getRenderNode();
      if (rootRenderNode !== null) {
        shapeMaskTestNode.shapeMask = shapeMaskStatic;
        shapeClipTestNode.shapeClip = shapeClipStatic;
        rootRenderNode?.appendChild(shapeMaskTestNode);
        rootRenderNode?.appendChild(shapeClipTestNode);
      }
    }
    // ColorMetrics对象互操作
    function colorMetricsTrans():ColorMetrics {
      return colorMetricsTest() as ColorMetrics;
    }
    // lengthMetrics对象互操作
    function lengthMetricsTrans(): LengthMetrics {
      return lengthMetricsTest() as LengthMetrics;
    }
    class TestNodeController extends NodeController {
      makeNode(uiContext: UIContext): FrameNode | null {
        let rootNode = new FrameNode(uiContext);
        shapeTrans(rootNode);
        return rootNode;
      }
    }
    @Entry
    @Component
    struct MyStateSample {
      nodeController: TestNodeController = new TestNodeController();
  
      build() {
        Column(undefined) {
          NodeContainer(this.nodeController)
            .size({width:200, height:200})
            .border({width:1})
          Button("test Button").focusBox({
            margin: LengthMetrics.px(20),
            strokeColor: colorMetricsTrans(),
            strokeWidth: lengthMetricsTrans()
          }).margin(30)
        }
      }
  }
  ```
  ![image](figures/graphicsTransfer.png)

  ### ArkTS1.2中使用ArkTS1.1Resource对象类型

  通过在ArkTS1.2中引用ArkTS1.1创建的Resource对象显示图片。

- 创建ArkTS1.1子模块`library2`，在`library2/src/main/ets/components`目录创提创建ArkTS1.1Resource的方法。

  ```TypeScript
    'use static'
  // library2/src/main/ets/components/MainPage.ets

  import transfer from '@ohos.transfer';
  import {$rawfile, $r} from '@ohos.arkui.component'
  import hilog from '@ohos.hilog'
  export function rawFileTest() {
    let rawFile = $rawfile('startIcon.png');
    let dynamicRawFile = transfer.transferDynamic(rawFile, 'Global.Resource');
    return dynamicRawFile! as Object;
  }
  export function resourceTest(): Object {
    let resource = $r('app.float.image_size');
    let dynamicResource = transfer.transferDynamic(resource, 'Global.Resource');
    return dynamicResource! as Object;
  }
  ```

- 在ArkTS1.2主模块中引入ArkTS1.1 Resource对象。

  ```TypeScript
  import { resourceTest, rawFileTest } from 'library2';
  // Resource $r对象互操作
  export function resourceTrans(): Resource {
    return  resourceTest() as Resource;
  }
  // Resource RawFile对象互操作
  export function rawFileTrans(): Resource {
     return rawFileTest() as Resource;
  }

  @Entry
  @Component
  struct MyStateSample {
    build() {
      Column(undefined) {
        Image(rawFileTrans())
          .size({width:resourceTrans(), height:resourceTrans()})
      }
    }
  }
  ```
  ![image](figures/resourceTransfer.png)

  ### 在ArkTS1.2中使用ArkTS1.1获取的UIContext对象

- 创建ArkTS1.2子模块`library2`，在`library2/src/main/ets/components`目录创提使用传入的UIContext用于逻辑处理。

  ```TypeScript
  'use static'
  // library2/src/main/ets/components/MainPage.ets

  import transfer from '@ohos.transfer';
  import { UIContext } from '@ohos.arkui.UIContext';

  const vpTest:number = 200;
  export function uiContextTest(uiContext:Object): number {
    let uiContextTrans = transfer.transferStatic(uiContext, 'ArkUI.UIContext');
    let uiContextStatic = uiContextTrans! as UIContext;
    return uiContextStatic.px2vp(vpTest);
  }
  ```
  
- 在ArkTS1.1主模块中获取UIContext并传递给ArkTS1.2。

  ```TypeScript
  // entry/src/main/ets/pages/Index.ets
  
  import { uiContextTest } from 'library2';
  import { UIContext } from '@kit.ArkUI';
  
  // uiContext互操作
  export function uiContextTrans(uiContext:UIContext): number {
    return uiContextTest(uiContext);
  }
  
  @Entry
  @Component
  struct MyStateSample {
    build() {
      Column(undefined) {
        Column()
          .backgroundColor('#ff0000ff')
          .size({width:uiContextTrans(this.getUIContext()), height:uiContextTrans(this.getUIContext())})
      }
    }
  }
  ```
  ![image](figures/uiContextTransfer.png)