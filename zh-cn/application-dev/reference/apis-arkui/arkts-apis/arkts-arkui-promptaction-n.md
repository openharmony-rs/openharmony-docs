# promptAction

创建并显示即时反馈、对话框和操作菜单。

> **说明：**

> - 本模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-app-ability-uiability.md)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在
创建组件实例后使用。
>
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见
> [UIContext](arkts-arkui-uicontext.md)说明。建议<!--Del-->在除
> [ServiceExtensionAbility](../../../../application-models/serviceextensionability-sys.md)等无UI界面的场景外，均<!--DelEnd-->使用
> UIContext中的弹窗方法。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [showToast](arkts-arkui-showtoast-f.md#showtoast-1) | Creates and displays a toast.创建并显示即时反馈。 |
| [openToast](arkts-arkui-opentoast-f.md#opentoast-1) | 显示即时反馈并通过Promise返回其id。@link @ohos.inputMethodEngine:inputMethodEngine.InputMethodAbility.createPanel(ctx: BaseContext, info: PanelInfo)}&gt; 。&gt;&gt; - 直接使用openToast可能导致[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用UIContext中的getPromptAction方法获&gt; 取到PromptAction对象，再通过该对象调用&gt; [openToast](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opentoast18)实现。 |
| [closeToast](arkts-arkui-closetoast-f.md#closetoast-1) | 关闭即时反馈。 |
| [showDialog](arkts-arkui-showdialog-f.md#showdialog-1) | 创建并显示对话框，对话框响应结果使用callback异步回调返回。 |
| [showDialog](arkts-arkui-showdialog-f.md#showdialog-2) | 创建并显示对话框，对话框通过Promise返回结果。 |
| [openCustomDialog](arkts-arkui-opencustomdialog-f.md#opencustomdialog-1) | 打开自定义弹窗。通过Promise返回结果。&lt;!--Del--&gt;不支持在ServiceExtension中使用。&lt;!--DelEnd--&gt;弹窗宽度在设备竖屏时默认为 所在窗口宽度 - 左右margin（16vp，设备为2in1时为40vp），最大默认宽度为400vp。 |
| [closeCustomDialog](arkts-arkui-closecustomdialog-f.md#closecustomdialog-1) | 关闭自定义弹窗。 |
| [showActionMenu](arkts-arkui-showactionmenu-f.md#showactionmenu-1) | 创建并显示操作菜单，菜单响应结果使用callback异步回调返回。 |
| [showActionMenu](arkts-arkui-showactionmenu-f.md#showactionmenu-2) | 创建并显示操作菜单，菜单响应后通过Promise返回结果。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [CommonController](arkts-arkui-commoncontroller-c.md) | 公共控制器，可以控制promptAction相关组件。 |
| [DialogController](arkts-arkui-dialogcontroller-c.md) | 自定义弹窗控制器，继承自[CommonController](#commoncontroller18)。DialogController可作为UIContext弹出自定义弹窗的成员变量，具体用法可看[openCustomDialogWithController](arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18)和[presentCustomDialog](arkts-apis-uicontext-promptaction.md#presentcustomdialog18)示例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ShowToastOptions](arkts-arkui-showtoastoptions-i.md) | Toast的选项。 |
| [Button](arkts-arkui-button-i.md) | 菜单中的菜单项按钮。 |
| [ShowDialogSuccessResponse](arkts-arkui-showdialogsuccessresponse-i.md) | 对话框的响应结果。 |
| [ShowDialogOptions](arkts-arkui-showdialogoptions-i.md) | 对话框的选项。 |
| [BaseDialogOptions](arkts-arkui-basedialogoptions-i.md) | 弹窗的选项。 |
| [CustomDialogOptions](arkts-arkui-customdialogoptions-i.md) | 自定义弹窗的内容，继承自[BaseDialogOptions](#basedialogoptions11)。 |
| [DialogOptions](arkts-arkui-dialogoptions-i.md) | 自定义弹窗的内容，继承自[BaseDialogOptions](#basedialogoptions11)。 |
| [ActionMenuSuccessResponse](arkts-arkui-actionmenusuccessresponse-i.md) | 操作菜单的响应结果。 |
| [ActionMenuOptions](arkts-arkui-actionmenuoptions-i.md) | 操作菜单的选项。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ShowDialogOptions](arkts-arkui-showdialogoptions-i-sys.md) | 对话框的选项。 |
| [BaseDialogOptions](arkts-arkui-basedialogoptions-i-sys.md) | 弹窗的选项。 |
| [ActionMenuOptions](arkts-arkui-actionmenuoptions-i-sys.md) | 操作菜单的选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ToastShowMode](arkts-arkui-toastshowmode-e.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。 |
| [CommonState](arkts-arkui-commonstate-e.md) | 自定义弹窗的状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ToastShowMode](arkts-arkui-toastshowmode-e-sys.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [DialogOptionsCornerRadius](arkts-arkui-dialogoptionscornerradius-t.md) | 表示弹窗背板的圆角半径允许的数据字段类型。 |
| [DialogOptionsBorderWidth](arkts-arkui-dialogoptionsborderwidth-t.md) | 表示弹窗背板的边框宽度允许的数据字段类型。 |
| [DialogOptionsBorderColor](arkts-arkui-dialogoptionsbordercolor-t.md) | 表示弹窗背板的边框颜色允许的数据字段类型。 |
| [DialogOptionsBorderStyle](arkts-arkui-dialogoptionsborderstyle-t.md) | 表示弹窗背板的边框样式允许的数据字段类型。 |
| [DialogOptionsShadow](arkts-arkui-dialogoptionsshadow-t.md) | 表示弹窗背板的阴影允许的数据字段类型。 |

