# Select (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghaibo0-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ecf5d58a25055daa53a34747272770e0f3c1f57a translatedAt=2026-09-03T11:53:00.289Z pushedAt=2026-09-16T01:38:59.409Z -->

The **Select** component provides a drop-down menu that allows users to select among multiple options. It is suitable for scenarios such as form input and preference settings, and can standardize selection interactions, improve operation efficiency, and reduce the misoperation rate.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [select](./ts-basic-components-select.md).

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
| mode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | Yes | Distortion animation mode of the drop-down menu with the system material. |

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

