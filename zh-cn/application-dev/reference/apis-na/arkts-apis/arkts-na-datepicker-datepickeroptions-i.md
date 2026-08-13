# DatePickerOptions

日期选择器组件的参数说明。 **说明：** - Date的使用请参考TimePickerOptions。 - 在DatePicker组件滑动过程中修改DatePickerOptions中的属性，会导致这些属性无法生效。 **说明：** - 先处理起始日期与结束日期的异常情形，再处理选中日期的异常情形。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface DatePickerOptions--><!--Device-unnamed-export declare interface DatePickerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

指定选择器的结束日期。 默认值：Date('2100-12-31') 取值范围：[Date('1900-01-31'), Date('2100-12-31')]

**类型：** Date

**默认值：** Date('2100-12-31')

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DatePickerOptions-end?: Date--><!--Device-DatePickerOptions-end?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DatePickerMode
```

设置日期展示模式。 默认值：DatePickerMode.DATE，显示年、月、日三列。 在DatePickerDialog中，当[DatePickerDialogOptions] (../../../reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions)的showTime设置 为true时，此参数不生效，默认显示年、月、日三列。

**类型：** [DatePickerMode](arkts-na-datepicker-datepickermode-e.md)

**默认值：** DatePickerMode.DATE - which means to display three columns: year, month, and day. <br>Decimal values are rounded off.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DatePickerOptions-mode?: DatePickerMode--><!--Device-DatePickerOptions-mode?: DatePickerMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date | Bindable<Date>
```

设置选中项的日期。 默认值：当前系统日期。 取值范围：[Date('1900-01-31'), Date('2100-12-31')] 从API version 23开始，该参数支持\$\$双向绑定变量。

**类型：** Date \| [Bindable](arkts-na-common-bindable-i.md)&lt;Date&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DatePickerOptions-selected?: Date | Bindable<Date>--><!--Device-DatePickerOptions-selected?: Date | Bindable<Date>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

指定选择器的起始日期。 默认值：Date('1970-1-1') 取值范围：[Date('1900-01-31'), Date('2100-12-31')]

**类型：** Date

**默认值：** Date('1970-1-1')

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DatePickerOptions-start?: Date--><!--Device-DatePickerOptions-start?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

