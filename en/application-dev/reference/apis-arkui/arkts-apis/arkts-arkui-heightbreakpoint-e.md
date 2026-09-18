# HeightBreakpoint

Enumerates the height breakpoint values corresponding to different window aspect ratio thresholds. The values are returned through [getWindowHeightBreakpoint](arkts-arkui-arkui-uicontext-uicontext-c.md#getwindowheightbreakpoint).

The following table lists default aspect ratio breakpoint thresholds for typical devices, serving as a reference for responsive layout design based on window aspect ratios. Device manufacturers may customize these thresholds through product-specific configurations when needed.

**Since:** 13

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## HEIGHT_SM

```TypeScript
HEIGHT_SM = 0
```

The window aspect ratio is less than 0.8.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## HEIGHT_MD

```TypeScript
HEIGHT_MD = 1
```

The window aspect ratio is greater than or equal to 0.8 and less than 1.2.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## HEIGHT_LG

```TypeScript
HEIGHT_LG = 2
```

The window aspect ratio is greater than or equal to 1.2.

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
