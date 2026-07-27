# Image (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

The **Image** component is usually used to display images in applications.

> **NOTE**
>
> This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [Image](ts-basic-components-image.md).

## Attributes

### analyzerConfig<sup>11+</sup>

analyzerConfig(config: ImageAnalyzerConfig)

Sets the AI image analysis types, including subject recognition and character recognition. By default, all types are supported. The types cannot be dynamically modified. Typical applications include album subject recognition, document/character extraction, and content moderation assistance.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description        |
| ------ | --------------------------------------------- | ---- | ------------ |
| config | [ImageAnalyzerConfig](ts-image-common.md#imageanalyzerconfig12) | Yes  | AI image analysis types.|

### edgeAntialiasing<sup>11+</sup>

edgeAntialiasing(value: number)

Sets an anti-aliasing effect on the edges of an SVG image. This attribute takes effect only for SVG images. The value must be greater than 0.333 and less than or equal to 1.333, with precision limited to 3 decimal places. A larger value indicates a stronger anti-aliasing effect.

This attribute can be used to optimize jagged edges in SVG images on devices with PPI lower than 200, but it may compromise the performance. Exercise caution when using this attribute.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                               |
| ------ | ------ | ---- | ----------------------------------- |
| value  | number | Yes  | Anti-aliasing effect on the edges of an SVG image. The value must be greater than 0.333 and less than or equal to 1.333. A larger value indicates a stronger anti-aliasing effect.<br>Default value: **0.0**, indicating that the anti-aliasing effect is disabled. (**0.0** is a reserved value for the disabled state and is not within the valid value range.)|

### pointLight<sup>11+</sup>

pointLight(value: PointLightStyle)

Sets a point light style to add 3D lighting and high gloss effects to an image. This attribute is commonly used in scenarios such as 3D cards and floating icons.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description        |
| ------ | ------------------------------------------------------------ | ---- | ------------ |
| value  | [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) | Yes  | Point light style.|

### enhancedImageQuality<sup>12+</sup>

enhancedImageQuality(imageQuality: ResolutionQuality)

Sets an enhanced image decoding resolution option. A higher image quality level indicates longer decoding time and higher memory usage. Select a level based on display requirements: **Low** indicates fast decoding speed and low memory usage, suitable for low-memory scenarios such as list thumbnails. **Medium** indicates a balance between image quality and performance. **High** indicates the best image quality but longer decoding time and higher memory usage, suitable for full-screen high-definition display.

This attribute does not support non-decoded image types such as SVG, [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md), and [DrawableDescriptor](../js-apis-arkui-drawableDescriptor.md#drawabledescriptor).

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                   | Mandatory| Description                            |
| ------ | --------------------------------------- | ---- | -------------------------------- |
| imageQuality | [ResolutionQuality](#resolutionquality12) | Yes  | Image resolution used for decoding.<br>Default value: **ResolutionQuality.Low**. That is, low-resolution decoding is used by default to reduce memory usage and improve decoding performance.|

## ResolutionQuality<sup>12+</sup>

type ResolutionQuality = import('../api/@ohos.multimedia.image').default.ResolutionQuality

Sets a resolution quality level.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type    | Description      |
| ------ | ---------- |
| import('../api/@ohos.multimedia.image').default.[ResolutionQuality](../../apis-image-kit/js-apis-image-sys.md#resolutionquality12) | Resolution quality level.|
