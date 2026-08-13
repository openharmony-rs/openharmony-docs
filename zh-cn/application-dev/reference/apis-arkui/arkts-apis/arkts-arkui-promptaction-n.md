# promptAction

创建并显示即时反馈、对话框和操作菜单，适用于系统通知、交互确认、菜单选择等场景。 > **说明：** > - 本模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md#UIAbility)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在 创建组件实例后使用。 > > - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见 > [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)说明。建议&lt;!--Del--&gt;在除 > [ServiceExtensionAbility](../../../application-models/serviceextensionability-sys.md)等无UI界面的场景外，均&lt;!--DelEnd--&gt;使用 > UIContext中的弹窗方法。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-unnamed-declare namespace promptAction--><!--Device-unnamed-declare namespace promptAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [showToast](arkts-arkui-promptaction-showtoast-f.md#showToast) | Creates and displays a toast. 创建并显示即时反馈。 |
| [openToast](arkts-arkui-promptaction-opentoast-f.md#openToast) | 显示即时反馈并通过Promise返回其id。 |
| [closeToast](arkts-arkui-promptaction-closetoast-f.md#closeToast) | 关闭即时反馈。 |
| [showDialog](arkts-arkui-promptaction-showdialog-f.md#showDialog) | 创建并显示对话框，对话框响应结果使用callback异步回调返回。 |
| [showDialog](arkts-arkui-promptaction-showdialog-f.md#showDialog) | 创建并显示对话框，对话框通过Promise返回结果。 |
| [openCustomDialog](arkts-arkui-promptaction-opencustomdialog-f.md#openCustomDialog) | 打开自定义弹窗。通过Promise返回结果。 &lt;!--Del--&gt;不支持在ServiceExtension中使用。&lt;!--DelEnd--&gt; 弹窗宽度在设备竖屏时默认为 所在窗口宽度 - 左右margin（16vp，设备为2in1时为40vp），最大默认宽度为400vp。 |
| [closeCustomDialog](arkts-arkui-promptaction-closecustomdialog-f.md#closeCustomDialog) | 关闭自定义弹窗。 |
| [showActionMenu](arkts-arkui-promptaction-showactionmenu-f.md#showActionMenu) | 创建并显示操作菜单，菜单响应结果使用callback异步回调返回。 |
| [showActionMenu](arkts-arkui-promptaction-showactionmenu-f.md#showActionMenu) | 创建并显示操作菜单，菜单响应后通过Promise返回结果。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [CommonController](arkts-arkui-promptaction-commoncontroller-c.md) | 公共控制器，可以控制promptAction相关组件。 |
| [DialogController](arkts-arkui-promptaction-dialogcontroller-c.md) | 自定义弹窗控制器，继承自[CommonController](../../apis-na/arkts-apis/arkts-na-promptaction-commoncontroller-c.md#CommonController)。 DialogController可作为UIContext弹出自定义弹窗的成员变量，具体用法可看 [openCustomDialogWithController](arkts-arkui-arkui-uicontext-promptaction-c.md#openCustomDialogWithController)和 [presentCustomDialog](arkts-arkui-arkui-uicontext-promptaction-c.md#presentCustomDialog)示例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | Toast的选项。 |
| [Button](arkts-arkui-promptaction-button-i.md) | 菜单中的菜单项按钮。 |
| [ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md) | 对话框的响应结果。 |
| [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | 对话框的选项。 |
| [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | 弹窗的选项。 |
| [CustomDialogOptions](arkts-arkui-promptaction-customdialogoptions-i.md) | 自定义弹窗的内容，继承自[BaseDialogOptions](../../apis-na/arkts-apis/arkts-na-promptaction-basedialogoptions-i.md#BaseDialogOptions)。 |
| [DialogOptions](arkts-arkui-promptaction-dialogoptions-i.md) | 自定义弹窗的内容，继承自[BaseDialogOptions](../../apis-na/arkts-apis/arkts-na-promptaction-basedialogoptions-i.md#BaseDialogOptions)，用于配置自定义弹窗的显示参数和行为。 |
| [ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md) | 操作菜单的响应结果。 |
| [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | 操作菜单的选项。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i-sys.md) | 对话框的选项。 |
| [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i-sys.md) | 弹窗的选项。 |
| [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i-sys.md) | 操作菜单的选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ToastShowMode](arkts-arkui-promptaction-toastshowmode-e.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。 |
| [CommonState](arkts-arkui-promptaction-commonstate-e.md) | 自定义弹窗的状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ToastShowMode](arkts-arkui-promptaction-toastshowmode-e-sys.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [DialogOptionsCornerRadius](arkts-arkui-promptaction-dialogoptionscornerradius-t.md) | 表示弹窗背板的圆角半径允许的数据字段类型。 |
| [DialogOptionsBorderWidth](arkts-arkui-promptaction-dialogoptionsborderwidth-t.md) | 表示弹窗背板的边框宽度允许的数据字段类型。 |
| [DialogOptionsBorderColor](arkts-arkui-promptaction-dialogoptionsbordercolor-t.md) | 表示弹窗背板的边框颜色允许的数据字段类型。 |
| [DialogOptionsBorderStyle](arkts-arkui-promptaction-dialogoptionsborderstyle-t.md) | 表示弹窗背板的边框样式允许的数据字段类型。 |
| [DialogOptionsShadow](arkts-arkui-promptaction-dialogoptionsshadow-t.md) | 表示弹窗背板的阴影允许的数据字段类型。 |

