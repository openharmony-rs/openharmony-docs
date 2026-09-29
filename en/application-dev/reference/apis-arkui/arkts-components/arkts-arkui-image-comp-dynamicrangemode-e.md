# DynamicRangeMode

```TypeScript
declare enum DynamicRangeMode
```

Describes the dynamic range of the image to be displayed.

**Since:** 12

<!--Device-unnamed-declare enum DynamicRangeMode--><!--Device-unnamed-declare enum DynamicRangeMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## HIGH

```TypeScript
HIGH = 0
```

Unrestricted dynamic range, which allows for the maximum brightening of an image.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DynamicRangeMode-HIGH = 0--><!--Device-DynamicRangeMode-HIGH = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONSTRAINT

```TypeScript
CONSTRAINT = 1
```

Restricted dynamic range, which brightens an image within certain constraints.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DynamicRangeMode-CONSTRAINT = 1--><!--Device-DynamicRangeMode-CONSTRAINT = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 2
```

Standard dynamic range, which does not brighten an image.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DynamicRangeMode-STANDARD = 2--><!--Device-DynamicRangeMode-STANDARD = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
