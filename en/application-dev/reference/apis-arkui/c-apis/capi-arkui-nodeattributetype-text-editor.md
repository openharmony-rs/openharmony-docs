# Text Editor

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_EDITOR_ENTER_KEY_TYPE

```c
NODE_TEXT_EDITOR_ENTER_KEY_TYPE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR
```

**Description**

Type of the **Enter** key of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Type of the **Enter** key. The parameter type is [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype). The default value is **ARKUI_ENTER_KEY_TYPE_NEW_LINE**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Type of the **Enter** key. The parameter type is [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype).</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_CARET_COLOR

```c
NODE_TEXT_EDITOR_CARET_COLOR
```

**Description**

Caret color of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: Caret color, in 0xARGB format. For example, **0xFFFF0000** indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Caret color, in 0xARGB format.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_SCROLL_BAR_COLOR

```c
NODE_TEXT_EDITOR_SCROLL_BAR_COLOR
```

**Description**

Scroll bar color of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.data[0].u32: Scroll bar color, in 0xARGB format.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.data[0].u32: Scroll bar color, in 0xARGB format.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_BAR_STATE

```c
NODE_TEXT_EDITOR_BAR_STATE
```

**Description**

Scroll bar display mode of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Scroll bar display mode of the text area. The parameter type is [ArkUI_BarState](capi-scroll-h.md#arkui_barstate). The default value is **ARKUI_BAR_STATE_AUTO**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Scroll bar display mode of the text area. The parameter type is [ArkUI_BarState](capi-scroll-h.md#arkui_barstate).</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR
```

**Description**

Whether to enable text entity recognition for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable text entity recognition. The value **1** indicates to enable text entity recognition, and **0** indicates the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether text entity recognition is enabled.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG

```c
NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG
```

**Description**

Recognition configuration for the **TextEditor** component. This attribute can be set and reset as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Recognition configuration. The parameter type is ArkUI_TextDataDetectorConfig.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS

```c
NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS
```

**Description**

Extended menu options for the **TextEditor** component. This attribute can be set and reset as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Extended menu options. The parameter type is [ArkUI_TextEditMenuOptions](capi-arkui-nativemodule-arkui-texteditmenuoptions.md).</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_PLACEHOLDER

```c
NODE_TEXT_EDITOR_PLACEHOLDER
```

**Description**

Placeholder options when there is no input for the **TextEditor** component. This attribute can be set and reset as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Placeholder options when there is no input. The parameter type is ArkUI_TextEditorPlaceholderOptions.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER

```c
NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER
```

**Description**

Styled string controller of the **TextEditor** component. This attribute can be set as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Styled string controller. The parameter type is ArkUI_TextEditorStyledStringController.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT
```

**Description**

Whether to enable preview text for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable preview text. The value **1** indicates to enable preview text, and **0** indicates the opposite. The default value is **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether preview text is enabled. The value **1** indicates preview text is enabled, and **0** indicates the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_LAYOUT_MANAGER

```c
NODE_TEXT_EDITOR_LAYOUT_MANAGER
```

**Description**

**TextLayoutManager** of the **TextEditor** component. This attribute can be obtained as required through APIs. **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Layout manager. The parameter type is [ArkUI_TextLayoutManager](capi-arkui-nativemodule-arkui-textlayoutmanager.md).</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR
```

**Description**

Whether to enable the AI menu for text selection and recognition of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable the AI menu for text selection and recognition. The value **1** means to enable, and **0** means the opposite. The default value is **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the AI menu is enabled for text selection and recognition.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR
```

**Description**

Background color of the selected content in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.data[0].u32: Background color of the selected content, in 0xARGB format.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.data[0].u32: Background color of the selected content, in 0xARGB format.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS
```

**Description**

Whether to enable the input method when the focus is obtained in a way other than by clicking in the **<br>TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable the input method when the focus is obtained in a way other than clicking. The value **1** means to enable, and **0** means the opposite. The default value is **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the input method is enabled when the focus is obtained in a way other than clicking. The value **1** indicates the input method is enabled, and **0** indicates the input method is disabled.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_MAX_LENGTH

```c
NODE_TEXT_EDITOR_MAX_LENGTH
```

**Description**

Maximum number of characters in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Maximum number of characters.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Maximum number of characters.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_MAX_LINES

```c
NODE_TEXT_EDITOR_MAX_LINES
```

**Description**

Maximum number of lines in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Maximum number of lines in the text editor.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Maximum number of lines in the text editor.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK
```

**Description**

Whether to enable haptic feedback of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable haptic feedback in the text editor. The value **1** means to enable, and ** 0** means the opposite. The default value is **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether haptic feedback is enabled. The value **1** indicates haptic feedback is enabled, and **0** indicates the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_COPY_OPTIONS

```c
NODE_TEXT_EDITOR_COPY_OPTIONS
```

**Description**

Copy options of the **TextEditor** component, which can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Copy options. The parameter type is [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions). The default value is ** ARKUI_COPY_OPTIONS_LOCAL_DEVICE**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Copy options. The parameter type is [ArkUI_CopyOptions](capi-native-type-h.md#arkui_copyoptions).</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE

```c
NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE
```

**Description**

Keyboard appearance of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance). The default value is **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance).</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_STOP_BACK_PRESS

```c
NODE_TEXT_EDITOR_STOP_BACK_PRESS
```

**Description**

Whether the **TextEditor** component blocks the propagation of return events. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to block the propagation of return events. The value **1** indicates to block, and ** 0** indicates the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the propagation of return events is blocked. The value **1** indicates that the propagation of return events is blocked, and **0** indicates the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING

```c
NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING
```

**Description**

Whether to enable automatic spacing for Chinese and Western characters in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable automatic spacing. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether automatic spacing is enabled. The value **1** indicates automatic spacing is enabled, and **0** indicates the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_CUSTOM_KEYBOARD

```c
NODE_TEXT_EDITOR_CUSTOM_KEYBOARD
```

**Description**

Custom keyboard of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md).</li> <li>.value[0]?.i32: Whether the custom keyboard supports avoidance. The value **0** indicates no, and the value * *1** indicates yes. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md).</li> <li>.value[0].i32: Whether the custom keyboard supports avoidance. The value **0** indicates no, and the value ** 1** indicates yes.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_BIND_SELECTION_MENU

```c
NODE_TEXT_EDITOR_BIND_SELECTION_MENU
```

**Description**

Binds the custom text selection menu of the **TextEditor** component. This attribute can be set and reset as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Text selection menu. The parameter type is ArkUI_TextEditorSelectionMenuOptions.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING

```c
NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING
```

**Description**

Whether to add spacing to the first and last lines of the **TextEditor** component to prevent text truncation. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to add spacing. The value **1** means to add spacing, and **0** means not to add spacing. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether spacing is added. The value **1** means that spacing is added, and **0** means spacing is not added.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING

```c
NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING
```

**Description**

Whether to enable line height adaptation of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable line height adaptation. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether line height adaptation is enabled. The value **1** means line height adaptation is enabled, and **0** means the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION
```

**Description**

Whether to enable punctuation compression for the beginning of a line in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable punctuation compression. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether punctuation compression is enabled. The value **1** means punctuation compression is enabled, and **0** means the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE
```

**Description**

Selected drag preview style of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Selected drag preview style configuration. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Selected drag preview style configuration. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_SINGLE_LINE

```c
NODE_TEXT_EDITOR_SINGLE_LINE
```

**Description**

Whether to enable single-line mode for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable single-line mode. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether single-line mode is enabled. The value **1** means single-line mode is enabled, and ** 0** means the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION
```

**Description**

Sets whether to enable orphan character optimization for text layout in **TextEditor**. After setting,text layout is improved by more efficiently handling orphan characters (the first character of the last line of a paragraph). When enabled, it adjusts line break points to avoid orphan characters as much as possible. The orphan character optimization feature only works when [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) is not **ARKUI_WORD_BREAK_BREAK_ALL**. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether orphan character optimization is enabled.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING

```c
NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING
```

**Description**

Sets whether to enable horizontal scrolling for the **TextEditor** component when the text width exceeds the content area width. This attribute can be set, reset, and obtained as required through APIs. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable horizontal scrolling. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether horizontal scrolling is enabled.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW
```

**Description**

Sets whether to enable punctuation overflow at the end of a line. <br>This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow, the default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_EDITOR_TYPE

```c
NODE_TEXT_EDITOR_TYPE = 22031
```

**Description**

Defines the text editor type. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: text editor type [OH_ArkUI_TextEditorType](capi-rich-editor-h.md#oh_arkui_texteditortype). The default value is <b>OH_ARKUI_TEXT_EDITOR_TYPE_NORMAL</b>.<br> Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: text editor type [OH_ArkUI_TextEditorType](capi-rich-editor-h.md#oh_arkui_texteditortype).

**Since**: 26.2.0

### NODE_TEXT_EDITOR_SHOW_PASSWORD_ICON

```c
NODE_TEXT_EDITOR_SHOW_PASSWORD_ICON = 22032
```

**Description**

Defines whether to display the password icon at the end of the password text editor. This attribute can be set, reset, and obtained as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].i32: whether to display the password icon at the end of the password text editor. The value <b>true</b> means to display the password icon, and <b>false</b> means the opposite. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].i32: The value <b>1</b> means to display the password icon, and <b>0</b> means the opposite.

**Since**: 26.2.0

### NODE_TEXT_EDITOR_PASSWORD_ICON

```c
NODE_TEXT_EDITOR_PASSWORD_ICON = 22033
```

**Description**

Defines the password icon of the text editor. This attribute can be set and reset as required through APIs.<br> Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute: .value[0].string: show icon image source. .value[1].string: hide icon image source. Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): .value[0].string: show icon image source. .value[1].string: hide icon image source.

**Since**: 26.2.0

### NODE_TEXT_EDITOR_ENABLE_AUTO_FILL

```c
NODE_TEXT_EDITOR_ENABLE_AUTO_FILL = 22034
```

**Description**

Sets whether to enable autofill. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable autofill. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether autofill is enabled. The value **1** means enabled, and **0** means disabled.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_CONTENT_TYPE

```c
NODE_TEXT_EDITOR_CONTENT_TYPE = 22035
```

**Description**

Sets the autofill type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: autofill type, used to specify the content type for autofill scenarios. <br>The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype). For details about the enum values and applicable scenarios, see [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: autofill type, used to determine the autofill content type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype).</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_PASSWORD_RULES

```c
NODE_TEXT_EDITOR_PASSWORD_RULES = 22036
```

**Description**

Defines the rules for generating passwords. When autofill is used, these rules are transparently transmitted to Password Vault for generating a new password. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: rules for generating passwords, used to control new password generation by being transparently transmitted to the Password Vault when autofill is triggered.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: rules for generating passwords.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_ENABLE_FILL_ANIMATION

```c
NODE_TEXT_EDITOR_ENABLE_FILL_ANIMATION = 22037
```

**Description**

Sets whether to enable the autofill animation. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable the autofill animation. The value **1** means to enable, and **0** means the opposite. The default value is **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the autofill animation is enabled. The value **1** means enabled, and **0** means disabled.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_SHOW_UNDERLINE

```c
NODE_TEXT_EDITOR_SHOW_UNDERLINE = 22038
```

**Description**

Sets whether to show the underline. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to show the underline. The value **1** means to show, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the underline is shown. The value **1** means shown, and **0** means not shown.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_UNDERLINE_COLOR

```c
NODE_TEXT_EDITOR_UNDERLINE_COLOR = 22039
```

**Description**

Sets the color of the underline. This attribute can be set, reset, and obtained as required through APIs. This attribute takes effect only after NODE_TEXT_EDITOR_SHOW_UNDERLINE is set to **1**.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color of the underline applied to the text being typed in. The value is in 0xARGB format.</li> <li>.value[1].u32: color of the underline applied to the text in the normal state. The value is in 0xARGB format.</li> <li>.value[2].u32: color of the underline applied to the text when an error is detected. The value is in 0xARGB format.</li> <li>.value[3].u32: color of the underline applied to the text when it is disabled. The value is in 0xARGB format.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color of the underline applied to the text being typed in. The value is in 0xARGB format.</li> <li>.value[1].u32: color of the underline applied to the text in the normal state. The value is in 0xARGB format.</li> <li>.value[2].u32: color of the underline applied to the text when an error is detected. The value is in 0xARGB format.</li> <li>.value[3].u32: color of the underline applied to the text when it is disabled. The value is in 0xARGB format.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_CARET_STYLE

```c
NODE_TEXT_EDITOR_CARET_STYLE = 22040
```

**Description**

Sets the caret width. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: caret width, in vp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: caret width, in vp.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_SELECT_ALL

```c
NODE_TEXT_EDITOR_SELECT_ALL = 22041
```

**Description**

Sets whether to select all text in the initial state. This attribute can be set, reset, and obtained as required through APIs. The full selection is triggered only when the component gains focus for the first time and the layout is complete. It is not triggered when the window regains focus.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to select all text in the initial state. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether to select all text in the initial state. The value **1** means to select all, and **0** means the opposite.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_BLUR_ON_SUBMIT

```c
NODE_TEXT_EDITOR_BLUR_ON_SUBMIT = 22042
```

**Description**

Sets whether to blur on submit. This attribute can be set, reset, and obtained as required through APIs. This attribute takes effect only when EnterKeyType is NEW_LINE and the Enter key is pressed. When set to **1**, the keyboard is closed and the component loses focus without inserting a newline. When set to **0**, a newline is inserted and the component retains focus.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to blur on submit. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether to blur on submit. The value **1** means to blur, and **0** means the opposite.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_CONTENT_RECT

```c
NODE_TEXT_EDITOR_CONTENT_RECT = 22043
```

**Description**

Gets the position and size of the editing content area. This attribute can only be obtained.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: x offset of the editing content area.</li> <li>.value[1].f32: y offset of the editing content area.</li> <li>.value[2].f32: width of the editing content area.</li> <li>.value[3].f32: height of the editing content area.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_EDITOR_SELECTION_MENU_HIDDEN = 22044
```

**Description**

Sets whether to hide the selection menu. This attribute can be set, reset, and obtained as required through APIs. When set to **1**, the selection menu is not displayed on long press, double-tap, or right-click, but the selection handles are not affected.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to hide the selection menu. The value **1** means to hide, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the selection menu is hidden. The value **1** means hidden, and **0** means not hidden.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_ENABLE_SKIP_PREVIEW_LONG_PRESS

```c
NODE_TEXT_EDITOR_ENABLE_SKIP_PREVIEW_LONG_PRESS = 22045
```

**Description**

Sets whether to skip the preview state on long press and directly enter the editing state. This attribute can be set, reset, and obtained as required through APIs. When set to **1**, long press directly enters the editing state (keyboard pops up and cursor twinkles), skipping the preview state. Double-tap behavior is not affected.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to skip the preview state on long press. The value **1** means to skip, and **0** means the opposite. The default value is **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether to skip the preview state on long press. The value **1** means to skip, and **0** means the opposite.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_CANCEL_BUTTON

```c
NODE_TEXT_EDITOR_CANCEL_BUTTON = 22046
```

**Description**

Defines the style of the cancel button of the text editor. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: button style [ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle). The default value is <b>ARKUI_CANCELBUTTON_STYLE_INPUT</b>.</li> <li>.value[1]?.f32: button icon size, in vp.</li> <li>.value[2]?.u32: button icon color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> <li>?.string: button icon image source. The value is the local address of the image, for example, /pages/icon.png.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: button style [ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle).</li> <li>.value[1].f32: icon size, in vp.</li> <li>.value[2].u32: button icon color, in 0xARGB format.</li> <li>.string: button icon image source.</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_SHOW_COUNTER

```c
NODE_TEXT_EDITOR_SHOW_COUNTER = 22047
```

**Description**

Defines the counter settings. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to show a character counter. The value <b>true</b> means to show a character counter.</li> <li>.value[1]?.f32: threshold percentage for displaying the character counter. The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. The value range is 1 to 100. If the value is a decimal, it is rounded down.</li> <li>.value[2]?.i32: whether to highlight the border when the number of entered characters reaches the maximum.</li> <li>.object: counter configuration. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to show a character counter.</li> <li>.value[1].f32: threshold percentage for displaying the character counter. The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. The value range is 1 to 100.</li> <li>.value[2].i32: whether to highlight the border when the number of entered characters reaches the maximum. The default value is <b>true</b>.</li> <li>.object: counter configuration. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-showcounterconfig.md).</li> </ul>

**Since**: 26.2.0

### NODE_TEXT_EDITOR_INPUT_FILTER

```c
NODE_TEXT_EDITOR_INPUT_FILTER = 22048
```

**Description**

Sets the input filter regex for the **TextEditor** component. <br>This attribute can be set, reset, and obtained as required through APIs. <br>This attribute is effective only in spanString mode (including both single-line and multi-line modes). <br>When both inputFilter and maxLength are set, the filter priority is: inputFilter first, then maxLength. <br>When the regex changes, existing content is silently re-filtered (consistent with TextInput behavior). <br>Non-character content (ImageSpan/SymbolSpan/BuilderSpan) is treated as \uFFFC during regex matching. <br>The format of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for property setting method parameters and property getting method return values is as follows. <br>**Parameter:**<br><br>.string: Regex expression string for input filtering. Only characters matching the regex whitelist are allowed. An empty string is equivalent to not setting the filter. <br>**Return:**<br><br>.string: The currently set input filter regex expression string.

**Since**: 26.2.0


