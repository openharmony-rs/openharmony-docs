# DataPanel

The **DataPanel** component is used to display proportions in a chart.

> **NOTE** > > - This component supports WithTheme since API version 26.0.0

## Child Components

Not supported

## DataPanel

```TypeScript
DataPanel(options: DataPanelOptions)
```

Creates a data panel component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [DataPanelOptions](arkts-arkui-datapaneloptions-i.md) | Yes | Parameters of the data panel. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ColorStop](arkts-arkui-colorstop-i.md) | Describes the gradient color stop. |
| [DataPanelConfiguration](arkts-arkui-datapanelconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |
| [DataPanelOptions](arkts-arkui-datapaneloptions-i.md) | Defines data panel configuration options. |
| [DataPanelShadowOptions](arkts-arkui-datapanelshadowoptions-i.md) | Inherits from [MultiShadowOptions](arkts-arkui-multishadowoptions-i.md) and has all properties of **MultiShadowOptions**. |

### Enums

| Name | Description |
| --- | --- |
| [DataPanelType](arkts-arkui-datapaneltype-e.md) | Enumerates data panel types. |

## Examples

```TypeScript
### Example 1: Setting Data Panel Types

This example shows how to set the data panel type using the type attribute of [DataPanelOptions](arkts-arkui-datapaneloptions-i.md).


```

```TypeScript
### Example 2: Setting Gradient Colors and Shadows

This example demonstrates how to set gradient colors and shadows using the [valueColors](arkts-arkui-datapanel-comp-attribute.md#valuecolors) and [trackShadow](#trackshadow10) for [LinearGradient](#lineargradient10).


```

```TypeScript
### Example 3: Disabling Animations and Shadows

This example demonstrates how to disable the rotation and shadow effects for the data proportion chart using the [closeEffect](arkts-arkui-datapanel-comp-attribute.md#closeeffect) API.


```

```TypeScript
### Example 4: Setting the Custom Content Area

This example shows how to customize the content area of the data panel using the [contentModifier](#contentmodifier12) API.
```
