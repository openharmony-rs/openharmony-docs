# @ohos.arkui.advanced.Dialog

## 导入模块

```TypeScript
import { AlertDialog, SelectDialog, ButtonOptions, PopoverOptions, TipsDialog, PopoverDialog, LoadingDialog, CustomContentDialog, ConfirmDialog } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md) |  |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AlertDialog](arkts-arkui-arkui-advanced-dialog-alertdialog-s.md) | 操作确认类弹出框，触发一个将产生严重后果的不可逆操作时，如删除、重置、取消编辑、停止等。 |
| [ConfirmDialog](arkts-arkui-arkui-advanced-dialog-confirmdialog-s.md) | 信息确认类弹出框，操作未正确执行（如网络错误、电池电量过低），或未正确操作时（如指纹录入），反馈的错误或提示信息。 |
| [CustomContentDialog](arkts-arkui-arkui-advanced-dialog-customcontentdialog-s.md) | 自定义内容区弹出框，同时支持定义操作区按钮样式。 |
| [LoadingDialog](arkts-arkui-arkui-advanced-dialog-loadingdialog-s.md) | 进度加载类弹出框，用于显示操作执行中的提示信息。 |
| [PopoverDialog](arkts-arkui-arkui-advanced-dialog-popoverdialog-s.md) | 弹出框是一种模态窗口，用于临时展示用户需关注的信息或待处理的操作，同时保持当前上下文环境。用户必须完成交互才能退出该模式。 @internal/component/ets/common}和[通用事件](../../apis-arkui/arkts-components/arkts-arkui-common-attribute.md)，编译工具链会额外生  > 成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Dialog本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议Dialog设置通用属性和通用事件。 |
| [SelectDialog](arkts-arkui-arkui-advanced-dialog-selectdialog-s.md) | 选择类弹出框，弹框中以列表或网格的形式提供可选的内容。 |
| [TipsDialog](arkts-arkui-arkui-advanced-dialog-tipsdialog-s.md) | 提示弹出框，即为带图形确认弹出框，必要时可通过图形化方式展现确认弹出框。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [PopoverOptions](arkts-arkui-arkui-advanced-dialog-popoveroptions-i.md) | 跟手弹出框参数，用于设置弹出框内容、位置属性等。  继承自[CustomPopupOptions](../arkts-components/arkts-arkui-custompopupoptions-i.md)。 |

