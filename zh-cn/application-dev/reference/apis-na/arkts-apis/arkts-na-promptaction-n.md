# promptAction

创建并显示即时反馈、对话框和操作菜单。 > **说明：** > > - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。 > > - 本模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md#UIAbility)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在创建组件实例后使用。 > > - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见 > [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)说明。建议&lt;!--Del--&gt;在除 > [ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)等无UI界面的场景外，均&lt;!--DelEnd--&gt;使用 > UIContext中的弹窗方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace promptAction--><!--Device-unnamed-declare namespace promptAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [openToast](arkts-na-promptaction-opentoast-f.md#openToast) | 显示即时反馈并通过Promise返回其id。 |
| [closeToast](arkts-na-promptaction-closetoast-f.md#closeToast) | 关闭即时反馈。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [CommonController](arkts-na-promptaction-commoncontroller-c.md) | 公共控制器，可以控制promptAction相关组件。 |
| [DialogController](arkts-na-promptaction-dialogcontroller-c.md) | 自定义弹窗控制器，继承自CommonController。 DialogController可作为UIContext弹出自定义弹窗的成员变量，具体用法可看 [openCustomDialogWithController](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#openCustomDialogWithController) 和[presentCustomDialog](../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#presentCustomDialog)示例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ShowToastOptions](arkts-na-promptaction-showtoastoptions-i.md) | Toast的选项。 |
| [Button](arkts-na-promptaction-button-i.md) | 菜单中的菜单项按钮。 |
| [ShowDialogSuccessResponse](arkts-na-promptaction-showdialogsuccessresponse-i.md) | 对话框的响应结果。 |
| [ShowDialogOptions](arkts-na-promptaction-showdialogoptions-i.md) | 对话框的选项。 |
| [BaseDialogOptions](arkts-na-promptaction-basedialogoptions-i.md) | 弹窗的选项。 |
| [CustomDialogOptions](arkts-na-promptaction-customdialogoptions-i.md) | 自定义弹窗的内容，继承自BaseDialogOptions。 |
| [DialogOptions](arkts-na-promptaction-dialogoptions-i.md) | 自定义弹窗的内容，继承自BaseDialogOptions。 |
| [ActionMenuSuccessResponse](arkts-na-promptaction-actionmenusuccessresponse-i.md) | 操作菜单的响应结果。 |
| [ActionMenuOptions](arkts-na-promptaction-actionmenuoptions-i.md) | 操作菜单的选项。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ShowDialogOptions](arkts-na-promptaction-showdialogoptions-i-sys.md) | 对话框的选项。 |
| [BaseDialogOptions](arkts-na-promptaction-basedialogoptions-i-sys.md) | 弹窗的选项。 |
| [ActionMenuOptions](arkts-na-promptaction-actionmenuoptions-i-sys.md) | 操作菜单的选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ToastShowMode](arkts-na-promptaction-toastshowmode-e.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。 |
| [CommonState](arkts-na-promptaction-commonstate-e.md) | 自定义弹窗的状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ToastShowMode](arkts-na-promptaction-toastshowmode-e-sys.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [PromptActionSingleButton](arkts-na-promptaction-promptactionsinglebutton-t.md) | 菜单中的菜单项按钮，仅支持1个按钮。 |
| [PromptActionDoubleButtons](arkts-na-promptaction-promptactiondoublebuttons-t.md) | 菜单中的菜单项按钮，仅支持2个按钮。 |
| [PromptActionTripleButtons](arkts-na-promptaction-promptactiontriplebuttons-t.md) | 菜单中的菜单项按钮，仅支持3个按钮。 |
| [PromptActionQuadrupleButtons](arkts-na-promptaction-promptactionquadruplebuttons-t.md) | 菜单中的菜单项按钮，仅支持4个按钮。 |
| [PromptActionQuintupleButtons](arkts-na-promptaction-promptactionquintuplebuttons-t.md) | 菜单中的菜单项按钮，仅支持5个按钮。 |
| [PromptActionSextupleButtons](arkts-na-promptaction-promptactionsextuplebuttons-t.md) | 菜单中的菜单项按钮，仅支持6个按钮。 |
| [DialogOptionsCornerRadius](arkts-na-promptaction-dialogoptionscornerradius-t.md) | 表示弹窗背板的圆角半径允许的数据字段类型。 |
| [DialogOptionsBorderWidth](arkts-na-promptaction-dialogoptionsborderwidth-t.md) | 表示弹窗背板的边框宽度允许的数据字段类型。 |
| [DialogOptionsBorderColor](arkts-na-promptaction-dialogoptionsbordercolor-t.md) | 表示弹窗背板的边框颜色允许的数据字段类型。 |
| [DialogOptionsBorderStyle](arkts-na-promptaction-dialogoptionsborderstyle-t.md) | 表示弹窗背板的边框样式允许的数据字段类型。 |
| [DialogOptionsShadow](arkts-na-promptaction-dialogoptionsshadow-t.md) | 表示弹窗背板的阴影允许的数据字段类型。 |

