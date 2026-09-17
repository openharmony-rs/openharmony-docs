# ImageFrameInfo

Image frame information set.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Playback duration of each image frame, in milliseconds.

Default value: **0**

Negative numbers are not supported. Setting negative values will cause the image to stay in the current frame for a long time, affecting normal playback.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: number | string
```

Image height. When the value is a string, it can represent a numeric value with or without units, for example, **"2"** or **"2px"**.

Default value: **0**

Unit: vp

**Type:** number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left?: number | string
```

Horizontal coordinate of the image relative to the upper left corner of the component. When the value is a string, it can represent a numeric value with or without units, for example, **"2"** or **"2px"**.

Default value: **0**

Unit: vp

**Type:** number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: string | Resource | PixelMap
```

Image path. The image format can be .jpg,jpeg,svg,png,bmp,webp,ico, or .heif. The Resource type is supported since API version 9, and the [PixelMap](../../../reference/apis-arkui/arkui-ts/ts-image-common.md#pixelmap) type is supported since API version 12.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [PixelMap](arkts-arkui-pixelmap-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top?: number | string
```

Vertical coordinate of the image relative to the upper left corner of the component. When the value is a string, it can represent a numeric value with or without units, for example, **"2"** or **"2px"**.

Default value: **0**

Unit: vp

**Type:** number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: number | string
```

Image width. When the value is a string, it can represent a numeric value with or without units, for example, **"2"** or **"2px"**.

Default value: **0**

Unit: vp

**Type:** number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
