# Enums (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

>**NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## IlluminatedType

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Value  | Description                                              |
| ------ | ---- | ------------------------------------------------------ |
| NONE | 0    | The component is not illuminated.|
| BORDER | 1    | The borders of the component can be illuminated.|
| CONTENT | 2    | The content of the component can be illuminated.|
| BORDER_CONTENT | 3    | The borders and content of the component can be illuminated.|
| BLOOM_BORDER | 4    | The borders of the component can be illuminated, with a luminous effect applied to the borders.|
| BLOOM_BORDER_CONTENT | 5    | The borders and content of the component can be illuminated, with a luminous effect applied to the borders.|

## ColorSpace<sup>20+</sup>

Enumerates color space types for specifying color rendering modes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   |  Value  | Description                  |
| ------  | ---- | -------------------- |
| BT2020<sup>24+</sup> | 2 | BT2020 color space with a wider gamut, applicable to high-end display devices.<br>**Model restriction:** This API can be used only in the stage model.<br>**System API**: This is a system API.|

## EdgeLightPosition

Defines the edge light position.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**System API**: This is a system API.

| Name          | Value | Description                        |
| -------------- | --- |---------------------------- |
| TOP_LEFT       | 0   | Edge light at the top-left corner.           |
| TOP_RIGHT      | 1   | Edge light at the top-right corner.           |
| BOTTOM_LEFT    | 2   | Edge light at the bottom-left corner.           |
| BOTTOM_RIGHT   | 3   | Edge light at the bottom-right corner.           |
| TOP            | 4   | Edge light along the top side.             |
| BOTTOM         | 5   | Edge light along the bottom side.             |
| LEFT           | 6   | Edge light along the left side.             |
| RIGHT          | 7   | Edge light along the right side.             |

## DistortionMode

Enumerates distortion modes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description             |
| ------ | --- | --------------- |
| DISTORTION_AUTO | 0 | When a material of the [IMMERSIVE](../arkts-apis-uimaterial.md#immersivematerial) type is applied, the distortion effect activates automatically according to the device's computing power tier. This feature is enabled for devices with high and mid-tier computing performance and remains inactive on low-performance hardware.|
| DISTORTION_ENABLED | 1 | The distortion effect is enabled when a system material is applied.|
| DISTORTION_DISABLED | 2 | The distortion effect is disabled when a system material is applied.|


## EdgeLightMode

Enumerates edge light modes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value| Description             |
| ------ | --- | --------------- |
| EDGELIGHT_AUTO | 0 | When a material of the [IMMERSIVE](../arkts-apis-uimaterial.md#immersivematerial) type is applied, the edge light effect activates automatically according to the device's computing power tier. This feature is enabled for devices with high and mid-tier computing performance and remains inactive on low-performance hardware.|
| EDGELIGHT_ENABLED | 1 | The edge light effect is enabled when a system material is applied.|
| EDGELIGHT_DISABLED | 2 | The edge light effect is disabled when a system material is applied.|
