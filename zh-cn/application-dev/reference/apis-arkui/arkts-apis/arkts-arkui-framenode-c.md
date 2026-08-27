# FrameNode

FrameNode表示组件树的实体节点，支持节点树操作、自定义绘制与布局、位置查询、动画等能力。[NodeController](arkts-arkui-nodecontroller-c.md)可通过 BuilderNode持有的FrameNode将其挂载到NodeContainer上， 也可通过FrameNode获取[RenderNode](arkts-arkui-rendernode-c.md)，挂载到其他FrameNode上。适用于需要通过代码动态创建和管理组件节点树的场景，可实现声明式组件无法直接满足的灵活 UI组合与自定义渲染需求。<!--RP2--><!--RP2End-->

> **说明：**
> 
> - 当前不支持在预览器中使用FrameNode节点。
> 
> - FrameNode节点暂不支持拖拽。
> 
> - FrameNode对象不支持使用JSON序列化。
> 
> - 在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的场景中调用[FrameNode](#framenode)对象的接口时，建议使用
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)的[runScopedTask](arkts-arkui-arkui-uicontext-uicontext-c.md#runscopedtask)接口明确UI
> 上下文，参考[执行绑定UI实例的闭包](../../../ui/arkts-global-interface.md#执行绑定ui实例的闭包)示例。
> 
> - FrameNode的接口中，仅[Optional](../arkts-components/arkts-arkui-optional-t.md)类型的必选参数支持传入null或undefined。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addComponentContent

```TypeScript
addComponentContent<T>(content: ComponentContent<T> | ReactiveComponentContent<T>): void
```

支持添加ComponentContent类型的组件内容。要求当前节点是一个可修改的节点，即[isModifiable](#ismodifiable)的返回值为true，否则抛出异常信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-arkui-componentcontent-c.md)&lt;T&gt; \| [ReactiveComponentContent](arkts-arkui-componentcontent-reactivecomponentcontent-c.md)&lt;T&gt; | 是 | FrameNode节点中显示的组件内容。<br>**起始版本：** 22 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |

## addSupportedUIStates

```TypeScript
addSupportedUIStates(uiStates: number, statesChangeHandler: UIStatesChangeHandler, excludeInner?: boolean): void
```

设置组件支持的多态样式状态。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiStates | number | 是 | 需要处理目标节点的UI状态。 可以通过位或计算同时指定多个状态，如：targetUIStates = UIState.PRESSED  \|  UIState.FOCUSED。 |
| statesChangeHandler | [UIStatesChangeHandler](arkts-arkui-uistateschangehandler-t.md) | 是 | 状态变化时的回调函数。 |
| excludeInner | boolean | 否 | 禁止内部默认状态样式处理的标志，默认值为false。内部默认状态样式处理指组件自身内置的状态样式响应（如Button按下时的默认视觉反馈）。 true表示禁止内部默认状态样式处理，false不禁止内部默认状态样式处理。 |

**示例**

请参考组件设置和删除多态样式状态示例。

## adoptChild

```TypeScript
adoptChild(child: FrameNode): void
```

当前节点接纳目标节点为附属节点。当前FrameNode如果不可修改，抛出异常信息。被接纳的附属节点不能已有父节点。调用该接口实际上不会将目标节点添加为子节点，而是仅允许当前节点接收该附属节点的生命周期回调。使用场景：当需要监听某个 节点的生命周期回调但不希望改变其父子关系或组件树结构时，可通过该接口接纳其为附属节点。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 指定待被接纳的节点。child节点不可以拥有父节点，否则抛出异常信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The current FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be disposed." |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |

**示例**

完整示例请参考接纳为附属节点示例。

## appendChild

```TypeScript
appendChild(node: FrameNode): void
```

在FrameNode最后一个子节点后添加新的子节点。当前FrameNode如果不可修改，抛出异常信息。[typeNode](arkts-arkui-typenode-n.md)在appendChild时会校验子组件类型或个数，不满足时抛出异常信息，限制 情况请查看[typeNode](arkts-arkui-typenode-n.md)描述。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 需要添加的FrameNode。node节点不可以为不可修改的FrameNode（例如通过getFrameNodeById等接口获取的声明式组件节点）。仅 BuilderNode通过getFrameNode接口获取的FrameNode可作为声明式子节点添加。若子节点不符合规格，则抛出异常信息。node节点不可以拥有父节 点，否则抛出异常信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: it cannot be adopted."<br>**适用版本：** 22+ |

**示例**

请参考节点操作示例。

## cancelAnimations

```TypeScript
cancelAnimations(properties: AnimationPropertyType[]): boolean
```

请求取消FrameNode上指定属性上的所有动画，该方法需在节点所处线程中调用，会阻塞当前线程以等待取消结果。如果动画成功取消，节点上的属性值会被恢复为取消时的显示值（即当前状态）。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| properties | [AnimationPropertyType](arkts-arkui-animationpropertytype-e.md)[] | 是 | 待取消的动画属性枚举数组。可以一次取消一个节点上的多个属性的动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示动画是否取消成功。 |

**示例**

请参考动画创建与取消示例。

## clearChildren

```TypeScript
clearChildren(): void
```

清除当前FrameNode的所有子节点。当前FrameNode如果不可修改，抛出异常信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |

**示例**

请参考节点操作示例。

## constructor

```TypeScript
constructor(uiContext: UIContext)
```

FrameNode的构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 创建对应节点时所需的UI上下文。 |

## convertPosition

```TypeScript
convertPosition(position: Position, targetNode: FrameNode): Position
```

将点的坐标从当前节点的坐标系转换为目标节点的坐标系。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-t.md) | 是 | 当前节点坐标系中的相对坐标。单位为VP。 |
| targetNode | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 本次坐标转换的目标节点，转换得到的点坐标就是该节点坐标系中的相对坐标。targetNode节点不可以为已释放的节点，且需与当前节点存在共同祖先节点，否则抛出异常信 息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 目标节点局部坐标系中的转换坐标，单位为VP。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100024](../errorcode-node.md#100024-节点没有公共祖先节点) | The current FrameNode and the target FrameNode do not have a common ancestor node. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'targetNode' is invalid: it cannot be disposed." |

**示例**

```TypeScript
@Entry
@Component
struct ConvertPositionTestOnly {
  private uiContext: UIContext = this.getUIContext();
  @State message: string = 'Hello World';
  @State nodeAOk: boolean = false;
  @State nodeBOk: boolean = false;

  build() {
    Column() {
      Text(this.message)
        .id('testNodeA')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .onAppear(() => {
          this.nodeAOk = true
        })
      Column() {
        Text('testNodeB')
          .id('testNodeB')
          .fontSize($r('app.float.page_text_font_size'))
          .fontWeight(FontWeight.Bold)
          .onAppear(() => {
            this.nodeBOk = true
          })

      }

      Button('运行convertPosition测试')
        .onClick(() => {
          this.runBasicTest();
        })
        .margin(20)

    }
    .width('100%')
    .height('100%')
  }

  private runBasicTest() {
    if (!this.nodeAOk || !this.nodeBOk) {
      return
    }

    // 等待UI渲染完成
    if (!this.uiContext) {
      return
    }
    const nodeA = this.uiContext.getAttachedFrameNodeById('testNodeA');
    const nodeB = this.uiContext.getAttachedFrameNodeById('testNodeB');

    if (!nodeA || !nodeB) {
      console.info('无法获取测试节点');
      return;
    }

    const result: Position | undefined = nodeA.convertPosition({ x: 30, y: 10 }, nodeB); // 显式声明可能返回undefined
    if (result === undefined) {
      console.info('convertPosition 转换失败，返回 undefined');
      return;
    }
    console.info(`输出: (${result.x}, ${result.y})`);

  }
}
```

## convertPositionFromWindow

```TypeScript
convertPositionFromWindow(positionByWindow: Position): Position
```

将点的坐标从当前节点所在窗口的坐标系转换为当前节点的坐标系。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionByWindow | [Position](arkts-arkui-position-t.md) | 是 | 当前节点所在窗口的坐标系中的相对坐标。单位为VP。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 当前节点坐标系中的转换坐标，单位为VP。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |
| [100028](../errorcode-node.md#100028-当前节点不在主节点树上) | The current FrameNode is not on the main tree. |

**示例**

请参考局部与窗口坐标转换示例。

## convertPositionToWindow

```TypeScript
convertPositionToWindow(positionByLocal: Position): Position
```

将点的坐标从当前节点的坐标系转换为当前节点所在窗口的坐标系。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionByLocal | [Position](arkts-arkui-position-t.md) | 是 | 当前节点坐标系中的相对坐标。单位为VP。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 当前节点所在窗口的坐标系中的转换坐标，单位为VP。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |
| [100028](../errorcode-node.md#100028-当前节点不在主节点树上) | The current FrameNode is not on the main tree. |

**示例**

请参考局部与窗口坐标转换示例。

## createAnimation

```TypeScript
createAnimation(property: AnimationPropertyType, startValue: Optional<number[]>, endValue: number[], param: AnimateParam): boolean
```

创建FrameNode上属性的动画。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [AnimationPropertyType](arkts-arkui-animationpropertytype-e.md) | 是 | 动画属性枚举。 |
| startValue | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;number[]&gt; | 是 | 动画属性的起始值。取值为undefined或数组，取值为数组时数组长度需要和属性枚举匹配。如果为undefined则表示不显式指定动画初值，节点 上一次设置的属性终值为此次动画的起点值。如果取值为数组，   - 对于AnimationPropertyType.ROTATION，取值格式为[rotationX, rotationY, rotationZ]，单位为度 （°），表示绕x、y、z轴的旋转角。   - 对于AnimationPropertyType.TRANSLATION，取值格式为[translateX, translateY]，单位为px，表示沿x、y轴的平移量。   - 对于AnimationPropertyType.SCALE，取值格式为[scaleX, scaleY]，表示x、y方向的缩放比例。   - 对于AnimationPropertyType.OPACITY，取 值格式为[opacity]，表示不透明度。opacity的取值范围为[0, 1]，超出范围的值会被钳位到[0, 1]，动画正常创建。   当节点上从未设置过该属性时，需要显式指定startValue才能正常创建动画。当 节点上已经设置过属性（如第二次及之后创建动画），则推荐不显式指定startValue或者显式指定startValue为上一次的终值，表示使用上一次的终值作为新的动画起点，避免起始值跳变。 |
| endValue | number[] | 是 | 动画属性的终止值。取值为数组，数组长度需要和属性枚举匹配。   - 对于AnimationPropertyType.ROTATION，取值格式为 [rotationX, rotationY, rotationZ]，单位为度（°），表示绕x、y、z轴的旋转角。   - 对于AnimationPropertyType.TRANSLATION，取值格式为 [translateX, translateY]，单位为px，表示沿x、y轴的平移量。   - 对于AnimationPropertyType.SCALE，取值格式为[scaleX, scaleY]，表示x、y方向的缩 放比例。   - 对于AnimationPropertyType.OPACITY，取值格式为[opacity]，表示不透明度。opacity的取值范围为[0, 1]，超出范围的值会被钳位到[0, 1]，动画正常创建。 |
| param | [AnimateParam](../arkts-components/arkts-arkui-animateparam-i.md) | 是 | 动画参数。包含时长、动画曲线、结束回调等参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示动画是否创建成功。 |

**示例**

请参考动画创建与取消示例。

## createFrameNodes

```TypeScript
static createFrameNodes(uiContext: UIContext, count: number): FrameNode[]
```

批量创建指定数量的FrameNode，返回FrameNode数组。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 创建对应节点时所需的UI上下文。 |
| count | number | 是 | 指定创建节点的数量，取值范围为大于零的整型。若给定值小于等于0或不是整数，则返回空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md)[] | 创建的FrameNode数组。 |

**示例**

```TypeScript
import { NodeController, FrameNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    // 创建20个FrameNode添加到根节点中。
    const children: FrameNode[] = FrameNode.createFrameNodes(uiContext, 20);
    for (let i = 0; i < children.length; i++) {
      this.rootNode.appendChild(children[i]);
    }
    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .width(300)
        .height(300)
    }.width('100%')
  }
}
```

## dispose

```TypeScript
dispose(): void
```

立即解除当前FrameNode对象对实体FrameNode节点的引用关系。

> **说明：**
> 
> - FrameNode对象调用dispose后，由于不对应任何实体FrameNode节点，在调用部分查询接口([getMeasuredSize](#getmeasuredsize)、
> [getLayoutPosition](#getlayoutposition))的时候会导致应用出现jscrash。
> 
> - 通过[getUniqueId](#getuniqueid)可以判断当前FrameNode是否对应一个实体FrameNode节点。当UniqueID大于0时表示该对象对应一个实体
> FrameNode节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { NodeController, FrameNode, BuilderNode } from '@kit.ArkUI';

@Component
struct TestComponent {
  build() {
    Column() {
      Text('This is a BuilderNode.')
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

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private builderNode: BuilderNode<[]> | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.builderNode = new BuilderNode(uiContext, { selfIdealSize: { width: 200, height: 100 } });
    this.builderNode.build(new WrappedBuilder(buildComponent));

    const rootRenderNode = this.rootNode.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode.size = { width: 200, height: 200 };
      rootRenderNode.backgroundColor = 0xffd5d5d5;
      rootRenderNode.appendChild(this.builderNode!.getFrameNode()!.getRenderNode());
    }

    return this.rootNode;
  }

  disposeFrameNode() {
    if (this.rootNode !== null && this.builderNode !== null) {
      // 解除rootNode对实体FrameNode节点的引用关系前，移除rootNode的所有子节点
      this.rootNode.removeChild(this.builderNode.getFrameNode());
      // 解除builderNode对实体FrameNode节点的引用关系
      this.builderNode.dispose();
      // 解除rootNode对实体FrameNode节点的引用关系
      this.rootNode.dispose();
    }
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
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column({ space: 4 }) {
      NodeContainer(this.myNodeController)
      Button('FrameNode dispose')
        .onClick(() => {
          this.myNodeController.disposeFrameNode();
        })
        .width('100%')
    }
  }
}
```

## disposeTree

```TypeScript
disposeTree(): void
```

下树并递归释放当前节点为根的子树。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
import { FrameNode, NodeController, BuilderNode } from '@kit.ArkUI';

// 自定义挂载事件的自定义组件，作为自定义组件树的入口
@Component
struct TestComponent {
  private myNodeController: MyNodeController = new MyNodeController(wrapBuilder(buildComponent2));

  build() {
    Column() {
      Text('This is a BuilderNode.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)
      NodeContainer(this.myNodeController)
    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('BuilderNode aboutToAppear');
  }

  aboutToDisappear() {
    console.info('BuilderNode aboutToDisappear');
  }
}

// 自定义挂载事件的自定义组件，作为TestComponent1的子组件与TestComponent3、TestComponent4的父组件
@Component
struct TestComponent2 {
  private myNodeController: MyNodeController = new MyNodeController(wrapBuilder(buildComponent3));
  private myNodeController2: MyNodeController = new MyNodeController(wrapBuilder(buildComponent4));

  build() {
    Column() {
      Text('This is a BuilderNode 2.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)
      NodeContainer(this.myNodeController)
      NodeContainer(this.myNodeController2)
    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('BuilderNode 2 aboutToAppear');
  }

  aboutToDisappear() {
    console.info('BuilderNode 2 aboutToDisappear');
  }
}

// 自定义挂载事件的自定义组件，作为buildComponent2的子组件
@Component
struct TestComponent3 {
  build() {
    Column() {
      Text('This is a BuilderNode 3.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)

    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('BuilderNode 3 aboutToAppear');
  }

  aboutToDisappear() {
    console.info('BuilderNode 3 aboutToDisappear');
  }
}

// 自定义挂载事件的自定义组件，作为buildComponent2的子组件
@Component
struct TestComponent4 {
  build() {
    Column() {
      Text('This is a BuilderNode 4.')
        .fontSize(16)
        .fontWeight(FontWeight.Bold)

    }
    .width('100%')
    .backgroundColor(Color.Gray)
  }

  aboutToAppear() {
    console.info('BuilderNode 4 aboutToAppear');
  }

  aboutToDisappear() {
    console.info('BuilderNode 4 aboutToDisappear');
  }
}

@Builder
function buildComponent() {
  TestComponent()
}

@Builder
function buildComponent2() {
  TestComponent2()
}

@Builder
function buildComponent3() {
  TestComponent3()
}

@Builder
function buildComponent4() {
  TestComponent4()
}

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private builderNode: BuilderNode<[]> | null = null;
  private wrappedBuilder: WrappedBuilder<[]>;

  constructor(builder: WrappedBuilder<[]>) {
    super();
    this.wrappedBuilder = builder;
  }

  makeNode(uiContext: UIContext): FrameNode | null {
    this.builderNode = new BuilderNode(uiContext, { selfIdealSize: { width: 200, height: 100 } });
    this.builderNode.build(this.wrappedBuilder);

    return this.builderNode.getFrameNode();
  }

  dispose() {
    if (this.builderNode !== null) {
      // 下树并递归释放当前节点为根的子树
      this.builderNode.getFrameNode()?.disposeTree()
    }
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
  private myNodeController: MyNodeController = new MyNodeController(wrapBuilder(buildComponent));

  build() {
    Column({ space: 4 }) {
      NodeContainer(this.myNodeController)
      Button('BuilderNode dispose')
        .onClick(() => {
          this.myNodeController.dispose();
        })
        .width('100%')
      Button('BuilderNode rebuild')
        .onClick(() => {
          this.myNodeController.rebuild();
        })
        .width('100%')
    }
  }
}
```

## getChild

```TypeScript
getChild(index: number): FrameNode | null
```

获取当前节点指定位置的子节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 需要查询的子节点的序列号。index取值范围为[0, +∞)，若当前节点有n个子节点，index取值有效范围为[0, n-1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | 子节点。若该FrameNode不包含所查询的子节点，则返回空对象null。 |

**示例**

请参考节点操作示例。

## getChild

```TypeScript
getChild(index: number, expandMode?: ExpandMode): FrameNode | null
```

获取当前节点指定位置的子节点，支持指定子节点展开模式。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 需要查询的子节点的序列号。index取值范围为[0, +∞)，若当前节点有n个子节点，index取值有效范围为[0, n-1]。 |
| expandMode | [ExpandMode](arkts-arkui-framenode-expandmode-e.md) | 否 | 指定子节点展开模式。默认值：ExpandMode.EXPAND |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | 子节点。若该FrameNode不包含所查询的子节点，则返回空对象null。 |

**示例**

请参考LazyForEach场景节点操作示例。

## getChildrenCount

```TypeScript
getChildrenCount(): number
```

获取当前FrameNode的子节点数量。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前FrameNode的子节点数量。 |

**示例**

请参考节点操作示例。

## getChildrenCount

```TypeScript
getChildrenCount(countMode?: ChildrenCountMode): number
```

根据指定的计数模式获取当前FrameNode的子节点数量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| countMode | [ChildrenCountMode](arkts-arkui-framenode-childrencountmode-e.md) | 否 | The children count mode. Default value is ChildrenCountMode.ALL_EXPAND. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Returns the number of children of the current FrameNode based on the count mode. |

**示例**

```TypeScript
import { NodeController, FrameNode, UIContext, BuilderNode, ChildrenCountMode, LengthUnit } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// BasicDataSource实现了IDataSource接口，用于管理listener监听，以及通知LazyForEach数据更新
class BasicDataSource implements IDataSource {
  private listeners: DataChangeListener[] = [];
  private originDataArray: string[] = [];

  public totalCount(): number {
    return 0;
  }

  public getData(index: number): string {
    return this.originDataArray[index];
  }

  // 该方法为框架侧调用，为LazyForEach组件向其数据源处添加listener监听
  registerDataChangeListener(listener: DataChangeListener): void {
    if (this.listeners.indexOf(listener) < 0) {
      console.info('add listener');
      this.listeners.push(listener);
    }
  }

  // 该方法为框架侧调用，为对应的LazyForEach组件在数据源处去除listener监听
  unregisterDataChangeListener(listener: DataChangeListener): void {
    const pos = this.listeners.indexOf(listener);
    if (pos >= 0) {
      console.info('remove listener');
      this.listeners.splice(pos, 1);
    }
  }

  // 通知LazyForEach组件需要重载所有子组件
  notifyDataReload(): void {
    this.listeners.forEach(listener => {
      listener.onDataReloaded();
    })
  }

  // 通知LazyForEach组件需要在index对应索引处添加子组件
  notifyDataAdd(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataAdd(index);
    })
  }

  // 通知LazyForEach组件在index对应索引处数据有变化，需要重建该子组件
  notifyDataChange(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataChange(index);
    })
  }

  // 通知LazyForEach组件需要在index对应索引处删除该子组件
  notifyDataDelete(index: number): void {
    this.listeners.forEach(listener => {
      listener.onDataDelete(index);
    })
  }

  // 通知LazyForEach组件将from索引和to索引处的子组件进行交换
  notifyDataMove(from: number, to: number): void {
    this.listeners.forEach(listener => {
      listener.onDataMove(from, to);
    })
  }

  notifyDatasetChange(operations: DataOperation[]): void {
    this.listeners.forEach(listener => {
      listener.onDatasetChange(operations);
    })
  }
}

// 自定义数据管理类管理string数组
class MyDataSource extends BasicDataSource {
  private dataArray: string[] = []

  public totalCount(): number {
    return this.dataArray.length;
  }

  public getData(index: number): string {
    return this.dataArray[index];
  }

  public addData(index: number, data: string): void {
    this.dataArray.splice(index, 0, data);
    this.notifyDataAdd(index);
  }

  public pushData(data: string): void {
    this.dataArray.push(data);
    this.notifyDataAdd(this.dataArray.length - 1);
  }
}

class Params {
  data: MyDataSource | null = null;
  scroller: Scroller | null = null;

  constructor(data: MyDataSource, scroller: Scroller) {
    this.data = data;
    this.scroller = scroller;
  }
}

@Builder
function buildData(params: Params) {
  List({ scroller: params.scroller }) {
    LazyForEach(params.data, (item: string) => {
      ListItem() {
        Column() {
          Text(item)
            .fontSize(20)
            .onAppear(() => {
              console.info(`${TEST_TAG} node appear: ${item}`)
            })
            .backgroundColor(Color.Pink)
            .margin({
              top: 30,
              bottom: 30,
              left: 10,
              right: 10
            })
        }
      }
      .id(item)
    }, (item: string) => item)
  }
  .cachedCount(5)
  .listDirection(Axis.Horizontal)
}

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;
  private data: MyDataSource = new MyDataSource();
  private scroller: Scroller = new Scroller();

  makeNode(uiContext: UIContext): FrameNode | null {
    this.uiContext = uiContext;
    for (let i = 0; i <= 20; i++) {
      this.data.pushData(`N${i}`);
    }
    const params: Params = new Params(this.data, this.scroller);
    const dataNode: BuilderNode<[Params]> = new BuilderNode(uiContext);
    dataNode.build(wrapBuilder<[Params]>(buildData), params);
    this.rootNode = dataNode.getFrameNode();
    const scrollToIndexOptions: ScrollToIndexOptions = {
      extraOffset: {
        value: 20, unit: LengthUnit.VP
      }
    };
    this.scroller.scrollToIndex(6, true, ScrollAlign.START, scrollToIndexOptions);
    return this.rootNode;
  }

  getChildCountAllExpand() {
    const childCount = this.rootNode?.getChildrenCount(ChildrenCountMode.ALL_EXPAND);
    console.info(TEST_TAG + 'ALL_EXPAND, childCount=' + childCount);
  }

  getChildCountOnlyExpanded() {
    const childCount = this.rootNode?.getChildrenCount(ChildrenCountMode.ONLY_EXPANDED);
    console.info(TEST_TAG + 'ONLY_EXPANDED, childCount=' + childCount);
  }
  
  getChildCountAllNotExpand() {
    const childCount = this.rootNode?.getChildrenCount(ChildrenCountMode.ALL_NOT_EXPAND);
    console.info(TEST_TAG + 'ALL_NOT_EXPAND, childCount=' + childCount);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getChildCount(ALL_EXPAND)')
          .width(300)
          .onClick(() => {
            this.myNodeController.getChildCountAllExpand();
          })
        Button('getChildCount(ONLY_EXPANDED)')
          .width(300)
          .onClick(() => {
            this.myNodeController.getChildCountOnlyExpanded();
          })
        Button('getChildCount(ALL_NOT_EXPAND)')
          .width(300)
          .onClick(() => {
            this.myNodeController.getChildCountAllNotExpand();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
  }
}
```

## getCrossLanguageOptions

```TypeScript
getCrossLanguageOptions(): CrossLanguageOptions
```

获取当前FrameNode的跨ArkTS语言访问选项。例如ArkTS语言创建的节点，返回该节点是否可通过非ArkTS语言进行属性设置和跨语言组件树操作，从API版本26.0.0开始支持获取是否可通过非ArkTS语言进行组件树操作。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CrossLanguageOptions](arkts-arkui-framenode-crosslanguageoptions-i.md) | 跨ArkTS语言访问选项。 |

**示例**

请参考节点操作示例。

## getCustomProperty

```TypeScript
getCustomProperty(name: string): Object | undefined
```

通过名称获取组件的自定义属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 自定义属性的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object \| undefined | 自定义属性的值。 |

**示例**

请参考节点操作示例。

## getFirstChild

```TypeScript
getFirstChild(): FrameNode | null
```

获取当前FrameNode的第一个子节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | 首个子节点。若该FrameNode不包含子节点，则返回空对象null。 |

**示例**

请参考节点操作示例。

## getFirstChildIndexWithoutExpand

```TypeScript
getFirstChildIndexWithoutExpand(): number
```

获取当前节点第一个在主节点树上的子节点的序列号。子节点序列号按所有子节点计算。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前节点第一个在主节点树上的子节点的序列号。 |

**示例**

请参考LazyForEach场景节点操作示例。

## getFrameNodeById

```TypeScript
getFrameNodeById(id: string): FrameNode | null
```

以当前节点为根节点，逐层查找所有子节点，返回第一个匹配指定id的节点。查找顺序为：先查找直接子节点，再查找二级子节点，依此类推，找到后立即返回。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 查询的子节点id，为通用属性设置的组件标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | 以当前节点为根节点，逐层查找所有子节点，返回第一个匹配指定id的节点。若当前节点所有的子节点中都不存在匹配该id的节点，则返回空对象null。 |

**示例**

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public rootNode: FrameNode | null = null;
  private id: string = 'text';

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    // 创建Column。
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    this.rootNode.appendChild(col);

    // 创建Text组件添加到Column中。
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize('Hello').id(this.id);
    col.appendChild(text);

    // 再次创建相同ID的Text组件添加到Column中。
    let text1 = typeNode.createNode(uiContext, 'Text');
    text1.initialize('World').id(this.id);
    col.appendChild(text1);
    this.update();
    return this.rootNode;
  }

  update() {
    if (this.rootNode) {
      // 查询并返回首个ID为“text”的组件，并设置backgroundColor属性。
      let node = this.rootNode.getFrameNodeById(this.id);
      node?.commonAttribute.backgroundColor('rgb(39,135,217)');
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .width(300)
        .height(300)
    }.width('100%')
  }
}
```

## getFrameNodeByUniqueId

```TypeScript
getFrameNodeByUniqueId(id: number): FrameNode | null
```

以当前节点为根节点，查找并返回指定UniqueID（系统分配的节点唯一标识，该标识可通过[getUniqueId](#getuniqueid)接口获取）的子节点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 查询的子节点的唯一标识UniqueID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | 以当前节点为根节点，查找到指定UniqueID的子节点。若当前节点无法查找到该UniqueID的子节点，则返回空对象null。 |

**示例**

```TypeScript
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public rootNode: FrameNode | null = null;
  private uniqueId: number = 0;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    // 创建Column。
    let col = typeNode.createNode(uiContext, 'Column');
    col.initialize({ space: 5 });
    this.rootNode.appendChild(col);

    // 创建Text组件添加到Column中。
    let text = typeNode.createNode(uiContext, 'Text');
    text.initialize('Hello');
    col.appendChild(text);

    // 再次创建Text组件添加到Column中。
    let text1 = typeNode.createNode(uiContext, 'Text');
    text1.initialize('World');
    this.uniqueId = text1.getUniqueId();
    col.appendChild(text1);
    this.update();
    return this.rootNode;
  }

  update() {
    if (this.rootNode) {
      // 查询并返回指定UniqueID的组件，并设置backgroundColor属性。
      let node = this.rootNode.getFrameNodeByUniqueId(this.uniqueId);
      node?.commonAttribute.backgroundColor('rgb(39,135,217)');
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Column() {
      NodeContainer(this.myNodeController)
        .borderWidth(1)
        .width(300)
        .height(300)
    }.width('100%')
  }
}
```

## getGlobalPositionOnDisplay

```TypeScript
getGlobalPositionOnDisplay(): Position
```

获取FrameNode相对于全局屏幕的位置偏移，单位为VP。与[getPositionToScreen](#getpositiontoscreen)的坐标系参考不同，请根据实际场景选择使用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 节点相对于全局屏幕的位置偏移，单位为VP。 |

**示例**

请参考节点操作示例。

## getId

```TypeScript
getId(): string
```

获取用户设置的节点ID（通用属性设置的组件标识）。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 用户设置的节点ID（通用属性设置的[组件标识]{ |

**示例**

请参考节点操作示例。

## getInspectorInfo

```TypeScript
getInspectorInfo(): Object
```

获取节点的结构信息，该信息和DevEco Studio内置<!--RP1-->ArkUI Inspector<!--RP1End-->工具里面的一致。

> **说明：**
> 
> getInspectorInfo接口用于获取所有节点的信息，作为调试接口使用，频繁调用会导致性能下降。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 节点的结构信息。 |

**示例**

请参考节点操作示例。

## getInteractionEventBindingInfo

```TypeScript
getInteractionEventBindingInfo(eventType: EventQueryType): InteractionEventBindingInfo | undefined
```

获取目标节点的事件绑定信息，如果该组件节点上没有绑定要查询的交互事件类型时，返回 undefined。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | [EventQueryType](arkts-arkui-eventquerytype-e.md) | 是 | 要查询的交互事件类型。例如EventQueryType.ON_CLICK表示查询点击事件的绑定信息，各枚举值的具体含义请参考 [EventQueryType](arkts-arkui-eventquerytype-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InteractionEventBindingInfo](arkts-arkui-framenode-interactioneventbindinginfo-i.md) \| undefined | 如果当前节点上绑定了所查询类型的交互事件，则返回一个InteractionEventBindingInfo对象，指示事件绑定 详细信息，如果没有绑定所查询类型的交互事件则返回undefined。 |

**示例**

请参考节点操作示例。

## getLastChildIndexWithoutExpand

```TypeScript
getLastChildIndexWithoutExpand(): number
```

获取当前节点最后一个在主节点树上的子节点的序列号。子节点序列号按所有子节点计算。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前节点最后一个在主节点树上的子节点的序列号。 |

**示例**

请参考LazyForEach场景节点操作示例。

## getLayoutPosition

```TypeScript
getLayoutPosition(): Position
```

获取FrameNode布局后相对于父组件的位置偏移，单位为PX。该偏移是父容器对该节点进行布局之后的结果，因此布局之后生效的offset属性和不参与布局的position属性不影响该偏移值。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 节点布局后相对于父组件的位置偏移，单位为PX。 |

**示例**

请参考节点操作示例。

## getMeasuredSize

```TypeScript
getMeasuredSize(): Size
```

获取FrameNode测量后的大小，单位为PX。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Size | 节点测量后的大小，单位为PX。 |

**示例**

请参考节点操作示例。

## getNextSibling

```TypeScript
getNextSibling(): FrameNode | null
```

获取当前FrameNode的下一个同级节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | 当前FrameNode的下一个同级节点。若该FrameNode不包含下一个同级节点，则返回空对象null。 |

**示例**

请参考节点操作示例。

## getNodePropertyValue

```TypeScript
getNodePropertyValue(property: AnimationPropertyType): number[]
```

获取FrameNode上的属性值。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [AnimationPropertyType](arkts-arkui-animationpropertytype-e.md) | 是 | 动画属性枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | 表示FrameNode上的属性值，返回的数组长度与属性枚举相关，异常时返回空数组。 |

**示例**

请参考动画创建与取消示例。

## getNodeType

```TypeScript
getNodeType(): string
```

获取节点的类型。系统组件类型为组件名称，例如，按钮组件Button的类型为Button。而对于自定义组件，若其有渲染内容，则其类型为 __Common__。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 节点的类型。 |

**示例**

请参考节点操作示例。

## getOpacity

```TypeScript
getOpacity(): number
```

获取节点的不透明度，最小值为0，最大值为1。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 节点的不透明度。范围是[0, 1]，值越大透明度越低。 |

**示例**

请参考节点操作示例。

## getParent

```TypeScript
getParent(): FrameNode | null
```

获取当前FrameNode的父节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | 当前FrameNode的父节点。若该FrameNode不包含父节点，则返回空对象null。 |

**示例**

请参考节点操作示例和获取根节点示例。

## getPositionToParent

```TypeScript
getPositionToParent(): Position
```

获取FrameNode相对于父组件的位置偏移，单位为VP。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 节点相对于父组件的位置偏移，单位为VP。 |

**示例**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToParent() {
    // 获取FrameNode相对于父组件的位置偏移
    let positionToParent = this.rootNode?.getPositionToParent();
    console.info(`${TEST_TAG}${JSON.stringify(positionToParent)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToParent')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToParent();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
  }
}
```

## getPositionToParentWithTransform

```TypeScript
getPositionToParentWithTransform(): Position
```

获取FrameNode相对于父组件带有绘制属性的位置偏移，单位为VP，绘制属性比如transform、 translate等，返回的坐标是组件布局时左上角变换后的坐标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 节点相对于父组件的位置偏移，单位为VP。当设置了其他（比如：transform、translate等）绘制属性，由于浮点数精度的影响，返回值会有微小偏差。 |

**示例**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToParentWithTransform() {
    // 获取FrameNode相对于父组件带有绘制属性的位置偏移
    let positionToParentWithTransform = this.rootNode?.getPositionToParentWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToParentWithTransform)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToParentWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToParentWithTransform();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
  }
}
```

## getPositionToScreen

```TypeScript
getPositionToScreen(): Position
```

获取FrameNode相对于屏幕的位置偏移，单位为VP。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 节点相对于屏幕的位置偏移，单位为VP。 |

**示例**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToScreen() {
    // 获取FrameNode相对于屏幕的位置偏移
    let positionToScreen = this.rootNode?.getPositionToScreen();
    console.info(`${TEST_TAG}${JSON.stringify(positionToScreen)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToScreen')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToScreen();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
  }
}
```

## getPositionToScreenWithTransform

```TypeScript
getPositionToScreenWithTransform(): Position
```

获取FrameNode相对于屏幕带有绘制属性的位置偏移，单位为VP，绘制属性比如transform、 translate等，返回的坐标是组件布局时左上角变换后的坐标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 节点相对于屏幕的位置偏移，单位为VP。 当设置了其他（比如：transform、translate等）绘制属性，由于浮点数精度的影响，返回值会有微小偏差。 |

**示例**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToScreenWithTransform() {
    // 获取FrameNode相对于屏幕带有绘制属性的位置偏移
    let positionToScreenWithTransform = this.rootNode?.getPositionToScreenWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToScreenWithTransform)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToScreenWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToScreenWithTransform();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
  }
}
```

## getPositionToWindow

```TypeScript
getPositionToWindow(): Position
```

获取FrameNode相对于窗口的位置偏移，单位为VP。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 节点相对于窗口的位置偏移，单位为VP。 |

**示例**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToWindow() {
    // 获取FrameNode相对于窗口的位置偏移
    let positionToWindow = this.rootNode?.getPositionToWindow();
    console.info(`${TEST_TAG}${JSON.stringify(positionToWindow)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('getPositionToWindow')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToWindow();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
  }
}
```

## getPositionToWindowWithTransform

```TypeScript
getPositionToWindowWithTransform(): Position
```

获取FrameNode相对于窗口带有绘制属性的位置偏移，单位为VP，绘制属性比如transform、 translate等，返回的坐标是组件布局时左上角变换后的坐标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-t.md) | 节点相对于窗口的位置偏移，单位为VP。 当设置了其他（比如：transform、translate等）绘制属性，由于浮点数精度的影响，返回值会有微小偏差。 |

**示例**

```TypeScript
import { NodeController, FrameNode, UIContext } from '@kit.ArkUI';

const TEST_TAG: string = 'FrameNode ';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.rootNode.appendChild(this.frameNode);
    return this.rootNode;
  }

  getPositionToWindowWithTransform() {
    // 获取FrameNode相对于窗口带有绘制属性的位置偏移
    let positionToWindowWithTransform = this.rootNode?.getPositionToWindowWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToWindowWithTransform)}`);
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }
        Button('getPositionToWindowWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToWindowWithTransform();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
  }
}
```

## getPreviousSibling

```TypeScript
getPreviousSibling(): FrameNode | null
```

获取当前FrameNode的上一个同级节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) \| null | 当前FrameNode的上一个同级节点。若该FrameNode不包含上一个同级节点，则返回空对象null。 |

**示例**

请参考节点操作示例。

## getRenderNode

```TypeScript
getRenderNode(): RenderNode | null
```

获取FrameNode中持有的[RenderNode](arkts-arkui-rendernode-c.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-arkui-rendernode-c.md) \| null | 一个RenderNode对象。若该FrameNode不包含RenderNode，则返回空对象null。如果当前FrameNode为声明式组件创建的节点，则返回null。 |

**示例**

```TypeScript
import { NodeController, FrameNode } from '@kit.ArkUI';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  private rootNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);

    // 获取rootNode持有的RenderNode
    const renderNode = this.rootNode.getRenderNode();
    if (renderNode !== null) {
      renderNode.size = { width: 100, height: 100 };
      renderNode.backgroundColor = 0XFFFF0000;
    }

    return this.rootNode;
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();

  build() {
    Row() {
      NodeContainer(this.myNodeController)
    }
  }
}
```

## getUniqueId

```TypeScript
getUniqueId(): number
```

获取系统分配的节点唯一标识（UniqueID）。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 系统分配的节点唯一标识（UniqueID）。 |

**示例**

请参考节点操作示例。

## getUserConfigBorderWidth

```TypeScript
getUserConfigBorderWidth(): Edges<LengthMetrics>
```

获取用户设置的边框宽度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Edges](arkts-arkui-graphics-edges-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt; | 用户设置的边框宽度。 |

**示例**

请参考节点操作示例。

## getUserConfigMargin

```TypeScript
getUserConfigMargin(): Edges<LengthMetrics>
```

获取用户设置的外边距。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Edges](arkts-arkui-graphics-edges-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt; | 用户设置的外边距。 |

**示例**

请参考节点操作示例。

## getUserConfigPadding

```TypeScript
getUserConfigPadding(): Edges<LengthMetrics>
```

获取用户设置的内边距。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Edges](arkts-arkui-graphics-edges-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt; | 用户设置的内边距。 |

**示例**

请参考节点操作示例。

## getUserConfigSize

```TypeScript
getUserConfigSize(): SizeT<LengthMetrics>
```

获取用户设置的宽高。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt; | 用户设置的宽高。 |

**示例**

请参考节点操作示例。

## insertChildAfter

```TypeScript
insertChildAfter(child: FrameNode, sibling: FrameNode | null): void
```

在FrameNode指定子节点之后添加新的子节点。当前FrameNode如果不可修改，抛出异常信息。[typeNode](arkts-arkui-typenode-n.md)在insertChildAfter时会校验子组件类型或个数，不满足时抛出异常信 息，限制情况请查看[typeNode](arkts-arkui-typenode-n.md)描述。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 需要添加的子节点。child节点不可以为不可修改的FrameNode（例如通过getFrameNodeById等接口获取的声明式组件节点）。仅 BuilderNode通过getFrameNode接口获取的FrameNode可作为声明式子节点添加。若子节点不符合规格，则抛出异常信息。child节点不可以拥有父 节点，否则抛出异常信息。 |
| sibling | [FrameNode](arkts-arkui-framenode-c.md) \| null | 是 | 新节点将插入到该节点之后。若该参数设置为空，则新节点将插入到首个子节点之前。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be adopted."<br>**适用版本：** 22+ |

**示例**

请参考节点操作示例。

## invalidate

```TypeScript
invalidate(): void
```

该方法会触发FrameNode自绘制内容的重新渲染，即重新调用[onDraw](#ondraw)方法进行自绘制。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## invalidateAttributes

```TypeScript
invalidateAttributes(): void
```

在当前帧触发节点属性更新。当前节点的属性在构建阶段后被修改，这些改动不会立即生效，而是延迟到下一帧统一处理。此功能强制当前帧内即时节点更新，确保同步应用渲染效果。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

从API version 21开始，通过if else动态切换两个节点，并且在节点创建时调用invalidateAttributes即时触发节点属性更新，避免组件切换过程中出现闪烁。

```TypeScript
// index.ets
import { FrameNode, NodeController, typeNode, NodeContent } from '@kit.ArkUI';

// 继承NodeController实现自定义NodeAdapter控制器
class MyNodeAdapterController extends NodeController {
  rootNode: FrameNode | null = null;
  imageUrl: string = '';

  constructor(imageUrl: string) {
    super();
    this.imageUrl = imageUrl;
  }

  makeNode(uiContext: UIContext): FrameNode | null {
    let imageNode = typeNode.createNode(uiContext, 'Image');
    imageNode.initialize($r(this.imageUrl))
    imageNode.attribute.syncLoad(true).width(100).height(100);
    // 强制当前帧内即时节点更新，避免出现切换闪烁
    imageNode.invalidateAttributes();
    return imageNode;
  }
}

// 自定义挂载事件的自定义组件，挂载前加载样例图片
@Component
struct NodeComponent3 {
  private rootSlot: NodeContent = new NodeContent();

  aboutToAppear(): void {
    const uiContext = this.getUIContext();
    let imageNode = typeNode.createNode(uiContext, 'Image');
    imageNode.initialize($r('app.media.startIcon'))
    imageNode.attribute.syncLoad(true).width(100).height(100);
    imageNode.invalidateAttributes();
    this.rootSlot.addFrameNode(imageNode);
  }

  build() {
    ContentSlot(this.rootSlot)
  }
}

// 自定义挂载事件的自定义组件，挂载前加载样例图片
@Component
struct NodeComponent4 {
  private rootSlot: NodeContent = new NodeContent();

  aboutToAppear(): void {
    const uiContext = this.getUIContext();
    let imageNode = typeNode.createNode(uiContext, 'Image');
    imageNode.initialize($r('app.media.startIcon'))
    imageNode.attribute.syncLoad(true).width(100).height(100);
    imageNode.invalidateAttributes();
    this.rootSlot.addFrameNode(imageNode);
  }

  build() {
    ContentSlot(this.rootSlot)
  }
}

@Entry
@Component
struct ListNodeTest {
  @State flag: boolean = true;
  adapterController: MyNodeAdapterController = new MyNodeAdapterController('app.media.startIcon');

  build() {
    Column() {
      Text('ListNode Adapter');
      if (this.flag) {
        NodeComponent3()
      } else {
        NodeComponent4()
      }
      if (this.flag) {
        NodeContainer(this.adapterController)
          .width(300).height(300)
          .borderWidth(1).borderColor(Color.Black)
      } else {
        NodeContainer(this.adapterController)
          .width(300).height(300)
          .borderWidth(1).borderColor(Color.Black)
      }
      if (this.flag) {
        Image($r('app.media.startIcon')).width(100).height(100).syncLoad(true)
      } else {
        Image($r('app.media.startIcon')).width(100).height(100).syncLoad(true)
      }
      Button('change').onClick(() => {
        this.flag = !this.flag;
      })
    }
    .borderWidth(1)
    .width('100%')
  }
}
```

## isAttached

```TypeScript
isAttached(): boolean
```

获取节点是否被挂载到主节点树上。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否被挂载到主节点树上。 |

**示例**

请参考节点操作示例。

## isClipToFrame

```TypeScript
isClipToFrame(): boolean
```

获取节点是否剪裁到组件区域。当调用[dispose](#dispose)解除对实体FrameNode节点的引用关系之后，返回值为true。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否剪裁到组件区域。 |

**示例**

请参考节点操作示例。

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前FrameNode对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用该节点的其他接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节 点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

**示例**

请参考检验FrameNode是否有效示例。

请参考检验NodeAdapter是否有效示例。

## isInRenderState

```TypeScript
isInRenderState(): boolean
```

获取节点是否处于渲染状态，如果一个节点的对应RenderNode在渲染树上，则处于渲染状态。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否处于渲染状态。 |

**示例**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  @State message: string = 'is on render tree';
  @State @Watch('change') isShow: boolean = true;
  data: Array<string> = ['hello1', 'hello2', 'hello3', 'hello4', 'hello5', 'hello6', 'hello7', 'hello8'];

  // 监听状态变化后打印是否处于渲染状态
  change() {
    let buttonNode = this.getUIContext().getFrameNodeById('testButton');
    if (buttonNode == null) {
      return;
    }
    let isOnRenderTree = buttonNode!.isInRenderState();
    if (isOnRenderTree) {
      hilog.info(1, 'frameNode', 'is on render tree');
    } else {
      hilog.info(1, 'frameNode', 'is not on render tree');
    }
  }

  build() {
    Column() {
      Button('change button visibility').onClick(() => {
        // 修改button的visibility状态
        this.isShow = !this.isShow;
      })
        .margin({ top: 20 })
      Button('test button')
        .visibility(this.isShow ? Visibility.Visible : Visibility.Hidden)
        .margin(20).id('testButton')

      List() {
        ForEach(this.data, (item: string, index: number) => {
          ListItem() {
            Text(item).id(item)
          }.alignSelf(ItemAlign.Center).width('100%')
        })
      }
      .width('30%')
      .alignSelf(ItemAlign.Center)
      .height('10%')
      .onReachEnd(() => {
        let textNode8 = this.getUIContext().getFrameNodeById('hello8');
        if (textNode8 != null) {
          let isOnRenderTree = textNode8!.isInRenderState();
          hilog.info(1, 'frameNode', 'is hello8 on RenderTree: %{public}s', isOnRenderTree);
        }
        let textNode1 = this.getUIContext().getFrameNodeById('hello1');
        if (textNode1 != null) {
          let isOnRenderTree = textNode1!.isInRenderState();
          if (isOnRenderTree) { this.message = 'is on render tree'; }
          hilog.info(1, 'frameNode', 'is hello1 on RenderTree: %{public}s', isOnRenderTree);
        }
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

## isModifiable

```TypeScript
isModifiable(): boolean
```

判断当前节点是否可修改。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断当前节点是否可修改。 |

**示例**

请参考节点操作示例。

## isOnMainTree

```TypeScript
isOnMainTree(): boolean
```

查询节点是否被挂载到主节点树上。与[isAttached](#isattached)均用于判断节点是否挂载到主节点树上，区别在于本接口在节点已调用 [dispose](#dispose)解除引用时会抛出错误码100026，开发者可根据是否需要节点dispose时的错误码校验（即抛出错误码100026）来选择使用本接口或 [isAttached](#isattached)接口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否被挂载到主节点树上。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |

**示例**

```TypeScript
import { NodeController, FrameNode, UIContext, typeNode } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

const TEST_TAG: string = 'FrameNode ';

// 继承NodeController实现自定义UI控制器
class MyNodeController extends NodeController {
  public frameNode: FrameNode | null = null;
  public childList: Array<FrameNode> = new Array<FrameNode>();
  private rootNode: FrameNode | null = null;
  private uiContext: UIContext | null = null;
  private childrenCount: number = 0;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.rootNode = new FrameNode(uiContext);
    this.uiContext = uiContext;

    this.frameNode = new FrameNode(uiContext);
    this.frameNode.commonAttribute.backgroundColor(Color.Pink);
    this.frameNode.commonAttribute.size({ width: 100, height: 100 });
    this.addCommonEvent(this.frameNode)
    this.rootNode.appendChild(this.frameNode);
    this.childrenCount = this.childrenCount + 1;
    for (let i = 0; i < 10; i++) {
      let childNode = new FrameNode(uiContext);
      this.childList.push(childNode);
      this.frameNode.appendChild(childNode);
    }
    let stackNode = typeNode.createNode(uiContext, 'Stack');
    this.frameNode.appendChild(stackNode);
    return this.rootNode;
  }

  addCommonEvent(frameNode: FrameNode) {
    frameNode.commonEvent.setOnClick((event: ClickEvent) => {
      console.info(`Click FrameNode: ${JSON.stringify(event)}`)
    })
  }

  createFrameNode() {
    let frameNode = new FrameNode(this.uiContext!);
    frameNode.commonAttribute.backgroundColor(Color.Pink);
    frameNode.commonAttribute.size({ width: 100, height: 100 });
    frameNode.commonAttribute.position({ x: this.childrenCount * 120, y: 0 });

    return frameNode;
  }

  appendChild() {
    const childNode = this.createFrameNode();
    this.rootNode!.appendChild(childNode);
    this.childrenCount = this.childrenCount + 1;
  }

  insertChildAfter(index: number) {
    let insertNode = this.createFrameNode();
    let childNode = this.rootNode!.getChild(index);
    this.rootNode!.insertChildAfter(insertNode, childNode);
    this.childrenCount = this.childrenCount + 1;
  }

  removeChild(index: number) {
    let childNode = this.rootNode!.getChild(index);
    if (childNode == null) {
      console.info(`${TEST_TAG} getchild at index {${index}} : fail`);
      return;
    }
    this.rootNode!.removeChild(childNode);
    this.childrenCount = this.childrenCount - 1;
  }

  getChildNumber() {
    console.info(`${TEST_TAG} getChildNumber ${this.rootNode!.getChildrenCount()}`)
    console.info(`${TEST_TAG} children count is ${this.childrenCount}`);
  }

  clearChildren() {
    this.rootNode!.clearChildren();
  }

  searchFrameNode() {
    if (this.rootNode!.getFirstChild() === null) {
      console.info(`${TEST_TAG} the rootNode does not have child node.`)
    }
    if (this.rootNode!.getFirstChild() === this.frameNode) {
      console.info(`${TEST_TAG} getFirstChild result: success. The first child of the rootNode is equals to frameNode.`);
    } else {
      console.info(`${TEST_TAG} getFirstChild result: fail. The first child of the rootNode is not equals to frameNode.`);
    }
    if (this.frameNode!.getChild(5) === this.frameNode!.getChild(4)!.getNextSibling()) {
      console.info(`${TEST_TAG} getNextSibling result: success.`);
    } else {
      console.info(`${TEST_TAG} getNextSibling result: fail.`);
    }
    if (this.frameNode!.getChild(3) === this.frameNode!.getChild(4)!.getPreviousSibling()) {
      console.info(`${TEST_TAG} getPreviousSibling result: success.`);
    } else {
      console.info(`${TEST_TAG} getPreviousSibling result: fail.`);
    }
    if (this.rootNode!.getFirstChild() !== null && this.rootNode!.getFirstChild()!.getParent() === this.rootNode) {
      console.info(`${TEST_TAG} getParent result: success.`);
    } else {
      console.info(`${TEST_TAG} getParent result: fail.`);
    }
    if (this.rootNode!.getParent() !== null) {
      console.info(`${TEST_TAG} get ArkTsNode success.`)
      console.info(`${TEST_TAG} check rootNode whether is modifiable ${this.rootNode!.isModifiable()}`)
      console.info(`${TEST_TAG} check getParent whether is modifiable ${this.rootNode!.getParent()!.isModifiable()}`)
    } else {
      console.info(`${TEST_TAG} get ArkTsNode fail.`);
    }
  }

  moveFrameNode() {
    const currentNode = this.frameNode!.getChild(10);
    try {
      currentNode!.moveTo(this.rootNode, 0);
      if (this.rootNode!.getChild(0) === currentNode) {
        console.info(`${TEST_TAG} moveTo result: success.`);
      } else {
        console.info(`${TEST_TAG} moveTo result: fail.`);
      }
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
      console.error(`${TEST_TAG} moveTo result: fail.`);
    }
  }

  getPositionToWindow() {
    let positionToWindow = this.rootNode?.getPositionToWindow();
    console.info(`${TEST_TAG}${JSON.stringify(positionToWindow)}`);
  }

  getPositionToParent() {
    let positionToParent = this.rootNode?.getPositionToParent();
    console.info(`${TEST_TAG}${JSON.stringify(positionToParent)}`);
  }

  getPositionToScreen() {
    let positionToScreen = this.rootNode?.getPositionToScreen();
    console.info(`${TEST_TAG}${JSON.stringify(positionToScreen)}`);
  }

  getGlobalPositionOnDisplay() {
    let positionOnGlobalDisplay = this.rootNode?.getGlobalPositionOnDisplay();
    console.info(`${TEST_TAG}${JSON.stringify(positionOnGlobalDisplay)}`);
  }

  getPositionToWindowWithTransform() {
    let positionToWindowWithTransform = this.rootNode?.getPositionToWindowWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToWindowWithTransform)}`);
  }

  getPositionToParentWithTransform() {
    let positionToParentWithTransform = this.rootNode?.getPositionToParentWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToParentWithTransform)}`);
  }

  getPositionToScreenWithTransform() {
    let positionToScreenWithTransform = this.rootNode?.getPositionToScreenWithTransform();
    console.info(`${TEST_TAG}${JSON.stringify(positionToScreenWithTransform)}`);
  }

  getMeasuredSize() {
    let measuredSize = this.frameNode?.getMeasuredSize();
    console.info(`${TEST_TAG}${JSON.stringify(measuredSize)}`);
  }

  getLayoutPosition() {
    let layoutPosition = this.frameNode?.getLayoutPosition();
    console.info(`${TEST_TAG}${JSON.stringify(layoutPosition)}`);
  }

  getUserConfigBorderWidth() {
    let userConfigBorderWidth = this.frameNode?.getUserConfigBorderWidth();
    console.info(`${TEST_TAG}${JSON.stringify(userConfigBorderWidth)}`);
  }

  getUserConfigPadding() {
    let userConfigPadding = this.frameNode?.getUserConfigPadding();
    console.info(`${TEST_TAG}${JSON.stringify(userConfigPadding)}`);
  }

  getUserConfigMargin() {
    let userConfigMargin = this.frameNode?.getUserConfigMargin();
    console.info(`${TEST_TAG}${JSON.stringify(userConfigMargin)}`);
  }

  getUserConfigSize() {
    let userConfigSize = this.frameNode?.getUserConfigSize();
    console.info(`${TEST_TAG}${JSON.stringify(userConfigSize)}`);
  }

  getId() {
    let id = this.frameNode?.getId();
    console.info(`${TEST_TAG}${id}`);
  }

  getUniqueId() {
    let uniqueId = this.frameNode?.getUniqueId();
    console.info(`${TEST_TAG}${uniqueId}`);
  }

  getNodeType() {
    let nodeType = this.frameNode?.getNodeType();
    console.info(`${TEST_TAG}${nodeType}`);
  }

  getOpacity() {
    let opacity = this.frameNode?.getOpacity();
    console.info(`${TEST_TAG}${JSON.stringify(opacity)}`);
  }

  isVisible() {
    let visible = this.frameNode?.isVisible();
    console.info(`${TEST_TAG}${JSON.stringify(visible)}`);
  }

  isClipToFrame() {
    let clipToFrame = this.frameNode?.isClipToFrame();
    console.info(`${TEST_TAG}${JSON.stringify(clipToFrame)}`);
  }

  isAttached() {
    let attached = this.frameNode?.isAttached();
    console.info(`${TEST_TAG}${JSON.stringify(attached)}`);
  }

  isOnMainTree() {
    let attached = this.frameNode?.isOnMainTree();
    console.info(`${TEST_TAG}${JSON.stringify(attached)}`);
  }

  getInspectorInfo() {
    let inspectorInfo = this.frameNode?.getInspectorInfo();
    console.info(`${TEST_TAG}${JSON.stringify(inspectorInfo)}`);
  }

  setCrossLanguageOptions() {
    console.info(`${TEST_TAG} getCrossLanguageOptions ${JSON.stringify(this.frameNode?.getCrossLanguageOptions())}`);
    try {
      this.frameNode?.setCrossLanguageOptions({
        attributeSetting: true
      });
      console.info(`${TEST_TAG} setCrossLanguageOptions success.`);
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
      console.error(`${TEST_TAG} setCrossLanguageOptions fail.`);
    }
    console.info(`${TEST_TAG} getCrossLanguageOptions ${JSON.stringify(this.frameNode?.getCrossLanguageOptions())}`);
  }

  getInteractionEventBindingInfo() {
    let bindingInfo = this.frameNode?.getInteractionEventBindingInfo(EventQueryType.ON_CLICK);
    console.info(`${TEST_TAG}${bindingInfo?.baseEventRegistered}`);
    console.info(`${TEST_TAG}${bindingInfo?.nodeEventRegistered}`);
    console.info(`${TEST_TAG}${bindingInfo?.nativeEventRegistered}`);
    console.info(`${TEST_TAG}${bindingInfo?.builtInEventRegistered}`);
    console.info(`${TEST_TAG}${JSON.stringify(bindingInfo)}`);
  }

  throwError() {
    try {
      this.rootNode!.getParent()!.clearChildren();
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
    }
    try {
      this.rootNode!.getParent()!.appendChild(new FrameNode(this.uiContext));
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
    }
    try {
      this.rootNode!.getParent()!.removeChild(this.rootNode!.getParent()!.getChild(0));
    } catch (err) {
      console.error(`${TEST_TAG} ${(err as BusinessError).code} : ${(err as BusinessError).message}`);
    }
  }
}

@Entry
@Component
struct Index {
  private myNodeController: MyNodeController = new MyNodeController();
  private scroller: Scroller = new Scroller();
  @State index: number = 0;

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Column() {
          Row() {
            Button('ADD')
              .onClick(() => {
                this.index++;
              })
            Button('DEC')
              .onClick(() => {
                this.index--;
              })
          }

          Text('Current index is ' + this.index)
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
        }

        Column() {
          Text('This is a NodeContainer.')
            .textAlign(TextAlign.Center)
            .borderRadius(10)
            .backgroundColor(0xFFFFFF)
            .width('100%')
            .fontSize(16)
          NodeContainer(this.myNodeController)
            .borderWidth(1)
            .width(300)
            .height(100)
        }

        Button('appendChild')
          .width(300)
          .onClick(() => {
            this.myNodeController.appendChild();
          })
        Button('insertChildAfter')
          .width(300)
          .onClick(() => {
            this.myNodeController.insertChildAfter(this.index);
          })
        Button('removeChild')
          .width(300)
          .onClick(() => {
            this.myNodeController.removeChild(this.index);
          })
        Button('clearChildren')
          .width(300)
          .onClick(() => {
            this.myNodeController.clearChildren();
          })
        Button('getChildNumber')
          .width(300)
          .onClick(() => {
            this.myNodeController.getChildNumber();
          })
        Button('searchFrameNode')
          .width(300)
          .onClick(() => {
            this.myNodeController.searchFrameNode();
          })
        Button('moveFrameNode')
          .width(300)
          .onClick(() => {
            this.myNodeController.moveFrameNode();
          })
        Button('getPositionToWindow')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToWindow();
          })
        Button('getPositionToParent')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToParent();
          })
        Button('getPositionToScreen')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToScreen();
          })
        Button('getGlobalPositionOnDisplay')
          .width(300)
          .onClick(() => {
            this.myNodeController.getGlobalPositionOnDisplay();
          })
        Button('getPositionToParentWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToParentWithTransform();
          })
        Button('getPositionToWindowWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToWindowWithTransform();
          })
        Button('getPositionToScreenWithTransform')
          .width(300)
          .onClick(() => {
            this.myNodeController.getPositionToScreenWithTransform();
          })
        Button('getMeasuredSize')
          .width(300)
          .onClick(() => {
            this.myNodeController.getMeasuredSize();
          })
        Button('getLayoutPosition')
          .width(300)
          .onClick(() => {
            this.myNodeController.getLayoutPosition();
          })
        Button('getUserConfigBorderWidth')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUserConfigBorderWidth();
          })
        Button('getUserConfigPadding')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUserConfigPadding();
          })
        Button('getUserConfigMargin')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUserConfigMargin();
          })
        Button('getUserConfigSize')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUserConfigSize();
          })
        Button('getId')
          .width(300)
          .onClick(() => {
            this.myNodeController.getId();
          })
        Button('getUniqueId')
          .width(300)
          .onClick(() => {
            this.myNodeController.getUniqueId();
          })
        Button('getNodeType')
          .width(300)
          .onClick(() => {
            this.myNodeController.getNodeType();
          })
        Button('getOpacity')
          .width(300)
          .onClick(() => {
            this.myNodeController.getOpacity();
          })
        Button('isVisible')
          .width(300)
          .onClick(() => {
            this.myNodeController.isVisible();
          })
        Button('isClipToFrame')
          .width(300)
          .onClick(() => {
            this.myNodeController.isClipToFrame();
          })
        Button('isAttached')
          .width(300)
          .onClick(() => {
            this.myNodeController.isAttached();
          })
        Button('isOnMainTree')
          .width(300)
          .onClick(() => {
            this.myNodeController.isOnMainTree();
          })
        Button('getInspectorInfo')
          .width(300)
          .onClick(() => {
            this.myNodeController.getInspectorInfo();
          })
        Button('getCustomProperty')
          .width(300)
          .onClick(() => {
            const uiContext: UIContext = this.getUIContext();
            if (uiContext) {
              const node: FrameNode | null = uiContext.getFrameNodeById('Test_Button') || null;
              if (node) {
                for (let i = 1; i < 4; i++) {
                  const key = 'customProperty' + i;
                  const property = node.getCustomProperty(key);
                  console.info(`${TEST_TAG}${key}`, JSON.stringify(property));
                }
              }
            }
          })
          .id('Test_Button')
          .customProperty('customProperty1', {
            'number': 10,
            'string': 'this is a string',
            'bool': true,
            'object': {
              'name': 'name',
              'value': 100
            }
          })
          .customProperty('customProperty2', {})
          .customProperty('customProperty2', undefined)
        Button('setCrossLanguageOptions')
          .width(300)
          .onClick(() => {
            this.myNodeController.setCrossLanguageOptions();
          })
        Button('getInteractionEventBindingInfo')
          .width(300)
          .onClick(() => {
            this.myNodeController.getInteractionEventBindingInfo();
          })
        Button('throwError')
          .width(300)
          .onClick(() => {
            this.myNodeController.throwError();
          })
      }
      .width('100%')
    }
    .scrollable(ScrollDirection.Vertical) // 滚动方向为纵向
  }
}
```

## isTransferred

```TypeScript
isTransferred(): boolean
```

判断FrameNode是否通过transfer.transferStatic或者transfer.transferDynamic方法创建。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回FrameNode是否通过transfer.transferStatic或transfer.transferDynamic方法创建。 |

## isVisible

```TypeScript
isVisible(): boolean
```

获取节点是否可见。

> **说明：**
> 
> 根据组件设置的visibility属性值判断该节点是否可见。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否可见。 |

**示例**

请参考节点操作示例。

## layout

```TypeScript
layout(position: Position): void
```

调用FrameNode的布局方法，为FrameNode及其子节点指定布局位置，如果布局方法被重写，则调用重写的方法。建议在[onLayout](#onlayout)方法中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-t.md) | 是 | 组件进行布局时使用的位置信息。单位为PX。 |

**示例**

请参考节点自定义示例。

## measure

```TypeScript
measure(constraint: LayoutConstraint): void
```

调用FrameNode的测量方法，根据父容器的布局约束，对FrameNode进行测量，计算出尺寸，如果测量方法被重写，则调用重写的方法。建议在[onMeasure](#onmeasure)方法中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | 是 | 组件进行测量时使用的父容器布局约束。 |

**示例**

请参考节点自定义示例。

## moveTo

```TypeScript
moveTo(targetParent: FrameNode, index?: number): void
```

将当前FrameNode移动到目标FrameNode的指定位置。当前FrameNode如果不可修改，抛出异常信息。targetParent为[typeNode](arkts-arkui-typenode-n.md)时会校验子组件类型或个数，不满足时抛出 异常信息，限制情况请查看[typeNode](arkts-arkui-typenode-n.md)描述。

> **说明：**
> 
> 当前仅支持以下类型的[TypedFrameNode](arkts-arkui-framenode-typedframenode-i.md)进行移动操作：[Stack](arkts-arkui-typenode-stack-t.md)、
> [XComponent](arkts-arkui-typenode-xcomponent-t.md)。对于其他类型的节点，移动操作不会生效。
> 
> 当前仅支持根节点为以下类型组件的[BuilderNode](arkts-arkui-buildernode-c.md)进行移动操作：
> Stack、XComponent、
> EmbeddedComponent。对于其他类型的组件，移动操作不会生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetParent | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 目标父节点。targetParent节点不可以为声明式创建的节点，即不可修改的FrameNode。若目标父节点不符合规格，则抛出异常信息。 |
| index | number | 否 | 子节点序列号。当前FrameNode将被添加到目标FrameNode对应序列号的子节点之前，若目标FrameNode有n个节点，index取值范围为[0, n-1]。 & lt;br/ & gt;若参数无效或不指定，则添加到目标FrameNode的最后。默认值：-1 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100027](../errorcode-node.md#100027-当前节点已被接纳为附属节点) | The current node has been adopted.<br>**适用版本：** 22+ |

**示例**

请参考节点操作示例。

## onDraw

```TypeScript
onDraw?(context: DrawContext): void
```

FrameNode的自绘制方法，该方法会重写默认绘制方法，在FrameNode进行内容绘制时被调用。该接口的[DrawContext](arkts-arkui-graphics-drawcontext-c.md)中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见 [调整自定义绘制Canvas的变换矩阵](../../../ui/arkts-user-defined-arktsNode-frameNode.md#调整自定义绘制canvas的变换矩阵)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [DrawContext](arkts-arkui-graphics-drawcontext-c.md) | 是 | 图形绘制上下文。自绘制区域无法超出组件自身大小。 |

**示例**

请参考节点自定义示例。

## onLayout

```TypeScript
onLayout(position: Position): void
```

FrameNode的自定义布局方法，该方法会重写默认布局方法，在FrameNode进行布局时被调用，为FrameNode及其子节点指定位置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-t.md) | 是 | 组件进行布局时使用的位置信息。单位为PX。 |

**示例**

请参考节点自定义示例。

## onMeasure

```TypeScript
onMeasure(constraint: LayoutConstraint): void
```

FrameNode的自定义测量方法，该方法会重写默认测量方法，在FrameNode进行测量时被调用，测量FrameNode及其内容的大小。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | 是 | 组件进行测量时使用的布局约束。 |

**示例**

请参考节点自定义示例。

## recycle

```TypeScript
recycle(): void
```

全局复用场景下，触发子组件回收，彻底释放FrameNode后端资源，以便于通过[reuse](#reuse)方法实现资源的重新复用，确保后端资源能够被有效回收并再次使用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考节点复用回收使用示例。

## removeAdoptedChild

```TypeScript
removeAdoptedChild(child: FrameNode): void
```

移除被接纳的目标附属节点。当前FrameNode如果不可修改，抛出异常信息。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 已被接纳的目标附属节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The current FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be null." |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |

**示例**

完整示例请参考接纳为附属节点示例。

## removeChild

```TypeScript
removeChild(node: FrameNode): void
```

从FrameNode中删除指定的子节点。当前FrameNode如果不可修改，抛出异常信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 需要删除的子节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |

**示例**

请参考节点操作示例。

## removeSupportedUIStates

```TypeScript
removeSupportedUIStates(uiStates: number): void
```

删除组件当前注册的状态处理。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiStates | number | 是 | 需要删除的UI状态。 可以通过位或计算同时指定删除多个状态，如：removeUIStates = UIState.PRESSED  \|  UIState.FOCUSED。 |

**示例**

请参考组件设置和删除多态样式状态示例。

## reuse

```TypeScript
reuse(): void
```

全局复用场景下，触发子组件复用，实现FrameNode后端资源的复用，提升资源利用效率。为保证资源充足，可以在recycle之后使用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考节点复用回收使用示例。

## setCrossLanguageOptions

```TypeScript
setCrossLanguageOptions(options: CrossLanguageOptions): void
```

设置当前FrameNode的跨ArkTS语言访问选项。例如ArkTS语言创建的节点，设置该节点是否可通过非ArkTS语言进行属性设置，从API版本26.0.0开始支持设置是否可通过非ArkTS语言进行组件树操作。当前 FrameNode如果不可修改或不可设置跨ArkTS语言访问选项，抛出异常信息。

> **说明：**
> 
> 当前仅支持[Scroll](arkts-arkui-typenode-scroll-t.md)、[Swiper](arkts-arkui-typenode-swiper-t.md)、[List](arkts-arkui-typenode-list-t.md)、
> [ListItem](arkts-arkui-typenode-listitem-t.md)、[ListItemGroup](arkts-arkui-typenode-listitemgroup-t.md)、
> [WaterFlow](arkts-arkui-typenode-waterflow-t.md)、[FlowItem](arkts-arkui-typenode-flowitem-t.md)、[Grid](arkts-arkui-typenode-grid-t.md)、
> [GridItem](arkts-arkui-typenode-griditem-t.md)、[TextInput](arkts-arkui-typenode-textinput-t.md)、[TextArea](arkts-arkui-typenode-textarea-t.md)、
> [Column](arkts-arkui-typenode-column-t.md)、[Row](arkts-arkui-typenode-row-t.md)、[Stack](arkts-arkui-typenode-stack-t.md)、
> [Flex](arkts-arkui-typenode-flex-t.md)、[RelativeContainer](arkts-arkui-typenode-relativecontainer-t.md)、
> [Progress](arkts-arkui-typenode-progress-t.md)、[LoadingProgress](arkts-arkui-typenode-loadingprogress-t.md)、
> [Image](arkts-arkui-typenode-image-t.md)、[Button](arkts-arkui-typenode-button-t.md)、[Checkbox](arkts-arkui-typenode-checkbox-t.md)、
> [Radio](arkts-arkui-typenode-radio-t.md)、[Slider](arkts-arkui-typenode-slider-t.md)、[Toggle](arkts-arkui-typenode-toggle-t.md)、
> [XComponent](arkts-arkui-typenode-xcomponent-t.md)类型的[TypedFrameNode](arkts-arkui-framenode-typedframenode-i.md)设置跨ArkTS语言访问选项。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CrossLanguageOptions](arkts-arkui-framenode-crosslanguageoptions-i.md) | 是 | 跨ArkTS语言访问选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100022](../errorcode-node.md#100022-framenode节点的组件类型不支持调整跨语言的通用属性设置权限) | The FrameNode cannot be set whether to support cross-language common attribute setting. |

**示例**

请参考节点操作示例。

## setLayoutPosition

```TypeScript
setLayoutPosition(position: Position): void
```

设置FrameNode的布局后的位置，默认单位PX。建议在[onLayout](#onlayout)方法中调用，用于设置自定义布局的结果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-t.md) | 是 | FrameNode的布局后的位置，单位为PX。 |

**示例**

请参考节点自定义示例。

## setMeasuredSize

```TypeScript
setMeasuredSize(size: Size): void
```

设置FrameNode的测量后的尺寸，默认单位PX。若设置的宽高为负数，自动取零。建议在[onMeasure](#onmeasure)方法中调用，用于设置自定义测量的结果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | Size | 是 | FrameNode的测量后的尺寸，单位为PX。 |

**示例**

请参考节点自定义示例。

## setNeedsLayout

```TypeScript
setNeedsLayout(): void
```

该方法会将FrameNode标记为需要布局的状态，下一帧将会进行重新布局，触发[onMeasure](#onmeasure)和[onLayout](#onlayout)方 法的调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考节点自定义示例。

## commonAttribute

```TypeScript
get commonAttribute(): CommonAttribute
```

获取FrameNode中持有的CommonAttribute接口，用于设置通用属性和 通用事件。仅可以修改自定义节点的属性。

> **说明：**
> 
> FrameNode的效果参考对齐方式为顶部起始端的Stack容器组件。
> 
> FrameNode的属性支持情况参考
> [属性或事件对attributemodifier的支持情况](../../../ui/arkts-user-defined-extension-attributeModifier.md#属性或事件对attributemodifier的支持情况)。

**类型：** [CommonAttribute](../arkts-components/arkts-arkui-common-attribute.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考基础事件示例。

## commonEvent

```TypeScript
get commonEvent(): UICommonEvent
```

获取FrameNode中持有的UICommonEvent对象，用于设置基础事件。设置的基础事件与声明式定义的事件平行，参与事件竞争；设置的基础事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。LazyForEach场景下，由于存在节点的销毁重建，对于重建的节点需要重新设置事件回调才能保证监听事件正常响应。

**类型：** [UICommonEvent](../arkts-components/arkts-arkui-uicommonevent-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考基础事件示例和LazyForEach场景基础事件使用示例。

## gestureEvent

```TypeScript
get gestureEvent(): UIGestureEvent
```

获取FrameNode中持有的UIGestureEvent对象，用于设置组件绑定的手势事件。通过gestureEvent接口设置的手势不会覆盖通过 绑定手势事件绑定的手势，两者同时设置了手势时，优先回调绑定手势事件设置的手势事件。LazyForEach场景下，由于存在节点的销毁重建，对于重建的节点需要重新设置手势事件回调才能保证监听事件正常响应。

**类型：** [UIGestureEvent](../arkts-components/arkts-arkui-uigestureevent-i.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

请参考手势事件示例。
