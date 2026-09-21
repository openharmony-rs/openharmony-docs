# ImageSpan properties/events

```TypeScript
declare class ImageSpanAttribute extends BaseSpan<ImageSpanAttribute>
```

The attributes inherit from [BaseSpan](arkts-arkui-span-comp-basespan-c.md). Among the universal attributes, [size](arkts-arkui-common-comp.md#common), [background](arkts-arkui-common-comp.md#common), and [border](arkts-arkui-common-comp.md#common) are supported.

Among all the universal events, only the [click event](arkts-arkui-common-comp.md#common) is supported. The following events are also supported.

@extends CommonMethod&lt;ImageSpanAttribute&gt; [since 10 - 10] @extends BaseSpan&lt;ImageSpanAttribute&gt; [since 11]

**Inheritance/Implementation:** ImageSpanAttribute extends BaseSpan<ImageSpanAttribute>

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alt

```TypeScript
alt(value: PixelMap)
```

Sets the placeholder image displayed during image loading.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | Placeholder image displayed during image loading. The [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) type is supported.<br>Default value: **null** |

## colorFilter

```TypeScript
colorFilter(filter: ColorFilter | DrawingColorFilter)
```

Sets the color filter for the image.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [ColorFilter](../arkts-apis/arkts-arkui-colorfilter-c.md) &#124; [DrawingColorFilter](arkts-arkui-image-comp-drawingcolorfilter-t.md) | Yes | 1. Color filter of the image. The input parameter is a 4 x 5 RGBA transformation matrix.<br>The first row of the matrix represents a vector value of R (red), the second row represents a vector value of G (green), the third row represents a vector value of B (blue), and the fourth row represents a vector value of A (alpha). The four rows represent different RGBA vector values.<br>If the matrix contains entries of 1 on the diagonal and entries of 0 in other places, the original color of the image is retained.<br> **Calculation rule:**<br>If the input filter matrix is as follows:<br>! [image-matrix-1](../../../reference/apis-arkui/arkui-ts/figures/image_matrix_1.png)<br>And the pixel point is [R, G, B, A] with color values in the [0, 255] range,<br>Then the color after filtering is [R', G', B', A'].<br>![image-matrix-2](../../../reference/apis-arkui/arkui-ts/figures/image_matrix_2.png)<br>2. The ColorFilter type of **@ohos.graphics.drawing** can be used as the input parameter.<br>**NOTE:** <br>The DrawingColorfilter type can be used in atomic services. The SVG image source takes effect only for the stroke attribute. |

## objectFit

```TypeScript
objectFit(value: ImageFit)
```

Sets the image scale type.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md) | Yes | Image scale type.<br>Default value: **ImageFit.Cover** |

## onComplete

```TypeScript
onComplete(callback: ImageCompleteCallback)
```

Triggered when the image is successfully loaded or decoded. The size of the loaded image is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ImageCompleteCallback](arkts-arkui-imagespan-comp-imagecompletecallback-t.md) | Yes | Callback triggered when the image is successfully loaded or decoded. |

## onError

```TypeScript
onError(callback: ImageErrorCallback)
```

Triggered when an error occurs during image loading.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ImageErrorCallback](arkts-arkui-image-comp-imageerrorcallback-t.md) | Yes | Callback triggered when an error occurs during image loading. |

## resizable

```TypeScript
resizable(value: ResizableOptions)
```

Sets the resizable image options. Resizing is effective for drag previews and placeholder images.

When a valid [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md) is set, the **objectRepeat**, **antialiased**, and **orientation** attributes do not take effect.

When the sum of the values of **top** and **bottom** is greater than the source image height, or the sum of the values of **left** and **right** is greater than the source image width, the [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md) attribute does not take effect.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md) or the image format is SVG.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md) | Yes | Resizable image options. |

## supportSvg2

```TypeScript
supportSvg2(enable: Optional<boolean>)
```

Sets whether to enable [enhanced SVG tag parsing](../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md). When this feature is enabled, SVG image rendering behavior changes accordingly.

After the **ImageSpan** component is created, the value of this attribute cannot be dynamically changed.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable [enhanced SVG tag parsing capabilities](../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md). <br>**true**: Enable enhanced SVG parsing. **false**: Use original SVG parsing.<br>Default value: **false**. |

## verticalAlign

```TypeScript
verticalAlign(value: ImageSpanAlignment)
```

Sets the alignment mode of the image relative to the line height.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageSpanAlignment](../arkts-apis/arkts-arkui-imagespanalignment-e.md) | Yes | Alignment mode of the image relative to the line height.<br>Default value: **ImageSpanAlignment.BOTTOM** |
