# @ohos.promptAction

创建并显示即时反馈、对话框和操作菜单。

> **说明：**

> - 本模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-app-ability-uiability.md)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在
创建组件实例后使用。
>
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见
> [UIContext](arkts-arkui-uicontext.md)说明。建议<!--Del-->在除
> [ServiceExtensionAbility](../../../../application-models/serviceextensionability-sys.md)等无UI界面的场景外，均<!--DelEnd-->使用
> UIContext中的弹窗方法。

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [promptAction](arkts-arkui-promptaction-n.md) | 创建并显示即时反馈、对话框和操作菜单。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 本模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-app-ability-uiability.md)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在<br/>    创建组件实例后使用。<br/>&gt;<br/>&gt; - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见<br/>&gt; [UIContext](arkts-arkui-uicontext.md)说明。建议&lt;!--Del--&gt;在除<br/>&gt; [ServiceExtensionAbility](../../../../application-models/serviceextensionability-sys.md)等无UI界面的场景外，均&lt;!--DelEnd--&gt;使用<br/>&gt; UIContext中的弹窗方法。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [LevelOrder](arkts-arkui-levelorder-c.md) | 弹窗层级，可以控制弹窗显示的顺序。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DismissDialogAction](arkts-arkui-dismissdialogaction-i.md) | Dialog关闭的信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ImmersiveMode](arkts-arkui-immersivemode-e.md) | 页面内弹窗蒙层显示区域模式。<br/> |
| [LevelMode](arkts-arkui-levelmode-e.md) | 弹窗显示层级模式。<br/> |

