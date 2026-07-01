# ArkUI_NodeAttributeType（富文本类组件相关属性）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6; @hddgzw-->
<!--Designer: @xiangyuan6; @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## 概述

定义ArkUI在Native侧可以设置的富文本类组件相关属性样式集合，包含TextEditor组件属性设置。

**起始版本：** 24

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

## NODE_TEXT_EDITOR_ENTER_KEY_TYPE

```c
NODE_TEXT_EDITOR_ENTER_KEY_TYPE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR = 22000
```

TextEditor组件回车键类型，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 回车键类型，参数类型[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)，默认值为ARKUI_ENTER_KEY_TYPE_NEW_LINE。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 回车键类型，参数类型[ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype)。 |

## NODE_TEXT_EDITOR_CARET_COLOR

```c
NODE_TEXT_EDITOR_CARET_COLOR = 22001
```

TextEditor组件光标颜色，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 光标颜色，采用0xARGB格式，例如0xFFFF0000表示红色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 光标颜色，采用0xARGB格式。 |

## NODE_TEXT_EDITOR_SCROLL_BAR_COLOR

```c
NODE_TEXT_EDITOR_SCROLL_BAR_COLOR = 22002
```

TextEditor组件滚动条颜色，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .data[0].u32 | 滚动条颜色，采用0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .data[0].u32 | 滚动条颜色，采用0xARGB格式。 |

## NODE_TEXT_EDITOR_BAR_STATE

```c
NODE_TEXT_EDITOR_BAR_STATE = 22003
```

TextEditor组件滚动条显示模式，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 滚动条显示模式，参数类型[ArkUI_BarState](capi-native-type-h.md#arkui_barstate)，默认值为ARKUI_BAR_STATE_AUTO。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 滚动条显示模式，参数类型[ArkUI_BarState](capi-native-type-h.md#arkui_barstate)。 |

## NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR = 22004
```

TextEditor组件文本实体识别功能开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否启用文本实体识别功能，0表示禁用，1表示启用，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用了文本实体识别功能。 |

## NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG

```c
NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG = 22005
```

TextEditor组件识别配置，支持属性设置和属性重置。<br>
作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 识别配置，参数类型[ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)。 |

## NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS

```c
NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS = 22006
```

TextEditor组件扩展菜单选项，支持属性设置和属性重置。<br>
作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 扩展菜单选项，参数类型[ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md)。 |

## NODE_TEXT_EDITOR_PLACEHOLDER

```c
NODE_TEXT_EDITOR_PLACEHOLDER = 22007
```

TextEditor组件无输入时的提示文本选项，支持属性设置和属性重置。<br>
作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 无输入时的提示文本选项，参数类型[ArkUI_TextEditorPlaceholderOptions](capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md)。 |

## NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER

```c
NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER = 22008
```

TextEditor组件属性字符串控制器，支持属性设置。<br>
作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 属性字符串控制器，参数类型[ArkUI_TextEditorStyledStringController](capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md)。 |

## NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT = 22009
```

TextEditor组件预上屏功能开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否启用预上屏功能，0表示禁用，1表示启用，默认值为1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用预上屏功能，0表示禁用，1表示启用。 |

## NODE_TEXT_EDITOR_LAYOUT_MANAGER

```c
NODE_TEXT_EDITOR_LAYOUT_MANAGER = 22010
```

TextEditor组件TextLayoutManager获取，支持属性获取。<br>
作为属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**返回：**

| 类型 | 说明 |
| -- | -- |
| .object | 布局管理器，参数类型[ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md)。 |

## NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR = 22011
```

TextEditor组件文本选择识别AI菜单开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否启用文本选择识别的AI菜单，0表示禁用，1表示启用，默认值为1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用了文本选择识别的AI菜单。 |

## NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR = 22012
```

TextEditor组件选中内容背景颜色，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .data[0].u32 | 选中内容的背景颜色，采用0xARGB格式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .data[0].u32 | 选中内容的背景颜色，采用0xARGB格式。 |

## NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS = 22013
```

TextEditor组件非点击获焦时拉起输入法开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 非点击获焦时是否拉起输入法，0表示不拉起，1表示拉起，默认值为1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 非点击获焦时是否拉起输入法，0表示不拉起，1表示拉起。 |

## NODE_TEXT_EDITOR_MAX_LENGTH

```c
NODE_TEXT_EDITOR_MAX_LENGTH = 22014
```

TextEditor组件最大字符数，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 最大字符数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 最大字符数。 |

## NODE_TEXT_EDITOR_MAX_LINES

```c
NODE_TEXT_EDITOR_MAX_LINES = 22015
```

TextEditor组件内容最大行数，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 文本编辑器中内容的最大行数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 文本编辑器中内容的最大行数。 |

## NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK = 22016
```

TextEditor组件触觉反馈开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否在文本编辑器中启用触觉反馈，0表示不启用，1表示启用，默认值为1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用了触觉反馈，0表示不启用，1表示启用。 |

## NODE_TEXT_EDITOR_COPY_OPTIONS

```c
NODE_TEXT_EDITOR_COPY_OPTIONS = 22017
```

TextEditor组件复制选项，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 复制选项，参数类型[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)，默认值为ARKUI_COPY_OPTIONS_LOCAL_DEVICE。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 复制选项，参数类型[ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions)。 |

## NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE

```c
NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE = 22018
```

TextEditor组件键盘外观，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 键盘外观，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)，默认值为ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 键盘外观，参数类型[ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance)。 |

## NODE_TEXT_EDITOR_STOP_BACK_PRESS

```c
NODE_TEXT_EDITOR_STOP_BACK_PRESS = 22019
```

TextEditor组件是否阻止返回事件传播，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否阻止返回事件传播，0表示不阻止，1表示阻止，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否阻止返回事件传播，0表示不阻止，1表示阻止。 |

## NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING

```c
NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING = 22020
```

TextEditor组件中西文自动间距开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否启用中西文自动间距，0表示不启用，1表示启用，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用中西文自动间距，0表示不启用，1表示启用。 |

## NODE_TEXT_EDITOR_CUSTOM_KEYBOARD

```c
NODE_TEXT_EDITOR_CUSTOM_KEYBOARD = 22021
```

TextEditor组件自定义键盘，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。 |
| .value[0]?.i32 | 设置自定义键盘是否支持避让功能，0表示不支持，1表示支持，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .object | 自定义键盘，参数类型[ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md)。 |
| .value[0].i32 | 设置自定义键盘是否支持避让功能，0表示不支持，1表示支持。 |

## NODE_TEXT_EDITOR_BIND_SELECTION_MENU

```c
NODE_TEXT_EDITOR_BIND_SELECTION_MENU = 22022
```

TextEditor组件自定义文本选择菜单绑定，支持属性设置和属性重置。<br>
作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 文本选择菜单，参数类型[ArkUI_TextEditorSelectionMenuOptions](capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md)。 |

## NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING

```c
NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING = 22023
```

TextEditor组件首行末行防截断间距开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否添加间距，0表示不添加，1表示添加，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否添加间距，0表示不添加，1表示添加。 |

## NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING

```c
NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING = 22024
```

TextEditor组件行高自适应开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 行高是否自适应，0表示不自适应，1表示自适应，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 行高是否自适应，0表示不自适应，1表示自适应。 |

## NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION = 22025
```

TextEditor组件行首标点符号压缩开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否启用行首标点符号压缩，0表示不启用，1表示启用，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用行首标点符号压缩，0表示不启用，1表示启用。 |

## NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE = 22026
```

TextEditor组件选中拖拽预览样式，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 选中拖拽预览样式配置，参数类型[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .object | 选中拖拽预览样式配置，参数类型[ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md)。 |

## NODE_TEXT_EDITOR_SINGLE_LINE

```c
NODE_TEXT_EDITOR_SINGLE_LINE = 22027
```

TextEditor组件单行模式开关，支持属性设置、属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 24


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否启用单行模式，0表示不启用，1表示启用，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用单行模式，0表示不启用，1表示启用。 |

## NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION = 22028
```

设置TextEditor文本排版时是否使能孤字优化，设置后，通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局。使能后，它会调整换行点以尽可能避免孤立字符。孤字优化特性需在[ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak)属性为非ARKUI_WORD_BREAK_BREAK_ALL时生效。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.0.0


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否使能孤字优化，1表示使能，0表示不使能。默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否使能孤字优化。 |

## NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING

```c
NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING = 22029
```

设置TextEditor组件在文本宽度超过内容区宽度时是否启用水平滚动，支持属性设置，属性重置和属性获取。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.0.0


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否启用水平滚动。1表示启用水平滚动，0表示不启用水平滚动。默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否启用水平滚动。 |
