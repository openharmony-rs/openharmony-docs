# 创建瀑布流（WaterFlow）

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangyuhao-->
<!--Designer: @zcdqs-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @HelloCrease-->

[瀑布流](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md)常用于展示图片信息，尤其在购物和资讯类应用中。
ArkUI提供了WaterFlow容器组件，用于构建瀑布流布局。WaterFlow组件支持条件渲染、循环渲染和懒加载等方式生成子组件。

> **说明：** 
>
> 本文仅展示关键代码片段，可运行的完整代码请参考[WaterFlow示例代码](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#示例)。

## 布局与约束

瀑布流支持横向和纵向布局。在纵向布局中，可以通过[columnsTemplate](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#columnstemplate)设置列数；在横向布局中，可以通过[rowsTemplate](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#rowstemplate)设置行数。

在瀑布流的纵向布局中，第一行的子节点按从左到右顺序排列，从第二行开始，每个子节点将放置在当前总高度最小的列。如果多个列的总高度相同，则按照从左到右的顺序填充。如下图：

![](figures/waterflow.png)

在瀑布流的横向布局中，每个子节点都会放置在当前总宽度最小的行。若多行总宽度相同，则按照从上到下的顺序进行填充。

![](figures/waterflow-row.png)

## 无限滚动

### 到达末尾时新增数据

瀑布流常用于无限滚动的信息流。可以在瀑布流组件到达末尾位置时触发的[onReachEnd](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#onreachend)事件回调中对[LazyForEach](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md)增加新数据，并将footer做成正在加载新数据的样式（使用[LoadingProgress](../reference/apis-arkui/arkui-ts/ts-basic-components-loadingprogress.md)组件）。

<!-- @[WaterFlowInfiniteScrolling_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/waterFlow/WaterFlowInfiniteScrolling.ets) -->

在此处应通过在数据末尾添加元素的方式来新增数据，不可直接修改dataArray后通过LazyForEach的onDataReloaded()方法通知瀑布流重新加载数据。

由于在瀑布流布局中，各子节点的高度不一致，下面的节点位置依赖于上面的节点，所以重新加载所有数据会触发整个瀑布流重新计算布局，可能会导致卡顿。在数据末尾增加数据后，应使用`onDatasetChange([{ type: DataOperationType.ADD, index: len, count: count }])`通知，以使瀑布流能够识别新增数据并继续加载，同时避免对已有数据进行重复处理。

![](figures/waterflow-demo1.gif)

### 提前新增数据

虽然在onReachEnd()触发时加载数据可以实现无限加载，但在滑动到底部会出现明显的停顿。

为了实现更加流畅的无限滑动，需要调整增加新数据的时机。比如可以在LazyForEach还剩余若干个数据未遍历的情况下提前加载新数据。以下代码通过在WaterFlow的[onScrollIndex](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#onscrollindex11)中判断当前显示的最后一个子节点相对数据集终点的距离，并在合适时机提前加载新数据，实现了无停顿的无限滚动。

<!-- @[waterFlowInfiniteScrollingEarly_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/waterFlow/WaterFlowInfiniteScrollingEarly.ets) -->

![](figures/waterflow-demo2.gif)

## 动态切换列数

通过动态调整瀑布流的列数，应用能够实现在列表模式与瀑布流模式间的切换，或适应屏幕宽度的变化。 若要动态设置列数，建议采用瀑布流的移动窗口布局模式，这可以实现更快速的列数转换。

<!-- @[waterFlowDynamicSwitchover_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/waterFlow/WaterFlowDynamicSwitchover.ets) -->

![](figures/waterflow-columns.gif)

## 分组混合布局

许多应用界面在瀑布流上方包含其他内容，这类场景可通过在Scroll或List内部嵌套WaterFlow来实现。类似下图：

![](figures/waterflow-sections1.png)

如果能够将不同部分的子节点整合到一个数据源中，那么通过设置 WaterFlowSections，可以在一个 WaterFlow 容器内实现混合布局。与嵌套滚动相比，这种方法可以简化滚动事件处理等应用逻辑。

每个瀑布流分组可以分别设置自己的列数、行间距、列间距、margin和子节点总数，如下代码可以实现上述效果：

<!-- @[waterFlowGroupingMixing_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/waterFlow/WaterFlowGroupingMixing.ets) -->

>**说明：**
>
>使用分组混合布局时不支持单独设置footer，可以使用最后一个分组作为尾部组件。
>
>增加或删除数据后需要同步修改对应分组的itemCount。

## 相关实例

针对瀑布流开发，有以下实例可供参考：

- [WaterFlow示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ScrollableComponent/entry/src/main/ets/pages/waterFlow)

<!--RP1--><!--RP1End-->