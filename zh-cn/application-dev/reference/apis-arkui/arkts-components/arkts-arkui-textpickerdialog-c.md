# TextPickerDialog

Defines TextPickerDialog which uses show method to show TextPicker dialog.

**起始版本：** 8

<!--Device-unnamed-declare class TextPickerDialog--><!--Device-unnamed-declare class TextPickerDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## show

```TypeScript
static show(options?: TextPickerDialogOptions)
```

定义文本滑动选择器弹窗并弹出。 > **说明：** > > 从API version 10开始，可以通过使用[UIContext](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md)中的 > [showTextPickerDialog](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md#showtextpickerdialog)来明确UI的执行上下文。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [showTextPickerDialog](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-uicontext-c.md#showtextpickerdialog)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialog-static show(options?: TextPickerDialogOptions)--><!--Device-TextPickerDialog-static show(options?: TextPickerDialogOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextPickerDialogOptions](arkts-arkui-textpickerdialogoptions-i.md) | 否 | 配置文本选择器弹窗的参数，缺省时无法弹出弹窗。至少需要提供range参数才能正常弹出弹窗， 其他参数均为可选配置。 |

