# @ohos.arkui.advanced.DialogV2

## 导入模块

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md) | 弹出框操作区按钮。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AlertDialogV2](arkts-arkui-arkui-advanced-dialogv2-alertdialogv2-s.md) | 操作确认类弹出框。当触发一个将产生严重后果的不可逆操作时，如删除、重置、取消编辑、停止等，会触发该类弹出框提示。 |
| [ConfirmDialogV2](arkts-arkui-arkui-advanced-dialogv2-confirmdialogv2-s.md) | 信息确认类弹出框，用于反馈错误或提示信息。当操作未正确执行（如网络错误、电池电量过低）或用户操作不当时（如指纹录入），弹出此类对话框进行提示。 |
| [CustomContentDialogV2](arkts-arkui-arkui-advanced-dialogv2-customcontentdialogv2-s.md) | 自定义内容区弹出框，同时支持定义操作区按钮样式。适用于需要展示复杂或自定义内容的场景，如用户协议确认、表单输入等。 |
| [LoadingDialogV2](arkts-arkui-arkui-advanced-dialogv2-loadingdialogv2-s.md) | 进度加载类弹出框，操作正在执行时的提示信息。适用于耗时操作的场景，如数据加载、文件上传等，用于告知用户当前正在处理中。 |
| [PopoverDialogV2](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2-s.md) | 跟手弹出框，基于目标组件位置弹出，上述的TipsDialogV2、SelectDialogV2、ConfirmDialogV2、AlertDialogV2、 LoadingDialogV2、CustomContentDialogV2都可作为弹出框内容。适用于需要跟随目标组件位置显示的场景，如工具提示、操作引导等。 |
| [SelectDialogV2](arkts-arkui-arkui-advanced-dialogv2-selectdialogv2-s.md) | 选择类弹出框，弹框中以列表或网格的形式提供可选的内容。适用于需要用户从多个选项中选择一个的场景，如选择语言、选择地区等。 |
| [TipsDialogV2](arkts-arkui-arkui-advanced-dialogv2-tipsdialogv2-s.md) | 提示弹出框，即为带图形确认弹出框，必要时可通过图形化方式展现确认弹出框。适用于需要图形化方式展示的重要提示场景，如应用卸载确认等。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AdvancedDialogV2ButtonOptions](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2buttonoptions-i.md) | 用于初始化AdvancedDialogV2Button对象。 |
| [PopoverDialogV2Options](arkts-arkui-arkui-advanced-dialogv2-popoverdialogv2options-i.md) | 跟手弹出框参数，用于设置弹出框内容、位置属性等。 继承自CustomPopupOptions。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AdvancedDialogV2ButtonAction](arkts-arkui-advanceddialogv2buttonaction-t.md) | 弹出框操作区按钮的点击事件类型。 |
| [AdvancedDialogV2OnCheckedChange](arkts-arkui-advanceddialogv2oncheckedchange-t.md) | 选择框选中状态改变事件。 |
| [PopoverDialogV2OnVisibleChange](arkts-arkui-popoverdialogv2onvisiblechange-t.md) | 跟手弹出框显示状态改变事件。 |

