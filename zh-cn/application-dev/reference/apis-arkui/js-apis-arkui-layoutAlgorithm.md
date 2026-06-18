# LayoutAlgorithm
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zju_ljz-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

[DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md)组件支持的布局算法详细信息。

> **说明：**
>
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { LayoutAlgorithm, CustomLayoutAlgorithm, RowLayoutAlgorithm, ColumnLayoutAlgorithm, StackLayoutAlgorithm, GridLayoutAlgorithm } from '@kit.ArkUI';
```

## LayoutAlgorithm

动态布局容器[DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md)的布局算法基础类型。

> **说明：**
>
> 该类型变量可以赋值具体的布局算法类对象，如[CustomLayoutAlgorithm](#customlayoutalgorithm)类对象、[RowLayoutAlgorithm](#rowlayoutalgorithm)类对象等。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

## CustomLayoutAlgorithm

自定义布局算法类。

**装饰器类型：** [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **说明：**
>
> CustomLayoutAlgorithm类对象可以作为[DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

### onMeasure
onMeasure(self: FrameNode, constraint: LayoutConstraint): void

通过重写此函数，开发者可以自定义测量子组件的大小。ArkUI框架会在动态布局组件确定尺寸时，将该组件对应的FrameNode和布局约束通过onMeasure传递给开发者。不允许在onMeasure函数中改变状态变量。

> **说明：**
>
> 在此函数中，开发者可以调用[FrameNode](js-apis-arkui-frameNode.md#framenode-1)的[getChild()](js-apis-arkui-frameNode.md#getchild12)方法获取子组件FrameNode，调用[FrameNode](js-apis-arkui-frameNode.md#framenode-1)的[measure()](js-apis-arkui-frameNode.md#measure12)方法测量子组件大小，参考DynamicLayout组件[示例1（自定义布局算法实现瀑布流布局）](./arkui-ts/ts-container-dynamiclayout.md#示例1自定义布局算法实现瀑布流布局)。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| self | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | 是 | 动态布局组件在组件树上的实体节点。|
| constraint | [LayoutConstraint](js-apis-arkui-frameNode.md#layoutconstraint12) | 是 | 动态布局组件进行测量时使用的布局约束。|

### onLayout

ArkTS-Dyn: onLayout(self: FrameNode, position: Position): void

ArkTS-Sta: onLayout(self: FrameNode, position: NodePosition): void

通过重写此函数，开发者可以自定义排列子组件的位置。ArkUI框架会在动态布局组件确定位置时，将该组件对应的FrameNode和布局位置通过onLayout传递给开发者。不允许在onLayout函数中改变状态变量。

> **说明：**
>
> 在此函数中，开发者可以调用[FrameNode](js-apis-arkui-frameNode.md#framenode-1)的[getChild()](js-apis-arkui-frameNode.md#getchild12)方法获取子组件FrameNode，调用[FrameNode](js-apis-arkui-frameNode.md#framenode-1)的[layout()](js-apis-arkui-frameNode.md#layout12)方法设置子组件位置，参考DynamicLayout组件[示例1（自定义布局算法实现瀑布流布局）](./arkui-ts/ts-container-dynamiclayout.md#示例1自定义布局算法实现瀑布流布局)。

**模型约束：** 此接口仅可在Stage模型下使用。
  
**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| self | [FrameNode](js-apis-arkui-frameNode.md#framenode-1) | 是 | 动态布局组件在组件树上的实体节点。|
| position | ArkTS-Dyn: [Position](js-apis-arkui-graphics.md#position)<br/>ArkTS-Sta: [NodePosition](js-apis-arkui-graphics.md#nodeposition23) | 是 | 动态布局组件进行布局时使用的位置信息。|

**示例：**

请参考DynamicLayout组件[示例1（自定义布局算法实现瀑布流布局）](./arkui-ts/ts-container-dynamiclayout.md#示例1自定义布局算法实现瀑布流布局)。

## RowLayoutAlgorithm

水平方向线性布局算法类。

**装饰器类型：** [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **说明：**
>
> RowLayoutAlgorithm类对象可以作为[DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 横向布局元素水平方向间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| alignItems | [VerticalAlign](./arkui-ts/ts-appendix-enums.md#verticalalign) | 否 | 是 | 所有子组件在垂直方向上的对齐格式。<br/> 默认值：VerticalAlign.Center <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | 否 | 是 | 所有子组件在水平方向上的对齐格式。<br/> 默认值：FlexAlign.Start <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| isReverse | boolean | 否 | 是 | 子组件在水平方向上的排列是否反转。取值为true表示子组件在水平方向上反转排列，由于水平方向受通用属性[direction](./arkui-ts/ts-universal-attributes-location.md#direction)影响，如果[direction](./arkui-ts/ts-universal-attributes-location.md#direction)属性生效，再做一次反转。取值为false表示子组件在水平方向上正序排列。<br/>默认值：false <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |

### constructor

constructor(option?: RowLayoutAlgorithmOptions)

水平方向线性布局算法类的构造函数。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| option | [RowLayoutAlgorithmOptions](#rowlayoutalgorithmoptions对象说明) | 否 | 水平方向线性布局算法的构造入参，设置布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。|

**示例：**

请参考DynamicLayout组件[示例2（切换布局算法）](./arkui-ts/ts-container-dynamiclayout.md#示例2切换布局算法)。

## RowLayoutAlgorithmOptions对象说明

设置水平方向线性布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 横向布局元素水平方向间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。|
| alignItems | [VerticalAlign](./arkui-ts/ts-appendix-enums.md#verticalalign) | 否 | 是 | 所有子组件在垂直方向上的对齐格式。<br/> 默认值：VerticalAlign.Center <br/> 非法值：按默认值处理。|
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | 否 | 是 | 所有子组件在水平方向上的对齐格式。<br/> 默认值：FlexAlign.Start <br/> 非法值：按默认值处理。|
| isReverse | boolean | 否 | 是 | 子组件在水平方向上的排列是否反转。取值为true表示子组件在水平方向上反转排列，由于水平方向受通用属性[direction](./arkui-ts/ts-universal-attributes-location.md#direction)影响，如果[direction](./arkui-ts/ts-universal-attributes-location.md#direction)属性生效，再做一次反转。取值为false表示子组件在水平方向上正序排列。<br/>默认值：false <br/> 非法值：按默认值处理。|

## ColumnLayoutAlgorithm

垂直方向线性布局算法类。

**装饰器类型：** [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **说明：**
>
> ColumnLayoutAlgorithm类对象可以作为[DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 纵向布局元素垂直方向间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| alignItems | [HorizontalAlign](./arkui-ts/ts-appendix-enums.md#horizontalalign) | 否 | 是 | 所有子组件在水平方向上的对齐格式。<br/> 默认值：HorizontalAlign.Center <br/>  非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | 否 | 是 | 所有子组件在垂直方向上的对齐格式。<br/> 默认值：FlexAlign.Start <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| isReverse | boolean | 否 | 是 | 子组件在垂直方向上的排列是否反转。取值为true表示子组件在垂直方向上反转排列。取值为false表示子组件在垂直方向上正序排列。<br/>默认值：false <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |

### constructor 

constructor(option?: ColumnLayoutAlgorithmOptions)

垂直方向线性布局算法类的构造函数。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| option | [ColumnLayoutAlgorithmOptions](#columnlayoutalgorithmoptions对象说明) | 否 | 垂直方向线性布局算法的构造入参，设置布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。|

**示例：**

请参考DynamicLayout组件[示例2（切换布局算法）](./arkui-ts/ts-container-dynamiclayout.md#示例2切换布局算法)。

## ColumnLayoutAlgorithmOptions对象说明

设置垂直方向线性布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| space | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 纵向布局元素垂直方向间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。|
| alignItems | [HorizontalAlign](./arkui-ts/ts-appendix-enums.md#horizontalalign) | 否 | 是 | 所有子组件在水平方向上的对齐格式。<br/> 默认值：HorizontalAlign.Center <br/>  非法值：按默认值处理。|
| justifyContent | [FlexAlign](./arkui-ts/ts-appendix-enums.md#flexalign) | 否 | 是 | 所有子组件在垂直方向上的对齐格式。<br/> 默认值：FlexAlign.Start <br/> 非法值：按默认值处理。|
| isReverse | boolean | 否 | 是 | 子组件在垂直方向上的排列是否反转。取值为true表示子组件在垂直方向上反转排列。取值为false表示子组件在垂直方向上正序排列。<br/>默认值：false <br/> 非法值：按默认值处理。|

## StackLayoutAlgorithm

堆叠布局算法类。

**装饰器类型：** [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **说明：**
>
> StackLayoutAlgorithm类对象可以作为[DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| alignContent | [LocalizedAlignment](./arkui-ts/ts-appendix-enums.md#localizedalignment20) | 否 | 是 | 设置子组件在堆叠布局算法中对齐格式。 <br/> 默认值：LocalizedAlignment.CENTER <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |

### constructor

constructor(option?: StackLayoutAlgorithmOptions)

堆叠布局算法类的构造函数。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| option | [StackLayoutAlgorithmOptions](#stacklayoutalgorithmoptions对象说明) | 否 | 堆叠布局算法的构造入参，设置九宫格对齐格式。|

**示例：**

请参考DynamicLayout组件[示例2（切换布局算法）](./arkui-ts/ts-container-dynamiclayout.md#示例2切换布局算法)。

## StackLayoutAlgorithmOptions对象说明

设置堆叠布局算法的对齐方式。

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| alignContent | [LocalizedAlignment](./arkui-ts/ts-appendix-enums.md#localizedalignment20) | 否 | 是 | 设置子组件在堆叠布局算法中对齐格式。<br/> 默认值：LocalizedAlignment.CENTER <br/> 非法值：按默认值处理。|

## GridLayoutAlgorithm

网格布局算法类。

**装饰器类型：** [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md)

> **说明：**
>
> GridLayoutAlgorithm类对象可以作为[DynamicLayout](./arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| columnsTemplate | string \| [ItemFillPolicy](./arkui-ts/ts-types.md#itemfillpolicy22) | 否 | 是 | 设置当前网格布局的列数。<br/> 默认值：'1fr' <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| columnsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 列与列之间的间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |
| rowsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 行与行之间的间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。<br/>装饰器类型：[@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) |

### constructor

constructor(option?: GridLayoutAlgorithmOptions)

网格布局算法类的构造函数。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| option | [GridLayoutAlgorithmOptions](#gridlayoutalgorithmoptions对象说明) | 否 | 网格布局算法的构造入参，设置网格布局的列数、列间距、行间距。|

**示例：**

请参考DynamicLayout组件[示例2（切换布局算法）](./arkui-ts/ts-container-dynamiclayout.md#示例2切换布局算法)。

## GridLayoutAlgorithmOptions对象说明

设置网格布局算法的列数模板、列间距、行间距。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| columnsTemplate | string \| [ItemFillPolicy](./arkui-ts/ts-types.md#itemfillpolicy22) | 否 | 是 | 设置当前网格布局的列数。<br/> 默认值：'1fr' <br/> 非法值：按默认值处理。|
| columnsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 列与列之间的间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。|
| rowsGap | [LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12) | 否 | 是 | 行与行之间的间距。<br/> 默认值：LengthMetrics.vp(0) <br/> 非法值：按默认值处理。|