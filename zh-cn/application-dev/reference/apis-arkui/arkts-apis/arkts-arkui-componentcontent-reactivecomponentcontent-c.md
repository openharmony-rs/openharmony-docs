# ReactiveComponentContent

ReactiveComponentContent继承自Content，是一个用于动态承载和复用 UI内容的容器组件。它通过@Builder函数构建UI，并利用[ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md#ReactiveBuilderNode)生成和管理组件树。该组件的核心价值在于为动态内容 提供完整的生命周期管理，使其能够融入ArkUI的组件复用体系，特别适用于长列表等需要高性能渲染的场景。

**继承/实现关系：** ReactiveComponentContent extends Content

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

<!--Device-unnamed-export class ReactiveComponentContent--><!--Device-unnamed-export class ReactiveComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<T>, config: BuildOptions, ...args: T)
```

ReactiveComponentContent的构造函数。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<T>, config: BuildOptions, ...args: T)--><!--Device-ReactiveComponentContent-constructor(uiContext: UIContext, builder: WrappedBuilder<T>, config: BuildOptions, ...args: T)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 创建对应节点时所需的UI上下文。 |
| builder | WrappedBuilder&lt;T&gt; | 是 | 封装带参builder函数的WrappedBuilder对象。 |
| config | [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | 是 | 配置Builder的构建行为，BuildOptions中所有属性均为可选。 |
| args | T | 是 | WrappedBuilder对象封装的builder函数的参数。负责将外部数据传递给构造函数中指定的WrappedBuilder&lt;T&gt;的builder函数。类型T需与 WrappedBuilder&lt;T&gt;中指定的参数类型保持一致。支持多个入参。不传入参数时默认为空数组[]。 |

## 示例

该示例展示了如何使用ReactiveComponentContent构造函数动态创建包含响应式内容的UI组件，实现了builder函数的嵌套调用和函数参数的灵活传递。

```TypeScript
import { ReactiveComponentContent, NodeContent, typeNode } from '@kit.ArkUI';

@Builder
function buildTextWithFunc(func: Function) {
  Text(func())
    .fontSize(20)
    .fontWeight(FontWeight.Bold)
    .margin({ bottom: 36 })
}

@Builder
function buildText(text: string, func: Function) {
  Column() {
    Text(text)
      .fontSize(20)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 12 })
    buildTextWithFunc(func)
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
            // 动态创建Column节点
            let column = typeNode.createNode(this.getUIContext(), 'Column');
            column.initialize();
            // 创建ReactiveComponentContent并添加到Column节点
            column.addComponentContent(new ReactiveComponentContent<[string, Function]>(this.getUIContext(),
              wrapBuilder<[string, Function]>(buildText), { nestingBuilderSupported: true },
              this.message,
              () => {
                return 'FUNCTION'
              }
            ));
            // 将构建好的节点添加到内容容器
            this.content.addFrameNode(column);
          })
        ContentSlot(this.content) // 显示动态添加的内容
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

立即释放当前ReactiveComponentContent对象对[实体节点](../../../ui/arkts-user-defined-node.md#基本概念)的引用关系。关于 ReactiveComponentContent的解绑场景请参见[解除实体节点引用关系](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。 > **说明：** > > ReactiveComponentContent对象调用dispose接口后，会与后端实体节点解除引用关系。调用dispose后再次调用该对象的其他接口可能会出现crash或返回默认值，建议在操作节点前通过 > [isDisposed](../../apis-na/arkts-apis/arkts-na-componentcontent-reactivecomponentcontent-c.md#isDisposed)接口检查其有效性。若前端ReactiveComponentContent对象无法释放，容易导致内存泄漏。建议开发者在 > 不需要操作该ReactiveComponentContent对象时，主动调用dispose释放后端节点，以减少引用关系的复杂性，降低内存泄漏风险。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveComponentContent-dispose(): void--><!--Device-ReactiveComponentContent-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

该示例展示了如何使用dispose接口正确释放ReactiveComponentContent对象，管理节点生命周期。

```TypeScript
import {
  ReactiveComponentContent,
  Binding,
  MutableBinding,
  UIContext,
  UIUtils,
  NodeController,
  FrameNode
} from '@kit.ArkUI';

// dispose
@Builder
function buildText(
  msgAge: MutableBinding<number>,
  message: MutableBinding<string>
) {
  Column() {
    Row() {
      Text(`age: ${msgAge.value}, name: ${message.value}`)
    }
  }
  .justifyContent(FlexAlign.Center)
  .alignItems(HorizontalAlign.Center)
  .width('100%')
  .height('100%')
}

interface GeneratedObjectLiteralInterface1 {
  msgAge: number;
  message: string;
}

const params: GeneratedObjectLiteralInterface1 = {
  msgAge: 10,
  message: 'Mike',
};

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private contentNode: ReactiveComponentContent<[Binding<number>, Binding<string>]> | null = null;

  makeNode(context: UIContext): FrameNode | null {
    // 创建FrameNode作为根容器
    this.rootNode = new FrameNode(context);
    // 创建ReactiveComponentContent响应式内容
    this.contentNode = new ReactiveComponentContent <[Binding<number>, Binding<string>]>(context,
      wrapBuilder<[Binding<number>, Binding<string>]>(buildText),
      {},
      UIUtils.makeBinding<number>(() => params.msgAge, (val: number) => {
        params.msgAge = val;
        console.info('NodeTest1 get', params.msgAge);
      }),
      UIUtils.makeBinding<string>(() => params.message, val => {
        console.info('NodeTest2 set before', params.message);
        params.message = val;
        console.info('NodeTest3 set after', params.message);
      }),
    );
    // 将响应式内容添加到根节点
    if (this.rootNode !== null) {
      this.rootNode.addComponentContent(this.contentNode);
    }
    return this.rootNode;
  }

  // 释放资源的方法
  dispose() {
    if (this.contentNode !== null) {
      this.contentNode.dispose(); // 释放ReactiveComponentContent资源
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      Column() {
        // 显示自定义节点内容
        NodeContainer(this.myNodeController)
          .width('100%')
          .height(100)
          .backgroundColor('#FFF0F0F0')
        // 触发资源释放
        Button('ReactiveComponentContent dispose')
          .onClick(() => {
            this.myNodeController.dispose(); // 调用dispose释放资源
          })
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

## flushState

```TypeScript
flushState(): void
```

更新ReactiveComponentContent。当ReactiveComponentContent中 [WrappedBuilder](../../../ui/state-management/arkts-wrapBuilder.md)对象封装的builder函数中使用的绑定参数是由V1装饰器（如@Observed）装饰的类实例 时，需要在此类数据变更后手动调用本接口更新数据。当使用V2装饰器（如@ObservedV2）装饰的类实例时，支持自动更新，无需手动调用。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveComponentContent-flushState(): void--><!--Device-ReactiveComponentContent-flushState(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

该示例展示了flushState接口在ReactiveComponentContent中的使用场景，通过对比使用V2装饰器（如@ObservedV2）装饰的类与使用V1装饰器（如@Observed）装饰的类的数据更新机制，演示了不同响应式方案下的状态更新策略。

```TypeScript
import {
  ReactiveComponentContent, NodeContent, Binding, UIUtils, typeNode
} from '@kit.ArkUI';

// Builder函数，用于构建显示年龄的文本组件
@Builder
function buildText(age: Binding<number>) {
  Column() {
    Text(`age: ${age.value}`); // 显示年龄值
  }
}

// 使用V2装饰器的类，支持自动状态更新
@ObservedV2
class GeneratedObjectLiteralInterface1 {
  constructor(age: number) {
    this.age = age;
  }

  @Trace age: number = 0; // 使用@Trace装饰器追踪属性变化
}

// 使用普通类（V1装饰器风格），需要手动触发更新
class GeneratedObjectLiteralInterface2 {
  constructor(age: number) {
    this.age = age;
  }

  age: number = 0; // 普通属性，无自动追踪
}

@Entry
@ComponentV2
struct Index {
  private content: NodeContent = new NodeContent();
  // V2装饰器的数据对象，支持自动更新
  params: GeneratedObjectLiteralInterface1 = new GeneratedObjectLiteralInterface1(25);
  // V1装饰器的数据对象，需要手动更新
  params2: GeneratedObjectLiteralInterface2 = new GeneratedObjectLiteralInterface2(25);
  private componentContent: ReactiveComponentContent<[Binding<number>]> | null = null;

  build() {
    Row() {
      Scroll() {
        Column({ space: 12 }) {
          // 创建使用V2装饰器的ReactiveComponentContent
          Button('绑定参数由V2装饰器装饰').onClick(
            () => {
              let column = typeNode.createNode(this.getUIContext(), 'Column');
              column.initialize();
              // 创建ReactiveComponentContent，使用V2装饰器的数据绑定
              column.addComponentContent(new ReactiveComponentContent<[Binding<number>]>(this.getUIContext(),
                wrapBuilder<[Binding<number>]>(buildText),
                {},
                UIUtils.makeBinding<number>(() => {
                  return this.params.age; // 绑定V2装饰器的数据
                })));

              this.content.addFrameNode(column);
            })

          // 创建使用V1装饰器的ReactiveComponentContent
          Button('绑定参数由V1装饰器装饰').onClick(
            () => {
              let column = typeNode.createNode(this.getUIContext(), 'Column');
              column.initialize();
              // 创建ReactiveComponentContent，使用V1装饰器的数据绑定
              this.componentContent =
                new ReactiveComponentContent<[Binding<number>]>(this.getUIContext(),
                  wrapBuilder<[Binding<number>]>(buildText),
                  {},
                  UIUtils.makeBinding<number>(() => {
                    return this.params2.age; // 绑定V1装饰器的数据
                  })
                );
              column.addComponentContent(this.componentContent);
              this.content.addFrameNode(column);
            })

          // 更新V2装饰器的数据（自动更新）
          Button('change age - V2可自动更新').onClick(() => {
            this.params.age += 1; // V2装饰器会自动检测变化并更新UI
          })

          // 更新V1装饰器的数据（需要手动更新）
          Button('change age - V1需手动更新').onClick(() => {
            this.params2.age += 1;
            // 对于V1装饰器的数据，需要手动调用flushState来触发UI更新
            this.componentContent?.flushState();
          })

          // 显示动态创建的内容
          ContentSlot(this.content)
        }
        .id('column')
        .width('100%')
      }
      .scrollable(ScrollDirection.Vertical)
      .scrollBar(BarState.On)
      .scrollBarColor(Color.Gray)
      .scrollBarWidth(10)
    }
    .height('100%')
  }
}
```

## inheritFreezeOptions

```TypeScript
inheritFreezeOptions(enabled: boolean): void
```

设置当前ReactiveComponentContent对象是否继承父组件中自定义组件的冻结策略[ComponentOptions](../arkts-components/arkts-arkui-componentoptions-i.md#ComponentOptions)。冻结策略用于控制组件在不活跃状态下是否暂停状态刷 新。如果设置继承状态为false，则ReactiveComponentContent对象的冻结策略为false。适用于多页面导航（Navigation）等需要对不活跃组件进行冻结管理的场景。 > **说明：** > > ReactiveComponentContent设置inheritFreezeOptions为true，且父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或 > ReactiveComponentContent时，会继承父组件的冻结策略。当子组件为自定义组件时，ReactiveComponentContent的冻结策略不会传递给该子组件。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveComponentContent-inheritFreezeOptions(enabled: boolean): void--><!--Device-ReactiveComponentContent-inheritFreezeOptions(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | ReactiveComponentContent对象是否设置为继承父组件中自定义组件的冻结策略。 &lt;br&gt;true：继承父组件中自定义组件的冻结策略；false：不继承父组件中自定义组件的冻结策略。 &lt;br&gt;**说明：** 仅当父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或ReactiveComponentContent时，设置true才会继承父组 件的冻结策略。 |

## 示例

该示例演示了ReactiveComponentContent设置继承状态为true，继承父自定义组件的冻结策略。组件在不活跃时冻结，切换为活跃状态时解冻并更新缓存的数据。

```TypeScript
import { ReactiveComponentContent, FrameNode, NodeController, Binding, UIUtils, UIContext } from '@kit.ArkUI';

@Builder
// builder组件
function buildText(count: Binding<number>) {

  Column() {
    TextBuilder({ message: count.value })
  }
}

class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private contentNode: ReactiveComponentContent<[Binding<number>]> | null = null;
  private count: number = 0;

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.contentNode = new ReactiveComponentContent(context, wrapBuilder<[Binding<number>]>(buildText), {},
      UIUtils.makeBinding<number>(() => {
        return this.count;
      }));
    this.contentNode.inheritFreezeOptions(true);
    if (this.rootNode !== null) {
      this.rootNode.addComponentContent(this.contentNode);
    }
    return this.rootNode;
  }

  update(): void {
    if (this.contentNode !== null) {
      this.count += 1;
      this.contentNode.flushState();
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
      Button('update ComponentContent')
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
        Text('BuilderNode处于冻结状态')
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

查询当前ReactiveComponentContent对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业 务需求，可能存在节点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveComponentContent-isDisposed(): boolean--><!--Device-ReactiveComponentContent-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。 &lt;br&gt;true：节点已与后端实体节点解除引用；false：节点未与后端实体节点解除引用。 |

## 示例

该示例展示了如何使用isDisposed接口检查ReactiveComponentContent对象是否已解除与后端实体节点的引用关系，提供了节点状态安全检测的完整实现方案。

```TypeScript
import {
  ReactiveComponentContent,
  Binding,
  MutableBinding,
  UIContext,
  UIUtils,
  NodeController,
  FrameNode
} from '@kit.ArkUI';

@Builder
function buildText(
  msgAge: MutableBinding<number>,
  message: MutableBinding<string>
) {
  Column() {
    Row() {
      Text(`age: ${msgAge.value}, name: ${message.value}`)
        .fontSize(15)
    }
  }
  .justifyContent(FlexAlign.Center)
  .alignItems(HorizontalAlign.Center)
  .width('100%')
  .height('100%')
}

interface GeneratedObjectLiteralInterface1 {
  msgAge: number;
  message: string;
}

const params: GeneratedObjectLiteralInterface1 = {
  msgAge: 10,
  message: 'Mike',
};

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private contentNode: ReactiveComponentContent<[Binding<number>, Binding<string>]> | null = null;

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.contentNode = new ReactiveComponentContent <[Binding<number>, Binding<string>]>(context,
      wrapBuilder<[Binding<number>, Binding<string>]>(buildText),
      {},
      UIUtils.makeBinding<number>(() => params.msgAge, (val: number) => {
        params.msgAge = val;
        console.info('NodeTest1 get', params.msgAge);
      }),
      UIUtils.makeBinding<string>(() => params.message, val => {
        console.info('NodeTest2 set before', params.message);
        params.message = val;
        console.info('NodeTest3 set after', params.message);
      }),
    );
    if (this.rootNode !== null) {
      this.rootNode.addComponentContent(this.contentNode);
    }
    return this.rootNode;
  }

  dispose() {
    if (this.contentNode !== null) {
      this.contentNode.dispose();
    }
  }

  // 检验当前Node是否已被释放
  isDisposed(): string {
    if (this.contentNode !== null) {
      if (this.contentNode.isDisposed()) {
        return 'contentNode isDisposed is true';
      } else {
        return 'contentNode isDisposed is false';
      }
    }
    return 'contentNode is null';
  }
}

@Entry
@Component
struct Index {
  @State text: string = ''
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      Column({ space: 12 }) {
        NodeContainer(this.myNodeController)
          .width('100%')
          .height(100)
          .backgroundColor('#FFF0F0F0')
        Button('dispose')
          .onClick(() => {
            this.myNodeController.dispose();
            this.text = '';
          })
          .fontSize(15)
          .width(200)
          .height(30)
        Button('isDisposed')
          .onClick(() => {
            this.text = this.myNodeController.isDisposed();
          })
          .width(200)
          .height(30)
          .fontSize(15)
        Text(this.text)
          .fontSize(15)
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

## isTransferred

```TypeScript
isTransferred(): boolean
```

判断ReactiveComponentContent是否通过transfer.transferStatic或者transfer.transferDynamic方法创建。如果通过上述两个接口创建，则不支持以下方法： [update](../../apis-na/arkts-apis/arkts-na-componentcontent-c.md#update)，[dispose](../../apis-na/arkts-apis/arkts-na-componentcontent-c.md#dispose)， [updateConfiguration](../../apis-na/arkts-apis/arkts-na-componentcontent-c.md#updateConfiguration)， [inheritFreezeOptions](arkts-arkui-componentcontent-c.md#inheritFreezeOptions)。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveComponentContent-isTransferred(): boolean--><!--Device-ReactiveComponentContent-isTransferred(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回ReactiveComponentContent是否通过transfer.transferStatic或transfer.transferDynamic方法创建。&lt;br/&gt;true： ReactiveComponentContent通过transfer.transferStatic或transfer.transferDynamic方法创建。&lt;br/&gt;false： ReactiveComponentContent不通过transfer.transferStatic或transfer.transferDynamic方法创建。 |

## recycle

```TypeScript
recycle(): void
```

触发ReactiveComponentContent中自定义组件的回收。自定义组件的回收是组件复用机制中的环节，具体信息请参见 [@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。从API版本26.0.0开始，ReactiveComponentContent中的自定义 组件支持V2组件复用，请参见[@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。 ReactiveComponentContent通过[reuse](../../apis-na/arkts-apis/arkts-na-componentcontent-reactivecomponentcontent-c.md#reuse)和recycle完成其内外自定义组件之间的复用事件传递，具体使用场景请参见 [BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveComponentContent-recycle(): void--><!--Device-ReactiveComponentContent-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

实现了一个包含多层组件复用的高性能长列表，通过ReactiveComponentContent动态管理Builder内容，在列表滚动时实现组件的自动回收与复用。

```TypeScript
import { NodeContent, typeNode, ReactiveComponentContent } from '@kit.ArkUI';

const TEST_TAG: string = 'Reuse+Recycle';

// 自定义数据源类，用于管理列表数据
class MyDataSource {
  private dataArray: string[] = [];
  private listener: DataChangeListener | null = null;

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number) {
    return this.dataArray[index];
  }

  public pushData(data: string) {
    this.dataArray.push(data);
  }

  public reloadListener(): void {
    this.listener?.onDataReloaded();
  }

  public registerDataChangeListener(listener: DataChangeListener): void {
    this.listener = listener;
  }

  public unregisterDataChangeListener(): void {
    this.listener = null;
  }
}

@Builder
function buildNode(param: string) {
  Row() {
    Text(`C${param} -- `)
    ReusableChildComponent2({ item: param })
  }
}

@Reusable
@Component
struct ReusableChildComponent {
  @Prop item: string = '';
  @Prop switch: string = '';
  private content: NodeContent = new NodeContent();
  // 创建ReactiveComponentContent实例，封装Builder动态内容
  private componentContent: ReactiveComponentContent<[string]> = new ReactiveComponentContent<[string]>(
    this.getUIContext(),
    wrapBuilder<[string]>(buildNode),
    { nestingBuilderSupported: true },
    this.item);

  aboutToAppear() {
    let column = typeNode.createNode(this.getUIContext(), 'Column');
    column.initialize();
    column.addComponentContent(this.componentContent);
    this.content.addFrameNode(column);
  }

  // 组件回收生命周期回调
  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToRecycle ${this.item}`);

    // 当开关开启时，触发内部ReactiveComponentContent的回收
    if (this.switch === 'open') {
      this.componentContent.recycle();
    }
  }

  // 组件复用生命周期回调
  aboutToReuse(params: object): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToReuse ${JSON.stringify(params)}`);

    // 当开关开启时，触发内部ReactiveComponentContent的复用
    if (this.switch === 'open') {
      this.componentContent.reuse(params);
    }
  }

  build() {
    Row() {
      Text(`A${this.item}--`)
      ReusableChildComponent3({ item: this.item })
      ContentSlot(this.content)
    }
  }
}

@Component
struct ReusableChildComponent2 {
  @Prop item: string = 'false';

  aboutToReuse(params: Record<string, object>) {
    console.info(`${TEST_TAG} ReusableChildComponent2 aboutToReuse ${JSON.stringify(params)}`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent2 aboutToRecycle ${this.item}`);
  }

  build() {
    Row() {
      Text(`D${this.item}`)
        .fontSize(20)
        .backgroundColor(Color.Yellow)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}

@Component
struct ReusableChildComponent3 {
  @Prop item: string = 'false';

  aboutToReuse(params: Record<string, object>) {
    console.info(`${TEST_TAG} ReusableChildComponent3 aboutToReuse ${JSON.stringify(params)}`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent3 aboutToRecycle ${this.item}`);
  }

  build() {
    Row() {
      Text(`B${this.item}`)
        .fontSize(20)
        .backgroundColor(Color.Yellow)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}

@Entry
@Component
struct Index {
  @State data: MyDataSource = new MyDataSource();

  aboutToAppear() {
    // 初始化100条测试数据
    for (let i = 0; i < 100; i++) {
      this.data.pushData(i.toString());
    }
  }

  build() {
    Column() {
      // 使用LazyForEach渲染长列表，启用组件复用
      List({ space: 3 }) {
        LazyForEach(this.data, (item: string) => {
          ListItem() {
            ReusableChildComponent({
              item: item,
              switch: 'open'
            })
          }
        }, (item: string) => item)
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

从API版本26.0.0开始，ReactiveComponentContent中的自定义组件支持V2组件复用。

```TypeScript
import { NodeContent, typeNode, ReactiveComponentContent } from '@kit.ArkUI';

const TEST_TAG: string = 'Reuse+Recycle';

class MyDataSource {
  private dataArray: string[] = [];
  private listener: DataChangeListener | null = null;

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number) {
    return this.dataArray[index];
  }

  public pushData(data: string) {
    this.dataArray.push(data);
  }

  public reloadListener(): void {
    this.listener?.onDataReloaded();
  }

  public registerDataChangeListener(listener: DataChangeListener): void {
    this.listener = listener;
  }

  public unregisterDataChangeListener(): void {
    this.listener = null;
  }
}

class Params {
  item: string = '';

  constructor(item: string) {
    this.item = item;
  }
}

@Builder
function buildNode(param: Params = new Params('hello')) {
  Row() {
    Text(`C${param.item} -- `)
    ReusableChildComponent2({ item: param.item }) // 该自定义组件在ReactiveComponentContent中无法被正确复用
  }
}

// 被回收复用的自定义组件，其状态变量会更新，而子自定义组件ReusableChildComponent3中的状态变量也会更新，但ReactiveComponentContent会阻断这一传递过程
@ReusableV2
@ComponentV2
struct ReusableChildComponent {
  @Param item: string = '';
  @Param switch: string = '';
  private content: NodeContent = new NodeContent();
  private componentContent: ReactiveComponentContent<[Params]> = new ReactiveComponentContent<[Params]>(
    this.getUIContext(),
    wrapBuilder<[Params]>(buildNode),
    { nestingBuilderSupported: true },
    new Params(this.item));

  aboutToAppear() {
    let column = typeNode.createNode(this.getUIContext(), 'Column');
    column.initialize();
    column.addComponentContent(this.componentContent);
    this.content.addFrameNode(column);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToRecycle ${this.item}`);

    // 当开关为open，通过ReactiveComponentContent的reuse接口和recycle接口传递给其下的自定义组件，例如ReusableChildComponent2，完成复用
    if (this.switch === 'open') {
      this.componentContent.recycle();
    }
  }

  aboutToReuse(): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToReuse`);

    // 当开关为open，通过ReactiveComponentContent的reuse接口和recycle接口传递给其下的自定义组件，例如ReusableChildComponent2，完成复用
    if (this.switch === 'open') {
      this.componentContent.reuse(new Params(this.item));
    }
  }

  build() {
    Row() {
      Text(`A${this.item}--`)
      ReusableChildComponent3({ item: this.item })
      ContentSlot(this.content)
    }
  }
}

@ComponentV2
struct ReusableChildComponent2 {
  @Param item: string = 'false';

  aboutToReuse() {
    console.info(`${TEST_TAG} ReusableChildComponent2 aboutToReuse`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent2 aboutToRecycle ${this.item}`);
  }

  build() {
    Row() {
      Text(`D${this.item}`)
        .fontSize(20)
        .backgroundColor(Color.Yellow)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}

@ComponentV2
struct ReusableChildComponent3 {
  @Param item: string = 'false';

  aboutToReuse() {
    console.info(`${TEST_TAG} ReusableChildComponent3 aboutToReuse`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent3 aboutToRecycle ${this.item}`);
  }

  build() {
    Row() {
      Text(`B${this.item}`)
        .fontSize(20)
        .backgroundColor(Color.Yellow)
        .margin({ left: 10 })
    }.margin({ left: 10, right: 10 })
  }
}


@Entry
@ComponentV2
struct Index {
  @Local data: MyDataSource = new MyDataSource();

  aboutToAppear() {
    for (let i = 0; i < 100; i++) {
      this.data.pushData(i.toString());
    }
  }

  build() {
    Column() {
      List({ space: 3 }) {
        LazyForEach(this.data, (item: string) => {
          ListItem() {
            ReusableChildComponent({
              item: item,
              switch: 'open' // 将open改为close可观察到，ReactiveComponentContent不通过reuse和recycle接口传递复用时，ReactiveComponentContent内部的自定义组件的行为表现
            })
          }
        }, (item: string) => item)
      }
      .width('100%')
      .height('100%')
    }
  }
}
```

## reuse

```TypeScript
reuse(param?: Object): void
```

触发ReactiveComponentContent中的自定义组件的复用。组件复用请参见[@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。 关于ReactiveComponentContent的解绑场景请参见 [解除实体节点引用关系](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。从API版本26.0.0开始， ReactiveComponentContent中的自定义组件支持V2组件复用，请参见 [@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。 ReactiveComponentContent通过reuse和[recycle](../../apis-na/arkts-apis/arkts-na-componentcontent-reactivecomponentcontent-c.md#recycle)接口完成其内外自定义组件之间的复用事件传递，具体使用场景请参见 [BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveComponentContent-reuse(param?: Object): void--><!--Device-ReactiveComponentContent-reuse(param?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | Object | 否 | 用于复用[ReactiveComponentContent](../../apis-na/arkts-apis/arkts-na-componentcontent-reactivecomponentcontent-c.md#ReactiveComponentContent)的参数。该参数将直接用于 ReactiveComponentContent中所有顶层自定义组件的复用，应该包含每个自定义组件的构造函数参数所需内容，否则会导致未定义行为。调用此方法将同步触发内部自定义组件的 [aboutToReuse](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10)生命周期回调，并 将该参数作为回调的入参。默认值为undefined，此时ReactiveComponentContent中的自定义组件将直接使用构造时的数据源。 |

## 示例

请参考[recycle](#recycle)中的示例。

## updateConfiguration

```TypeScript
updateConfiguration(): void
```

传递系统环境变化事件，触发节点的全量更新，用于通知对象更新所使用的系统环境配置。适用于系统深浅色模式切换、语言变更、字体大小调整等需要节点响应系统配置变化的场景。系统环境变化的相关信息请参见 [@ohos.app.ability.Configuration (环境变量)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md#Configuration)。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveComponentContent-updateConfiguration(): void--><!--Device-ReactiveComponentContent-updateConfiguration(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

该示例展示了如何使用updateConfiguration接口响应系统环境配置变化，实现ReactiveComponentContent构建的UI节点的动态适配更新。

```TypeScript
import { NodeController, FrameNode, ReactiveComponentContent, UIContext, FrameCallback } from '@kit.ArkUI';
import { AbilityConstant, Configuration, EnvironmentCallback, ConfigurationConstant } from '@kit.AbilityKit';

@Builder
function buildText() {
  Column() {
    Text('Hello')
      .fontSize(20)
      .fontWeight(FontWeight.Bold)
  }
  .backgroundColor($r('sys.color.ohos_id_color_background')) // 使用系统颜色资源，会根据深浅色模式自动切换
  .width('100%')
  .alignItems(HorizontalAlign.Center)
  .padding(16)
}

const componentContentMap: Array<ReactiveComponentContent<[]>> = new Array();

class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    return this.rootNode;
  }

  createNode(context: UIContext) {
    this.rootNode = new FrameNode(context);
    let component = new ReactiveComponentContent<[]>(context, wrapBuilder(buildText), {});
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

// 遍历所有ReactiveComponentContent实例，调用updateConfiguration通知系统环境变化
function updateColorMode() {
  componentContentMap.forEach((value) => {
    // updateConfiguration()的作用：传递系统环境变化事件，触发节点的全量更新
    // 当系统深浅色模式、语言、字体大小等配置发生变化时，调用此接口会通知ReactiveComponentContent重新应用最新的系统配置
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
        // 当系统配置更新时，通过帧回调触发updateConfiguration调用
        this.getUIContext()?.postFrameCallback(new MyFrameCallback());
      }
    }
    // 注册监听系统环境变化的回调
    this.getUIContext().getHostContext()?.getApplicationContext().on('environment', environmentCallback);
    // 设置应用深浅色跟随系统
    this.getUIContext()
      .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
    this.myNodeController.createNode(this.getUIContext());
  }

  aboutToDisappear(): void {
    // 移除componentContentMap中的引用，并将自定义节点释放
    this.myNodeController.deleteNode();
  }

  build() {
    Column({ space: 16 }) {
      NodeContainer(this.myNodeController);
      Button('设置深色')
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

