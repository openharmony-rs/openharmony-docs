# showToast

## showToast

```TypeScript
function showToast(options: ShowToastOptions): void
```

创建并显示文本提示框。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.arkui.UIContext.PromptAction#showToast

<!--Device-prompt-function showToast(options: ShowToastOptions): void--><!--Device-prompt-function showToast(options: ShowToastOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 文本弹窗选项。 |

**示例：**

```TypeScript
import prompt from '@ohos.prompt'
prompt.showToast({
  message: 'Message Info',
  duration: 2000
});
```

