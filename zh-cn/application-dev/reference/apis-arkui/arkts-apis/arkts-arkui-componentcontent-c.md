# ComponentContent

有两种创建实体封装组件的方式。ComponentContent需要通过update接口手动更新内容，主要适用于弹窗等解耦封装场景；ReactiveComponentContent支持响应式数据自动更新、完整生命周期管理和组件复用，适用 于长列表等高性能渲染场景。开发者可根据实际需求从以下方式中选择。 ComponentContent表示组件内容的实体封装，其对象支持在非UI组件中创建与传递，便于开发者对弹窗类组件进行解耦封装。其底层使用了BuilderNode，具体使用规格参考 BuilderNode。 ReactiveComponentContent表示组件内容的实体封装，其对象支持在非UI组件中创建与传递。它支持响应式数据自动更新、完整的生命周期管理和组件复用，适用于长列表等需要高性能渲染的场景。其底层使用了 ReactiveBuilderNode，具体使用规格参考[ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md#ReactiveBuilderNode)。 > **说明：** > > - 当前不支持在预览器中使用ComponentContent和ReactiveComponentContent。 > > - ComponentContent对象不支持使用JSON序列化。

**继承/实现关系：** ComponentContent extends Content

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export class ComponentContent--><!--Device-unnamed-export class ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<[]>)
```

ComponentContent的构造函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[]>)--><!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[]>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 创建对应节点时所需要的UI上下文。 |
| builder | WrappedBuilder&lt;[]&gt; | 是 | 封装不带参builder函数的WrappedBuilder对象。 |

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T)
```

ComponentContent的构造函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T)--><!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 创建对应节点时所需要的UI上下文。 |
| builder | WrappedBuilder&lt;[T]&gt; | 是 | 封装带参builder函数的WrappedBuilder对象。 |
| args | T | 是 | WrappedBuilder对象封装的builder函数的参数，类型T需与`WrappedBuilder&lt;[T]&gt;`中指定的参数类型保持一致，用于将外部数据传递给builder函数以构建UI 内容。 |

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T, options: BuildOptions)
```

ComponentContent的构造函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T, options: BuildOptions)--><!--Device-ComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<[T]>, args: T, options: BuildOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 创建对应节点时所需要的UI上下文。 |
| builder | WrappedBuilder&lt;[T]&gt; | 是 | 封装带参builder函数的WrappedBuilder对象。 |
| args | T | 是 | WrappedBuilder对象封装的builder函数的参数，类型T需与`WrappedBuilder&lt;[T]&gt;`中指定的参数类型保持一致，用于将外部数据传递给builder函数以构建UI 内容。 |
| options | [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | 是 | 构建配置参数，用于配置Builder的构建行为，BuildOptions中所有属性都是可选的。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { ComponentContent, NodeContent, typeNode } from '@kit.ArkUI';

interface ParamsInterface {
  text: string;
  func: Function;
}

@Builder
function buildTextWithFunc(func: Function) {
  Text(func())
    .fontSize(20)
    .fontWeight(FontWeight.Bold)
    .margin({ bottom: 36 })
}

@Builder
function buildText(params: ParamsInterface) {
  Column() {
    Text(params.text)
      .fontSize(20)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 12 })
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
      Column({ space: 12 }) {
        Button('addComponentContent')
          .onClick(() => {
            let column = typeNode.createNode(this.getUIContext(), 'Column');
            column.initialize();
            column.addComponentContent(new ComponentContent<ParamsInterface>(this.getUIContext(),
              wrapBuilder<[ParamsInterface]>(buildText), {
                text: this.message, func: () => {
                  return 'FUNCTION'
                }
              }, { nestingBuilderSupported: true }));
            this.content.addFrameNode(column);
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

ArkTS-Sta示例：

```TypeScript
import { Text, Column, Component, UIContext, Builder, Entry, Row, wrapBuilder, FontWeight, ContentSlot, Button, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { NodeContent, FrameNode, ComponentContent } from '@ohos.arkui.node';

@Builder
function buildText() {
  Column() {
    Text('HELLO')
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}

@Entry
@Component
struct Index {
  private content: NodeContent = new NodeContent();

  build() {
    Row() {
      Column() {
        Button('addComponentContent')
          .onClick((event: ClickEvent) => {
            let frameNode: FrameNode = new FrameNode(this.getUIContext());
            frameNode.addComponentContent(new ComponentContent(this.getUIContext(), wrapBuilder(buildText)));
            this.content.addFrameNode(frameNode);
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

## dispose

```TypeScript
dispose(): void
```

立即释放当前ComponentContent对象对[基本概念：实体节点](../../../ui/arkts-user-defined-node.md#基本概念)的引用关系。关于ComponentContent的解绑场景请参见 [解除实体节点引用关系](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。 > **说明：** > > 当ComponentContent对象调用dispose之后，会与后端实体节点解除引用关系。调用dispose后再次调用该对象的其他接口可能会出现crash或返回默认值，建议在操作节点前通过 > [isDisposed](../../apis-na/arkts-apis/arkts-na-componentcontent-c.md#isDisposed)接口检查其有效性。若前端对象ComponentContent无法释放，容易导致内存泄漏。建议在不再需要操作该 > ComponentContent对象时，开发者主动调用dispose释放后端节点，以减少引用关系的复杂性，降低内存泄漏的风险。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-dispose(): void--><!--Device-ComponentContent-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

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
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = 'hello';

  build() {
    Row() {
      Column() {
        Button('click me')
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
            promptAction.openCustomDialog(contentNode);

            setTimeout(() => {
              promptAction.closeCustomDialog(contentNode)
                .then(() => {
                  console.info('customDialog closed.');
                  if (contentNode !== null) {
                    contentNode.dispose(); // 释放contentNode
                  }
                }).catch((error: BusinessError) => {
                let message = error.message;
                let code = error.code;
                console.error(`Failed to close customDialog. Code: ${code}, message: ${message}`);
              })
            }, 2000); // 2秒后自动关闭
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

## inheritFreezeOptions

```TypeScript
inheritFreezeOptions(enabled: boolean): void
```

设置当前ComponentContent对象是否继承父组件中自定义组件的冻结策略。冻结策略用于控制组件在不活跃状态下是否暂停状态刷新。如果设置继承状态为false，则ComponentContent对象的冻结策略为false。适用 于多页面导航（Navigation）等需要对不活跃组件进行冻结管理的场景。 > **说明：** > > ComponentContent设置inheritFreezeOptions为true，且父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或 > ReactiveComponentContent时，会继承父组件的冻结策略。当子组件为自定义组件时，ComponentContent的冻结策略不会传递给该子组件。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-inheritFreezeOptions(enabled: boolean): void--><!--Device-ComponentContent-inheritFreezeOptions(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | ComponentContent对象是否设置为继承父组件中自定义组件的冻结策略。 &lt;br&gt;true：继承父组件中自定义组件的冻结策略；false：不继承父组件中自定义组件的冻结策略。 &lt;br&gt;**说明：** 仅当父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或ReactiveComponentContent时，设置true才会继承父组 件的冻结策略。 |

## 示例

```TypeScript
import { ComponentContent, FrameNode, NodeController, UIContext } from '@kit.ArkUI';

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

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private contentNode: ComponentContent<Params> | null = null;
  private count: number = 0;

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.contentNode =
      new ComponentContent(context, wrapBuilder(buildText), new Params(this.count)); // 通过buildText创建ComponentContent
    this.contentNode.inheritFreezeOptions(true); // 设置ComponentContent的冻结继承状态为True
    if (this.rootNode !== null) {
      this.rootNode.addComponentContent(this.contentNode); // 将ComponentContent上树
    }
    return this.rootNode;
  }

  update(): void {
    if (this.contentNode !== null) {
      this.count += 1;
      this.contentNode.update(new Params(this.count)); // 更新ComponentContent中的数据，可以触发Log
    }
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
      Button('update ComponentContent') // 点击更新ComponentContent
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

  info() {
    console.info(`freeze-test TextBuilder message callback ${this.message}`); // 根据message内容变化来打印日志来判断是否冻结
  }

  build() {
    Row() {
      Column() {
        Text(`文本更新次数： ${this.message}`)
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

查询当前ComponentContent对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在 节点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-isDisposed(): boolean--><!--Device-ComponentContent-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

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
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = 'hello';
  @State beforeDispose: string = ''
  @State afterDispose: string = ''

  build() {
    Row() {
      Column() {
        Button('click me')
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
            promptAction.openCustomDialog(contentNode);

            setTimeout(() => {
              promptAction.closeCustomDialog(contentNode)
                .then(() => {
                  console.info('customDialog closed.');
                  if (contentNode !== null) {
                    this.beforeDispose =
                      contentNode.isDisposed() ? 'before dispose componentContent isDisposed is true' :
                        'before dispose componentContent isDisposed is false';
                    contentNode.dispose(); // 释放contentNode
                    this.afterDispose = contentNode.isDisposed() ? 'after dispose componentContent isDisposed is true' :
                      'after dispose componentContent isDisposed is false';
                  }
                }).catch((error: BusinessError) => {
                  let message = error.message;
                  let code = error.code;
                  console.error(`Failed to close customDialog. Code: ${code}, message: ${message}`);
                })
            }, 1000); // 1秒后自动关闭
          })
        Text(this.beforeDispose)
          .fontSize(25)
          .margin({ top: 10, bottom: 10 })
        Text(this.afterDispose)
          .fontSize(25)
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

## isTransferred

```TypeScript
isTransferred(): boolean
```

判断ComponentContent是否通过transfer.transferStatic或者transfer.transferDynamic方法创建。如果通过上述两个接口创建，则不支持以下方法： [update](../../apis-na/arkts-apis/arkts-na-componentcontent-c.md#update)，[dispose](../../apis-na/arkts-apis/arkts-na-componentcontent-c.md#dispose)， [updateConfiguration](../../apis-na/arkts-apis/arkts-na-componentcontent-c.md#updateConfiguration)， [inheritFreezeOptions](#inheritFreezeOptions)。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-isTransferred(): boolean--><!--Device-ComponentContent-isTransferred(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回ComponentContent是否通过transfer.transferStatic或transfer.transferDynamic方法创建。&lt;br/&gt;true： ComponentContent通过transfer.transferStatic或transfer.transferDynamic方法创建。&lt;br/&gt;false：ComponentContent不通过 transfer.transferStatic或transfer.transferDynamic方法创建。 |

## 示例

ArkTS-Sta示例：

```TypeScript
import { Text, Column, FontWeight, wrapBuilder, UIContext } from '@ohos.arkui.component';
import { ComponentContent } from '@ohos.arkui.node';
import transfer from '@ohos.transfer';

@Builder
function buildText() {
  Column() {
    Text('Hello World')
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}

export function createComponentContent(context: Object): Any {
  let contextSta = transfer.transferStatic(context, 'ArkUI.UIContext');
  let componentContentSta = new ComponentContent(contextSta as UIContext, wrapBuilder(buildText));
  // 给转换接口传入静态的ComponentContent，创建动态的ComponentContent。
  let componentContentDyn = transfer.transferDynamic(componentContentSta, 'ArkUI.ComponentContent');
  return componentContentDyn;
}
```

ArkTS-Dyn示例：

```TypeScript
import { ComponentContent, NodeContent, FrameNode, UIContext } from '@kit.ArkUI';
import { createComponentContent } from 'library';

// 调用静态侧接口createComponentContent，返回从静态转换动态的ComponentContent对象。
export function ComponentContentTransferDynamic(uiContext: UIContext): ComponentContent<object> {
  let componentContentDyn = createComponentContent(uiContext) as ComponentContent<object>;
  return componentContentDyn;
}

@Entry
@Component
struct Index {
  @State isTransfered: string = '';
  @State isDisposed: string = '';
  private content: NodeContent = new NodeContent();
  private componentContent: ComponentContent<object> | null = null;

  build() {
    Column({ space: 5 }) {
      Text(`isTransfer: ${this.isTransfered}`)
      Text(`isDisposed: ${this.isDisposed}`)
      // 添加转换后的ComponentContent类型的组件内容至frameNode中。
      Button('addComponentContent')
        .onClick(() => {
          let frameNode = new FrameNode(this.getUIContext());
          this.componentContent = ComponentContentTransferDynamic(this.getUIContext());
          frameNode.addComponentContent(this.componentContent);
          this.content.addFrameNode(frameNode);
        })
      // 查询当前ComponentContent是否通过转换接口创建。
      Button('isTransfered')
        .onClick(() => {
          this.isTransfered += this.componentContent?.isTransferred().toString();
        })
      // 查询当前ComponentContent是否已解除与后端实体节点的引用关系。
      Button('isDisposed')
        .onClick(() => {
          this.isDisposed += ' before: ' + this.componentContent?.isDisposed().toString();
          this.componentContent?.dispose();
          this.isDisposed += ' after: ' + this.componentContent?.isDisposed().toString();
        })
      ContentSlot(this.content)
    }
    .width('100%')
    .height('100%')
  }
}
```

## recycle

```TypeScript
recycle(): void
```

- 触发ComponentContent中自定义组件的回收。自定义组件的回收是组件复用机制中的环节，具体信息请参见 [@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。 - ComponentContent通过reuse和recycle完成其内外自定义组件之间的复用事件传递，具体使用场景请参见 [BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。 从API版本26.0.0开始，ComponentContent中的自定义组件支持V2组件复用，请参见 [@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-recycle(): void--><!--Device-ComponentContent-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reuse

```TypeScript
reuse(param?: Object): void
```

触发ComponentContent中的自定义组件的复用。组件复用请参见[@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。关于 ComponentContent的解绑场景请参见[解除实体节点引用关系](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。 ComponentContent通过reuse和[recycle](../../apis-na/arkts-apis/arkts-na-componentcontent-c.md#recycle)接口完成其内外自定义组件之间的复用事件传递，具体使用场景请参见 [BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。 从API版本26.0.0开始，ComponentContent中的自定义组件支持V2组件复用，请参见 [@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-reuse(param?: Object): void--><!--Device-ComponentContent-reuse(param?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | Object | 否 | 用于复用ComponentContent的参数。该参数将直接用于ComponentContent中所有顶层自定义组件的复用，应该包含每个自定义组件的构造函数参数所需内容，否则 会导致未定义行为。调用此方法将同步触发内部自定义组件的 [aboutToReuse](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10)生命周期回调，并 将该参数作为回调的入参。默认值为undefined，此时ComponentContent中的自定义组件将直接使用构造时的数据源。 |

## update

```TypeScript
update(args: T): void
```

用于更新[WrappedBuilder](../../../ui/state-management/arkts-wrapBuilder.md)对象封装的builder函数参数，与constructor传入的参数类型保持一致。适用 于组件内容需要动态变化的场景，如弹窗内容更新等。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-update(args: T): void--><!--Device-ComponentContent-update(args: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | T | 是 | 用于更新[WrappedBuilder](../../../ui/state-management/arkts-wrapBuilder.md)对象封装的builder函数参数，与 constructor传入的参数类型保持一致。 |

## 示例

```TypeScript
import { ComponentContent } from '@kit.ArkUI';

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
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = 'hello';

  build() {
    Row() {
      Column() {
        Button('click me')
          .margin({ top: 200 })
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
            promptAction.openCustomDialog(contentNode);

            setTimeout(() => {
              contentNode.update(new Params('new message'));
            }, 2000); // 2秒后自动更新弹窗内容文本
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

传递系统环境变化事件，触发节点的全量更新。适用于系统深浅色模式切换、语言变更、字体大小调整等需要节点响应系统配置变化的场景。系统环境变化的相关信息请参见 [@ohos.app.ability.Configuration (环境变量)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md#Configuration)。 > **说明：** > > updateConfiguration接口用于通知对象更新当前的系统环境变化。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentContent-updateConfiguration(): void--><!--Device-ComponentContent-updateConfiguration(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

```TypeScript
import { NodeController, FrameNode, ComponentContent, UIContext, FrameCallback } from '@kit.ArkUI';
import { AbilityConstant, Configuration, EnvironmentCallback, ConfigurationConstant } from '@kit.AbilityKit';

@Builder
function buildText() {
  Column() {
    Text('Hello')
      .fontSize(36)
      .fontWeight(FontWeight.Bold)
  }
  .backgroundColor($r('sys.color.ohos_id_color_background'))
  .width('100%')
  .alignItems(HorizontalAlign.Center)
  .padding(16)
}

const componentContentMap: Array<ComponentContent<Object>> = new Array();

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    return this.rootNode;
  }

  createNode(context: UIContext) {
    this.rootNode = new FrameNode(context);
    let component = new ComponentContent<Object>(context, wrapBuilder(buildText));
    componentContentMap.push(component);
    this.rootNode.addComponentContent(component);
  }

  deleteNode() {
    let node = componentContentMap.pop();
    this.rootNode?.dispose();
    node?.dispose();
  }
}

class MyFrameCallback extends FrameCallback {
  onFrame() {
    updateColorMode();
  }
}

function updateColorMode() {
  componentContentMap.forEach((value) => {
    value.updateConfiguration();
  })
}

@Entry
@Component
struct FrameNodeTypeTest {
  private myNodeController: MyNodeController = new MyNodeController();

  aboutToAppear(): void {
    let environmentCallback: EnvironmentCallback = {
      onMemoryLevel: (level: AbilityConstant.MemoryLevel): void => {
        console.info('onMemoryLevel');
      },
      onConfigurationUpdated: (config: Configuration): void => {
        console.info(`onConfigurationUpdated ${config}`);
        this.getUIContext()?.postFrameCallback(new MyFrameCallback());
      }
    }
    // 注册监听回调
    this.getUIContext().getHostContext()?.getApplicationContext().on('environment', environmentCallback);
    // 设置应用深浅色跟随系统
    this.getUIContext()
      .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
    this.myNodeController.createNode(this.getUIContext());
  }

  aboutToDisappear(): void {
    // 移除map中的引用，并将自定义节点释放
    this.myNodeController.deleteNode();
  }

  build() {
    Column({ space: 16 }) {
      NodeContainer(this.myNodeController);
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
  }
}
```

