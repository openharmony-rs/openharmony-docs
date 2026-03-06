# Interfaces (Others) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> In the following API examples, you must first use [getUIContext()](arkts-apis-window-Window.md#getuicontext10) in **@ohos.window** to obtain a **UIContext** instance, and then call the APIs using the obtained instance. Alternatively, you can obtain a **UIContext** instance through the built-in method [getUIContext()](arkui-ts/ts-custom-component-api.md#getuicontext) of the custom component. In this document, the **UIContext** instance is represented by **uiContext**.
> 
> This document describes only system APIs provided by the module. For details about other public APIs, see [Interfaces (Others)](arkts-apis-uicontext-i.md).

## BackgroundLuminanceSamplingConfigs<sup>23+</sup>

Sets the background luminance sampling parameters.

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| **Name**     | **Type**| **Read-Only** | **Optional**| **Description**                   |
| --------- | ---- | ----- | ---- | -----------------------|
| samplingInterval  | number | No| Yes| Color sampling interval, in milliseconds. The minimum value is 180 ms.<br> Default value: **500**  |
| brightThreshold     | number | No| Yes| Light color brightness threshold. The value must be an integer in the range of [0, 255]. The dark color brightness threshold must be less than the light color brightness threshold.<br> Default value: **220**|
| darkThreshold     | number | No| Yes| Dark color brightness threshold. The value must be an integer in the range of [0, 255]. The dark color brightness threshold must be less than the light color brightness threshold.<br> Default value: **150**|
| region     | [Edges](./js-apis-arkui-graphics.md#edgest12)\<[LengthMetrics](./js-apis-arkui-graphics.md#lengthmetrics12)\> | No| Yes| Sample area offset relative to the component, calculated from the component's upper left corner as the reference point.<br> The component's own area is used by default.|
