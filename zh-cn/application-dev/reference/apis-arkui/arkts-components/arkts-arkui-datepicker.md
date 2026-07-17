# DatePicker

滑动选择日期的组件。

**说明：**

- 该组件不建议开发者在动效过程中修改属性数据。

- 最大显示行数在横、竖屏模式下存在差异。竖屏时默认为5行，横屏时依赖系统配置，未配置时默认显示为3行。可通过如下参数查看具体配置值
    $r('sys.float.ohos_id_picker_show_count_landscape')。

子组件

该组件为基础组件，不建议包含子组件。


## DatePicker

```TypeScript
DatePicker(options?: DatePickerOptions)
```

根据指定日期范围创建日期选择器。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerInterface-(options?: DatePickerOptions): DatePickerAttribute--><!--Device-DatePickerInterface-(options?: DatePickerOptions): DatePickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | DatePickerOptions | 否 | 配置日期选择器组件的参数。 |

## 汇总

- [DatePickerDialogOptions](arkts-arkui-datepicker-datepickerdialogoptions-i.md)
- [DatePickerOptions](arkts-arkui-datepicker-datepickeroptions-i.md)
- [DatePickerResult](arkts-arkui-datepicker-datepickerresult-i.md)
- [LunarSwitchStyle](arkts-arkui-datepicker-lunarswitchstyle-i.md)
- [DatePickerMode](arkts-arkui-datepicker-datepickermode-e.md)
