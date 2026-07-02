# @ohos.selectionInput.SelectionPanel (划词面板)

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @no86-->
<!--Designer: @mmwwbb-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

划词面板是用户选中文本后弹出的操作面板，本模块提供划词面板的属性信息和类型。

> **说明：**
>
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块仅支持PC/2in1设备。开发者可通过canIUse('SystemCapability.SelectionInput.Selection')判断当前设备是否支持该功能。

## 导入模块

```ts
import { PanelInfo, PanelType } from '@kit.BasicServicesKit';
```

## PanelInfo

划词面板属性信息，包含面板类型、位置和宽高。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --------- | -------- | -------- | -------- | -------- |
| panelType | [PanelType](#paneltype) | 否 | 否 | 划词面板类型。 |
| x | number | 否 | 否 | 划词面板左上角的x轴坐标，单位为px。取值范围[0, +∞)，传入负数时面板无法正常显示。 |
| y | number | 否 | 否 | 划词面板左上角的y轴坐标，单位为px。取值范围[0, +∞)，传入负数时面板无法正常显示。 |
| width | number | 否 | 否 | 划词面板宽度，单位为px。取值范围(0, +∞)，传入0或负数时面板无法正常显示。 |
| height | number | 否 | 否 | 划词面板高度，单位为px。取值范围(0, +∞)，传入0或负数时面板无法正常显示。 |

## PanelType

划词面板类型枚举。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称          | 值   | 说明         |
| ------------- | ---- | ------------ |
| MENU_PANEL | 1    | 菜单面板为一级面板，显示当前应用程序可以提供的功能，如翻译、搜索等。 |
| MAIN_PANEL | 2    | 主面板为二级面板，当用户点击菜单面板中的功能按钮时弹出，展示具体的翻译或搜索结果等内容。 |
