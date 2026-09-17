# Progress

The **Progress** component represents a progress indicator that displays the progress of content loading or an operation.

## Child Components

Not supported

## Progress

```TypeScript
Progress(options: ProgressOptions<Type>)
```

Creates a progress indicator.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ProgressOptions](arkts-arkui-progressoptions-i.md)&lt;[Type](../arkts-apis/arkts-arkui-arkui-statemanagement-type-d.md)&gt; | Yes | Options of the progress indicator, which vary by progress indicator type. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [CapsuleStyleOptions](arkts-arkui-capsulestyleoptions-i.md) | Capsule style options. |
| [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md) | Provides common style configuration options for the progress indicator. |
| [EclipseStyleOptions](arkts-arkui-eclipsestyleoptions-i.md) | Options of the eclipse style. The eclipse style visualizes the progress in a way similar to the moon waxing from new to full. |
| [LinearStyleOptions](arkts-arkui-linearstyleoptions-i.md) | Linear style options. |
| [ProgressConfiguration](arkts-arkui-progressconfiguration-i.md) | Provides progress indicator configuration. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |
| [ProgressOptions](arkts-arkui-progressoptions-i.md) | Defines progress bar options. |
| [ProgressStyleMap](arkts-arkui-progressstylemap-i.md) | Defines the mapping between progress indicators and styles. |
| [ProgressStyleOptions](arkts-arkui-progressstyleoptions-i.md) | Defines the progress bar style options. |
| [RingStyleOptions](arkts-arkui-ringstyleoptions-i.md) | Options of the ring style without scales. |
| [ScaleRingStyleOptions](arkts-arkui-scaleringstyleoptions-i.md) | Options of the ring style with scales. |
| [ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md) | Defines the scan effect options. |

### Enums

| Name | Description |
| --- | --- |
| [ProgressStatus](arkts-arkui-progressstatus-e.md) | Current state of the progress indicator. |
| [ProgressStyle](arkts-arkui-progressstyle-e.md) | Enumerates progress indicator styles. |
| [ProgressType](arkts-arkui-progresstype-e.md) | Enumerates progress indicator types. |

## Examples

```TypeScript
### Example 1: Setting Progress Indicator Types

This example demonstrates how to set the progress indicator type using the input parameter type of [ProgressOptions](arkts-arkui-progressoptions-i.md).


```

```TypeScript
### Example 2: Setting Ring Progress Indicator Attributes

This example demonstrates how to set attributes of a ring progress indicator using the strokeWidth and shadow properties in the [style](#style8) API.


```

```TypeScript
### Example 3: Setting the Animation for the Ring Progress Indicator

This example demonstrates how to enable or disable animations for a ring progress indicator using the status and enableScanEffect properties in the [style](#style8) API.


```

```TypeScript
### Example 4: Setting Capsule Progress Indicator Attributes

This example demonstrates how to set attributes for a capsule progress indicator using properties such as borderColor, borderWidth, content, font, fontColor, enableScanEffect, and showDefaultPercentage in the [style](#style8) API.


```

```TypeScript
### Example 5: Setting the Smooth Effect

This example demonstrates how to enable or disable the smooth effect for the progress animation using the enableSmoothEffect property in the [style](#style8) API.


```

```TypeScript
### Example 6: Setting the Custom Content Area

This example implements a custom progress indicator using the [contentModifier](#contentmodifier12) API. This progress indicator displays a star shape with a total progress value of 3, and the current value can be incremented or decremented through buttons. The achieved progress is filled with a custom color.


```

```TypeScript
### Example 7: Securing Sensitive Information

This example illustrates how to secure sensitive information using the [privacySensitive](#privacysensitive12) attribute. Note that the display requires widget framework support.


```

```TypeScript
### Example 8: Setting Capsule Progress Indicator Border Radius

This example demonstrates how to set the border radius of the capsule progress indicator using the input parameter borderRadius of [CapsuleStyleOptions](arkts-arkui-capsulestyleoptions-i.md).

The borderRadius attribute is supported since API version 18.


```

```TypeScript
### Example 9: Setting Attributes of Linear and Capsule Progress Indicators

This example demonstrates how to implement the gradient color of the linear progress indicator and capsule progress indicator using LinearGradient (available since API version 23) of the [color](#color) attribute.
```
