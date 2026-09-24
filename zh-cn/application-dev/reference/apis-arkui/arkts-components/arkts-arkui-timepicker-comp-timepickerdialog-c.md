# TimePickerDialog

```TypeScript
declare class TimePickerDialog
```

以24小时的时间区间创建时间滑动选择器，展示在弹窗上。适用于需要用户选择时间的场景，如设置闹钟、日程安排、预约时间等。该组件提供直观的时间选择交互，支持12小时制和24小时制切换，并可自定义样式和布局，帮助应用快速实现时间选择功能，提升用户体验。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: TimePickerDialogOptions)
```

定义时间滑动选择器弹窗并弹出。

> **说明：** 
> 
> 从API version 10开始，可以通过使用[UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md)中的
> [showTimePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showtimepickerdialog)来明确UI的执行上下文。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [showTimePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showtimepickerdialog)

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TimePickerDialogOptions](arkts-arkui-timepicker-comp-timepickerdialogoptions-i.md) | 否 | 配置时间选择器弹窗的参数。参数缺省时不弹出弹窗。 |
