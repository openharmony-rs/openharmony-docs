# 滑动选择文本选择器

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TEXT_PICKER_OPTION_RANGE

```c
NODE_TEXT_PICKER_OPTION_RANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_PICKER
```

**描述：**

设置滑动选择文本选择器的选择列表，支持属性设置，属性重置和属性获取接口。 使用场景：单列选择器适用于单一类别选择（如省份、品牌），多列选择器适用于多个独立类别组合选择（如省-市），多列联动选择器适用于有层级关系的选择场景（如省-市-区，第二列根据第一列自动更新）。 需先设置该参数后，才能使用 NODE_TEXT_PICKER_OPTION_SELECTED 和 NODE_TEXT_PICKER_SELECTED_INDEX 设置选中项。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：使用的选择器类型{@link ArkUI_TextPickerRangeType}，默认值为ARKUI_TEXTPICKER_RANGETYPE_SINGLE。<br>ARKUI_TEXTPICKER_RANGETYPE_SINGLE适用于单列选择，ARKUI_TEXTPICKER_RANGETYPE_MULTI适用于多列独立选择，<br>ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT适用于单列带图片选择，ARKUI_TEXTPICKER_RANGETYPE_CASCADE适用于多列联动选择。</li><br><li>?.string：针对不同选择器类型有如下输入范式：1：单列选择器，入参格式为用分号分隔的一组字符串；<br>2：多列选择器，支持多对纯文本字符串对，多对之间使用分号分隔，每对内部使用逗号分隔。不传此参数时不设置选择列表。</li><br><li>?.object：针对不同选择器类型有如下输入范式：<br>1：单列支持图片的选择器，输入结构体为{@link ARKUI_TextPickerRangeContentArray}；<br>2：多列联动选择器，输入结构体为{@link ARKUI_TextCascadePickerRangeContentArray}。不传此参数时不设置选择列表。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：使用的选择器类型{@link ArkUI_TextPickerRangeType}。</li> <li>?.string：针对不同选择器类型有如下输出范式：1：单列选择器，输出格式为用分号分隔的一组字符串；2：多列选择器，输出多对纯文本字符串对，多对之间使用分号分隔，每对内部使用逗号分隔。</li> </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_OPTION_SELECTED

```c
NODE_TEXT_PICKER_OPTION_SELECTED
```

**描述：**

设置滑动选择文本内容的组件默认选中项在数组中的索引值，支持属性设置，属性重置和属性获取接口。需先通过 NODE_TEXT_PICKER_OPTION_RANGE 设置选项列表后才能使用该参数。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].u32：默认选中项在选择器选项数组中的索引值，取值范围为[0, length-1]。超出范围时抛出异常。多列选择器时，如存在多个索引值则逐个添加。默认值：0。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].u32：选中项在选择器选项数组中的索引值，如存在多个索引值则逐个添加。</li> </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_OPTION_VALUE

```c
NODE_TEXT_PICKER_OPTION_VALUE
```

**描述：**

设置滑动选择文本内容的组件默认选中项的值，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：选中项的值，如存在多个值则逐个添加，用分号分隔。默认值：空字符串，未设置时使用默认值。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：选中项的值，如存在多个值则逐个添加，用分号分隔。</li> </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_TEXT_PICKER_DISAPPEAR_TEXT_STYLE
```

**描述：**

设置滑动选择文本内容的组件所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：参数5个，格式为字符串，以 ';' 分割：</li><br> 参数1： 文本颜色，#argb类型；<br> 参数2： 文本大小，数字类型，单位fp；<br> 参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")；<br> 参数4： 文本字体列表，使用 ',' 进行分割；<br> 参数5： 文本样式，字符串枚举("normal", "italic")；<br> 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。<br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1：文本颜色，#argb类型。 参数2：文本大小，数字类型，单位fp。 参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4：文本字体列表，使用 ',' 进行分割。 参数5：文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。 </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_TEXT_STYLE

```c
NODE_TEXT_PICKER_TEXT_STYLE
```

**描述：**

设置滑动选择文本内容的组件所有选项中除了最上、最下及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：参数5个，格式为字符串，以 ';' 分割：</li><br> 参数1： 文本颜色，#argb类型。<br> 参数2： 文本大小，数字类型，单位fp。<br> 参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br> 参数4： 文本字体列表，使用 ',' 进行分割。<br> 参数5： 文本样式，字符串枚举("normal", "italic")。<br> 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。<br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1：文本颜色，#argb类型。 参数2：文本大小，数字类型，单位fp。 参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4：文本字体列表，使用 ',' 进行分割。 参数5：文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。 </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_SELECTED_TEXT_STYLE

```c
NODE_TEXT_PICKER_SELECTED_TEXT_STYLE
```

**描述：**

设置滑动选择文本内容的组件选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：参数5个，格式为字符串，以 ';' 分割：</li><br> 参数1： 文本颜色，#argb类型；<br> 参数2： 文本大小，数字类型，单位fp；<br> 参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")；<br> 参数4： 文本字体列表，使用 ',' 进行分割；<br> 参数5： 文本样式，字符串枚举("normal", "italic")；<br> 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。<br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1：文本颜色，#argb类型。 参数2：文本大小，数字类型，单位fp。 参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4：文本字体列表，使用 ',' 进行分割。 参数5：文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。 </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_SELECTED_INDEX

```c
NODE_TEXT_PICKER_SELECTED_INDEX
```

**描述：**

设置滑动选择文本内容的组件默认选中项的索引数组，支持属性设置，属性重置和属性获取接口。 需先通过 NODE_TEXT_PICKER_OPTION_RANGE 设置选项列表后才能使用该参数。设置选项列表后，如未通过本参数设置索引数组，则默认选中各列的第1项。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0...].i32：默认选中项在选择器选项数组中的索引值数组。用于多列选择器时设置每列的默认选中项索引。默认值：每列均为0。取值范围：每列索引值为[0, 对应列长度-1]，超出范围时抛出异常。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0...].i32：当前选中的索引值数组，用于多列选择器时表示每列的选中项索引。</li> </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_CAN_LOOP

```c
NODE_TEXT_PICKER_CAN_LOOP
```

**描述：**

Picker组件可循环滚动属性，支持属性设置，属性重置和属性获取接口。 使用场景：循环滚动适用于选项有限且希望提供快速选择体验的场景（如省份选择）；非循环滚动适用于选项有明确边界、需要限制用户选择范围的场景（如数量选择避免误操作）。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：0表示不可循环，1表示可循环。默认值：1。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：0表示不可循环，1表示可循环。</li> </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT

```c
NODE_TEXT_PICKER_DEFAULT_PICKER_ITEM_HEIGHT
```

**描述：**

设置Picker组件各选择项的高度，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].f32：当前设置的选项高度值，单位为vp。默认值：40.0vp，未设置时使用默认值。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].f32：当前设置的选项高度值，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_PICKER_ENABLE_HAPTIC_FEEDBACK = 15010
```

**描述：**

设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：是否开启触控反馈。1表示开启触控反馈，0表示不开启触控反馈。开启后，是否存在触控反馈取决于系统硬件支持情况。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：是否开启触控反馈。1表示开启触控反馈，0表示不开启触控反馈。</li> </ul>

**起始版本：** 18

### NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE

```c
NODE_TEXT_PICKER_SELECTED_BACKGROUND_STYLE = 15011
```

**描述：**

设置选中项的背景颜色和边框圆角。支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].u32：背景颜色，采用 0xARGB 格式。其中A表示透明度(0x00完全透明~0xFF完全不透明)，<br>RGB表示颜色值(0x000000~0xFFFFFF)，每个字节取值范围0x00~0xFF。例如，0xFF1122FF表示完全不透明的蓝色。</li><br><li>.value[1].f32：左上角的圆角半径，单位为VP。</li><br><li>.value[2].f32：右上角的圆角半径，单位为VP。</li><br><li>.value[3].f32：左下角的圆角半径，单位为VP。</li><br><li>.value[4].f32：右下角的圆角半径，单位为VP。</li><br></ul><br><p>默认值：背景颜色：0x0C182431；圆角半径：24.0。</p><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].u32：背景颜色，采用 0xARGB 格式，例如，<b>0xFF1122FF</b>。</li><br><li>.value[1].f32：左上角的圆角半径，单位为VP。</li><br><li>.value[2].f32：右上角的圆角半径，单位为VP。</li><br><li>.value[3].f32：左下角的圆角半径，单位为VP。</li><br><li>.value[4].f32：右下角的圆角半径，单位为VP。</li> </ul>

**起始版本：** 20

### NODE_TEXT_PICKER_COLUMN_WIDTHS

```c
NODE_TEXT_PICKER_COLUMN_WIDTHS = 15009
```

**描述：**

设置每一个选择项列宽，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].f32：设置的第1个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等，默认值为不设置时各列均分。</li><br><li>.value[1]?.f32：设置的第2个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。</li><br><li>.value[2]?.f32：设置的第3个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。</li><br><li>...</li><br><li>.value[n]?.f32：设置的第n+1个选择项列宽，为总宽度的百分比。默认情况下，所有选择项的列宽相等。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].f32：第1列宽度，总宽度的百分比。</li><br><li>.value[1].f32：第2列宽度，总宽度的百分比。</li><br><li>.value[2].f32：第3列宽度，总宽度的百分比。</li><br><li>...</li><br><li>.value[n].f32：第n+1列宽度，总宽度的百分比。</li> </ul>

**起始版本：** 18


