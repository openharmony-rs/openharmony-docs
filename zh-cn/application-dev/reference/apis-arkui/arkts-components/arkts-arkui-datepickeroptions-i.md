# DatePickerOptions

日期选择器组件的参数说明。

> **说明：**
>
> - Date的使用请参考[TimePickerOptions](arkts-arkui-timepickeroptions-i.md)。
>
> - 在DatePicker组件滑动过程中修改DatePickerOptions中的属性，会导致这些属性无法生效。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

指定选择器的结束日期。

默认值：Date('2100-12-31')

取值范围：[Date('1900-01-31'), Date('2100-12-31')]

**类型：** Date

**默认值：** Date('2100-12-31') [since 11]

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DatePickerMode
```

设置日期展示模式。

默认值：DatePickerMode.DATE，显示年、月、日三列。

在[DatePickerDialog](./date_picker)中，当[DatePickerDialogOptions]
(../../../../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions)的showTime设置为
true时，此参数不生效，默认显示年、月、日三列。

**类型：** DatePickerMode

**默认值：** DatePickerMode.DATE - which means to display three columns: year, month, and day.
<br>Decimal values are rounded off.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

设置选中项的日期。

默认值：当前系统日期。

取值范围：[Date('1900-01-31'), Date('2100-12-31')]

从API version 10开始，该参数支持[$$](../../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

**类型：** Date

**默认值：** current system date [since 11]

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

指定选择器的起始日期。

默认值：Date('1970-1-1')

取值范围：[Date('1900-01-31'), Date('2100-12-31')]

**类型：** Date

**默认值：** Date('1970-1-1') [since 11]

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

