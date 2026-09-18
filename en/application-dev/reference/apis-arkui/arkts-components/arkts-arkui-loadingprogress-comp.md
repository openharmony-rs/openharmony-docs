# LoadingProgress

The **LoadingProgress** component is used to create a loading progress animation.

The loading progress animation stops when the component is invisible. The component's visibility is determined by the value of **ratios** in the [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) event callback: If the value is greater than 0, the component is visible.

> **NOTE** > > - This component supports WithTheme since API version 26.0.0.

## Child Components

Not supported

## LoadingProgress

```TypeScript
LoadingProgress()
```

Creates a loading progress component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [LoadingProgressConfiguration](arkts-arkui-loadingprogressconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |

### Enums

| Name | Description |
| --- | --- |
| [LoadingProgressStyle](arkts-arkui-loadingprogressstyle-e.md) | Enumerates style types of **LoadingProgress**. This API is not recommended for use. |

## Examples

```TypeScript
### Example 1: Setting the Color of the Loading Progress Animation

This example demonstrates how to set the color of the loading progress bar using the [color](#color) API.


```

```TypeScript
### Example 2: Setting the Custom Content Area

This example demonstrates how to customize the content area using the [contentModifier](#contentmodifier12) API, and how to toggle the display of the custom content based on the [enableLoading](#enableloading10) attribute of [LoadingProgressConfiguration](arkts-arkui-loadingprogressconfiguration-i.md).
```
