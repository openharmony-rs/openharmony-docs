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
| [showToast](arkts-arkui-promptaction-showtoast-f.md#showToast-1) | Creates and displays a toast.<br/><br/>创建并显示即时反馈。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 从API version 9开始支持，从API version 18开始废弃，建议使用[showToast](arkts-apis-uicontext-promptaction.md#showtoast)替代。<br/>     showToast需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>     [getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，<br/>     然后通过该对象进行调用。且直接使用showToast可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>     [getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的<br/>     [PromptAction](arkts-apis-uicontext-promptaction.md)对象。<br/>&gt;<br/>&gt; - Toast样式单一，不支持内容的自定义，具体支持能力请参考[ShowToastOptions](#showtoastoptions)提供的接口。<br/> |
| [openToast](arkts-arkui-promptaction-opentoast-f.md#openToast-1) | 显示即时反馈并通过Promise返回其id。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 不支持在输入法类型窗口中使用子窗（showMode设置为TOP_MOST或者SYSTEM_TOP_MOST）的openToast，详情见输入法框架的约束与限制说明<br/>&gt; [createPanel](@ohos.inputMethodEngine:inputMethodEngine.InputMethodAbility.createPanel(ctx: BaseContext, info: PanelInfo))<br/>&gt; 。<br/>&gt;<br/>&gt; - 直接使用openToast可能导致[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用UIContext中的getPromptAction方法获<br/>&gt; 取到PromptAction对象，再通过该对象调用<br/>&gt; [openToast](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opentoast18)实现。<br/> |
| [closeToast](arkts-arkui-promptaction-closetoast-f.md#closeToast-1) | 关闭即时反馈。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 直接使用closeToast可能导致[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用<br/>  UIContext中的getPromptAction方法获取<br/>&gt; 到PromptAction对象，再通过该对象调用<br/>&gt; [closeToast](../../../../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#closetoast18)实现。<br/> |
| [showDialog](arkts-arkui-promptaction-showdialog-f.md#showDialog-1) | 创建并显示对话框，对话框响应结果使用callback异步回调返回。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 从API version 9开始支持，从API version 18开始废弃，建议使用[showDialog](arkts-apis-uicontext-promptaction.md#showdialog)替代。<br/>showDialog需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，<br/>然后通过该对象进行调用。且直接使用showDialog可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象。<br/> |
| [showDialog](arkts-arkui-promptaction-showdialog-f.md#showDialog-2) | 创建并显示对话框，对话框通过Promise返回结果。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 从API version 9开始支持，从API version 18开始废弃，建议使用[showDialog](arkts-apis-uicontext-promptaction.md#showdialog-1)替代。<br/>showDialog需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取[PromptAction](arkts-apis-uicontext-promptaction.md)对象，<br/>然后通过该对象进行调用。且直接使用showDialog可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象。<br/> |
| [openCustomDialog](arkts-arkui-promptaction-opencustomdialog-f.md#openCustomDialog-1) | 打开自定义弹窗。通过Promise返回结果。<br/><br/>&lt;!--Del--&gt;不支持在ServiceExtension中使用。&lt;!--DelEnd--&gt;<br/><br/>弹窗宽度在设备竖屏时默认为 所在窗口宽度 - 左右margin（16vp，设备为2in1时为40vp），最大默认宽度为400vp。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 从API version 11开始支持，从API version 18开始废弃，建议使用[openCustomDialog](arkts-apis-uicontext-promptaction.md#opencustomdialog12-1)替代。<br/>openCustomDialog需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象，然后通过该对象进行调用。且直接使用openCustomDialog可能导致<br/>[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 12开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象。<br/> |
| [closeCustomDialog](arkts-arkui-promptaction-closecustomdialog-f.md#closeCustomDialog-1) | 关闭自定义弹窗。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 从API version 11开始支持，从API version 18开始废弃，建议使用[closeCustomDialog](arkts-apis-uicontext-promptaction.md#closecustomdialog12-1)替代。<br/>closeCustomDialog需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象，然后通过该对象进行调用。且直接使用closeCustomDialog可能导致<br/>[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 12开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象。<br/> |
| [showActionMenu](arkts-arkui-promptaction-showactionmenu-f.md#showActionMenu-1) | 创建并显示操作菜单，菜单响应结果使用callback异步回调返回。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 从API version 9开始支持，从API version 18开始废弃，建议使用[showActionMenu](arkts-apis-uicontext-promptaction.md#showactionmenu11)替代。<br/>showActionMenu需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象，然后通过该对象进行调用。且直接使用showActionMenu可能导致<br/>[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 11开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象。<br/> |
| [showActionMenu](arkts-arkui-promptaction-showactionmenu-f.md#showActionMenu-2) | 创建并显示操作菜单，菜单响应后通过Promise返回结果。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 从API version 9开始支持，从API version 18开始废弃，建议使用[showActionMenu](arkts-apis-uicontext-promptaction.md#showactionmenu)替代。<br/>showActionMenu需先通过[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象，然后通过该对象进行调用。且直接使用showActionMenu可能导致<br/>[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题。<br/>&gt;<br/>&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的<br/>[getPromptAction](arkts-apis-uicontext-uicontext.md#getpromptaction)方法获取当前UI上下文关联的<br/>[PromptAction](arkts-apis-uicontext-promptaction.md)对象。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [CommonController](arkts-arkui-promptaction-commoncontroller-c.md) | 公共控制器，可以控制promptAction相关组件。<br/> |
| [DialogController](arkts-arkui-promptaction-dialogcontroller-c.md) | 自定义弹窗控制器，继承自[CommonController](#commoncontroller18)。<br/><br/>DialogController可作为UIContext弹出自定义弹窗的成员变量，具体用法可看<br/>[openCustomDialogWithController](arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18)和<br/>[presentCustomDialog](arkts-apis-uicontext-promptaction.md#presentcustomdialog18)示例。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ShowToastOptions](arkts-arkui-promptaction-showtoastoptions-i.md) | Toast的选项。 |
| [Button](arkts-arkui-promptaction-button-i.md) | 菜单中的菜单项按钮。<br/> |
| [ShowDialogSuccessResponse](arkts-arkui-promptaction-showdialogsuccessresponse-i.md) | 对话框的响应结果。<br/> |
| [ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i.md) | 对话框的选项。<br/> |
| <!--DelRow-->[ShowDialogOptions](arkts-arkui-promptaction-showdialogoptions-i-sys.md) | 对话框的选项。<br/> |
| [BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i.md) | 弹窗的选项。<br/> |
| <!--DelRow-->[BaseDialogOptions](arkts-arkui-promptaction-basedialogoptions-i-sys.md) | 弹窗的选项。<br/> |
| [CustomDialogOptions](arkts-arkui-promptaction-customdialogoptions-i.md) | 自定义弹窗的内容，继承自[BaseDialogOptions](#basedialogoptions11)。<br/> |
| [DialogOptions](arkts-arkui-promptaction-dialogoptions-i.md) | 自定义弹窗的内容，继承自[BaseDialogOptions](#basedialogoptions11)。<br/> |
| [ActionMenuSuccessResponse](arkts-arkui-promptaction-actionmenusuccessresponse-i.md) | 操作菜单的响应结果。<br/> |
| [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md) | 操作菜单的选项。<br/> |
| <!--DelRow-->[ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i-sys.md) | 操作菜单的选项。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ToastShowMode](arkts-arkui-promptaction-toastshowmode-e.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。<br/> |
| <!--DelRow-->[ToastShowMode](arkts-arkui-promptaction-toastshowmode-e-sys.md) | 设置Toast的显示模式，默认显示在应用内，支持显示在子窗。<br/> |
| [CommonState](arkts-arkui-promptaction-commonstate-e.md) | 自定义弹窗的状态。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DialogOptionsCornerRadius](arkts-arkui-promptaction-dialogoptionscornerradius-t.md) | 表示弹窗背板的圆角半径允许的数据字段类型。<br/> |
| [DialogOptionsBorderWidth](arkts-arkui-promptaction-dialogoptionsborderwidth-t.md) | 表示弹窗背板的边框宽度允许的数据字段类型。<br/> |
| [DialogOptionsBorderColor](arkts-arkui-promptaction-dialogoptionsbordercolor-t.md) | 表示弹窗背板的边框颜色允许的数据字段类型。<br/> |
| [DialogOptionsBorderStyle](arkts-arkui-promptaction-dialogoptionsborderstyle-t.md) | 表示弹窗背板的边框样式允许的数据字段类型。<br/> |
| [DialogOptionsShadow](arkts-arkui-promptaction-dialogoptionsshadow-t.md) | 表示弹窗背板的阴影允许的数据字段类型。<br/> |

