# TextPicker

滑动选择文本、图片或图文混排内容的组件，用户可以按需创建单列数据选择器、多列非联动数据选择器和多列联动数据选择器，适用于需要用户从预设选项中选择数据的场景，如日期选择、地区选择、配置项设置等。组件支持循环滚动、自定义文本样式、分割线样式、渐隐效果、选择项高度调整、触控反馈、表冠灵敏度设置等特性，提供流畅的滑动交互体验和灵活的数据展示方式。

> **说明：** > > - 该组件从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 该组件不建议开发者在动效过程中修改属性数据。 > > - 最大显示行数在横、竖屏模式下存在差异。竖屏时默认为5行，横屏时依赖系统配置，未配置时默认显示为3行。 > 可通过如下参数查看具体配置值$r('sys.float.ohos_id_picker_show_count_landscape')。 > > - 多列非联动数据选择器和多列联动数据选择器在下文中统称为多列数据选择器。

>

## 子组件 > > 该组件为基础组件，不建议包含子组件。

## TextPicker

```TypeScript
TextPicker(options?: TextPickerOptions)
```

根据指定的数据列表创建文本选择器。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextPickerOptions](arkts-arkui-textpickeroptions-i.md) | 否 | 配置文本选择器的参数。当需要自定义选择器的数据源、选中项、列宽等配置时传入此参数。参数缺省时组件无法显示。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [DividerOptions](arkts-arkui-divideroptions-i.md) | 分割线的信息。 |
| [PickerBackgroundStyle](arkts-arkui-pickerbackgroundstyle-i.md) | 选择器选中项的背景样式，包括选中项的背景颜色和边框圆角半径。 |
| [TextCascadePickerRangeContent](arkts-arkui-textcascadepickerrangecontent-i.md) | 多列联动数据选择器的数据选项内容。 |
| [TextPickerDialogOptions](arkts-arkui-textpickerdialogoptions-i.md) | 文本选择器弹窗的参数继承自[TextPickerOptions](arkts-arkui-textpickeroptions-i.md)。 |
| [TextPickerDialogOptionsExt](arkts-arkui-textpickerdialogoptionsext-i.md) | 文本选择器弹窗的参数继承自[TextPickerOptions](arkts-arkui-textpickeroptions-i.md)。 |
| [TextPickerOptions](arkts-arkui-textpickeroptions-i.md) | 文本选择器的参数说明。 |
| [TextPickerRangeContent](arkts-arkui-textpickerrangecontent-i.md) | 单列数据选择器的数据选项内容。 |
| [TextPickerResult](arkts-arkui-textpickerresult-i.md) | 文本选择器结果。 |
| [TextPickerTextStyle](arkts-arkui-textpickertextstyle-i.md) | 文本样式选项，继承自[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnTextPickerChangeCallback](arkts-arkui-ontextpickerchangecallback-t.md) | 定义触发onChange事件的回调类型。 |
| [TextPickerEnterSelectedAreaCallback](arkts-arkui-textpickerenterselectedareacallback-t.md) | 定义触发onEnterSelectedArea事件的回调类型。 |
| [TextPickerScrollStopCallback](arkts-arkui-textpickerscrollstopcallback-t.md) | 定义触发onScrollStop事件的回调类型。 |

## 示例

```TypeScript
### 示例1（设置选择器列数）

该示例通过配置range实现单列数据选择器和多列数据选择器，并使用columnWidths调整每一列的宽度。

从API version 18开始，新增了[TextPickerOptions](#textpickeroptions对象说明)的columnWidths属性。


```

```TypeScript
### 示例2（设置文本样式）

该示例使用[disappearTextStyle](#disappeartextstyle10)、[textStyle](#textstyle10)、[selectedTextStyle](#selectedtextstyle10)设置文本选择器中的文本样式。


```

```TypeScript
### 示例3（设置无分割线样式）

该示例通过配置[divider](#divider12)为null实现无分割线样式的文本选择器。


```

```TypeScript
### 示例4（设置分割线样式）

该示例通过配置divider的DividerOptions设置文本选择器的分割线样式。


```

```TypeScript
### 示例5（设置渐隐效果）

该示例通过配置[gradientHeight](#gradientheight12)设置文本选择器的渐隐效果高度。


```

```TypeScript
### 示例6（设置选择项高度）

该示例通过配置[defaultPickerItemHeight](#defaultpickeritemheight)设置选择项的高度。


```

```TypeScript
### 示例7（设置循环滚动）

该示例通过配置[canLoop](#canloop10)设置文本选择器是否循环滚动。


```

```TypeScript
### 示例8（设置选中项索引值）

该示例通过配置[selectedIndex](#selectedindex10)设置默认选中项的索引值。


```

```TypeScript
### 示例9（设置关闭文本样式变化动效与对应文本样式）

该示例通过配置[disableTextStyleAnimation](#disabletextstyleanimation15)、[defaultTextStyle](#defaulttextstyle15)实现关闭文本选择器文本样式变化的动效，并设置文本样式。

从API version 15开始，新增disableTextStyleAnimation、defaultTextStyle接口。


```

```TypeScript
### 示例10（设置选中项背景样式）

该示例通过配置[selectedBackgroundStyle](#selectedbackgroundstyle20)实现文本选择器选中项的背景样式。


```

```TypeScript
### 示例11（设置文本的最大字号、最小字号、超长文本截断方式）

该示例通过配置[disappearTextStyle](#disappeartextstyle20)、[textStyle](#textstyle20)和[selectedTextStyle](#selectedtextstyle20)，设置文本的颜色、最大字号、最小字号、超长文本截断方式。

从API version 20开始，新增disappearTextStyle、textStyle和selectedTextStyle接口。
```
