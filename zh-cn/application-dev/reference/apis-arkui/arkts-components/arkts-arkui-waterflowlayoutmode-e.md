# WaterFlowLayoutMode

瀑布流组件布局模式枚举。  
**说明：** | 对比维度 | ALWAYS_TOP_DOWN (默认) | SLIDING_WINDOW | |---------|------------------------|----------------| | 适用场景 | 固定列数 | 动态列数、大数据量、屏幕旋转 | | 布局策略 | 从顶部开始完整布局 | 滑动窗口式布局 | | 性能特点 | 依赖上方所有 FlowItem | 只考虑视窗内布局 | | 跳转效率 | 需要计算上方所有布局 | 快速跳转，无需完整计算 | | 列数切换 | 需要重新计算全部布局 | 只重新布局视窗内容 | | 屏幕旋转 | 支持，但性能较差 | 支持，性能好 | | 滚动条显示 | 始终支持 | API 18+ 支持 | | 布局一致性 | 始终保持一致 | 跳转后可能不一致 |

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ALWAYS_TOP_DOWN

```TypeScript
ALWAYS_TOP_DOWN = 0
```

默认的从上到下的布局模式。视窗内的FlowItem依赖视窗上方所有FlowItem的布局信息。因此跳转或切换列数时，需要计算出上方所有的FlowItem的布局信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDING_WINDOW

```TypeScript
SLIDING_WINDOW = 1
```

移动窗口式的布局模式。只考虑视窗内的布局信息，对视窗上方的FlowItem没有依赖关系，因此向后跳转或切换列数时只需要布局视窗内的FlowItem。建议优先采用该模式，尤其在应用需要支持屏幕旋转或动态切换列数的场景下。  
**说明：**
1. 无动画跳转到较远的位置时，会以目标位置为基准，向前或向后布局FlowItem。这之后如果滑回跳转前的位置，内容的布局效果可能和之前不一致。这个效果会导致跳转后回滑到顶部时，顶部节点可能不对齐。
2. 使用SLIDING_WINDOW布局模式并设置[WaterFlowSections](arkts-arkui-waterflowsections-c.md)分组时，滚动动画结束后，若视窗内包含分组起始位置，且检测到该分组在视窗内的列或行起始位置未对齐，或分组起始FlowItem与分组起始索引不一致，WaterFlow会重新计算布局以校正分组内容位置。
3. 使用SLIDING_WINDOW布局模式调用backToTop回到顶部操作时，若回顶动画结束后仍未到达顶部，WaterFlow会执行一次无动画的顶部校正，使内容重新对齐到起始位置。
4. [scroller](arkts-arkui-waterflowoptions-i.md)的currentOffset或offset接口返回的总偏移量在触发跳转或数据更新后不准确，在回滑到顶部时会重新校准，从API version 23开始，新增offset接口。
5. 如果在同一帧内调用跳转（如无动画的[scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex)、[scrollEdge](arkts-arkui-scroller-c.md#scrolledge)）和输入偏移量（如滑动手势或滚动动画），两者都会生效。
6. 调用无动画的[scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex)进行跳转，如果跳转到较远位置（超过视窗内的FlowItem数量的位置）时，移动窗口模式对总偏移量进行估算。
7. 仅在API version 18及以上版本中支持滚动条scrollBar显示。低于此版本时，设置滚动条将不显示。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
