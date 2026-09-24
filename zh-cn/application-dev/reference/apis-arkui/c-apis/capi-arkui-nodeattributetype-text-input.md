# 文本输入

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TEXT_INPUT_PLACEHOLDER

```c
NODE_TEXT_INPUT_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT
```

**描述：**

单行文本输入框的默认提示文本内容属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：默认提示文本的内容。当需要在输入框显示提示信息引导用户输入时设置此属性，例如"请输入用户名"、"请输入密码"等。不设置时输入框无提示文本。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：默认提示文本的内容。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_TEXT

```c
NODE_TEXT_INPUT_TEXT
```

**描述：**

单行文本输入框的默认文本内容属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：输入框的默认文本内容，用于设置输入框初始显示的文本。当需要在输入框中预置文本时设置此属性，例如表单默认值、编辑初始内容等。不设置时输入框为空。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：默认文本的内容。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_CARET_COLOR

```c
NODE_TEXT_INPUT_CARET_COLOR
```

**描述：**

光标颜色属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：光标颜色数值，0xARGB格式，形如 0xFFFF0000 表示红色。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：光标颜色数值，0xARGB格式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_CARET_STYLE

```c
NODE_TEXT_INPUT_CARET_STYLE
```

**描述：**

光标风格属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：光标宽度数值，单位为vp。取值范围：[0, +∞)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：光标宽度数值，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_SHOW_UNDERLINE

```c
NODE_TEXT_INPUT_SHOW_UNDERLINE
```

**描述：**

单行文本输入框下划线属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示不展示下划线，1表示展示下划线。默认值0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示不展示下划线，1表示展示下划线。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_MAX_LENGTH

```c
NODE_TEXT_INPUT_MAX_LENGTH
```

**描述：**

输入框支持的最大文本数属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：最大文本数，无单位。取值范围：[0, +∞)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：最大文本数，无单位。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ENTER_KEY_TYPE

```c
NODE_TEXT_INPUT_ENTER_KEY_TYPE
```

**描述：**

回车键类型属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：回车键类型，具体枚举值请参考[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)。默认值ARKUI_ENTER_KEY_TYPE_DONE，显示为完成样式。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)，用于确定输入框回车键的显示样式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_PLACEHOLDER_COLOR

```c
NODE_TEXT_INPUT_PLACEHOLDER_COLOR
```

**描述：**

无输入时默认提示文本的颜色属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：颜色数值，0xARGB格式，形如 0xFFFF0000 表示红色。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：颜色数值，0xARGB格式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_PLACEHOLDER_FONT

```c
NODE_TEXT_INPUT_PLACEHOLDER_FONT
```

**描述：**

无输入时默认提示文本的字体配置（包括大小、字重、样式、字体列表）属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0]?.f32：可选字体大小数值，默认值16.0，单位为fp。取值范围：[0, +∞)。传入负数时不生效。</li> <li>.value[1]?.i32：可选字体样式，具体枚举值请参考[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。默认值为ARKUI_FONT_STYLE_NORMAL，表示标准字体样式。</li> <li>.value[2]?.i32：可选字体粗细样式，具体枚举值请参考[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。默认值ARKUI_FONT_WEIGHT_NORMAL，表示正常字体粗细。</li> <li>?.string：字体族内容，多个字体族之间使用逗号分隔，形如“字重；字体族1，字体族2”。不传入时使用系统默认字体族。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：字体大小数值，单位为fp。</li> <li>.value[1].i32：字体样式[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。</li> <li>.value[2].i32：字体粗细样式[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。</li> <li>.string：字体族内容，多个字体族之间使用逗号分隔。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS
```

**描述：**

聚焦时是否绑定输入法属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起，默认值为1。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_TYPE

```c
NODE_TEXT_INPUT_TYPE
```

**描述：**

输入框的类型属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：输入框类型，具体枚举值请参考[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)。默认值为ARKUI_TEXTINPUT_TYPE_NORMAL，表示基本输入模式。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：输入框类型枚举[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)，用于确定输入框的输入内容和键盘样式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR
```

**描述：**

输入框文本选中时的背景色属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：颜色数值，0xARGB格式，形如 0xFFFF0000 表示红色。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：颜色数值，0xARGB格式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_SHOW_PASSWORD_ICON

```c
NODE_TEXT_INPUT_SHOW_PASSWORD_ICON
```

**描述：**

密码输入模式时是否显示末尾图标属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示不显示图标，1表示显示图标，默认值为0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示不显示图标，1表示显示图标。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_EDITING

```c
NODE_TEXT_INPUT_EDITING
```

**描述：**

控制单行文本输入框编辑态属性，支持属性设置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示退出编辑态，1表示维持现状。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示退出编辑态，1表示维持现状。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_CANCEL_BUTTON

```c
NODE_TEXT_INPUT_CANCEL_BUTTON
```

**描述：**

单行文本右侧清除按钮样式属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：按钮样式[ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle)，默认值为ARKUI_CANCELBUTTON_STYLE_INPUT，表示清除按钮输入样式。</li> <li>.value[1]?.f32：图标大小数值，单位为vp。取值范围：[0, +∞)。传入负数时不生效。不传入时使用系统默认图标大小。</li> <li>.value[2]?.u32：按钮图标颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。不传入时使用系统默认图标颜色。</li> <li>?.string：按钮图标地址，入参内容为图片本地地址，例如 /pages/icon.png。不传入时使用系统默认清除图标。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：按钮样式[ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle)。</li> <li>.value[1].f32：图标大小数值，单位为vp。</li> <li>.value[2].u32：按钮图标颜色数值，0xargb格式。</li> <li>.string：按钮图标地址。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_TEXT_SELECTION

```c
NODE_TEXT_INPUT_TEXT_SELECTION
```

**描述：**

组件在获焦状态下，设置文本选中并高亮的区域，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：选中文本的起始位置，取值范围[0, 文本长度]，需小于终止位置才生效。</li> <li>.value[1].i32：选中文本的终止位置，取值范围[0, 文本长度]。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：选中文本的起始位置。</li> <li>.value[1].i32：选中文本的终止位置。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_UNDERLINE_COLOR

```c
NODE_TEXT_INPUT_UNDERLINE_COLOR
```

**描述：**

开启下划线时，支持配置下划线颜色。<br> 需先设置NODE_TEXT_INPUT_SHOW_UNDERLINE属性为1以开启下划线后，本属性设置才生效。主题配置的默认下划线颜色为0x33182431，表示深灰色，不透明度为20%。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：typing下划线颜色，必填，表示键入时的下划线颜色，0xargb类型。</li> <li>.value[1].u32：normal下划线颜色，必填，表示非特殊状态时下划线颜色，0xargb类型。</li> <li>.value[2].u32：error下划线颜色，必填，表示错误时下划线颜色，0xargb类型。</li> <li>.value[3].u32：disable下划线颜色，必填，表示禁用时下划线颜色，0xargb类型。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：typing下划线颜色，表示键入时的下划线颜色，0xargb类型。</li> <li>.value[1].u32：normal下划线颜色，表示非特殊状态时下划线颜色，0xargb类型。</li> <li>.value[2].u32：error下划线颜色，表示错误时下划线颜色，0xargb类型。</li> <li>.value[3].u32：disable下划线颜色，表示禁用时下划线颜色，0xargb类型。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ENABLE_AUTO_FILL

```c
NODE_TEXT_INPUT_ENABLE_AUTO_FILL
```

**描述：**

设置是否启用自动填充。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否启用自动填充，默认值1。 0表示不启用，1表示启用。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否启用自动填充。1表示启用，0表示不启用。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_CONTENT_TYPE

```c
NODE_TEXT_INPUT_CONTENT_TYPE
```

**描述：**

自动填充类型。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：参数类型[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)，用于自动填充场景指定内容类型。具体枚举值及适用场景请参考[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)枚举说明。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：自动填充内容类型枚举[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)，用于确定自动填充的内容类型。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_PASSWORD_RULES

```c
NODE_TEXT_INPUT_PASSWORD_RULES
```

**描述：**

定义生成密码的规则。在触发自动填充时，所设置的密码规则会透传给密码保险箱，用于新密码的生成。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：定义生成密码的规则，用于在触发自动填充时透传给密码保险箱以控制新密码的生成。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：定义生成密码的规则。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_SELECT_ALL

```c
NODE_TEXT_INPUT_SELECT_ALL
```

**描述：**

设置当初始状态，是否全选文本。不支持内联模式。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否全选文本，默认值：0。 1表示会全选文本，0表示不会全选文本。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否全选文本。1表示会全选文本，0表示不会全选文本。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_INPUT_FILTER

```c
NODE_TEXT_INPUT_INPUT_FILTER
```

**描述：**

通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。 单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：正则表达式，用于过滤用户输入内容。匹配表达式的输入允许显示，不匹配的输入将被过滤。当需要限制用户只能输入特定格式的字符时设置此属性，例如"^[a-zA-Z]+$"表示只允许字母，"^[0-9]+$"表示只允许数字。不设置时允许所有字符输入。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：正则表达式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_STYLE

```c
NODE_TEXT_INPUT_STYLE
```

**描述：**

设置输入框为默认风格或内联输入风格。内联输入风格是一种无边框的嵌入式输入样式，输入框直接融入页面内容中。 内联输入风格只支持输入框类型的枚举[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_NORMAL。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：参数类型[ArkUI_TextInputStyle](capi-text-input-h.md#arkui_textinputstyle)。内联输入风格只支持输入框类型[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_NORMAL。默认值为ARKUI_TEXTINPUT_STYLE_DEFAULT。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：输入框样式枚举[ArkUI_TextInputStyle](capi-text-input-h.md#arkui_textinputstyle)，用于确定输入框的显示样式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_CARET_OFFSET

```c
NODE_TEXT_INPUT_CARET_OFFSET
```

**描述：**

设置或获取光标所在位置信息。设置输入光标的位置。返回当前光标所在位置信息。 在当前帧更新光标位置同时调用该接口，该接口不生效。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：从字符串开始到光标所在位置的字符长度，取值范围[0, 文本长度]。超出范围时自动修正为边界值。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：光标所在位置的索引值。</li> <li>.value[1].f32：光标相对输入框的x坐标值，单位为px。</li> <li>.value[2].f32：光标相对输入框的y坐标值，单位为px。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_CONTENT_RECT

```c
NODE_TEXT_INPUT_CONTENT_RECT
```

**描述：**

获取已编辑文本内容区域相对组件的位置和大小。<br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：水平方向横坐标，单位为px。</li> <li>.value[1].f32：竖直方向纵坐标，单位为px。</li> <li>.value[2].f32：内容宽度大小，单位为px。</li> <li>.value[3].f32：内容高度大小，单位为px。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_CONTENT_LINE_COUNT

```c
NODE_TEXT_INPUT_CONTENT_LINE_COUNT
```

**描述：**

获取已编辑文本内容的行数。<br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：已编辑文本内容行数。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN
```

**描述：**

设置长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。默认值0。 设置为1时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，隐藏系统文本选择菜单。 设置为0时，显示系统文本选择菜单。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。1表示不弹出菜单，0表示弹出菜单。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_BLUR_ON_SUBMIT

```c
NODE_TEXT_INPUT_BLUR_ON_SUBMIT
```

**描述：**

设置输入框在submit状态下，触发回车键是否失焦。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：触发回车键后是否失焦。默认值1。 0表示不失焦，1表示失焦。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：触发回车键后是否失焦。1表示失焦，0表示不失焦。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_CUSTOM_KEYBOARD

```c
NODE_TEXT_INPUT_CUSTOM_KEYBOARD
```

**描述：**

设置自定义键盘。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li> <li>.value[0]?.i32：设置自定义键盘是否支持避让功能，默认值0。 1表示支持避让，0表示不支持避让。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li> <li>.value[0].i32：设置自定义键盘是否支持避让功能。0表示不支持避让，1表示支持避让。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_WORD_BREAK

```c
NODE_TEXT_INPUT_WORD_BREAK
```

**描述：**

文本断行规则属性，仅在内联输入风格编辑态生效，支持属性设置，属性重置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：参数类型[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)。仅在内联输入风格编辑态生效。默认值ARKUI_WORD_BREAK_BREAK_WORD。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本断行规则枚举[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)，用于确定文本的断行方式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS
```

**描述：**

设置输入框获取焦点时是否弹出键盘，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否弹出键盘。默认值1。 0表示获取焦点时不弹出键盘，1表示获取焦点时弹出键盘。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否弹出键盘。1表示弹出键盘，0表示不弹出键盘。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_NUMBER_OF_LINES

```c
NODE_TEXT_INPUT_NUMBER_OF_LINES
```

**描述：**

设置该属性后，通过该属性计算TextInput组件的高度。 例如：设置numberOfLines为3时，组件将默认显示足够容纳3行文本内容的高度。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置行数，取值范围[1, +∞)，用于通过该属性计算TextInput组件的高度。例如：设置为3时，组件将默认显示足够容纳3行文本内容的高度。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置numberOfLines的值。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_LETTER_SPACING

```c
NODE_TEXT_INPUT_LETTER_SPACING = 7032
```

**描述：**

设置该属性后，通过该属性调整TextInput组件的字符间距。 接口支持设置，重置以及获取该属性。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置letterSpacing的值，默认单位fp。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：获取letterSpacing的值，默认单位fp。</li> </ul>

**起始版本：** 15

### NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT = 7033
```

**描述：**

设置TextInput组件是否开启输入预上屏。 接口支持设置，重置以及获取该属性。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置是否开启输入预上屏。默认值1。 0表示不开启输入预上屏，1表示开启输入预上屏。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：获取是否开启输入预上屏。0表示不开启输入预上屏，1表示开启输入预上屏。</li> </ul>

**起始版本：** 15

### NODE_TEXT_INPUT_HALF_LEADING

```c
NODE_TEXT_INPUT_HALF_LEADING = 7034
```

**描述：**

设置文本将行间距平分至行的顶部与底部。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置文本是否将行间距平分至行的顶部与底部。默认值0。 1表示将行间距平分至行的顶部与底部，0表示不平分。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本行间距是否平分至行的顶部与底部。1表示平分，0表示不平分。</li> </ul>

**起始版本：** 18

### NODE_TEXT_INPUT_KEYBOARD_APPEARANCE

```c
NODE_TEXT_INPUT_KEYBOARD_APPEARANCE = 7035
```

**描述：**

设置输入框拉起的键盘样式。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)。具体枚举值请参考ArkUI_KeyboardAppearance枚举说明。默认值ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE，不使用沉浸式样式。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)。具体枚举值请参考ArkUI_KeyboardAppearance枚举说明。默认值ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE。</li> </ul>

**起始版本：** 15

### NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION

```c
NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036
```

**描述：**

设置是否启用自动填充动效。仅当输入框类型[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_PASSWORD、ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD或ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD时，该动效才生效。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否启用自动填充动效。启用之后，仅输入框类型的枚举[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_PASSWORD、ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD或ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD的输入框在进行自动填充时动效可生效。1表示启用，0表示不启用。默认值1。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否启用自动填充动效。0表示不启用，1表示启用。启用之后，仅输入框类型的枚举[ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype)设置为ARKUI_TEXTINPUT_TYPE_PASSWORD、ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD或ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD的输入框在进行自动填充时动效可生效。</li> </ul>

**起始版本：** 20

### NODE_TEXT_INPUT_LINE_HEIGHT

```c
NODE_TEXT_INPUT_LINE_HEIGHT = 7037
```

**描述：**

设置输入框文本的高度，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本的高度，单位fp。默认值是自适应字体大小。不传入该参数时，文本的高度设置为5fp。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本的高度，单位fp。</li> </ul>

**起始版本：** 20

### NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR = 7038
```

**描述：**

开启选中词文本识别。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：开启选中词文本识别，true表示开启识别，false表示关闭识别。默认值：true。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启选中词文本识别。</li> </ul>

**起始版本：** 22

### NODE_TEXT_INPUT_SHOW_COUNTER

```c
NODE_TEXT_INPUT_SHOW_COUNTER = 7040
```

**描述：**

设置输入的字符数超过阈值时是否显示计数器并设置计数器样式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启计数器。值为1表示开启计数器，值为0表示不开启计数器。</li> <li>.value[1]?.f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]，小数时向下取整，若超出取值范围，则接口属性设置不生效。默认值-1，即始终显示计数器。</li> <li>.value[2]?.i32：输入字符超出限制时高亮边框，1表示高亮边框，0表示不高亮边框。默认值1。</li> <li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启计数器。0表示不开启计数器，1表示开启计数器。</li> <li>.value[1].f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]。</li> <li>.value[2].i32：输入字符超出限制时高亮边框。0表示不高亮边框，1表示高亮边框。</li> <li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li> </ul>

**起始版本：** 22

### NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE

```c
NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE = 7041
```

**描述：**

用于设置或获取文本输入控制器。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：文本内容基础控制器。参数类型为[ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：文本内容基础控制器。参数类型为[ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)。</li> </ul>

**起始版本：** 23

### NODE_TEXT_INPUT_ELLIPSIS_MODE

```c
NODE_TEXT_INPUT_ELLIPSIS_MODE = 7042
```

**描述：**

设置单行文本输入框中文本省略位置，支持属性设置，属性重置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：参数类型[ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode)。默认值为ARKUI_ELLIPSIS_MODE_END。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：参数类型[ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode)。</li> </ul>

**起始版本：** 24

### NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION

```c
	  NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION = 7043
```

**描述：**

设置TextInput文本排版时是否使能孤字优化。使能后通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局，调整换行点以尽可能避免孤立字符。 注意：该特性需在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否使能孤字优化。该特性需在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。1表示使能，0表示不使能。默认值0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否使能孤字优化。0表示不使能，1表示使能。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION = 7044
```

**描述：**

设置输入字符行首标点压缩开关，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否打开行首标点压缩开关。1表示开启行首标点压缩，0表示关闭行首标点压缩。默认值0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否打开行首标点压缩开关。0表示关闭行首标点压缩，1表示开启行首标点压缩。</li> </ul>

**起始版本：** 23

### NODE_TEXT_INPUT_INCLUDE_FONT_PADDING

```c
NODE_TEXT_INPUT_INCLUDE_FONT_PADDING = 7045
```

**描述：**

设置单行输入框内文字是否在首行顶部和尾行底部增加间距以避免文字截断。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置输入框内文字是否在首行顶部和尾行底部增加间距以避免文字截断。1表示开启增加间距，0表示关闭增加间距。默认值：0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否在首行顶部和尾行底部增加间距。0表示不增加间距，1表示增加间距。</li> </ul>

**起始版本：** 23

### NODE_TEXT_INPUT_FALLBACK_LINE_SPACING

```c
NODE_TEXT_INPUT_FALLBACK_LINE_SPACING = 7046
```

**描述：**

针对多行文本显示场景，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。1表示开启自适应，0表示关闭自适应。默认值：0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启行高基于文字实际高度自适应。0表示关闭自适应，1表示开启自适应。</li> </ul>

**起始版本：** 23

### NODE_TEXT_INPUT_DIRECTION

```c
NODE_TEXT_INPUT_DIRECTION = 7047
```

**描述：**

单行输入框的文本排版方向。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：表示文本的排版方向，取[ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection)枚举值。默认值为ARKUI_TEXT_DIRECTION_DEFAULT。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：表示文本的排版方向，对应取值及含义请参考[ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection)枚举值。</li> </ul>

**起始版本：** 23

### NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE = 7048
```

**描述：**

用于设置文本输入框内文本选中状态下的拖拽预览样式。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：文本选中状态下的拖拽预览样式。参数类型为[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：文本选中状态下的拖拽预览样式。参数类型为[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。</li> </ul>

**起始版本：** 23

### NODE_TEXT_INPUT_TEXT_OVERFLOW

```c
NODE_TEXT_INPUT_TEXT_OVERFLOW = 7049
```

**描述：**

单行文本输入框中文本超长时的显示方式属性，支持属性设置，属性重置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：表示文本超长时的显示方式[ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow)。内联模式非编辑态下默认值为ARKUI_TEXT_OVERFLOW_ELLIPSIS，内联模式编辑态下默认值为ARKUI_TEXT_OVERFLOW_CLIP。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：表示文本超长时的显示方式[ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow)。</li> </ul>

**起始版本：** 24

### NODE_TEXT_INPUT_DECORATION

```c
NODE_TEXT_INPUT_DECORATION = 7050
```

**描述：**

定义单行输入框的文本装饰线样式与颜色，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：装饰样式配置项，为可选参数。参数类型为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)。不传入时不添加装饰线。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：装饰样式配置项。参数类型为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_INPUT_LINEAR_GRADIENT

```c
NODE_TEXT_INPUT_LINEAR_GRADIENT = 7051
```

**描述：**

设置文本输入框内文本线性渐变效果，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：线性渐变的起始角度，单位为deg。当线性渐变的方向为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)的ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，线性渐变的起始角度属性生效，否则按线性渐变的方向属性为主要布局方式。取值范围为(-∞,+∞)，0点方向顺时针旋转为正向角度，当超过360时，是按照360取余处理，默认值：180。</li> <li>.value[1].i32：线性渐变的方向，取值为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)枚举。设置除ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM之外的方向后，起始角度不生效。默认值：ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM。</li> <li>.value[2].i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li> <li>.object：指定位置处的渐变色颜色，参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。 - colors：渐变色颜色数组，元素为0xargb格式，形如0xFFFF0000表示红色。 - stops：指定颜色所处位置的数组，取值范围[0,1.0]，0表示容器开始处，1.0表示结尾处。建议递增设置。 - size：颜色个数，若小于colors数组长度则仅生效前size个颜色。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：线性渐变的起始角度，单位为deg。当线性渐变的方向为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)的ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，线性渐变的起始角度为设置值，其他情况均为默认值0。</li> <li>.value[1].i32：线性渐变的方向。对应取值及含义请参考[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)。</li> <li>.value[2].i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li> <li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。 colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。 size：生效后渐变色的颜色个数。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_INPUT_RADIAL_GRADIENT

```c
NODE_TEXT_INPUT_RADIAL_GRADIENT = 7052
```

**描述：**

设置文本输入框的文本径向渐变效果，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0]?.f32：径向渐变的中心点X轴坐标，即相对于当前文本输入框左上角的X轴坐标，单位为vp。默认值为文本输入框宽度的一半。</li> <li>.value[1]?.f32：径向渐变的中心点Y轴坐标，即相对于当前文本输入框左上角的Y轴坐标，单位为vp。默认值为文本输入框高度的一半。</li> <li>.value[2]?.f32：径向渐变的半径，单位为vp。取值范围[0, +∞)，默认值0。传入负数时不生效。</li> <li>.value[3]?.i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li> <li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。 colors：渐变色数组，元素为0xargb格式，形如0xFFFF0000表示红色。 stops：指定颜色所处位置的数组，取值范围[0,1.0]，0表示容器开始处，1.0表示结尾处。建议递增设置，若后一元素小于前一元素，则按等于前一元素的值处理。 size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置异常值。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0]?.f32：径向渐变的中心点X轴坐标，即相对于当前文本输入框左上角的X轴坐标，单位为vp。</li> <li>.value[1]?.f32：径向渐变的中心点Y轴坐标，即相对于当前文本输入框左上角的Y轴坐标，单位为vp。</li> <li>.value[2]?.f32：径向渐变的半径，单位为vp，默认值0。</li> <li>.value[3]?.i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li> <li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。 colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。 size：生效后渐变色的颜色个数。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_AREA_PLACEHOLDER

```c
NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA
```

**描述：**

多行文本输入框的默认提示文本内容属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：默认提示文本的内容。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：默认提示文本的内容。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_TEXT

```c
NODE_TEXT_AREA_TEXT
```

**描述：**

多行文本输入框的默认文本内容属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：默认文本的内容。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：默认文本的内容。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_MAX_LENGTH

```c
NODE_TEXT_AREA_MAX_LENGTH
```

**描述：**

输入框支持的最大文本数属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：最大文本数的数字。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：最大文本数的数字。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_PLACEHOLDER_COLOR

```c
NODE_TEXT_AREA_PLACEHOLDER_COLOR
```

**描述：**

无输入时默认提示文本的颜色属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：颜色数值，0xARGB格式，形如 0xFFFF0000 表示红色。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：颜色数值，0xARGB格式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_PLACEHOLDER_FONT

```c
NODE_TEXT_AREA_PLACEHOLDER_FONT
```

**描述：**

无输入时默认提示文本的字体配置（包括大小、字重、样式、字体列表）属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0]?.f32：可选字体大小数值，默认值16.0，单位为fp。</li> <li>.value[1]?.i32：可选字体样式[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL。</li> <li>.value[2]?.i32：可选字体粗细样式[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_NORMAL。</li> <li>?.string：字体族内容，多个字体族之间使用逗号分隔，形如“字重；字体族1，字体族2”。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：字体大小数值，单位为fp。</li> <li>.value[1].i32：字体样式[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。</li> <li>.value[2].i32：字体粗细样式[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。</li> <li>.string：字体族内容，多个字体族之间使用逗号分隔。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_CARET_COLOR

```c
NODE_TEXT_AREA_CARET_COLOR
```

**描述：**

光标颜色属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：光标颜色数值，0xARGB格式，形如 0xFFFF0000 表示红色。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：光标颜色数值，0xARGB格式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_EDITING

```c
NODE_TEXT_AREA_EDITING
```

**描述：**

控制多行文本输入框编辑态属性，支持属性设置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示退出编辑态，1表示维持现状。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示退出编辑态，1表示维持现状。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_TYPE

```c
NODE_TEXT_AREA_TYPE
```

**描述：**

输入框的类型属性，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：输入框类型枚举[ArkUI_TextAreaType](capi-text-area-h.md#arkui_textareatype)，默认值为ARKUI_TEXTAREA_TYPE_NORMAL。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：输入框类型枚举[ArkUI_TextAreaType](capi-text-area-h.md#arkui_textareatype)。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_SHOW_COUNTER

```c
NODE_TEXT_AREA_SHOW_COUNTER
```

**描述：**

设置输入的字符数超过阈值时是否显示计数器并设置计数器样式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启计数器。值为1时为开启。默认值0。</li> <li>.value[1]?.f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]，小数时向下取整，若超出取值范围，则接口属性设置不生效。默认值-1，即始终显示计数器。</li> <li>.value[2]?.i32：输入字符超出限制时是否高亮边框。1表示高亮边框，0表示不高亮边框。默认值1。</li> <li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启计数器。0表示不开启计数器，1表示开启计数器。</li> <li>.value[1].f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]。</li> <li>.value[2].i32：输入字符超出限制时是否高亮边框。0表示不高亮边框，1表示高亮边框。</li> <li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_AREA_SELECTION_MENU_HIDDEN
```

**描述：**

设置长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。 设置为1时，单击输入框光标、长按输入框、双击输入框、三击输入框或者右键输入框，隐藏系统文本选择菜单。 设置为0时，显示系统文本选择菜单。 默认值0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：长按、双击输入框或者右键输入框时，是否不弹出文本选择菜单。0表示显示系统文本选择菜单，1表示隐藏系统文本选择菜单。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_BLUR_ON_SUBMIT

```c
NODE_TEXT_AREA_BLUR_ON_SUBMIT
```

**描述：**

设置多行输入框在submit状态下，触发回车键是否失焦。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：触发回车键后是否失焦。 0表示触发回车键后不失焦，1表示触发回车键后失焦。 默认值0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：触发回车键后是否失焦。0表示触发回车键后不失焦，1表示触发回车键后失焦。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_INPUT_FILTER

```c
NODE_TEXT_AREA_INPUT_FILTER
```

**描述：**

通过正则表达式设置输入过滤器。匹配表达式的输入允许显示，不匹配的输入将被过滤。 单字符输入场景仅支持单字符匹配，多字符输入场景支持字符串匹配，例如粘贴。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：正则表达式，用于过滤用户输入内容。匹配表达式的输入允许显示，不匹配的输入将被过滤。当需要限制用户只能输入特定格式的字符时设置此属性，例如"^[a-zA-Z]+$"表示只允许字母，"^[0-9]+$"表示只允许数字。不设置时允许所有字符输入。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.string：正则表达式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR
```

**描述：**

设置文本选中底板颜色，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：颜色数值，0xARGB格式，形如 0xFFFF0000 表示红色。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].u32：颜色数值，0xARGB格式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ENTER_KEY_TYPE

```c
NODE_TEXT_AREA_ENTER_KEY_TYPE
```

**描述：**

设置输入法回车键类型，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_DONE。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：回车键类型枚举[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS
```

**描述：**

设置TextArea通过点击以外的方式获焦时，是否绑定输入法，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起。默认值为1。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：0表示聚焦不拉起输入法，1表示拉起。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_CARET_OFFSET

```c
NODE_TEXT_AREA_CARET_OFFSET
```

**描述：**

设置或获取光标所在位置信息。设置输入光标的位置。返回当前光标所在位置信息。 在当前帧更新光标位置同时调用该接口，该接口不生效。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：从字符串开始到光标所在位置的字符长度，取值范围[0, 文本长度]。超出范围时自动修正为边界值。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：光标所在位置的索引值。</li> <li>.value[1].f32：光标相对输入框的x坐标位值，单位为px。</li> <li>.value[2].f32：光标相对输入框的y坐标位值，单位为px。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_CONTENT_RECT

```c
NODE_TEXT_AREA_CONTENT_RECT
```

**描述：**

获取已编辑文本内容区域相对组件的位置和大小。<br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：水平方向横坐标，单位为px。</li> <li>.value[1].f32：竖直方向纵坐标，单位为px。</li> <li>.value[2].f32：内容宽度大小，单位为px。</li> <li>.value[3].f32：内容高度大小，单位为px。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_CONTENT_LINE_COUNT

```c
NODE_TEXT_AREA_CONTENT_LINE_COUNT
```

**描述：**

获取已编辑文本内容的行数。<br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：已编辑文本内容行数。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_TEXT_SELECTION

```c
NODE_TEXT_AREA_TEXT_SELECTION
```

**描述：**

组件在获焦状态下，调用该接口设置文本选择区域并高亮显示，且只有在selectionStart小于selectionEnd时，文字才会被选取、高亮显示。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：选中文本的起始位置，取值范围[0, 文本长度]，需小于终止位置才生效。</li> <li>.value[1].i32：选中文本的终止位置，取值范围[0, 文本长度]。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：选中文本的起始位置。</li> <li>.value[1].i32：选中文本的终止位置。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ENABLE_AUTO_FILL

```c
NODE_TEXT_AREA_ENABLE_AUTO_FILL
```

**描述：**

设置是否启用自动填充。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否启用自动填充。 1表示启用，0表示不启用。 默认值1。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否启用自动填充。1表示已启用，0表示未启用。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_CONTENT_TYPE

```c
NODE_TEXT_AREA_CONTENT_TYPE
```

**描述：**

自动填充类型。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：参数类型[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)。用于指定自动填充的内容类型，以便系统提供更准确的自动填充建议。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：参数类型[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)。用于指定自动填充的内容类型，以便系统提供更准确的自动填充建议。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS
```

**描述：**

设置输入框获取焦点时是否弹出键盘，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：获取焦点时是否弹出键盘。 1表示弹出键盘，0表示不弹出键盘。 默认值1。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：获取焦点时是否弹出键盘。1表示弹出键盘，0表示不弹出键盘。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_NUMBER_OF_LINES

```c
NODE_TEXT_AREA_NUMBER_OF_LINES
```

**描述：**

设置该属性后，通过该属性计算TextArea组件的高度。 例如：设置numberOfLines为3时，组件将默认显示足够容纳3行文本内容的高度。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置行数，取值范围[1, +∞)。用于通过该属性计算TextArea组件的高度。例如：设置为3时，组件将默认显示足够容纳3行文本内容的高度。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置numberOfLines的值。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_LETTER_SPACING

```c
NODE_TEXT_AREA_LETTER_SPACING = 8023
```

**描述：**

设置该属性后，通过该属性调整TextArea组件的字符间距。 接口支持设置，重置以及获取该属性。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：设置letterSpacing的值，默认单位fp。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：获取letterSpacing的值，默认单位fp。</li> </ul>

**起始版本：** 15

### NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024
```

**描述：**

设置TextArea组件是否开启输入预上屏。 接口支持设置，重置以及获取该属性。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置是否开启输入预上屏。 0表示不开启输入预上屏，1表示开启输入预上屏。 默认值1。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启输入预上屏。1表示已开启，0表示未开启。</li> </ul>

**起始版本：** 15

### NODE_TEXT_AREA_HALF_LEADING

```c
NODE_TEXT_AREA_HALF_LEADING = 8025
```

**描述：**

设置文本是否将行间距平分至行的顶部与底部。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置文本是否将行间距平分至行的顶部与底部。 1表示将行间距平分至行的顶部与底部，0表示不平分。 默认值0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本行间距是否平分至行的顶部与底部。1表示平分，0表示不平分。</li> </ul>

**起始版本：** 18

### NODE_TEXT_AREA_KEYBOARD_APPEARANCE

```c
NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026
```

**描述：**

设置输入框拉起的键盘样式。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)。默认值ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：键盘样式，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)。</li> </ul>

**起始版本：** 15

### NODE_TEXT_AREA_MAX_LINES

```c
NODE_TEXT_AREA_MAX_LINES = 8027
```

**描述：**

设置输入框内联模式编辑态时文本可显示的最大行数，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：内联输入风格编辑态时文本可显示的最大行数。取值范围[1, +∞)。 内联模式下，默认值是3，非内联模式下，默认值是+∞，不限制最大行数。 不传入该参数时，使用默认值。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：最大行数。</li> </ul>

**起始版本：** 20

### NODE_TEXT_AREA_LINE_SPACING

```c
NODE_TEXT_AREA_LINE_SPACING = 8028
```

**描述：**

设置输入框文本的行间距，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本的行间距，取值范围[0, +∞)，单位为fp。默认值是0。超出范围时自动修正为边界值。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本的行间距，单位fp。</li> </ul>

**起始版本：** 20

### NODE_TEXT_AREA_MIN_LINES

```c
NODE_TEXT_AREA_MIN_LINES = 8029
```

**描述：**

设置节点的最小行数。支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：最小行数，取值范围[1, +∞)。传入0或负数时参数不生效。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：最小行数，取值范围[1, +∞)。</li> </ul>

**起始版本：** 20

### NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL

```c
NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL = 8030
```

**描述：**

设置支持滚动时节点的最大行数。支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：支持滚动时的最大行数。取值范围[1, +∞)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：支持滚动时的最大行数。取值范围[1, +∞)。</li> </ul>

**起始版本：** 20

### NODE_TEXT_AREA_LINE_HEIGHT

```c
NODE_TEXT_AREA_LINE_HEIGHT = 8031
```

**描述：**

设置输入框文本的高度，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本的高度。默认值是自适应字体大小，单位fp。不传入该参数时，文本的高度设置为5fp。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本的高度，单位fp。</li> </ul>

**起始版本：** 20

### NODE_TEXT_AREA_BAR_STATE

```c
NODE_TEXT_AREA_BAR_STATE = 8032
```

**描述：**

定义文本输入框滚动条状态。支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本控制滚动条状态。参数类型为[ArkUI_BarState](capi-scroll-h.md#arkui_barstate)。默认值为ARKUI_BAR_STATE_AUTO。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：文本控制滚动条状态。参数类型为[ArkUI_BarState](capi-scroll-h.md#arkui_barstate)。</li> </ul>

**起始版本：** 22

### NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR = 8033
```

**描述：**

开启选中词文本识别。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：开启选中词文本识别，true表示开启识别，false表示关闭识别。默认值：true。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启选中词文本识别。</li> </ul>

**起始版本：** 22

### NODE_TEXT_AREA_SCROLL_BAR_COLOR

```c
NODE_TEXT_AREA_SCROLL_BAR_COLOR = 8035
```

**描述：**

设置输入框滚动条颜色，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.data[0].u32：滚动条颜色数值。0xARGB类型。默认值：0x66182431，显示为灰色。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.data[0].u32：滚动条颜色数值。</li> </ul>

**起始版本：** 22

### NODE_TEXT_AREA_CUSTOM_KEYBOARD

```c
NODE_TEXT_AREA_CUSTOM_KEYBOARD = 8036
```

**描述：**

设置文本输入框的自定义键盘。支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li> <li>.value[0]?.i32：设置自定义键盘是否支持避让功能， 1表示支持避让，0表示不支持避让。 默认值为0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。</li> <li>.value[0].i32：设置自定义键盘是否支持避让功能。0表示不支持避让，1表示支持避让。</li> </ul>

**起始版本：** 22

### NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE

```c
NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE = 8037
```

**描述：**

用于设置或获取文本区域控制器。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：文本内容基础控制器。参数类型为[ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：文本内容基础控制器。参数类型为[ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md)。</li> </ul>

**起始版本：** 23

### NODE_TEXT_AREA_ELLIPSIS_MODE

```c
NODE_TEXT_AREA_ELLIPSIS_MODE = 8038
```

**描述：**

设置多行文本输入框中文本省略位置，支持属性设置，属性重置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：参数类型[ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode)。默认值为ARKUI_ELLIPSIS_MODE_END。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：参数类型[ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode)。</li> </ul>

**起始版本：** 24

### NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION = 8039
```

**描述：**

设置TextArea文本排版时是否使能孤字优化。使能后通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局，调整换行点以尽可能避免孤立字符。 注意：该特性需在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否使能孤字优化。该特性需在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。1表示使能，0表示不使能。默认值0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否使能孤字优化。0表示不使能，1表示使能。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION = 8040
```

**描述：**

设置输入字符行首标点压缩开关，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否打开行首标点压缩开关。 1表示开启行首标点压缩，0表示关闭行首标点压缩。默认值0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否打开行首标点压缩开关。0表示关闭行首标点压缩，1表示开启行首标点压缩。</li> </ul>

**起始版本：** 23

### NODE_TEXT_AREA_INCLUDE_FONT_PADDING

```c
NODE_TEXT_AREA_INCLUDE_FONT_PADDING = 8041
```

**描述：**

设置多行输入框内文字是否在首行顶部和尾行底部增加间距以避免文字截断。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：设置输入框内文字是否在首行顶部和尾行底部增加间距以避免文字截断。1表示开启增加间距，0表示关闭增加间距。默认值：0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否在首行顶部和尾行底部增加间距。0表示不增加间距，1表示增加间距。</li> </ul>

**起始版本：** 23

### NODE_TEXT_AREA_FALLBACK_LINE_SPACING

```c
NODE_TEXT_AREA_FALLBACK_LINE_SPACING = 8042
```

**描述：**

针对多行文本显示场景，支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：支持行高基于文字实际高度自适应。此接口仅当行高小于文字实际高度时生效。1表示开启自适应，0表示关闭自适应。默认值：0。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启行高基于文字实际高度自适应。0表示关闭自适应，1表示开启自适应。</li> </ul>

**起始版本：** 23

### NODE_TEXT_AREA_HORIZONTAL_SCROLLING

```c
NODE_TEXT_AREA_HORIZONTAL_SCROLLING = 8043
```

**描述：**

设置多行输入框在文本宽度超过输入框内容区宽度时是否启用水平滚动。默认值为0，文本会被输入框自动换行。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否启用水平滚动。1表示启用水平滚动，0表示不启用水平滚动。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否启用水平滚动。1表示启用水平滚动，0表示不启用水平滚动。</li> </ul>

**起始版本：** 24

### NODE_TEXT_AREA_DIRECTION

```c
NODE_TEXT_AREA_DIRECTION = 8044
```

**描述：**

多行输入框的文本排版方向。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：表示文本的排版方向，取[ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection)枚举值。默认值为ARKUI_TEXT_DIRECTION_DEFAULT。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：表示文本的排版方向，对应取值及含义请参考[ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection)枚举值。</li> </ul>

**起始版本：** 23

### NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE = 8045
```

**描述：**

用于设置多行文本输入框内文本选中状态下的拖拽预览样式。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：文本选中状态下的拖拽预览样式。参数类型为[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：文本选中状态下的拖拽预览样式。参数类型为[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。</li> </ul>

**起始版本：** 23

### NODE_TEXT_AREA_TEXT_OVERFLOW

```c
NODE_TEXT_AREA_TEXT_OVERFLOW = 8046
```

**描述：**

多行文本输入框中文本超长时的显示方式属性，支持属性设置，属性重置，属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：表示文本超长时的显示方式[ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow)。默认值为ARKUI_TEXT_OVERFLOW_CLIP。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：表示文本超长时的显示方式[ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow)。</li> </ul>

**起始版本：** 24

### NODE_TEXT_AREA_DECORATION

```c
NODE_TEXT_AREA_DECORATION = 8047
```

**描述：**

定义多行输入框的文本装饰线样式与颜色，支持属性设置、属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：装饰样式配置项，为可选参数。参数类型为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.object：装饰样式配置项。参数类型为[OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md)。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_AREA_LINEAR_GRADIENT

```c
NODE_TEXT_AREA_LINEAR_GRADIENT = 8048
```

**描述：**

设置多行文本输入框的文本线性渐变效果，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：线性渐变的起始角度，单位为deg。当线性渐变的方向为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)的ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，线性渐变的起始角度属性生效，否则按线性渐变的方向属性为主要布局方式。取值范围为(-∞,+∞)，0点方向顺时针旋转为正向角度，当超过360时，是按照360取余处理，默认值：180。</li> <li>.value[1].i32：线性渐变的方向，取值为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)枚举。设置除ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM之外的方向后，起始角度不生效。默认值：ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM。</li> <li>.value[2].i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li> <li>.object：指定位置处的渐变色颜色，参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。 - colors：渐变色颜色数组，元素为0xargb格式，形如0xFFFF0000表示红色。 - stops：指定颜色所处位置的数组，取值范围[0,1.0]，0表示容器开始处，1.0表示结尾处。建议递增设置。 - size：颜色个数，若小于colors数组长度则仅生效前size个颜色。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].f32：线性渐变的起始角度，单位为deg。当线性渐变的方向为[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)的ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM时，线性渐变的起始角度为设置值，其他情况均为默认值0。</li> <li>.value[1].i32：线性渐变的方向。对应取值及含义请参考[ArkUI_LinearGradientDirection](capi-native-type-h.md#arkui_lineargradientdirection)。</li> <li>.value[2].i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li> <li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。 colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。 size：生效后渐变色的颜色个数。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_AREA_RADIAL_GRADIENT

```c
NODE_TEXT_AREA_RADIAL_GRADIENT = 8049
```

**描述：**

设置多行文本输入框的文本径向渐变效果，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0]?.f32：径向渐变的中心点X轴坐标，即相对于当前多行文本输入框左上角的X轴坐标，单位为vp。默认值为多行文本输入框宽度的一半。</li> <li>.value[1]?.f32：径向渐变的中心点Y轴坐标，即相对于当前多行文本输入框左上角的Y轴坐标，单位为vp。默认值为多行文本输入框高度的一半。</li> <li>.value[2]?.f32：径向渐变的半径，单位为vp。取值范围[0, +∞)，默认值0。传入负数时不生效。</li> <li>.value[3]?.i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li> <li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。 colors：渐变色数组，元素为0xargb格式，形如0xFFFF0000表示红色。 stops：指定颜色所处位置的数组，取值范围[0,1.0]，0表示容器开始处，1.0表示结尾处。建议递增设置，若后一元素小于前一元素，则按等于前一元素的值处理。 size：颜色个数，若小于colors数组长度则仅生效前size个颜色，不建议设置异常值。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0]?.f32：径向渐变的中心点X轴坐标，即相对于当前多行文本输入框左上角的X轴坐标，单位为vp。</li> <li>.value[1]?.f32：径向渐变的中心点Y轴坐标，即相对于当前多行文本输入框左上角的Y轴坐标，单位为vp。</li> <li>.value[2]?.f32：径向渐变的半径，单位为vp，默认值0。</li> <li>.value[3]?.i32：渐变的颜色是否重复着色，0表示不重复着色，1表示重复着色。默认值：0。</li> <li>.object：指定位置处的渐变色颜色。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。 colors：渐变色颜色数组，数组元素为0xargb格式，形如0xFFFF0000表示红色。 stops：stops表示指定颜色所处位置的数组，数组元素取值范围为[0,1.0]，0表示需要设置渐变色的容器的开始处，1.0表示容器的结尾处。 size：生效后渐变色的颜色个数。</li> </ul>

**起始版本：** 26.0.0


