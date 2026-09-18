# @ohos.arkui.components.ArkDynamicLayout

## Modules to Import

```TypeScript
import { DynamicLayout, DynamicLayoutAttribute } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [DynamicLayoutAttribute](arkts-arkui-arkui-components-arkdynamiclayout-dynamiclayoutattribute-c.md) | The [universal attributes](../arkts-components/arkts-arkui-commonmethod-c.md) are supported. |

### Interfaces

| Name | Description |
| --- | --- |
| [DynamicLayoutInterface](arkts-arkui-arkui-components-arkdynamiclayout-dynamiclayoutinterface-i.md) | Defines the dynamic layout container. |

### Constants

| Name | Description |
| --- | --- |
| [DynamicLayout](arkts-arkui-arkui-components-arkdynamiclayout-con.md#dynamiclayout) | Defines the dynamic layout container component, which supports dynamically switching between different layout algorithms at runtime without changing the status of child components.  > **Child Components** >  > Child components are supported. |
| [DynamicLayoutInstance](arkts-arkui-arkui-components-arkdynamiclayout-con.md#dynamiclayoutinstance) | Defines DynamicLayout Component instance. |

## Examples

```TypeScript
### Example 1: Implementing Waterfall Layout Using a Custom Layout Algorithm

This example shows how to override the onMeasure and onLayout functions to implement a waterfall layout for displaying a product list. In the waterfall layout, the heights of child components are calculated and the cumulative height of each column is recorded during the measurement phase, and child components are assigned to the column with the smallest current height during the layout phase, achieving an automatic fill effect.

Since API version 24, onMeasure and onLayout are added.


```

```TypeScript
### Example 2: Switching the Layout Algorithm

This example shows how to dynamically switch the layout algorithm of the DynamicLayout component by changing the LayoutAlgorithm variable decorated with [@Local](../../../ui/state-management/arkts-new-local.md). The example demonstrates how to switch the layout algorithm to RowLayoutAlgorithm (horizontal linear layout), ColumnLayoutAlgorithm (vertical linear layout), StackLayoutAlgorithm (stack layout), and GridLayoutAlgorithm (grid layout).

> NOTE
> 
> In this example, the preset layoutGravity attribute takes effect only under the Stack layout algorithm and does not take effect under the Row or Column layout algorithm.

Since API version 24, RowLayoutAlgorithm, ColumnLayoutAlgorithm, StackLayoutAlgorithm, and GridLayoutAlgorithm have been added.


```

```TypeScript
### Example 3: Modifying the Layout Algorithm Attributes

This example shows how to modify the space and justifyContent attributes of RowLayoutAlgorithm to update the layout effect of the DynamicLayout component.

Since API version 24, the space and justifyContent attributes are added.
```
