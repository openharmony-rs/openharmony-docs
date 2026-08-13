# DatePicker

DatePicker是滑动选择日期的组件，支持公历和农历切换，可配置日期范围、选择模式和文本样式。用于需要用户选择日期的应用场景， 提供统一的日期选择交互体验，能够提升用户体验，减少开发工作量。 > **说明：** > > - 该组件从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 该组件不建议开发者在动效过程中修改属性数据。 > > - 最大显示行数在横、竖屏模式下存在差异。竖屏时默认为5行，横屏时依赖系统配置，未配置时默认显示为3行。 > 可通过$r('sys.float.ohos_id_picker_show_count_landscape')查看横屏时的具体配置值。 >

## 子组件 > > 该组件为基础组件，不建议包含子组件。

## DatePicker

```TypeScript
DatePicker(options?: DatePickerOptions)
```

根据指定日期范围创建日期选择器。使用场景包括：生日选择、会议预订、行程安排等需要用户选择日期的应用功能。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerInterface-(options?: DatePickerOptions): DatePickerAttribute--><!--Device-DatePickerInterface-(options?: DatePickerOptions): DatePickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DatePickerOptions](arkts-arkui-datepickeroptions-i.md) | 否 | 配置日期选择器组件的参数。不传该参数时使用默认配置（start默认为Date('1970-01-01')， end默认为Date('2100-12-31')，selected默认为当前系统日期）。 |

## 汇总

- [DatePickerDialogOptions](arkts-arkui-datepickerdialogoptions-i.md)
- [DatePickerOptions](arkts-arkui-datepickeroptions-i.md)
- [DatePickerResult](arkts-arkui-datepickerresult-i.md)
- [LunarSwitchStyle](arkts-arkui-lunarswitchstyle-i.md)
- [DatePickerMode](arkts-arkui-datepickermode-e.md)
