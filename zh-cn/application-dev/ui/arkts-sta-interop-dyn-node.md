# 使用ArkTS-Dyn的自定义节点对象

## FrameNode和TypedFrameNode自定义节点

针对FrameNode和[TypedFrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#typedframenode12)类型，UI框架通过[transferStatic](../reference/apis-arkts/js-apis-transfer.md)接口将ArkTS-Dyn的基类FrameNode和子类TypedFrameNode对象转换为ArkTS-Sta的基类FrameNode对象，转换后的FrameNode对象可在ArkTS-Sta上下文中进行树构建。

如下示例代码展示了相关用法。

- 创建ArkTS-Dyn子模块dynamic_module，并在该模块中导出自定义节点创建函数。

  ```
  import { FrameNode, typeNode } from '@ohos.arkui.node';
  import { UIContext } from '@ohos.arkui.UIContext';
  
  export function createChild(context: Object): Object {
    let parent = new FrameNode(context as UIContext);
    parent.commonAttribute
      .width('100%')
      .height('100%');
    let textTypeNode = typeNode.createNode(context as UIContext, 'Text');
    textTypeNode.initialize('textTypeNode')
      .fontSize(25)
      .id('textTypeNode');
    parent.appendChild(textTypeNode);
    // 返回通用类型
    return parent;
  }
  ```

- 配置相关模块依赖后，在ArkTS-Sta模块中导入动态模块使用。

  ```
  'use static'
  import { Entry, Component, Column, NodeContainer } from '@ohos.arkui.component';
  import { FrameNode, NodeController } from '@ohos.arkui.node';
  import { UIContext } from '@ohos.arkui.UIContext';
  import transfer from '@ohos.transfer';
  import { createChild } from 'dynamic_module';
  
  class MyNodeController extends NodeController {
    makeNode(uiContext: UIContext): FrameNode | null {
      // 调用互操作接口将ArkTS-Sta的UIContext转换为ArkTS-Dyn的UIContext后调用ArkTS-Dyn接口
      let dynamicFrameNode = createChild(transfer.transferDynamic(uiContext, 'ArkUI.UIContext'));
      // 调用互操作接口将ArkTS-Dyn的FrameNode转换为ArkTS-Dyn的FrameNode类型
      return transfer.transferStatic(dynamicFrameNode, 'ArkUI.FrameNode') as FrameNode;
    }
  }
  
  @Entry
  @Component
  struct Index {
    myNodeController: MyNodeController = new MyNodeController();
  
    build() {
      Column() {
        NodeContainer(this.myNodeController)
          .width('100%')
          .height('40%')
      }
      .width('100%')
      .height('100%')
    }
  }
  ```


### 使用限制

由于 FrameNode 在 ArkTS 1.2 和 ArkTS 1.1 中存在实现差异，通过 transferStatic 接口转换得到的 FrameNode 类型仅支持部分能力，包括 UI 节点树查询和操作、获取节点大小和位置信息、解除对实体引用。其他能力，如设置属性、注册事件等无法支持，调用上述接口将导致运行时异常。

### ComponentContent声明式自定义节点

[ComponentContent](../reference/apis-arkui/js-apis-arkui-ComponentContent.md)对象主要用于作为 UI 组件相关接口的输入参数。由于 ArkTS 1.2 和 ArkTS 1.1 在动静态类型上的差异，ArkTS 1.1 的 `ComponentContent` 对象不能直接用作 ArkTS 1.2 相关接口的参数。在互操作场景下，主要通过 `@Builder` 函数实现互操作。以下示例代码展示了相关用法。

- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出ComponentContent使用的UI构建函数。

  ```
  export class Params {
    text: string = '';
    constructor(text: string) {
      this.text = text;
    }
  }
  
  // 导出ComponentContent使用的UI构建函数
  @Builder
  export function buildText(params: Params) {
    Column() {
      Text(params.text)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .margin({bottom: 36})
    }.backgroundColor('#FFF0F0F0')
  }
  ```

- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块的UI构建函数。然后，通过UI构建函数互操作创建ArkTS-Sta的ComponentContent对象。
  ```
  'use static'
  import { Entry, Component, Column, NodeContainer, Builder, ComponentContent, wrapBuilder } from '@ohos.arkui.component';
  import { FrameNode, NodeController } from '@ohos.arkui.node';
  import { UIContext } from '@ohos.arkui.UIContext';
  import { buildText, Params } from 'dynamic_module';

  // 使用UI构建互操作封装 ArkTS 1.1 的 UI 构建函数。
  @Builder
  function wrapBuildText(value: Params) {
    Column() {
      buildText(value)
    }
  }
  
  class MyNodeController extends NodeController {
    makeNode(uiContext: UIContext): FrameNode | null {
      let frameNode = new FrameNode(uiContext);
      frameNode.addComponentContent(new ComponentContent<Params>(uiContext, wrapBuilder(wrapBuildText), new Params('Hello World')));
      return frameNode;
    }
  }
  
  @Entry
  @Component
  struct Index {
    myNodeController: MyNodeController = new MyNodeController();
  
    build() {
      Column() {
        NodeContainer(this.myNodeController)
          .width('100%')
          .height('40%')
      }
      .width('100%')
      .height('100%')
    }
  }
  ```

## BuilderNode声明式自定义节点

BuilderNode 对象主要用于创建声明式自定义节点封装类，配合 FrameNode 构建 UI 组件树。在互操作场景下，主要通过 FrameNode 间接实现 BuilderNode 的互操作。以下示例代码展示了相关用法。

- 创建ArkTS-Dyn子模块dynamic_module，在动态模块中创建并导出BuilderNode对象。

  ```
  import { BuilderNode, UIContext } from '@kit.ArkUI';
  
  class Params {
    text: string = '';
    constructor(text: string) {
      this.text = text;
    }
  }
  
  @Builder
  function buildText(params: Params) {
    Column() {
      Text(params.text)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .margin({ bottom: 36 })
    }
  }
  
  // 创建BuilderNode并返回通用类型对象
  export function createTextNode(context: Object, message: string): Object {
    let builderNode = new BuilderNode<[Params]>(context as UIContext);
    builderNode.build(wrapBuilder<[Params]>(buildText), new Params(message));
    return builderNode;
  }
  ```

- 在ArkTS-Sta模块中配置相关模块依赖后，导入动态模块创建BuilderNode函数，并通过FrameNode互操作创建ArkTS-Sta的FrameNode对象。

  ```
  'use static'
  import { Entry, Component, Column, NodeContainer } from '@ohos.arkui.component';
  import { FrameNode, NodeController } from '@ohos.arkui.node';
  import { UIContext } from '@ohos.arkui.UIContext';
  import transfer from '@ohos.transfer';
  import { createTextNode } from 'dynamic_module';
  
  class TextNodeController extends NodeController {
    private textNode?: Any; // 接收ArkTS-Dyn的通用类型对象。
    private message: string = 'DEFAULT'; // 传递给ArkTS-Dyn对象的参数数据。
  
    constructor(message: string) {
      super();
      this.message = message;
    }
  
    makeNode(context: UIContext): FrameNode | null {
      // 将转换后的UIContext和消息传递给createTextNode方法
      this.textNode = createTextNode(transfer.transferDynamic(context, 'ArkUI.UIContext'), this.message);
      // 通过ESValue接口获取ArkTS-Dyn的FrameNode对象。
      let dynamicFrameNode = ESValue.wrap(this.textNode).invokeMethod('getFrameNode');
      // 将转换后的FrameNode对象返回
      return transfer.transferStatic(dynamicFrameNode.unwrap(), 'ArkUI.FrameNode') as FrameNode;
    }
  }
  
  @Entry
  @Component
  struct Index {
    myNodeController: TextNodeController = new TextNodeController('Hello World');
  
    build() {
      Column() {
        NodeContainer(this.myNodeController)
          .width('100%')
          .height(100)
      }
      .width('100%')
      .height('100%')
    }
  }
  ```
