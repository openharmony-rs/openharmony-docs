# WaterFlowLayoutMode

瀑布流组件布局模式枚举。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ALWAYS_TOP_DOWN

```TypeScript
ALWAYS_TOP_DOWN = 0
```

默认的从上到下的布局模式。视窗内的FlowItem依赖视窗上方所有FlowItem的布局信息。因此跳转或切换列数时，需要计算出上方所有的FlowItem的布局信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDING_WINDOW

```TypeScript
SLIDING_WINDOW = 1
```

移动窗口式的布局模式。只考虑视窗内的布局信息，对视窗上方的FlowItem没有依赖关系，因此向后跳转或切换列数时只需要布局视窗内的FlowItem。
建议优先采用该模式，尤其在应用需要支持屏幕旋转或动态切换列数的场景下。

<p><strong>说明</strong>
<br> 1. 无动画跳转到较远的位置时，会以目标位置为基准，向前或向后布局FlowItem。这之后如果滑回跳转前的位置，内容的布局效果可能和之前不一致。
这个效果会导致跳转后回滑到顶部时，顶部节点可能不对齐。所以该布局模式下会在滑动到顶部后自动调整布局，保证顶部对齐。
如果有多个分组的情况下，会在滑动结束时调整在视窗内的分组。
<br> 2. scroller的currentOffset或offset接口返回的总偏移量在触发跳转或数据更新后不准确，在回滑到顶部时会重新校准。
<br> 3. 如果在同一帧内调用跳转（如无动画的scrollToIndex、scrollEdge）和输入偏移量（如滑动手势或滚动动画），两者都会生效。
<br> 4. 调用无动画的scrollToIndex进行跳转，如果跳转到较远位置（超过视窗内的FlowItem数量的位置）时，移动窗口模式对总偏移量进行估算。
</p>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

