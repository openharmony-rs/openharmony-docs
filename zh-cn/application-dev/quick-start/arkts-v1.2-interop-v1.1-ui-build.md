# UI构建互操作

## 介绍

在ArkTS1.2中使用ArkTS1.1 UI模块的场景主要包括：

- 在ArkTS1.2的自定义组件的[build](../ui/state-management/arkts-create-custom-components.md)成员函数，使用[\@Builder](../ui/state-management/arkts-builder.md)装饰的函数可以调用ArkTS1.1的自定义组件。
- 在ArkTS1.2的自定义组件build成员函数，使用\@Builder装饰的函数可以调用ArkTS1.1的使用\@Builder装饰的函数和[WrappedBuilder](../ui/state-management/arkts-wrapBuilder.md)对象。
- 在ArkTS1.2使用ArkTS1.1自定义组件时，为对应自定义组件中的使用[\@BuilderParam](../ui/state-management/arkts-builderparam.md)装饰的成员赋值。
- 在ArkTS1.2中使用ArkTS1.1自定义节点对象，如[FrameNode](../ui/arkts-user-defined-arktsNode-frameNode.md)，[BuilderNode](../ui/arkts-user-defined-arktsNode-builderNode.md)。

## 使用ArkTS1.1的自定义组件

ArkUI互操作能力支持静态上下文使用动态模块的自定义组件，包括创建并传递参数。

以下示例展示了如何在静态上下文中使用动态模块的自定义组件。

- 创建ArkTS1.1子模块dynamic_module，并在动态模块中创建和导出自定义组件。如何创建子模块参考共享包（[HAR](har-package.md)）说明。

  ```
  @Component
  export struct HelloComponent {
    @State message: string = 'Hello, World!';
  
    build() {
      Row() {
        Text(this.message)
          .onClick(() => {
            this.message = 'Hello, ArkUI!';
          })
      }
    }
  }
  ```

- 在ArkTS1.2主模块中配置相关模块依赖后，导入动态模块的自定义组件。如何导入和使用子模块参考共享包（[HAR](har-package.md)）说明。

  ```
  'use static'
  import { Entry, Component, Builder, Column, Divider, BuilderParam } from '@ohos.arkui.component';
  import { HelloComponent } from 'dynamic_module'; // 从动态模块中导入

  @Entry
  @Component
  struct ParentComponent {
    @Builder
    localBuilder() {
      HelloComponent({ message: 'Hello Local' }) // 支持在@Builder函数中使用动态类型的自定义组件。
    }
    @BuilderParam content: () => void = this.localBuilder;
  
    build() {
      Column() {
        HelloComponent({ message: 'Hello World!' }) // 支持在自定义组件build函数中使用动态类型的自定义组件
        Divider()
        this.content()
      }
    }
  }
  ```

### 规格限制

- 静态上下文的自定义组件build函数可以使用动态类型自定义组件。

- 静态上下文的\@Builder函数可以使用动态类型自定义组件。

- 在静态上下文中，可以初始化动态类型自定义组件的内部成员对象。关于状态变量的初始化规则，请参见状态管理互操作。

- 在静态上下文中，不能对动态类型的自定义组件设置通用样式，否则会导致编译错误。
  ```
  'use static'
  import { Entry, Component, Stack, Column } from '@ohos.arkui.component';
  import { HelloComponent } from 'dynamic_module'; // 从动态模块中导入
  
  @Entry
  @Component
  struct ParentComponent {
  
    build() {
      Column() {
        // 不支持对动态自定义组件设置通用样式，如下代码将产生编译报错。
        HelloComponent({ message: 'Hello World!' })
          .width(100)
          .height(100)
  
        // 开发者可以通过嵌套一个Stack组件，将通用样式设置在Stack组件上。
        Stack() {
          HelloComponent({ message: 'Hello World!' })
        }.width(100).height(100)
      }
    }
  }
  ```

- 静态上下文中不支持通过@Reusable装饰器来使能动态类型自定义组件的回收复用。

## 使用ArkTS1.1的\@Builder函数

ArkUI互操作能力支持在静态上下文中使用动态模块的\@Builder函数，使用规格限制与非互操作场景相同。

以下示例展示在静态上下文中使用动态模块的\@Builder函数。


- 创建ArkTS1.1子模块dynamic_module，在动态模块中创建并导出\@Builder函数。

  ```
  @Builder
  export function showTextBuilder() {
    Text('Hello World')
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }
  ```


- 在ArkTS1.2模块中配置相关模块依赖后，导入动态模块的\@Builder函数使用。

  ```
  'use static'
  import { Entry, Component, Column, Divider, Builder, BuilderParam } from '@ohos.arkui.component';
  import { showTextBuilder } from 'dynamic_module';
  
  @Builder
  function wrapTextBuilder() {
    showTextBuilder() // 支持在@Builder函数中直接使用。
  }
  
  @Entry
  @Component
  struct BuilderDemo {
    // 通过ArkTS1.2的Builder函数封装后赋值给@BuilderParam。
    @BuilderParam content: ()=>void = wrapTextBuilder;
  
    @Builder
    localBuilder() {
      showTextBuilder() // 支持在局部@Builder函数中直接使用。
    }
  
    build() {
      Column() {
        showTextBuilder() // 支持在自定义组件build函数中直接使用。
        Divider()
        this.content()
        Divider()
        this.localBuilder()
      }
    }
  }
  ```

## 使用ArkTS1.1的WrappedBuilder对象

由于动静态类型差异，ArkTS1.1的WrappedBuilder对象类型在ArkTS1.2上下文中被转换为了Any类型，UI互操作编译工具无法对Any类型进行编译期适配优化，因此开发者需要显式调用互操作接口[compatibleWrappedBuilder](../reference/apis-arkui/arkui-ts/ts-interop-compatible-WrappedBuilder.md)来使用ArkTS1.1的WrappedBuilder对象。


以下示例展示了在ArkTS1.2上下文中使用动态WrappedBuilder对象的方法。


- 创建ArkTS1.1子模块dynamic_module，在动态模块中创建并导出WrappedBuilder对象。

  ```
  @Builder
  function textBuilder(value: string, size: number) {
    Text(value)
      .fontSize(size)
  }
  
  export const myTextBuilder: Object = wrapBuilder(textBuilder); // 使用Object类型导出。
  ```


- 在ArkTS1.2模块中配置相关模块依赖后，导入动态模块的WrappedBuilder对象。

  ```
  'use static'
  import { Entry, Component, Column, compatibleWrappedBuilder } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import { myTextBuilder } from 'dynamic_module';
  
  @Entry
  @Component
  struct Index {
    @State message: string = 'Hello World';
  
    build() {
      Column() {
        // 调用互操作接口并传入WrappedBuilder对象和参数进行UI构建。
        compatibleWrappedBuilder(myTextBuilder, ESValue.wrap(this.message), ESValue.wrap(50))
      }
    }
  }
  ```


### 规格限制

- compatibleWrappedBuilder函数建议在自定义组件的build函数或者\@Builder函数内使用。
- compatibleWrappedBuilder函数的第一个参数需要传递ArkTS 1.1的WrappedBuilder对象，传递其他类型对象会导致UI异常。
- compatibleWrappedBuilder函数支持的\@Builder函数的参数最多不超过10个，否则将引发运行时异常。

## 给ArkTS1.1自定义组件的\@BuilderParam赋值

针对 ArkTS 1.1 的自定义组件，通过 `@BuilderParam` 定制化功能模块。UI 互操作通过编译期适配优化，支持在 ArkTS 1.2 上下文中初始化 ArkTS 1.1 自定义组件的 `@BuilderParam` 成员对象。以下示例代码展示了具体用法。


- 创建ArkTS1.1子模块dynamic_module，并在该模块中导出自定义组件。

  ```
  @Component
  export struct CustomContainer {
    @Builder
    closerBuilder() {
    }
  
    @BuilderParam closer: () => void = this.closerBuilder;
  
    build() {
      Column() {
        this.closer()
      }
    }
  }
  ```


- 配置相关模块依赖后，在ArkTS1.2模块中导入动态模块的自定义组件。

  ```
  'use static'
  import { Entry, Component, Builder, Column, Text, ClickEvent, Color } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import { CustomContainer } from 'dynamic_module';
  
  @Entry
  @Component
  struct CustomContainerUser {
    @State text: string = 'header';
  
    @Builder
    localBuilder() {
      Text(this.text)
        .onClick((value: ClickEvent) => {
          this.text = 'changeHeader';
        })
    }
  
    build() {
      Column() {
        // 创建CustomContainer，在创建CustomContainer时，通过其后紧跟一个大括号“{}”形成尾随闭包
        // 作为传递给子组件CustomContainer 的 @BuilderParam 参数 closer: () => void
        CustomContainer() {
          Column() {
            Text(this.text)
          }.backgroundColor(Color.Yellow)
          .onClick((value: ClickEvent) => {
            this.text = 'changeHeader';
          })
        }
        // 通过参数初始化 @BuilderParam 成员。
        CustomContainer({closer: this.localBuilder})
      }
    }
  }
  ```

## 使用ArkTS1.1的自定义节点对象

### FrameNode和TypedFrameNode自定义节点

针对FrameNode和[TypedFrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#typedframenode12)类型，UI框架通过[transferStatic](../reference/apis-arkts/js-apis-transfer.md)接口将ArkTS1.1的基类FrameNode和子类TypedFrameNode对象转换为ArkTS1.2的基类FrameNode对象，转换后的FrameNode对象可在ArkTS1.2上下文中进行树构建。

如下示例代码展示了相关用法。

- 创建ArkTS1.1子模块dynamic_module，并在该模块中导出自定义节点创建函数。

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

- 配置相关模块依赖后，在ArkTS1.2模块中导入动态模块使用。

  ```
  'use static'
  import { Entry, Component, Column, NodeContainer } from '@ohos.arkui.component';
  import { FrameNode, NodeController } from '@ohos.arkui.node';
  import { UIContext } from '@ohos.arkui.UIContext';
  import transfer from '@ohos.transfer';
  import { createChild } from 'dynamic_module';
  
  class MyNodeController extends NodeController {
    makeNode(uiContext: UIContext): FrameNode | null {
      // 调用互操作接口将ArkTS1.2的UIContext转换为ArkTS1.1的UIContext后调用ArkTS1.1接口
      let dynamicFrameNode = createChild(transfer.transferDynamic(uiContext, 'ArkUI.UIContext'));
      // 调用互操作接口将ArkTS1.1的FrameNode转换为ArkTS1.1的FrameNode类型
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


#### 使用限制

由于 FrameNode 在 ArkTS 1.2 和 ArkTS 1.1 中存在实现差异，通过 transferStatic 接口转换得到的 FrameNode 类型仅支持部分能力，包括 UI 节点树查询和操作、获取节点大小和位置信息、解除对实体引用。其他能力，如设置属性、注册事件等无法支持，调用上述接口将导致运行时异常。

### ComponentContent声明式自定义节点

[ComponentContent](../reference/apis-arkui/js-apis-arkui-ComponentContent.md)对象主要用于作为 UI 组件相关接口的输入参数。由于 ArkTS 1.2 和 ArkTS 1.1 在动静态类型上的差异，ArkTS 1.1 的 `ComponentContent` 对象不能直接用作 ArkTS 1.2 相关接口的参数。在互操作场景下，主要通过 `@Builder` 函数实现互操作。以下示例代码展示了相关用法。

- 创建ArkTS1.1子模块dynamic_module，在动态模块中创建并导出ComponentContent使用的UI构建函数。

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

- 在ArkTS1.2模块中配置相关模块依赖后，导入动态模块的UI构建函数。然后，通过UI构建函数互操作创建ArkTS1.2的ComponentContent对象。
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

### BuilderNode声明式自定义节点

BuilderNode 对象主要用于创建声明式自定义节点封装类，配合 FrameNode 构建 UI 组件树。在互操作场景下，主要通过 FrameNode 间接实现 BuilderNode 的互操作。以下示例代码展示了相关用法。

- 创建ArkTS1.1子模块dynamic_module，在动态模块中创建并导出BuilderNode对象。

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

- 在ArkTS1.2模块中配置相关模块依赖后，导入动态模块创建BuilderNode函数，并通过FrameNode互操作创建ArkTS1.2的FrameNode对象。

  ```
  'use static'
  import { Entry, Component, Column, NodeContainer } from '@ohos.arkui.component';
  import { FrameNode, NodeController } from '@ohos.arkui.node';
  import { UIContext } from '@ohos.arkui.UIContext';
  import transfer from '@ohos.transfer';
  import { createTextNode } from 'dynamic_module';
  
  class TextNodeController extends NodeController {
    private textNode?: Any; // 接收ArkTS1.1的通用类型对象。
    private message: string = 'DEFAULT'; // 传递给ArkTS1.1对象的参数数据。
  
    constructor(message: string) {
      super();
      this.message = message;
    }
  
    makeNode(context: UIContext): FrameNode | null {
      // 将转换后的UIContext和消息传递给createTextNode方法
      this.textNode = createTextNode(transfer.transferDynamic(context, 'ArkUI.UIContext'), this.message);
      // 通过ESValue接口获取ArkTS1.1的FrameNode对象。
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
