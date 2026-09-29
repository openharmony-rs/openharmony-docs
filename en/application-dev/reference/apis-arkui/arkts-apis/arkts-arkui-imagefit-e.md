# ImageFit

```TypeScript
declare enum ImageFit
```

Sets the image filling effect.

**Since:** 7

<!--Device-unnamed-declare enum ImageFit--><!--Device-unnamed-declare enum ImageFit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Contain

```TypeScript
Contain
```

The image or video is scaled with its aspect ratio retained to fit entirely within the display boundaries, with horizontal center alignment.

![ImageFit-Examples01](../../../reference/apis-arkui/arkui-ts/figures/image_fit_contain.png)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ImageFit-Contain--><!--Device-ImageFit-Contain-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Cover

```TypeScript
Cover
```

The image or video is scaled while maintaining the aspect ratio so that both sides are greater than or equal to the display boundaries, aligned horizontally in the center.

![ImageFit-Examples02](../../../reference/apis-arkui/arkui-ts/figures/image_fit_cover.png)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ImageFit-Cover--><!--Device-ImageFit-Cover-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto
```

The image or video is scaled appropriately based on its own dimensions and the component's size to fill the view while maintaining the aspect ratio, aligned horizontally in the center.

![ImageFit-Examples03](../../../reference/apis-arkui/arkui-ts/figures/image_fit_auto.png)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ImageFit-Auto--><!--Device-ImageFit-Auto-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Fill

```TypeScript
Fill
```

The image or video is scaled without maintaining the aspect ratio to fill the display boundaries, with horizontal center alignment.

![ImageFit-Examples04](../../../reference/apis-arkui/arkui-ts/figures/image_fit_fill.png)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ImageFit-Fill--><!--Device-ImageFit-Fill-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ScaleDown

```TypeScript
ScaleDown
```

The image or video is displayed while maintaining the aspect ratio, only scaling down or keeping the original size, aligned horizontally in the center.

![ImageFit-Examples05](../../../reference/apis-arkui/arkui-ts/figures/image_fit_scaleDown.png)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ImageFit-ScaleDown--><!--Device-ImageFit-ScaleDown-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## None

```TypeScript
None
```

The image is displayed at its original size, aligned horizontally in the center.

![ImageFit-Examples06](../../../reference/apis-arkui/arkui-ts/figures/image_fit_none.png)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ImageFit-None--><!--Device-ImageFit-None-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TOP_START

```TypeScript
TOP_START = 7
```

The image or video is displayed at the top start position of the component in the original size.

![ImageFit-Examples07](../../../reference/apis-arkui/arkui-ts/figures/image_fit_top_start.png)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ImageFit-TOP_START = 7--><!--Device-ImageFit-TOP_START = 7-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TOP

```TypeScript
TOP = 8
```

The image or video is displayed at the top center position of the component in the original size.

![ImageFit-Examples08](../../../reference/apis-arkui/arkui-ts/figures/image_fit_top.png)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ImageFit-TOP = 8--><!--Device-ImageFit-TOP = 8-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TOP_END

```TypeScript
TOP_END = 9
```

The image or video is displayed at the top end position of the component in the original size.

![ImageFit-Examples09](../../../reference/apis-arkui/arkui-ts/figures/image_fit_top_end.png)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ImageFit-TOP_END = 9--><!--Device-ImageFit-TOP_END = 9-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## START

```TypeScript
START = 10
```

The image or video is displayed at the start position (vertically centered) of the component in the original size.

![ImageFit-Examples10](../../../reference/apis-arkui/arkui-ts/figures/image_fit_start.png)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ImageFit-START = 10--><!--Device-ImageFit-START = 10-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CENTER

```TypeScript
CENTER = 11
```

The image or video is displayed at the center position of the component in the original size.

![ImageFit-Examples11](../../../reference/apis-arkui/arkui-ts/figures/image_fit_center.png)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ImageFit-CENTER = 11--><!--Device-ImageFit-CENTER = 11-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END = 12
```

The image or video is displayed at the end position (vertically centered) of the component in the original size.

![ImageFit-Examples12](../../../reference/apis-arkui/arkui-ts/figures/image_fit_end.png)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ImageFit-END = 12--><!--Device-ImageFit-END = 12-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_START

```TypeScript
BOTTOM_START = 13
```

The image or video is displayed at the bottom start position of the component in the original size.

![ImageFit-Examples13](../../../reference/apis-arkui/arkui-ts/figures/image_fit_bottom_start.png)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ImageFit-BOTTOM_START = 13--><!--Device-ImageFit-BOTTOM_START = 13-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM

```TypeScript
BOTTOM = 14
```

The image or video is displayed at the bottom center position of the component in the original size.

![ImageFit-Examples14](../../../reference/apis-arkui/arkui-ts/figures/image_fit_bottom.png)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ImageFit-BOTTOM = 14--><!--Device-ImageFit-BOTTOM = 14-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BOTTOM_END

```TypeScript
BOTTOM_END = 15
```

The image or video is displayed at the bottom end position of the component in the original size.

![ImageFit-Examples15](../../../reference/apis-arkui/arkui-ts/figures/image_fit_bottom_end.png)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ImageFit-BOTTOM_END = 15--><!--Device-ImageFit-BOTTOM_END = 15-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MATRIX

```TypeScript
MATRIX = 16
```

The image, with the use of [imageMatrix](../arkts-components/arkts-arkui-image-comp-attribute.md#imagematrix), is displayed in the specified position of the **Image component**, keeping its original size. SVG images are not supported.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ImageFit-MATRIX = 16--><!--Device-ImageFit-MATRIX = 16-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
