# TextPicker

滑动选择文本、图片或图文混排内容的组件，用户可以按需创建单列数据选择器、多列非联动数据选择器和多列联动数据选择器。

> **说明：**

> - 该组件不建议开发者在动效过程中修改属性数据。
>
> - 最大显示行数在横、竖屏模式下存在差异。竖屏时默认为5行，横屏时依赖系统配置，未配置时默认显示为3行。可通过如下参数查看具体配置
> 值$r('sys.float.ohos_id_picker_show_count_landscape')。
>
> - 多列非联动数据选择器和多列联动数据选择器在下文中统称为多列数据选择器。

子组件

该组件为基础组件，不建议包含子组件。


## TextPicker

```TypeScript
TextPicker(options?: TextPickerOptions)
```

根据指定的数据列表创建文本选择器。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerInterface-(options?: TextPickerOptions): TextPickerAttribute--><!--Device-TextPickerInterface-(options?: TextPickerOptions): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextPickerOptions](arkts-arkui-textpickeroptions-i.md) | 否 | 配置文本选择器的参数。参数缺省时组件无法显示。  |

## 汇总

- [DividerOptions](arkts-arkui-textpicker-divideroptions-i.md)
- [PickerBackgroundStyle](arkts-arkui-textpicker-pickerbackgroundstyle-i.md)
- [TextCascadePickerRangeContent](arkts-arkui-textpicker-textcascadepickerrangecontent-i.md)
- [TextPickerDialogOptions](arkts-arkui-textpicker-textpickerdialogoptions-i.md)
- [TextPickerDialogOptionsExt](arkts-arkui-textpicker-textpickerdialogoptionsext-i.md)
- [TextPickerOptions](arkts-arkui-textpicker-textpickeroptions-i.md)
- [TextPickerRangeContent](arkts-arkui-textpicker-textpickerrangecontent-i.md)
- [TextPickerResult](arkts-arkui-textpicker-textpickerresult-i.md)
- [TextPickerTextStyle](arkts-arkui-textpicker-textpickertextstyle-i.md)
- [OnTextPickerChangeCallback](arkts-arkui-textpicker-ontextpickerchangecallback-t.md)
- [TextPickerEnterSelectedAreaCallback](arkts-arkui-textpicker-textpickerenterselectedareacallback-t.md)
- [TextPickerScrollStopCallback](arkts-arkui-textpicker-textpickerscrollstopcallback-t.md)
