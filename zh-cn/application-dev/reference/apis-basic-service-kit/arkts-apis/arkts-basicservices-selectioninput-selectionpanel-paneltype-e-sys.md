# PanelType（系统接口）

划词面板类型枚举，定义面板的两级架构：菜单面板（一级）和主面板（二级）。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export enum PanelType--><!--Device-unnamed-export enum PanelType-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## MENU_PANEL

```TypeScript
MENU_PANEL = 1
```

菜单面板为一级面板，显示当前应用可以提供的功能，如翻译、搜索等。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanelType-MENU_PANEL = 1--><!--Device-PanelType-MENU_PANEL = 1-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## MAIN_PANEL

```TypeScript
MAIN_PANEL = 2
```

主面板为二级面板，当用户点击菜单面板中的功能按钮时弹出，展示具体的翻译或搜索结果等内容。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanelType-MAIN_PANEL = 2--><!--Device-PanelType-MAIN_PANEL = 2-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

