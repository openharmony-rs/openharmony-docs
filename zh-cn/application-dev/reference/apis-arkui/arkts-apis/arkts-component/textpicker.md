# component/textPicker

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [DividerOptions](textpicker-divideroptions-i.md) | 分割线的信息。 |
| [PickerBackgroundStyle](textpicker-pickerbackgroundstyle-i.md) | 选择器选中项的背景样式，包括选中项的背景颜色和边框圆角半径。 |
| [TextCascadePickerRangeContent](textpicker-textcascadepickerrangecontent-i.md) | 多列联动数据选择器的数据选项内容。 |
| [TextPickerDialogOptions](textpicker-textpickerdialogoptions-i.md) | 文本选择器弹窗的参数继承自[TextPickerOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 默认值： { color: \_\_\_ESCAPED\_DOLLAR\_\_\_r('sys.color.comp\_\_\_ESCAPED\_UNDERSCORE\_\_\_background\_\_\_ESCAPED\_UNDERSCORE\_\_\_tertiary'), borderRadius: \_\_\_ESCAPED\_DOLLAR\_\_\_r('sys.float.corner\_\_\_ESCAPED\_UNDERSCORE\_\_\_radius\_\_\_ESCAPED\_UNDERSCORE\_\_\_level12') } |
| [TextPickerDialogOptionsExt](textpicker-textpickerdialogoptionsext-i.md) | 文本选择器弹窗的参数继承自[TextPickerOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [TextPickerOptions](textpicker-textpickeroptions-i.md) | 文本选择器的参数说明。 |
| [TextPickerRangeContent](textpicker-textpickerrangecontent-i.md) | 单列数据选择器的数据选项内容。 |
| [TextPickerResult](textpicker-textpickerresult-i.md) | 文本选择器结果。 |
| [TextPickerTextStyle](textpicker-textpickertextstyle-i.md) | 文本样式选项，继承自[PickerTextStyle]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TextPickerDialogOptionsExt](textpicker-textpickerdialogoptionsext-i-sys.md) | 文本选择器弹窗的参数继承自[TextPickerOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnTextPickerChangeCallback](arkts-arkui-ontextpickerchangecallback-t.md) | 滑动选中TextPicker文本内容后，触发该回调。当显示文本或图片加文本列表时，选中项的文本值为选中项中的文本值，当显示图片列表时， 选中项的文本值为空。 |
| [TextPickerEnterSelectedAreaCallback](arkts-arkui-textpickerenterselectedareacallback-t.md) | 定义触发onEnterSelectedArea事件的回调类型。 在多列联动场景中，不建议使用该回调，由于该回调标识的是滑动过程中选项进入分割线区域内的节点，而跟随变化的选项并不涉及滑动，因此， 回调的返回值中，仅当前滑动列的值会正常变化，其余未滑动列的值保持不变。 |
| [TextPickerScrollStopCallback](arkts-arkui-textpickerscrollstopcallback-t.md) | 定义触发onScrollStop事件的回调类型。 当显示文本或图片加文本列表时，value值为选中项中的文本值，当显示图片列表时，value值为空。 |

