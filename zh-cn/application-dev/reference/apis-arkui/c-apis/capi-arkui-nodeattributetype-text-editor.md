# 富文本

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TEXT_EDITOR_ENTER_KEY_TYPE

```c
NODE_TEXT_EDITOR_ENTER_KEY_TYPE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR
```

**描述：**

TextEditor组件回车键类型，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：回车键类型，参数类型[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_NEW_LINE。 <br>**返回：**<br><br>.value[0].i32：回车键类型，参数类型[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype)。

**起始版本：** 24

### NODE_TEXT_EDITOR_CARET_COLOR

```c
NODE_TEXT_EDITOR_CARET_COLOR
```

**描述：**

TextEditor组件光标颜色，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].u32：光标颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。 <br>**返回：**<br><br>.value[0].u32：光标颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。

**起始版本：** 24

### NODE_TEXT_EDITOR_SCROLL_BAR_COLOR

```c
NODE_TEXT_EDITOR_SCROLL_BAR_COLOR
```

**描述：**

TextEditor组件滚动条颜色，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.data[0].u32：滚动条颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。 <br>**返回：**<br><br>.data[0].u32：滚动条颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。

**起始版本：** 24

### NODE_TEXT_EDITOR_BAR_STATE

```c
NODE_TEXT_EDITOR_BAR_STATE
```

**描述：**

TextEditor组件滚动条显示模式，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：滚动条显示模式，参数类型[ArkUI_BarState](capi-scroll-h.md#arkui_barstate)，默认值为ARKUI_BAR_STATE_AUTO。 <br>**返回：**<br><br>.value[0].i32：滚动条显示模式，参数类型[ArkUI_BarState](capi-scroll-h.md#arkui_barstate)。

**起始版本：** 24

### NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR
```

**描述：**

TextEditor组件文本实体识别功能开关，启用后，文本中的电话号码、邮箱、链接等实体将被自动识别并标记为可交互内容。 配合NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG属性可自定义识别类型和交互行为。支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用文本实体识别功能，0表示禁用，1表示启用，默认值为0。推荐在需要自动识别并高亮文本中实体信息的场景下设置此属性。 <br>**返回：**<br><br>.value[0].i32：是否启用了文本实体识别功能，0表示禁用，1表示启用。

**起始版本：** 24

### NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG

```c
NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG
```

**描述：**

TextEditor组件文本实体识别配置，设置后，可配置识别类型、实体显示样式，并可选择是否开启长按预览功能。配合NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR属性使用， 支持属性设置和属性重置。 <br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.object：文本实体识别配置，设置后可指定需要识别的文本实体类型（如电话号码、邮箱、链接等）及识别后的交互行为。仅在启用文本实体识别功能( NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR设置为1)后传入此参数以自定义识别类型，不传入时使用系统默认识别配置。参数类型ArkUI_TextDataDetectorConfig。

**起始版本：** 24

### NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS

```c
NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS
```

**描述：**

TextEditor组件扩展菜单选项，支持属性设置和属性重置。 <br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.object：扩展菜单选项，设置后可自定义默认菜单项的行为，或添加自定义选项内容。参数类型[ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)。

**起始版本：** 24

### NODE_TEXT_EDITOR_PLACEHOLDER

```c
NODE_TEXT_EDITOR_PLACEHOLDER
```

**描述：**

TextEditor组件无输入时的提示文本选项，支持属性设置和属性重置。 <br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.object：无输入时的提示文本选项，参数类型ArkUI_TextEditorPlaceholderOptions。不传入时，编辑器无输入状态下不显示提示文本。

**起始版本：** 24

### NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER

```c
NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER
```

**描述：**

TextEditor组件属性字符串控制器，支持属性设置。设置后，可通过该控制器管理TextEditor中的内容、光标、选区、输入样式及编辑状态。 <br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.object：属性字符串控制器，参数类型ArkUI_TextEditorStyledStringController。

**起始版本：** 24

### NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT
```

**描述：**

TextEditor组件预上屏功能开关，启用后，组件内显示输入法输入过程中的拼音、笔画字符。支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用预上屏功能，0表示禁用，1表示启用，默认值为1。 <br>**返回：**<br><br>.value[0].i32：是否启用预上屏功能，0表示禁用，1表示启用。

**起始版本：** 24

### NODE_TEXT_EDITOR_LAYOUT_MANAGER

```c
NODE_TEXT_EDITOR_LAYOUT_MANAGER
```

**描述：**

TextEditor组件TextLayoutManager获取，获取后，可通过布局管理器查询文本的布局信息，如行数、行高和内容偏移等。支持属性获取。 <br>作为属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**返回：**<br><br>.object：布局管理器，可通过该管理器查询文本的布局信息。参数类型[ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)。

**起始版本：** 24

### NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR
```

**描述：**

TextEditor组件的AI菜单开关，用于控制选中特殊文本实体时是否弹出AI识别菜单。该功能支持属性的设置、重置与获取，启用后可基于选中文本内容提供智能识别及操作选项。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用文本选择识别的AI菜单，0表示禁用，1表示启用，默认值为1。 <br>**返回：**<br><br>.value[0].i32：是否启用了文本选择识别的AI菜单，0表示禁用，1表示启用。

**起始版本：** 24

### NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR
```

**描述：**

TextEditor组件选中内容背景颜色，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.data[0].u32：选中内容的背景颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。 <br>**返回：**<br><br>.data[0].u32：选中内容的背景颜色，采用0xARGB格式，例如0xFFFF0000表示红色。默认跟随系统主题。

**起始版本：** 24

### NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS
```

**描述：**

TextEditor组件非点击获焦时拉起输入法开关，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：非点击获焦时是否拉起输入法，0表示不拉起，1表示拉起，默认值为1。 <br>**返回：**<br><br>.value[0].i32：非点击获焦时是否拉起输入法，0表示不拉起，1表示拉起。

**起始版本：** 24

### NODE_TEXT_EDITOR_MAX_LENGTH

```c
NODE_TEXT_EDITOR_MAX_LENGTH
```

**描述：**

TextEditor组件最大字符数，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：文本编辑器允许输入的最大长度，取值范围为[0, +∞)，超出此限制后将阻止继续输入文本。设置为0、负数或未设置该属性时不限制输入长度。 <br>**返回：**<br><br>.value[0].i32：文本编辑器允许输入的最大长度。

**起始版本：** 24

### NODE_TEXT_EDITOR_MAX_LINES

```c
NODE_TEXT_EDITOR_MAX_LINES
```

**描述：**

TextEditor组件内容最大行数，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：文本编辑器最大行数限制，取值范围：(0, +∞)。设置为0、负数或未设置该属性时，取默认值UINT32_MAX，不限制行数。建议在需要固定显示高度的场景下设置该参数。 <br>**返回：**<br><br>.value[0].i32：文本编辑器最大行数限制。

**起始版本：** 24

### NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK
```

**描述：**

TextEditor组件触感反馈开关，启用后，在文本拖选等交互操作时将产生触感反馈震动响应，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否在文本编辑器中启用触感反馈，0表示不启用，1表示启用，默认值为1。 <br>**返回：**<br><br>.value[0].i32：是否启用了触感反馈，0表示不启用，1表示启用。

**起始版本：** 24

### NODE_TEXT_EDITOR_COPY_OPTIONS

```c
NODE_TEXT_EDITOR_COPY_OPTIONS
```

**描述：**

TextEditor组件复制选项，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：复制选项，参数类型[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)，默认值为ARKUI_COPY_OPTIONS_LOCAL_DEVICE。 <br>**返回：**<br><br>.value[0].i32：复制选项，参数类型[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)。

**起始版本：** 24

### NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE

```c
NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE
```

**描述：**

TextEditor组件键盘外观，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：键盘外观，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)，默认值为ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE。 <br>**返回：**<br><br>.value[0].i32：文本编辑器当前设置的键盘外观类型，参数类型[ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance)。

**起始版本：** 24

### NODE_TEXT_EDITOR_STOP_BACK_PRESS

```c
NODE_TEXT_EDITOR_STOP_BACK_PRESS
```

**描述：**

TextEditor组件是否阻止返回键事件向上层传播，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否阻止返回事件传播，0表示不阻止，1表示阻止，默认值为0。推荐在编辑器有未保存内容或需要拦截返回键防止意外退出的场景设置为1。 <br>**返回：**<br><br>.value[0].i32：是否阻止返回事件传播，0表示不阻止，1表示阻止。

**起始版本：** 24

### NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING

```c
NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING
```

**描述：**

TextEditor组件中西文自动间距开关，支持属性设置、属性重置和属性获取。适用于包含中英文混排内容的编辑场景，启用后可在中文与西文之间自动添加间距，改善混排文本的阅读体验。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用中西文自动间距，0表示不启用，1表示启用，默认值为0。推荐在包含中英文混排内容的编辑场景设置为1，以改善混排文本的阅读体验。 <br>**返回：**<br><br>.value[0].i32：是否启用中西文自动间距，0表示不启用，1表示启用。

**起始版本：** 24

### NODE_TEXT_EDITOR_CUSTOM_KEYBOARD

```c
NODE_TEXT_EDITOR_CUSTOM_KEYBOARD
```

**描述：**

TextEditor组件自定义键盘。当需要替换系统默认键盘时传入此参数（如数字键盘、表情键盘等特殊输入布局），不传入时使用系统默认键盘。支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md)。 <br>.value[0]?.i32：设置自定义键盘是否支持内容避让功能，即键盘弹出时页面内容自动调整位置以避免被键盘遮挡，0表示不支持，1表示支持，默认值为0。 <br>**返回：**<br><br>.object：自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md)。 <br>.value[0].i32：自定义键盘是否支持内容避让功能，即键盘弹出时页面内容自动调整位置以避免被键盘遮挡，0表示不支持，1表示支持。

**起始版本：** 24

### NODE_TEXT_EDITOR_BIND_SELECTION_MENU

```c
NODE_TEXT_EDITOR_BIND_SELECTION_MENU
```

**描述：**

TextEditor组件自定义文本选择菜单绑定，支持属性设置和属性重置。 <br>作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.object：自定义选择菜单，不传入时使用系统默认文本选择菜单。参数类型ArkUI_TextEditorSelectionMenuOptions。

**起始版本：** 24

### NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING

```c
NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING
```

**描述：**

TextEditor组件首行尾行防截断间距开关，启用后，在首行和尾行增加间距以避免文字截断，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否添加首行尾行防截断间距，0表示不添加，1表示添加，默认值为0。 <br>**返回：**<br><br>.value[0].i32：是否添加首行尾行防截断间距，0表示不添加，1表示添加。

**起始版本：** 24

### NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING

```c
NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING
```

**描述：**

TextEditor组件行高自适应开关，在多行文字叠加时，行高可以基于文字实际高度自适应，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：行高是否自适应，0表示不自适应，1表示自适应，默认值为0。 <br>**返回：**<br><br>.value[0].i32：行高是否自适应，0表示不自适应，1表示自适应。

**起始版本：** 24

### NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION
```

**描述：**

TextEditor组件行首标点符号压缩开关，启用后，行首的标点符号将缩减占位宽度，调整文本排版对齐效果，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用行首标点符号压缩，0表示不启用，1表示启用，默认值为0。 <br>**返回：**<br><br>.value[0].i32：是否启用行首标点符号压缩，0表示不启用，1表示启用。

**起始版本：** 24

### NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE
```

**描述：**

TextEditor组件选中拖拽预览样式，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.object：选中拖拽预览样式配置，参数类型[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。当需要自定义选中文本拖拽时的预览效果时传入此参数，不传入时使用系统默认拖拽预览样式。 <br>**返回：**<br><br>.object：选中拖拽预览样式配置，参数类型[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md)。

**起始版本：** 24

### NODE_TEXT_EDITOR_SINGLE_LINE

```c
NODE_TEXT_EDITOR_SINGLE_LINE
```

**描述：**

TextEditor组件单行模式开关，支持属性设置、属性重置和属性获取。启用单行模式后，NODE_TEXT_EDITOR_MAX_LINES属性设置的最大行数将不再生效。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用单行模式，0表示不启用，1表示启用，默认值为0。 <br>**返回：**<br><br>.value[0].i32：是否启用单行模式，0表示不启用，1表示启用。

**起始版本：** 24

### NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION
```

**描述：**

TextEditor组件孤字优化开关，支持属性设置、属性重置和属性获取。启用后会调整换行点以尽可能避免孤字。 仅在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用孤字优化，0表示不启用，1表示启用。默认值为0。仅在[ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。 <br>**返回：**<br><br>.value[0].i32：是否启用孤字优化，0表示不启用，1表示启用。

**起始版本：** 26.0.0

### NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING

```c
NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING
```

**描述：**

设置TextEditor组件在文本宽度超过内容区宽度时是否启用水平滚动，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用水平滚动，0表示不启用水平滚动，1表示启用水平滚动。默认值为0。 <br>**返回：**<br><br>.value[0].i32：是否启用水平滚动，0表示不启用水平滚动，1表示启用水平滚动。

**起始版本：** 26.0.0

### NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW
```

**描述：**

设置TextEditor组件是否启用行尾标点符号悬挂，支持属性设置、属性重置和属性获取。 <br>启用后，行尾单个标点符号超出排版宽度而不换行，避免行尾标点符号换行至下一行行首，从而改善文本排版效果。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用行尾标点符号悬挂，0表示不启用标点符号悬挂，1表示启用标点符号悬挂。默认值为0。 <br>**返回：**<br><br>.value[0].i32：是否启用行尾标点符号悬挂，0表示不启用行尾标点符号悬挂，1表示启用行尾标点符号悬挂。

**起始版本：** 26.0.0

### NODE_TEXT_EDITOR_TYPE

```c
NODE_TEXT_EDITOR_TYPE = 22031
```

**描述：**

设置TextEditor组件的文本编辑器类型，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：文本编辑器类型，数据类型[OH_ArkUI_TextEditorType](capi-rich-editor-h.md#oh_arkui_texteditortype)，默认值为OH_ARKUI_TEXT_EDITOR_TYPE_NORMAL。 <br>**返回：**<br><br>.value[0].i32：文本编辑器类型，数据类型[OH_ArkUI_TextEditorType](capi-rich-editor-h.md#oh_arkui_texteditortype)。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_SHOW_PASSWORD_ICON

```c
NODE_TEXT_EDITOR_SHOW_PASSWORD_ICON = 22032
```

**描述：**

设置密码输入模式下是否在文本末尾显示密码图标，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否在文本末尾显示密码图标，true表示显示密码图标，false表示不显示。 <br>**返回：**<br><br>.value[0].i32：是否在文本末尾显示密码图标，1表示显示密码图标，0表示不显示。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_PASSWORD_ICON

```c
NODE_TEXT_EDITOR_PASSWORD_ICON = 22033
```

**描述：**

设置TextEditor组件的密码图标，支持属性设置和属性重置。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].string：显示密码图标时的图片资源。 <br>.value[1].string：隐藏密码图标时的图片资源。 <br>**返回：**<br><br>.value[0].string：显示密码图标时的图片资源。 <br>.value[1].string：隐藏密码图标时的图片资源。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_ENABLE_AUTO_FILL

```c
NODE_TEXT_EDITOR_ENABLE_AUTO_FILL = 22034
```

**描述：**

设置TextEditor组件是否启用自动填充，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用自动填充，默认值0。0表示不启用，1表示启用。 <br>**返回：**<br><br>.value[0].i32：是否启用自动填充。1表示启用，0表示不启用。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_CONTENT_TYPE

```c
NODE_TEXT_EDITOR_CONTENT_TYPE = 22035
```

**描述：**

设置TextEditor组件的自动填充类型，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：参数类型[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)，用于自动填充场景指定内容类型。具体枚举值及适用场景请参考[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)枚举说明。 <br>**返回：**<br><br>.value[0].i32：自动填充内容类型枚举[ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype)，用于确定自动填充的内容类型。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_PASSWORD_RULES

```c
NODE_TEXT_EDITOR_PASSWORD_RULES = 22036
```

**描述：**

定义生成密码的规则。在触发自动填充时，所设置的密码规则会透传给密码保险箱，用于新密码的生成。支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.string：定义生成密码的规则，用于在触发自动填充时透传给密码保险箱以控制新密码的生成。 <br>**返回：**<br><br>.string：定义生成密码的规则。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_ENABLE_FILL_ANIMATION

```c
NODE_TEXT_EDITOR_ENABLE_FILL_ANIMATION = 22037
```

**描述：**

设置TextEditor组件是否启用自动填充动效，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否启用自动填充动效。1表示启用，0表示不启用。默认值1。 <br>**返回：**<br><br>.value[0].i32：是否启用自动填充动效。1表示启用，0表示不启用。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_SHOW_UNDERLINE

```c
NODE_TEXT_EDITOR_SHOW_UNDERLINE = 22038
```

**描述：**

设置TextEditor组件是否显示下划线，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否显示下划线，0表示不显示，1表示显示。默认值为0。 <br>**返回：**<br><br>.value[0].i32：是否显示下划线。1表示显示，0表示不显示。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_UNDERLINE_COLOR

```c
NODE_TEXT_EDITOR_UNDERLINE_COLOR = 22039
```

**描述：**

开启下划线时，支持配置下划线颜色，支持属性设置、属性重置和属性获取。 <br>需先设置NODE_TEXT_EDITOR_SHOW_UNDERLINE属性为1以开启下划线后，本属性设置才生效。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].u32：typing下划线颜色，表示键入时的下划线颜色，0xARGB类型。 <br>.value[1].u32：normal下划线颜色，表示非特殊状态时下划线颜色，0xARGB类型。 <br>.value[2].u32：error下划线颜色，表示错误时下划线颜色，0xARGB类型。 <br>.value[3].u32：disable下划线颜色，表示禁用时下划线颜色，0xARGB类型。 <br>**返回：**<br><br>.value[0].u32：typing下划线颜色，表示键入时的下划线颜色，0xARGB类型。 <br>.value[1].u32：normal下划线颜色，表示非特殊状态时下划线颜色，0xARGB类型。 <br>.value[2].u32：error下划线颜色，表示错误时下划线颜色，0xARGB类型。 <br>.value[3].u32：disable下划线颜色，表示禁用时下划线颜色，0xARGB类型。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_CARET_STYLE

```c
NODE_TEXT_EDITOR_CARET_STYLE = 22040
```

**描述：**

设置TextEditor组件的光标宽度，支持属性设置、属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].f32：光标宽度，单位vp。 <br>**返回：**<br><br>.value[0].f32：光标宽度，单位vp。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_SELECT_ALL

```c
NODE_TEXT_EDITOR_SELECT_ALL = 22041
```

**描述：**

设置TextEditor组件在初始状态时是否全选文本，支持属性设置、属性重置和属性获取。 <br>仅在首次获焦并完成布局阶段时触发全选。窗口恢复获焦时不执行全选。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否全选文本，默认值为0。1表示会全选文本，0表示不会全选文本。 <br>**返回：**<br><br>.value[0].i32：是否全选文本。1表示会全选文本，0表示不会全选文本。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_BLUR_ON_SUBMIT

```c
NODE_TEXT_EDITOR_BLUR_ON_SUBMIT = 22042
```

**描述：**

设置TextEditor组件在提交时是否失焦，支持属性设置、属性重置和属性获取。 <br>仅在EnterKeyType为NEW_LINE时按Enter键生效：设置为1时关闭键盘并失焦，不插入换行；设置为0时插入换行，不失焦。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否在提交时失焦，默认值为0。1表示提交时失焦，0表示提交时不失焦。 <br>**返回：**<br><br>.value[0].i32：是否在提交时失焦。1表示提交时失焦，0表示提交时不失焦。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_CONTENT_RECT

```c
NODE_TEXT_EDITOR_CONTENT_RECT = 22043
```

**描述：**

获取TextEditor组件编辑内容区域的位置和大小，仅支持属性获取。 <br>作为属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**返回：**<br><br>.value[0].f32：编辑内容区域的x轴偏移。 <br>.value[1].f32：编辑内容区域的y轴偏移。 <br>.value[2].f32：编辑内容区域的宽度。 <br>.value[3].f32：编辑内容区域的高度。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_EDITOR_SELECTION_MENU_HIDDEN = 22044
```

**描述：**

设置TextEditor组件是否隐藏选择菜单，支持属性设置、属性重置和属性获取。 <br>设置为1时，长按、双击或右击时不弹出选择菜单，但不影响选区手柄。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否隐藏选择菜单，默认值为0。1表示隐藏，0表示不隐藏。 <br>**返回：**<br><br>.value[0].i32：是否隐藏选择菜单。1表示隐藏，0表示不隐藏。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_ENABLE_SKIP_PREVIEW_LONG_PRESS

```c
NODE_TEXT_EDITOR_ENABLE_SKIP_PREVIEW_LONG_PRESS = 22045
```

**描述：**

设置TextEditor组件是否跳过长按预览态直接进入编辑态，支持属性设置、属性重置和属性获取。 <br>设置为1时，长按后直接进入编辑态（键盘弹出、光标闪烁），跳过预览态。双击行为不受影响。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.value[0].i32：是否跳过长按预览态，默认值为0。1表示跳过预览态，0表示不跳过。 <br>**返回：**<br><br>.value[0].i32：是否跳过长按预览态。1表示跳过预览态，0表示不跳过。

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_CANCEL_BUTTON

```c
NODE_TEXT_EDITOR_CANCEL_BUTTON = 22046
```

**描述：**

设置TextEditor组件的清除按钮样式属性，支持属性设置，属性重置和属性获取。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：按钮样式[ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle)，默认值为ARKUI_CANCELBUTTON_STYLE_INPUT，表示清除按钮输入样式。</li> <li>.value[1]?.f32：图标大小数值，单位为vp。取值范围：[0, +∞)。传入负数时不生效。不传入时使用系统默认图标大小。</li> <li>.value[2]?.u32：按钮图标颜色数值，0xargb格式，形如 0xFFFF0000 表示红色。不传入时使用系统默认图标颜色。</li> <li>?.string：按钮图标地址，入参内容为图片本地地址，例如 /pages/icon.png。不传入时使用系统默认清除图标。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：按钮样式[ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle)。</li> <li>.value[1].f32：图标大小数值，单位为vp。</li> <li>.value[2].u32：按钮图标颜色数值，0xargb格式。</li> <li>.string：按钮图标地址。</li> </ul>

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_SHOW_COUNTER

```c
NODE_TEXT_EDITOR_SHOW_COUNTER = 22047
```

**描述：**

设置TextEditor组件输入的字符数超过阈值时是否显示计数器并设置计数器样式，支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启计数器。值为1表示开启计数器，值为0表示不开启计数器。</li> <li>.value[1]?.f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]，小数时向下取整，若超出取值范围，则接口属性设置不生效。默认值-1，即始终显示计数器。</li> <li>.value[2]?.i32：输入字符超出限制时高亮边框，1表示高亮边框，0表示不高亮边框。默认值1。</li> <li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li> </ul><br> **属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式：**<br><ul> <li>.value[0].i32：是否开启计数器。0表示不开启计数器，1表示开启计数器。</li> <li>.value[1].f32：可输入字符数占最大字符限制的百分比值，超过此值时显示计数器，取值范围[1, 100]。</li> <li>.value[2].i32：输入字符超出限制时高亮边框。0表示不高亮边框，1表示高亮边框。</li> <li>.object：计数器配置，配置属性为文本输入框未达到最大字符数时计数器的颜色以及超出最大字符数时计数器的颜色。参数类型为 [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md)。</li> </ul>

**起始版本：** 26.2.0

### NODE_TEXT_EDITOR_INPUT_FILTER

```c
NODE_TEXT_EDITOR_INPUT_FILTER = 22048
```

**描述：**

设置TextEditor组件的输入过滤正则表达式，支持属性设置、属性重置和属性获取。 <br>该属性仅在spanString模式下生效（包含单行和多行模式）。 <br>当同时设置inputFilter和maxLength时，过滤优先级为：先inputFilter过滤，再maxLength截断。 <br>正则表达式变更时，已有内容会被静默重新过滤（与TextInput行为一致）。 <br>非字符内容（ImageSpan/SymbolSpan/BuilderSpan）在正则匹配时被视为\uFFFC字符。 <br>作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。 <br>**参数：**<br><br>.string：输入过滤的正则表达式字符串。仅允许匹配正则白名单的字符输入。空字符串等效于不设置过滤。 <br>**返回：**<br><br>.string：当前设置的输入过滤正则表达式字符串。

**起始版本：** 26.2.0


