# Menu Control (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=b9c1325011d9c59753edc8719ffca6256df6a642 translatedAt=2026-09-01T12:44:42.150Z -->

A context menu – a vertical list of items – can be bound to a component and displayed by long-pressing, clicking, or right-clicking the component.

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [Menu Control](./ts-universal-attributes-menu.md).

## ContextMenuOptions<sup>10+</sup>

Configures the visual presentation options of the system menu, including the nonlinear animation mode (distortion effect) and the streaming animation mode of the menu under the new material, to improve the interactive experience and visual quality of menu display.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

<!--Table: 20%; 20%; 10%; 10%; 40%-->
| Name                 | Type                                                        | Read-Only| Optional| Description                                                        |
| --------------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| distortionMode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | No | Yes | Sets the nonlinear animation mode of the menu under system materials.<br />**Default value:** DistortionMode.DISTORTION_AUTO <br/>**Since:** 26.0.0 <br />**System API:** This is a system API.|
| edgeLightMode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode)| No | Yes | Sets the edge light animation mode of the menu under system materials.<br />**Default value:** EdgeLightMode.EDGELIGHT_DISABLED <br/>**Since:** 26.0.0 <br />**System API:** This is a system API.|
