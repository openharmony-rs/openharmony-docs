# FrameNode

定义FrameNode。

**起始版本：** 11

<!--Device-unnamed-export class FrameNode--><!--Device-unnamed-export class FrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="addcomponentcontent"></a>
## addComponentContent

```TypeScript
addComponentContent<T>(content: ComponentContent<T> | ReactiveComponentContent<T>): void
```

支持添加ComponentContent类型的组件内容。要求当前节点是一个可修改的节点，即[isModifiable](arkts-arkui-framenode-c.md#ismodifiable-1)的返回值为true，否则抛出异常信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-addComponentContent<T>(content: ComponentContent<T> | ReactiveComponentContent<T>): void--><!--Device-FrameNode-addComponentContent<T>(content: ComponentContent<T> | ReactiveComponentContent<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ComponentContent](../arkts-components/arkts-arkui-componentcontent-t.md)&lt;T&gt; \| ReactiveComponentContent&lt;T&gt; | 是 | FrameNode节点中显示的组件内容。<br>**起始版本：** 12 - 21 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |

<a id="addsupporteduistates"></a>
## addSupportedUIStates

```TypeScript
addSupportedUIStates(uiStates: number, statesChangeHandler: UIStatesChangeHandler, excludeInner?: boolean): void
```

设置组件支持的多态样式状态。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-addSupportedUIStates(uiStates: number, statesChangeHandler: UIStatesChangeHandler, excludeInner?: boolean): void--><!--Device-FrameNode-addSupportedUIStates(uiStates: number, statesChangeHandler: UIStatesChangeHandler, excludeInner?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiStates | number | 是 | 需要处理目标节点的UI状态。<br>可以通过位或计算同时指定设置多个状态，如：targetUIStates = UIState.PRESSED  \|UIState.FOCUSED。 |
| statesChangeHandler | [UIStatesChangeHandler](arkts-arkui-uistateschangehandler-t.md) | 是 | 状态变化时的回调函数。 |
| excludeInner | boolean | 否 | 禁止内部默认状态样式处理的标志，默认值为false。<br> true表示禁止内部默认状态样式处理，false不禁止内部默认状态样式处理。 |

<a id="adoptchild"></a>
## adoptChild

```TypeScript
adoptChild(child: FrameNode): void
```

当前节点接纳目标节点为附属节点。被接纳的附属节点不能已有父节点。调用该接口实际上不会将其添加为子节点，而是仅允许其接收对应子节点的生命周期回调。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-adoptChild(child: FrameNode): void--><!--Device-FrameNode-adoptChild(child: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 指定待被接纳的节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The current FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be disposed." |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |

<a id="appendchild"></a>
## appendChild

```TypeScript
appendChild(node: FrameNode): void
```

在FrameNode最后一个子节点后添加新的子节点。当前FrameNode如果不可修改，抛出异常信息。[typeNode](arkts-arkui-typenode-n.md)在appendChild时会校验子组件类型或个数，不满足时抛出异常信息，限制情况请查看[typeNode](arkts-arkui-typenode-n.md)描述。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-appendChild(node: FrameNode): void--><!--Device-FrameNode-appendChild(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 需要添加的FrameNode。<br/> node节点不可以为声明式创建的节点，即不可修改的FrameNode。仅有从BuilderNode中获取的声明式节点可以作为子节点。若子节点不符合规格，则抛出异常信息。<br/> node节点不可以拥有父节点，否则抛出异常信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'node' is invalid: it cannot be adopted."<br>**适用版本：** 22+ |

<a id="cancelanimations"></a>
## cancelAnimations

```TypeScript
cancelAnimations(properties: AnimationPropertyType[]): boolean
```

请求取消FrameNode上指定属性上的所有动画，该方法需在节点所处线程中调用，会阻塞当前线程以等待取消结果。如果动画成功取消，节点上的属性值会被恢复为取消时的显示值（即当前状态）。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-cancelAnimations(properties: AnimationPropertyType[]): boolean--><!--Device-FrameNode-cancelAnimations(properties: AnimationPropertyType[]): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| properties | [AnimationPropertyType](arkts-arkui-animationpropertytype-e.md)[] | 是 | 待取消的动画属性枚举数组。可以一次取消一个节点上的多个属性的动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示动画是否取消成功。<br/>返回值为true：动画取消成功。<br/>返回值为false：动画取消失败。<br/>可能导致动画取消失败的原因：<br/> 1. 节点已经释放，调用过[dispose](arkts-arkui-framenode-c.md#dispose-1)方法。<br/> 2. 对于系统组件的代理节点，即对于[isModifiable](arkts-arkui-framenode-c.md#ismodifiable-1)为false的节点，调用该接口会失败。<br/> 3. 属性枚举数组存在非法枚举值。<br/> 4. 系统异常。如发生ipc异常导致动画取消失败。<br/> 1. 即使属性上没有动画，尝试取消该属性的动画，在无系统异常情况下调用取消接口也会返回true。<br/> 2. 如果开发者保证传入参数合法且节点正常，返回false时表明发生了系统异常。此时开发者可隔一段时间后再次尝试取消，或通过调用duration为0的[createAnimation](arkts-arkui-framenode-c.md#createanimation-1)接口停止属性上的动画。 |

<a id="clearchildren"></a>
## clearChildren

```TypeScript
clearChildren(): void
```

清除当前FrameNode的所有子节点。当前FrameNode如果不可修改，抛出异常信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-clearChildren(): void--><!--Device-FrameNode-clearChildren(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |

<a id="constructor"></a>
## constructor

```TypeScript
constructor(uiContext: UIContext)
```

FrameNode的构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-constructor(uiContext: UIContext)--><!--Device-FrameNode-constructor(uiContext: UIContext)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 创建对应节点时所需的UI上下文。 |

<a id="convertposition"></a>
## convertPosition

```TypeScript
convertPosition(position: Position, targetNode: FrameNode): Position
```

将点的坐标从当前节点的坐标系转换为目标节点的坐标系。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-convertPosition(position: Position, targetNode: FrameNode): Position--><!--Device-FrameNode-convertPosition(position: Position, targetNode: FrameNode): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-i.md) | 是 | 当前节点坐标系中的相对坐标。 |
| targetNode | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 本次坐标转换的目标节点，转换得到的点坐标就是该节点坐标系中的相对坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 目标节点局部坐标系中的转换坐标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100024](../errorcode-node.md#100024-节点没有公共祖先节点) | The current FrameNode and the target FrameNode do not have a common ancestor node. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'targetNode' is invalid: it cannot be disposed." |

<a id="convertpositionfromwindow"></a>
## convertPositionFromWindow

```TypeScript
convertPositionFromWindow(positionByWindow: Position): Position
```

将点的坐标从当前节点所在窗口的坐标系转换为当前节点的坐标系。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-convertPositionFromWindow(positionByWindow: Position): Position--><!--Device-FrameNode-convertPositionFromWindow(positionByWindow: Position): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionByWindow | [Position](arkts-arkui-position-i.md) | 是 | 当前节点所在窗口的坐标系中的相对坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 当前节点坐标系中的转换坐标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |
| [100028](../errorcode-node.md#100028-当前节点不在主节点树上) | The current FrameNode is not on the main tree. |

<a id="convertpositiontowindow"></a>
## convertPositionToWindow

```TypeScript
convertPositionToWindow(positionByLocal: Position): Position
```

将点的坐标从当前节点的坐标系转换为当前节点所在窗口的坐标系。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-convertPositionToWindow(positionByLocal: Position): Position--><!--Device-FrameNode-convertPositionToWindow(positionByLocal: Position): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionByLocal | [Position](arkts-arkui-position-i.md) | 是 | 当前节点坐标系中的相对坐标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 当前节点所在窗口的坐标系中的转换坐标。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |
| [100028](../errorcode-node.md#100028-当前节点不在主节点树上) | The current FrameNode is not on the main tree. |

<a id="createanimation"></a>
## createAnimation

```TypeScript
createAnimation(property: AnimationPropertyType, startValue: Optional<number[]>, endValue: number[], param: AnimateParam): boolean
```

创建FrameNode上属性的动画。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-createAnimation(property: AnimationPropertyType, startValue: Optional<number[]>, endValue: number[], param: AnimateParam): boolean--><!--Device-FrameNode-createAnimation(property: AnimationPropertyType, startValue: Optional<number[]>, endValue: number[], param: AnimateParam): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [AnimationPropertyType](arkts-arkui-animationpropertytype-e.md) | 是 | 动画属性枚举。 |
| startValue | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;number[]&gt; | 是 | 动画属性的起始值。取值为undefined或数组，取值为数组时数组长度需要和属性枚举匹配。如果为undefined则表示不显式指定动画初值，节点上一次设置的属性终值为此次动画的起点值。如果取值为数组，<br/>- 对于AnimationPropertyType.ROTATION，取值格式为[rotationX, rotationY, rotationZ]，单位为度（°），表示绕x、y、z轴的旋转角。<br/>- 对于AnimationPropertyType.TRANSLATION，取值格式为[translateX, translateY]，单位为px，表示沿x、y轴的平移量。<br/>- 对于AnimationPropertyType.SCALE，取值格式为[scaleX, scaleY]，表示x、y方向的缩放比例。<br/>- 对于AnimationPropertyType.OPACITY，取值格式为[opacity]，表示不透明度。opacity的取值范围为[0, 1]。<br/>当节点上从未设置过该属性时，需要显式指定startValue才能正常创建动画。当节点上已经设置过属性（如第二次及之后创建动画），则推荐不显式指定startValue或者显式指定startValue为上一次的终值，表示使用上一次的终值作为新的动画起点，避免起始值跳变。 |
| endValue | number[] | 是 | 动画属性的终止值。取值为数组，数组长度需要和属性枚举匹配。<br/>- 对于AnimationPropertyType.ROTATION，取值格式为[rotationX, rotationY, rotationZ]，单位为度（°），表示绕x、y、z轴的旋转角。<br/>- 对于AnimationPropertyType.TRANSLATION，取值格式为[translateX, translateY]，单位为px，表示沿x、y轴的平移量。<br/>- 对于AnimationPropertyType.SCALE，取值格式为[scaleX, scaleY]，表示x、y方向的缩放比例。<br/>- 对于AnimationPropertyType.OPACITY，取值格式为[opacity]，表示不透明度。opacity的取值范围为[0, 1]。 |
| param | [AnimateParam](../arkts-components/arkts-arkui-animateparam-i.md) | 是 | 动画参数。包含时长、动画曲线、结束回调等参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示动画是否创建成功。<br/>返回值为true：动画创建成功，如果动画参数中设置结束回调，动画结束后会调用结束回调。<br/>返回值为false：动画创建失败，即使动画参数中设置结束回调，结束回调也不会被调用。<br/>可能导致动画创建失败的原因：<br/> 1. 节点已经释放，调用过[dispose](arkts-arkui-framenode-c.md#dispose-1)方法。<br/> 2. 对于系统组件的代理节点，即对于[isModifiable](arkts-arkui-framenode-c.md#ismodifiable-1)为false的节点，调用该接口会失败。<br/> 3. 属性枚举非法，或属性枚举需要的长度与startValue或endValue的长度不匹配。<br/> 4. 该属性在第一次创建动画时没有显式指定startValue导致没有动画起点值，或设置的动画终值和动画起始值（当startValue为undefined时动画起始值为上一次的终值）相同，此时无动画产生。 |

<a id="createframenodes"></a>
## createFrameNodes

```TypeScript
static createFrameNodes(uiContext: UIContext, count: number): FrameNode[]
```

批量创建指定数量的FrameNode，返回FrameNode数组。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-static createFrameNodes(uiContext: UIContext, count: number): FrameNode[]--><!--Device-FrameNode-static createFrameNodes(uiContext: UIContext, count: number): FrameNode[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 创建对应节点时所需的UI上下文。 |
| count | number | 是 | 指定创建节点的数量，取值范围为大于零的整型。若给定值小于等于0或不是整数，则返回空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md)[] | Array of created FrameNodes. |

<a id="dispose"></a>
## dispose

```TypeScript
dispose(): void
```

立即解除当前FrameNode对象对实体FrameNode节点的引用关系。

> **说明：**  
>  
> - FrameNode对象调用dispose后，由于不对应任何实体FrameNode节点，在调用部分查询接口([getMeasuredSize](arkts-arkui-framenode-c.md#getmeasuredsize-1)、  
> [getLayoutPosition](arkts-arkui-framenode-c.md#getlayoutposition-1))的时候会导致应用出现jscrash。  
>  
> - 通过[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid-1)可以判断当前FrameNode是否对应一个实体FrameNode节点。当UniqueId大于0时表示该对象对应一个实体  
> FrameNode节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-dispose(): void--><!--Device-FrameNode-dispose(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="disposetree"></a>
## disposeTree

```TypeScript
disposeTree(): void
```

下树并递归释放当前节点为根的子树。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-disposeTree(): void--><!--Device-FrameNode-disposeTree(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="getchild"></a>
## getChild

```TypeScript
getChild(index: number): FrameNode | null
```

获取当前节点指定位置的子节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getChild(index: number): FrameNode | null--><!--Device-FrameNode-getChild(index: number): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 需要查询的子节点的序列号。<br/>index取值范围为[0, +∞)，若当前节点有n个子节点，index取值有效范围为[0, n-1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | Child node obtained. If the FrameNode does not contain the specified child node, null is returned. |

<a id="getchild-1"></a>
## getChild

```TypeScript
getChild(index: number, expandMode?: ExpandMode): FrameNode | null
```

获取当前节点指定位置的子节点，支持指定子节点展开模式。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getChild(index: number, expandMode?: ExpandMode): FrameNode | null--><!--Device-FrameNode-getChild(index: number, expandMode?: ExpandMode): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 需要查询的子节点的序列号。<br/>index取值范围为[0, +∞)，若当前节点有n个子节点，index取值有效范围为[0, n-1]。 |
| expandMode | [ExpandMode](arkts-arkui-framenode-expandmode-e.md) | 否 | 指定子节点展开模式。<br/>默认值：ExpandMode.EXPAND |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | Child node obtained. If the FrameNode does not contain the specified child node, null is returned. |

<a id="getchildrencount"></a>
## getChildrenCount

```TypeScript
getChildrenCount(): number
```

获取当前FrameNode的子节点数量。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getChildrenCount(): number--><!--Device-FrameNode-getChildrenCount(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取当前FrameNode的子节点数量。 |

<a id="getchildrencount-1"></a>
## getChildrenCount

```TypeScript
getChildrenCount(countMode?: ChildrenCountMode): number
```

根据指定的计数模式获取当前FrameNode的子节点数量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getChildrenCount(countMode?: ChildrenCountMode): int--><!--Device-FrameNode-getChildrenCount(countMode?: ChildrenCountMode): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| countMode | [ChildrenCountMode](arkts-arkui-framenode-childrencountmode-e.md) | 否 | The children count mode. Default value is ChildrenCountMode.ALL_EXPAND. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | - Returns the number of children of the current FrameNode based on the count mode. |

<a id="getcrosslanguageoptions"></a>
## getCrossLanguageOptions

```TypeScript
getCrossLanguageOptions(): CrossLanguageOptions
```

获取当前FrameNode的跨ArkTS语言访问选项。例如ArkTS语言创建的节点，返回该节点是否可通过非ArkTS语言进行属性设置和跨语言组件树操作，从API版本26.0.0开始支持获取是否可通过非ArkTS语言进行组件树操作。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getCrossLanguageOptions(): CrossLanguageOptions--><!--Device-FrameNode-getCrossLanguageOptions(): CrossLanguageOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CrossLanguageOptions](arkts-arkui-framenode-crosslanguageoptions-i.md) | 跨ArkTS语言访问选项。 |

<a id="getcustomproperty"></a>
## getCustomProperty

```TypeScript
getCustomProperty(name: string): Object | undefined
```

通过名称获取组件的自定义属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getCustomProperty(name: string): Object | undefined--><!--Device-FrameNode-getCustomProperty(name: string): Object | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 自定义属性的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | Value of the custom property. |

<a id="getfirstchild"></a>
## getFirstChild

```TypeScript
getFirstChild(): FrameNode | null
```

获取当前FrameNode的第一个子节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getFirstChild(): FrameNode | null--><!--Device-FrameNode-getFirstChild(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | First child node. If the FrameNode does not contain any child node, null is returned. |

<a id="getfirstchildindexwithoutexpand"></a>
## getFirstChildIndexWithoutExpand

```TypeScript
getFirstChildIndexWithoutExpand(): number
```

获取当前节点第一个在主节点树上的子节点的序列号。子节点序列号按所有子节点计算。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getFirstChildIndexWithoutExpand(): number--><!--Device-FrameNode-getFirstChildIndexWithoutExpand(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前节点第一个在主节点树上的子节点的序列号。 |

<a id="getframenodebyid"></a>
## getFrameNodeById

```TypeScript
getFrameNodeById(id: string): FrameNode | null
```

以当前节点为根节点，逐层查找所有子节点，返回第一个匹配指定id的节点。查找顺序为：先查找直接子节点，再查找二级子节点，依此类推，找到后立即返回。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getFrameNodeById(id: string): FrameNode | null--><!--Device-FrameNode-getFrameNodeById(id: string): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 查询的子节点id，为通用属性设置的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | First node that matches the specified ID, which is returned by searching for all child nodes layer by layer from the current node (which is used as the root node). If no child node of the current node matches the specified ID, a null is returned. |

<a id="getframenodebyuniqueid"></a>
## getFrameNodeByUniqueId

```TypeScript
getFrameNodeByUniqueId(id: number): FrameNode | null
```

以当前节点为根节点，查找并返回指定UniqueID（系统分配的节点唯一标识，该标识可通过[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid-1)接口获取）的子节点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getFrameNodeByUniqueId(id: int): FrameNode | null--><!--Device-FrameNode-getFrameNodeByUniqueId(id: int): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 查询的子节点的唯一标识UniqueID。<br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | Child node with the unique ID, which is found from the current node (which is used as the root node). If the child node with the unique ID cannot be found under the current node, a null is returned. |

<a id="getglobalpositionondisplay"></a>
## getGlobalPositionOnDisplay

```TypeScript
getGlobalPositionOnDisplay(): Position
```

获取FrameNode相对于全局屏幕的位置偏移，单位为VP。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getGlobalPositionOnDisplay(): Position--><!--Device-FrameNode-getGlobalPositionOnDisplay(): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 节点相对于全局屏幕的位置偏移，单位为VP。 |

<a id="getid"></a>
## getId

```TypeScript
getId(): string
```

获取用户设置的节点ID（通用属性设置的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)）。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getId(): string--><!--Device-FrameNode-getId(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 用户设置的节点ID（通用属性设置的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)）。 |

<a id="getinspectorinfo"></a>
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

<!--Device-FrameNode-getInspectorInfo(): Object--><!--Device-FrameNode-getInspectorInfo(): Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 节点的结构信息。 |

<a id="getinteractioneventbindinginfo"></a>
## getInteractionEventBindingInfo

```TypeScript
getInteractionEventBindingInfo(eventType: EventQueryType): InteractionEventBindingInfo | undefined
```

获取目标节点的事件绑定信息，如果该组件节点上没有绑定要查询的交互事件类型时，返回 undefined。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getInteractionEventBindingInfo(eventType: EventQueryType): InteractionEventBindingInfo | undefined--><!--Device-FrameNode-getInteractionEventBindingInfo(eventType: EventQueryType): InteractionEventBindingInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventType | [EventQueryType](arkts-arkui-eventquerytype-e.md) | 是 | 要查询的交互事件类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InteractionEventBindingInfo](arkts-arkui-framenode-interactioneventbindinginfo-i.md) | Returns an **InteractionEventBindingInfo** object containing event binding details if the interaction event is bound to the current node; returns **undefined** otherwise. |

<a id="getlastchildindexwithoutexpand"></a>
## getLastChildIndexWithoutExpand

```TypeScript
getLastChildIndexWithoutExpand(): number
```

获取当前节点最后一个在主节点树上的子节点的序列号。子节点序列号按所有子节点计算。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getLastChildIndexWithoutExpand(): number--><!--Device-FrameNode-getLastChildIndexWithoutExpand(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前节点最后一个在主节点树上的子节点的序列号。 |

<a id="getlayoutposition"></a>
## getLayoutPosition

```TypeScript
getLayoutPosition(): Position
```

获取FrameNode布局后相对于父组件的位置偏移，单位为PX。该偏移是父容器对该节点进行布局之后的结果，因此布局之后生效的offset属性和不参与布局的position属性不影响该偏移值。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getLayoutPosition(): Position--><!--Device-FrameNode-getLayoutPosition(): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 节点布局后相对于父组件的位置偏移，单位为PX。 |

<a id="getmeasuredsize"></a>
## getMeasuredSize

```TypeScript
getMeasuredSize(): Size
```

获取FrameNode测量后的大小，单位为PX。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getMeasuredSize(): Size--><!--Device-FrameNode-getMeasuredSize(): Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Size](../arkts-components/arkts-arkui-size-i.md) | 节点测量后的大小，单位为PX。 |

<a id="getnextsibling"></a>
## getNextSibling

```TypeScript
getNextSibling(): FrameNode | null
```

获取当前FrameNode的下一个同级节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getNextSibling(): FrameNode | null--><!--Device-FrameNode-getNextSibling(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | Next sibling node of the current FrameNode. If the FrameNode does not have the next sibling node, null is returned. |

<a id="getnodepropertyvalue"></a>
## getNodePropertyValue

```TypeScript
getNodePropertyValue(property: AnimationPropertyType): number[]
```

获取FrameNode上的属性值。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getNodePropertyValue(property: AnimationPropertyType): number[]--><!--Device-FrameNode-getNodePropertyValue(property: AnimationPropertyType): number[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| property | [AnimationPropertyType](arkts-arkui-animationpropertytype-e.md) | 是 | 动画属性枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | Current property value from the render node. The array length corresponds to the property type.<br>The return value format varies by property:<br>- An empty array (length 0) is returned if the node has been disposed, the [dispose](arkts-arkui-framenode-c.md#dispose-1)API has been called, or the property enumeration is invalid.<br>- **AnimationPropertyType.ROTATION**: [rotationX, rotationY, rotationZ] in degrees (°).<br>- **AnimationPropertyType.TRANSLATION**: [translateX, translateY] in px.<br>- **AnimationPropertyType.SCALE**: [scaleX, scaleY](scale factors).<br>- **AnimationPropertyType.OPACITY**: [opacity].<br>1. After animation cancellation, the node's property value is restored to the display value at the time of cancellation, which can be obtained using this API.<br>2. During animation playback, this API returns the final target value rather than real-time interpolated values.<br> |

<a id="getnodetype"></a>
## getNodeType

```TypeScript
getNodeType(): string
```

获取节点的类型。系统组件类型为组件名称，例如，按钮组件[Button](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-mouseevent-button-e.md)的类型为Button。而对于自定义组件，若其有渲染内容，则其类型为__Common__。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getNodeType(): string--><!--Device-FrameNode-getNodeType(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 节点的类型。 |

<a id="getopacity"></a>
## getOpacity

```TypeScript
getOpacity(): number
```

获取节点的不透明度，最小值为0，最大值为1。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getOpacity(): number--><!--Device-FrameNode-getOpacity(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 节点的不透明度。范围是[0, 1]，值越大透明度越低。 |

<a id="getparent"></a>
## getParent

```TypeScript
getParent(): FrameNode | null
```

获取当前FrameNode的父节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getParent(): FrameNode | null--><!--Device-FrameNode-getParent(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | Parent node of the current FrameNode. If the FrameNode does not contain a parent node, null is returned. |

<a id="getpositiontoparent"></a>
## getPositionToParent

```TypeScript
getPositionToParent(): Position
```

获取FrameNode相对于父组件的位置偏移，单位为VP。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getPositionToParent(): Position--><!--Device-FrameNode-getPositionToParent(): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 节点相对于父组件的位置偏移，单位为VP。 |

<a id="getpositiontoparentwithtransform"></a>
## getPositionToParentWithTransform

```TypeScript
getPositionToParentWithTransform(): Position
```

获取FrameNode相对于父组件带有绘制属性的位置偏移，单位为VP，绘制属性比如[transform](../arkts-components/arkts-arkui-commonmethod-c.md#transform-1),[translate](../arkts-components/arkts-arkui-commonmethod-c.md#translate-1)等，返回的坐标是组件布局时左上角变换后的坐标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getPositionToParentWithTransform(): Position--><!--Device-FrameNode-getPositionToParentWithTransform(): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 节点相对于父组件的位置偏移，单位为VP。 当设置了其他（比如：transform, translate等）绘制属性，由于浮点数精度的影响，返回值会有微小偏差。 |

<a id="getpositiontoscreen"></a>
## getPositionToScreen

```TypeScript
getPositionToScreen(): Position
```

获取FrameNode相对于屏幕的位置偏移，单位为VP。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getPositionToScreen(): Position--><!--Device-FrameNode-getPositionToScreen(): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 节点相对于屏幕的位置偏移，单位为VP。 |

<a id="getpositiontoscreenwithtransform"></a>
## getPositionToScreenWithTransform

```TypeScript
getPositionToScreenWithTransform(): Position
```

获取FrameNode相对于屏幕带有绘制属性的位置偏移，单位为VP，绘制属性比如[transform](../arkts-components/arkts-arkui-commonmethod-c.md#transform-1),[translate](../arkts-components/arkts-arkui-commonmethod-c.md#translate-1)等，返回的坐标是组件布局时左上角变换后的坐标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getPositionToScreenWithTransform(): Position--><!--Device-FrameNode-getPositionToScreenWithTransform(): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 节点相对于屏幕的位置偏移，单位为VP。 当设置了其他（比如：transform, translate等）绘制属性，由于浮点数精度的影响，返回值会有微小偏差。 |

<a id="getpositiontowindow"></a>
## getPositionToWindow

```TypeScript
getPositionToWindow(): Position
```

获取FrameNode相对于窗口的位置偏移，单位为VP。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getPositionToWindow(): Position--><!--Device-FrameNode-getPositionToWindow(): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 节点相对于窗口的位置偏移，单位为VP。 |

<a id="getpositiontowindowwithtransform"></a>
## getPositionToWindowWithTransform

```TypeScript
getPositionToWindowWithTransform(): Position
```

获取FrameNode相对于窗口带有绘制属性的位置偏移，单位为VP，绘制属性比如[transform](../arkts-components/arkts-arkui-commonmethod-c.md#transform-1),[translate](../arkts-components/arkts-arkui-commonmethod-c.md#translate-1)等，返回的坐标是组件布局时左上角变换后的坐标。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getPositionToWindowWithTransform(): Position--><!--Device-FrameNode-getPositionToWindowWithTransform(): Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Position](arkts-arkui-position-i.md) | 节点相对于窗口的位置偏移，单位为VP。 当设置了其他（比如：transform, translate等）绘制属性，由于浮点数精度的影响，返回值会有微小偏差。 |

<a id="getprevioussibling"></a>
## getPreviousSibling

```TypeScript
getPreviousSibling(): FrameNode | null
```

获取当前FrameNode的上一个同级节点。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getPreviousSibling(): FrameNode | null--><!--Device-FrameNode-getPreviousSibling(): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | Previous sibling node of the current FrameNode. If the FrameNode does not have the previous sibling node, null is returned. |

<a id="getrendernode"></a>
## getRenderNode

```TypeScript
getRenderNode(): RenderNode | null
```

获取FrameNode中持有的[RenderNode](arkts-arkui-rendernode-c.md)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getRenderNode(): RenderNode | null--><!--Device-FrameNode-getRenderNode(): RenderNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderNode](arkts-arkui-rendernode-c.md) | **RenderNode** instance. If the current FrameNode does not hold any RenderNode,**null** is returned. If the current FrameNode is a node created by a declarative component, **null** is returned. |

<a id="getuniqueid"></a>
## getUniqueId

```TypeScript
getUniqueId(): number
```

获取系统分配的唯一标识的节点UniqueID。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getUniqueId(): number--><!--Device-FrameNode-getUniqueId(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 系统分配的唯一标识的节点UniqueID。 |

<a id="getuserconfigborderwidth"></a>
## getUserConfigBorderWidth

```TypeScript
getUserConfigBorderWidth(): Edges<LengthMetrics>
```

获取用户设置的边框宽度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getUserConfigBorderWidth(): Edges<LengthMetrics>--><!--Device-FrameNode-getUserConfigBorderWidth(): Edges<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Edges](arkts-arkui-edges-i.md)&lt;LengthMetrics&gt; | 用户设置的边框宽度。 |

<a id="getuserconfigmargin"></a>
## getUserConfigMargin

```TypeScript
getUserConfigMargin(): Edges<LengthMetrics>
```

获取用户设置的外边距。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getUserConfigMargin(): Edges<LengthMetrics>--><!--Device-FrameNode-getUserConfigMargin(): Edges<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Edges](arkts-arkui-edges-i.md)&lt;LengthMetrics&gt; | 用户设置的外边距。 |

<a id="getuserconfigpadding"></a>
## getUserConfigPadding

```TypeScript
getUserConfigPadding(): Edges<LengthMetrics>
```

获取用户设置的内边距。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getUserConfigPadding(): Edges<LengthMetrics>--><!--Device-FrameNode-getUserConfigPadding(): Edges<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Edges](arkts-arkui-edges-i.md)&lt;LengthMetrics&gt; | 用户设置的内边距。 |

<a id="getuserconfigsize"></a>
## getUserConfigSize

```TypeScript
getUserConfigSize(): SizeT<LengthMetrics>
```

获取用户设置的宽高。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-getUserConfigSize(): SizeT<LengthMetrics>--><!--Device-FrameNode-getUserConfigSize(): SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SizeT](../arkts-components/arkts-arkui-sizet-t.md)&lt;LengthMetrics&gt; | 用户设置的宽高。 |

<a id="insertchildafter"></a>
## insertChildAfter

```TypeScript
insertChildAfter(child: FrameNode, sibling: FrameNode | null): void
```

在FrameNode指定子节点之后添加新的子节点。当前FrameNode如果不可修改，抛出异常信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-insertChildAfter(child: FrameNode, sibling: FrameNode | null): void--><!--Device-FrameNode-insertChildAfter(child: FrameNode, sibling: FrameNode | null): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 需要添加的子节点。<br/>child节点不可以为声明式创建的节点，即不可修改的FrameNode。仅有从BuilderNode中获取的声明式节点可以作为子节点。若子节点不符合规格，则抛出异常信息。<br/> child节点不可以拥有父节点，否则抛出异常信息。 |
| sibling | [FrameNode](arkts-arkui-framenode-c.md) \| null | 是 | 需要添加的子节点。<br/>child节点不可以为声明式创建的节点，即不可修改的FrameNode。仅有从BuilderNode中获取的声明式节点可以作为子节点。若子节点不符合规格，则抛出异常信息。<br/> child节点不可以拥有父节点，否则抛出异常信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be adopted."<br>**适用版本：** 22+ |

<a id="invalidate"></a>
## invalidate

```TypeScript
invalidate(): void
```

该方法会触发FrameNode自绘制内容的重新渲染。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-invalidate(): void--><!--Device-FrameNode-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="invalidateattributes"></a>
## invalidateAttributes

```TypeScript
invalidateAttributes(): void
```

在当前帧触发节点属性更新。

当前节点的属性在构建阶段后被修改，这些改动不会立即生效，而是延迟到下一帧统一处理。

此功能强制当前帧内即时节点更新，确保同步应用渲染效果。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-invalidateAttributes(): void--><!--Device-FrameNode-invalidateAttributes(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="isattached"></a>
## isAttached

```TypeScript
isAttached(): boolean
```

获取节点是否被挂载到主节点树上。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-isAttached(): boolean--><!--Device-FrameNode-isAttached(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否被挂载到主节点树上。<br/>true表示节点被挂载到主节点树上，false表示节点不是被挂载到主节点树上。 |

<a id="iscliptoframe"></a>
## isClipToFrame

```TypeScript
isClipToFrame(): boolean
```

获取节点是否是剪裁到组件区域。当调用[dispose](arkts-arkui-framenode-c.md#dispose-1)解除对实体FrameNode节点的引用关系之后，返回值为true。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-isClipToFrame(): boolean--><!--Device-FrameNode-isClipToFrame(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否是剪裁到组件区域。<br/>true表示节点剪裁到组件区域，false表示节点不是剪裁到组件区域。 |

<a id="isdisposed"></a>
## isDisposed

```TypeScript
isDisposed(): boolean
```

查询当前FrameNode对象是否已解除与后端实体节点的引用关系。前端节点均绑定有相应的后端实体节点，当节点调用dispose接口解除绑定后，再次调用接口可能会出现crash、返回默认值的情况。由于业务需求，可能存在节点在dispose后仍被调用接口的情况。为此，提供此接口以供开发者在操作节点前检查其有效性，避免潜在风险。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-isDisposed(): boolean--><!--Device-FrameNode-isDisposed(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 后端实体节点是否解除引用。true为节点已与后端实体节点解除引用，false为节点未与后端实体节点解除引用。 |

<a id="isinrenderstate"></a>
## isInRenderState

```TypeScript
isInRenderState(): boolean
```

获取节点是否处于渲染状态，如果一个节点的对应RenderNode在渲染树上，则处于渲染状态。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-isInRenderState(): boolean--><!--Device-FrameNode-isInRenderState(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否处于渲染状态。<br/>true：处于渲染状态；false：不处于渲染状态。 |

<a id="ismodifiable"></a>
## isModifiable

```TypeScript
isModifiable(): boolean
```

判断当前节点是否可修改。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-isModifiable(): boolean--><!--Device-FrameNode-isModifiable(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断当前节点是否可修改。<br/>true表示当前节点可修改，false表示当前节点不可修改。<br/>当节点为[自定义组件节点](docroot://ui/arkts-user-defined-node.md#自定义组件节点-framenode)中的系统组件代理节点或节点已经[dispose](arkts-arkui-framenode-c.md#dispose-1)时返回false。<br/>当返回false时，当前FrameNode不支持[appendChild](arkts-arkui-framenode-c.md#appendchild-1)、[insertChildAfter](arkts-arkui-framenode-c.md#insertchildafter-1)、[removeChild](arkts-arkui-framenode-c.md#removechild-1)、[clearChildren](arkts-arkui-framenode-c.md#clearchildren-1)、[createAnimation](arkts-arkui-framenode-c.md#createanimation-1)、[cancelAnimations](arkts-arkui-framenode-c.md#cancelanimations-1)的操作。 |

<a id="isonmaintree"></a>
## isOnMainTree

```TypeScript
isOnMainTree(): boolean
```

查询节点是否被挂载到主节点树上。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-isOnMainTree(): boolean--><!--Device-FrameNode-isOnMainTree(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否被挂载到主节点树上。<br/>true表示节点被挂载到主节点树上，false表示节点没有被挂载到主节点树上。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |

<a id="istransferred"></a>
## isTransferred

```TypeScript
isTransferred(): boolean
```

获取FrameNode上的属性值。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-isTransferred(): boolean--><!--Device-FrameNode-isTransferred(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - Returns true if the FrameNode was converted between dynamic and static states,otherwise, returns false. |

<a id="isvisible"></a>
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

<!--Device-FrameNode-isVisible(): boolean--><!--Device-FrameNode-isVisible(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 节点是否可见。<br/>true表示节点可见，false表示节点不可见。 |

<a id="layout"></a>
## layout

```TypeScript
layout(position: Position): void
```

调用FrameNode的布局方法，为FrameNode及其子节点指定布局位置，如果布局方法被重写，则调用重写的方法。建议在[onLayout](arkts-arkui-framenode-c.md#onlayout-1)方法中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-layout(position: Position): void--><!--Device-FrameNode-layout(position: Position): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-i.md) | 是 | 组件进行布局时使用的位置信息。 |

<a id="measure"></a>
## measure

```TypeScript
measure(constraint: LayoutConstraint): void
```

调用FrameNode的测量方法，根据父容器的布局约束，对FrameNode进行测量，计算出尺寸，如果测量方法被重写，则调用重写的方法。建议在[onMeasure](arkts-arkui-framenode-c.md#onmeasure-1)方法中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-measure(constraint: LayoutConstraint): void--><!--Device-FrameNode-measure(constraint: LayoutConstraint): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | 是 | 组件进行测量时使用的父容器布局约束。 |

<a id="moveto"></a>
## moveTo

```TypeScript
moveTo(targetParent: FrameNode, index?: number): void
```

将当前FrameNode移动到目标FrameNode的指定位置。当前FrameNode如果不可修改，抛出异常信息。targetParent为[typeNode](arkts-arkui-typenode-n.md)时会校验子组件类型或个数，不满足时抛出异常信息，限制情况请查看[typeNode](arkts-arkui-typenode-n.md)描述。

> **说明：**  
>  
> 当前仅支持以下类型的[TypedFrameNode](arkts-arkui-framenode-typedframenode-i.md)进行移动操作：[Stack](arkts-arkui-typenode-stack-t.md)、  
> [XComponent](arkts-arkui-typenode-xcomponent-t.md)。对于其他类型的节点，移动操作不会生效。  
>  
> 当前仅支持根节点为以下类型组件的[BuilderNode](arkts-arkui-buildernode-c.md)进行移动操作：[Stack](../../apis-arkts/arkts-apis/arkts-arkts-util-stack-stack-c.md)、  
> [XComponent](../arkts-components/arkts-arkui-xcomponent.md)、[EmbeddedComponent](../arkts-components/arkts-arkui-embeddedcomponent.md)。对于其他类型的组件，移动操作不会生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-moveTo(targetParent: FrameNode, index?: number): void--><!--Device-FrameNode-moveTo(targetParent: FrameNode, index?: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetParent | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 目标父节点。<br/>targetParent节点不可以为声明式创建的节点，即不可修改的FrameNode。若目标父节点不符合规格，则抛出异常信息。 |
| index | number | 否 | 子节点序列号。当前FrameNode将被添加到目标FrameNode对应序列号的子节点之前，若目标FrameNode有n个节点，index取值范围为[0, n-1]。<br/   >若参数无效或不指定，则添加到目标FrameNode的最后。<br/>默认值：-1 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |
| [100027](../errorcode-node.md#100027-当前节点已被接纳为附属节点) | The current node has been adopted.<br>**适用版本：** 22+ |

<a id="ondraw"></a>
## onDraw

```TypeScript
onDraw?(context: DrawContext): void
```

FrameNode的自绘制方法，该方法会重写默认绘制方法，在FrameNode进行内容绘制时被调用。

该接口的[DrawContext](arkts-arkui-graphics-drawcontext-c.md)中的Canvas是用于记录指令的临时Canvas，并非节点的真实Canvas。使用请参见[调整自定义绘制Canvas的变换矩阵](docroot://ui/arkts-user-defined-arktsNode-frameNode.md#调整自定义绘制canvas的变换矩阵)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-onDraw?(context: DrawContext): void--><!--Device-FrameNode-onDraw?(context: DrawContext): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [DrawContext](../arkts-components/arkts-arkui-drawcontext-t.md) | 是 | 图形绘制上下文。自绘制区域无法超出组件自身大小。 |

<a id="onlayout"></a>
## onLayout

```TypeScript
onLayout(position: Position): void
```

FrameNode的自定义布局方法，该方法会重写默认布局方法，在FrameNode进行布局时被调用，为FrameNode及其子节点指定位置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-onLayout(position: Position): void--><!--Device-FrameNode-onLayout(position: Position): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-i.md) | 是 | 组件进行布局时使用的位置信息。 |

<a id="onmeasure"></a>
## onMeasure

```TypeScript
onMeasure(constraint: LayoutConstraint): void
```

FrameNode的自定义测量方法，该方法会重写默认测量方法，在FrameNode进行测量时被调用，测量FrameNode及其内容的大小。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-onMeasure(constraint: LayoutConstraint): void--><!--Device-FrameNode-onMeasure(constraint: LayoutConstraint): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | 是 | 组件进行测量时使用的布局约束。 |

<a id="recycle"></a>
## recycle

```TypeScript
recycle(): void
```

全局复用场景下，触发子组件回收，彻底释放FrameNode后端资源，以便于资源的重新复用，确保后端资源能够被有效回收并再次使用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-recycle(): void--><!--Device-FrameNode-recycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="removeadoptedchild"></a>
## removeAdoptedChild

```TypeScript
removeAdoptedChild(child: FrameNode): void
```

移除被接纳的目标附属节点。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-removeAdoptedChild(child: FrameNode): void--><!--Device-FrameNode-removeAdoptedChild(child: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 正在被接纳的节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The current FrameNode is not modifiable. |
| [100025](../errorcode-node.md#100025-传入参数不符合要求) | The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'child' is invalid: it cannot be null." |
| [100026](../errorcode-node.md#100026-调用接口的实例对象已与后端实体节点解绑) | The current FrameNode has been disposed. |

<a id="removechild"></a>
## removeChild

```TypeScript
removeChild(node: FrameNode): void
```

从FrameNode中删除指定的子节点。当前FrameNode如果不可修改，抛出异常信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-removeChild(node: FrameNode): void--><!--Device-FrameNode-removeChild(node: FrameNode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 是 | 需要删除的子节点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100021](../errorcode-node.md#100021-framenode节点不可修改) | The FrameNode is not modifiable. |

<a id="removesupporteduistates"></a>
## removeSupportedUIStates

```TypeScript
removeSupportedUIStates(uiStates: number): void
```

删除组件当前注册的状态处理。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-removeSupportedUIStates(uiStates: number): void--><!--Device-FrameNode-removeSupportedUIStates(uiStates: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiStates | number | 是 | 需要删除的UI状态。<br>可以通过位或计算同时指定删除多个状态，如：removeUIStates = UIState.PRESSED  \|UIState.FOCUSED。 |

<a id="reuse"></a>
## reuse

```TypeScript
reuse(): void
```

全局复用场景下，触发子组件复用，实现FrameNode后端资源的复用，提升资源利用效率。为保证资源充足，可以在recycle之后使用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-reuse(): void--><!--Device-FrameNode-reuse(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="setcrosslanguageoptions"></a>
## setCrossLanguageOptions

```TypeScript
setCrossLanguageOptions(options: CrossLanguageOptions): void
```

设置当前FrameNode的跨ArkTS语言访问选项。例如ArkTS语言创建的节点，设置该节点是否可通过非ArkTS语言进行属性设置，从API版本26.0.0开始支持设置是否可通过非ArkTS语言进行组件树操作。当前FrameNode如果不可修改或不可设置跨ArkTS语言访问选项，抛出异常信息。

> **说明：**  
>  
> 当前仅支持[Scroll](arkts-arkui-typenode-scroll-t.md), [Swiper](arkts-arkui-typenode-swiper-t.md)，[List](arkts-arkui-typenode-list-t.md)，  
> [ListItem](arkts-arkui-typenode-listitem-t.md)，[ListItemGroup](arkts-arkui-typenode-listitemgroup-t.md)，  
> [WaterFlow](arkts-arkui-typenode-waterflow-t.md)，[FlowItem](arkts-arkui-typenode-flowitem-t.md)，[Grid](arkts-arkui-typenode-grid-t.md)，  
> [GridItem](arkts-arkui-typenode-griditem-t.md)，[TextInput](arkts-arkui-typenode-textinput-t.md)，[TextArea](arkts-arkui-typenode-textarea-t.md)，  
> [Column](arkts-arkui-typenode-column-t.md)，[Row](arkts-arkui-typenode-row-t.md)，[Stack](arkts-arkui-typenode-stack-t.md)，  
> [Flex](arkts-arkui-typenode-flex-t.md)，[RelativeContainer](arkts-arkui-typenode-relativecontainer-t.md)，  
> [Progress](arkts-arkui-typenode-progress-t.md)，[LoadingProgress](arkts-arkui-typenode-loadingprogress-t.md)，  
> [Image](arkts-arkui-typenode-image-t.md)，[Button](arkts-arkui-typenode-button-t.md)，[CheckBox](arkts-arkui-typenode-checkbox-t.md)，  
> [Radio](arkts-arkui-typenode-radio-t.md)，[Slider](arkts-arkui-typenode-slider-t.md)，[Toggle](arkts-arkui-typenode-toggle-t.md)，  
> [XComponent](arkts-arkui-typenode-xcomponent-t.md)类型的[TypedFrameNode](arkts-arkui-framenode-typedframenode-i.md)设置跨ArkTS语言访问选项。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-setCrossLanguageOptions(options: CrossLanguageOptions): void--><!--Device-FrameNode-setCrossLanguageOptions(options: CrossLanguageOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CrossLanguageOptions](arkts-arkui-framenode-crosslanguageoptions-i.md) | 是 | 跨ArkTS语言访问选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100022](../errorcode-node.md#100022-framenode节点的组件类型不支持调整跨语言的通用属性设置权限) | The FrameNode cannot be set whether to support cross-language common attribute setting. |

<a id="setlayoutposition"></a>
## setLayoutPosition

```TypeScript
setLayoutPosition(position: Position): void
```

设置FrameNode的布局后的位置，默认单位PX。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-setLayoutPosition(position: Position): void--><!--Device-FrameNode-setLayoutPosition(position: Position): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-position-i.md) | 是 | FrameNode的布局后的位置。 |

<a id="setmeasuredsize"></a>
## setMeasuredSize

```TypeScript
setMeasuredSize(size: Size): void
```

设置FrameNode的测量后的尺寸，默认单位PX。若设置的宽高为负数，自动取零。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-setMeasuredSize(size: Size): void--><!--Device-FrameNode-setMeasuredSize(size: Size): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Size](../arkts-components/arkts-arkui-size-i.md) | 是 | FrameNode的测量后的尺寸。 |

<a id="setneedslayout"></a>
## setNeedsLayout

```TypeScript
setNeedsLayout(): void
```

该方法会将FrameNode标记为需要布局的状态，下一帧将会进行重新布局。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-setNeedsLayout(): void--><!--Device-FrameNode-setNeedsLayout(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## commonAttribute

```TypeScript
get commonAttribute(): CommonAttribute
```

获取FrameNode中持有的CommonAttribute接口，用于设置[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)和[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

仅可以修改自定义节点的属性。

> **说明：**  
>  
> FrameNode的效果参考对齐方式为顶部起始端的[Stack](../../apis-arkts/arkts-apis/arkts-arkts-util-stack-stack-c.md)容器组件。  
>  
> FrameNode的属性支持情况参考  
> [属性或事件对attributemodifier的支持情况](docroot://ui/arkts-user-defined-extension-attributeModifier.md#属性或事件对attributemodifier的支持情况)。

**类型：** CommonAttribute

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-get commonAttribute(): CommonAttribute--><!--Device-FrameNode-get commonAttribute(): CommonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## commonEvent

```TypeScript
get commonEvent(): UICommonEvent
```

获取FrameNode中持有的UICommonEvent对象，用于设置基础事件。设置的基础事件与声明式定义的事件平行，参与事件竞争；设置的基础事件不覆盖原有的声明式事件。同时设置两个事件回调的时候，优先回调声明式事件。

LazyForEach场景下，由于存在节点的销毁重建，对于重建的节点需要重新设置事件回调才能保证监听事件正常响应。

**类型：** UICommonEvent

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-get commonEvent(): UICommonEvent--><!--Device-FrameNode-get commonEvent(): UICommonEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gestureEvent

```TypeScript
get gestureEvent(): UIGestureEvent
```

获取FrameNode中持有的UIGestureEvent对象，用于设置组件绑定的手势事件。通过gestureEvent接口设置的手势不会覆盖通过[绑定手势事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)绑定的手势，两者同时设置了手势时，优先回调绑定手势事件设置的手势事件。

**类型：** UIGestureEvent

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-FrameNode-get gestureEvent(): UIGestureEvent--><!--Device-FrameNode-get gestureEvent(): UIGestureEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

