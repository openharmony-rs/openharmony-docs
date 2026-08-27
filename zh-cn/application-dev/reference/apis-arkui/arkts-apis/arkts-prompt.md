# @ohos.prompt

创建并显示文本提示框、对话框和操作菜单。

> **说明：**
> 
> 从API version 9 开始，该接口不再维护，推荐使用新接口[@ohos.promptAction (弹窗)](arkts-arkui-promptaction-n.md)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [promptAction/promptAction](arkts-arkui-promptaction-n.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [showActionMenu](arkts-arkui-prompt-showactionmenu-f.md) | 创建并显示操作菜单，菜单响应结果异步返回。 |
| [showActionMenu](arkts-arkui-prompt-showactionmenu-f.md) | 创建并显示操作菜单，菜单响应后同步返回结果。 |
| [showDialog](arkts-arkui-prompt-showdialog-f.md) | 创建并显示对话框，对话框响应结果异步返回。 |
| [showDialog](arkts-arkui-prompt-showdialog-f.md) | 创建并显示对话框，对话框响应后同步返回结果。 |
| [showToast](arkts-arkui-prompt-showtoast-f.md) | 创建并显示文本提示框。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ActionMenuOptions](arkts-arkui-prompt-actionmenuoptions-i.md) | 操作菜单的选项。 |
| [ActionMenuSuccessResponse](arkts-arkui-prompt-actionmenusuccessresponse-i.md) | 操作菜单的响应结果。 |
| [Button](arkts-arkui-prompt-button-i.md) | 菜单中的菜单项按钮。 |
| [ShowDialogOptions](arkts-arkui-prompt-showdialogoptions-i.md) | 对话框的选项。 |
| [ShowDialogSuccessResponse](arkts-arkui-prompt-showdialogsuccessresponse-i.md) | 对话框的响应结果。 |
| [ShowToastOptions](arkts-arkui-prompt-showtoastoptions-i.md) | 文本提示框的选项。 |
