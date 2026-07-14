# TimePicker

滑动选择时间的组件。

> **说明：**

> - 该组件不建议开发者在动效过程中修改属性数据。
>
> - 最大显示行数在横、竖屏模式下存在差异。竖屏时默认为5行，横屏时依赖系统配置，未配置时默认显示为3行。可通过如下参数查看具体配置值
    $r('sys.float.ohos_id_picker_show_count_landscape')。


## TimePicker

```TypeScript
TimePicker(options?: TimePickerOptions)
```

创建滑动选择器，默认使用24小时的时间区间。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TimePickerOptions | 否 | 配置时间选择组件的参数。 |

## 汇总

- [TimePickerDialogOptions](arkts-arkui-timepicker-timepickerdialogoptions-i.md)
- [TimePickerOptions](arkts-arkui-timepicker-timepickeroptions-i.md)
- [TimePickerResult](arkts-arkui-timepicker-timepickerresult-i.md)
- [DateTimeOptions](arkts-arkui-timepicker-datetimeoptions-t.md)
- [OnTimePickerChangeCallback](arkts-arkui-timepicker-ontimepickerchangecallback-t.md)
- [TimePickerFormat](arkts-arkui-timepicker-timepickerformat-e.md)
