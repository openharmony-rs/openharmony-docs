# CalendarPickerDialog

```TypeScript
declare class CalendarPickerDialog
```

点击日期弹出日历选择器弹窗，可在弹窗内选择日期。适用于需要在应用中进行日期选择的场景，如日程管理、预订系统、表单填写等。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: CalendarDialogOptions): void
```

显示日历选择器弹窗，供用户选择日期。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CalendarDialogOptions](arkts-arkui-calendarpicker-comp-calendardialogoptions-i.md) | 否 | 配置日历选择器弹窗的参数，缺省时无法弹出弹窗。 |
