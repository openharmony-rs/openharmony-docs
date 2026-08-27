# DatePickerOptions

日期选择器组件的参数说明。

> **说明：**
> 
> - Date的使用请参考[TimePickerOptions](arkts-arkui-timepickeroptions-i.md)。
> 
> - 在DatePicker组件滑动过程中修改DatePickerOptions中的属性，会导致这些属性无法生效。
> 
> - 如果需要设置的起止日期范围在\[Date('1900-01-31'), Date('2100-12-31')]之外，推荐使用
> [DatePickerComponent](../arkts-apis/arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponent-s.md)。

> **起始日期、结束日期和选中日期的异常情形说明：**
> 
> - 起始日期晚于结束日期，选中日期未设置：起始日期、结束日期和选中日期都为默认值。
> - 起始日期晚于结束日期，选中日期早于起始日期默认值：起始日期、结束日期都为默认值，选中日期为起始日期默认值。
> - 起始日期晚于结束日期，选中日期晚于结束日期默认值：起始日期、结束日期都为默认值，选中日期为结束日期默认值。
> - 起始日期晚于结束日期，选中日期在起始日期与结束日期默认值范围内：起始日期、结束日期都为默认值，选中日期为设置的值。
> - 选中日期早于起始日期：选中日期为起始日期。
> - 选中日期晚于结束日期：选中日期为结束日期。
> - 起始日期晚于当前系统日期，选中日期未设置：选中日期为起始日期。
> - 结束日期早于当前系统日期，选中日期未设置：选中日期为结束日期。
> - 日期格式不符合规范，如'1999-13-32'：取默认值。
> - 起始日期或结束日期早于系统有效范围：起始日期或结束日期取起始日期默认值。
> - 起始日期或结束日期晚于系统有效范围：起始日期或结束日期取结束日期默认值。
> - 起始日期与结束日期同时早于系统有效范围：起始日期与结束日期取系统有效范围最早日期。
> - 起始日期与结束日期同时晚于系统有效范围：起始日期与结束日期取系统有效范围最晚日期。

> **说明：**
> 
> 先处理起始日期与结束日期的异常情形，再处理选中日期的异常情形。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## end

```TypeScript
end?: Date
```

指定选择器的结束日期。适用于需要限制可选日期上限的场景，如设置有效期截止日。

> 默认值：Date('2100-12-31')

> 取值范围：[Date('1900-01-31'), Date('2100-12-31')]

> **说明：**
> 
> 设置了start或end且为非默认值的场景下，canLoop不生效。

**类型：** Date

**默认值：** Date('2100-12-31') [since 11]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DatePickerMode
```

设置日期展示模式。适用于需要自定义日期展示列的场景，如仅需选择年月或月日。不传入时默认为DatePickerMode.DATE，显示年、月、日三列。在[DatePickerDialog](arkts-arkui-datepickerdialog-c.md)中，当 [DatePickerDialogOptions](arkts-arkui-datepickerdialogoptions-i.md)的showTime设置为true时，此参数不生效，默认显示年、月、日三列。 这是为保证布局合理性，当showTime为true时会额外显示时间列。

> **说明：**
> 
> 上述DatePickerDialog相关限制仅适用于DatePickerDialog组件。

**类型：** [DatePickerMode](arkts-arkui-datepickermode-e.md)

**默认值：** DatePickerMode.DATE - which means to display three columns: year, month, and day. 
Decimal values are rounded off.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

设置选中项的日期。适用于需要预设初始选中日期（如编辑已有记录、默认显示指定日期）的场景。

> 默认值：当前系统日期（受start和end参数影响，详见下方异常情形说明）。

> Date对象可配置的日期范围：[Date('1900-01-31'), Date('2100-12-31')]，selected参数的有效取值范围：必须在start和end参数设置的日
> 期范围内。

> 从API version 10开始，该参数支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

**类型：** Date

**默认值：** current system date [since 11]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

指定选择器的起始日期。适用于需要限制可选日期下限的场景，如仅允许选择某一日期之后的日期。

> 默认值：Date('1970-01-01')

> 取值范围：[Date('1900-01-31'), Date('2100-12-31')]

> **说明：**
> 
> 设置了start或end且为非默认值的场景下，canLoop不生效。

**类型：** Date

**默认值：** Date('1970-1-1') [since 11]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
