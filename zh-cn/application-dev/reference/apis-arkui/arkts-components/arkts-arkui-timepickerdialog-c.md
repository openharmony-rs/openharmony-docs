# TimePickerDialog

以24小时的时间区间创建时间滑动选择器，展示在弹窗上。

**起始版本：** 8

<!--Device-unnamed-declare class TimePickerDialog--><!--Device-unnamed-declare class TimePickerDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: TimePickerDialogOptions)
```

定义时间滑动选择器弹窗并弹出。

**说明：**

showTimePickerDialog需先获取[UIContext](../arkts-apis/arkts-arkui-uicontext.md)实例后再进行调用。

- 从API version 10开始，可以通过使用[UIContext](../arkts-apis/arkts-arkui-uicontext.md)中的[showTimePickerDialog](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#showtimepickerdialog)来明确UI的执行上下文。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** showTimePickerDialog

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerDialog-static show(options?: TimePickerDialogOptions)--><!--Device-TimePickerDialog-static show(options?: TimePickerDialogOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TimePickerDialogOptions](arkts-arkui-timepickerdialogoptions-i.md) | 否 | 配置时间选择器弹窗的参数。参数缺省时无法弹出弹窗。 |

