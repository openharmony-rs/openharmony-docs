# Flex

The **Flex** component is a container that uses the flexible box model for layout. It provides an efficient mechanism for arranging and aligning child elements, as well as distributing available space among them. For details, see [Flex Layout](../../../ui/arkts-layout-development-flex-layout.md). > **NOTE** > > - This component is supported since API version 7. Updates will be marked with a superscript to indicate their > earliest API version. > > - The **Flex** component adapts the layout of flex items during rendering. This may affect the performance. > Therefore, you are advised to use Column or Row instead under scenarios where > consistently high performance is required. For best practices, see > [Using Layout Components Properly](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-improve-layout-performance#section12745188175420) > > - If the main axis length of the **Flex** component is unspecified, it follows the size of the parent container by > default. If the **Flex** component contains child components for which > position is set, the > **Flex** component does not follow the size of the parent container. If the main axis length of the **Column** or > **Row** component is unspecified, it follows the size of the child nodes by default. > > - If **Flex**, **Column**, or **Row** containers have no child components and no explicit width or height settings, > their default width or height is **-1**. > > - You can set the main axis length of a **Flex** component to **auto** to make it adapt to the layout of its child > components. This way, the **Flex** component's length is subject to the **constraintSize** attribute and the > maximum and minimum length constraints passed from the parent container, with **constraintSize** taking precedence. > > **Child Components** > > This component can contain child components.

## Flex

```TypeScript
Flex(value?: FlexOptions)
```

Creates a **Flex** component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FlexOptions](arkts-arkui-flexoptions-i.md) | No | Parameters of the child components in the **Flex** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [FlexOptions](arkts-arkui-flexoptions-i.md) | Describes the layout and alignment of child components within the **Flex** component. |
| [FlexSpaceOptions](arkts-arkui-flexspaceoptions-i.md) | Sets the spacing between child components along the main axis or cross axis of the **Flex** component. |

## Examples

```TypeScript
### Example 1: Setting the Child Component Layout Direction

This example demonstrates different layout directions for child components by setting the direction property.


```

```TypeScript
### Example 2: Implementing Single- and Multi-Line Layouts

This example demonstrates single-line and multi-line layouts for child components by setting the wrap property.


```

```TypeScript
### Example 3: Setting Alignment Along the Main Axis

This example demonstrates different alignment effects for child components along the main axis by setting the justifyContent property.


```

```TypeScript
### Example 4: Setting Alignment Along the Cross Axis

This example demonstrates different alignment effects for child components along the cross axis by setting the alignItems property.


```

```TypeScript
### Example 5: Setting Alignment of Multiple Lines

This example demonstrates different alignment effects for multiple lines of content by setting the alignContent property.


```

```TypeScript
### Example 6: Setting the Spacing Between Child Components Along the Main Axis or Cross Axis

This example sets the spacing along the main axis and cross axis for child components in single-line or multi-line arrangement by configuring the space attribute.


```

```TypeScript
### Example 7: Implementing a Flex Component with Adaptive Width

This example shows how the Flex component can automatically adjust to fit the layout of child components when the width is set to auto.
```
