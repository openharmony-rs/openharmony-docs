#  Select (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghaibo0-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The **Select** component provides a drop-down menu that allows users to select among multiple options.

> **NOTE**
>
> - This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [Select](./ts-basic-components-select.md).

## menuDistortionMode

menuDistortionMode(mode: DistortionMode)

Sets the distortion animation mode for a drop-down menu with the system material. If this API is not used, the default value is **DistortionMode.DISTORTION_AUTO**.

**Since**: 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| mode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | Yes| Distortion mode of the drop-down menu with a system material.|

## menuEdgeLightMode

menuEdgeLightMode(mode: EdgeLightMode)

Sets the edge light mode for a drop-down menu with the system material. If this API is not used, the default value is **EdgeLightMode.EDGELIGHT_DISABLED**.

**Since**: 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| mode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode) | Yes| Edge light mode of the drop-down menu with a system material.|
