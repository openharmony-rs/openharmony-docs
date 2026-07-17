# WaterFlow

瀑布流容器，由“行”和“列”分割的单元格所组成，通过容器自身的排列规则，将不同大小的“项目”自上而下，如瀑布般紧密布局。

> **说明：**
>
> 该组件从API version 9 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> WaterFlow组件支持展示瀑布流布局，不支持编辑模式和子元素拖动功能。
>
> 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考[手势拦截增强]{@link common}进行处理。

## 子组件

仅支持[FlowItem]{@link flow_item}子组件和自定义组件。自定义组件在WaterFlow下使用时，建议使用FlowItem作为自定义组件的顶层组件，不建议给自定义组件设置属性和事件方法。

支持通过渲染控制类型（[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、[ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、[LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)和[Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)）动态生成子组件，更推荐使用LazyForEach或Repeat以优化性能。

> **说明：**  
>  
> WaterFlow子组件的visibility属性设置为None时不显示，但该子组件周围的columnsGap、rowsGap、margin仍会生效。  
> > 在涉及大量子组件的情况下，建议采用懒加载、缓存数据、组件复用、固定宽高以及布局优化等方法，以提升性能和减少内存占用。最佳实践请参考  
> [优化瀑布流加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-waterflow-performance-optimization)  
> 。  
>  
> 纵向布局时，WaterFlow会计算每一列中已放置子组件的累计高度，并将新子组件放入累计高度最小的那一列，以保持整体布局紧凑。  
>  
> 若多个列的高度相同，优先放入最左边的列。在RTL模式下，优先放入最右边的列。  
>  
> 从API version 21开始，WaterFlow单个子组件的宽高最大为16777216px；API version 20及之前，WaterFlow单个子组件的宽高最大为1000000px。子组件超出该大小可能导致滚动或显示异  
> 常。

## WaterFlowOptions对象说明

瀑布流组件参数对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |  
| ---------- | ----------------------------------------------- | ------ | -- | -------------------------------------------- |  
| footer | [CustomBuilder](docroot://reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8) | 否 | 是 | 设置WaterFlow尾部组件，用于在瀑布流末尾显示自定义内容（如加载提示、底部标识等）。不设置时不显示尾部组件。<br/>**说明：** <br/>使用方法参见[示例1](docroot://reference/apis-arkui/arkui-ts/ts-container-waterflow.md#示例1使用基本瀑布流)。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| footerContent<sup>18+</sup> | [ComponentContent]{@link ./../../../arkui/ComponentContent} | 否 | 是 | 设置WaterFlow尾部组件。<br/>该参数的优先级高于参数footer，即同时设置footer和footerContent时，以footerContent设置的组件为准。<br/>**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。 |  
| scroller | [Scroller]{@link scroll:Scroller} | 否 | 是 | 可滚动组件的控制器，与可滚动组件绑定。<br/>**说明：** <br/>不允许和其他滚动类组件，如：[ArcList]{@link ./../../../@ohos.arkui.ArcList}、[List]{@link list}、[Grid]{@link grid}、[Scroll]{@link scroll}和[WaterFlow]{@link water_flow}绑定同一个滚动控制对象。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |  
| sections<sup>12+</sup> | [WaterFlowSections]{@link WaterFlowSections} | 否 | 是 | 设置FlowItem分组，实现同一个瀑布流组件内部各分组使用不同列数混合布局。适用于需要在不同区域使用不同列数布局的场景。不设置时使用统一列数布局。<br/>**说明：** <br/>1. 使用分组混合布局时会忽略[columnsTemplate](docroot://reference/apis-arkui/arkui-ts/ts-container-waterflow.md#columnstemplate)和[rowsTemplate](docroot://reference/apis-arkui/arkui-ts/ts-container-waterflow.md#rowstemplate)属性。<br/>2. 使用分组混合布局时不支持单独设置footer，可以使用最后一个分组作为尾部组件。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |  
| layoutMode<sup>12+</sup> |[WaterFlowLayoutMode]{@link WaterFlowLayoutMode} | 否 | 是 | 设置WaterFlow的布局模式，根据使用场景选择更切合的模式。<br/>**说明：** <br/>默认值：[ALWAYS_TOP_DOWN]{@link WaterFlowLayoutMode}。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |

## SectionOptions<sup>12+</sup>对象说明

FlowItem分组配置信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |  
|------|-----|-----|----|-----|  
| itemsCount | number | 否 | 否 | 分组中FlowItem数量，必须是非负数。若splice、push、update方法收到的分组中有分组的itemsCount小于0，则不会执行该方法。 避免使用itemsCount为0的分组，这可能导致布局计算异常。|  
| crossCount | number | 否 | 是 | 纵向布局时为列数，横向布局时为行数，默认值：1。小于1的按默认值处理。 |  
| columnsGap | [Dimension]{@link units:Dimension} | 否 | 是 | 该分组的列间距，不设置该参数时默认使用瀑布流的[columnsGap](docroot://reference/apis-arkui/arkui-ts/ts-container-waterflow.md#columnsgap)，设置非法值时使用0vp。 |  
| rowsGap | [Dimension]{@link units:Dimension} | 否 | 是 | 该分组的行间距，不设置该参数时默认使用瀑布流的[rowsGap](docroot://reference/apis-arkui/arkui-ts/ts-container-waterflow.md#rowsgap)，设置非法值时使用0vp。 |  
| margin | [Margin]{@link units:Margin} \| [Dimension]{@link units:Dimension} | 否 | 是 | 该分组的外边距参数为Length类型时，四个方向外边距同时生效。<br>默认值：0<br>单位：vp<br>margin设置百分比时，上下左右外边距均以瀑布流的width作为基础值。 |  
| onGetItemMainSizeByIndex | [GetItemMainSizeByIndex]{@link GetItemMainSizeByIndex} | 否 | 是 | 瀑布流组件布局过程中获取指定index的FlowItem的主轴大小，纵向瀑布流时为高度，横向瀑布流时为宽度，单位vp。<br/>**说明：** <br/>1. 同时使用onGetItemMainSizeByIndex和FlowItem的宽高属性时，主轴大小以onGetItemMainSizeByIndex返回结果为准，onGetItemMainSizeByIndex会覆盖FlowItem的主轴长度。<br/>2. 使用onGetItemMainSizeByIndex可以提高瀑布流跳转到指定位置或index时的效率，避免混用设置onGetItemMainSizeByIndex和未设置的分组，会导致布局异常。<br/>3. onGetItemMainSizeByIndex返回负数时FlowItem高度为0。 |

## WaterFlowLayoutMode<sup>12+</sup>枚举说明

瀑布流组件布局模式枚举。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |  
| ------ | ------ | -------------------- |  
| ALWAYS_TOP_DOWN | 0 | 默认的从上到下的布局模式。视窗内的FlowItem依赖视窗上方所有FlowItem的布局信息。因此跳转或切换列数时，需要计算出上方所有的FlowItem的布局信息。 |  
| SLIDING_WINDOW | 1 | 移动窗口式的布局模式。只考虑视窗内的布局信息，对视窗上方的FlowItem没有依赖关系，因此向后跳转或切换列数时只需要布局视窗内的FlowItem。建议优先采用该模式，尤其在应用需要支持屏幕旋转或动态切换列数的场景下。 <br/>**说明：** <br/>1. 无动画跳转到较远的位置时，会以目标位置为基准，向前或向后布局FlowItem。这之后如果滑回跳转前的位置，内容的布局效果可能和之前不一致。 这个效果会导致跳转后回滑到顶部时，顶部节点可能不对齐。所以该布局模式下会在滑动到顶部后自动调整布局，保证顶部对齐。在有多个分组的情况下，会在滑动结束时调整在视窗内的分组。<br/> 2. [scroller](docroot://reference/apis-arkui/arkui-ts/ts-container-waterflow.md#waterflowoptions对象说明)的[currentOffset]{@link scroll:Scroller.currentOffset}或[offset]{@link scroll:Scroller.offset}接口返回的总偏移量在触发跳转或数据更新后不准确，在回滑到顶部时会重新校准，从API version 23开始，新增offset接口。 <br/> 3. 如果在同一帧内调用跳转（如无动画的[scrollToIndex]{@link scroll:Scroller.scrollToIndex}、[scrollEdge]{@link scroll:Scroller.scrollEdge}）和输入偏移量（如滑动手势或滚动动画），两者都会生效。 <br/> 4. 调用无动画的[scrollToIndex]{@link scroll:Scroller.scrollToIndex}进行跳转，如果跳转到较远位置（超过视窗内的FlowItem数量的位置）时，移动窗口模式对总偏移量进行估算。 <br/> 5. 仅在API version 18及以上版本中支持滚动条[scrollBar](docroot://reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#scrollbar11)显示。低于此版本时，设置滚动条将不显示。|

| 对比维度 | ALWAYS_TOP_DOWN (默认) | SLIDING_WINDOW |  
|---------|------------------------|----------------|  
| 适用场景 | 固定列数、简单瀑布流 | 动态列数、大数据量、屏幕旋转 |  
| 布局策略 | 从顶部开始完整布局 | 滑动窗口式布局 |  
| 性能特点 | 依赖上方所有 FlowItem | 只考虑视窗内布局 |  
| 跳转效率 | 需要计算上方所有布局 | 快速跳转，无需完整计算 |  
| 列数切换 | 需要重新计算全部布局 | 只重新布局视窗内容 |  
| 屏幕旋转 | 支持，但性能较差 | 支持，性能好 |  
| 滚动条显示 | 始终支持 | API 18+ 支持 |  
| 布局一致性 | 始终保持一致 | 跳转后可能不一致 |

## WaterFlow

```TypeScript
WaterFlow(options?: WaterFlowOptions)
```

创建瀑布流容器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowInterface-(options?: WaterFlowOptions): WaterFlowAttribute--><!--Device-WaterFlowInterface-(options?: WaterFlowOptions): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | WaterFlowOptions | 否 | 瀑布流组件参数。 |

## 汇总

- [UIWaterFlowEvent](arkts-arkui-waterflow-uiwaterflowevent-i.md)
- [WaterFlowOptions](arkts-arkui-waterflow-waterflowoptions-i.md)
- [GetItemMainSizeByIndex](arkts-arkui-waterflow-getitemmainsizebyindex-t.md)
- [OnWaterFlowScrollIndexCallback](arkts-arkui-waterflow-onwaterflowscrollindexcallback-t.md)
- [WaterFlowLayoutMode](arkts-arkui-waterflow-waterflowlayoutmode-e.md)
