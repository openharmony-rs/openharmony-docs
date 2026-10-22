# Custom Dialog Box (CustomDialog) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

Displays a custom dialog box through the [CustomDialogController](ts-methods-custom-dialog-box.md#customdialogcontroller) class. When using a dialog box component, prioritize a custom dialog box for easier customization of the dialog box style and content.

> **NOTE**
>
> This API is supported since API version 7. Newly added content in later versions will be marked with a superscript to indicate the starting version.
>
> This page covers only the system APIs of this module. For other public APIs, see [Custom Dialog Box (CustomDialog)](ts-methods-custom-dialog-box.md).

## CustomDialogControllerOptions

Defines the style of the custom dialog box.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name                           | Type                                     | Read-Only | Optional | Description                                     |
| ----------------------------- | ---------------------------------------- | ---- | ---------------------------------------- | ---------------------------------------- |
| distortionMode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | No | Yes | Distortion animation mode of the dialog box under system materials.<br/>**Default value:** **DistortionMode.DISTORTION_AUTO** <br/>**System API:** This is a system API.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model.|
| edgeLightMode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode) | No | Yes | Edge light animation mode of the dialog box under system materials.<br/>**Default value:** **EdgeLightMode.EDGELIGHT_AUTO** <br/>**System API:** This is a system API.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can be used only in the stage model. |