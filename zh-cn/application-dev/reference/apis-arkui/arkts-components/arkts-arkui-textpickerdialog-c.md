# TextPickerDialog

A text picker dialog box is a dialog box that allows users to select text from the given range.

**起始版本：** 8

<!--Device-unnamed-declare class TextPickerDialog--><!--Device-unnamed-declare class TextPickerDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: TextPickerDialogOptions)
```

定义文本滑动选择器弹窗并弹出。
> **说明：**

showTextPickerDialog需先获取[UIContext](../arkts-apis/arkts-arkui-uicontext.md)实例后再进行调用。
> 从API version 10开始，可以通过使用[UIContext](../arkts-apis/arkts-arkui-uicontext.md)中的  
> [showTextPickerDialog](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showtextpickerdialog)  
> 来明确UI的执行上下文。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** showTextPickerDialog

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerDialog-static show(options?: TextPickerDialogOptions)--><!--Device-TextPickerDialog-static show(options?: TextPickerDialogOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextPickerDialogOptions](arkts-arkui-textpickerdialogoptions-i.md) | 否 | 配置文本选择器弹窗的参数。参数缺省时无法弹出弹窗。 |

