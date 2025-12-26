# @ohos.selectionInput.SelectionPanel (划词面板)

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @no86-->
<!--Designer: @mmwwbb-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

本模块提供划词面板的属性信息和类型。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { PanelInfo, PanelType } from '@ohos.selectionInput.SelectionPanel';
```

## PanelInfo

划词面板属性信息。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模式下使用。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --------- | -------- | -------- | -------- | -------- |
| panelType | [PanelType](#paneltype) | 否 | 否 | 划词面板类型。 |
| x     | ArkTS-Dyn:number<br>ArkTS-Sta:int | 否 | 否 | 划词面板左上角的x轴坐标，单位为px。|
| y     | ArkTS-Dyn:number<br>ArkTS-Sta:int | 否 | 否 | 划词面板左上角的y轴坐标，单位为px。|
| width | ArkTS-Dyn:number<br>ArkTS-Sta:int | 否 | 否 | 划词面板宽度，单位为px。          |
| height| ArkTS-Dyn:number<br>ArkTS-Sta:int | 否 | 否 | 划词面板高度，单位为px。          |

## PanelType

划词面板类型枚举。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模式下使用。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

| 名称          | 值   | 说明         |
| ------------- | ---- | ------------ |
| MENU_PANEL | 1    | 菜单面板类型。 |
| MAIN_PANEL | 2    | 主面板类型。 |
