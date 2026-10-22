# Video (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @qianpinyi-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=814c7cb9af37d443e12a84b71f28815df508c584 translatedAt=2026-08-28T01:38:41.405Z pushedAt=2026-09-01T06:27:07.411Z -->

The **Video** component is used to play a video and control its playback. It supports playback, pause, progress control, speed playback, and full-screen switching.

> **NOTE**
>
> This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only the system APIs of this module. For details about other public APIs, see [Video](ts-media-components-video.md).

## Attributes

### surfaceBackgroundColor<sup>15+</sup>

surfaceBackgroundColor(color: ColorMetrics)

Sets the background color of the **surfaceNode** (the node that renders the video image) in the **Video** component.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name|       Type   | Mandatory|           Description               |
| ------ | ------------ | ---- | ---------------------------- |
| color  | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | Yes | Background color of the **surfaceNode** in the **Video** component. Only black and transparent colors are supported. Other colors are set to black by default.<br>Default value: **Color.Black** |