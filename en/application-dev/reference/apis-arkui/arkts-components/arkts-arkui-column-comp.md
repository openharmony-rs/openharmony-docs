# Column

The **Column** component lays out child components vertically. > **NOTE** > > If no height or width is set for the **Column** component, the component automatically adapts to the size of its > child components in the main axis and cross axis respectively. > > **Child Components** > > Supported

## Column

```TypeScript
Column(options?: ColumnOptions)
```

Creates a vertical linear layout container. You can set the spacing between child components.

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
| options | [ColumnOptions](arkts-arkui-columnoptions-i.md) | No | Vertical spacing between two adjacent child components. The value can be of the number or string type. |

## Column

```TypeScript
Column(options?: ColumnOptions | ColumnOptionsV2)
```

Creates a vertical linear layout container. You can set the spacing between child components.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ColumnOptions](arkts-arkui-columnoptions-i.md) &#124; [ColumnOptionsV2](arkts-arkui-columnoptionsv2-i.md) | No | Vertical spacing between two adjacent child components. The value can be of the number, string, or Resource type. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ColumnOptions](arkts-arkui-columnoptions-i.md) | Sets the spacing between child components of the **Column** component. |
| [ColumnOptionsV2](arkts-arkui-columnoptionsv2-i.md) | Sets the spacing between child components of the **Column** component. |

### Types

| Name | Description |
| --- | --- |
| [SpaceType](arkts-arkui-spacetype-t.md) | Describes the supported data types for the **space** parameter in the constructors of the **Column** component. The type is a union of the following types. |

## Examples

```TypeScript
### Example 1: Setting the Layout Attributes of the Column Component

This example demonstrates how to set the layout attributes of the Column component, such as the spacing and alignment mode, and its effect.
```

```TypeScript

```

```TypeScript
### Example 2: Configuring the Reverse Attribute

This example demonstrates how to set the reverse attribute of the Column component and its effect.
```
