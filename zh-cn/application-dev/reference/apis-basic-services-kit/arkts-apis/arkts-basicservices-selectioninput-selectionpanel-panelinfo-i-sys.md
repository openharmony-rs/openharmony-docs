# PanelInfo(划词面板)（系统接口）

划词面板属性信息，包含面板类型、位置和宽高。开发者通过panelType指定面板类型（菜单面板或主面板），通过x、y设定面板左上角坐标，通过width、height设定面板尺寸，各项属性共同定义面板的呈现形态。

**起始版本：** 24

<!--Device-unnamed-export interface PanelInfo--><!--Device-unnamed-export interface PanelInfo-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { PanelInfo, PanelType } from '@kit.BasicServicesKit';
```

## height

```TypeScript
height: int
```

划词面板高度，单位为px。取值范围(0, +∞)，传入0或负数时面板无法正常创建。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanelInfo-height: int--><!--Device-PanelInfo-height: int-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## panelType

```TypeScript
panelType: PanelType
```

划词面板类型枚举，有两种面板可供选择，详见[PanelType](arkts-basicservices-selectioninput-selectionpanel-paneltype-e-sys.md)。

**类型：** [PanelType](arkts-basicservices-selectioninput-selectionpanel-paneltype-e-sys.md)

**默认值：** MENU_PANEL

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanelInfo-panelType: PanelType--><!--Device-PanelInfo-panelType: PanelType-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## width

```TypeScript
width: int
```

划词面板宽度，单位为px。取值范围(0, +∞)，传入0或负数时面板无法正常创建。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanelInfo-width: int--><!--Device-PanelInfo-width: int-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## x

```TypeScript
x: int
```

划词面板左上角的x轴坐标，单位为px。以主屏幕左上角为原点，x轴正方向向右。取值范围[0, +∞)，传入负数时面板无法正常创建。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanelInfo-x: int--><!--Device-PanelInfo-x: int-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## y

```TypeScript
y: int
```

划词面板左上角的y轴坐标，单位为px。以主屏幕左上角为原点，y轴正方向向下。取值范围[0, +∞)，传入负数时面板无法正常创建。

**类型：** int

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanelInfo-y: int--><!--Device-PanelInfo-y: int-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

