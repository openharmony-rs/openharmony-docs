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

Type of the **Enter** key of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Type of the **Enter** key. The parameter type is {@link ArkUI_EnterKeyType}. The default value is **ARKUI_ENTER_KEY_TYPE_NEW_LINE**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: Type of the **Enter** key. The parameter type is {@link ArkUI_EnterKeyType}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_CARET_COLOR

```c
NODE_TEXT_EDITOR_CARET_COLOR
```

**Description**

Caret color of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: Caret color, in 0xARGB format. For example, **0xFFFF0000** indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: Caret color, in 0xARGB format.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_SCROLL_BAR_COLOR

```c
NODE_TEXT_EDITOR_SCROLL_BAR_COLOR
```

**Description**

Scroll bar color of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.data[0].u32: Scroll bar color, in 0xARGB format.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.data[0].u32: Scroll bar color, in 0xARGB format.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_BAR_STATE

```c
NODE_TEXT_EDITOR_BAR_STATE
```

**Description**

Scroll bar display mode of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Scroll bar display mode of the text area. The parameter type is {@link ArkUI_BarState}. The default value is **ARKUI_BAR_STATE_AUTO**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: Scroll bar display mode of the text area. The parameter type is {@link ArkUI_BarState}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_DATA_DETECTOR
```

**Description**

Whether to enable text entity recognition for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable text entity recognition. The value **1** indicates to enable text entity recognition, and **0** indicates the opposite. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether text entity recognition is enabled.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG

```c
NODE_TEXT_EDITOR_DATA_DETECTOR_CONFIG
```

**Description**

Recognition configuration for the **TextEditor** component. This attribute can be set and reset as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: Recognition configuration. The parameter type is {@link ArkUI_TextDataDetectorConfig}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS

```c
NODE_TEXT_EDITOR_EDIT_MENU_OPTIONS
```

**Description**

Extended menu options for the **TextEditor** component. This attribute can be set and reset as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: Extended menu options. The parameter type is {@link ArkUI_TextEditMenuOptions}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_PLACEHOLDER

```c
NODE_TEXT_EDITOR_PLACEHOLDER
```

**Description**

Placeholder options when there is no input for the **TextEditor** component. This attribute can be set and reset as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: Placeholder options when there is no input. The parameter type is {@link ArkUI_TextEditorPlaceholderOptions}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER

```c
NODE_TEXT_EDITOR_STYLED_STRING_CONTROLLER
```

**Description**

Styled string controller of the **TextEditor** component. This attribute can be set as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: Styled string controller. The parameter type is {@link ArkUI_TextEditorStyledStringController}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_EDITOR_ENABLE_PREVIEW_TEXT
```

**Description**

Whether to enable preview text for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable preview text. The value **1** indicates to enable preview text, and **0** indicates the opposite. The default value is **1**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether preview text is enabled. The value **1** indicates preview text is enabled, and **0** indicates the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_LAYOUT_MANAGER

```c
NODE_TEXT_EDITOR_LAYOUT_MANAGER
```

**Description**

**TextLayoutManager** of the **TextEditor** component. This attribute can be obtained as required through APIs. **Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: Layout manager. The parameter type is {@link ArkUI_TextLayoutManager}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_EDITOR_ENABLE_SELECTED_DATA_DETECTOR
```

**Description**

Whether to enable the AI menu for text selection and recognition of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable the AI menu for text selection and recognition. The value **1** means to enable, and **0** means the opposite. The default value is **1**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether the AI menu is enabled for text selection and recognition.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_EDITOR_SELECTED_BACKGROUND_COLOR
```

**Description**

Background color of the selected content in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.data[0].u32: Background color of the selected content, in 0xARGB format.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.data[0].u32: Background color of the selected content, in 0xARGB format.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_EDITOR_ENABLE_KEYBOARD_ON_FOCUS
```

**Description**

Whether to enable the input method when the focus is obtained in a way other than by clicking in the **<br>TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable the input method when the focus is obtained in a way other than clicking. The value **1** means to enable, and **0** means the opposite. The default value is **1**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether the input method is enabled when the focus is obtained in a way other than clicking. The value **1** indicates the input method is enabled, and **0** indicates the input method is disabled.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_MAX_LENGTH

```c
NODE_TEXT_EDITOR_MAX_LENGTH
```

**Description**

Maximum number of characters in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Maximum number of characters.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Maximum number of characters.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_MAX_LINES

```c
NODE_TEXT_EDITOR_MAX_LINES
```

**Description**

Maximum number of lines in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Maximum number of lines in the text editor.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Maximum number of lines in the text editor.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK

```c
NODE_TEXT_EDITOR_ENABLE_HAPTIC_FEEDBACK
```

**Description**

Whether to enable haptic feedback of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable haptic feedback in the text editor. The value **1** means to enable, and ** 0** means the opposite. The default value is **1**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether haptic feedback is enabled. The value **1** indicates haptic feedback is enabled, and **0** indicates the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_COPY_OPTIONS

```c
NODE_TEXT_EDITOR_COPY_OPTIONS
```

**Description**

Copy options of the **TextEditor** component, which can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Copy options. The parameter type is {@link ArkUI_CopyOptions}. The default value is ** ARKUI_COPY_OPTIONS_LOCAL_DEVICE**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: Copy options. The parameter type is {@link ArkUI_CopyOptions}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE

```c
NODE_TEXT_EDITOR_KEYBOARD_APPEARANCE
```

**Description**

Keyboard appearance of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Appearance of the keyboard. The parameter type is {@link ArkUI_KeyboardAppearance}. The default value is **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: Appearance of the keyboard. The parameter type is {@link ArkUI_KeyboardAppearance}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_STOP_BACK_PRESS

```c
NODE_TEXT_EDITOR_STOP_BACK_PRESS
```

**Description**

Whether the **TextEditor** component blocks the propagation of return events. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to block the propagation of return events. The value **1** indicates to block, and ** 0** indicates the opposite. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether the propagation of return events is blocked. The value **1** indicates that the propagation of return events is blocked, and **0** indicates the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING

```c
NODE_TEXT_EDITOR_ENABLE_AUTO_SPACING
```

**Description**

Whether to enable automatic spacing for Chinese and Western characters in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable automatic spacing. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether automatic spacing is enabled. The value **1** indicates automatic spacing is enabled, and **0** indicates the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_CUSTOM_KEYBOARD

```c
NODE_TEXT_EDITOR_CUSTOM_KEYBOARD
```

**Description**

Custom keyboard of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: Custom keyboard. The parameter type is {@link ArkUI_NodeHandle}.</li><br><li>.value[0]?.i32: Whether the custom keyboard supports avoidance. The value **0** indicates no, and the value * *1** indicates yes. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: Custom keyboard. The parameter type is {@link ArkUI_NodeHandle}.</li> <li>.value[0].i32: Whether the custom keyboard supports avoidance. The value **0** indicates no, and the value ** 1** indicates yes.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_BIND_SELECTION_MENU

```c
NODE_TEXT_EDITOR_BIND_SELECTION_MENU
```

**Description**

Binds the custom text selection menu of the **TextEditor** component. This attribute can be set and reset as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: Text selection menu. The parameter type is {@link ArkUI_TextEditorSelectionMenuOptions}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING

```c
NODE_TEXT_EDITOR_INCLUDE_FONT_PADDING
```

**Description**

Whether to add spacing to the first and last lines of the **TextEditor** component to prevent text truncation. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to add spacing. The value **1** means to add spacing, and **0** means not to add spacing. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether spacing is added. The value **1** means that spacing is added, and **0** means spacing is not added.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING

```c
NODE_TEXT_EDITOR_FALLBACK_LINE_SPACING
```

**Description**

Whether to enable line height adaptation of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable line height adaptation. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether line height adaptation is enabled. The value **1** means line height adaptation is enabled, and **0** means the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_EDITOR_COMPRESS_LEADING_PUNCTUATION
```

**Description**

Whether to enable punctuation compression for the beginning of a line in the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable punctuation compression. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether punctuation compression is enabled. The value **1** means punctuation compression is enabled, and **0** means the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_EDITOR_SELECTED_DRAG_PREVIEW_STYLE
```

**Description**

Selected drag preview style of the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: Selected drag preview style configuration. The parameter type is {@link ArkUI_SelectedDragPreviewStyle}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: Selected drag preview style configuration. The parameter type is {@link ArkUI_SelectedDragPreviewStyle}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_SINGLE_LINE

```c
NODE_TEXT_EDITOR_SINGLE_LINE
```

**Description**

Whether to enable single-line mode for the **TextEditor** component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable single-line mode. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether single-line mode is enabled. The value **1** means single-line mode is enabled, and ** 0** means the opposite.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_EDITOR_ORPHAN_CHAR_OPTIMIZATION
```

**Description**

Sets whether to enable orphan character optimization for text layout in **TextEditor**. After setting,text layout is improved by more efficiently handling orphan characters (the first character of the last line of a paragraph). When enabled, it adjusts line break points to avoid orphan characters as much as possible. The orphan character optimization feature only works when {@link ArkUI_WordBreak}<br>is not **ARKUI_WORD_BREAK_BREAK_ALL**.<br>**Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether orphan character optimization is enabled.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING

```c
NODE_TEXT_EDITOR_HORIZONTAL_SCROLLING
```

**Description**

Sets whether to enable horizontal scrolling for the **TextEditor** component when the text width exceeds the content area width. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable horizontal scrolling. The value **1** means to enable, and **0** means the opposite. The default value is **0**.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether horizontal scrolling is enabled.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_EDITOR_PUNCTUATION_OVERFLOW
```

**Description**

Sets whether to enable punctuation overflow at the end of a line. <br>This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable punctuation overflow, the default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow.</li> </ul>

**Since**: 26.0.0


