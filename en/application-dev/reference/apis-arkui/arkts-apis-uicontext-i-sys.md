# Interfaces (Others) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=d08606d031c19ca91bcb797bc358ec3a21ddc632 translatedAt=2026-10-29T09:07:15.300Z pushedAt=2026-10-30T02:17:46.877Z nl=1 -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> For the following APIs, you must first call [getUIContext()](arkts-apis-window-Window.md#getuicontext10) in **ohos.window** or the built-in method [getUIContext()](arkui-ts/ts-custom-component-api.md#getuicontext) of a custom component to obtain a UIContext instance, and then call the corresponding method through this instance. In this document, the UIContext object is represented by uiContext.
> 
> This page contains only the system APIs of this module. For other public APIs, see [Interfaces (Others)](arkts-apis-uicontext-i.md).

## BackgroundLuminanceSamplingConfigs<sup>23+</sup>

Defines the background luminance sampling parameter configurations. Background luminance sampling periodically samples colors from the background area of a component and determines whether the background is light or dark based on the luminance threshold, so as to support scenarios such as adaptive light/dark style of components.

**Model constraint**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type| Read-Only | Optional| Description                   |
| --------- | ---- | ----- | ---- | -----------------------|
| samplingInterval  | number | No | Yes | Color sampling interval, in milliseconds. Value range: ≥ 180 ms. If a value less than 180 ms is passed in, it is automatically corrected to 180 ms. Set a smaller value (for example, 180-300 ms) when more frequent background color sampling responses are needed, and set a larger value (for example, 500-1000 ms) to conserve system resources.<br> Default value: 500 ms |
| brightThreshold   | number | No | Yes | Light brightness threshold. The value is an integer in the range [0, 255]. The set light brightness threshold must be greater than the dark brightness threshold; otherwise, an exception is thrown. Customize this value when the sensitivity of light determination needs to be adjusted. A setting lower than the default value **220** makes light determination more lenient, and a setting higher than the default value makes light determination stricter.<br> Default value: **220** |
| darkThreshold     | number | No | Yes | Dark brightness threshold. The value is an integer in the range [0, 255]. The set dark brightness threshold must be less than the light brightness threshold. Customize this value when the sensitivity of dark determination needs to be adjusted. A setting higher than the default value **150** makes dark determination more lenient, and a setting lower than the default value makes dark determination stricter.<br> Default value: **150** |
| region     | [Edges](js-apis-arkui-graphics.md#edgest12)\<[LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12)\> | No | Yes | Offset of the sampling area relative to the component, calculated based on the upper left corner of the component. It is recommended to set the sampling area within the visible range to avoid inaccurate sampling results caused by excessive offset.<br> By default, the sampling area is the same as the set component region (that is, when no offset is set, the sampling area equals the component's own area). |
