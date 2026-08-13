# FrameNode

定义FrameNode。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class FrameNode--><!--Device-unnamed-export declare class FrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addComponentContent

```TypeScript
addComponentContent<T>(content: ComponentContent<T> | ReactiveComponentContent): void
```

支持添加ComponentContent类型的组件内容。要求当前节点是一个可修改的节点，即[isModifiable](#isModifiable)的返回值为true，否则抛出异常信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-addComponentContent<T>(content: ComponentContent<T> | ReactiveComponentContent): void--><!--Device-FrameNode-addComponentContent<T>(content: ComponentContent<T> | ReactiveComponentContent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](arkts-na-componentcontent-c.md)&lt;T&gt; \| [ReactiveComponentContent](arkts-na-componentcontent-reactivecomponentcontent-c.md) | 是 | FrameNode节点中显示的组件内容。<br>**起始版本：** 23 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../../apis-arkui/errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |

## addSupportedUIStates

```TypeScript
addSupportedUIStates(uiStates: int, statesChangeHandler: UIStatesChangeHandler, excludeInner?: boolean): void
```

设置组件支持的多态样式状态。为了提高效率，需要通过状态 以及它们对应的处理程序函数。当状态发生变化时，处理程序函数将 可以在回调中根据当前状态更新UI样式。 对于某些类型的控制节点，系统对某些状态（例如，按钮）有默认的样式处理 组件有默认的样式更改状态（PRESSED状态）。使用此方法自定义状态处理时 对于这样的组件，系统的默认样式更改将首先应用，然后是自定义样式。 最终的效果是两者的结合。你可以将`excludeInner`设置为`true`来禁用系统默认的 样式处理，尽管这取决于系统实现。 调用此方法时，提供的`handler`函数将立即执行。你不需要 显式为NORMAL状态注册一个处理程序。如果为非NORMAL状态注册处理程序，则系统 将在状态恢复为NORMAL时自动调用处理程序，允许您恢复UI风格。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-addSupportedUIStates(uiStates: int, statesChangeHandler: UIStatesChangeHandler, excludeInner?: boolean): void--><!--Device-FrameNode-addSupportedUIStates(uiStates: int, statesChangeHandler: UIStatesChangeHandler, excludeInner?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiStates | int | 是 | 目标UI声明节点需要处理。可以组合多个状态 使用OR操作，例如`targetUIStates = UIState.PRESSED \| UIState.FOCUSED`。 &lt;br&gt;取值限定为整数。 - 需要处理目标节点的UI状态。&lt;br&gt;可以通过位或计算同时指定设置多个状态，如：targetUIStates = UIState.PRESSED  \| UIState.FOCUSED。 |
| statesChangeHandler | [UIStatesChangeHandler](arkts-na-uistateschangehandler-t.md) | 是 | 状态变化时的回调函数。 |
| excludeInner | boolean | 否 | =false] - A flag to disable the system's default style handling for states. |

## adoptChild

```TypeScript
adoptChild(child: FrameNode): void
```

当前节点接纳目标节点为附属节点。被接纳的附属节点不能已有父节点。调用该接口实际上不会将其添加为子节点，而是仅允许其接收对应子节点的生命周期回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-adoptChild(child: FrameNode): void--><!--Device-FrameNode-adoptChild(child: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-na-framenode-c.md) | 是 | 指定待被接纳的节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../../apis-arkui/errorcode-node.md#100021-framenode节点不可修改) | The current FrameNode is not modifiable. |
| [100025](../../apis-arkui/errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be disposed." |
| [100026](../../apis-arkui/errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |

## appendChild

```TypeScript
appendChild(node: FrameNode): void
```

在FrameNode最后一个子节点后添加新的子节点。当前FrameNode如果不可修改，抛出异常信息。 typeNode在appendChild时会校验子组件类型或个数，不满足时抛出异常信息，限制情况请查看 typeNode描述。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-appendChild(node: FrameNode): void--><!--Device-FrameNode-appendChild(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-na-framenode-c.md) | 是 | 需要添加的FrameNode。&lt;br/&gt; node节点不可以为声明式创建的节点，即不可修改的FrameNode。仅有从BuilderNode中获取的声明式节点可以作为子节点。 若子节点不符合规格，则抛出异常信息。&lt;br/&gt; node节点不可以拥有父节点，否则抛出异常信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../../apis-arkui/errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100025](../../apis-arkui/errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: it cannot be adopted." |

## cancelAnimations

```TypeScript
cancelAnimations(properties: AnimationPropertyType[]): boolean
```

请求取消FrameNode上指定属性上的所有动画，该方法需在节点所处线程中调用，会阻塞当前线程以等待取消结果。如果动画成功取消，节点上的属性值会被恢复为取消时的显示值（即当前状态）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-cancelAnimations(properties: AnimationPropertyType[]): boolean--><!--Device-FrameNode-cancelAnimations(properties: AnimationPropertyType[]): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| properties | [AnimationPropertyType](arkts-na-enums-animationpropertytype-e.md)[] | 是 | 待取消的动画属性枚举数组。可以一次取消一个节点上的多个属性的动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示动画是否取消成功。&lt;br/&gt;返回值为true：动画取消成功。&lt;br/&gt;返回值为false：动画取消失败。&lt;br/&gt;可能导致动画取消失败的原因：&lt;br/&gt; 1. 节点已经释放，调用过 [dispose]{ |

## clearChildren

```TypeScript
clearChildren(): void
```

清除当前FrameNode的所有子节点。当前FrameNode如果不可修改，抛出异常信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-clearChildren(): void--><!--Device-FrameNode-clearChildren(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../../apis-arkui/errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |

## constructor

```TypeScript
constructor(uiContext: UIContext, options?: FrameNodeOptions)
```

FrameNode的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-constructor(uiContext: UIContext, options?: FrameNodeOptions)--><!--Device-FrameNode-constructor(uiContext: UIContext, options?: FrameNodeOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 创建对应节点时所需的UI上下文。<br>**起始版本：** 23 |
| options | [FrameNodeOptions](arkts-na-framenode-framenodeoptions-i.md) | 否 | FrameNode创建时的可选参数。默认值：undefined，表示不支持多线程操作。<br>**起始版本：** 24 |

## convertPosition

```TypeScript
convertPosition(position: NodePosition, targetNode: FrameNode): NodePosition
```

从当前节点的坐标系转换点的坐标 到目标节点的坐标系。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-convertPosition(position: NodePosition, targetNode: FrameNode): NodePosition--><!--Device-FrameNode-convertPosition(position: NodePosition, targetNode: FrameNode): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [NodePosition](arkts-na-nodeposition-t.md) | 是 | 当前节点坐标系中的相对坐标。 |
| targetNode | [FrameNode](arkts-na-framenode-c.md) | 是 | 本次坐标转换的目标节点，转换得到的点坐标就是该节点坐标系中的相对坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 目标节点局部坐标系中的转换坐标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100025](../../apis-arkui/errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'targetNode' is invalid: it cannot be disposed." |
| [100024](../../apis-arkui/errorcode-node.md#100024-节点没有公共祖先节点) | The current FrameNode and the target FrameNode do not have a common ancestor node. |

## convertPositionFromWindow

```TypeScript
convertPositionFromWindow(positionByWindow: NodePosition): NodePosition
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-convertPositionFromWindow(positionByWindow: NodePosition): NodePosition--><!--Device-FrameNode-convertPositionFromWindow(positionByWindow: NodePosition): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionByWindow | [NodePosition](arkts-na-nodeposition-t.md) | 是 | 当前节点所在窗口的坐标系中的相对坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 当前节点坐标系中的转换坐标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100026](../../apis-arkui/errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |
| [100028](../../apis-arkui/errorcode-node.md#100028-当前节点不在主节点树上) | The current FrameNode is not on the main tree. |

## convertPositionToWindow

```TypeScript
convertPositionToWindow(positionByLocal: NodePosition): NodePosition
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-convertPositionToWindow(positionByLocal: NodePosition): NodePosition--><!--Device-FrameNode-convertPositionToWindow(positionByLocal: NodePosition): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionByLocal | [NodePosition](arkts-na-nodeposition-t.md) | 是 | 当前节点坐标系中的相对坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 当前节点所在窗口的坐标系中的转换坐标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100026](../../apis-arkui/errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |
| [100028](../../apis-arkui/errorcode-node.md#100028-当前节点不在主节点树上) | The current FrameNode is not on the main tree. |

## createAnimation

```TypeScript
createAnimation(property: AnimationPropertyType, startValue: double[] | undefined, endValue: double[], param: AnimateParam): boolean
```

在FrameNode中创建属性动画。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-createAnimation(property: AnimationPropertyType, startValue: double[] | undefined, endValue: double[], param: AnimateParam): boolean--><!--Device-FrameNode-createAnimation(property: AnimationPropertyType, startValue: double[] | undefined, endValue: double[], param: AnimateParam): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [AnimationPropertyType](arkts-na-enums-animationpropertytype-e.md) | 是 | 动画属性枚举。 |
| startValue | double[] \| undefined | 是 | 动画属性的起始值。取值为undefined或数组，取值为数组时数组长度需要和属性枚举匹配。如果为undefined则表示不显式指定动画初值， 节点上一次设置的属性终值为此次动画的起点值。如果取值为数组，&lt;br/&gt;- 对于AnimationPropertyType.ROTATION，取值格式为[rotationX, rotationY, rotationZ]，单位 为度（°），表示绕x、y、z轴的旋转角。&lt;br/&gt;- 对于AnimationPropertyType.TRANSLATION，取值格式为[translateX, translateY]，单位为px，表示沿x、y轴的平移量。 &lt;br/&gt;- 对于AnimationPropertyType.SCALE，取值格式为[scaleX, scaleY]，表示x、y方向的缩放比例。&lt;br/&gt;- 对于AnimationPropertyType.OPACITY， 取值格式为[opacity]，表示不透明度。opacity的取值范围为[0, 1]。&lt;br/&gt;当节点上从未设置过该属性时，需要显式指定startValue才能正常创建动画。当节点上已经设置过属性（如第二次及之后创建动画）， 则推荐不显式指定startValue或者显式指定startValue为上一次的终值，表示使用上一次的终值作为新的动画起点，避免起始值跳变。 |
| endValue | double[] | 是 | 动画属性的终止值。取值为数组，数组长度需要和属性枚举匹配。&lt;br/&gt;- 对于AnimationPropertyType.ROTATION，取值格式为 [rotationX, rotationY, rotationZ]，单位为度（°），表示绕x、y、z轴的旋转角。&lt;br/&gt;- 对于AnimationPropertyType.TRANSLATION，取值格式为 [translateX, translateY]，单位为px，表示沿x、y轴的平移量。&lt;br/&gt;- 对于AnimationPropertyType.SCALE，取值格式为[scaleX, scaleY]，表示x、y方向的缩 放比例。&lt;br/&gt;- 对于AnimationPropertyType.OPACITY，取值格式为[opacity]，表示不透明度。opacity的取值范围为[0, 1]。 |
| param | AnimateParam | 是 | 动画参数。包含时长、动画曲线、结束回调等参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示动画是否创建成功。&lt;br/&gt;返回值为true：动画创建成功，如果动画参数中设置结束回调，动画结束后会调用结束回调。&lt;br/&gt;返回值为false：动画创建失败，即使动画参数中设置结束回 调，结束回调也不会被调用。&lt;br/&gt;可能导致动画创建失败的原因：&lt;br/&gt; 1. 节点已经释放，调用过[dispose]{ |

## createFrameNodes

```TypeScript
static createFrameNodes(uiContext: UIContext, count: int): FrameNode[]
```

创建指定数量的FrameNode对象并返回。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-static createFrameNodes(uiContext: UIContext, count: int): FrameNode[]--><!--Device-FrameNode-static createFrameNodes(uiContext: UIContext, count: int): FrameNode[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 创建对应节点时所需的UI上下文。 |
| count | int | 是 | 指定创建节点的数量，取值范围为大于零的整型。若给定值小于等于0或不是整数，则返回空数组。 &lt;br&gt;取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-na-framenode-c.md)[] | the array of created FrameNode objects. |

## dispose

```TypeScript
dispose(): void
```

立即解除当前FrameNode对象对实体FrameNode节点的引用关系。 > **说明：** > > - FrameNode对象调用dispose后，由于不对应任何实体FrameNode节点，在调用部分查询接口([getMeasuredSize](#getMeasuredSize)、 > [getLayoutPosition](#getLayoutPosition))的时候会导致应用出现jscrash。 > > - 通过[getUniqueId](#getUniqueId)可以判断当前FrameNode是否对应一个实体FrameNode节点。当UniqueId大于0时表示该对象对应一个实体 > FrameNode节点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-dispose(): void--><!--Device-FrameNode-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disposeTree

```TypeScript
disposeTree(): void
```

下树并递归释放当前节点为根的子树。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-disposeTree(): void--><!--Device-FrameNode-disposeTree(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getChild

```TypeScript
getChild(index: int, expandMode?: ExpandMode | undefined): FrameNode | null
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getChild(index: int, expandMode?: ExpandMode | undefined): FrameNode | null--><!--Device-FrameNode-getChild(index: int, expandMode?: ExpandMode | undefined): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 需要查询的子节点的序列号。index取值范围为[0, +∞)，若当前节点有n个子节点，index取值有效范围为[0, n-1]。 |
| expandMode | [ExpandMode](arkts-na-framenode-expandmode-e.md) \| undefined | 否 | 指定子节点展开模式。&lt;br/&gt;默认值：ExpandMode.EXPAND |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-na-framenode-c.md) | Returns a FrameNode. When the required node does not exist, returns null. |

## getChildrenCount

```TypeScript
getChildrenCount(): int
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getChildrenCount(): int--><!--Device-FrameNode-getChildrenCount(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 获取当前FrameNode的子节点数量。 |

## getChildrenCount

```TypeScript
getChildrenCount(countMode?: ChildrenCountMode): int
```

根据指定的计数模式获取当前FrameNode的子节点数量。 .0.0 .0.0

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getChildrenCount(countMode?: ChildrenCountMode): int--><!--Device-FrameNode-getChildrenCount(countMode?: ChildrenCountMode): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| countMode | [ChildrenCountMode](arkts-na-framenode-childrencountmode-e.md) | 否 | The children count mode. Default value is ChildrenCountMode.ALL_EXPAND. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Returns the number of children of the current FrameNode based on the count mode. |

## getCrossLanguageOptions

```TypeScript
getCrossLanguageOptions(): CrossLanguageOptions
```

获取当前FrameNode的跨ArkTS语言访问选项。例如ArkTS语言创建的节点，返回该节点是否可通过非ArkTS语言进行属性设置，从API版本26.0.0开始支持获取是否可通过非ArkTS语言进行组件树操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getCrossLanguageOptions(): CrossLanguageOptions--><!--Device-FrameNode-getCrossLanguageOptions(): CrossLanguageOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CrossLanguageOptions](arkts-na-framenode-crosslanguageoptions-i.md) | 跨ArkTS语言访问选项。 |

## getCustomProperty

```TypeScript
getCustomProperty(name: string): CustomProperty
```

通过名称获取组件的自定义属性。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getCustomProperty(name: string): CustomProperty--><!--Device-FrameNode-getCustomProperty(name: string): CustomProperty-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 自定义属性的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CustomProperty | 自定义属性的值。 |

## getFirstChild

```TypeScript
getFirstChild(): FrameNode | null
```

获取当前FrameNode的第一个子节点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getFirstChild(): FrameNode | null--><!--Device-FrameNode-getFirstChild(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-na-framenode-c.md) | Returns a FrameNode, which is first child of the current FrameNode. If current FrameNode does not have child node, returns null. If current FrameNode does not have child node, returns null. |

## getFirstChildIndexWithoutExpand

```TypeScript
getFirstChildIndexWithoutExpand(): int
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getFirstChildIndexWithoutExpand(): int--><!--Device-FrameNode-getFirstChildIndexWithoutExpand(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 当前节点第一个在主节点树上的子节点的序列号。 |

## getFrameNodeById

```TypeScript
getFrameNodeById(id: string): FrameNode | null
```

以当前节点为根节点，逐层查找所有子节点，返回第一个匹配指定id的节点。查找顺序为：先查找直接子节点，再查找二级子节点，依此类推，找到后立即返回。 .0.0 .0.0

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getFrameNodeById(id: string): FrameNode | null--><!--Device-FrameNode-getFrameNodeById(id: string): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 查询的子节点id，为通用属性设置的组件标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-na-framenode-c.md) | The first child node with the specified ID, or null if not found. |

## getFrameNodeByUniqueId

```TypeScript
getFrameNodeByUniqueId(id: int): FrameNode | null
```

以当前节点为根节点，查找并返回指定UniqueID（系统分配的节点唯一标识，该标识可通过[getUniqueId](#getUniqueId)接口获取）的子节点。 1.如果唯一标识对应的是内置组件，则返回关联的FrameNode。 2.如果该onlyId对应自定义组件：如果该组件已经渲染了内容，则其根节点为 返回，类型为__Common__；如果组件没有渲染的内容，则返回其第一个子项的FrameNode 组件返回。 3.如果不对应任何组件，则返回null。 .0.0

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getFrameNodeByUniqueId(id: int): FrameNode | null--><!--Device-FrameNode-getFrameNodeByUniqueId(id: int): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | int | 是 | 查询的子节点的唯一标识UniqueID。 &lt;br&gt;取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-na-framenode-c.md) | The FrameNode with the target uniqueId, or null if the frameNode is not existed. |

## getGlobalPositionOnDisplay

```TypeScript
getGlobalPositionOnDisplay(): NodePosition
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getGlobalPositionOnDisplay(): NodePosition--><!--Device-FrameNode-getGlobalPositionOnDisplay(): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 节点相对于全局屏幕的位置偏移，单位为VP。 |

## getId

```TypeScript
getId(): string
```

获取用户设置的节点ID（通用属性设置的组件标识）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getId(): string--><!--Device-FrameNode-getId(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 用户设置的节点ID（通用属性设置的[组件标识]{ |

## getInspectorInfo

```TypeScript
getInspectorInfo(): Object
```

获取节点的结构信息，该信息和DevEco Studio内置&lt;!--RP1--&gt;ArkUI Inspector&lt;!--RP1End--&gt;工具里面的一致。 > **说明：** > > getInspectorInfo接口用于获取所有节点的信息，作为调试接口使用，频繁调用会导致性能下降。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getInspectorInfo(): Object--><!--Device-FrameNode-getInspectorInfo(): Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 节点的结构信息。 |

## getInteractionEventBindingInfo

```TypeScript
getInteractionEventBindingInfo(eventType: EventQueryType): InteractionEventBindingInfo | undefined
```

获取目标节点的事件绑定信息，如果该组件节点上没有绑定要查询的交互事件类型时，返回 undefined。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getInteractionEventBindingInfo(eventType: EventQueryType): InteractionEventBindingInfo | undefined--><!--Device-FrameNode-getInteractionEventBindingInfo(eventType: EventQueryType): InteractionEventBindingInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | [EventQueryType](arkts-na-enums-eventquerytype-e.md) | 是 | 要查询的交互事件类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InteractionEventBindingInfo](arkts-na-framenode-interactioneventbindinginfo-i.md) | Returns one InteractionEventBindingInfo object indicating the event binding details if any interaction events binded on current node, returns undefined if no one binded on. |

## getLastChildIndexWithoutExpand

```TypeScript
getLastChildIndexWithoutExpand(): int
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getLastChildIndexWithoutExpand(): int--><!--Device-FrameNode-getLastChildIndexWithoutExpand(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 当前节点最后一个在主节点树上的子节点的序列号。 |

## getLayoutPosition

```TypeScript
getLayoutPosition(): NodePosition
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getLayoutPosition(): NodePosition--><!--Device-FrameNode-getLayoutPosition(): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 节点布局后相对于父组件的位置偏移，单位为PX。 |

## getMeasuredSize

```TypeScript
getMeasuredSize(): Size
```

获取FrameNode测量后的大小，单位为PX。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getMeasuredSize(): Size--><!--Device-FrameNode-getMeasuredSize(): Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Size](arkts-na-graphics-size-i.md) | 节点测量后的大小，单位为PX。 |

## getNextSibling

```TypeScript
getNextSibling(): FrameNode | null
```

获取当前FrameNode的下一个同级节点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getNextSibling(): FrameNode | null--><!--Device-FrameNode-getNextSibling(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-na-framenode-c.md) | Returns a FrameNode. If current FrameNode does not have next sibling node, returns null. |

## getNodePropertyValue

```TypeScript
getNodePropertyValue(property: AnimationPropertyType): double[]
```

从节点获取属性值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getNodePropertyValue(property: AnimationPropertyType): double[]--><!--Device-FrameNode-getNodePropertyValue(property: AnimationPropertyType): double[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [AnimationPropertyType](arkts-na-enums-animationpropertytype-e.md) | 是 | 动画属性枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double[] | the property value on the node. |

## getNodeType

```TypeScript
getNodeType(): string
```

获取节点的类型。系统组件类型为组件名称，例如，按钮组件Button的类型为Button。而对于自定义组件，若其有渲染内容，则其类型为__Common__。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getNodeType(): string--><!--Device-FrameNode-getNodeType(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 节点的类型。 |

## getOpacity

```TypeScript
getOpacity(): double
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getOpacity(): double--><!--Device-FrameNode-getOpacity(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 节点的不透明度。范围是[0, 1]，值越大透明度越低。 |

## getParent

```TypeScript
getParent(): FrameNode | null
```

获取当前FrameNode的父节点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getParent(): FrameNode | null--><!--Device-FrameNode-getParent(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-na-framenode-c.md) | Returns a FrameNode. If current FrameNode does not have parent node, returns null. |

## getPositionToParent

```TypeScript
getPositionToParent(): NodePosition
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getPositionToParent(): NodePosition--><!--Device-FrameNode-getPositionToParent(): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 节点相对于父组件的位置偏移，单位为VP。 |

## getPositionToParentWithTransform

```TypeScript
getPositionToParentWithTransform(): NodePosition
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getPositionToParentWithTransform(): NodePosition--><!--Device-FrameNode-getPositionToParentWithTransform(): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 节点相对于父组件的位置偏移，单位为VP。 当设置了其他（比如：transform, translate等）绘制属性，由于浮点数精度的影响，返回值会有微小偏差。 |

## getPositionToScreen

```TypeScript
getPositionToScreen(): NodePosition
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getPositionToScreen(): NodePosition--><!--Device-FrameNode-getPositionToScreen(): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 节点相对于屏幕的位置偏移，单位为VP。 |

## getPositionToScreenWithTransform

```TypeScript
getPositionToScreenWithTransform(): NodePosition
```

获取FrameNode相对于屏幕带有绘制属性的位置偏移，单位为VP，绘制属性比如transform, translate等，返回的坐标是组件布局时左上角变换后的坐标。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getPositionToScreenWithTransform(): NodePosition--><!--Device-FrameNode-getPositionToScreenWithTransform(): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 节点相对于屏幕的位置偏移，单位为VP。 当设置了其他（比如：transform, translate等）绘制属性，由于浮点数精度的影响，返回值会有微小偏差。 |

## getPositionToWindow

```TypeScript
getPositionToWindow(): NodePosition
```

Get the position of the node relative to window.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getPositionToWindow(): NodePosition--><!--Device-FrameNode-getPositionToWindow(): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | Returns position of the node relative to window. |

## getPositionToWindowWithTransform

```TypeScript
getPositionToWindowWithTransform(): NodePosition
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getPositionToWindowWithTransform(): NodePosition--><!--Device-FrameNode-getPositionToWindowWithTransform(): NodePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodePosition](arkts-na-nodeposition-t.md) | 节点相对于窗口的位置偏移，单位为VP。 当设置了其他（比如：transform, translate等）绘制属性，由于浮点数精度的影响，返回值会有微小偏差。 |

## getPreviousSibling

```TypeScript
getPreviousSibling(): FrameNode | null
```

获取当前FrameNode的上一个同级节点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getPreviousSibling(): FrameNode | null--><!--Device-FrameNode-getPreviousSibling(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-na-framenode-c.md) | Returns a FrameNode. If current FrameNode does not have previous sibling node, returns null. |

## getRenderNode

```TypeScript
getRenderNode(): RenderNode | null
```

获取FrameNode中持有的[RenderNode](../../apis-arkui/arkts-apis/arkts-arkui-rendernode-c.md#RenderNode)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getRenderNode(): RenderNode | null--><!--Device-FrameNode-getRenderNode(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](../../apis-arkui/arkts-apis/arkts-arkui-rendernode-c.md) | Returns a RenderNode inside the FrameNode, or null if not contained. |

## getUniqueId

```TypeScript
getUniqueId(): int
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getUniqueId(): int--><!--Device-FrameNode-getUniqueId(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 系统分配的唯一标识的节点UniqueID。 |

## getUserConfigBorderWidth

```TypeScript
getUserConfigBorderWidth(): NodeEdges<LengthMetrics>
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getUserConfigBorderWidth(): NodeEdges<LengthMetrics>--><!--Device-FrameNode-getUserConfigBorderWidth(): NodeEdges<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodeEdges](arkts-na-graphics-nodeedges-i.md)&lt;[LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)&gt; | 用户设置的边框宽度。 |

## getUserConfigMargin

```TypeScript
getUserConfigMargin(): NodeEdges<LengthMetrics>
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getUserConfigMargin(): NodeEdges<LengthMetrics>--><!--Device-FrameNode-getUserConfigMargin(): NodeEdges<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodeEdges](arkts-na-graphics-nodeedges-i.md)&lt;[LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)&gt; | 用户设置的外边距。 |

## getUserConfigPadding

```TypeScript
getUserConfigPadding(): NodeEdges<LengthMetrics>
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getUserConfigPadding(): NodeEdges<LengthMetrics>--><!--Device-FrameNode-getUserConfigPadding(): NodeEdges<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NodeEdges](arkts-na-graphics-nodeedges-i.md)&lt;[LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)&gt; | 用户设置的内边距。 |

## getUserConfigSize

```TypeScript
getUserConfigSize(): SizeT<LengthMetrics>
```

获取用户设置的宽高。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-getUserConfigSize(): SizeT<LengthMetrics>--><!--Device-FrameNode-getUserConfigSize(): SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeT](arkts-na-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-na-graphics-lengthmetrics-c.md)&gt; | 用户设置的宽高。 |

## insertChildAfter

```TypeScript
insertChildAfter(child: FrameNode, sibling: FrameNode | null): void
```

在FrameNode指定子节点之后添加新的子节点。当前FrameNode如果不可修改，抛出异常信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-insertChildAfter(child: FrameNode, sibling: FrameNode | null): void--><!--Device-FrameNode-insertChildAfter(child: FrameNode, sibling: FrameNode | null): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-na-framenode-c.md) | 是 | 需要添加的子节点。&lt;br/&gt;child节点不可以为声明式创建的节点，即不可修改的FrameNode。仅有从BuilderNode中获取的声明式节点可以作为子节点。若子节点不 符合规格，则抛出异常信息。&lt;br/&gt; child节点不可以拥有父节点，否则抛出异常信息。 |
| sibling | [FrameNode](arkts-na-framenode-c.md) \| null | 是 | 新节点将插入到该节点之后。若该参数设置为空，则新节点将插入到首个子节点之前。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../../apis-arkui/errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100025](../../apis-arkui/errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be adopted." |

## invalidate

```TypeScript
invalidate(): void
```

该方法会触发FrameNode自绘制内容的重新渲染。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-invalidate(): void--><!--Device-FrameNode-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## invalidateAttributes

```TypeScript
invalidateAttributes(): void
```

在当前帧触发节点属性更新。 当前节点的属性在构建阶段后被修改，这些改动不会立即生效，而是延迟到下一帧统一处理。 此功能强制当前帧内即时节点更新，确保同步应用渲染效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-invalidateAttributes(): void--><!--Device-FrameNode-invalidateAttributes(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isAttached

```TypeScript
isAttached(): boolean
```

获取节点是否被挂载到主节点树上。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-isAttached(): boolean--><!--Device-FrameNode-isAttached(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否被挂载到主节点树上。&lt;br/&gt;true表示节点被挂载到主节点树上，false表示节点不是被挂载到主节点树上。 |

## isClipToFrame

```TypeScript
isClipToFrame(): boolean
```

获取节点是否是剪裁到组件区域。当调用[dispose](#dispose)解除对实体FrameNode节点的引用关系之后，返回值为true。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-isClipToFrame(): boolean--><!--Device-FrameNode-isClipToFrame(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否是剪裁到组件区域。&lt;br/&gt;true表示节点剪裁到组件区域，false表示节点不是剪裁到组件区域。 |

## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前FrameNode对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节点在 dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-isDisposed(): boolean--><!--Device-FrameNode-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

## isInRenderState

```TypeScript
isInRenderState(): boolean
```

获取节点是否处于渲染状态，如果一个节点的对应RenderNode在渲染树上，则处于渲染状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-isInRenderState(): boolean--><!--Device-FrameNode-isInRenderState(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否处于渲染状态。&lt;br/&gt;true：处于渲染状态；false：不处于渲染状态。 |

## isMinimized

```TypeScript
isMinimized(): boolean
```

用于查询当前FrameNode是否为轻量化的FrameNode，轻量化的FrameNode占用的内存更小，但是不支持除了isMinimized以外的任何接口调用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-isMinimized(): boolean--><!--Device-FrameNode-isMinimized(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前FrameNode是否为轻量化的FrameNode，true表示当前FrameNode为轻量化的FrameNode，false表示当前FrameNode不是轻量化的 FrameNode |

## isModifiable

```TypeScript
isModifiable(): boolean
```

判断当前节点是否可修改。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-isModifiable(): boolean--><!--Device-FrameNode-isModifiable(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断当前节点是否可修改。&lt;br/&gt;true表示当前节点可修改，false表示当前节点不可修改。&lt;br/&gt;当节点为 [自定义组件节点](../../../ui/arkts-user-defined-node.md#自定义组件节点-framenode)中的系统组件代理节点或节点已经 [dispose]{ |

## isOnMainTree

```TypeScript
isOnMainTree(): boolean
```

查询节点是否被挂载到主节点树上。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-isOnMainTree(): boolean--><!--Device-FrameNode-isOnMainTree(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否被挂载到主节点树上。&lt;br/&gt;true表示节点被挂载到主节点树上，false表示节点没有被挂载到主节点树上。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100026](../../apis-arkui/errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The curent FrameNode has been disposed. |

## isTransferred

```TypeScript
isTransferred(): boolean
```

判断FrameNode是否通过transfer.transferStatic或者transfer.transferDynamic方法创建。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-isTransferred(): boolean--><!--Device-FrameNode-isTransferred(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回ComponentContent是否通过transfer.transferStatic或transfer.transferDynamic方法创建。&lt;br/&gt;true： ComponentContent通过transfer.transferStatic或transfer.transferDynamic方法创建。&lt;br/&gt;false：ComponentContent不通过 transfer.transferStatic或transfer.transferDynamic方法创建。 |

## isVisible

```TypeScript
isVisible(): boolean
```

获取节点是否可见。 > **说明：** > > 根据组件设置的visibility属性值判断该节点是否可见。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-isVisible(): boolean--><!--Device-FrameNode-isVisible(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否可见。&lt;br/&gt;true表示节点可见，false表示节点不可见。 |

## layout

```TypeScript
layout(position: NodePosition): void
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-layout(position: NodePosition): void--><!--Device-FrameNode-layout(position: NodePosition): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [NodePosition](arkts-na-nodeposition-t.md) | 是 | 组件进行布局时使用的位置信息。 |

## measure

```TypeScript
measure(constraint: LayoutConstraint): void
```

调用FrameNode的测量方法，根据父容器的布局约束，对FrameNode进行测量，计算出尺寸，如果测量方法被重写，则调用重写的方法。建议在[onMeasure](#onMeasure)方法中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-measure(constraint: LayoutConstraint): void--><!--Device-FrameNode-measure(constraint: LayoutConstraint): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | [LayoutConstraint](arkts-na-framenode-layoutconstraint-i.md) | 是 | 组件进行测量时使用的父容器布局约束。 |

## moveTo

```TypeScript
moveTo(targetParent: FrameNode, index?: int): void
```

将当前节点移动到目标 FrameNode 中作为其子节点。 若当前 FrameNode 不可修改，将抛出异常。 当 targetParent 为类型节点（typeNode）时，本接口会验证子节点的类型或数量。 若验证失败，将抛出异常。具体限制请参阅 typeNode 说明。 若当前 FrameNode 已被收养，将抛出异常。 &lt;p&gt;&lt;strong&gt;说明&lt;/strong&gt;： &lt;br&gt;当前移动操作仅支持以下类型的 TypedFrameNode：Stack、XComponent。 &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-moveTo(targetParent: FrameNode, index?: int): void--><!--Device-FrameNode-moveTo(targetParent: FrameNode, index?: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetParent | [FrameNode](arkts-na-framenode-c.md) | 是 | 目标父节点。 目标父节点不能是声明式创建的节点（即不可修改的 FrameNode）。 若不符合规范，将抛出异常。 |
| index | int | 否 | 节点移动至目标父节点中的索引位置。若该值为负数或无效值，节点将被移动到目标父节点的末尾。默认移动到目标父节点末尾。 若目标 FrameNode 已有 n 个子节点，则 index 的取值范围为 [0, n)。 &lt;br&gt;取值限定为整数。默认值：-1。 &lt;br&gt;默认值: -1 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../../apis-arkui/errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100027](../../apis-arkui/errorcode-node.md#100027-当前节点已被接纳为附属节点) | The current node has been adopted. |

## onDraw

```TypeScript
onDraw(context: DrawContext): void
```

该接口的[DrawContext](arkts-na-graphics-drawcontext-c.md#DrawContext)中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见 [调整自定义绘制Canvas的变换矩阵](../../../ui/arkts-user-defined-arktsNode-frameNode.md#调整自定义绘制canvas的变换矩阵)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-onDraw(context: DrawContext): void--><!--Device-FrameNode-onDraw(context: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [DrawContext](arkts-na-graphics-drawcontext-c.md) | 是 | 图形绘制上下文。自绘制区域无法超出组件自身大小。 |

## onLayout

```TypeScript
onLayout(position: NodePosition): void
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-onLayout(position: NodePosition): void--><!--Device-FrameNode-onLayout(position: NodePosition): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [NodePosition](arkts-na-nodeposition-t.md) | 是 | 组件进行布局时使用的位置信息。 |

## onMeasure

```TypeScript
onMeasure(constraint: LayoutConstraint): void
```

FrameNode的自定义测量方法，该方法会重写默认测量方法，在FrameNode进行测量时被调用，测量FrameNode及其内容的大小。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-onMeasure(constraint: LayoutConstraint): void--><!--Device-FrameNode-onMeasure(constraint: LayoutConstraint): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | [LayoutConstraint](arkts-na-framenode-layoutconstraint-i.md) | 是 | 组件进行测量时使用的布局约束。 |

## recycle

```TypeScript
recycle(): void
```

全局复用场景下，触发子组件回收，彻底释放FrameNode后端资源，以便于资源的重新复用，确保后端资源能够被有效回收并再次使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-recycle(): void--><!--Device-FrameNode-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## removeAdoptedChild

```TypeScript
removeAdoptedChild(child: FrameNode): void
```

移除被接纳的目标附属节点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-removeAdoptedChild(child: FrameNode): void--><!--Device-FrameNode-removeAdoptedChild(child: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-na-framenode-c.md) | 是 | 正在被接纳的节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../../apis-arkui/errorcode-node.md#100021-framenode节点不可修改) | The current FrameNode is not modifiable. |
| [100025](../../apis-arkui/errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be null." |
| [100026](../../apis-arkui/errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |

## removeChild

```TypeScript
removeChild(node: FrameNode): void
```

从FrameNode中删除指定的子节点。当前FrameNode如果不可修改，抛出异常信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-removeChild(node: FrameNode): void--><!--Device-FrameNode-removeChild(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-na-framenode-c.md) | 是 | 需要删除的子节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../../apis-arkui/errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |

## removeSupportedUIStates

```TypeScript
removeSupportedUIStates(uiStates: int): void
```

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-removeSupportedUIStates(uiStates: int): void--><!--Device-FrameNode-removeSupportedUIStates(uiStates: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiStates | int | 是 | 需要删除的UI状态。可以通过位或计算同时指定删除多个状态，如：removeUIStates = UIState.PRESSED  \|  UIState.FOCUSED。 |

## reuse

```TypeScript
reuse(): void
```

全局复用场景下，触发子组件复用，实现FrameNode后端资源的复用，提升资源利用效率。为保证资源充足，可以在recycle之后使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-reuse(): void--><!--Device-FrameNode-reuse(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setCrossLanguageOptions

```TypeScript
setCrossLanguageOptions(value: CrossLanguageOptions): void
```

设置当前FrameNode的跨ArkTS语言访问选项。例如ArkTS语言创建的节点，设置该节点是否可通过非ArkTS语言进行属性设置，从API版本26.0.0开始支持设置是否可通过非ArkTS语言进行组件树操作。当前 FrameNode如果不可修改或不可设置跨ArkTS语言访问选项，抛出异常信息。 > **说明：** > > 当前仅支持Scroll, > Swiper， > List， > ListItem， > ListItemGroup， > WaterFlow， > FlowItem， > Grid， > GridItem， > TextInput， > TextArea， > Column， > Row， > Stack， > Flex， > RelativeContainer， > Progress， > LoadingProgress， > Image， > Button， > CheckBox， > Radio， > Slider， > Toggle， > XComponent类型的 > [TypedFrameNode](arkts-na-framenode-typedframenode-c.md#TypedFrameNode)设置跨ArkTS语言访问选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-setCrossLanguageOptions(value: CrossLanguageOptions): void--><!--Device-FrameNode-setCrossLanguageOptions(value: CrossLanguageOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CrossLanguageOptions](arkts-na-framenode-crosslanguageoptions-i.md) | 是 | 跨ArkTS语言访问选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100022](../../apis-arkui/errorcode-node.md#100022-framenode节点的组件类型不支持调整跨语言的通用属性设置权限) | The FrameNode cannot be set whether to support cross-language common attribute setting. |

## setLayoutPosition

```TypeScript
setLayoutPosition(position: NodePosition): void
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-setLayoutPosition(position: NodePosition): void--><!--Device-FrameNode-setLayoutPosition(position: NodePosition): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [NodePosition](arkts-na-nodeposition-t.md) | 是 | FrameNode的布局后的位置。 |

## setMeasuredSize

```TypeScript
setMeasuredSize(size: Size): void
```

设置FrameNode的测量后的尺寸，默认单位PX。若设置的宽高为负数，自动取零。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-setMeasuredSize(size: Size): void--><!--Device-FrameNode-setMeasuredSize(size: Size): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Size](arkts-na-graphics-size-i.md) | 是 | FrameNode的测量后的尺寸。 |

## setNeedsLayout

```TypeScript
setNeedsLayout(): void
```

该方法会将FrameNode标记为需要布局的状态，下一帧将会进行重新布局。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameNode-setNeedsLayout(): void--><!--Device-FrameNode-setNeedsLayout(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

