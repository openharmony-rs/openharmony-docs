# WaterFlow

瀑布流容器，由“行”和“列”分割的单元格所组成，通过容器自身的排列规则，将不同大小的“项目”自上而下，如瀑布般紧密布局。支持多列布局、分组混合布局、懒加载、自动计算列数和边缘渐隐等功能，适用于图片画廊、商品展示、内容信息流等需要展示不同尺寸内容的场景。

> **说明：** > > 该组件从API version 9 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。 > > WaterFlow组件支持展示瀑布流布局，不支持编辑模式和子元素拖动功能。 > > 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。

## 子组件

仅支持FlowItem子组件和自定义组件。自定义组件在WaterFlow下使用时，建议使用FlowItem作为自定义组件的顶层组件，不建议给自定义组件设置属性和事件方法。

支持通过渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和[Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。

> **说明：** 
> 
> WaterFlow子组件的visibility属性设置为None时不显示，但该子组件周围的columnsGap、rowsGap、margin仍会生效。
> 
> 在涉及大量子组件的情况下，建议采用懒加载、缓存数据、组件复用、固定宽高以及布局优化等方法，以提升性能和减少内存占用。最佳实践请参考
> [优化瀑布流加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-waterflow-performance-optimization)
> 。
> 
> 纵向布局时，WaterFlow会计算每一列中已放置子组件的累计高度，并将新子组件放入累计高度最小的那一列，以保持整体布局紧凑。
> 
> 当FlowItem的主轴大小在显示后发生变化时，WaterFlow会清理受影响的布局信息，并根据当前[layoutMode](arkts-arkui-waterflowlayoutmode-e.md)从变化位置或当前窗口起始位置重新计算相关
> FlowItem的布局位置。由于瀑布流会将重新参与布局的FlowItem放入当前累计主轴大小最小的列或行，这些FlowItem所在列或行及偏移可能发生变化，表现为位置跳动。为减少位置跳动，建议保持FlowItem主轴大小稳定；图片
> 等异步内容建议预先设置固定宽高或占位大小，使用分组混合布局时也可以通过[GetItemMainSizeByIndex](arkts-arkui-getitemmainsizebyindex-t.md)回调提供稳定的主轴大小。
> 
> 使用[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)或
> [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)动态生成FlowItem时，如果影响FlowItem主轴大小的数据发生变
> 化，应同时通知框架数据已变化：LazyForEach场景请调用[DataChangeListener](arkts-arkui-datachangelistener-i.md)对应方法（如
> onDataChange、[onDataReloaded](arkts-arkui-datachangelistener-i.md#ondatareloaded)或
> [onDatasetChange](arkts-arkui-datachangelistener-i.md#ondatasetchange)）；Repeat场景应按
> [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)的数据更新规则修改状态数组。否则可能复用旧节点或旧缓存，导致显示内容、布局
> 结果与数据不一致。
> 
> 若多个列的高度相同，优先放入最左边的列。在RTL模式下，优先放入最右边的列。
> 
> 从API version 21开始，WaterFlow单个子组件的宽高最大为16777216px；API version 20及之前，WaterFlow单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异
> 常。

## WaterFlow

```TypeScript
WaterFlow(options?: WaterFlowOptions)
```

创建瀑布流容器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [WaterFlowOptions](arkts-arkui-waterflowoptions-i.md) | 否 | 瀑布流组件参数，用于设置滚动控制器、尾部组件、分组和布局模式。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [UIWaterFlowEvent](arkts-arkui-uiwaterflowevent-i.md) | frameNode中[getEvent('WaterFlow')](../arkts-apis/arkts-arkui-typenode-getevent-f.md)方法的返回值，可用于给WaterFlow节点设置滚动事件。 |
| [WaterFlowOptions](arkts-arkui-waterflowoptions-i.md) | 瀑布流组件参数对象。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [GetItemMainSizeByIndex](arkts-arkui-getitemmainsizebyindex-t.md) | 根据index获取指定Item的主轴大小。 |
| [OnWaterFlowScrollIndexCallback](arkts-arkui-onwaterflowscrollindexcallback-t.md) | WaterFlow组件可见区域item变化事件的回调类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [WaterFlowLayoutMode](arkts-arkui-waterflowlayoutmode-e.md) | 瀑布流组件布局模式枚举。 |

## 示例

```TypeScript
### 示例1（使用基本瀑布流）

该示例展示了WaterFlow组件数据加载处理、属性设置和事件回调等基本使用场景。

WaterFlowDataSource实现了[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)数据源接口[IDataSource](ts-rendering-control-lazyforeach.md#idatasource)，用于通过LazyForEach给WaterFlow提供子组件。

当[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)数据中影响FlowItem宽高的字段发生变化时，需要在修改数据后通知[DataChangeListener](ts-rendering-control-lazyforeach.md#datachangelistener)，例如调用[onDataChange](ts-rendering-control-lazyforeach.md#ondatachange8)或[onDataReloaded](ts-rendering-control-lazyforeach.md#ondatareloaded)。只修改数据内容但不触发数据变化通知时，LazyForEach可能不会刷新对应FlowItem。
```

```TypeScript

```

```TypeScript
### 示例2（自动计算列数）

该示例通过auto-fill实现了自动计算列数的效果。

WaterFlowDataSource说明及完整代码参考[示例1（使用基本瀑布流）](#示例1使用基本瀑布流)。


```

```TypeScript
### 示例3（使用分组）

该示例展示了分组的初始化以及splice、update、values、length等接口的不同效果。

如果配合状态管理V2使用，详情见：[WaterFlow与makeObserved](../../../ui/state-management/arkts-v1-v2-migration-inner-object.md#滚动组件)。

WaterFlowDataSource说明及完整代码参考[示例1（使用基本瀑布流）](#示例1使用基本瀑布流)。


```

```TypeScript
### 示例4（双指缩放改变列数）

该示例通过[priorityGesture](ts-gesture-settings.md#prioritygesture)和[PinchGesture](ts-basic-gestures-pinchgesture.md)实现了双指缩放改变列数效果。

WaterFlowDataSource说明及完整代码参考[示例1（使用基本瀑布流）](#示例1使用基本瀑布流)。


```

```TypeScript
### 示例5（设置边缘渐隐效果）

该示例通过[fadingEdge](ts-container-scrollable-common.md#fadingedge14)实现了WaterFlow组件开启边缘渐隐效果，并通过fadingEdgeLength参数设置边缘渐隐长度。

WaterFlowDataSource说明及完整代码参考[示例1（使用基本瀑布流）](#示例1使用基本瀑布流)。


```

```TypeScript
### 示例6（单边边缘效果）

该示例通过[edgeEffect](ts-container-scrollable-common.md#edgeeffect11)接口，实现了WaterFlow组件设置单边边缘效果。

WaterFlowDataSource说明及完整代码参考[示例1（使用基本瀑布流）](#示例1使用基本瀑布流)。


```

```TypeScript
### 示例7（WaterFlow组件设置和改变尾部组件）

从API version 18开始，该示例通过[WaterFlowOptions对象说明](#waterflowoptions对象说明)的footerContent接口，实现了WaterFlow组件设置尾部组件。通过ComponentContent的update函数更新尾部组件。

WaterFlowDataSource说明及完整代码参考[示例1（使用基本瀑布流）](#示例1使用基本瀑布流)。


```

```TypeScript
### 示例8（WaterFlow组件实现下拉刷新）

该示例通过[Refresh](ts-container-refresh.md)组件和WaterFlow组件，实现了下拉刷新瀑布流组件数据源。

WaterFlowDataSource说明及完整代码参考[示例1（使用基本瀑布流）](#示例1使用基本瀑布流)。


```

```TypeScript
### 示例9（WaterFlow组件基于断点配置列数）

从API version 22开始，该示例展示了WaterFlow组件支持基于断点配置列数效果。

WaterFlow宽度属于sm及更小的断点区间时显示2列。



WaterFlow宽度属于md断点区间时显示3列。



WaterFlow宽度属于lg及更大的断点区间时显示5列。


```

```TypeScript
### 示例10（WaterFlow组件实现获取内容高度）

从API version 22 开始，该示例通过WaterFlow组件，实现了获取内容高度。

WaterFlowDataSource说明及完整代码参考[示例1（使用基本瀑布流）](#示例1使用基本瀑布流)。


```

```TypeScript
### 示例11（设置滚动事件）

该示例通过FrameNode中的getEvent('WaterFlow')获取[UIWaterFlowEvent](arkts-arkui-uiwaterflowevent-i.md)，并为WaterFlow设置滚动事件回调，用于事件监听方因无法直接修改页面代码而无法使用声明式接口设置回调的场景。

从API version 19开始，新增UIWaterFlowEvent接口。
```
