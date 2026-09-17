# PanelInfo

划词面板属性信息，包含面板类型、位置和宽高。开发者通过panelType指定面板类型（菜单面板或主面板），通过x、y设定面板左上角坐标，通过width、height设定面板尺寸，各项属性共同定义面板的呈现形态。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

## 导入模块

```TypeScript
import { PanelInfo, PanelType } from '@kit.BasicServicesKit';
```

## height

```TypeScript
height: number
```

划词面板高度，单位为px。取值范围(0, +∞)，传入0或负数时面板无法正常创建。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

## panelType

```TypeScript
panelType: PanelType
```

划词面板类型枚举，有两种面板可供选择，详见[PanelType](arkts-basicservices-selectioninput-selectionpanel-paneltype-e.md)。

**类型：** [PanelType](arkts-basicservices-selectioninput-selectionpanel-paneltype-e.md)

**默认值：** MENU_PANEL

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

## width

```TypeScript
width: number
```

划词面板宽度，单位为px。取值范围(0, +∞)，传入0或负数时面板无法正常创建。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

## x

```TypeScript
x: number
```

划词面板左上角的x轴坐标，单位为px。以主屏幕左上角为原点，x轴正方向向右。取值范围[0, +∞)，传入负数时面板无法正常创建。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

## y

```TypeScript
y: number
```

划词面板左上角的y轴坐标，单位为px。以主屏幕左上角为原点，y轴正方向向下。取值范围[0, +∞)，传入负数时面板无法正常创建。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection
