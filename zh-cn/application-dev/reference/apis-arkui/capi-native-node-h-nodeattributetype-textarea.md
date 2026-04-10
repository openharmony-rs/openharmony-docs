# ArkUI_NodeAttributeType（TextArea组件相关属性）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6; @kangshihui-->
<!--Designer: @xiangyuan6; @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## 概述

定义ArkUI在Native侧可以设置的TextArea组件相关属性样式集合，包含TextArea组件属性设置。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

## NODE_TEXT_AREA_PLACEHOLDER

```c
NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA = 8000
```

多行文本输入框的默认提示文本内容属性，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .string | 默认提示文本的内容。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .string | 默认提示文本的内容。 |

## NODE_TEXT_AREA_TEXT

```c
NODE_TEXT_AREA_TEXT = 8001
```

多行文本输入框的默认文本内容属性，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .string | 默认文本的内容。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .string | 默认文本的内容。 |

## NODE_TEXT_AREA_MAX_LENGTH

```c
NODE_TEXT_AREA_MAX_LENGTH = 8002
```

输入框支持的最大文本数属性，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 最大文本数的数字。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 最大文本数的数字。 |

## NODE_TEXT_AREA_PLACEHOLDER_COLOR

```c
NODE_TEXT_AREA_PLACEHOLDER_COLOR = 8003
```

无输入时默认提示文本的颜色属性，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 颜色数值，0xargb格式。 |

## NODE_TEXT_AREA_PLACEHOLDER_FONT

```c
NODE_TEXT_AREA_PLACEHOLDER_FONT = 8004
```

无输入时默认提示文本的字体配置（包括大小、字重、样式、字体列表）属性，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0]?.f32 | 可选字体大小数值，默认值16.0，单位为fp。 |
| .value[1]?.i32 | 可选字体样式[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL。 |
| .value[2]?.i32 | 可选字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL。 |
| ?.string | 字体族内容，多个字体族之间使用逗号分隔，形如“字重；字体族1，字体族2”。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 字体大小数值，单位为fp。 |
| .value[1].i32 | 字体样式[ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle)。 |
| .value[2].i32 | 字体粗细样式[ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight)。 |
| .string | 字体族内容，多个字体族之间使用逗号分隔。 |

## NODE_TEXT_AREA_CARET_COLOR

```c
NODE_TEXT_AREA_CARET_COLOR = 8005
```

光标颜色属性，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 背景色数值，0xargb格式，形如 0xFFFF0000 表示红色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 背景色数值，0xargb格式。 |

## NODE_TEXT_AREA_EDITING

```c
NODE_TEXT_AREA_EDITING = 8006
```

控制多行文本输入框编辑态属性，支持属性设置，属性获取接口。<br>
作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | false表示退出编辑态，true表示维持现状。<br>属性获取方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： |
| .value[0].i32 | false表示退出编辑态，true表示维持现状。 |

## NODE_TEXT_AREA_TYPE

```c
NODE_TEXT_AREA_TYPE = 8007
```

输入框的类型属性，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 输入框类型枚举[ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype)，默认值为ARKUI_TEXTAREA_TYPE_NORMAL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 输入框类型枚举[ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype)。 |

## NODE_TEXT_AREA_SHOW_COUNTER

```c
NODE_TEXT_AREA_SHOW_COUNTER = 8008
```

设置输入的字符数超过阈值时是否显示计数器并设置计数器样式，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否开启计数器，值为true时为开启。默认值false。 |
| .value[1]?.f32 | 可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]，小数时向下取整，若超出取值范围，则接口属性设置不生效。 |
| .value[2]?.i32 | 输入字符超出限制时是否高亮边框。true表示高亮边框，false表示不高亮边框。默认值true。 |
| .object | 计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为[ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否开启计数器，值为true时开启。 |
| .value[1].f32 | 可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]。 |
| .value[2].i32 | 输入字符超出限制时是否高亮边框，值为true时高亮边框。 |
| .object | 计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为[ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md)。 |

## NODE_TEXT_AREA_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_AREA_SELECTION_MENU_HIDDEN = 8009
```

设置长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。默认值false。<br>设置为true时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，隐藏系统文本选择菜单。<br>设置为false时，显示系统文本选择菜单。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。 |

## NODE_TEXT_AREA_BLUR_ON_SUBMIT

```c
NODE_TEXT_AREA_BLUR_ON_SUBMIT = 8010
```

设置多行输入框在submit状态下，触发回车键是否失焦。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否失焦。false表示触发回车键后不失焦，true表示触发回车键后失焦。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否失焦。 |

## NODE_TEXT_AREA_INPUT_FILTER

```c
NODE_TEXT_AREA_INPUT_FILTER = 8011
```

通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .string | 正则表达式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .string | 正则表达式。 |

## NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR = 8012
```

设置文本选中底板颜色，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 颜色数值，0xargb格式。 |

## NODE_TEXT_AREA_ENTER_KEY_TYPE

```c
NODE_TEXT_AREA_ENTER_KEY_TYPE = 8013
```

设置输入法回车键类型，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 回车键类型枚举[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_DONE。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 回车键类型枚举[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)。 |

## NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS = 8014
```

设置TextArea通过点击以外的方式获焦时，是否绑定输入法，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | false表示聚焦不拉起输入法，true表示拉起，默认值为true。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 0表示聚焦不拉起输入法，1表示拉起。 |

## NODE_TEXT_AREA_CARET_OFFSET

```c
NODE_TEXT_AREA_CARET_OFFSET = 8015
```

设置或获取光标所在位置信息。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>
设置输入光标的位置。<br>
返回当前光标所在位置信息。在当前帧更新光标位置同时调用该接口，该接口不生效。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 从字符串开始到光标所在位置的字符长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 光标所在位置的索引值。 |
| .value[1].f32 | 光标相对输入框的x坐标位值。 |
| .value[2].f32 | 光标相对输入框的y坐标位值。 |

## NODE_TEXT_AREA_CONTENT_RECT

```c
NODE_TEXT_AREA_CONTENT_RECT = 8016
```

获取已编辑文本内容区域相对组件的位置和大小。<br>
作为属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 水平方向横坐标。 |
| .value[1].f32 | 竖直方向纵坐标。 |
| .value[2].f32 | 内容宽度大小。 |
| .value[3].f32 | 内容高度大小。 |

## NODE_TEXT_AREA_CONTENT_LINE_COUNT

```c
NODE_TEXT_AREA_CONTENT_LINE_COUNT = 8017
```

获取已编辑文本内容的行数。<br>
作为属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 已编辑文本内容行数。 |

## NODE_TEXT_AREA_TEXT_SELECTION

```c
NODE_TEXT_AREA_TEXT_SELECTION = 8018
```

组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取、高亮显示。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 选中文本的起始位置。 |
| .value[1].i32 | 选中文本的终止位置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 选中文本的起始位置。 |
| .value[1].i32 | 选中文本的终止位置。 |

## NODE_TEXT_AREA_ENABLE_AUTO_FILL

```c
NODE_TEXT_AREA_ENABLE_AUTO_FILL = 8019
```

设置是否启用自动填充。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否启用自动填充，默认值true。<br>true表示启用，false表示不启用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用自动填充。 |

## NODE_TEXT_AREA_CONTENT_TYPE

```c
NODE_TEXT_AREA_CONTENT_TYPE = 8020
```

自动填充类型。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 参数类型[ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 参数类型[ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype)。 |

## NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS = 8021
```

设置输入框获取焦点时是否弹出键盘，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否弹出键盘。默认值true。<br>false表示获取焦点时不弹出键盘，true表示获取焦点时弹出键盘。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否弹出键盘。 |

## NODE_TEXT_AREA_NUMBER_OF_LINES

```c
NODE_TEXT_AREA_NUMBER_OF_LINES = 8022
```

设置该属性后，通过该属性计算TextArea组件的高度。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 设置numberOfLines的值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 设置numberOfLines的值。 |

## NODE_TEXT_AREA_LETTER_SPACING

```c
NODE_TEXT_AREA_LETTER_SPACING = 8023
```

设置该属性后，通过该属性调整TextArea组件的字符间距。接口支持设置，重置以及获取该属性。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 设置[letterSpacing](arkui-ts/ts-basic-components-text.md#letterspacing)的值，默认单位fp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 获取[letterSpacing](arkui-ts/ts-basic-components-text.md#letterspacing)的值，默认单位fp。 |

## NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024
```

设置TextArea组件是否开启输入预上屏。接口支持设置，重置以及获取该属性。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 设置是否开启输入预上屏。false表示不开启输入预上屏，true表示开启输入预上屏。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 获取是否开启输入预上屏。 |

## NODE_TEXT_AREA_HALF_LEADING

```c
NODE_TEXT_AREA_HALF_LEADING = 8025
```

设置文本将行间距平分至行的顶部与底部。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 18


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 设置文本是否将行间距平分至行的顶部与底部。默认值false。<br>true表示将行间距平分至行的顶部与底部，false表示不平分。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 设置文本是否将行间距平分至行的顶部与底部。 |

## NODE_TEXT_AREA_KEYBOARD_APPEARANCE

```c
NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026
```

设置输入框拉起的键盘样式。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)。 |

## NODE_TEXT_AREA_MAX_LINES

```c
NODE_TEXT_AREA_MAX_LINES = 8027
```

设置输入框内联模式编辑态时文本可显示的最大行数，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 内联输入风格编辑态时文本可显示的最大行数。内联模式下，默认值是3，<br>非内联模式下，默认值是+∞，不限制最大行数。设置为undefined时，最大行数设置为5。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 最大行数的数字。 |

## NODE_TEXT_AREA_LINE_SPACING

```c
NODE_TEXT_AREA_LINE_SPACING = 8028
```

设置输入框文本的行间距，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 文本的行间距的数字。默认值是0，单位fp。设置为undefined时，行间距设置为5。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 文本的行间距的数字，单位fp。 |

## NODE_TEXT_AREA_MIN_LINES

```c
NODE_TEXT_AREA_MIN_LINES = 8029
```

设置节点的最小行数。支持属性设置、属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 最小行数的数字。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 最小行数的数字。 |

## NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL

```c
NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL = 8030
```

设置支持滚动时节点的最大行数。支持属性设置、属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 支持滚动时的最大行数的数字。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 支持滚动时的最大行数的数字。 |

## NODE_TEXT_AREA_LINE_HEIGHT

```c
NODE_TEXT_AREA_LINE_HEIGHT = 8031
```

设置输入框文本的高度，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 文本的高度的数字。默认值是自适应字体大小，单位fp。设置为undefined时，文本的高度设置为5。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 文本的高度的数字，单位fp。 |

## NODE_TEXT_AREA_BAR_STATE

```c
NODE_TEXT_AREA_BAR_STATE = 8032
```

定义文本输入框滚动条状态。支持属性设置、属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 文本控制滚动条状态。参数类型为[ArkUI_BarState](capi-native-type-h.md#arkui_barstate)。默认值为ARKUI_BAR_STATE_AUTO。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 文本控制滚动条状态。参数类型为[ArkUI_BarState](capi-native-type-h.md#arkui_barstate)。 |

## NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR = 8033
```

开启选中词文本识别。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 开启选中词文本识别，true表示开启识别，false表示关闭识别。默认值：true。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否开启选中词文本识别。 |

## NODE_TEXT_AREA_SCROLL_BAR_COLOR

```c
NODE_TEXT_AREA_SCROLL_BAR_COLOR = 8035
```

设置输入框滚动条颜色，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 滚动条颜色数值。0xargb类型。默认值：0x66182431，显示为灰色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 滚动条颜色数值。 |

## NODE_TEXT_AREA_CUSTOM_KEYBOARD

```c
NODE_TEXT_AREA_CUSTOM_KEYBOARD = 8036
```

设置文本输入框的自定义键盘。支持属性设置、属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。 |
| .value[0]?.i32 | 设置自定义键盘是否支持避让功能。<br>true表示支持避让，false表示不支持避让。<br>默认值：false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .object | 自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。 |
| .value[0].i32 | 设置自定义键盘是否支持避让功能。 |

## NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE

```c
NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE = 8037
```

用于设置或获取文本区域控制器。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 23


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 文本内容基础控制器，参数类型为[ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .object | 文本内容基础控制器，参数类型为[ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)。 |

## NODE_TEXT_AREA_ELLIPSIS_MODE

```c
NODE_TEXT_AREA_ELLIPSIS_MODE = 8038
```

设置多行文本输入框中文本省略位置，支持属性设置，属性重置，属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 参数类型[ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode)。默认值为ARKUI_ELLIPSIS_MODE_END。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 参数类型[ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode)。 |

## NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION = 8039
```

设置TextArea文本排版时是否使能孤字优化，设置后通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局。使能后，它会调整换行点以尽可能避免孤立字符。孤字优化特性需在[ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.0.0


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否使能，true表示使能，false表示不使能。默认值false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否使能孤字优化。 |

## NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION = 8040
```

设置输入字符行首标点压缩开关，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 23


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否打开行首标点压缩开关。<br>true表示开启行首标点压缩，false表示关闭行首标点压缩。默认值false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否打开行首标点压缩开关。 |

## NODE_TEXT_AREA_INCLUDE_FONT_PADDING

```c
NODE_TEXT_AREA_INCLUDE_FONT_PADDING = 8041
```

设置多行输入框内文字是否在首行和尾行增加间距以避免文字截断。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 23


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 设置输入框内文字是否在首行和尾行增加间距以避免文字截断。true表示开启增加间距，false表示关闭增加间距。默认值：false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 输入框内文字是否在首行和尾行增加间距。true表示增加间距，false表示不增加间距。 |

## NODE_TEXT_AREA_FALLBACK_LINE_SPACING

```c
NODE_TEXT_AREA_FALLBACK_LINE_SPACING = 8042
```

针对多行文字叠加，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 23


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 支持行高基于文字实际高度自适应。true表示开启自适应，false表示关闭自适应。默认值：false。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否开启行高基于文字实际高度自适应。true表示开启自适应，false表示关闭自适应。 |

## NODE_TEXT_AREA_HORIZONTAL_SCROLLING

```c
NODE_TEXT_AREA_HORIZONTAL_SCROLLING = 8043
```

设置多行输入框在文本宽度超过输入框内容区宽度时是否启用水平滚动。默认值为false，文本会被输入框自动换行。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否启用水平滚动。true表示启用水平滚动，false表示不启用水平滚动。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用水平滚动。 |

## NODE_TEXT_AREA_DIRECTION

```c
NODE_TEXT_AREA_DIRECTION = 8044
```

多行输入框的文本排版方向。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 23


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 表示文本的排版方向，取[ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection)枚举值。默认值为ARKUI_TEXT_DIRECTION_DEFAULT。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 表示文本的排版方向，对应取值及含义请参考[ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection)枚举值。 |

## NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE = 8045
```

用于设置多行文本输入框内文本选中状态下的拖拽预览样式。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 23


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 文本选中状态下的拖拽预览样式。参数类型为[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .object | 文本选中状态下的拖拽预览样式。参数类型为[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)。 |

## NODE_TEXT_AREA_TEXT_OVERFLOW

```c
NODE_TEXT_AREA_TEXT_OVERFLOW = 8046
```

多行文本输入框中文本超长时的显示方式属性，支持属性设置，属性重置，属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 表示文本超长时的显示方式[ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow)。默认值为ARKUI_TEXT_OVERFLOW_CLIP。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 表示文本超长时的显示方式[ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow)。 |

## NODE_TEXT_AREA_DECORATION

```c
NODE_TEXT_AREA_DECORATION = 8047
```

定义多行输入框的文本装饰线样式与颜色，支持属性设置、属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 装饰样式配置项，为可选参数。参数类型为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .object | 装饰样式配置项。参数类型为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)。 |
