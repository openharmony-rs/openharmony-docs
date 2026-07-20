# TimePickerOptions

时间选择器组件的参数说明。

在TimePicker组件滑动过程中修改TimePickerOptions中的属性，会导致这些属性无法生效。

Date对象用于处理日期和时间，使用方式如下。

**方式1：** new Date()

获取系统当前日期和时间。

**方式2：** new Date(value: number | string)

**方式3：** new Date(year: number, monthIndex: number, date?: number, hours?: number, minutes?: number, seconds?:number, ms?: number)

**起始版本：** 8

<!--Device-unnamed-declare interface TimePickerOptions--><!--Device-unnamed-declare interface TimePickerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

指定时间选择组件的结束时间。

默认值：Date(0, 0, 0, 23, 59, 59)

**说明：**

1. 仅设置的小时和分钟生效。2. 设置了end且为非默认值的场景下，loop不生效。

**类型：** Date

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerOptions-end?: Date--><!--Device-TimePickerOptions-end?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## format

```TypeScript
format?: TimePickerFormat
```

指定需要显示的TimePicker的格式。

默认值：TimePickerFormat.HOUR_MINUTE

**类型：** TimePickerFormat

**默认值：** HOUR_MINUTE

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerOptions-format?: TimePickerFormat--><!--Device-TimePickerOptions-format?: TimePickerFormat-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

设置选中项的时间。

默认值：当前系统时间

从API version 10开始，该参数支持[$$](docroot://ui/state-management/arkts-two-way-sync.md)双向绑定变量。

**类型：** Date

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerOptions-selected?: Date--><!--Device-TimePickerOptions-selected?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

指定时间选择组件的起始时间。

默认值：Date(0, 0, 0, 0, 0, 0)

**说明：**

1. 仅设置的小时和分钟生效。2. 设置了start且为非默认值的场景下，loop不生效。

**类型：** Date

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TimePickerOptions-start?: Date--><!--Device-TimePickerOptions-start?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

