# DatePickerDialog

```TypeScript
declare class DatePickerDialog
```

根据指定的日期范围创建日期滑动选择器并展示在弹窗上。该组件适用于需要用户快速选择日期的应用场景，如日程安排、活动安排、生日设置等。使用该组件可以简化开发流程，提供统一的日期选择用户体验，并支持多种自定义选项以满足不同需求。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: DatePickerDialogOptions)
```

定义日期滑动选择器弹窗并弹出。

> **说明：** 
> 
> 从API version 10开始，可以通过使用[UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md)中的
> [showDatePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showdatepickerdialog)来明确UI的执行上下文。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [showDatePickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showdatepickerdialog)

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DatePickerDialogOptions](arkts-arkui-datepicker-comp-datepickerdialogoptions-i.md) | 否 | 配置日期选择器弹窗的参数，缺省时不弹出弹窗。 |
