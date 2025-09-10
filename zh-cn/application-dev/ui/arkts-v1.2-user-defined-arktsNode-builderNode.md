# 自定义声明式节点 (BuilderNode)（ArkTS1.2）

## 概述

从API version 20开始，自定义声明式节点（[BuilderNode](../reference/apis-arkui/js-apis-arkui-builderNode-static.md)）提供挂载系统组件的能力，支持无状态的UI方式。通过[全局自定义构建函数](../ui/state-management/arkts-builder.md#全局自定义构建函数) @Builder 定制组件树。组件树的根节点[FrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md) 可通过[getFrameNode](../reference/apis-arkui/js-apis-arkui-builderNode-static.md#getframenode) 获取。该节点可由[NodeController](../reference/apis-arkui/js-apis-arkui-nodeController.md) 返回并挂载于[NodeContainer](../reference/apis-arkui/arkui-ts/ts-basic-components-nodecontainer.md) 节点下，或在FrameNode树与[RenderNode](../reference/apis-arkui/js-apis-arkui-renderNode.md) 树中嵌入声明式组件，实现混合显示。

由BuilderNode构建的ArkTS组件树支持与自定义节点（如FrameNode、RenderNode）关联使用，确保系统组件与自定义节点的混合显示。此外，对于需与自定义节点对接的第三方框架，BuilderNode提供了嵌入系统组件的方法。

BuilderNode 提供了组件预创建功能，可以自定义系统组件的创建时机。此功能特别适用于初始化耗时较长的声明式组件，通过预创建，可显著减少初始化时间，优化加载效率。

## 基本概念

- 系统组件：组件是UI的必要元素，形成了在界面中的样子，由ArkUI直接提供的称为[系统组件](arkts-ui-development-overview.md)。

- 实体节点：由后端创建的Native节点。

BuilderNode仅可作为叶子节点进行使用。如有更新需要，建议使用BuilderNode中的[update](../reference/apis-arkui/js-apis-arkui-builderNode-static.md#update)方式触发更新，不建议使用BuilderNode中获取的RenderNode对节点进行修改操作。

> **说明：**
>
> - BuilderNode只支持一个由[wrapBuilder](../ui/state-management/arkts-v1.2-wrapBuilder.md)包装的[全局自定义构建函数](../ui/state-management/arkts-builder.md#全局自定义构建函数)@Builder。
>
> - 新建的BuilderNode在[build](../reference/apis-arkui/js-apis-arkui-builderNode-static.md#build)之后，才能通过[getFrameNode](../reference/apis-arkui/js-apis-arkui-builderNode-static.md#getframenode)获取到指向根节点的FrameNode对象；否则，返回null。
>
> - 如果传入的Builder的根节点为未设置通用样式的[自定义组件](./state-management/arkts-create-custom-components.md#创建自定义组件)、[ContentSlot](../../application-dev/ui/state-management/arkts-rendering-control-contentslot.md#contentslot混合开发)、[LazyForEach](../../application-dev/ui/state-management/arkts-v1.2-rendering-control-lazyforeach.md)、[Repeat](../../application-dev/ui/state-management/arkts-v1.2-rendering-control-repeat.md)(全量加载模式)、[ForEach](../../application-dev/ui/state-management/arkts-v1.2-rendering-control-foreach.md)、[if/else](../../application-dev/ui/state-management/arkts-rendering-control-ifelse.md)，需要额外生成一个FrameNode。在节点树中显示为“BuilderProxyNode”。
>
> - 不支持根节点为[懒加载模式](../../application-dev/ui/state-management/arkts-v1.2-rendering-control-repeat.md#默认懒加载)的repeat节点。
>
> - 如果BuilderNode挂载在FrameNode或者NodeContainer组件上，则使用父节点的布局约束进行布局。
>
> - 如果BuilderNode的FrameNode通过[getRenderNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#getrendernode)形式将自己的节点挂载在RenderNode节点上，由于其FrameNode未上树，其大小默认为0，需要通过构造函数中的[selfIdeaSize](../reference/apis-arkui/js-apis-arkui-builderNode.md#renderoptions)显式指定布局约束大小。
>
> - BuilderNode的预加载并不会减少组件的创建时间。Web组件创建的时候需要在内核中加载资源，预创建不能减少Web组件的创建的时间，但是可以让内核进行预加载，减少正式使用时候内核的加载耗时。

## 创建BuilderNode对象

BuilderNode对象为一个模板类，需要在创建的时候指定类型。该类型需要与后续build方法中传入的[WrappedBuilder](../ui/state-management/arkts-v1.2-wrapBuilder.md)的类型保持一致，否则会存在编译告警导致编译失败。

## 创建组件树

通过BuilderNode的build方法，依据传入的WrappedBuilder对象创建组件树并持有其根节点。

> **说明：**
>
> 无状态的UI方法全局@Builder最多拥有一个根节点。
>
> build方法中对应的@Builder最多支持一个参数作为入参。
>
> 需要操作BuilderNode中的对象时，必须保证其引用不被回收。如果BuilderNode对象被虚拟机回收，它的FrameNode和RenderNode对象也会与后端节点解引用，导致从BuilderNode中获取的FrameNode对象不再对应任何节点。

创建离线节点和组件树，结合FrameNode使用。

BuilderNode的根节点直接作为[NodeController](../reference/apis-arkui/js-apis-arkui-nodeController.md)的[makeNode](../reference/apis-arkui/js-apis-arkui-nodeController.md#makenode)返回值。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode } from '@ohos.arkui.node';

class Params {
  text: string = "";

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
  }
}

class TextNodeController extends NodeController {
  private textNode: BuilderNode<Params> | null = null;
  private message: string = "DEFAULT";

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    this.textNode = new BuilderNode<Params>(context);
    this.textNode!.build(wrapBuilder(buildText), new Params(this.message));
    return this.textNode!.getFrameNode();
  }
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        NodeContainer(new TextNodeController(this.message))
          .width('100%')
          .height(100)
          .backgroundColor('#FFF0F0F0')
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

结合使用BuilderNode和RenderNode。

将BuilderNode的RenderNode挂载到其他RenderNode下时，需要显式指定[selfIdeaSize](../reference/apis-arkui/js-apis-arkui-builderNode.md#renderoptions)的大小作为BuilderNode的布局约束。不建议采用这种方式挂载节点。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight
} from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode, RenderNode } from '@ohos.arkui.node';

class Params {
  text: string = "";

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
  }
}

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private textNode: BuilderNode<Params> | null = null;
  private message: string = "DEFAULT";

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    let renderNode = new RenderNode();
    renderNode.clipToFrame = false;
    this.textNode = new BuilderNode<Params>(context, { selfIdealSize: { width: 150, height: 150 } });
    this.textNode?.build(wrapBuilder(buildText), new Params(this.message));
    const textRenderNode = this.textNode?.getFrameNode()?.getRenderNode();
    const rootRenderNode = this.rootNode?.getRenderNode();
    if (rootRenderNode !== null && textRenderNode) {
      rootRenderNode!.appendChild(renderNode);
      renderNode.appendChild(textRenderNode!);
    }
    return this.rootNode!;
  }
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        NodeContainer(new TextNodeController(this.message))
          .width('100%')
          .height(100)
          .backgroundColor('#FFF0F0F0')
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

## 更新组件树

通过BuilderNode对象的build创建组件树。依照传入的WrappedBuilder对象创建组件树，并持有组件树的根节点。

自定义组件的更新遵循[状态管理](../ui/state-management/arkts-state-management-overview.md)的更新机制。WrappedBuilder中直接使用的自定义组件其父组件为BuilderNode对象。因此，更新子组件即WrappedBuilder中定义的自定义组件，需要遵循状态管理的定义将相关的状态变量定义为[\@Prop](../ui/state-management/arkts-prop.md)或者[\@ObjectLink](../ui/state-management/arkts-observed-and-objectlink.md)。装饰器的选择请参照状态管理的装饰器规格结合应用开发需求进行选择。

使用update更新BuilderNode中的节点。

使用[updateConfiguration](../reference/apis-arkui/js-apis-arkui-builderNode-static.md#updateconfiguration12)触发BuilderNode中节点的全量更新。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight,
  ClickEvent,
  Button,
  Color
} from '@ohos.arkui.component';
import { State, Prop } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode, RenderNode } from '@ohos.arkui.node';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

// 自定义组件
@Component
struct TextBuilder {
  @Prop message: string = "TextBuilder";

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .backgroundColor(Color.Gray)
      }
    }
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
    TextBuilder({ message: params.text }) // 自定义组件
  }
}

class TextNodeController extends NodeController {
  private textNode: BuilderNode<Params> | null = null;
  private message: string = "";

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    this.textNode = new BuilderNode<Params>(context);
    this.textNode!.build(wrapBuilder(buildText), new Params(this.message));
    return this.textNode!.getFrameNode()!;
  }

  update(message: string) {
    if (this.textNode !== null) {
      this.textNode!.update(new Params(message));
    }
  }
}

@Entry
@Component
struct Index {
  @State message: string = "hello";
  private textNodeController: TextNodeController = new TextNodeController(this.message);
  private count: number = 0;

  build() {
    Row() {
      Column() {
        NodeContainer(this.textNodeController)
          .width('100%')
          .height(200)
          .backgroundColor('#FFF0F0F0')
        Button('Update')
          .onClick((event: ClickEvent) => {
            this.count += 1;
            const message = "Update " + this.count.toString();
            this.textNodeController.update(message);
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

## 解除实体节点引用关系

由于BuilderNode对应的是后端的实体节点，正常的内存释放依赖前端对象的回收。如果期望直接释放BuilderNode对后端节点的引用，则可以通过调用[dispose](../reference/apis-arkui/js-apis-arkui-builderNode-static.md#dispose12)解除引用关系，此时持有的前端BuilderNode对象不再影响后端节点的生命周期。

> **说明：**
>
> 在BuilderNode对象调用dispose之后，不仅BuilderNode对象与后端实体节点解除引用关系，BuilderNode中的FrameNode与RenderNode也会同步和实体节点解除引用关系。
>
> 如果BuilderNode对象无法释放，则可能导致内存泄漏。建议在不再需要对该BuilderNode对象进行操作时，主动调用dispose释放与后端节点的引用关系，以减少引用关系的复杂性，降低内存泄漏的风险。

## 通过系统环境变化更新节点

使用[updateConfiguration](../reference/apis-arkui/js-apis-arkui-builderNode-static.md#updateconfiguration12)监听[系统环境变化](../reference/apis-ability-kit/js-apis-app-ability-configuration.md)事件，以触发节点的全量更新。

> **说明：**
>
> updateConfiguration接口用于通知对象进行更新，更新所使用的系统环境取决于应用当前系统环境的变化。

```ts
import {
  Text,
  Column,
  Component,
  UIContext,
  Builder,
  Entry,
  Row,
  wrapBuilder,
  NodeContainer,
  FontWeight,
  ClickEvent,
  Button,
  Color,
  $r
} from '@ohos.arkui.component';
import { State, Prop } from '@ohos.arkui.stateManagement';
import { NodeController, BuilderNode, FrameNode, RenderNode } from '@ohos.arkui.node';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

// 自定义组件
@Component
struct TextBuilder {
  // 作为自定义组件中需要更新的属性，数据类型为基础属性，定义为@Prop
  @Prop message: string = "TextBuilder";

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
    }
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
    TextBuilder({ message: params.text }) // 自定义组件
  }.backgroundColor($r('sys.color.ohos_id_color_background'))
}

class TextNodeController extends NodeController {
  private textNode: BuilderNode<Params> | null = null;
  private message: string = "";

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    return this.textNode?.getFrameNode() ? this.textNode!.getFrameNode()! : null;
  }

  createNode(context: UIContext): void {
    this.textNode = new BuilderNode<Params>(context);
    this.textNode!.build(wrapBuilder(buildText), new Params(this.message));
    builderNodeMap.push(this.textNode!);
  }

  deleteNode(): void {
    let node = builderNodeMap.pop();
    node?.dispose();
  }

  update(message: string): void {
    if (this.textNode !== null) {
      // 调用update进行更新。
      this.textNode!.update(new Params(message));
    }
  }
}

// 记录创建的自定义节点对象
const builderNodeMap: Array<BuilderNode<Params>> = new Array<BuilderNode<Params>>();

function updateColorMode() {
  builderNodeMap.forEach((value, index) => {
    // 通知BuilderNode环境变量改变，触发深浅色切换
    value.updateConfiguration();
  })
}

@Entry
@Component
struct Index {
  @State message: string = "hello";
  private textNodeController: TextNodeController = new TextNodeController(this.message);
  private count: number = 0;

  aboutToAppear(): void {
    //创建自定义节点并添加至map
    this.textNodeController.createNode(this.getUIContext());
  }

  aboutToDisappear(): void {
    //移除map中的引用，并将自定义节点释放
    this.textNodeController.deleteNode();
  }

  build() {
    Row() {
      Column() {
        NodeContainer(this.textNodeController)
          .width('100%')
          .height(200)
          .backgroundColor('#FFF0F0F0')
        Button('Update')
          .onClick((event: ClickEvent) => {
            this.count += 1;
            const message = "Update " + this.count.toString();
            this.textNodeController.update(message);
          })
        Button('通知切换环境变量')
          .onClick((event: ClickEvent) => {
            updateColorMode()
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```
