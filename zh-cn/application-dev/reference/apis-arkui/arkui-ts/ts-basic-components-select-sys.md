#  Select (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghaibo0-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

提供下拉选择菜单，让用户在多个选项间选择。

> **说明：**
>
> - 该组件从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本文仅介绍当前模块的系统接口，其他公开接口参见[select](./ts-basic-components-select.md)。

## menuDistortionMode

menuDistortionMode(mode: DistortionMode)

系统材质下，设置下拉菜单的非线性动画模式。未通过该接口设置时，默认为DistortionMode.DISTORTION_AUTO。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| mode | [DistortionMode](./ts-appendix-enums-sys.md#distortionmode) | 是 | 设置系统材质下下拉菜单的非线性动画模式。 |

## menuEdgeLightMode

menuEdgeLightMode(mode: EdgeLightMode)

系统材质下，设置下拉菜单的流光动画模式。未通过该接口设置时，默认为EdgeLightMode.EDGELIGHT_DISABLED。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| mode | [EdgeLightMode](./ts-appendix-enums-sys.md#edgelightmode) | 是 | 设置系统材质下下拉菜单的流光动画模式。 |

