# ImageFrameInfo

```TypeScript
interface ImageFrameInfo
```

Image frame information set.

**Since:** 7

<!--Device-unnamed-interface ImageFrameInfo--><!--Device-unnamed-interface ImageFrameInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Playback duration of each image frame, in milliseconds.

Default value: **0**

Negative values are not supported. Setting a negative value causes the image to stay on the current frame for a long time, affecting normal playback.

**Type:** number

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ImageFrameInfo-duration?: number--><!--Device-ImageFrameInfo-duration?: number-End-->

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageFrameInfo-height?: number | string--><!--Device-ImageFrameInfo-height?: number | string-End-->

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageFrameInfo-left?: number | string--><!--Device-ImageFrameInfo-left?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: string | Resource | PixelMap
```

Image path. The image format can be .jpg,jpeg,svg,png,bmp,webp,ico, or .heif. The Resource type is supported since API version 9, and the [PixelMap](../../../reference/apis-arkui/arkui-ts/ts-image-common.md#pixelmap) type is supported since API version 12.

**String format description:**

- Supports loading local image paths and network image addresses. When a relative path is used to reference a local  
image, cross-package or cross-module invocation is not supported. Files in the **resources** directory cannot be accessed through relative paths. You need to use the Resource type (such as **$r** or **$rawfile**) to reference them. For details about how to reference images, see [Loading Image Resources](../../../ui/arkts-graphics-display.md#loading-image-resources).  
- Supports `http` and `https` network image addresses. When using a network image, you must apply for the  
`ohos.permission.INTERNET` permission.  
- Supports strings with the `file://` path prefix. The application sandbox URI is  
`file://&lt;bundleName&gt;/&lt;sandboxPath&gt;`. For the sandbox path, you need to use [fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md) to convert the path into an application sandbox URI, and then pass it for display. At the same time, ensure that the files under the directory package path have read permission.  
- Supports `Base64` strings.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md)

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageFrameInfo-src: string | Resource | PixelMap--><!--Device-ImageFrameInfo-src: string | Resource | PixelMap-End-->

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageFrameInfo-top?: number | string--><!--Device-ImageFrameInfo-top?: number | string-End-->

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-ImageFrameInfo-width?: number | string--><!--Device-ImageFrameInfo-width?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
