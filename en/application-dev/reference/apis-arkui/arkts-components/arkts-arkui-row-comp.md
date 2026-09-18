# Row

The **Row** component lays out child components horizontally. > **NOTE** > > If no width or height is set for the **Row** component, the component automatically adapts to the size of its child > components in the main axis and cross axis respectively. > > **Child Components** > > Supported

## Row

```TypeScript
Row(options?: RowOptions)
```

Creates a horizontal linear layout container. You can set the spacing between child components.

> **NOTE:** 
> 
> Excessive component nesting (either too deep a hierarchy or too many nested components) incurs significant
> performance overhead. For performance purposes, you are advised to remove redundant nodes to simplify the
> component tree, use layout boundaries to reduce redundant layout calculations, properly apply rendering control
> syntax and layout component methods to minimize unnecessary re-renders and computations. For details about the
> best practices, see
> [Layout Optimization](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-improve-layout-performance)
> .

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RowOptions](arkts-arkui-rowoptions-i.md) | No | Spacing between elements in the horizontal layout. The value can be of the number or string type. |

## Row

```TypeScript
Row(options?: RowOptions | RowOptionsV2)
```

Creates a horizontal linear layout container. You can set the spacing between child components.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RowOptions](arkts-arkui-rowoptions-i.md) &#124; [RowOptionsV2](arkts-arkui-rowoptionsv2-i.md) | No | Spacing between elements in a horizontal layout. The value can be of the number, string, or Resource type. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [RowOptions](arkts-arkui-rowoptions-i.md) | Sets the spacing between child components of the **Row** component. |
| [RowOptionsV2](arkts-arkui-rowoptionsv2-i.md) | Sets the spacing between child components of the **Row** component. |

## Examples

```TypeScript
### Example 1: Setting the Layout Attributes of the Row Component

This example demonstrates the effect of setting the layout attributes (such as the spacing and alignment mode) of the Row component.
```

```TypeScript

```

```TypeScript
### Example 2: Configuring the Reverse Attribute

This example shows the effect after setting the reverse attribute of the Row component, demonstrating how to reverse the arrangement order of child components.
```
