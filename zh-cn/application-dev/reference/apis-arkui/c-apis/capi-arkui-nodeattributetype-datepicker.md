# 日期选择器

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_DATE_PICKER_LUNAR

```c
NODE_DATE_PICKER_LUNAR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_DATE_PICKER
```

**描述：**

设置日期选择器组件的日期是否显示农历，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：是否显示农历，默认值0。0表示不展示农历，1表示展示农历。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：是否显示农历。返回0表示不展示农历，返回1表示展示农历。</li> </ul><br> *

**起始版本：** 12

### NODE_DATE_PICKER_START

```c
NODE_DATE_PICKER_START
```

**描述：**

设置日期选择器组件选择器的起始日期，支持属性设置，属性重置和属性获取接口。设置的起始日期会限定日期选择的有效范围，超出范围的选中日期会自动调整。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：日期，默认值"1970-1-1"。格式：年-月-日，年份支持1或4位，月份和日期为1-2位数字。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：设置的起始日期，格式为年-月-日。</li> </ul><br> *

**起始版本：** 12

### NODE_DATE_PICKER_END

```c
NODE_DATE_PICKER_END
```

**描述：**

设置日期选择器组件选择器的结束日期，支持属性设置，属性重置和属性获取接口。设置的结束日期会限定日期选择的有效范围，超出范围的选中日期会自动调整。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：日期，默认值"2100-12-31"。格式：年-月-日，年份支持1或4位，月份和日期为1-2位数字。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：设置的结束日期，格式为年-月-日。</li> </ul><br> *

**起始版本：** 12

### NODE_DATE_PICKER_SELECTED

```c
NODE_DATE_PICKER_SELECTED
```

**描述：**

设置日期选择器组件选中项的日期，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：日期，默认值"2024-01-22"，未设置时使用默认值。格式：年-月-日，年份支持1或4位，月份和日期为1-2位数字。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：选中的日期，格式为年-月-日。</li> </ul><br> *

**起始版本：** 12

### NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE

```c
NODE_DATE_PICKER_DISAPPEAR_TEXT_STYLE
```

**描述：**

设置日期选择器组件的所有选项中最上和最下两个选项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：参数5个，格式为字符串，以 ';' 分割：</li><br> 参数1： 文本颜色，#ARGB类型。<br> 参数2： 文本大小，数字类型，单位fp。<br> 参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br> 参数4： 文本字体列表，使用 ',' 进行分割。<br> 参数5： 文本样式，字符串枚举("normal", "italic")。<br> 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。<br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1：文本颜色，#argb类型。 参数2：文本大小，数字类型，单位fp。 参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4：文本字体列表，使用 ',' 进行分割。 参数5：文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。 </ul><br> *

**起始版本：** 12

### NODE_DATE_PICKER_TEXT_STYLE

```c
NODE_DATE_PICKER_TEXT_STYLE
```

**描述：**

设置日期选择器组件的所有选项中除了边缘项及选中项以外的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：参数5个，格式为字符串，以 ';' 分割：</li><br> 参数1： 文本颜色，#argb类型。<br> 参数2： 文本大小，数字类型，单位fp。<br> 参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br> 参数4： 文本字体列表，使用 ',' 进行分割。<br> 参数5： 文本样式，字符串枚举("normal", "italic")。<br> 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。<br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1：文本颜色，#argb类型。 参数2：文本大小，数字类型，单位fp。 参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4：文本字体列表，使用 ',' 进行分割。 参数5：文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。 </ul><br> *

**起始版本：** 12

### NODE_DATE_PICKER_SELECTED_TEXT_STYLE

```c
NODE_DATE_PICKER_SELECTED_TEXT_STYLE
```

**描述：**

设置日期选择器组件的选中项的文本颜色、字号、字体粗细，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.string：参数5个，格式为字符串，以 ';' 分割：</li><br> 参数1： 文本颜色，#argb类型。<br> 参数2： 文本大小，数字类型，单位fp。<br> 参数3： 文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。<br> 参数4： 文本字体列表，使用 ',' 进行分割。<br> 参数5： 文本样式，字符串枚举("normal", "italic")。<br> 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal" 。未设置时使用系统默认样式。<br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.string：参数5个，格式为字符串，以 ';' 分割：</li> 参数1：文本颜色，#argb类型。 参数2：文本大小，数字类型，单位fp。 参数3：文本粗细，字符串枚举("bold", "normal", "bolder", "lighter", "medium", "regular")。 参数4：文本字体列表，使用 ',' 进行分割。 参数5：文本样式，字符串枚举("normal", "italic")。 如 "#ff182431;14;normal;Arial,HarmonyOS Sans;normal"。 </ul><br> *

**起始版本：** 12

### NODE_DATE_PICKER_MODE

```c
NODE_DATE_PICKER_MODE = 13007
```

**描述：**

设置要显示的日期选项列。DatePicker显示不同样式的日期列，支持属性设置，属性重置和属性获取接口。 使用场景：根据应用需求选择合适的日期显示模式，如需要精确选择到日时使用年/月/日模式，只需要月份时使用年/月模式等。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：显示的日期列类型。参数类型{@link ArkUI_DatePickerMode}。默认值：完整的日期列（年、月、日）。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：当前设置的日期列类型枚举值，类型为{@link ArkUI_DatePickerMode}。</li> </ul>

**起始版本：** 18

### NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_DATE_PICKER_ENABLE_HAPTIC_FEEDBACK = 13008
```

**描述：**

设置是否开启触控反馈。支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：是否开启触控反馈。1表示开启触控反馈，0表示不开启触控反馈。开启后，是否存在触控反馈取决于系统硬件支持情况。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：是否开启触控反馈。1表示开启触控反馈，0表示不开启触控反馈。</li> </ul>

**起始版本：** 18

### NODE_DATE_PICKER_CAN_LOOP

```c
NODE_DATE_PICKER_CAN_LOOP = 13009
```

**描述：**

Picker组件可循环滚动属性，支持属性设置，属性重置和属性获取接口。 使用场景：循环滚动适用于选项有限且希望提供快速选择体验的场景（如月份选择）；非循环滚动适用于选项有明确边界、需要限制用户选择范围的场景（如日期选择避免跨年混淆）。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：是否可循环。1表示可循环，0表示不可循环。默认值：1，设置异常值时使用默认值。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：0表示不可循环，1表示可循环。</li> </ul><br> 说明：可循环情况下，年份随着月份的循环滚动进行联动加减，月份随着日的循环滚动进行联动加减。 不可循环情况下，年/月/日到达本列的顶部或底部时，无法再进行滚动，年/月/日之间也无法再联动加减。

**起始版本：** 20


