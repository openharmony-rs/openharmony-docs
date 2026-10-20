# LayoutAlgorithm

[DynamicLayout](../arkts-components/arkts-arkui-dynamiclayout-comp-attribute.md)组件支持的布局算法详细信息。

LayoutAlgorithm是动态布局容器的布局算法基础类型，提供了多种布局算法实现，包括线性布局、堆叠布局和网格布局。
 开发者可以根据实际场景选择合适的布局算法，也可以继承CustomLayoutAlgorithm实现自定义布局。



## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ColumnLayoutAlgorithm](arkts-arkui-layoutalgorithm-columnlayoutalgorithm-c.md) | 垂直方向线性布局算法类，用于实现子组件的垂直线性排列。适用于需要垂直排列子组件的场景，如纵向列表、垂直堆叠的表单项、垂直菜单等。支持设置子组件间距、水平对齐方式、垂直对齐方式和排列方向，提供类似Column组件的布局能力。 |
| [CustomLayoutAlgorithm](arkts-arkui-layoutalgorithm-customlayoutalgorithm-c.md) | 自定义布局算法类，允许开发者实现自定义的测量和布局逻辑。适用于需要精细控制子组件尺寸和位置的复杂布局场景，如瀑布流布局、不规则网格布局、动态流式布局等。通过重写onMeasure和onLayout方法，开发者可以实现内置布局算法无法覆盖的布局策略。 |
| [GridLayoutAlgorithm](arkts-arkui-layoutalgorithm-gridlayoutalgorithm-c.md) | 网格布局算法类。 |
| [RowLayoutAlgorithm](arkts-arkui-layoutalgorithm-rowlayoutalgorithm-c.md) | 水平方向线性布局算法类，用于实现子组件的水平线性排列。适用于需要水平排列子组件的场景，如横向列表、工具栏、标签栏、操作按钮组等。支持设置子组件间距、垂直对齐方式、水平对齐方式和排列方向，提供类似Row组件的布局能力。 |
| [StackLayoutAlgorithm](arkts-arkui-layoutalgorithm-stacklayoutalgorithm-c.md) | 堆叠布局算法类，用于实现子组件的堆叠排列。适用于需要子组件重叠显示的场景，如图层叠加、悬浮按钮、带背景的内容区域、卡片叠加效果等。支持设置子组件在堆叠容器中的对齐方式，提供类似Stack组件的布局能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColumnLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-columnlayoutalgorithmoptions-i.md) | 设置垂直方向线性布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。 |
| [GridLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-gridlayoutalgorithmoptions-i.md) | 设置网格布局算法的列数模板、列间距、行间距。 |
| [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md) | 动态布局容器[DynamicLayout](../arkts-components/arkts-arkui-dynamiclayout-comp-attribute.md)的布局算法基础类型。 |
| [RowLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-rowlayoutalgorithmoptions-i.md) | 设置水平方向线性布局算法的间距、主轴对齐方式、交叉轴对齐方式及主轴排列方向。 |
| [StackLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-stacklayoutalgorithmoptions-i.md) | 设置堆叠布局算法的对齐方式。 |
