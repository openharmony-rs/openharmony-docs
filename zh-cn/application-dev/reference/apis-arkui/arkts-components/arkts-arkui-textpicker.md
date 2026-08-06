# TextPicker

滑动选择文本、图片或图文混排内容的组件，用户可以按需创建单列数据选择器、多列非联动数据选择器和多列联动数据选择器，适用于需要用户从预设选项中选 择数据的场景，如日期选择、地区选择、配置项设置等。组件支持循环滚动、自定义文本样式、分割线样式、渐隐效果、选择项高度调整、触控反馈、表冠灵敏度 设置等特性，提供流畅的滑动交互体验和灵活的数据展示方式。 > **说明：** > > - 该组件从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 该组件不建议开发者在动效过程中修改属性数据。 > > - 最大显示行数在横、竖屏模式下存在差异。竖屏时默认为5行，横屏时依赖系统配置，未配置时默认显示为3行。 > 可通过如下参数查看具体配置值$r('sys.float.ohos_id_picker_show_count_landscape')。 > > - 多列非联动数据选择器和多列联动数据选择器在下文中统称为多列数据选择器。 >

## 子组件 > > 该组件为基础组件，不建议包含子组件。

## TextPicker

```TypeScript
TextPicker(options?: TextPickerOptions)
```

根据指定的数据列表创建文本选择器。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerInterface-(options?: TextPickerOptions): TextPickerAttribute--><!--Device-TextPickerInterface-(options?: TextPickerOptions): TextPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 配置文本选择器的参数。当需要自定义选择器的数据源、选中项、列宽等配置时传入此参数。参数缺省时 组件无法显示。  |

## 汇总

