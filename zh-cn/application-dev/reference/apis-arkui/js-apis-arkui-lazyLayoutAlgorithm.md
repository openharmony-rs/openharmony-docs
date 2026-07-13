# LazyLayoutAlgorithm

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong; @rongShao-Z; @guozejun-->
<!--Designer: @yylong-->
<!--Tester: @huchuyun-->
<!--Adviser: @Brilliantry_Rui-->

[LazyDynamicLayout](./arkui-ts/ts-container-lazydynamiclayout.md)组件支持的懒加载布局算法详细信息。

> **说明：**
>

> 本模块接口仅可在Stage模型下使用。

**起始版本：** 26.0.0

## 导入模块

```ts
import { LazyLayoutAlgorithm, LazyCustomLayoutAlgorithm, LazyLayoutHelper, LazyLayoutDirection } from '@kit.ArkUI';
```

## LazyLayoutAlgorithm

懒加载动态布局容器[LazyDynamicLayout](./arkui-ts/ts-container-lazydynamiclayout.md)的布局算法基础类型。

> **说明：**
> 该类型变量可以赋值具体的布局算法类对象，如[LazyCustomLayoutAlgorithm](#lazycustomlayoutalgorithm)类对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LazyLayoutDirection

懒加载布局方向枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| ---- | ---- | ---- |
| FORWARD | 0 | 向前方向，表示当前布局是从内容起始端往末尾端布局。 |
| BACKWARD | 1 | 向后方向，表示当前布局是从内容末尾端往起始端布局。 |

## LazyLayoutHelper

懒加载布局辅助类，提供布局方向和可视区域位置信息。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### getViewStart

getViewStart(): number

获取可视区域的起始位置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| number | 可视区域的起始位置。<br>单位：px。 |

### getViewEnd

getViewEnd(): number

获取可视区域的结束位置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| number | 可视区域的结束位置。<br>单位：px。 |

### getLazyLayoutDirection

getLazyLayoutDirection(): LazyLayoutDirection

获取懒加载布局方向。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [LazyLayoutDirection](#lazylayoutdirection) | 懒加载布局方向。 |

### setAdjustedOffset

setAdjustedOffset(offset: number): void

设置懒加载的调整偏移量。

在布局列数、间距等参数变化场景下，需要调用该接口调整偏移量以保持可视区域第一个子组件相对位置保持不变。<br>
以垂直方向布局为例，当布局方向为LazyLayoutDirection.FORWARD时，该接口设置的偏移量为容器上边界的调整量，当布局方向为LazyLayoutDirection.BACKWARD时，该接口设置的偏移量为容器下边界的调整量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| offset | number | 是 | 设置的调整偏移量，往内容末尾端调整为正，往内容起始端调整为负。单位：px。 |

### setChildrenInactive

setChildrenInactive(children: number[]): void

设置子组件为非激活状态。

如果子组件是通过[ForEach](./arkui-ts/ts-rendering-control-foreach.md)或[Repeat](./arkui-ts/ts-rendering-control-repeat.md)（未启用[virtualScroll](./arkui-ts/ts-rendering-control-repeat.md#virtualscroll)）生成的，设置为非激活状态后将不显示。<br>
如果子组件是通过[LazyForEach](./arkui-ts/ts-rendering-control-lazyforeach.md)或[Repeat](./arkui-ts/ts-rendering-control-repeat.md)（启用[virtualScroll](./arkui-ts/ts-rendering-control-repeat.md#virtualscroll)）生成的，设置为非激活状态后将销毁或回收。<br>
[LazyForEach](./arkui-ts/ts-rendering-control-lazyforeach.md)或[Repeat](./arkui-ts/ts-rendering-control-repeat.md)（启用[virtualScroll](./arkui-ts/ts-rendering-control-repeat.md#virtualscroll)）只支持连续的激活子组件；在两个激活子组件之间设置子组件为非激活状态不会生效。<br>
布局在可视区域外的子组件会自动设置为非激活状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| children | number[] | 是 | 设置为非激活状态的子组件索引数组。 |

## LazyCustomLayoutAlgorithm

自定义懒加载布局算法类。

> **说明：**
>
> LazyCustomLayoutAlgorithm类对象可以作为[LazyDynamicLayout](./arkui-ts/ts-container-lazydynamiclayout.md)组件的入参指定布局算法。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(option?: LazyCustomLayoutAlgorithmOptions)

自定义懒加载布局算法类的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| option | [LazyCustomLayoutAlgorithmOptions](#lazycustomlayoutalgorithmoptions) | 否 | 自定义懒加载布局算法的构造入参，设置布局算法的轴向。|

### onMeasure

onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void

通过重写此函数，开发者可以自定义测量子组件的大小。ArkUI框架会在懒加载动态布局组件确定尺寸时，将该组件对应的FrameNode、布局约束和懒加载辅助对象通过onMeasure传递给开发者。不允许在onMeasure函数中改变状态变量。

> **说明：**
>
> - 在此函数中，开发者可以调用[FrameNode](js-apis-arkui-frameNode.md#framenode-1)的[getChild()](js-apis-arkui-frameNode.md#getchild12)方法获取子组件FrameNode，调用[FrameNode](js-apis-arkui-frameNode.md#framenode-1)的[measure()](js-apis-arkui-frameNode.md#measure12)方法测量子组件大小，参考LazyDynamicLayout组件[示例1（实现懒加载自定义布局）](./arkui-ts/ts-container-lazydynamiclayout.md#示例1实现懒加载自定义布局)。
> - 在此函数中调用[getChild()](js-apis-arkui-frameNode.md#getchild12)方法获取子组件时，必须传入[ExpandMode.LAZY_NOT_EXPAND](js-apis-arkui-frameNode.md#expandmode15)，避免全量加载子组件导致懒加载失效。调用[getChildrenCount()](js-apis-arkui-frameNode.md#getchildrencount12)方法获取子组件总数时，必须传入[ChildrenCountMode.ALL_NOT_EXPAND](js-apis-arkui-frameNode.md#childrencountmode)，避免获取子组件总数时全量加载子组件导致懒加载失效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| self | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | 是 | 懒加载动态布局组件在组件树上的实体节点。|
| constraint | [LayoutConstraint](js-apis-arkui-frameNode.md#layoutconstraint12) | 是 | 懒加载动态布局组件进行测量时使用的布局约束。|
| helper | [LazyLayoutHelper](#lazylayouthelper) | 否 | 懒加载布局辅助对象，提供布局方向和可视区域位置信息。为undefined时表示不支持懒加载。helper为undefined的场景如下：<br>1. 在[WaterFlow](./arkui-ts/ts-container-waterflow.md)组件多列模式或分段模式的多列分段下使用时不支持懒加载。<br>2. 在[List](./arkui-ts/ts-container-list.md)组件下使用，当List设置了[lanes](./arkui-ts/ts-container-list.md#lanes9)、[chainAnimation](./arkui-ts/ts-container-list.md#chainanimation)、[scrollSnapAlign](./arkui-ts/ts-container-list.md#scrollsnapalign10)属性中的任意一个时不支持懒加载。 |

### onLayout

onLayout(self: FrameNode, position: Position): void

通过重写此函数，开发者可以自定义排列子组件的位置。ArkUI框架会在懒加载动态布局组件确定位置时，将该组件对应的FrameNode和布局位置通过onLayout传递给开发者。不允许在onLayout函数中改变状态变量。

> **说明：**
>
> - 在此函数中，开发者可以调用[FrameNode](js-apis-arkui-frameNode.md#framenode-1)的[getChild()](js-apis-arkui-frameNode.md#getchild12)方法获取子组件FrameNode，调用[FrameNode](js-apis-arkui-frameNode.md#framenode-1)的[layout()](js-apis-arkui-frameNode.md#layout12)方法设置子组件位置，参考LazyDynamicLayout组件[示例1（实现懒加载自定义布局）](./arkui-ts/ts-container-lazydynamiclayout.md#示例1实现懒加载自定义布局)。
> - 在此函数中调用[getChild()](js-apis-arkui-frameNode.md#getchild12)方法获取子组件时，必须传入[ExpandMode.LAZY_NOT_EXPAND](js-apis-arkui-frameNode.md#expandmode15)，避免全量加载子组件导致懒加载失效。调用[getChildrenCount()](js-apis-arkui-frameNode.md#getchildrencount12)方法获取子组件总数时，必须传入[ChildrenCountMode.ALL_NOT_EXPAND](js-apis-arkui-frameNode.md#childrencountmode)，避免获取子组件总数时全量加载子组件导致懒加载失效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| self | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | 是 | 懒加载动态布局组件在组件树上的实体节点。|
| position | [Position](js-apis-arkui-graphics.md#position) | 是 | 懒加载动态布局组件进行布局时使用的位置信息。|

**示例：**

请参考LazyDynamicLayout组件[示例1（实现懒加载自定义布局）](./arkui-ts/ts-container-lazydynamiclayout.md#示例1实现懒加载自定义布局)。

## LazyCustomLayoutAlgorithmOptions

自定义懒加载布局算法的构造入参，设置布局算法的主轴方向。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| axis | [Axis](./arkui-ts/ts-appendix-enums.md#axis) | 否 | 是 | 定义懒加载布局的主轴方向。<br/>默认值：Axis.Vertical |