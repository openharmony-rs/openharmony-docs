# PanelType

输入法面板类型枚举。定义面板的类别，决定面板是软键盘还是状态栏。 PanelType使用建议：   
- 选取原则：输入法应用通常需要创建一个`SOFT_KEYBOARD`面板作为主键盘界面。`STATUS_BAR`面板为可选面板，仅在需要显示输入法状态信息时创建。   
- 规格限制：单个输入法应用仅允许创建一个`SOFT_KEYBOARD`类型和一个`STATUS_BAR`类型的面板。重复创建同类型面板将返回错误。   
- 相关接口间的配合/制约关系：`PanelType`需配合`PanelFlag`使用。当前`PanelFlag`仅用于描述`SOFT_KEYBOARD`类型面板的状态；对`STATUS_BAR`类型面板，`PanelFlag`的设置 不产生实际效果。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## SOFT_KEYBOARD

```TypeScript
SOFT_KEYBOARD = 0
```

软键盘类型。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## STATUS_BAR

```TypeScript
STATUS_BAR
```

状态栏类型。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework
