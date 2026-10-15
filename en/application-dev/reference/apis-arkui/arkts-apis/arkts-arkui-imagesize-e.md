# ImageSize

```TypeScript
declare enum ImageSize
```

Sets the width and height effect of an image.

**Since:** 7

<!--Device-unnamed-declare enum ImageSize--><!--Device-unnamed-declare enum ImageSize-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto
```

The original image aspect ratio is retained.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ImageSize-Auto--><!--Device-ImageSize-Auto-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Contain

```TypeScript
Contain
```

The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ImageSize-Contain--><!--Device-ImageSize-Contain-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Cover

```TypeScript
Cover
```

The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ImageSize-Cover--><!--Device-ImageSize-Cover-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FILL

```TypeScript
FILL = 3
```

The image is scaled to fill the display area, and its aspect ratio is not retained.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ImageSize-FILL = 3--><!--Device-ImageSize-FILL = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
