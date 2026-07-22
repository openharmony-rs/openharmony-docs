# DatePickerDialog

根据指定的日期范围创建日期滑动选择器并展示在弹窗上。

**起始版本：** 8

<!--Device-unnamed-declare class DatePickerDialog--><!--Device-unnamed-declare class DatePickerDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: DatePickerDialogOptions)
```

定义日期滑动选择器弹窗并弹出。
> **说明：**

showDatePickerDialog需先获取[UIContext](../arkts-apis/arkts-arkui-uicontext.md)实例后再进行调用。

- 从API version 10开始，可以通过使用[UIContext](../arkts-apis/arkts-arkui-uicontext.md)中的[showDatePickerDialog](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showdatepickerdialog)来明确UI的执行上下文。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** showDatePickerDialog

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerDialog-static show(options?: DatePickerDialogOptions)--><!--Device-DatePickerDialog-static show(options?: DatePickerDialogOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DatePickerDialogOptions](arkts-arkui-datepickerdialogoptions-i.md) | 否 | 配置日期选择器弹窗的参数。参数缺省时无法弹出弹窗。 |

