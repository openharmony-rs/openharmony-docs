# Interfaces (Others) (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=bbc6406dab71d9f75b4831661ca1204731bcdd0c translatedAt=2026-08-05T03:09:35.306Z pushedAt=2026-08-05T06:52:30.558Z -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs in later versions are marked with a superscript to indicate their initial API version.
>
> For the following APIs, you must first call [getUIContext()](arkts-apis-window-Window.md#getuicontext10) in ohos.window or the built-in method [getUIContext()](arkui-ts/ts-custom-component-api.md#getuicontext) of a custom component to obtain a UIContext instance, and then call the corresponding method through this instance. In this document, the UIContext object is represented by uiContext.
>
> This page contains only the system APIs of this module. For other public APIs, see [Interfaces (Others)](arkts-apis-uicontext-i.md).

## BackgroundLuminanceSamplingConfigs<sup>23+</sup>

Defines the background luminance sampling parameter configuration.

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model constraint**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type| Read-Only | Optional| Description                   |
| --------- | ---- | ----- | ---- | -----------------------|
| samplingInterval  | number | No  | Yes  | Sampling interval, in milliseconds. Value range: ≥180 ms. Set a smaller value (for example, 180–300 ms) when more frequent background color sampling responses are needed, and set a larger value (for example, 500–1000 ms) to conserve system resources.<br> Default value: 500 ms   |
| brightThreshold     | number | No  | Yes  | Light brightness threshold. The value is an integer in the range [0, 255]. The light brightness threshold must be greater than the dark brightness threshold. When you need to adjust the sensitivity of light‑color detection, you can customize this value. A lower value makes the light‑color detection more lenient, while a higher value makes it more stringent.<br> Default value: 220 |
| darkThreshold     | number | No  | Yes  | Dark brightness threshold. The value is an integer in the range [0, 255]. The dark brightness threshold must be less than the light brightness threshold. When you need to adjust the sensitivity of dark‑color detection, you can customize this value. A higher value makes the dark‑color detection more lenient, while a lower value makes it more stringent.<br> Default value: 150 |
| region     | [Edges](js-apis-arkui-graphics.md#edgest12)\<[LengthMetrics](js-apis-arkui-graphics.md#lengthmetrics12)\> | No  | Yes  | Offset of the sampling area relative to the component, calculated based on the upper left corner of the component. It is recommended to set the sampling area within the visible range to avoid inaccurate sampling results caused by excessive offset.<br> The component's own region is used by default. |