# LayoutAlgorithm

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ColumnLayoutAlgorithm](arkts-arkui-layoutalgorithm-columnlayoutalgorithm-c.md) | A vertical linear layout algorithm class, which is used to implement vertical linear arrangement of child components. It is suitable for scenarios where child components need to be arranged vertically, such as vertical lists, vertically stacked form items, and vertical menus. It supports setting the spacing between child components, horizontal alignment mode, vertical alignment mode, and arrangement direction, which provides layout capabilities similar to the **Column** component. |
| [CustomLayoutAlgorithm](arkts-arkui-layoutalgorithm-customlayoutalgorithm-c.md) | A custom layout algorithm class, which allows you to implement custom measurement and layout logic. It is suitable for complex layout scenarios that require fine-grained control over child component sizes and positions, such as waterfall flow layout, irregular grid layout, and dynamic flow layout. By overriding **onMeasure** and **onLayout**, you can implement layout strategies that are not covered by the built-in layout algorithms. |
| [GridLayoutAlgorithm](arkts-arkui-layoutalgorithm-gridlayoutalgorithm-c.md) | A grid layout algorithm class, which is used to implement grid arrangement of child components. It is suitable for scenarios where child components need to be arranged in a grid format, such as grid menus, photo grids, app lists, and product displays. It supports setting the column count template, column spacing, and row spacing, which provides layout capabilities similar to the **Grid** component. |
| [RowLayoutAlgorithm](arkts-arkui-layoutalgorithm-rowlayoutalgorithm-c.md) | A horizontal linear layout algorithm class, which is used to implement horizontal linear arrangement of child components. It is suitable for scenarios where child components need to be arranged horizontally, such as horizontal lists, toolbars, tab bars, and action button groups. It supports setting the spacing between child components, vertical alignment mode, horizontal alignment mode, and arrangement direction, which provides layout capabilities similar to the **Row** component. |
| [StackLayoutAlgorithm](arkts-arkui-layoutalgorithm-stacklayoutalgorithm-c.md) | A stack layout algorithm class, which is used to implement stacked arrangement of child components. It is suitable for scenarios where child components need to be displayed in a stacking manner, such as stacked layers, floating buttons, content areas with backgrounds, and card stack effects. It supports setting the alignment mode of child components within the stack container, which provides layout capabilities similar to the **Stack** component. |

### Interfaces

| Name | Description |
| --- | --- |
| [ColumnLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-columnlayoutalgorithmoptions-i.md) | Sets the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the vertical linear layout algorithm. |
| [GridLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-gridlayoutalgorithmoptions-i.md) | Sets the column count template, column spacing, and row spacing of the grid layout algorithm. |
| [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md) | Basic layout algorithm of the [DynamicLayout](../arkts-components/arkts-arkui-dynamiclayout-comp-attribute.md#dynamiclayoutattribute) container. |
| [RowLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-rowlayoutalgorithmoptions-i.md) | Sets the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the horizontal linear layout algorithm. |
| [StackLayoutAlgorithmOptions](arkts-arkui-layoutalgorithm-stacklayoutalgorithmoptions-i.md) | Sets the alignment method of the stack layout algorithm. |
