# ReactiveBuilderNode

ReactiveBuilderNode支持通过无状态的UI方法[@Builder](../../../ui/state-management/arkts-builder.md)生成组件树，并持有该组件树的根节点，不支持定义为状态变 量。ReactiveBuilderNode中持有的FrameNode仅用于将此ReactiveBuilderNode作为子节点挂载到其他FrameNode上。对 ReactiveBuilderNode持有的FrameNode进行属性设置与子节点操作可能会导致未定义行为，因此不建议通过ReactiveBuilderNode的 [getFrameNode](arkts-arkui-buildernode-c.md#getframenode)方法和FrameNode节点的 [getRenderNode](arkts-arkui-framenode-c.md#getrendernode)方法获取RenderNode，并通过 [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md)的接口对其进行属性设置与子节点操作。

**起始版本：** 22

<!--Device-unnamed-export class ReactiveBuilderNode--><!--Device-unnamed-export class ReactiveBuilderNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(builder: WrappedBuilder<Args>, config: BuildOptions, ...args: Args): void
```

依照传入的对象创建组件树，并持有组件树的根节点。无状态的UI方法[@Builder](../../../ui/state-management/arkts-builder.md)最多拥有一个根节点。 支持自定义组件。 > **说明：** > > - @Builder进行创建和更新的规格参考[@Builder](../../../ui/state-management/arkts-builder.md)。 > > - @Builder嵌套使用的时候需要保证内外的@Builder方法的入参对象一致。 > > - 需要操作ReactiveBuilderNode中的对象时，需要保证其引用不被回收。当ReactiveBuilderNode对象被虚拟机回收之后，它的FrameNode、 > [RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md)对象也会与后端节点解引用。即从ReactiveBuilderNode中获取的FrameNode对象不对应任何一个节点。 > > - ReactiveBuilderNode对象会持有实体节点的引用。如果不需要使用ReactiveBuilderNode前端对象管理后端节点，可以调用 > [dispose](#dispose)接口，实现前后端对象的解绑。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-build(builder: WrappedBuilder<Args>, config: BuildOptions, ...args: Args): void--><!--Device-ReactiveBuilderNode-build(builder: WrappedBuilder<Args>, config: BuildOptions, ...args: Args): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | WrappedBuilder&lt;Args&gt; | 是 | 创建对应节点树时所需的无状态UI方法 [@Builder](../../../ui/state-management/arkts-builder.md)。 |
| config | [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | 是 | 用于配置Builder的构建行为，BuildOptions中所有属性都是可选的，各属性默认值请参见BuildOptions的说明。 |
| args | Args | 是 | builder的入参，用于构造WrappedBuilder对象封装的builder函数。支持多个入参。默认值为undefined。 |

**示例**

该示例演示了如何使用ReactiveBuilderNode的build接口动态创建响应式UI组件树，通过数据绑定实现UI内容的动态更新。

```TypeScript
import { ReactiveBuilderNode, NodeContent, Binding, MutableBinding, UIUtils} from '@kit.ArkUI';

// Builder函数，用于构建显示多个数据的UI组件
@Builder
function buildText(age: Binding<number>, name: MutableBinding<string>, count: number) {
  Column() {
    Text(age.value.toString());
    Text(name.value);
    Text(count.toString());
  }
}

@Entry
@Component
struct Index {
  private content: NodeContent = new NodeContent();
  private age: number = 10;
  private grades: number = 100;

  build() {
    Row() {
      Column() {
        Text()
        // 点击时动态创建并添加ReactiveBuilderNode
        Button('add ReactiveBuilderNode').onClick(
          () => {
            // 创建ReactiveBuilderNode实例，泛型参数指定三个参数的类型
            let node = new ReactiveBuilderNode<[Binding<number>, MutableBinding<string>, number]>(this.getUIContext());
            
            // 构建节点内容，传入builder函数和参数
            node.build(
              wrapBuilder<[Binding<number>, Binding<string>, number]>(buildText),  // 包装builder函数
              {},
              UIUtils.makeBinding<number>(() => {
                return this.age
              }),
              UIUtils.makeBinding<string>(() => 'Hello World'),
              this.grades
            );
            // 将构建好的FrameNode添加到内容容器中显示
            this.content.addFrameNode(node.getFrameNode());
            node.dispose();
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

用于构造ReactiveBuilderNode类。当将ReactiveBuilderNode生成的内容嵌入到其它[RenderNode](../../apis-na/arkts-apis/arkts-na-rendernode-c.md)中显示时，需要显式指定 [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md)中的[selfIdealSize](arkts-arkui-buildernode-renderoptions-i.md)，否则ReactiveBuilderNode内的节点默认父组件布局约束为 [0, 0]。调用此接口，若不设置selfIdealSize则认为ReactiveBuilderNode中子树的根节点大小为[0, 0]。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-constructor(uiContext: UIContext, options?: RenderOptions)--><!--Device-ReactiveBuilderNode-constructor(uiContext: UIContext, options?: RenderOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md) | 是 | UI上下文，获取方式可参考 UIContext获取方法。uiContext需要为一个有效的值，即UI上下文正 确，如果传入非法值或者未设置，会导致创建失败。 |
| options | [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | 否 | ReactiveBuilderNode的构造可选参数，参数用于构造节点的理想大小和节点的渲染类型。 <br>默认值：undefined |

## dispose

```TypeScript
dispose(): void
```

立即释放当前ReactiveBuilderNode对象对[实体节点](../../../ui/arkts-user-defined-node.md#基本概念)的引用关系。关于ReactiveBuilderNode的解绑场景请参见 [节点解绑](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。 > **说明：** > > 当ReactiveBuilderNode对象调用dispose之后，会与后端实体节点解除引用关系。若前端对象ReactiveBuilderNode无法释放，容易导致内存泄漏。建议在不再需要对该 > ReactiveBuilderNode对象进行操作时，开发者主动调用dispose释放后端节点，以减少引用关系的复杂性，降低内存泄漏的风险。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-dispose(): void--><!--Device-ReactiveBuilderNode-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

该示例演示了如何通过dispose接口实现ReactiveBuilderNode组件的动态移除与资源释放。

```TypeScript
import { FrameNode, NodeController, ReactiveBuilderNode } from '@kit.ArkUI';

@Component
struct TestComponent {
  build() {
    Column() {
      Text('This is a ReactiveBuilderNode.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)
    }
    .width('100%')
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

// 自定义节点控制器，管理ReactiveBuilderNode和FrameNode
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private builderNode: ReactiveBuilderNode<[]> | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    // 创建根FrameNode
    this.rootNode = new FrameNode(uiContext);
    this.builderNode = new ReactiveBuilderNode(uiContext, { selfIdealSize: { width: 200, height: 100 } });
    // 构建ReactiveBuilderNode内容
    this.builderNode.build(new WrappedBuilder(buildComponent), {});

    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.size = { width: 200, height: 200 };
      rootRenderNode.backgroundColor = 0xff666666;
      // 将ReactiveBuilderNode的RenderNode添加到根节点
      rootRenderNode.appendChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }

    return this.rootNode;
  }

  // 释放资源的方法
  dispose() {
    if (this.builderNode !== null) {
      this.builderNode.dispose(); // 释放ReactiveBuilderNode资源
    }
  }

  // 移除BuilderNode的方法
  removeBuilderNode() {
    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null && this.builderNode !== null && this.builderNode.getFrameNode() !== null) {
      // 从根节点移除BuilderNode的RenderNode
      rootRenderNode.removeChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 4 }) {
      NodeContainer(this.myNodeController)
      // 移除并释放ReactiveBuilderNode
      Button('ReactiveBuilderNode dispose')
        .onClick(() => {
          this.myNodeController.removeBuilderNode();
          this.myNodeController.dispose();
        })
        .width('70%')
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}
```

## flushState

```TypeScript
flushState(): void
```

根据绑定数据的变化刷新ReactiveBuilderNode的数据状态。当ReactiveBuilderNode中 [WrappedBuilder](../../../ui/state-management/arkts-wrapBuilder.md)对象封装的builder函数中使用的绑定参数是由V1装饰器（如@Observed）装饰的类实例 时，需要在此类数据变更后手动调用此方法以更新数据，当使用V2装饰器（如@ObservedV2）装饰的类实例时，支持自动更新，无需手动调用。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-flushState(): void--><!--Device-ReactiveBuilderNode-flushState(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

该示例展示了flushState接口在V1和V2装饰器下的不同使用方式，演示了ReactiveBuilderNode在不同数据响应机制下的更新策略。

```TypeScript
import { ReactiveBuilderNode, NodeContent, Binding, UIUtils } from '@kit.ArkUI';

@Builder
function buildText(age: Binding<number>) {
  Column() {
    Text(`age: ${age.value}`);
  }
}

// 使用V2装饰器的类，支持自动状态更新
@ObservedV2
class GeneratedObjectLiteralInterface_1 {
  constructor(age: number) {
    this.age = age;
  }

  @Trace age: number = 0;
}

// 使用普通类（V1装饰器风格），需要手动触发更新
class GeneratedObjectLiteralInterface_2 {
  constructor(age: number) {
    this.age = age;
  }

  age: number = 0;
}

@Entry
@ComponentV2
struct Index {
  private content: NodeContent = new NodeContent();
  params: GeneratedObjectLiteralInterface_1 = new GeneratedObjectLiteralInterface_1(25);
  params2: GeneratedObjectLiteralInterface_2 = new GeneratedObjectLiteralInterface_2(25);
  private node1: ReactiveBuilderNode<[Binding<number>]> | null = null;

  build() {
    Row() {
      Scroll() {
        Column({ space: 12 }) {
          // 创建使用V2装饰器的ReactiveBuilderNode
          Button('绑定参数由V2装饰器装饰').onClick(
            () => {
              let node =
                new ReactiveBuilderNode<[Binding<number>]>(this.getUIContext());
              node.build(
                wrapBuilder<[Binding<number>]>(buildText),
                {},
                UIUtils.makeBinding<number>(() => {
                  return this.params.age;
                })
              );
              this.content.addFrameNode(node.getFrameNode());
              node.dispose();
            })
          // 创建使用V1装饰器的ReactiveBuilderNode
          Button('绑定参数由V1装饰器装饰').onClick(
            () => {
              this.node1 =
                new ReactiveBuilderNode<[Binding<number>]>(this.getUIContext());
              this.node1.build(
                wrapBuilder<[Binding<number>]>(buildText),
                {},
                UIUtils.makeBinding<number>(() => {
                  return this.params2.age;
                })
              );
              this.content.addFrameNode(this.node1.getFrameNode());
            })
          Button('change age - V2可自动更新').onClick(() => {
            this.params.age += 1; // V2装饰器会自动检测变化并更新UI
          })
          Button('change age - V1需手动更新').onClick(() => {
            this.params2.age += 1;
            // 对于V1装饰器的数据，需要手动调用flushState来触发UI更新
            this.node1?.flushState();
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

## getFrameNode

```TypeScript
getFrameNode(): FrameNode | null
```

获取ReactiveBuilderNode中的FrameNode。在ReactiveBuilderNode执行build操作之后，才会生成FrameNode。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-getFrameNode(): FrameNode | null--><!--Device-ReactiveBuilderNode-getFrameNode(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | ReactiveBuilderNode持有的FrameNode对象，用于将该ReactiveBuilderNode作为子节点挂载到其他FrameNode上。若该 ReactiveBuilderNode不包含FrameNode，则返回空对象null。 |

**示例**

该示例演示了如何使用getFrameNode接口获取ReactiveBuilderNode构建的FrameNode节点，并通过NodeContent动态管理UI节点。

```TypeScript
import { ReactiveBuilderNode, NodeContent, Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

// Builder函数，构建包含文本和按钮的UI组件
@Builder
function buildText(age: Binding<number>, name: MutableBinding<string>, count: number) {
  Column() {
    Text(age.value.toString());
    Text(name.value);
    Text(count.toString());
    Button('click').onClick(() => {
      name.value = 'new name';
    });
  }
}

interface GeneratedObjectLiteralInterface_1 {
  age: number;
  name: string;
  count: number;
}

@Entry
@Component
struct Index {
  private content: NodeContent = new NodeContent();  // 动态节点内容容器
  @State params: GeneratedObjectLiteralInterface_1 = {  // 状态数据对象
    age: 10,
    name: 'Hello World',
    count: 100
  };

  // 扩展Builder
  @Builder
  extendBlank(age: Binding<number>) {
    Row() {
      Blank();
      Text(`age: ${age.value}, blank`);
    }
    .height(20)
  }

  build() {
    Row() {
      Column() {
        Text()
        // 直接使用buildText Builder构建静态内容
        buildText(UIUtils.makeBinding<number>(() => {
          return this.params.age
        }),
          UIUtils.makeBinding<string>(() => this.params.name, val => {
            this.params.name = this.params.name + '+1';
          }),
          this.params.count)
        // 使用extendBlank Builder构建扩展内容
        this.extendBlank(UIUtils.makeBinding<number>(() => {
          return this.params.age
        }))
        
        // 动态添加ReactiveBuilderNode
        Button('add ReactiveBuilderNode').onClick(
          () => {
            // 创建ReactiveBuilderNode实例
            let node = new ReactiveBuilderNode<[Binding<number>, MutableBinding<string>, number]>(this.getUIContext());
            
            // 构建节点内容
            node.build(
              wrapBuilder<[Binding<number>, Binding<string>, number]>(buildText),
              {},
              UIUtils.makeBinding<number>(() => {
                return this.params.age
              }),
              UIUtils.makeBinding<string>(() => this.params.name, val => {
                this.params.name = val;
              }),
              this.params.count
            );
            this.content.addFrameNode(node.getFrameNode());
            node.dispose();
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

## inheritFreezeOptions

```TypeScript
inheritFreezeOptions(enabled: boolean): void
```

设置当前ReactiveBuilderNode对象是否继承父组件中自定义组件的冻结策略。如果设置继承状态为false，则ReactiveBuilderNode对象的冻结策略为false。在这种情况下，节点在不活跃状态下不会被冻结。 > **说明：** > > ReactiveBuilderNode设置inheritFreezeOptions为true，且父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或 > ReactiveComponentContent时，会继承父组件的冻结策略。当子组件为自定义组件时，ReactiveBuilderNode的冻结策略不会传递给子组件。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-inheritFreezeOptions(enabled: boolean): void--><!--Device-ReactiveBuilderNode-inheritFreezeOptions(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | ReactiveBuilderNode对象是否设置为继承父组件中自定义组件的冻结策略。true为继承父组件中自定义组件的冻结策略，false为不继承父组件中自定义组件的冻结 策略。仅当父组件为自定义组件、BuilderNode、ComponentContent、ReactiveBuilderNode或ReactiveComponentContent时，设置为true才会生效。 |

**示例**

该示例演示了ReactiveBuilderNode设置继承状态为true时，继承父自定义组件的冻结策略。在页面跳转后进入不活跃状态时进行冻结，切换为活跃状态时解冻，更新缓存的数据。

```TypeScript
import { ReactiveBuilderNode, FrameNode, NodeController, Binding, UIUtils } from '@kit.ArkUI';

@Builder
function buildText(count: Binding<number>) {
  Column() {
    TextBuilder({ message: count.value })
  }
}

// 自定义节点控制器（逻辑不变）
class TextNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private textNode: ReactiveBuilderNode<[Binding<number>]> | null = null;
  private count: number = 0; // 内部计数状态

  makeNode(context: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(context);
    this.textNode = new ReactiveBuilderNode(context, { selfIdealSize: { width: 150, height: 150 } });
    // 构建节点内容
    this.textNode.build(wrapBuilder<[Binding<number>]>(buildText), {}, UIUtils.makeBinding<number>(() => {
      return this.count
    }));
    // 启用冻结继承选项，当父组件冻结时自动冻结
    this.textNode.inheritFreezeOptions(true);
    // 将ReactiveBuilderNode添加到根节点
    if (this.rootNode !== null) {
      this.rootNode.appendChild(this.textNode.getFrameNode());
    }
    return this.rootNode;
  }

  update(): void {
    if (this.textNode !== null) {
      this.count += 1; // 增加计数
      this.textNode.flushState();
    }
  }

  aboutToDisappear() {
    this.textNode?.dispose();
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
      PageOneStack({ message: $message, logNumber: $logNumber })
    } else if (name === 'pageTwo') {
      PageTwoStack({ message: $message, logNumber: $logNumber })
    }
  }

  @Builder
  CustomTitle() {
    Text('NavIndex')
      .fontSize(20)
      .fontColor(Color.Black)
      .fontWeight(FontWeight.Normal)
  }

  build() {
    Column() {
      Button('update builderNode')
        .fontSize(18)
        .onClick(() => {
          textNodeController.update();
        })

      Navigation(this.pageInfo) {
        Column() {
          Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
            .fontSize(18)
            .width('80%')
            .height(40)
            .margin(10)
            .onClick(() => {
              this.pageInfo.pushPath({ name: 'pageOne' });
            })
        }
      }
      .title(this.CustomTitle)
      .navDestination(this.PageMap)
      .mode(NavigationMode.Stack)
    }
    .width('100%')
    .height('100%')
    .padding(10)
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

        Button('Next Page', { stateEffect: true, type: ButtonType.Capsule })
          .fontSize(18)
          .width('80%')
          .height(40)
          .margin(8)
          .onClick(() => {
            this.pageInfo.pushPathByName('pageTwo', null);
          })

        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .fontSize(18)
          .width('80%')
          .height(40)
          .margin(8)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }
      .width('100%')
      .height('100%')
    }
    .title('pageOne')
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
      Column({ space: 8 }) {
        NavigationContentMsgStack({ message: this.message, index: this.index, logNumber: this.logNumber })

        Text('BuilderNode处于冻结状态')
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ top: 16, bottom: 16 })

        Button('Back Page', { stateEffect: true, type: ButtonType.Capsule })
          .fontSize(18)
          .width('80%')
          .height(40)
          .margin(8)
          .onClick(() => {
            this.pageInfo.pop();
          })
      }
      .width('100%')
      .height('100%')
    }
    .title('pageTwo')
    .onBackPressed(() => {
      this.pageInfo.pop();
      return true;
    })
  }
}

@Component({ freezeWhenInactive: true })
  // 启用非活动时冻结
struct NavigationContentMsgStack {
  @Link message: number;
  @Link index: number;
  @Link logNumber: number;

  build() {
    Column() {
      if (this.index === 1) {
        NodeContainer(textNodeController)
          .margin({ bottom: 5 })
      }
    }
  }
}

// 文本构建器组件，支持冻结
@Component({ freezeWhenInactive: true })
struct TextBuilder {
  @Prop @Watch('info') message: number = 0;
  @State count: number = 0;

  info() {
    this.count++;
    console.info(`freeze-test TextBuilder message callback change time ${this.count}`);
    console.info(`freeze-test TextBuilder message callback change message ${this.message}`);
  }

  build() {
    Row() {
      Column() {
        Text(`文本更新内容： ${this.message}`)
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ top: 16, bottom: 16 })

        Text(`文本更新次数： ${this.count}`)
          .fontSize(18)
          .fontWeight(FontWeight.Bold)
          .margin({ top: 16, bottom: 16 })
      }
    }
  }
}
```

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前ReactiveBuilderNode对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可 能存在节点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-isDisposed(): boolean--><!--Device-ReactiveBuilderNode-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

**示例**

该示例演示了ReactiveBuilderNode释放节点前后分别使用[isDisposed](#isdisposed)接口验证节点的状态，释放节点前节点调用isDisposed接口返回false，释放节点后节点调用isDisposed接口返回true。

```TypeScript
import { FrameNode, NodeController, ReactiveBuilderNode } from '@kit.ArkUI';

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
  private rootNode: FrameNode | null = null; // 根FrameNode容器
  private builderNode: ReactiveBuilderNode<[]> | null = null; // ReactiveBuilderNode实例

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.builderNode = new ReactiveBuilderNode(uiContext, { selfIdealSize: { width: 200, height: 100 } });
    // 构建ReactiveBuilderNode内容，使用WrappedBuilder包装Builder函数
    this.builderNode.build(new WrappedBuilder(buildComponent), {});

    const rootRenderNode = this.rootNode!.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.size = { width: 300, height: 50 };
      rootRenderNode.backgroundColor = 0xffd5d5d5;
      // 将ReactiveBuilderNode的RenderNode添加到根节点
      rootRenderNode.appendChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }

    return this.rootNode;
  }

  // 释放资源的方法
  dispose() {
    if (this.builderNode !== null) {
      this.builderNode.dispose(); // 释放ReactiveBuilderNode资源
    }
  }

  // 检查节点是否已释放的方法
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
      // 从根节点移除BuilderNode的RenderNode
      rootRenderNode.removeChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }
  }
}

@Entry
@Component
struct Index {
  @State text: string = ''; // 状态变量，用于显示节点状态信息
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 4 }) {
      NodeContainer(this.myNodeController)
      Button('BuilderNode dispose')
        .onClick(() => {
          this.myNodeController.removeBuilderNode();
          this.myNodeController.dispose(); // 释放资源
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
      // 显示节点状态信息
      Text(this.text)
        .fontSize(20)
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

将输入事件分发到ReactiveBuilderNode管理的目标节点。适用于在自定义NodeContainer中将父组件接收的触摸、鼠标或轴事件转发给ReactiveBuilderNode内部组件，使内部组件能够响应相应交互的场 景。 offsetA为builderNode相对于父组件的偏移，offsetB为命中位置相对于builderNode的偏移，offsetC为offsetA+offsetB，最终输入给postInputEvent当中。  > **说明：** > > 传入的坐标值需要转换为px，坐标转换示例可以参考下面示例代码。 > > 鼠标左键点击事件将转换为触摸事件，转发时应注意不在外层同时绑定触摸事件与鼠标事件，否则可能导致坐标偏移。这是由于在事件转换过程中，事件的 > [SourceType](../../../reference/apis-arkui/arkui-ts/ts-gesture-settings.md#sourcetype枚举说明8)不会发生变化，规格可查看 > onTouch。 > > 注入事件为轴事件（AxisEvent）时，由于轴事件中缺少旋转轴信息，因此注入的事件无法触发 > RotationGesture。 > > 转发的事件会在被分发到的目标组件所在的子树里做触摸测试（TouchTest），并触发对应手势，原始事件也会触发当前组件所在组件树中的手势。不保证两类手势的竞争结果。 > > 如果是开发者构造的事件，必填字段必须赋值，比如触摸事件的touches字段、轴事件的scrollStep字段，同时要保证事件的完整，比如触摸事件的TouchType中DOWN和UP字段都要 > 有，防止出现未定义行为。 > > [webview](../../apis-arkweb/arkts-apis/arkts-web-webview.md)已经处理过坐标系变换，可以将事件直接下发。 > > postTouchEvent接口需要提供手势坐标相对于接收事件的目标节点内的局部坐标，postInputEvent接口需要提供手势坐标相对于接收事件的目标节点内的窗口坐标。 > > 不建议同一个事件转发多次。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-postInputEvent(event: InputEventType): boolean--><!--Device-ReactiveBuilderNode-postInputEvent(event: InputEventType): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [InputEventType](arkts-arkui-inputeventtype-t.md) | 是 | 待分发的输入事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 事件是否被成功分发。如果事件分发成功，则返回true；否则，返回false。 |

**示例**

请参考示例13（ReactiveBuilderNode中鼠标事件）、示例14（ReactiveBuilderNode中触摸事件）、示例15（ReactiveBuilderNode中轴事件）。

## postInputEventWithStrategy

```TypeScript
postInputEventWithStrategy(event: InputEventType, competitionStrategy?: CompetitionStrategy): boolean
```

将含有竞争策略的事件分发到目标UI组件节点。 接口调用前需要将event转化为对应的事件，并对event中的window参数的坐标进行转化：offsetA表示ReactiveBuilderNode相对于父组件的偏移量，offsetB为命中位置相对于 ReactiveBuilderNode的偏移量，offsetC是offsetA与offsetB之和，最终作为event中的window参数，传递给postInputEventWithStrategy方法，具体请参考示例。  > **说明：** > > - 传入的坐标值单位需要转换为px，坐标转换示例可以参考下面示例代码。 > > - 系统在处理鼠标左键点击事件时将转换为触摸事件，转发时应注意不在外层同时绑定触摸事件与鼠标事件，否则可能导致坐标偏移。这是由于在事件转换过程中， > [SourceType](../../../reference/apis-arkui/arkui-ts/ts-gesture-settings.md#sourcetype枚举说明8)不会发生变化，规格可查看 > onTouch。 > > - 注入事件为轴事件AxisEvent时，由于轴事件中缺少旋转轴信息，因此注入的事件无法触发旋转手势 > RotationGesture。 > > - 转发的事件会在被分发到的目标组件及其子组件里做事件处理，并触发对应手势。可以通过入参控制当前组件和目标组件手势是否为竞争关系。 > > - 如果event转化为对应的事件后，该事件为开发者构造的事件，必填字段必须赋值，比如触摸事件的touches字段，轴事件的scrollStep字段。要保证事件的完整，比如触摸事件的 > TouchType中必须同时包含DOWN和UP两个字段，防止出现程序异常或意外崩溃。 > > - [webview](../../apis-arkweb/arkts-apis/arkts-web-webview.md)已经处理过坐标系变换，可以将事件直接下发。 > > - postTouchEvent接口需要提供手势坐标相对于接收事件的目标节点内的局部坐标，postInputEventWithStrategy接口需要提供手势坐标相对于接收事件的目标节点内的窗口坐标。 > > - 支持同一个事件转发多次。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-postInputEventWithStrategy(event: InputEventType, competitionStrategy?: CompetitionStrategy): boolean--><!--Device-ReactiveBuilderNode-postInputEventWithStrategy(event: InputEventType, competitionStrategy?: CompetitionStrategy): boolean-End-->

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

## postTouchEvent

```TypeScript
postTouchEvent(event: TouchEvent): boolean
```

将原始事件派发到某个ReactiveBuilderNode创建的FrameNode上。适用于在自定义NodeContainer中将父组件接收的触摸事件转发给ReactiveBuilderNode内部组件，使内部组件能够响应触摸交互 的场景。 postTouchEvent是从组件树的中间节点往下分发，需要变换到父组件坐标系才能分发成功，参考下图。 offsetA为builderNode相对于父组件的偏移量，可以通过FrameNode中的[getPositionToParent](arkts-arkui-framenode-c.md#getpositiontoparent) 获取。offsetB为触点相对于builderNode的偏移量，可以通过 [TouchEvent](../../../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#touchevent对象说明)获取。offsetC为offsetA 与offsetB的和，是传给postTouchEvent的最终结果。  > **说明：** > > 传入的坐标值需要转换为px，如果builderNode有仿射变换，则需要再叠加仿射变换。 > > 在[webview](../../apis-arkweb/arkts-apis/arkts-web-webview.md)中，内部已经处理过坐标系变换，可以将TouchEvent事件直接下发。 > > 同一时间戳，postTouchEvent只能调用一次。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-postTouchEvent(event: TouchEvent): boolean--><!--Device-ReactiveBuilderNode-postTouchEvent(event: TouchEvent): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | TouchEvent | 是 | 用于派发到ReactiveBuilderNode创建出的FrameNode上的触摸事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 派发事件是否成功。true：已命中响应事件的组件；false：未命中任何可响应事件的组件。 <br>**说明：** <br>如果未按照预期命中组件，需要确认： <br>1. 坐标系是否转换正确。 <br>2. 组件是否处于可交互状态。 <br>3. 是否绑定事件。 |

**示例**

当触摸下方蓝色区域时，触摸事件会经过坐标转换后传递给上方的ReactiveBuilderNode按钮，触发按钮的触摸反馈和日志输出，实现了触摸事件的跨节点精准传递。

```TypeScript
import { NodeController, ReactiveBuilderNode, FrameNode, UIContext } from '@kit.ArkUI';

@Builder
function ButtonBuilder() {
  Column() {
    Button(`Button`)
      .borderWidth(2)
      .backgroundColor(Color.Gray)
      .width('100%')
      .height('100%')
      .gesture(
        TapGesture()
          .onAction((event: GestureEvent) => {
            console.info('TapGesture');
          })
      )
      .onTouch(() => {
        console.info(`postTouchEvent Success`);
      })
  }
  .width(500)
  .height(300)
  .backgroundColor(Color.Gray)
}

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: ReactiveBuilderNode<[]> | null = null;
  private wrapBuilder: WrappedBuilder<[]> = wrapBuilder(ButtonBuilder);

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new ReactiveBuilderNode(uiContext);
    this.rootNode.build(this.wrapBuilder, {});
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
        .backgroundColor('#ADD8E6')
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

触发ReactiveBuilderNode中自定义组件的回收。自定义组件的回收是组件复用机制中的环节，具体信息请参见 [@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。从API版本26.0.0开始，ReactiveBuilderNode中的自定义组件支持V 2组件复用，请参见[@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。 ReactiveBuilderNode通过[reuse](#reuse)和recycle完成其内外自定义组件之间的复用事件传递，具体使用场景请参见 [BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-recycle(): void--><!--Device-ReactiveBuilderNode-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

该示例展示了在长列表场景下，如何使用ReactiveBuilderNode的reuse和recycle接口实现组件复用机制，优化列表滚动的性能表现。

```TypeScript
import { FrameNode, NodeController, ReactiveBuilderNode, UIContext } from '@kit.ArkUI';

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

  // 注册数据变化监听器
  public registerDataChangeListener(listener: DataChangeListener): void {
    this.listener = listener;
  }

  public unregisterDataChangeListener(): void {
    this.listener = null;
  }
}

// 构建器函数，用于创建列表项UI
@Builder
function buildNode(text: string) {
  Row() {
    Text(`C${text} -- `)
    ReusableChildComponent2({ item: text }) // 嵌套可复用组件
  }
}

// 自定义节点控制器，管理ReactiveBuilderNode
class MyNodeController extends NodeController {
  public builderNode: ReactiveBuilderNode<[string]> | null = null;
  public item: string = '';

  // 创建节点方法
  makeNode(uiContext: UIContext): FrameNode | null {
    if (this.builderNode == null) {
      // 创建ReactiveBuilderNode并设置理想尺寸
      this.builderNode = new ReactiveBuilderNode(uiContext, { selfIdealSize: { width: 300, height: 200 } });
      // 使用构建器函数构建节点内容
      this.builderNode.build(wrapBuilder<[string]>(buildNode), {}, this.item);
    }
    return this.builderNode.getFrameNode();
  }

  aboutToDisappear() {
    this.builderNode?.dispose();
  }
}

@Reusable
@Component
struct ReusableChildComponent {
  @Prop item: string = '';
  @Prop switch: string = '';
  private controller: MyNodeController = new MyNodeController();

  aboutToAppear() {
    this.controller.item = this.item; // 初始化控制器数据
  }

  // 组件回收时的生命周期回调
  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToRecycle ${this.item}`);

    // 当开关打开时，触发builderNode的回收
    if (this.switch === 'open') {
      this.controller?.builderNode?.recycle();
    }
  }

  // 组件复用时的生命周期回调
  aboutToReuse(params: object): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToReuse ${JSON.stringify(params)}`);

    // 当开关打开时，触发builderNode的复用
    if (this.switch === 'open') {
      this.controller?.builderNode?.reuse(params);
    }
  }

  build() {
    Row() {
      Text(`A${this.item}--`)
      ReusableChildComponent3({ item: this.item })
      NodeContainer(this.controller); // 包含NodeContainer用于显示自定义节点
    }
  }
}

@Component
struct ReusableChildComponent2 {
  @Prop item: string = 'false';

  // 复用时的回调
  aboutToReuse(params: Record<string, object>) {
    console.info(`${TEST_TAG} ReusableChildComponent2 aboutToReuse ${JSON.stringify(params)}`);
  }

  // 回收时的回调
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

  // 复用时的回调
  aboutToReuse(params: Record<string, object>) {
    console.info(`${TEST_TAG} ReusableChildComponent3 aboutToReuse ${JSON.stringify(params)}`);
  }

  // 回收时的回调
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
    // 初始化列表数据
    for (let i = 0; i < 100; i++) {
      this.data.pushData(i.toString());
    }
  }

  build() {
    Column() {
      // 使用LazyForEach渲染长列表，支持组件复用
      List({ space: 3 }) {
        LazyForEach(this.data, (item: string) => {
          ListItem() {
            ReusableChildComponent({
              item: item,
              switch: 'open' // 开启复用回收功能
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

从API版本26.0.0开始，ReactiveBuilderNode中的自定义组件支持V2组件复用。

```TypeScript
import { FrameNode, NodeController, ReactiveBuilderNode, UIContext } from '@kit.ArkUI';

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
  public item: string = '';

  constructor(item: string) {
    this.item = item;
  }
}

@Builder
function buildNode(param: Params = new Params('hello')) {
  Row() {
    Text(`C${param.item} -- `)
    ChildComponent2({ item: param.item })
  }
}

class MyNodeController extends NodeController {
  public builderNode: ReactiveBuilderNode<[Params]> | null = null;
  public item: string = '';

  makeNode(uiContext: UIContext): FrameNode | null {
    if (this.builderNode == null) {
      this.builderNode = new ReactiveBuilderNode(uiContext, { selfIdealSize: { width: 300, height: 200 } });
      this.builderNode.build(wrapBuilder<[Params]>(buildNode), {}, new Params(this.item));
    }
    return this.builderNode.getFrameNode();
  }

  aboutToDisappear() {
    this.builderNode?.dispose();
  }
}

// 被回收复用的自定义组件，其状态变量会更新，而子自定义组件ChildComponent3中的状态变量也会更新，但ReactiveBuilderNode会阻断这一传递过程。
@ReusableV2
@ComponentV2
struct ReusableChildComponent {
  @Param item: string = '';
  @Param switch: string = '';
  private controller: MyNodeController = new MyNodeController();

  aboutToAppear() {
    this.controller.item = this.item;
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToRecycle ${this.item}`);

    // 当开关为open，通过ReactiveBuilderNode的reuse接口和recycle接口传递给其下的自定义组件，例如ChildComponent2，完成复用。
    if (this.switch === 'open') {
      this.controller?.builderNode?.recycle();
    }
  }

  aboutToReuse(): void {
    console.info(`${TEST_TAG} ReusableChildComponent aboutToReuse`);

    // 当开关为open，通过ReactiveBuilderNode的reuse接口和recycle接口传递给其下的自定义组件，例如ChildComponent2，完成复用。
    if (this.switch === 'open') {
      this.controller?.builderNode?.reuse(new Params(this.item));
    }
  }

  build() {
    Row() {
      Text(`A${this.item}--`)
      ChildComponent3({ item: this.item })
      NodeContainer(this.controller);
    }
  }
}

@ComponentV2
struct ChildComponent2 {
  @Param item: string = 'false';

  aboutToReuse() {
    console.info(`${TEST_TAG} ChildComponent2 aboutToReuse`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ChildComponent2 aboutToRecycle ${this.item}`);
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
struct ChildComponent3 {
  @Param item: string = 'false';

  aboutToReuse() {
    console.info(`${TEST_TAG} ChildComponent3 aboutToReuse`);
  }

  aboutToRecycle(): void {
    console.info(`${TEST_TAG} ChildComponent3 aboutToRecycle ${this.item}`);
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
              switch: 'open' // 将open改为close可观察到，ReactiveBuilderNode不通过reuse和recycle接口传递复用时，ReactiveBuilderNode内部的自定义组件的行为表现。
            })
          }
        }, (item: string) => item)
      }
      .id('List')
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

触发ReactiveBuilderNode中的自定义组件的复用。组件复用请参见[@Reusable装饰器：V1组件复用](../../../ui/state-management/arkts-reusable.md)。关于 ReactiveBuilderNode的解绑场景请参见[节点解绑](../../../ui/arkts-user-defined-arktsNode-builderNode.md#解除实体节点引用关系)。从API版本26.0.0 开始，ReactiveBuilderNode中的自定义组件支持V2组件复用，请参见 [@ReusableV2装饰器：V2组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。 ReactiveBuilderNode通过reuse和[recycle](#recycle)完成其内外自定义组件之间的复用事件传递，具体使用场景请参见 [BuilderNode调用reuse和recycle接口实现节点复用能力](../../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode调用reuse和recycle接口实现节点复用能力)。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-reuse(param?: Object): void--><!--Device-ReactiveBuilderNode-reuse(param?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | Object | 否 | 用于复用[ReactiveBuilderNode](#reactivebuildernode)的参数。该参数将直接用于 [ReactiveBuilderNode](#reactivebuildernode)中所有顶层自定义组件的复用，应该包含每个自定义组件的构造函数参数所需内容，否则，会导致未定义行为。调用此方法将同步触发内部自定 义组件的[aboutToReuse](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10)生命周期 回调，并将该参数作为回调的入参。默认值为undefined，此时ReactiveBuilderNode中的自定义组件将直接使用构造时的数据源。 |

**示例**

请参考[recycle](#recycle)中的示例。

## updateConfiguration

```TypeScript
updateConfiguration(): void
```

传递系统环境变化事件，触发节点的全量更新。可用于通知对象更新，是否触发更新由应用当前的系统环境变化决定。系统环境变化的相关信息请参见 [@ohos.app.ability.Configuration (环境变量)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md)。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ReactiveBuilderNode-updateConfiguration(): void--><!--Device-ReactiveBuilderNode-updateConfiguration(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

该示例展示了如何使用updateConfiguration接口响应系统环境变化，实现ReactiveBuilderNode构建的UI节点的动态更新。

```TypeScript
import { NodeController, ReactiveBuilderNode, FrameNode, UIContext, FrameCallback, Binding, UIUtils } from '@kit.ArkUI';
import { AbilityConstant, Configuration, ConfigurationConstant, EnvironmentCallback } from '@kit.AbilityKit';

// 自定义组件
@Component
struct TextBuilder {
  // 作为自定义组件中需要更新的属性，数据类型为基础属性，定义为@Prop
  @Prop message: string = 'TextBuilder';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 30 })
      }
      .justifyContent(FlexAlign.Center)
      .alignItems(HorizontalAlign.Center)
      .width('100%')
    }
    .width('100%')
  }
}

@Builder
function buildText(text: Binding<string>) {
  Column() {
    Text(text.value)
      .fontSize(20)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 15 })
    TextBuilder({ message: text.value }) // 自定义组件
  }
  .backgroundColor($r('sys.color.ohos_id_color_background'))
  .justifyContent(FlexAlign.Center)
  .alignItems(HorizontalAlign.Center)
  .width('100%')
  .height('100%')
}

// 继承NodeController实现自定义textNode控制器
class TextNodeController extends NodeController {
  private textNode: ReactiveBuilderNode<[Binding<string>]> | null = null;
  private message: string = '';

  constructor(message: string) {
    super();
    this.message = message;
  }

  makeNode(context: UIContext): FrameNode | null {
    return this.textNode?.getFrameNode() ? this.textNode?.getFrameNode() : null;
  }

  createNode(context: UIContext) {
    this.textNode = new ReactiveBuilderNode(context);
    this.textNode.build(wrapBuilder<[Binding<string>]>(buildText), {},
      UIUtils.makeBinding<string>(() => this.message, val => {
        this.message = val;
      }));
    builderNodeMap.push(this.textNode);
  }

  deleteNode() {
    let node = builderNodeMap.pop();
    node?.dispose();
  }

  update(message: string) {
    this.message = message;
    this.textNode?.flushState();
  }
}

// 记录创建的自定义节点对象
const builderNodeMap: Array<ReactiveBuilderNode<[text: Binding<string>]>> = new Array();

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
    // 移除builderNodeMap中的引用，并将自定义节点释放
    this.textNodeController.deleteNode();
  }

  build() {
    Row() {
      Column({ space: 12 }) {
        NodeContainer(this.textNodeController)
          .width('100%')
          .height(70)
          .backgroundColor('#FFF0F0F0')
        Button('Update')
          .onClick(() => {
            this.count += 1;
            const message = 'Update ' + this.count.toString();
            this.textNodeController.update(message);
          })
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
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

