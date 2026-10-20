# PanelType

```TypeScript
export enum PanelType
```

输入法面板类型枚举。定义面板的类别，决定面板是软键盘还是状态栏。<br> <br>| 名称 | 值 | 说明 | 使用场景 |

| ------------- | ---- | ------------ | -------- |  
| SOFT_KEYBOARD | 0 | 软键盘类型。 | 适用于需要键盘输入交互的场景，是输入法应用的主要面板类型。大多数输入法应用至少需要创建一个软键盘面板。 |  
| STATUS_BAR | 1 | 状态栏类型。 | 适用于需要在屏幕顶部显示输入法状态信息（如当前输入语言、输入模式等）的场景。通常作为辅助面板与软键盘面板配合使用。 |

<br>PanelType使用建议：<br> <br>- 选取原则：输入法应用通常需要创建一个`SOFT_KEYBOARD`面板作为主键盘界面。`STATUS_BAR`面板为可选面板，仅在需要显示输入法状态信息时创建。<br>- 规格限制：单个输入法应用仅允许创建一个`SOFT_KEYBOARD`类型和一个`STATUS_BAR`类型的面板。重复创建同类型面板将返回错误。<br>- 相关接口间的配合/制约关系：`PanelType`需配合`PanelFlag`使用。当前`PanelFlag`仅用于描述`SOFT_KEYBOARD`类型面板的状态；对`STATUS_BAR`类型面板，`PanelFlag`的设置不产生实际效果。

**起始版本：** 11

<!--Device-unnamed-export enum PanelType--><!--Device-unnamed-export enum PanelType-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## SOFT_KEYBOARD

```TypeScript
SOFT_KEYBOARD = 0
```

软键盘类型。

**起始版本：** 11

<!--Device-PanelType-SOFT_KEYBOARD = 0--><!--Device-PanelType-SOFT_KEYBOARD = 0-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## STATUS_BAR

```TypeScript
STATUS_BAR = 1
```

状态栏类型。

**起始版本：** 11

<!--Device-PanelType-STATUS_BAR = 1--><!--Device-PanelType-STATUS_BAR = 1-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework
