# Text Input

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_INPUT_PLACEHOLDER

```c
NODE_TEXT_INPUT_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT
```

**Description**

Defines the default placeholder text of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: default placeholder text.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: default placeholder text.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_TEXT

```c
NODE_TEXT_INPUT_TEXT
```

**Description**

Defines the default text content of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: default text content.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: default text content.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CARET_COLOR

```c
NODE_TEXT_INPUT_CARET_COLOR
```

**Description**

Defines the caret color attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: caret color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: caret color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CARET_STYLE

```c
NODE_TEXT_INPUT_CARET_STYLE
```

**Description**

Defines the caret style attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: caret width, in vp.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: caret width, in vp.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SHOW_UNDERLINE

```c
NODE_TEXT_INPUT_SHOW_UNDERLINE
```

**Description**

Defines the underline attribute of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to show an underline. The value <b>true</b> means to show an underline, and <b>false</b> means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The value <b>1</b> means to show an underline, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_MAX_LENGTH

```c
NODE_TEXT_INPUT_MAX_LENGTH
```

**Description**

Defines the maximum number of characters in the text input. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: maximum number of characters in the text input, without a unit.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: maximum number of characters in the text input.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ENTER_KEY_TYPE

```c
NODE_TEXT_INPUT_ENTER_KEY_TYPE
```

**Description**

Defines the type of the Enter key. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: type of the Enter key{@link ArkUI_EnterKeyType}. The default value is <b>ARKUI_ENTER_KEY_TYPE_DONE</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: type of the Enter key{@link ArkUI_EnterKeyType}.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_PLACEHOLDER_COLOR

```c
NODE_TEXT_INPUT_PLACEHOLDER_COLOR
```

**Description**

Defines the placeholder text color. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: color value, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_PLACEHOLDER_FONT

```c
NODE_TEXT_INPUT_PLACEHOLDER_FONT
```

**Description**

Defines the placeholder text font. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0]?.f32: font size, in fp. Optional. The default value is <b>16.0</b>.</li><br><li>.value[1]?.i32: font style {@link ArkUI_FontStyle}. Optional. The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li><br><li>.value[2]?.i32: font weight {@link ArkUI_FontWeight}. Optional. The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li><br><li>?.string: font family. Multiple font families are separated by commas (,). Example: "font weight; font family 1, font family 2".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].f32: font size, in fp.</li><br><li>.value[1].i32: font style {@link ArkUI_FontStyle}.</li><br><li>.value[2].i32: font weight {@link ArkUI_FontWeight}.</li> <li>.string: font family. Multiple font families are separated by commas (,).</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS
```

**Description**

Defines whether to enable the input method when the component obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable the input method when the component obtains focus. The value <b>true</b> means to enable the input method, and <b>false</b> means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The value <b>1</b> means to enable the input method when the component obtains focus, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_TYPE

```c
NODE_TEXT_INPUT_TYPE
```

**Description**

Defines the text box type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: text box type {@link ArkUI_TextInputType}. The default value is <b>ARKUI_TEXTINPUT_TYPE_NORMAL</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: text box type {@link ArkUI_TextInputType}.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR
```

**Description**

Defines the background color of the selected text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: color value, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SHOW_PASSWORD_ICON

```c
NODE_TEXT_INPUT_SHOW_PASSWORD_ICON
```

**Description**

Defines whether to display the password icon at the end of the password text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to display the password icon at the end of the password text box. The value <b>true</b> means to display the password icon, and <b>false</b> means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The value <b>1</b> means to display the password icon at the end of the password text box, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_EDITING

```c
NODE_TEXT_INPUT_EDITING
```

**Description**

Defines the editable state for the single-line text box. This attribute can be set as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to remain in the editable state. The value <b>true</b> means to remain in the editable state, and <b>false</b> means to exit the editable state.</li><br></ul><br>**Format of the {@link ArkUI_AttributeItem} for obtaining the attribute:**<br><ul> <li>.value[0].i32: whether to remain in the editable state. The value <b>true</b> means to remain in the editable state, and <b>false</b> means to exit the editable state.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CANCEL_BUTTON

```c
NODE_TEXT_INPUT_CANCEL_BUTTON
```

**Description**

Defines the style of the cancel button on the right of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: button style {@link ArkUI_CancelButtonStyle}. The default value is <b>ARKUI_CANCELBUTTON_STYLE_INPUT</b>.</li><br><li>.value[1]?.f32: button icon size, in vp.</li><br><li>.value[2]?.u32: button icon color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br><li>?.string: button icon image source. The value is the local address of the image, for example, /pages/icon.png.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: button style {@link ArkUI_CancelButtonStyle}.</li> <li>.value[1].f32: icon size, in vp.</li><br><li>.value[2].u32: button icon color, in 0xARGB format.</li> <li>.string: button icon image source.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_TEXT_SELECTION

```c
NODE_TEXT_INPUT_TEXT_SELECTION
```

**Description**

Sets the text selection area, which will be highlighted. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: start position of the text selection.</li><br><li>.value[1].i32: end position of the text selection.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: start position of the text selection.</li><br><li>.value[1].i32: end position of the text selection.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_UNDERLINE_COLOR

```c
NODE_TEXT_INPUT_UNDERLINE_COLOR
```

**Description**

Sets the color of the text underline when it is enabled.<br> The default underline color configured for the theme is <b>'0x33182431'</b>.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color of the underline applied to the text being typed in. The value is in 0xARGB format.</li><br><li>.value[1].u32: color of the underline applied to the text in the normal state. The value is in 0xARGB format.</li><br><li>.value[2].u32: color of the underline applied to the text when an error is detected. The value is in 0xARGB format.</li><br><li>.value[3].u32: color of the underline applied to the text when it is disabled. The value is in 0xARGB format.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: color of the underline applied to the text being typed in. The value is in 0xARGB format.</li><br><li>.value[1].u32: color of the underline applied to the text in the normal state. The value is in 0xARGB format.</li><br><li>.value[2].u32: color of the underline applied to the text when an error is detected. The value is in 0xARGB format.</li><br><li>.value[3].u32: color of the underline applied to the text when it is disabled. The value is in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ENABLE_AUTO_FILL

```c
NODE_TEXT_INPUT_ENABLE_AUTO_FILL
```

**Description**

Sets whether to enable autofill.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable autofill. The default value is <b>true</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable autofill.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CONTENT_TYPE

```c
NODE_TEXT_INPUT_CONTENT_TYPE
```

**Description**

Sets the autofill type.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: autofill type. The parameter type is {@link ArkUI_TextInputContentType}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: autofill type. The parameter type is {@link ArkUI_TextInputContentType}.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_PASSWORD_RULES

```c
NODE_TEXT_INPUT_PASSWORD_RULES
```

**Description**

Defines the rules for generating passwords. When autofill is used, these rules are transparently transmitted to Password Vault for generating a new password.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: rules for generating passwords.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: rules for generating passwords.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SELECT_ALL

```c
NODE_TEXT_INPUT_SELECT_ALL
```

**Description**

Sets whether to select all text in the initial state. The inline mode is not supported.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to select all text in the initial state. The default value is b>false</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to select all text in the initial state.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_INPUT_FILTER

```c
NODE_TEXT_INPUT_INPUT_FILTER
```

**Description**

Sets the regular expression for input filtering. Only inputs that comply with the regular expression can be displayed. Other inputs are filtered out. The specified regular expression can match single characters, but not strings.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: regular expression.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: regular expression.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_STYLE

```c
NODE_TEXT_INPUT_STYLE
```

**Description**

Sets the text box to the default style or inline input style.<br> For the inline input style, only <b>InputType.Normal</b> is supported.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: text input style. The parameter type is {@link ArkUI_TextInputStyle}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: text input style. The parameter type is {@link ArkUI_TextInputStyle}.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CARET_OFFSET

```c
NODE_TEXT_INPUT_CARET_OFFSET
```

**Description**

Sets or obtains the caret position.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: character count from the beginning of a string to the caret position.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: index of the caret position.</li><br><li>.value[1].f32: X coordinate of the caret relative to the text box.</li><br><li>.value[2].f32: Y coordinate of the caret relative to the text box.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CONTENT_RECT

```c
NODE_TEXT_INPUT_CONTENT_RECT
```

**Description**

Obtains the position of the edited text area relative to the component and its size. **Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: horizontal coordinate.</li><br><li>.value[1].f32: vertical coordinate.</li><br><li>.value[2].f32: content width.</li><br><li>.value[3].f32: content height.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CONTENT_LINE_COUNT

```c
NODE_TEXT_INPUT_CONTENT_LINE_COUNT
```

**Description**

Obtains the number of lines of the edited text. **Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: number of lines of the edited text.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN
```

**Description**

Sets whether to hide the text selection menu when the text box is long-pressed, double-click, or right-clicked. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-click, or right-clicked. The default value is <b>false</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-click, or right-clicked.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_BLUR_ON_SUBMIT

```c
NODE_TEXT_INPUT_BLUR_ON_SUBMIT
```

**Description**

Sets whether the text box loses focus after the Enter key is pressed to submit information.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the text box loses focus.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the text box loses focus.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CUSTOM_KEYBOARD

```c
NODE_TEXT_INPUT_CUSTOM_KEYBOARD
```

**Description**

Set up a custom keyboard.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: custom keyboard, The parameter type is {@link ArkUI_NodeHandle}.</li><br><li>.value[0]?.i32: Sets whether the custom keyboard supports the avoidance feature, default value false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: custom keyboard, The parameter type is {@link ArkUI_NodeHandle}.</li> <li>.value[0].i32: Set whether the custom keyboard supports the avoidance function.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_WORD_BREAK

```c
NODE_TEXT_INPUT_WORD_BREAK
```

**Description**

Defines the line break rule. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_WordBreak}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_WordBreak}.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS
```

**Description**

Sets whether the keyboard pops up when the input box gains focus. It supports property setting, property reset and property acquisition interfaces.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to pop up the keyboard.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether to pop up the keyboard.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_NUMBER_OF_LINES

```c
NODE_TEXT_INPUT_NUMBER_OF_LINES
```

**Description**

When this property is set, the height of the textInput component is calculated using this property.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: set the value of numberOfLines.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: the value of numberOfLines.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_LETTER_SPACING

```c
NODE_TEXT_INPUT_LETTER_SPACING = 7032
```

**Description**

Sets the letter spacing of the <b>TextInput</b> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: letter spacing. The default unit is fp.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: letter spacing. The default unit is fp.</li> </ul>

**Since**: 15

### NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT = 7033
```

**Description**

Sets whether to enable preview text for the <b>TextInput</b> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable preview tex.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable preview tex.</li> </ul>

**Since**: 15

### NODE_TEXT_INPUT_HALF_LEADING

```c
NODE_TEXT_INPUT_HALF_LEADING = 7034
```

**Description**

Sets whether to center text vertically in the textInput component.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to center text vertically. The default value is <b>false</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to center text vertically.</li> </ul>

**Since**: 18

### NODE_TEXT_INPUT_KEYBOARD_APPEARANCE

```c
NODE_TEXT_INPUT_KEYBOARD_APPEARANCE = 7035
```

**Description**

Set the keyboard style of textInput<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: keyboard style, the parameter type is {@link ArkUI_KeyboardAppearanceType}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: keyboard style, the parameter type is {@link ArkUI_KeyboardAppearanceType}.</li> </ul>

**Since**: 15

### NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION

```c
NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036
```

**Description**

Set whether to enable the auto fill animation or not.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to enable the auto fill animation.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Get the flag of whether the auto fill animation is enabled.</li> </ul>

**Since**: 20

### NODE_TEXT_INPUT_LINE_HEIGHT

```c
NODE_TEXT_INPUT_LINE_HEIGHT = 7037
```

**Description**

Set the line height of the input node. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: line height value.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: line height value.</li> </ul>

**Since**: 20

### NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR = 7038
```

**Description**

Enables selected data detector.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Enable selected text recognition, default value true.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether selected text recognition is enabled.</li> </ul>

**Since**: 22

### NODE_TEXT_INPUT_SHOW_COUNTER

```c
NODE_TEXT_INPUT_SHOW_COUNTER = 7040
```

**Description**

Defines the counter settings. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to show a character counter. The value <b>true</b> means to show a character counter.</li><br><li>.value[1]?.f32: threshold percentage for displaying the character counter. The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. The value range is 1 to 100. If the value is a decimal, it is rounded down.</li><br><li>.value[2]?.i32: whether to highlight the border when the number of entered characters reaches the maximum.</li><br><li>.object: counter configuration. The parameter type is {@link ArkUI_ShowCounterConfig}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: whether to show a character counter.</li><br><li>.value[1].f32: threshold percentage for displaying the character counter. The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. The value range is 1 to 100.</li><br><li>.value[2].i32: whether to highlight the border when the number of entered characters reaches the maximum. The default value is <b>true</b>.</li><br><li>.object: counter configuration. The parameter type is {@link ArkUI_ShowCounterConfig}.</li> </ul>

**Since**: 22

### NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE

```c
NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE = 7041
```

**Description**

Used to set or get the text content base controller.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: the text content base controller. The parameter type is {@link ArkUI_TextContentBaseController}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: the text content base controller. The parameter type is {@link ArkUI_TextContentBaseController}.</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_ELLIPSIS_MODE

```c
NODE_TEXT_INPUT_ELLIPSIS_MODE = 7042
```

**Description**

Defines the ellipsis position. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_EllipsisMode}, the default value is ARKUI_ELLIPSIS_MODE_END.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_EllipsisMode}.</li> </ul>

**Since**: 24

### NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION

```c
	  NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION = 7043
```

**Description**

Whether to avoid an orphan word on the last line of the paragraph.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The current state of this feature.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION = 7044
```

**Description**

Whether to compress punctuation at the beginning of line.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether compress punctuation at the beginning of line.</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_INCLUDE_FONT_PADDING

```c
NODE_TEXT_INPUT_INCLUDE_FONT_PADDING = 7045
```

**Description**

Determines whether the layout adds extra padding at the top and bottom to make space for characters.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Enable include the font padding, true means enable this feature, false means disable. The default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether include the font padding.</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_FALLBACK_LINE_SPACING

```c
NODE_TEXT_INPUT_FALLBACK_LINE_SPACING = 7046
```

**Description**

Whether to include ascent/descent from fallback fonts to prevent overlapping lines.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether fallback line spacing.</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_DIRECTION

```c
NODE_TEXT_INPUT_DIRECTION = 7047
```

**Description**

Writing direction of the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: writing direction of the text. The value is an enum of {@link ArkUI_TextDirection}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: writing direction the text. The value is an enum of {@link ArkUI_TextDirection}.</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE = 7048
```

**Description**

Used to set the selected drag preview style. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: selected drag preview style configuration. The parameter type is {@link ArkUI_SelectedDragPreviewStyle}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: selected drag preview style configuration. The parameter type is {@link ArkUI_SelectedDragPreviewStyle}.</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_TEXT_OVERFLOW

```c
NODE_TEXT_INPUT_TEXT_OVERFLOW = 7049
```

**Description**

Defines the textinput textOverflow attribute. which can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: display mode when the text is too long {@link ArkUI_TextOverflow}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: display mode when the text is too long {@link ArkUI_TextOverflow}.</li> </ul>

**Since**: 24

### NODE_TEXT_INPUT_DECORATION

```c
NODE_TEXT_INPUT_DECORATION = 7050
```

**Description**

Defines the text decoration style and color for single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>?.object: Optional. The decoration style options. The parameter type is {@link OH_ArkUI_DecorationStyleOptions}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: The decoration style options. The parameter type is {@link OH_ArkUI_DecorationStyleOptions}.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_LINEAR_GRADIENT

```c
NODE_TEXT_INPUT_LINEAR_GRADIENT = 7051
```

**Description**

Sets a linear gradient effect for text in the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: start angle of the linear gradient. The setting takes effect only when <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>. A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>.</li><br><li>.value[1].i32: direction of the linear gradient. When a direction other than <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> is set, the <b>angle</b> property is ignored. The parameter type is {@link ArkUI_LinearGradientDirection}.</li><br><li>.value[2].i32: whether the colors are repeated. The default value is <b>false</b>.</li><br><li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].f32: start angle of the linear gradient. When <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>, <b>angle</b> at the set value; otherwise, it is at default value.</li><br><li>.value[1].i32: direction of the linear gradient.</li><br><li>.value[2].i32: whether the colors are repeated.</li><br><li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_RADIAL_GRADIENT

```c
NODE_TEXT_INPUT_RADIAL_GRADIENT = 7052
```

**Description**

Sets a radial gradient effect for text in the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the text.</li><br><li>.value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text.</li><br><li>.value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>.</li><br><li>.value[3]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.</li><br><li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].f32: X-coordinate of the radial gradient center relative to the upper left corner of the text.</li><br><li>.value[1].f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text.</li><br><li>.value[2].f32: radius of the radial gradient. The default value is <b>0</b>.</li><br><li>.value[3].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.</li><br><li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_INPUT_PUNCTUATION_OVERFLOW = 7053
```

**Description**

Sets whether to enable punctuation overflow at line ends. <br>This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable punctuation overflow, the default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_PLACEHOLDER

```c
NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA
```

**Description**

Defines the default placeholder text for the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: default placeholder text.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: default placeholder text.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_TEXT

```c
NODE_TEXT_AREA_TEXT
```

**Description**

Defines the default text content for the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: default text content.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: default text content.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_MAX_LENGTH

```c
NODE_TEXT_AREA_MAX_LENGTH
```

**Description**

Defines the maximum number of characters in the text input. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: maximum number of characters in the text input.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: maximum number of characters in the text input.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_PLACEHOLDER_COLOR

```c
NODE_TEXT_AREA_PLACEHOLDER_COLOR
```

**Description**

Defines the placeholder text color. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: color value, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_PLACEHOLDER_FONT

```c
NODE_TEXT_AREA_PLACEHOLDER_FONT
```

**Description**

Defines the placeholder text font. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0]?.f32: font size, in fp. Optional. The default value is <b>16.0</b>.</li><br><li>.value[1]?.i32: font style {@link ArkUI_FontStyle}. Optional. The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li><br><li>.value[2]?.i32: font weight {@link ArkUI_FontWeight}. Optional. The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li><br><li>?.string: font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2".</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].f32: font size, in fp.</li><br><li>.value[1].i32: font style {@link ArkUI_FontStyle}.</li><br><li>.value[2].i32: font weight {@link ArkUI_FontWeight}.</li> <li>.string: font family. Multiple font families are separated by commas (,).</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CARET_COLOR

```c
NODE_TEXT_AREA_CARET_COLOR
```

**Description**

Defines the caret color attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: background color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_EDITING

```c
NODE_TEXT_AREA_EDITING
```

**Description**

Defines the editable state for the multi-line text box. This attribute can be set as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to remain in the editable state. The value <b>true</b> means to remain in the editable state, and <b>false</b> means to exit the editable state.</li><br></ul><br>**Format of the {@link ArkUI_AttributeItem} for obtaining the attribute:**<br><ul> <li>.value[0].i32: whether to remain in the editable state. The value <b>true</b> means to remain in the editable state, and <b>false</b> means to exit the editable state.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_TYPE

```c
NODE_TEXT_AREA_TYPE
```

**Description**

Defines the text box type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: text box type {@link ArkUI_TextAreaType}. The default value is <b>ARKUI_TEXTAREA_TYPE_NORMAL</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: text box type {@link ArkUI_TextAreaType}.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_SHOW_COUNTER

```c
NODE_TEXT_AREA_SHOW_COUNTER
```

**Description**

Defines the counter settings. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to show a character counter. The value <b>true</b> means to show a character counter.</li><br><li>.value[1]?.f32: threshold percentage for displaying the character counter. The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. The value range is 1 to 100. If the value is a decimal, it is rounded down.</li><br><li>.value[2]?.i32: whether to highlight the border when the number of entered characters reaches the maximum.</li><br><li>.object: counter configuration. The parameter type is {@link ArkUI_ShowCounterConfig}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: whether to show a character counter.</li><br><li>.value[1].f32: threshold percentage for displaying the character counter. The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. The value range is 1 to 100.</li><br><li>.value[2].i32: whether to highlight the border when the number of entered characters reaches the maximum. The default value is <b>true</b>.</li><br><li>.object: counter configuration. The parameter type is {@link ArkUI_ShowCounterConfig}.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_AREA_SELECTION_MENU_HIDDEN
```

**Description**

Sets whether to hide the text selection menu when the text box is long-pressed, double-click, or right-clicked. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-click, or right-clicked. The default value is <b>false</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-click, or right-clicked.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_BLUR_ON_SUBMIT

```c
NODE_TEXT_AREA_BLUR_ON_SUBMIT
```

**Description**

Sets whether the multi-line text box loses focus after the Enter key is pressed to submit information. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the text box loses focus.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the text box loses focus.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_INPUT_FILTER

```c
NODE_TEXT_AREA_INPUT_FILTER
```

**Description**

Sets the regular expression for input filtering. Only inputs that comply with the regular expression can be displayed. Other inputs are filtered out. The specified regular expression can match single characters, but not strings.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: regular expression.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.string: regular expression.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR
```

**Description**

Defines the background color of the selected text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: color value, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ENTER_KEY_TYPE

```c
NODE_TEXT_AREA_ENTER_KEY_TYPE
```

**Description**

Defines the type of the Enter key. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: type of the Enter key{@link ArkUI_EnterKeyType}. The default value is <b>ARKUI_ENTER_KEY_TYPE_DONE</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: type of the Enter key{@link ArkUI_EnterKeyType}.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS
```

**Description**

Defines whether to enable the input method when the component obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable the input method when the component obtains focus. The value <b>true</b> means to enable the input method, and <b>false</b> means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The value <b>1</b> means to enable the input method when the component obtains focus, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CARET_OFFSET

```c
NODE_TEXT_AREA_CARET_OFFSET
```

**Description**

Sets or obtains the position of the cursor. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Length of characters from the beginning of the string to the position of the cursor.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Index value of the cursor position.</li><br><li>.value[1].f32: indicates the x-coordinate value of the cursor relative to the text box.</li><br><li>.value[2].f32: indicates the y-coordinate value of the cursor relative to the text box.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CONTENT_RECT

```c
NODE_TEXT_AREA_CONTENT_RECT
```

**Description**

Obtains the position of the edited text area relative to the component and its size. **Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: horizontal coordinate.</li><br><li>.value[1].f32: vertical coordinate.</li><br><li>.value[2].f32: content width.</li><br><li>.value[3].f32: content height.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CONTENT_LINE_COUNT

```c
NODE_TEXT_AREA_CONTENT_LINE_COUNT
```

**Description**

Obtains the number of lines of the edited text. **Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: number of lines of the edited text.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_TEXT_SELECTION

```c
NODE_TEXT_AREA_TEXT_SELECTION
```

**Description**

Sets the text selection area, which will be highlighted. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: start position of the text selection.</li><br><li>.value[1].i32: end position of the text selection.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: start position of the text selection.</li><br><li>.value[1].i32: end position of the text selection.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ENABLE_AUTO_FILL

```c
NODE_TEXT_AREA_ENABLE_AUTO_FILL
```

**Description**

Sets whether to enable autofill.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable autofill. The default value is <b>true</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable autofill.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CONTENT_TYPE

```c
NODE_TEXT_AREA_CONTENT_TYPE
```

**Description**

Sets the autofill type.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: autofill type. The parameter type is {@link ArkUI_TextInputContentType}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: autofill type. The parameter type is {@link ArkUI_TextInputContentType}.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS
```

**Description**

Sets whether the keyboard pops up when the input box gains focus. It supports property setting, property reset and property acquisition interfaces.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether to pop up the keyboard.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether to pop up the keyboard.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_NUMBER_OF_LINES

```c
NODE_TEXT_AREA_NUMBER_OF_LINES
```

**Description**

When this property is set, the height of the textArea component is calculated using this property.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: set the value of numberOfLines.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Set the value of numberOfLines.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_LETTER_SPACING

```c
NODE_TEXT_AREA_LETTER_SPACING = 8023
```

**Description**

Sets the letter spacing of the <b>TextArea</b> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: letter spacing. The default unit is fp.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: letter spacing. The default unit is fp.</li> </ul>

**Since**: 15

### NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024
```

**Description**

Sets whether to enable preview text for the <b>TextArea</b> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable preview tex.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable preview tex.</li> </ul>

**Since**: 15

### NODE_TEXT_AREA_HALF_LEADING

```c
NODE_TEXT_AREA_HALF_LEADING = 8025
```

**Description**

Sets whether to center text vertically in the textArea component.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to center text vertically. The default value is <b>false</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to center text vertically.</li> </ul>

**Since**: 18

### NODE_TEXT_AREA_KEYBOARD_APPEARANCE

```c
NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026
```

**Description**

Set the keyboard style of textArea<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: keyboard style, the parameter type is {@link ArkUI_KeyboardAppearanceType}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: keyboard style, the parameter type is {@link ArkUI_KeyboardAppearanceType}.</li> </ul>

**Since**: 15

### NODE_TEXT_AREA_MAX_LINES

```c
NODE_TEXT_AREA_MAX_LINES = 8027
```

**Description**

Set the max lines of the node. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: max lines count.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: max lines count.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_LINE_SPACING

```c
NODE_TEXT_AREA_LINE_SPACING = 8028
```

**Description**

Set line spacing of the node. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: line spacing value.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: line spacing value.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_MIN_LINES

```c
NODE_TEXT_AREA_MIN_LINES = 8029
```

**Description**

Set the min lines of the node. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: min lines count.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: min line count.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL

```c
NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL = 8030
```

**Description**

Set the max lines of the node with scroll. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: max lines count with scroll.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: max line count with scroll.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_LINE_HEIGHT

```c
NODE_TEXT_AREA_LINE_HEIGHT = 8031
```

**Description**

Set the line height of the node. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: line height value.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: line height value.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_BAR_STATE

```c
NODE_TEXT_AREA_BAR_STATE = 8032
```

**Description**

Define bar state of the text area. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: bar state of the text area, specified using the {@link ArkUI_BarState} enum. The default value is <b>ARKUI_BAR_STATE_AUTO</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: bar state of the text area, specified using the {@link ArkUI_BarState} enum.</li> </ul>

**Since**: 22

### NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR = 8033
```

**Description**

Enables selected data detector.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Enable selected text recognition, default value true.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether selected text recognition is enabled.</li> </ul>

**Since**: 22

### NODE_TEXT_AREA_SCROLL_BAR_COLOR

```c
NODE_TEXT_AREA_SCROLL_BAR_COLOR = 8035
```

**Description**

Defines the color of the scrollbar. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.data[0].u32: color of the scroll bar thumb, in 0xARGB format.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.data[0].u32: color of the scroll bar thumb, in 0xARGB format.</li> </ul>

**Since**: 22

### NODE_TEXT_AREA_CUSTOM_KEYBOARD

```c
NODE_TEXT_AREA_CUSTOM_KEYBOARD = 8036
```

**Description**

Sets up a custom keyboard.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: custom keyboard, The parameter type is {@link ArkUI_NodeHandle}.</li><br><li>.value[0]?.i32: Sets whether the custom keyboard supports the avoidance feature, default value false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: custom keyboard, The parameter type is {@link ArkUI_NodeHandle}.</li> <li>.value[0].i32: Set whether the custom keyboard supports the avoidance function.</li> </ul>

**Since**: 22

### NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE

```c
NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE = 8037
```

**Description**

Used to set or get the text content base controller.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: the text content base controller. The parameter type is {@link ArkUI_TextContentBaseController}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: the text content base controller. The parameter type is {@link ArkUI_TextContentBaseController}.</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_ELLIPSIS_MODE

```c
NODE_TEXT_AREA_ELLIPSIS_MODE = 8038
```

**Description**

Defines the ellipsis position. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_EllipsisMode}, the default value is ARKUI_ELLIPSIS_MODE_END.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_EllipsisMode}.</li> </ul>

**Since**: 24

### NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION = 8039
```

**Description**

Whether to avoid an orphan word on the last line of the paragraph.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether enable the feature true means enable this feature, false means disable. The default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The current state of this feature.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION = 8040
```

**Description**

Whether to compress punctuation at the beginning of line.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether compress punctuation at the beginning of line.</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_INCLUDE_FONT_PADDING

```c
NODE_TEXT_AREA_INCLUDE_FONT_PADDING = 8041
```

**Description**

Determines whether the layout adds extra padding at the top and bottom to make space for characters.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Enable include the font padding, true means enable this feature, false means disable. The default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether include the font padding.</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_FALLBACK_LINE_SPACING

```c
NODE_TEXT_AREA_FALLBACK_LINE_SPACING = 8042
```

**Description**

Whether to include ascent/descent from fallback fonts to prevent overlapping lines.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether fallback line spacing.</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_HORIZONTAL_SCROLLING

```c
NODE_TEXT_AREA_HORIZONTAL_SCROLLING = 8043
```

**Description**

Whether to enable horizontal scrolling when text is wider than the view. The default value is false, and text will be wrapped by the view.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: Whether enable the feature.</li> </ul>

**Since**: 24

### NODE_TEXT_AREA_DIRECTION

```c
NODE_TEXT_AREA_DIRECTION = 8044
```

**Description**

Writing direction of the text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: writing direction of the text. The value is an enum of {@link ArkUI_TextDirection}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: writing direction the text. The value is an enum of {@link ArkUI_TextDirection}.</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE = 8045
```

**Description**

Used to set the selected drag preview style. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: selected drag preview style configuration. The parameter type is {@link ArkUI_SelectedDragPreviewStyle}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: selected drag preview style configuration. The parameter type is {@link ArkUI_SelectedDragPreviewStyle}.</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_TEXT_OVERFLOW

```c
NODE_TEXT_AREA_TEXT_OVERFLOW = 8046
```

**Description**

Defines the textarea textOverflow attribute. which can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: display mode when the text is too long {@link ArkUI_TextOverflow}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: display mode when the text is too long {@link ArkUI_TextOverflow}.</li> </ul>

**Since**: 24

### NODE_TEXT_AREA_DECORATION

```c
NODE_TEXT_AREA_DECORATION = 8047
```

**Description**

Defines the text decoration style and color for multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>?.object: Optional. The decoration style options. The parameter type is {@link OH_ArkUI_DecorationStyleOptions}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: The decoration style options. The parameter type is {@link OH_ArkUI_DecorationStyleOptions}.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_LINEAR_GRADIENT

```c
NODE_TEXT_AREA_LINEAR_GRADIENT = 8048
```

**Description**

Sets a linear gradient effect for text in the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: start angle of the linear gradient. The setting takes effect only when <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>. A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>.</li><br><li>.value[1].i32: direction of the linear gradient. When a direction other than <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> is set, the <b>angle</b> property is ignored. The parameter type is {@link ArkUI_LinearGradientDirection}.</li><br><li>.value[2].i32: whether the colors are repeated. The default value is <b>false</b>.</li><br><li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].f32: start angle of the linear gradient. When <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>, <b>angle</b> at the set value; otherwise, it is at default value.</li><br><li>.value[1].i32: direction of the linear gradient.</li><br><li>.value[2].i32: whether the colors are repeated.</li><br><li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_RADIAL_GRADIENT

```c
NODE_TEXT_AREA_RADIAL_GRADIENT = 8049
```

**Description**

Sets a radial gradient effect for text in the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the text.</li><br><li>.value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text.</li><br><li>.value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>.</li><br><li>.value[3]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.</li><br><li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].f32: X-coordinate of the radial gradient center relative to the upper left corner of the text.</li><br><li>.value[1].f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text.</li><br><li>.value[2].f32: radius of the radial gradient. The default value is <b>0</b>.</li><br><li>.value[3].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.</li><br><li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is {@link ArkUI_ColorStop}. Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_AREA_PUNCTUATION_OVERFLOW = 8050
```

**Description**

Sets whether to enable punctuation overflow at line ends. <br>This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable punctuation overflow, the default value is false.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow.</li> </ul>

**Since**: 26.0.0


