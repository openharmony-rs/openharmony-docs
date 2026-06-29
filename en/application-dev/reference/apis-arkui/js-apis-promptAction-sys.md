# @ohos.promptAction (Prompt) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **PromptAction** module provides APIs for creating and showing toasts, dialog boxes, and action menus.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.promptAction (Prompt)](js-apis-promptAction.md).

## Modules to Import

```ts
import { promptAction } from '@kit.ArkUI';
```

### ToastShowMode

Enumerates display modes for toasts. By default, the toast is displayed within the application and supports display in sub-windows.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Value  | Description                  |
| -------- | ---- | ---------------------- |
| SYSTEM_TOP_MOST | 2    | The toast is displayed in a window of the TYPE_SYSTEM_TOAST type.|

### BaseDialogOptions<sup>11+</sup>

Defines the options of the dialog box.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name           | Type                                                        | Read-Only| Optional| Description                                                        |
| --------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./arkui-ts/ts-appendix-enums-sys.md#distortionmode) | No| Yes| Non-linear animation mode for a dialog box with the system material.<br>**Default value**: DistortionMode.DISTORTION_AUTO<br>**System API**: This is a system API.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|
| edgeLightMode | [EdgeLightMode](./arkui-ts/ts-appendix-enums-sys.md#edgelightmode) | No| Yes| Flowing light animation mode for a dialog box with the system material.<br>**Default value**: EdgeLightMode.EDGELIGHT_AUTO<br>**System API**: This is a system API.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|

### ActionMenuOptions

Describes the options for showing the action menu.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                         | Type                                                        | Read-Only| Optional| Description                                                        |
| ----------------------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./arkui-ts/ts-appendix-enums-sys.md#distortionmode) | No| Yes| Non-linear animation mode for a dialog box with the system material.<br>**Default value**: DistortionMode.DISTORTION_AUTO<br>**System API**: This is a system API.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|
| edgeLightMode | [EdgeLightMode](./arkui-ts/ts-appendix-enums-sys.md#edgelightmode) | No| Yes| Flowing light animation mode for a dialog box with the system material.<br>**Default value**: EdgeLightMode.EDGELIGHT_AUTO<br>**System API**: This is a system API.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|

### ShowDialogOptions

Describes the options for showing the dialog box.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                             | Type                                                        | Read-Only| Optional| Description                                                        |
| --------------------------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./arkui-ts/ts-appendix-enums-sys.md#distortionmode) | No| Yes| Non-linear animation mode for a dialog box with the system material.<br>**Default value**: DistortionMode.DISTORTION_AUTO<br>**System API**: This is a system API.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|
| edgeLightMode | [EdgeLightMode](./arkui-ts/ts-appendix-enums-sys.md#edgelightmode) | No| Yes| Flowing light animation mode for a dialog box with the system material.<br>**Default value**: EdgeLightMode.EDGELIGHT_AUTO<br>**System API**: This is a system API.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API can be used in atomic services since API version 26.0.0.|

<!--no_check-->