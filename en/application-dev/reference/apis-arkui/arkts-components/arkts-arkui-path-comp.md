# Path

The **Path** component is used to draw a custom closed shape based on a specified drawing path. > **Note** > > This component supports dynamic constructor parameter updates using the > [updateConstructorParams](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#properties) API of the > [AttributeUpdater](../../../reference/apis-arkui/js-apis-arkui-AttributeUpdater.md) class since API version 20. > > **Child Components** > > None

## Path

```TypeScript
Path(options?: PathOptions)
```

Use new to create Path. Annonymous Object Rectification.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PathOptions](arkts-arkui-pathoptions-i.md) | No | path options |

## Path

```TypeScript
Path(options?: PathOptions)
```

Defines the constructor of Path component

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PathOptions](arkts-arkui-pathoptions-i.md) | No | Options of the path.<br>The **undefined** and **null** values are treated as invalid and will not take effect. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PathOptions](arkts-arkui-pathoptions-i.md) | Describes the options of the path. |

## Examples

```TypeScript
### Example 1: Drawing Rectangles

This example demonstrates how to use commands, fillOpacity, and stroke to draw a closed shape with the specified path, opacity, and stroke color.


```

```TypeScript
### Example 2: Drawing a Path Using Different Parameter Types

This example demonstrates how to draw a path using different length types of the width, height, and commands attributes.


```

```TypeScript
### Example 3: Dynamically Setting Attributes of the Path Component Using attributeModifier

This example shows how to use attributeModifier to dynamically set the commands, fill, fillOpacity, stroke, strokeDashArray, strokeDashOffset, strokeLineCap, strokeLineJoin, strokeMiterLimit, strokeOpacity, strokeWidth, and antiAlias attributes of the Path component.
```
