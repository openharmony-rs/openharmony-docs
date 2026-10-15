# Text Input

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_INPUT_PLACEHOLDER

```c
NODE_TEXT_INPUT_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT
```

**Description**

Defines the default placeholder text of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: default placeholder text.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: default placeholder text.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_TEXT

```c
NODE_TEXT_INPUT_TEXT
```

**Description**

Default text of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: Default text content, used to set the text initially displayed in the input box. Set this parameter when you need to preset text in the input box, for example, form default values, initial editing content, etc. When not set, the input box is empty.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: Default text content.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CARET_COLOR

```c
NODE_TEXT_INPUT_CARET_COLOR
```

**Description**

Caret color attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: caret color, in 0xARGB format. For example, **0xFFFF0000** indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Caret color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CARET_STYLE

```c
NODE_TEXT_INPUT_CARET_STYLE
```

**Description**

Caret style attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Caret width, in vp. Value range: [0, +∞).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Caret width, in vp.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SHOW_UNDERLINE

```c
NODE_TEXT_INPUT_SHOW_UNDERLINE
```

**Description**

Underline of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to show an underline. **1** means to show an underline; **0** means the opposite. Default value: **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether an underline is shown. The value **1** means that an underline is shown, and **0**<br>means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_MAX_LENGTH

```c
NODE_TEXT_INPUT_MAX_LENGTH
```

**Description**

Maximum number of characters in the text input. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: maximum number of characters in the text input, without a unit. Value range: [0, +∞).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: maximum number of characters in the text input, without a unit.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ENTER_KEY_TYPE

```c
NODE_TEXT_INPUT_ENTER_KEY_TYPE
```

**Description**

Type of the **Enter** key. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: type of the **Enter** key. The value is an enumerated value of [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype). The default value is <b>ARKUI_ENTER_KEY_TYPE_DONE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: type of the **Enter** key. The value is an enumerated value of [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype), used to determine the display style of the **Enter** key in the input box.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_PLACEHOLDER_COLOR

```c
NODE_TEXT_INPUT_PLACEHOLDER_COLOR
```

**Description**

Default placeholder text color when there is no input. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_PLACEHOLDER_FONT

```c
NODE_TEXT_INPUT_PLACEHOLDER_FONT
```

**Description**

Default placeholder text font (including the size, weight, style, and font family) when there is no input. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.f32: Font size, in fp. This parameter is optional. The default value is **16.0**. Value range: [0, +∞). When a negative value is passed, the setting does not take effect.</li> <li>.value[1]?.i32: Font style. This parameter is optional. The value is an enumerated value of {@link ArkUI_FontStyle}. Default value: **ARKUI_FONT_STYLE_NORMAL**, which indicates the normal font style.</li> <li>.value[2]?.i32: Font weight. This parameter is optional. The value is an enumerated value of {@link ArkUI_FontWeight}. Default value: **ARKUI_FONT_WEIGHT_NORMAL**, which indicates the normal font weight.</li> <li>?.string: Font family. Multiple font families are separated by commas (,). For example, "font family 1,font family 2". When not passed, the system default font family is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Font size, in fp.</li> <li>.value[1].i32: Font style. The value is an enumerated value of [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> <li>.value[2].i32: Font weight. The value is an enumerated value of [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> <li>.string: Font family. Multiple font families are separated by commas (,).</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS
```

**Description**

Whether to enable the input method when the component obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable the input method when the component obtains focus. The value **1** indicates means to enable the input method, and <b>false</b> means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the input method is enabled when the component obtains focus. The value **1** means <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_TYPE

```c
NODE_TEXT_INPUT_TYPE
```

**Description**

Text input type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Text input type. The value is an enumerated value of [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype). The default value is **ARKUI_TEXTINPUT_TYPE_NORMAL**, which indicates the basic input mode.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Text input type. The value is an enumerated value of [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype), used to determine the input content and keyboard style of the input box.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR
```

**Description**

Background color of the selected text. This attribute can be set, reset, and obtained as required This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color, in 0xARGB format. For example, **0xFFFF0000** indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SHOW_PASSWORD_ICON

```c
NODE_TEXT_INPUT_SHOW_PASSWORD_ICON
```

**Description**

Whether to display the password icon at the end of the password text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to display the password icon. **1** means to display; **0** otherwise. Default value: **0**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the password icon is displayed. The value **1** means that the password icon is displayed, and **0** means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_EDITING

```c
NODE_TEXT_INPUT_EDITING
```

**Description**

Editable state for the single-line text box. This attribute can be set and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to remain in the editable state. **1** means to remain in the editable state, and **0**<br>means to exit the editable state.</li> </ul><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for obtaining the attribute:**<br><ul> <li>.value[0].i32: Whether to remain in the editable state. **1** means to remain in the editable state, and **0**<br>means to exit the editable state.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CANCEL_BUTTON

```c
NODE_TEXT_INPUT_CANCEL_BUTTON
```

**Description**

Style of the cancel button on the right of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Button style. The value is an enumerated value of [ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle). The default value is **ARKUI_CANCELBUTTON_STYLE_INPUT**, which indicates the clear button input style.</li> <li>.value[1]?.f32: Icon size, in vp. Value range: [0, +∞). When a negative value is passed, the setting does not take effect. When not passed, the system default icon size is used.</li> <li>.value[2]?.u32: Button icon color, in 0xARGB format, for example, **0xFFFF0000** indicates red. When not passed, the system default icon color is used.</li> <li>?.string: Button icon address. The value is the local address of an image, for example, /pages/icon.png. When not passed, the system default clear icon is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Button style. The value is an enumerated value of [ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle).</li> <li>.value[1].f32: Button icon size, in vp.</li> <li>.value[2].u32: Button icon color, in 0xARGB format.</li> <li>.string: Button icon address.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_TEXT_SELECTION

```c
NODE_TEXT_INPUT_TEXT_SELECTION
```

**Description**

Text selection area. After set, the selected area will be highlighted. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: start position of the text selection.</li> <li>.value[1].i32: end position of the text selection.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: start position of the text selection.</li> <li>.value[1].i32: end position of the text selection.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_UNDERLINE_COLOR

```c
NODE_TEXT_INPUT_UNDERLINE_COLOR
```

**Description**

Color of the underline when it is shown. This attribute takes effect only after **NODE_TEXT_INPUT_SHOW_UNDERLINE** is set to **1** to show the underline. The default underline color configured for the theme is **0x33182431**, which indicates dark gray with 20% opacity.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: Color of the underline applied to the text being typed in. This parameter is mandatory. The value is in 0xARGB format.</li> <li>.value[1].u32: Color of the underline applied to the text in the normal state. This parameter is mandatory. The value is in 0xARGB format.</li> <li>.value[2].u32: Color of the underline applied to the text when an error is detected. This parameter is mandatory. The value is in 0xARGB format.</li> <li>.value[3].u32: Color of the underline applied to the text when it is disabled. This parameter is mandatory. The value is in 0xARGB format.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Color of the underline applied to the text being typed in. The value is in 0xARGB format.</li> <li>.value[1].u32: Color of the underline applied to the text in the normal state. The value is in 0xARGB format.</li> <li>.value[2].u32: Color of the underline applied to the text when an error is detected. The value is in 0xARGB format.</li> <li>.value[3].u32: Color of the underline applied to the text when it is disabled. The value is in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ENABLE_AUTO_FILL

```c
NODE_TEXT_INPUT_ENABLE_AUTO_FILL
```

**Description**

Whether to enable autofill.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable autofill. The default value is **1**. **1** indicates to enable, and **0** indicates the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether autofill is enabled. The value **1** means auto-fill is enabled, and **0** means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CONTENT_TYPE

```c
NODE_TEXT_INPUT_CONTENT_TYPE
```

**Description**

Autofill type.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype), used to specify the content type in autofill scenarios. For specific enumerated values and application scenarios, see [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype), used to determine the auto-filled content type.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_PASSWORD_RULES

```c
NODE_TEXT_INPUT_PASSWORD_RULES
```

**Description**

Rules for generating passwords. When autofill is used, these rules are transparently transmitted to Password Vault for generating a new password.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: rules for generating passwords, which are transparently passed to the password vault to control new password generation when autofill is triggered.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: rules for generating passwords.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SELECT_ALL

```c
NODE_TEXT_INPUT_SELECT_ALL
```

**Description**

Whether to select all text in the initial state. This attribute is not available for the inline input style.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to select all text. Default value: **0**. The value **1** means to select all text, and **0** means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether all text is selected. **1** means all text is selected, and **0** means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_INPUT_FILTER

```c
NODE_TEXT_INPUT_INPUT_FILTER
```

**Description**

Regular expression for input filtering. Only inputs that comply with the regular expression can be displayed. Other inputs are filtered out. For single-character input scenarios, only single-character matching is supported; for multi-character input scenarios (such as pasting), string matching is supported.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: Regular expression, used to filter user input. Input matching the expression is allowed to be displayed, and input not matching is filtered out. Set this parameter when you need to restrict users to inputting only characters in a specific format. For example, **"^[a-zA-Z]+$"** allows only letters, and **"^[0-9]+$"** allows only digits. When not set, all characters are allowed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: Regular expression.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_STYLE

```c
NODE_TEXT_INPUT_STYLE
```

**Description**

Text box style (default style or inline input style). The inline input style is a borderless embedded input style where the input box blends directly into the page content. The inline input style is only available when [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_NORMAL**.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Text box style. The parameter type is [ArkUI_TextInputStyle](capi-text-input-h.md#arkui_textinputstyle). The inline input style is only available when [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_NORMAL**. The default value is **ARKUI_TEXTINPUT_STYLE_DEFAULT**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Text box style. The parameter type is [ArkUI_TextInputStyle](capi-text-input-h.md#arkui_textinputstyle), used to determine the display style of the input box.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CARET_OFFSET

```c
NODE_TEXT_INPUT_CARET_OFFSET
```

**Description**

Caret position. Sets the position of the caret. Returns the position information of the caret. If this API is called when the caret position is updated in the current frame, it will not take effect.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: length from the start of the string to the position where the caret is located. The value range is [0, Text length]. If the value is out of range, it is automatically corrected to the boundary value.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: index of the caret position.</li> <li>.value[1].f32: X-coordinate of the caret relative to the input box, in px.</li> <li>.value[2].f32: Y-coordinate of the caret relative to the input box, in px.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CONTENT_RECT

```c
NODE_TEXT_INPUT_CONTENT_RECT
```

**Description**

Position of the edited text area relative to the component and its size.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X-coordinate, in px.</li> <li>.value[1].f32: Y-coordinate, in px.</li> <li>.value[2].f32: Content width, in px.</li> <li>.value[3].f32: Content height, in px.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CONTENT_LINE_COUNT

```c
NODE_TEXT_INPUT_CONTENT_LINE_COUNT
```

**Description**

Number of lines of the edited text.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of lines of the edited text.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN
```

**Description**

Whether to hide the text selection menu when the text box is long-pressed, double-tapped, or right-clicked. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to hide the text selection menu when the text box is long-pressed, double-tapped, or right-clicked. The default value is **0**. **1**: The system text selection menu is hidden when a user clicks the text box cursor, long-presses the text box, double-taps the text box, triple-taps the text box, or right-clicks the text box. **0**: The system text selection menu is displayed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the text selection menu is hidden when the text box is long-pressed, double-tapped, or right-clicked. The value **1** means the text selection menu is hidden, and **0** means the text selection menu is displayed.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_BLUR_ON_SUBMIT

```c
NODE_TEXT_INPUT_BLUR_ON_SUBMIT
```

**Description**

Whether the text box loses focus after the **Enter** key is pressed to submit information.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the text box loses focus after the **Enter** key is pressed to submit information. The default value is **1**. **1**: The text box loses focus. **0**: The text box does not lose focus.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the text box loses focus after the **Enter** key is pressed to submit information. The value **1** indicates the text box loses focus, and **0** indicates the text box does not lose focus.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_CUSTOM_KEYBOARD

```c
NODE_TEXT_INPUT_CUSTOM_KEYBOARD
```

**Description**

Custom keyboard.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md).</li> <li>.value[0]?.i32: Whether the custom keyboard supports avoidance. The default value is **0**. **1** to support; **0** otherwise.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md).</li> <li>.value[0].i32: Whether the custom keyboard supports avoidance. The value **1** indicates the custom keyboard supports avoidance, **0** indicates the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_WORD_BREAK

```c
NODE_TEXT_INPUT_WORD_BREAK
```

**Description**

Defines the line break rule. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The parameter type is [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The parameter type is [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak).</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS
```

**Description**

Whether to show the keyboard when the text box obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to show the keyboard. Default value: **1**. **1** to show; **0** otherwise.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the keyboard is shown. The value **1** indicates the keyboard is shown, and 0 indicates the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_NUMBER_OF_LINES

```c
NODE_TEXT_INPUT_NUMBER_OF_LINES
```

**Description**

Number of lines in the TextInput component, which can be used to work out the height of the component. For example, if **numberOfLines** is set to **3**, the component displays three lines of text by default.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Number of lines, with a value range of [1, +∞). This parameter is used to calculate the height of the **TextInput** component. For example, when set to 3, the component displays a height sufficient to accommodate three lines of text content by default.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Number of lines.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_LETTER_SPACING

```c
NODE_TEXT_INPUT_LETTER_SPACING = 7032
```

**Description**

Letter spacing of the TextInput component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: letter spacing. The default unit is fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: letter spacing. The default unit is fp.</li> </ul>

**Since**: 15

### NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT = 7033
```

**Description**

Whether to enable preview text for the TextInput component. This attribute can be set, reset, and obtained as required through APIs. "Preview text" describes a temporary text staging state. The preview text feature must be enabled in the input method. During text input, before a candidate word is confirmed, marked text is displayed in the text box. For example, when entering Chinese characters via Pinyin, the Pinyin letters are displayed in the input box before the candidate word is confirmed. This state is called preview.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable preview text. The default value is **1**. **1** to enable; **0** otherwise.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether preview text is enabled. The value **1** indicates preview text is enabled, **0**<br>indicates the opposite.</li> </ul>

**Since**: 15

### NODE_TEXT_INPUT_HALF_LEADING

```c
NODE_TEXT_INPUT_HALF_LEADING = 7034
```

**Description**

Whether to enable half leading.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable half leading. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable half leading.</li> </ul>

**Since**: 18

### NODE_TEXT_INPUT_KEYBOARD_APPEARANCE

```c
NODE_TEXT_INPUT_KEYBOARD_APPEARANCE = 7035
```

**Description**

Appearance of the keyboard when the text box is started.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: keyboard appearance. The parameter type is ArkUI_KeyboardAppearanceType. For specific enumerated values, see **ArkUI_KeyboardAppearance**. The default value is **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**, which indicates no immersive style is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: keyboard appearance. The parameter type is ArkUI_KeyboardAppearanceType.</li> </ul>

**Since**: 15

### NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION

```c
NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036
```

**Description**

Whether to enable the autofill animation. This animation takes effect only when the input box type {@link ArkUI_TextInputType} is set to **ARKUI_TEXTINPUT_TYPE_PASSWORD**, **ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD**, or **ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD**.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable the autofill animation. When enabled, the animation takes effect during auto-fill only for the input box whose [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_PASSWORD**, **ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD**, or **ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD**. **1** to enable; **0**<br>otherwise. Default value: **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the autofill animation is enabled. The value **1** means enabled, and **0** means disabled. When enabled, the animation takes effect during auto-fill only for the input box whose [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype) enumeration is set to **ARKUI_TEXTINPUT_TYPE_PASSWORD**, **ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD**, or **ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD**.</li> </ul>

**Since**: 20

### NODE_TEXT_INPUT_LINE_HEIGHT

```c
NODE_TEXT_INPUT_LINE_HEIGHT = 7037
```

**Description**

Line height of text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: text line height, in fp. The default value is adaptive to the font size.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: text line height, in fp. The default value is adaptive to the font size.</li> </ul>

**Since**: 20

### NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR = 7038
```

**Description**

Whether to enable entity recognition for selected text. This attribute supports the recognition of entity information such as phone numbers, email addresses, and URLs in the selected text, making it convenient for users to quickly make calls, send emails, or open URLs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable entity recognition for selected text. **1** to enable; **0** otherwise. The default value is **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether entity recognition for selected text is enabled. The value **1** indicates entity recognition is enabled, and **0** indicates the opposite.</li> </ul>

**Since**: 22

### NODE_TEXT_INPUT_SHOW_COUNTER

```c
NODE_TEXT_INPUT_SHOW_COUNTER = 7040
```

**Description**

Whether to show a counter and its style when the number of input characters exceeds a threshold. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to show a counter. **1** to show; **0** otherwise.</li> <li>.value[1]?.f32: Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1,<br>&nbsp;100]. If the value is a decimal, it is rounded down. If the value is out of the range, the attribute setting does not take effect. The default value is **-1**, meaning the counter is always shown.</li> <li>.value[2]?.i32: Whether to highlight the border when the number of entered characters exceeds the maximum. **1**<br>means to highlight; **0** otherwise.</li> <li>.object: Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is {@link ArkUI_ShowCounterConfig}.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the counter is shown. The value **1** means the counter is shown, and **0** means the opposite.</li> <li>.value[1].f32: Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1,<br>&nbsp;100].</li> <li>.value[2].i32: Whether the border is highlighted when the number of entered characters exceeds the maximum. **1**<br>indicates that the border is highlighted; **0** otherwise.</li> <li>.object: Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is {@link ArkUI_ShowCounterConfig}.</li> </ul>

**Since**: 22

### NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE

```c
NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE = 7041
```

**Description**

Text input controller.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Basic controller for text. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Basic controller for text. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_ELLIPSIS_MODE

```c
NODE_TEXT_INPUT_ELLIPSIS_MODE = 7042
```

**Description**

Text ellipsis mode of the single-line text box.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode), the default value is ARKUI_ELLIPSIS_MODE_END.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode).</li> </ul>

**Since**: 24

### NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION

```c
	  NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION = 7043
```

**Description**

Whether to enable orphan character optimization for text layout in the **TextInput** component. When set, the orphan character (the first character in the last line of a paragraph) is processed more efficiently to improve the text layout. When enabled, it adjusts line break points to avoid orphan characters as much as possible.<br>Note: The orphan character optimization feature takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not set to **ARKUI_WORD_BREAK_BREAK_ALL**.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The current state of this feature.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION = 7044
```

**Description**

Whether to enable leading punctuation compression of a text line.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether compress punctuation at the beginning of line.</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_INCLUDE_FONT_PADDING

```c
NODE_TEXT_INPUT_INCLUDE_FONT_PADDING = 7045
```

**Description**

Whether to add spacing to the top of the first line and the bottom of the last line of text in a single-line text box to avoid text truncation.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Enable include the font padding, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether include the font padding.</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_FALLBACK_LINE_SPACING

```c
NODE_TEXT_INPUT_FALLBACK_LINE_SPACING = 7046
```

**Description**

Whether the line height can be automatically adjusted based on the actual text height for multi-line text display. This enumerated value takes effect only when the line height is smaller than the actual text height.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether enable the feature, true means enable this feature, false means disable. The default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether fallback line spacing.</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_DIRECTION

```c
NODE_TEXT_INPUT_DIRECTION = 7047
```

**Description**

Text layout direction of the single-line text box.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: writing direction of the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: writing direction the text. The value is an enum of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection).</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE = 7048
```

**Description**

Drag preview style when the text in the text box is selected.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: selected drag preview style configuration. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: selected drag preview style configuration. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul>

**Since**: 23

### NODE_TEXT_INPUT_TEXT_OVERFLOW

```c
NODE_TEXT_INPUT_TEXT_OVERFLOW = 7049
```

**Description**

Display mode when the text is too long in the single-line text box.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: display mode when the text is too long [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow).</li> </ul>

**Since**: 24

### NODE_TEXT_INPUT_DECORATION

```c
NODE_TEXT_INPUT_DECORATION = 7050
```

**Description**

Text decorative line style and color of the single-line text box.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>?.object: Optional. The decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: The decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_LINEAR_GRADIENT

```c
NODE_TEXT_INPUT_LINEAR_GRADIENT = 7051
```

**Description**

Linear gradient effect of the text in the text box.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: start angle of the linear gradient. The setting takes effect only when <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>. A positive value indicates a clockwise rotation from the origin, (0, 0). The default value is <b>180</b>.</li> <li>.value[1].i32: direction of the linear gradient. When a direction other than <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> is set, the <b>angle</b> property is ignored. The parameter type is [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection).</li> <li>.value[2].i32: whether the colors are repeated. The default value is <b>false</b>.</li> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: start angle of the linear gradient. When <b>direction</b> is set to <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b>, <b>angle</b> at the set value; otherwise, it is at default value.</li> <li>.value[1].i32: direction of the linear gradient.</li> <li>.value[2].i32: whether the colors are repeated.</li> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_RADIAL_GRADIENT

```c
NODE_TEXT_INPUT_RADIAL_GRADIENT = 7052
```

**Description**

Radial gradient effect of the text in the text box.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the text.</li> <li>.value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text.</li> <li>.value[2]?.f32: radius of the radial gradient. The default value is <b>0</b>.</li> <li>.value[3]?.i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.</li> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X-coordinate of the radial gradient center relative to the upper left corner of the text.</li> <li>.value[1].f32: Y-coordinate of the radial gradient center relative to the upper left corner of the text.</li> <li>.value[2].f32: radius of the radial gradient. The default value is <b>0</b>.</li> <li>.value[3].i32: whether the colors are repeated. The value <b>1</b> means that the colors are repeated, and <b>0</b> means the opposite.</li> <li>.object: array of color stops, each of which consists of a color and its stop position. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). Invalid colors are automatically skipped. colors: colors of the color stops. stops: stop positions of the color stops. size: number of colors.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_INPUT_PUNCTUATION_OVERFLOW = 7053
```

**Description**

Whether to enable punctuation hanging at the end of a line for the **TextInput** component.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow, the default value is false.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable punctuation overflow.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_PLACEHOLDER

```c
NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA
```

**Description**

Defines the default placeholder text for the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: default placeholder text.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: default placeholder text.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_TEXT

```c
NODE_TEXT_AREA_TEXT
```

**Description**

Defines the default text content for the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: default text content.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: default text content.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_MAX_LENGTH

```c
NODE_TEXT_AREA_MAX_LENGTH
```

**Description**

Maximum number of characters in the text input.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: maximum number of characters in the text input.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: maximum number of characters in the text input.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_PLACEHOLDER_COLOR

```c
NODE_TEXT_AREA_PLACEHOLDER_COLOR
```

**Description**

Default placeholder text color when there is no input.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color value, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_PLACEHOLDER_FONT

```c
NODE_TEXT_AREA_PLACEHOLDER_FONT
```

**Description**

Defines the placeholder text font. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.f32: font size, in fp. Optional. The default value is <b>16.0</b>.</li> <li>.value[1]?.i32: font style [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). Optional. The default value is <b>ARKUI_FONT_STYLE_NORMAL</b>.</li> <li>.value[2]?.i32: font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). Optional. The default value is <b>ARKUI_FONT_WEIGHT_NORMAL</b>.</li> <li>?.string: font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2".</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: font size, in fp.</li> <li>.value[1].i32: font style [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).</li> <li>.value[2].i32: font weight [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).</li> <li>.string: font family. Multiple font families are separated by commas (,).</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CARET_COLOR

```c
NODE_TEXT_AREA_CARET_COLOR
```

**Description**

Caret color attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: background color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_EDITING

```c
NODE_TEXT_AREA_EDITING
```

**Description**

Editable state for the multi-line text box.<br> This attribute can be set and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to remain in the editable state. The value <b>true</b> means to remain in the editable state, and <b>false</b> means to exit the editable state.</li> </ul><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) for obtaining the attribute:**<br><ul> <li>.value[0].i32: whether to remain in the editable state. The value <b>true</b> means to remain in the editable state, and <b>false</b> means to exit the editable state.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_TYPE

```c
NODE_TEXT_AREA_TYPE
```

**Description**

Text area type. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: text box type [ArkUI_TextAreaType](capi-text-area-h.md#arkui_textareatype). The default value is <b>ARKUI_TEXTAREA_TYPE_NORMAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: text box type [ArkUI_TextAreaType](capi-text-area-h.md#arkui_textareatype).</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_SHOW_COUNTER

```c
NODE_TEXT_AREA_SHOW_COUNTER
```

**Description**

Whether to show a counter and its style when the number of input characters exceeds a threshold.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to show the counter. **1** to show; **0** otherwise. The default value is **0**.</li> <li>.value[1]?.f32: Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1,<br>&nbsp;100]. If the value is a decimal, it is rounded down. If the value is out of the range, the attribute setting does not take effect. The default value is **-1**, which means the counter is always shown.</li> <li>.value[2]?.i32: Whether to highlight the border when the number of entered characters exceeds the maximum. **1**<br>to highlight; **0** otherwise. The default value is **1**.</li> <li>.object: Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is {@link ArkUI_ShowCounterConfig}.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the counter is shown. **1** indicates the counter is shown; **0** otherwise.</li> <li>.value[1].f32: Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1,<br>&nbsp;100].</li> <li>.value[2].i32: Whether the border is highlighted when the number of entered characters exceeds the maximum. **1**<br>indicates that the border is highlighted, and **0** indicates the opposite.</li> <li>.object: Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is {@link ArkUI_ShowCounterConfig}.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_AREA_SELECTION_MENU_HIDDEN
```

**Description**

Whether to hide the text selection menu when the text box is long-pressed, double-tapped, or right-clicked.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to hide the text selection menu when the text box is long-pressed, double-click, or right-clicked. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the text selection menu is hidden when the text box is long-pressed, double-tapped, right-clicked.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_BLUR_ON_SUBMIT

```c
NODE_TEXT_AREA_BLUR_ON_SUBMIT
```

**Description**

Sets whether the multi-line text box loses focus after the Enter key is pressed to submit information. **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the text box loses focus.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the text box loses focus.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_INPUT_FILTER

```c
NODE_TEXT_AREA_INPUT_FILTER
```

**Description**

Regular expression for input filtering.<br> Only inputs that comply with the regular expression can be displayed. Other inputs are filtered out. For single-character input scenarios, only single-character matching is supported; for multi-character input scenarios (such as pasting), string matching is supported.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: regular expression.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: regular expression.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR
```

**Description**

Background color of the selected text.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: color value, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ENTER_KEY_TYPE

```c
NODE_TEXT_AREA_ENTER_KEY_TYPE
```

**Description**

Defines the type of the Enter key. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: type of the Enter key[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype). The default value is <b>ARKUI_ENTER_KEY_TYPE_DONE</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: type of the Enter key[ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype).</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS
```

**Description**

Whether to enable the input method when the **TextArea** component obtains focus in a way other than clicking.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable the input method when the **TextArea** component obtains focus in a way other than clicking. **1** means to enable, and **0** to disable. Default value: **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the input method is enabled when the component obtains focus. The value **1** means that the input method is enabled when the component obtains focus, and **0** means the opposite.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CARET_OFFSET

```c
NODE_TEXT_AREA_CARET_OFFSET
```

**Description**

Caret position.<br> Sets the position of the caret.<br> Returns the position information of the caret. If this API is called when the caret position is updated in the current frame, it will not take effect.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Length of characters from the beginning of the string to the position of the cursor.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Index value of the cursor position.</li> <li>.value[1].f32: indicates the x-coordinate value of the cursor relative to the text box.</li> <li>.value[2].f32: indicates the y-coordinate value of the cursor relative to the text box.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CONTENT_RECT

```c
NODE_TEXT_AREA_CONTENT_RECT
```

**Description**

Position of the edited text area relative to the component and its size.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: X-coordinate, in px.</li> <li>.value[1].f32: Y-coordinate, in px.</li> <li>.value[2].f32: content width, in px.</li> <li>.value[3].f32: content height.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CONTENT_LINE_COUNT

```c
NODE_TEXT_AREA_CONTENT_LINE_COUNT
```

**Description**

Number of lines of the edited text.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of lines of the edited text.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_TEXT_SELECTION

```c
NODE_TEXT_AREA_TEXT_SELECTION
```

**Description**

Text selection range, which will be highlighted, when the component is focused.<br> This enumerated value works only when the value of **selectionStart** is less than that of **selectionEnd**.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: start position of the text selection.</li> <li>.value[1].i32: end position of the text selection.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: start position of the text selection.</li> <li>.value[1].i32: end position of the text selection.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ENABLE_AUTO_FILL

```c
NODE_TEXT_AREA_ENABLE_AUTO_FILL
```

**Description**

Whether to enable autofill.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable autofill. **1** indicates to enable, and **0** indicates the opposite. Default value: **1**.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether autofill is enabled. **1** indicates enabled, and **0** indicates disabled.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_CONTENT_TYPE

```c
NODE_TEXT_AREA_CONTENT_TYPE
```

**Description**

Autofill type.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype). It is used to specify the auto filled content type so that the system can provide more accurate autofill suggestions.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype). It is used to specify the auto filled content type so that the system can provide more accurate autofill suggestions.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS
```

**Description**

Whether to show the keyboard when the text box obtains focus.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to pop up the keyboard.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether to pop up the keyboard.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_NUMBER_OF_LINES

```c
NODE_TEXT_AREA_NUMBER_OF_LINES
```

**Description**

When this property is set, the height of the textArea component is calculated using this property.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: set the value of numberOfLines.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Set the value of numberOfLines.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_LETTER_SPACING

```c
NODE_TEXT_AREA_LETTER_SPACING = 8023
```

**Description**

Letter spacing of the **TextArea** component.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: letter spacing. The default unit is fp.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: letter spacing. The default unit is fp.</li> </ul>

**Since**: 15

### NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024
```

**Description**

Whether to enable preview text for the **TextArea** component.<br> This attribute can be set, reset, and obtained as required through APIs.<br> "Preview text" describes a temporary text staging state. The preview text feature must be enabled in the input method. During text input, before a candidate word is confirmed, marked text is displayed in the text box. For example, when entering Chinese characters via Pinyin, the Pinyin letters are displayed in the input box before the candidate word is confirmed. This state is called preview.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable preview tex.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to enable preview tex.</li> </ul>

**Since**: 15

### NODE_TEXT_AREA_HALF_LEADING

```c
NODE_TEXT_AREA_HALF_LEADING = 8025
```

**Description**

Whether to enable half leading.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to center text vertically. The default value is <b>false</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether to center text vertically.</li> </ul>

**Since**: 18

### NODE_TEXT_AREA_KEYBOARD_APPEARANCE

```c
NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026
```

**Description**

Set the keyboard style of textArea<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: keyboard style, the parameter type is ArkUI_KeyboardAppearanceType.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: keyboard style, the parameter type is ArkUI_KeyboardAppearanceType.</li> </ul>

**Since**: 15

### NODE_TEXT_AREA_MAX_LINES

```c
NODE_TEXT_AREA_MAX_LINES = 8027
```

**Description**

Maximum number of lines that can be displayed with the inline style in the editing state.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: max lines count.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: max lines count.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_LINE_SPACING

```c
NODE_TEXT_AREA_LINE_SPACING = 8028
```

**Description**

Line spacing of text in the text box.<br> This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: line spacing value.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: line spacing value.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_MIN_LINES

```c
NODE_TEXT_AREA_MIN_LINES = 8029
```

**Description**

Minimum number of lines for the node. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Minimum number of lines. The value range is [1, +∞). The setting does not take effect when 0 or a negative value is passed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Minimum number of lines. The value range is [1, +∞).</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL

```c
NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL = 8030
```

**Description**

Maximum number of lines for the node when scrolling is enabled. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Maximum number of lines when scrolling is enabled. Value range: [1, +∞).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Maximum number of lines when scrolling is enabled. Value range: [1, +∞).</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_LINE_HEIGHT

```c
NODE_TEXT_AREA_LINE_HEIGHT = 8031
```

**Description**

Line height of text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Text line height, in fp. The default value is adaptive to the font size.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Text line height, in fp.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_BAR_STATE

```c
NODE_TEXT_AREA_BAR_STATE = 8032
```

**Description**

Scrollbar status of the text input box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Scrollbar status of the text input box. The parameter type is [ArkUI_BarState](capi-scroll-h.md#arkui_barstate). The default value is <b>ARKUI_BAR_STATE_AUTO</b>, which indicates the scrollbar is displayed as needed (displayed upon touch and automatically disappears after 2 seconds).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Scrollbar status of the text input box. The parameter type is [ArkUI_BarState](capi-scroll-h.md#arkui_barstate).</li> </ul>

**Since**: 22

### NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR = 8033
```

**Description**

Whether to enable entity recognition for selected text, supporting the recognition of entity information such as phone numbers, email addresses, and URLs in the selected text, making it convenient for users to quickly make calls, send emails, or open URLs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable entity recognition for selected text. <b>1</b> to enable; <b>0</b> otherwise. Default value: <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether entity recognition for selected text is enabled. <b>1</b> indicates enabled, and <b>0</b> indicates disabled.</li> </ul>

**Since**: 22

### NODE_TEXT_AREA_SCROLL_BAR_COLOR

```c
NODE_TEXT_AREA_SCROLL_BAR_COLOR = 8035
```

**Description**

Scrollbar color of the text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.data[0].u32: Scrollbar color, in 0xARGB format. Default value: <b>0x66182431</b>, indicating gray.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.data[0].u32: Scrollbar color, in 0xARGB format.</li> </ul>

**Since**: 22

### NODE_TEXT_AREA_CUSTOM_KEYBOARD

```c
NODE_TEXT_AREA_CUSTOM_KEYBOARD = 8036
```

**Description**

Custom keyboard of the text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md).</li> <li>.value[0]?.i32: Whether the custom keyboard supports the avoidance feature. <b>1</b> indicates support for avoidance, and <b>0</b> indicates the opposite. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md).</li> <li>.value[0].i32: Whether the custom keyboard supports the avoidance feature. <b>1</b> indicates support for avoidance, and <b>0</b> indicates the opposite.</li> </ul>

**Since**: 22

### NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE

```c
NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE = 8037
```

**Description**

Text area controller.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Basic controller of the text content. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Basic controller of the text content. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_ELLIPSIS_MODE

```c
NODE_TEXT_AREA_ELLIPSIS_MODE = 8038
```

**Description**

Text ellipsis mode of the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> This attribute has the following configuration dependencies: <ul> <li>This attribute takes effect only when <b>NODE_TEXT_AREA_TEXT_OVERFLOW</b> is set to <b>ARKUI_TEXT_OVERFLOW_ELLIPSIS</b>.</li> <li>When <b>TEXT_OVERFLOW</b> is set to <b>ARKUI_TEXT_OVERFLOW_CLIP</b>, the <b>ELLIPSIS_MODE</b> setting does not take effect.</li> <li>It is recommended to set <b>TEXT_OVERFLOW</b> to <b>ELLIPSIS</b> first, and then set <b>ELLIPSIS_MODE</b> to a specified ellipsis position.</li> </ul><br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Ellipsis mode. The parameter type [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode). For details about the enumerated values, see the [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode) description. The default value is <b>ARKUI_ELLIPSIS_MODE_END</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Enum for text ellipsis position [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode), used to determine the ellipsis position when text exceeds the limit.</li> </ul>

**Since**: 24

### NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION = 8039
```

**Description**

Whether to enable orphan character optimization for text layout in the <b>TextArea</b> component. When set, the orphan character (the first character in the last line of a paragraph) is processed more efficiently to improve the text layout. When enabled, it adjusts line break points to avoid orphan characters as much as possible. The orphan character optimization feature takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not set to <b>ARKUI_WORD_BREAK_BREAK_ALL</b>.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable orphan character optimization. This feature takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not <b>ARKUI_WORD_BREAK_BREAK_ALL</b>. <b>1</b> to enable; <b>0</b> otherwise. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether orphan character optimization is enabled. The value <b>1</b> means enabled, and <b>0</b> means disabled.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION = 8040
```

**Description**

Whether to enable the feature of compressing punctuations at the beginning of a text line. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable leading punctuation compression. <b>1</b> indicates to enable, and <b>0</b> indicates the opposite. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether leading punctuation compression is enabled. <b>1</b> indicates enabled, and <b>0</b> indicates disabled.</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_INCLUDE_FONT_PADDING

```c
NODE_TEXT_AREA_INCLUDE_FONT_PADDING = 8041
```

**Description**

Whether to add spacing to the first and last lines of text in a multi-line text box to avoid text truncation.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to add spacing to the first and last lines of text in a text box to avoid text truncation. <b>1</b> to add; <b>0</b> otherwise. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether spacing is added to the first and last lines of text in a text box. <b>1</b> indicates spacing is added; <b>0</b> otherwise.</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_FALLBACK_LINE_SPACING

```c
NODE_TEXT_AREA_FALLBACK_LINE_SPACING = 8042
```

**Description**

Whether the line height can be automatically adjusted based on the actual text height for multi-line text display. This enumerated value takes effect only when the line height is smaller than the actual text height.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether the line height can be automatically adjusted based on the actual text height. <b>1</b> to be adjusted; <b>0</b> otherwise. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the line height can be automatically adjusted based on the actual text height. <b>1</b> means that the line height can be automatically adjusted; <b>0</b> otherwise.</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_HORIZONTAL_SCROLLING

```c
NODE_TEXT_AREA_HORIZONTAL_SCROLLING = 8043
```

**Description**

Whether to enable horizontal scrolling for a multi-line text box when the text width exceeds the width of the content area in the text box. The default value is <b>0</b>, meaning that the text will be automatically wrapped by the text box.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable horizontal scrolling. <b>1</b> to enable; <b>0</b> otherwise. Default value: <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether horizontal scrolling is enabled. <b>1</b> indicates enabled, and <b>0</b> indicates disabled.</li> </ul>

**Since**: 24

### NODE_TEXT_AREA_DIRECTION

```c
NODE_TEXT_AREA_DIRECTION = 8044
```

**Description**

Text layout direction of the multi-line text box.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Text layout direction. The value is an enumerated value of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). The default value is <b>ARKUI_TEXT_DIRECTION_DEFAULT</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Text layout direction. For details about the values and meanings, see the enumerated values of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection).</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE = 8045
```

**Description**

Drag preview style when the text in the multi-line text box is selected.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-selecteddragpreviewstyle.md).</li> </ul>

**Since**: 23

### NODE_TEXT_AREA_TEXT_OVERFLOW

```c
NODE_TEXT_AREA_TEXT_OVERFLOW = 8046
```

**Description**

Display mode when the text is too long in the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Display mode when the text is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). The default value is <b>ARKUI_TEXT_OVERFLOW_CLIP</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Display mode when the text is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow).</li> </ul>

**Since**: 24

### NODE_TEXT_AREA_DECORATION

```c
NODE_TEXT_AREA_DECORATION = 8047
```

**Description**

Text decorative line style and color of the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>?.object: Decoration style options. This parameter is optional. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md). When not passed, no decoration line is added.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: Decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_LINEAR_GRADIENT

```c
NODE_TEXT_AREA_LINEAR_GRADIENT = 8048
```

**Description**

Linear gradient effect of the text in the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].f32: Start angle of the linear gradient, in degree. When the linear gradient direction is <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection), the start angle of the linear gradient takes effect. Otherwise, the linear gradient direction is used as the main layout mode. The value range is (-∞,+∞). A positive value indicates a clockwise rotation from the origin (0, 0). When the value exceeds 360, the remainder of 360 is used. The default value is <b>180</b>.</li> <li>.value[1].i32: Direction of the linear gradient. The value is an enumerated value of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection). If the linear gradient direction is set to a value other than <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection), the start angle of the linear gradient does not take effect. Default value: <b>ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM</b> of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection).</li> <li>.value[2].i32: Whether the gradient colors are repeated. The value <b>0</b> indicates that the gradient colors are not repeated, and <b>1</b> indicates that the gradient colors are repeated. The default value is <b>0</b>.</li> <li>.object: Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). <b>colors</b>: colors of the color stops, in 0xARGB format. For example, <b>0xFFFF0000</b> indicates red. <b>stops</b>: stop positions of the color stops. The value range is [0, 1.0]. <b>0</b> represents the start of the gradient container, and <b>1.0</b> represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value. <b>size</b>: number of colors. If the value is smaller than the length of the <b>colors</b> array, only the first <b>size</b> colors take effect. Values greater than the <b>colors</b> array length, values less than or equal to 0, or invalid values are not recommended.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].f32: Start angle of the linear gradient, in degree. When the direction of the linear gradient is <b>ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM</b> of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection), the start angle is the set value. In other cases, the default value <b>0</b> is used.</li> <li>.value[1].i32: Direction of the linear gradient. For details about the values and meanings, see [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection).</li> <li>.value[2].i32: Whether the gradient colors are repeated. The value <b>0</b> indicates that the gradient colors are not repeated, and <b>1</b> indicates that the gradient colors are repeated. The default value is <b>0</b>.</li> <li>.object: Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). <b>colors</b>: colors of the color stops, in 0xARGB format. For example, <b>0xFFFF0000</b> indicates red. <b>stops</b>: stop positions of the color stops. The value range is [0, 1.0]. <b>0</b> represents the start of the gradient container, and <b>1.0</b> represents the end. <b>size</b>: number of effective gradient colors.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_RADIAL_GRADIENT

```c
NODE_TEXT_AREA_RADIAL_GRADIENT = 8049
```

**Description**

Radial gradient effect of the text in the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the multi-line text box, in vp. The default value is half the width of the multi-line text input box.</li> <li>.value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the multi-line text box, in vp. The default value is half the height of the multi-line text input box.</li> <li>.value[2]?.f32: Radius of the radial gradient. The value range is [0, +∞), and the default value is <b>0</b>. If a negative value is passed, the setting does not take effect.</li> <li>.value[3]?.i32: Whether the gradient colors are repeated. The value <b>0</b> indicates that the gradient colors are not repeated, and <b>1</b> indicates that the gradient colors are repeated. The default value is <b>0</b>.</li> <li>.object: Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). <b>colors</b>: colors of the color stops, in 0xARGB format. For example, <b>0xFFFF0000</b> indicates red. <b>stops</b>: stop positions of the color stops. The value range is [0, 1.0]. <b>0</b> represents the start of the gradient container, and <b>1.0</b> represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value. <b>size</b>: number of colors. If the value is smaller than the length of the <b>colors</b> array, only the first <b>size</b> colors take effect. Values greater than the <b>colors</b> array length, values less than or equal to 0, or invalid values are not recommended.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0]?.f32: X-coordinate of the radial gradient center relative to the upper left corner of the multi-line text box, in vp.</li> <li>.value[1]?.f32: Y-coordinate of the radial gradient center relative to the upper left corner of the multi-line text box, in vp.</li> <li>.value[2]?.f32: Radius of the radial gradient, in vp. Default value: <b>0</b>.</li> <li>.value[3]?.i32: Whether the gradient colors are repeated. The value <b>0</b> indicates that the gradient color is not repeated, and <b>1</b> indicates that the gradient color is repeated. The default value is <b>0</b>.</li> <li>.object: Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md). <b>colors</b>: colors of the color stops, in 0xARGB format. For example, <b>0xFFFF0000</b> indicates red. <b>stops</b>: stop positions of the color stops. The value range is [0, 1.0]. <b>0</b> represents the start of the gradient container, and <b>1.0</b> represents the end. <b>size</b>: number of effective gradient colors.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_AREA_PUNCTUATION_OVERFLOW = 8050
```

**Description**

Whether to enable punctuation hanging at the end of a line for the <b>TextArea</b> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable punctuation hanging at the end of a line. The value <b>1</b> means to enable, and <b>0</b> means the opposite. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether punctuation hanging at the end of a line is enabled. <b>1</b> indicates enabled, <b>0</b> indicates disabled.</li> </ul>

**Since**: 26.0.0


