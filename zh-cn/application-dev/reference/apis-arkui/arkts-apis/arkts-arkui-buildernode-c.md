# BuilderNode

提供能够挂载系统组件的自定义节点BuilderNode。BuilderNode仅可作为叶子节点使用，支持通过@Builder生成组件树、实现组件复用与回收、跨节点事件分发以及状态同步，适用于在应用内动态创建和管理自定义组件节点的场景。 使用方式参考[BuilderNode开发指南](../../../ui/arkts-user-defined-arktsNode-builderNode.md)。 与BuilderNode相比，ReactiveBuilderNode能通过多参数的无状态UI方法@Builder生成组件树，适用于需要多参数数据绑定和响应式UI动态更新的场景。 > **说明：** > > - 若传入的Builder的根节点为语法节点（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)/ > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)/ > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)/ > [ContentSlot](../../../ui/rendering-control/arkts-rendering-control-contentslot.md)…）、 > Span、ContainerSpan、 > SymbolSpan或自定义组件，将额外生成一个FrameNode，在节点树中显示为“ > BuilderProxyNode”，这会导致树结构变化，影响事件传递等测试流程。详情参见 > [BuilderNode内的BuilderProxyNode导致树结构发生变化](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode内的builderproxynode导致树结构发生变化)。 > > - 如果在跨页面复用BuilderNode时显示异常，可参考[跨页面复用注意事项](../../../ui/arkts-user-defined-arktsNode-builderNode.md#跨页面复用注意事项)。 > > - 当前不支持在预览器中使用BuilderNode。 > > - BuilderNode下的自定义组件支持使用[@Prop装饰器](../../../ui/state-management/arkts-prop.md)。不支持使用 > [@Link装饰器](../../../ui/state-management/arkts-link.md)来跨越BuilderNode同步外界的数据和状态。 > > - 如果BuilderNode的子节点是自定义组件，不支持该自定义组件使用[@Reusable装饰器](../../../ui/state-management/arkts-reusable.md)，详细内容参见 > [BuilderNode在子自定义组件中使用@Reusable装饰器](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode在子自定义组件中使用reusable装饰器)。 > > - 从API version 12开始，自定义组件支持接收[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例。可以通过 > [传递LocalStorage实例](../../../ui/state-management/arkts-localstorage.md#自定义组件接收localstorage实例)来使用LocalStorage相关的装饰器 > [@LocalStorageProp](../../../ui/state-management/arkts-localstorage.md#localstorageprop)、 > [@LocalStorageLink](../../../ui/state-management/arkts-localstorage.md#localstoragelink)。 > > - 从API version 20开始，通过配置[BuildOptions](arkts-arkui-buildernode-buildoptions-i.md)，内部自定义组件的 > [@Consume](../../../ui/state-management/arkts-provide-and-consume.md)支持接收所在页面的 > [@Provide](../../../ui/state-management/arkts-provide-and-consume.md)数据。 > > - 其余装饰器行为未定义，不建议使用。 > > - 仅支持在自定义组件中使用[Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)。 > > - BuilderNode对象不支持使用JSON序列化。

**起始版本：** 11

<!--Device-unnamed-export class BuilderNode--><!--Device-unnamed-export class BuilderNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(builder: WrappedBuilder<Args>, arg?: Object): void
```

依照传入的对象创建组件树，并持有组件树的根节点。无状态的UI方法[@Builder](../../../ui/state-management/arkts-builder.md)最多拥有一个根节点。 支持自定义组件。 > **说明：** > > - @Builder嵌套使用的时候需要保证内外的@Builder方法的入参对象一致。 > > - 最外层的@Builder只支持一个入参。 > > - build的参数是值传递，需要使用[update](#update)接口进行更新。 > > - 需要操作BuilderNode中的对象时，需要保证其引用不被回收。当BuilderNode对象被虚拟机回收之后，它的FrameNode、 > [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md)对象也会与后端节点解引用。即从BuilderNode中获取的FrameNode对象不对应任何一个节点。 > > - BuilderNode对象会持有实体节点的引用。如果不需要使用BuilderNode前端对象管理后端节点，可以调用[dispose](#dispose)接口，实现前后端对象的解绑。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-build(builder: WrappedBuilder<Args>, arg?: Object): void--><!--Device-BuilderNode-build(builder: WrappedBuilder<Args>, arg?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | WrappedBuilder&lt;Args&gt; | 是 | 创建对应节点树的时候所需的无状态UI方法 [@Builder](../../../ui/state-management/arkts-builder.md)。 |
| arg | Object | 否 | builder的入参。当前仅支持一个入参，且入参对象类型与@Builder定义的入参类型保持一致。 <br>默认值：undefined |

## build

```TypeScript
build(builder: WrappedBuilder<Args>, arg: Object, options: BuildOptions): void
```

依照传入的对象创建组件树，并持有组件树的根节点。无状态的UI方法[@Builder](../../../ui/state-management/arkts-builder.md)最多拥有一个根节点。 支持自定义组件。相比 [build(builder: WrappedBuilder\&lt;Args&gt;, arg?: Object)](#build) 接口，本接口支持builder的配置参数，用于配置Builder的构建行为，具体属性见[BuildOptions](arkts-arkui-buildernode-buildoptions-i.md)。 > **说明：** > > - @Builder进行创建和更新的规格参考[@Builder](../../../ui/state-management/arkts-builder.md)。 > > - @Builder嵌套使用的时候需要保证内外的@Builder方法的入参对象一致。 > > - 最外层的@Builder只支持一个入参。 > > - build的参数是值传递，需要使用[update](#update)接口进行更新。 > > - 需要操作BuilderNode中的对象时，需要保证其引用不被回收。当BuilderNode对象被虚拟机回收之后，它的FrameNode、 > [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md)对象也会与后端节点解引用。即从BuilderNode中获取的FrameNode对象不对应任何一个节点。 > > - BuilderNode对象会持有实体节点的引用。如果不需要使用BuilderNode前端对象管理后端节点，可以调用[dispose](#dispose)接口，实现前后端对象的解绑。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-build(builder: WrappedBuilder<Args>, arg: Object, options: BuildOptions): void--><!--Device-BuilderNode-build(builder: WrappedBuilder<Args>, arg: Object, options: BuildOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | WrappedBuilder&lt;Args&gt; | 是 | 创建对应节点树的时候所需的无状态UI方法 [@Builder](../../../ui/state-management/arkts-builder.md)。 |
| arg | Object | 是 | builder的入参。当前仅支持一个入参，且入参对象类型与@Builder定义的入参类型保持一致。 |
| options | [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | 是 | builder的配置参数，用于配置Builder的构建行为，具体属性和说明见[BuildOptions](arkts-arkui-buildernode-buildoptions-i.md)。 |

**示例**

```TypeScript
import { BuilderNode, NodeContent } from '@kit.ArkUI';

// 定义传递参数的接口
interface ParamsInterface {
  text: string;
  func: Function;
}

@Builder
function buildTextWithFunc(func: Function) {
  Text(func())
    .fontSize(50)
    .fontWeight(FontWeight.Bold)
    .margin({ bottom: 36 })
}

@Builder
function buildText(params: ParamsInterface) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    buildTextWithFunc(params.func)
  }
}


@Entry
@Component
struct Index {
  @State message: string = 'HELLO';
  private content: NodeContent = new NodeContent();

  build() {
    Row() {
      Column() {
        Button('addBuilderNode')
          .onClick(() => {
            let buildNode = new BuilderNode<[ParamsInterface]>(this.getUIContext());
            // 创建节点树
            buildNode.build(wrapBuilder<[ParamsInterface]>(buildText), {
              text: this.message, func: () => {
                return 'FUNCTION';
              }
            }, { nestingBuilderSupported: true });
            this.content.addFrameNode(buildNode.getFrameNode());
            buildNode.dispose();
          })
        ContentSlot(this.content)
      }
      .id('column')
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

## constructor

```TypeScript
constructor(uiContext: UIContext, options?: RenderOptions)
```

当将BuilderNode生成的内容嵌入到其它RenderNode中显示时，需要显式指定RenderOptions中的selfIdealSize，否则Builder内的节点默认父组件布局约束为[0, 0]。该场景下，若不设置 selfIdealSize则认为BuilderNode中子树的根节点大小为[0, 0]。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-constructor(uiContext: UIContext, options?: RenderOptions)--><!--Device-BuilderNode-constructor(uiContext: UIContext, options?: RenderOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md) | 是 | UI上下文，获取方式可参考 UIContext获取方法。uiContext需要为一个有效的值，即UI上下文正 确，如果传入非法值或者未设置，会导致创建失败。 |
| options | [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | 否 | BuilderNode的构造可选参数，参数用于构造节点的理想大小和节点的渲染类型。 <br>默认值：undefined |

## dispose

```TypeScript
dispose(): void
```

立即释放当前BuilderNode对象对[实体节点](../../../ui/arkts-user-defined-node.md#基本概念)的引用关系。关于BuilderNode的解绑场景请参见 [节点解绑](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。 > **说明：** > > 当BuilderNode对象调用dispose之后，会与后端实体节点解除引用关系。若前端对象BuilderNode无法释放，容易导致内存泄漏。建议在不再需要对该BuilderNode对象进行操作时，开发者主动调用dispose > 释放后端节点，以减少引用关系的复杂性，降低内存泄漏的风险。具体场景可见 > [BuilderNode前后端循环引用导致的内存泄漏问题](../../../ui/arkts-user-defined-node-faq.md#buildernode前后端循环引用导致的内存泄漏问题)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-dispose(): void--><!--Device-BuilderNode-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getFrameNode

```TypeScript
getFrameNode(): FrameNode | null
```

获取BuilderNode中的FrameNode。在BuilderNode执行build操作之后，才会生成FrameNode。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-getFrameNode(): FrameNode | null--><!--Device-BuilderNode-getFrameNode(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | BuilderNode持有的FrameNode对象，用于将该BuilderNode作为子节点挂载到其他FrameNode上。若该BuilderNode不包含 FrameNode，则返回空对象null。 |

## inheritFreezeOptions

```TypeScript
inheritFreezeOptions(enabled: boolean): void
```

设置当前BuilderNode对象是否继承父组件中自定义组件的冻结策略。如果设置继承状态为false，则BuilderNode对象的冻结策略为false。在这种情况下，节点在不活跃状态下不会被冻结。 > **说明：** > > BuilderNode设置inheritFreezeOptions为true，且父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或 > ReactiveComponentContent时，会继承父组件的冻结策略。当子组件为自定义组件时，BuilderNode的冻结策略不会传递给子组件。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-inheritFreezeOptions(enabled: boolean): void--><!--Device-BuilderNode-inheritFreezeOptions(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | BuilderNode对象是否设置为继承父组件中自定义组件的冻结策略。 <br>true：继承父组件中自定义组件的冻结策略；false：不继承父组件中自定义组件的冻结策略。 <br>**说明：** 仅当父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或ReactiveComponentContent时，设置为true才会生效。 |

**示例**

该示例演示了BuilderNode设置继承状态为true，继承父自定义组件的冻结策略，在处于不活跃状态时冻结，切换为活跃状态时解冻，更新缓存的数据。

```TypeScript
import { BuilderNode, FrameNode, NodeController } from '@kit.ArkUI';

// 自定义传递参数的类
class Params {
  count: number = 0;

  constructor(count: number) {
    this.count = count;
  }
}

@Builder
// builder组件
function buildText(params: Params) {

  Column() {
    TextBuilder({ message: params.count })
  }
}

// 继承NodeController实现自定义textNode控制器
class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private textNode: BuilderNode<[Params]> | null = null;
  private count: number = 0;

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.textNode = new BuilderNode(context, { selfIdealSize: { width: 150, height: 150 } });
    this.textNode.build(wrapBuilder<[Params]>(buildText), new Params(this.count)); // 创建BuilderNode节点
    this.textNode.inheritFreezeOptions(true); // 设置BuilderNode的冻结继承状态为true
    if (this.rootNode !== null) {
      this.rootNode.appendChild(this.textNode.getFrameNode()); // 将BuilderNode上树
    }
    return this.rootNode;
  }

  update(): void {
    if (this.textNode !== null) {
      this.count += 1;
      this.textNode.update(new Params(this.count)); // 更新BuilderNode中的数据，可以触发Log
    }

  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

const textNodeController: TextNodeController = new TextNodeController();

@Entry
@Component
struct MyNavigationTestStack {
  @Provide('pageInfo') pageInfo: NavPathStack = new NavPathStack();
  @State message: number = 0;
  @State logNumber: number = 0;

  @Builder
  PageMap(name: string) {
    if (name === 'pageOne') {
      PageOneStack({ message: this.message, logNumber: this.logNumber })
    } else if (name === 'pageTwo') {
      PageTwoStack({ message: this.message, logNumber: this.logNumber })
    }
  }

  build() {
    Column() {
      Button('update builderNode') // 点击更新BuilderNode
        .onClick(() => {
          textNodeController.update();
        })
      Navigation(this.pageInfo) {
        Column() {
          Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
            .width('80%')
            .height(40)
            .margin(20)
            .onClick(() => {
              this.pageInfo.pushPath({ name: 'pageOne' }); // 将name指定的NavDestination页面信息入栈
            })
        }
      }.title('NavIndex')
      .navDestination(this.PageMap)
      .mode(NavigationMode.Stack)
    }
  }
}

@Component
struct PageOneStack { // 页面一
  @Consume('pageInfo') pageInfo: NavPathStack;
  @State index: number = 1;
  @Link message: number;
  @Link logNumber: number;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })
        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule }) // 切换至页面二
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageTwo', null);
          })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule }) // 返回主页面
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@Component
struct PageTwoStack { // 页面二
  @Consume('pageInfo') pageInfo: NavPathStack;
  @State index: number = 2;
  @Link message: number;
  @Link logNumber: number;

  build() {
    NavDestination() {
      Column() {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })
        Text('BuilderNode处于冻结')
          .fontWeight(FontWeight.Bold)
          .margin({ top: 48, bottom: 48 })
        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule }) // 返回至页面一
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@Component({ freezeWhenInactive: true })
  // 设置冻结策略为不活跃冻结
struct NavigationContentMsgStack {
  @Link message: number;
  @Link index: number;
  @Link logNumber: number;

  build() {
    Column() {
      if (this.index === 1) {
        NodeContainer(textNodeController)
      }
    }
  }
}

@Component({ freezeWhenInactive: true })
  // 设置冻结策略为不活跃冻结
struct TextBuilder {
  @Prop @Watch('info') message: number = 0;
  @State count: number = 0;

  info() {
    this.count++;
    console.info(`freeze-test TextBuilder message callback change time ${this.count}`); // 根据message内容变化来打印日志来判断是否冻结
    console.info(`freeze-test TextBuilder message callback change message ${this.message}`); // 根据message内容变化来打印日志来判断是否冻结
  }

  build() {
    Row() {
      Column() {
        Text(`文本更新内容： ${this.message}`)
          .fontWeight(FontWeight.Bold)
          .margin({ top: 48, bottom: 48 })
        Text(`文本更新次数： ${this.count}`)
          .fontWeight(FontWeight.Bold)
          .margin({ top: 48, bottom: 48 })
      }
    }
  }
}
```

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前BuilderNode对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节点在 dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-isDisposed(): boolean--><!--Device-BuilderNode-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

**示例**

该示例演示了BuilderNode释放节点前后分别使用[isDisposed](#isdisposed)接口验证节点的状态，释放节点前节点调用isDisposed接口返回false，释放节点后节点调用isDisposed接口返回true。

```TypeScript
import { FrameNode, NodeController, BuilderNode } from '@kit.ArkUI';

// 自定义组件
@Component
struct TestComponent {
  build() {
    Column() {
      Text('This is a BuilderNode.')
        .fontSize(25)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
    .height(30)
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('aboutToAppear');
  }

  aboutToDisappear() {
    console.info('aboutToDisappear');
  }
}

@Builder
function buildComponent() {
  TestComponent()
}

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private builderNode: BuilderNode<[]> | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.builderNode = new BuilderNode(uiContext, { selfIdealSize: { width: 200, height: 100 } });
    this.builderNode.build(new WrappedBuilder(buildComponent));

    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.size = { width: 300, height: 300 };
      rootRenderNode.backgroundColor = 0xffd5d5d5;
      rootRenderNode.appendChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }

    return this.rootNode;
  }

  // 释放当前builderNode
  dispose() {
    if (this.builderNode !== null) {
      this.builderNode.dispose();
    }
  }

  // 检验当前builderNode是否已被释放
  isDisposed(): string {
    if (this.builderNode !== null) {
      if (this.builderNode.isDisposed()) {
        return 'builderNode isDisposed is true';
      } else {
        return 'builderNode isDisposed is false';
      }
    }
    return 'builderNode is null';
  }

  removeBuilderNode() {
    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null && this.builderNode !== null && this.builderNode.getFrameNode() !== null) {
      rootRenderNode.removeChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }
  }
}

@Entry
@Component
struct Index {
  @State text: string = '';
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 4 }) {
      NodeContainer(this.myNodeController)
      Button('BuilderNode dispose')
        .onClick(() => {
          this.myNodeController.removeBuilderNode();
          this.myNodeController.dispose();
          this.text = '';
        })
        .width(200)
        .height(50)
      Button('BuilderNode isDisposed')
        .onClick(() => {
          this.text = this.myNodeController.isDisposed();
        })
        .width(200)
        .height(50)
      Text(this.text)
        .fontSize(25)
    }
    .width('100%')
    .height('100%')
  }
}
```

## postInputEvent

```TypeScript
postInputEvent(event: InputEventType): boolean
```

将输入事件分发到BuilderNode管理的目标节点。适用于在自定义NodeContainer中将父组件接收的触摸、鼠标或轴事件转发给BuilderNode内部组件，使内部组件能够响应相应交互的场景。 offsetA为builderNode相对于父组件的偏移，offsetB为命中位置相对于builderNode的偏移，offsetC为offsetA+offsetB，最终输入给postInputEvent中的window信息。  > **说明：** > > - 传入的坐标值需要转换为px，坐标转换示例可以参考下面示例代码。 > > - 鼠标左键点击事件将转换为触摸事件，转发时应注意不在外层同时绑定触摸事件与鼠标事件，否则可能导致坐标偏移。这是由于在事件转换过程中，SourceType不会发生变化，规格可查看 > onTouch。 > > - 注入事件为轴事件（AxisEvent）时，由于轴事件中缺少旋转轴信息，因此注入的事件无法触发 > RotationGesture。 > > - 转发的事件会在被分发到的目标组件所在的子树里做触摸测试（TouchTest），并触发对应手势，原始事件也会触发当前组件所在组件树中的手势。不保证两类手势的竞争结果。 > > - 如果是开发者构造的事件，必填字段必须赋值，比如触摸事件的touches字段，轴事件的scrollStep字段。要保证事件的完整，比如触摸事件的TouchType中DOWN和UP字段都要 > 有，防止出现未定义行为。 > > - [webview](../../apis-arkweb/arkts-apis/arkts-web-webview.md)已经处理过坐标系变换，可以将事件直接下发。 > > - postTouchEvent接口需要提供手势坐标相对于接收事件的目标节点内的局部坐标，postInputEvent接口需要提供手势坐标相对于接收事件的目标节点内的窗口坐标。 > > - 不建议同一个事件转发多次。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-postInputEvent(event: InputEventType): boolean--><!--Device-BuilderNode-postInputEvent(event: InputEventType): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [InputEventType](arkts-arkui-inputeventtype-t.md) | 是 | 用于事件分发的输入事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 事件是否被成功派发。如果事件派发成功，则返回true；否则，返回false。 |

**示例**

请参考示例1（BuilderNode中鼠标事件）、示例2（BuilderNode中触摸事件）、示例3（BuilderNode中轴事件）。

## postInputEventWithStrategy

```TypeScript
postInputEventWithStrategy(event: InputEventType, competitionStrategy?: CompetitionStrategy): boolean
```

将含有竞争策略的事件分发到目标UI组件节点。 接口调用前需要将event转化为对应的事件，并对event中的window参数的坐标进行转化：offsetA表示builderNode相对于父组件的偏移量，offsetB为命中位置相对于builderNode的偏移量， offsetC是offsetA与offsetB之和，最终作为event中的window参数，传递给postInputEventWithStrategy方法，具体请参考示例。  > **说明：** > > - 传入的坐标值单位需要转换为px，坐标转换示例可以参考下面示例代码。 > > - 系统在处理鼠标左键点击事件时将转换为触摸事件，转发时应注意不在外层同时绑定触摸事件与鼠标事件，否则可能导致坐标偏移。这是由于在事件转换过程中， > [SourceType](../../../reference/apis-arkui/arkui-ts/ts-gesture-settings.md#sourcetype枚举说明8)不会发生变化，规格可查看 > onTouch。 > > - 注入事件为轴事件AxisEvent时，由于轴事件中缺少旋转轴信息，因此注入的事件无法触发旋转手势 > RotationGesture。 > > - 转发的事件会在被分发到的目标组件及其子组件里做事件处理，并触发对应手势。可以通过入参控制当前组件和目标组件手势是否为竞争关系。 > > - 如果event转化为对应的事件后，该事件为开发者构造的事件，必填字段必须赋值，比如触摸事件的touches字段，轴事件的scrollStep字段。要保证事件的完整，比如触摸事件的 > TouchType中必须同时包含DOWN和UP两个字段，防止出现程序异常或意外崩溃。 > > - [webview](../../apis-arkweb/arkts-apis/arkts-web-webview.md)已经处理过坐标系变换，可以将事件直接下发。 > > - postTouchEvent接口需要提供手势坐标相对于接收事件的目标节点内的局部坐标，postInputEventWithStrategy接口需要提供手势坐标相对于接收事件的目标节点内的窗口坐标。 > > - 支持同一个事件转发多次。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-postInputEventWithStrategy(event: InputEventType, competitionStrategy?: CompetitionStrategy): boolean--><!--Device-BuilderNode-postInputEventWithStrategy(event: InputEventType, competitionStrategy?: CompetitionStrategy): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [InputEventType](arkts-arkui-inputeventtype-t.md) | 是 | 用于事件分发的输入事件。 |
| competitionStrategy | CompetitionStrategy | 否 | 分发事件的手势竞争策略。CompetitionStrategy.DEFAULT表示非竞争模式（目标组件与当前组件的手势不 竞争），适用于当前组件与目标组件各自独立处理手势、无需竞争同一事件的场景；CompetitionStrategy.COMPETITION表示竞争模式（目标组件与当前组件的手势参与竞争），适用于当前组件与目标组件需要竞争同一 手势事件的场景。不传入时默认为CompetitionStrategy.DEFAULT（非竞争）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 事件是否被成功派发。如果成功，则返回true；否则，返回false。 |

**示例**

请参考示例16（BuilderNode中带竞争策略的鼠标事件）、示例17（BuilderNode中带竞争策略的触摸事件）、示例18（BuilderNode中带竞争策略的轴事件）。

## postTouchEvent

```TypeScript
postTouchEvent(event: TouchEvent): boolean
```

将原始事件派发到某个BuilderNode创建出的FrameNode上。适用于在自定义NodeContainer中将父组件接收的触摸事件转发给BuilderNode内部组件，使内部组件能够响应触摸交互的场景。 postTouchEvent是从组件树的中间节点往下分发，需要变换到父组件坐标系才能分发成功，参考下图。 offsetA为builderNode相对于父组件的偏移量，可以通过FrameNode中的[getPositionToParent](arkts-arkui-framenode-c.md#getpositiontoparent) 获取。offsetB为触点相对于builderNode的偏移量，可以通过 [TouchEvent](../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#touchevent对象说明)获取。offsetC为offsetA 与offsetB的和，是传给postTouchEvent的最终结果。  > **说明：** > > - 传入的坐标值需要转换为px，如果builderNode有仿射变换，则需要再叠加仿射变换。 > > - 在[webview](../../apis-arkweb/arkts-apis/arkts-web-webview.md)中，内部已经处理过坐标系变换，可以将TouchEvent事件直接下发。 > > - 同一时间戳，postTouchEvent只能调用一次。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-postTouchEvent(event: TouchEvent): boolean--><!--Device-BuilderNode-postTouchEvent(event: TouchEvent): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | TouchEvent | 是 | 用于派发到BuilderNode创建出的FrameNode上的触摸事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 派发事件是否成功。true：已命中响应事件的组件；false：未命中任何可响应事件的组件。 <br>**说明：** <br>如果未按照预期命中组件，需要确认以下几点： <br>1. 坐标系是否转换正确。 <br>2. 组件是否处于可交互状态。 <br>3. 是否绑定事件。 |

**示例**

```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext } from '@kit.ArkUI';

// 自定义传递参数的类
class Params {
  text: string = 'this is a text';
}

@Builder
function ButtonBuilder(params: Params) {
  Column() {
    Button(`button ` + params.text)
      .borderWidth(2)
      .backgroundColor(Color.Orange)
      .width('100%')
      .height('100%')
      .gesture(
        TapGesture()
          .onAction((event: GestureEvent) => {
            console.info('TapGesture');
          })
      )
  }
  .width(500)
  .height(300)
  .backgroundColor(Color.Gray)
}

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: BuilderNode<[Params]> | null = null;
  private wrapBuilder: WrappedBuilder<[Params]> = wrapBuilder(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new BuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, { text: 'this is a string' });
    return this.rootNode.getFrameNode();
  }

  // 坐标转换示例
  postTouchEvent(event: TouchEvent, uiContext: UIContext): boolean {
    if (this.rootNode == null) {
      return false;
    }
    let node: FrameNode | null = this.rootNode.getFrameNode();
    let offsetX: number | null | undefined = node?.getPositionToParent().x;
    let offsetY: number | null | undefined = node?.getPositionToParent().y;
    
    let changedTouchLen = event.changedTouches.length;
    for (let i = 0; i < changedTouchLen; i++) {
      if (offsetX != null && offsetY != null && offsetX != undefined && offsetY != undefined) {
        event.changedTouches[i].x = uiContext.vp2px(offsetX + event.changedTouches[i].x);
        event.changedTouches[i].y = uiContext.vp2px(offsetY + event.changedTouches[i].y);
      }
    }
    // 将事件派发至BuilderNode创建的FrameNode上，result记录派发是否成功
    let result = this.rootNode.postTouchEvent(event);
    console.info(`result ${result}`);
    return result;
  }

  aboutToDisappear() {
    this.rootNode?.dispose();
  }
}

@Entry
@Component
struct MyComponent {
  private nodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.nodeController)
        .height(300)
        .width(500)

      Column()
        .width(500)
        .height(300)
        .backgroundColor(Color.Pink)
        .onTouch((event) => {
          if (event != undefined) {
            this.nodeController.postTouchEvent(event, this.getUIContext());
          }
        })
    }
  }
}
```

## recycle

```TypeScript
recycle(): void
```

触发BuilderNode中自定义组件的回收。自定义组件的回收是组件复用机制中的环节，具体信息请参见 [@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。从API版本26.0.0开始，BuilderNode中的自定义组件支持V2组件复用，请参 见[@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。 > **说明：** > > BuilderNode通过reuse和recycle完成其内外自定义组件之间的复用事件传递，具体使用场景请参见 > [BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-recycle(): void--><!--Device-BuilderNode-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reuse

```TypeScript
reuse(param?: Object): void
```

触发BuilderNode中的自定义组件的复用。组件复用请参见[@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。关于BuilderNode 的解绑场景请参见[节点解绑](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。从API版本26.0.0开始，BuilderNode中的自定义 组件支持V2组件复用，请参见[@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。 BuilderNode通过reuse和[recycle](#recycle)完成其内外自定义组件之间的复用事件传递，具体使用场景请参见 [BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-reuse(param?: Object): void--><!--Device-BuilderNode-reuse(param?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | Object | 否 | 用于复用BuilderNode的参数。该参数将直接用于BuilderNode中所有顶层自定义组件的复用，应该包含每个自定义组件的构造函数参数所需内容，否则，会导致未定义行为。 调用此方法将同步触发内部自定义组件的 [aboutToReuse](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10)生命周期回调，并 将该参数作为回调的入参。默认值为undefined，此时BuilderNode中的自定义组件将直接使用构造时的数据源。 |

## update

```TypeScript
update(arg: Object): void
```

根据提供的参数更新BuilderNode，该参数与[build](#build)方法调用时传入的参数类型相 同。对自定义组件进行update的时候需要在自定义组件中将使用的变量定义为[@Prop](../../../ui/state-management/arkts-prop.md)类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-update(arg: Object): void--><!--Device-BuilderNode-update(arg: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arg | Object | 是 | 用于更新BuilderNode的参数，和 [build](#build)调用时传入的参数类型一致。 |

**示例**

```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext } from '@kit.ArkUI';

// 自定义传递参数的类
class Params {
  text: string = '';
  constructor(text: string) {
    this.text = text;
  }
}

// 自定义组件
@Component
struct TextBuilder {
  @Prop message: string = 'TextBuilder';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .margin({bottom: 36})
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
      .margin({ bottom: 36 })
    TextBuilder({message: params.text}) // 自定义组件
  }
}

// 继承NodeController实现自定义textNode控制器
class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private textNode: BuilderNode<[Params]> | null = null;
  private message: string = '';

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    this.textNode = new BuilderNode(context);
    this.textNode.build(wrapBuilder<[Params]>(buildText), new Params(this.message));
    return this.textNode.getFrameNode();
  }

  // 根据传入参数更新BuilderNode
  update(message: string) {
    if (this.textNode !== null) {
      this.textNode.update(new Params(message));
    }
  }
  aboutToDisappear() {
    this.textNode?.dispose();
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'hello';
  private textNodeController: TextNodeController = new TextNodeController(this.message);
  private count = 0;

  build() {
    Row() {
      Column() {
        NodeContainer(this.textNodeController)
          .width('100%')
          .height(200)
          .backgroundColor('#FFF0F0F0')
        Button('Update')
          .onClick(() => {
            this.count += 1;
            const message = 'Update ' + this.count.toString();
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

## updateConfiguration

```TypeScript
updateConfiguration(): void
```

传递系统环境变化事件，触发节点的全量更新。系统环境变化的相关信息请参见 [@ohos.app.ability.Configuration (环境变量)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md)。 > **说明：** > > updateConfiguration接口用于通知对象更新，更新所使用的系统环境由应用当前的系统环境变化决定。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-BuilderNode-updateConfiguration(): void--><!--Device-BuilderNode-updateConfiguration(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { NodeController, BuilderNode, FrameNode, UIContext, FrameCallback } from '@kit.ArkUI';
import { AbilityConstant, Configuration, ConfigurationConstant, EnvironmentCallback } from '@kit.AbilityKit';

class Params {
  text: string = '';

  constructor(text: string) {
    this.text = text;
  }
}

// 自定义组件
@Component
struct TextBuilder {
  // 作为自定义组件中需要更新的属性，数据类型为基础属性，定义为@Prop
  @Prop message: string = 'TextBuilder';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 36 })
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
      .margin({ bottom: 36 })
    TextBuilder({ message: params.text }) // 自定义组件
  }.backgroundColor($r('sys.color.ohos_id_color_background'))
}

// 继承NodeController实现自定义textNode控制器
class TextNodeController extends NodeController {
  private textNode: BuilderNode<[Params]> | null = null;
  private message: string = '';

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    return this.textNode?.getFrameNode() ? this.textNode?.getFrameNode() : null;
  }

  createNode(context: UIContext) {
    this.textNode = new BuilderNode(context);
    this.textNode.build(wrapBuilder<[Params]>(buildText), new Params(this.message));
    builderNodeMap.push(this.textNode);
  }

  deleteNode() {
    let node = builderNodeMap.pop();
    node?.dispose();
  }

  update(message: string) {
    if (this.textNode !== null) {
      // 调用update进行更新
      this.textNode.update(new Params(message));
    }
  }
}

// 记录创建的自定义节点对象
const builderNodeMap: Array<BuilderNode<[Params]>> = new Array();

class MyFrameCallback extends FrameCallback {
  onFrame() {
    updateColorMode();
  }
}

function updateColorMode() {
  builderNodeMap.forEach((value, index) => {
    // 通知BuilderNode环境变量改变，触发深浅色切换
    value.updateConfiguration();
  })
}

@Entry
@Component
struct Index {
  @State message: string = 'hello';
  private textNodeController: TextNodeController = new TextNodeController(this.message);
  private count = 0;

  aboutToAppear(): void {
    let environmentCallback: EnvironmentCallback = {
      onMemoryLevel: (level: AbilityConstant.MemoryLevel): void => {
        console.info('onMemoryLevel');
      },
      onConfigurationUpdated: (config: Configuration): void => {
        console.info(`onConfigurationUpdated ${JSON.stringify(config)}`);
        this.getUIContext()?.postFrameCallback(new MyFrameCallback());
      }
    };
    // 注册监听回调
    this.getUIContext().getHostContext()?.getApplicationContext().on('environment', environmentCallback);
    // 设置应用深浅色跟随系统
    this.getUIContext()
      .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
    // 创建自定义节点并添加至builderNodeMap
    this.textNodeController.createNode(this.getUIContext());
  }

  aboutToDisappear(): void {
    // 移除map中的引用，并将自定义节点释放
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
          .onClick(() => {
            this.count += 1;
            const message = 'Update ' + this.count.toString();
            this.textNodeController.update(message);
          })
        Button('切换深色')
          .onClick(() => {
            this.getUIContext()
              .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_DARK);
          })
        Button('设置浅色')
          .onClick(() => {
            this.getUIContext()
              .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT);
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

