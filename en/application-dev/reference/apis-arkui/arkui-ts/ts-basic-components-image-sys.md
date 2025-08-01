# Image (System API)

The **Image** component is usually used to display images in applications.

> **NOTE**
>
> This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [Image](ts-basic-components-image.md).

## Attributes

### analyzerConfig<sup>11+</sup>

analyzerConfig(config: ImageAnalyzerConfig)

Sets the AI image analysis types, including subject recognition and character recognition. By default, all types are supported. The types cannot be dynamically modified.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description        |
| ------ | --------------------------------------------- | ---- | ------------ |
| config | [ImageAnalyzerConfig](ts-image-common.md#imageanalyzerconfig) | Yes  | AI image analysis types.|

### edgeAntialiasing<sup>11+</sup>

edgeAntialiasing(value: number)

Sets antialiasing for the image. This attribute applies only to SVG images. The value range is $(0.333, 1.333]$, with precision limited to 3 decimal places.

This attribute can be used to optimize jagged edges in SVG images on devices with PPI lower than 200, but it may compromise the performance. Exercise caution when using this attribute.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                               |
| ------ | ------ | ---- | ----------------------------------- |
| value  | number | Yes  | Antialiasing strength of the image.<br>Default value: **0.0**.|

### pointLight<sup>11+</sup>

pointLight(value: PointLightStyle)

Sets the point light style.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description        |
| ------ | ------------------------------------------------------------ | ---- | ------------ |
| value  | [PointLightStyle](ts-universal-attributes-point-light-style-sys.md#pointlightstyle) | Yes  | Point light style.|

### enhancedImageQuality<sup>12+</sup>

enhancedImageQuality(imageQuality: ResolutionQuality)

Sets the image resolution for decoding the image.

This attribute does not support non-decoded image types such as SVG, [PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md), and [DrawableDescriptor](../js-apis-arkui-drawableDescriptor.md#drawabledescriptor).

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                   | Mandatory| Description                            |
| ------ | --------------------------------------- | ---- | -------------------------------- |
| imageQuality | [ResolutionQuality](#resolutionquality12) | Yes  | Image resolution used for decoding.|

## ResolutionQuality<sup>12+</sup>

Enumerates the image resolutions used for decoding the image.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Description                     |
| ------ | --------------------------  |
| Low   | Low resolution, with moderate decoding time.  |
| Medium | Medium resolution, with moderate decoding time. |
| High   | High resolution, with long decoding time.   |
