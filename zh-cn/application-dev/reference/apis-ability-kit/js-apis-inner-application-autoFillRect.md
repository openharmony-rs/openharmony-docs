# AutoFillRect

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

用于自动填充的矩形区域。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**起始版本：** 26.0.0

## AutoFillRect

**原子化服务API（仅ArkTS-Dyn）**：从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称   | 类型                                   | 只读 | 可选 | 说明                                               |
| ------ | -------------------------------------- | ---- | ---- | ------------------------------------------------- |
| left   | ArkTS-Dyn: number<br>ArkTS-Sta: double | 否   | 否   | AutoFill表单或页面节点与页面左边界的距离，单位是px。|
| top    | ArkTS-Dyn: number<br>ArkTS-Sta: double | 否   | 否   | AutoFill表单或页面节点与页面上边界的距离，单位是px。|
| height | ArkTS-Dyn: number<br>ArkTS-Sta: double | 否   | 否   | AutoFill表单或页面节点的高度，单位是px。            |
| width  | ArkTS-Dyn: number<br>ArkTS-Sta: double | 否   | 否   | AutoFill表单或页面节点的宽度，单位是px。            |
