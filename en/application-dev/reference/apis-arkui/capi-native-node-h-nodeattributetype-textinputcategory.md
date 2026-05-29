# ArkUI_NodeAttributeType (Text Input Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6; @kangshihui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for text input components including **TextInput** and **TextArea**.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_TEXT_INPUT_PLACEHOLDER

```c
NODE_TEXT_INPUT_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT = 7000
```

Default placeholder text of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Default placeholder text.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Default placeholder text.|

## NODE_TEXT_INPUT_TEXT

```c
NODE_TEXT_INPUT_TEXT = 7001
```

Default text of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Default text content.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Default text content.|

## NODE_TEXT_INPUT_CARET_COLOR

```c
NODE_TEXT_INPUT_CARET_COLOR = 7002
```

Caret color attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Caret color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Caret color, in 0xARGB format.|

## NODE_TEXT_INPUT_CARET_STYLE

```c
NODE_TEXT_INPUT_CARET_STYLE = 7003
```

Caret style attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Caret width, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Caret width, in vp.|

## NODE_TEXT_INPUT_SHOW_UNDERLINE

```c
NODE_TEXT_INPUT_SHOW_UNDERLINE = 7004
```

Underline of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to show an underline. **true** means to show an underline; **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether an underline is shown. The value **1** means that an underline is shown, and **0** means the opposite.|

## NODE_TEXT_INPUT_MAX_LENGTH

```c
NODE_TEXT_INPUT_MAX_LENGTH = 7005
```

Maximum number of characters in the text input. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Maximum number of characters in the text input, without a unit.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Maximum number of characters in the text input.|

## NODE_TEXT_INPUT_ENTER_KEY_TYPE

```c
NODE_TEXT_INPUT_ENTER_KEY_TYPE = 7006
```

Type of the **Enter** key. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Type of the **Enter** key, specified using the [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype) enum. The default value is **ARKUI_ENTER_KEY_TYPE_DONE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the **Enter** key, specified using the [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype) enum.|

## NODE_TEXT_INPUT_PLACEHOLDER_COLOR

```c
NODE_TEXT_INPUT_PLACEHOLDER_COLOR = 7007
```

Default placeholder text color when there is no input. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format.|

## NODE_TEXT_INPUT_PLACEHOLDER_FONT

```c
NODE_TEXT_INPUT_PLACEHOLDER_FONT = 7008
```

Default placeholder text font (including the size, weight, style, and font family) when there is no input. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | Font size, in fp. This parameter is optional. The default value is **16.0**.|
| .value[1]?.i32 | Font style, specified using the [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle) enum. This parameter is optional. The default value is **ARKUI_FONT_STYLE_NORMAL**.|
| .value[2]?.i32 | Font weight, specified using the [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) enum. This parameter is optional. The default value is **ARKUI_FONT_WEIGHT_NORMAL**.|
| ?.string | Font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2".|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Font size, in fp.|
| .value[1].i32 | Font style, specified using the [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle) enum.|
| .value[2].i32 | Font weight, specified using the [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) enum.|
| .string | Font family. Multiple font families are separated by commas (,).|

## NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_INPUT_ENABLE_KEYBOARD_ON_FOCUS = 7009
```

Whether to enable the input method when the component obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the input method when the component obtains focus. **true** means to enable the input method; **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the input method is enabled when the component obtains focus. The value **1** means that the input method is enabled when the component obtains focus, and **0** means the opposite.|

## NODE_TEXT_INPUT_TYPE

```c
NODE_TEXT_INPUT_TYPE = 7010
```

Text input type. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text input type, specified using the [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype) enum. The default value is **ARKUI_TEXTINPUT_TYPE_NORMAL**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text input type, specified using the [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype) enum.|

## NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_INPUT_SELECTED_BACKGROUND_COLOR = 7011
```

Background color of the selected text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format.|

## NODE_TEXT_INPUT_SHOW_PASSWORD_ICON

```c
NODE_TEXT_INPUT_SHOW_PASSWORD_ICON = 7012
```

Whether to display the password icon at the end of the password text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to display the password icon. **true** means to display; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the password icon is displayed. The value **1** means that the password icon is displayed, and **0** means the opposite.|

## NODE_TEXT_INPUT_EDITING

```c
NODE_TEXT_INPUT_EDITING = 7013
```

Editable state for the single-line text box. This attribute can be set and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to remain in the editable state. **true** means to remain in the editable state, and **false** means to exit the editable state.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether to remain in the editable state. **true** means to remain in the editable state, and **false** means to exit the editable state.|

## NODE_TEXT_INPUT_CANCEL_BUTTON

```c
NODE_TEXT_INPUT_CANCEL_BUTTON = 7014
```

Style of the cancel button on the right of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Button style, specified using the [ArkUI_CancelButtonStyle](capi-native-type-h.md#arkui_cancelbuttonstyle) enum. The default value is **ARKUI_CANCELBUTTON_STYLE_INPUT**.|
| .value[1]?.f32 | Button icon size, in vp.|
| .value[2]?.u32 | Button icon color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|
| ?.string | Button icon address. The value is the local address of an image, for example, **/pages/icon.png**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Button style, specified using the [ArkUI_CancelButtonStyle](capi-native-type-h.md#arkui_cancelbuttonstyle) enum.|
| .value[1].f32 | Button icon size, in vp.|
| .value[2].u32 | Button icon color, in 0xARGB format.|
| .string | Button icon address.|

## NODE_TEXT_INPUT_TEXT_SELECTION

```c
NODE_TEXT_INPUT_TEXT_SELECTION = 7015
```

Text selection area, which will be highlighted, for the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Start position of the text selection.|
| .value[1].i32 | End position of the text selection.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Start position of the text selection.|
| .value[1].i32 | End position of the text selection.|

## NODE_TEXT_INPUT_UNDERLINE_COLOR

```c
NODE_TEXT_INPUT_UNDERLINE_COLOR = 7016
```

Color of the underline when it is shown. The default underline color configured for the theme is **'0x33182431'**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the underline applied to the text being typed in. This parameter is mandatory. The value is in 0xARGB format.|
| .value[1].u32 | Color of the underline applied to the text in the normal state. This parameter is mandatory. The value is in 0xARGB format.|
| .value[2].u32 | Color of the underline applied to the text when an error is detected. This parameter is mandatory. The value is in 0xARGB format.|
| .value[3].u32 | Color of the underline applied to the text when it is disabled. This parameter is mandatory. The value is in 0xARGB format.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the underline applied to the text being typed in. The value is in 0xARGB format.|
| .value[1].u32 | Color of the underline applied to the text in the normal state. The value is in 0xARGB format.|
| .value[2].u32 | Color of the underline applied to the text when an error is detected. The value is in 0xARGB format.|
| .value[3].u32 | Color of the underline applied to the text when it is disabled. The value is in 0xARGB format.|

## NODE_TEXT_INPUT_ENABLE_AUTO_FILL

```c
NODE_TEXT_INPUT_ENABLE_AUTO_FILL = 7017
```

Whether to enable autofill.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable autofill. The default value is **true**.<br>**true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether autofill is enabled.|

## NODE_TEXT_INPUT_CONTENT_TYPE

```c
NODE_TEXT_INPUT_CONTENT_TYPE = 7018
```

Autofill type.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype).|

## NODE_TEXT_INPUT_PASSWORD_RULES

```c
NODE_TEXT_INPUT_PASSWORD_RULES = 7019
```

Rules for generating passwords. When autofill is used, these rules are transparently transmitted to Password Vault for generating a new password.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Rules for generating passwords.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Rules for generating passwords.|

## NODE_TEXT_INPUT_SELECT_ALL

```c
NODE_TEXT_INPUT_SELECT_ALL = 7020
```

Whether to select all text in the initial state. This attribute is not available for the inline input style.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to select all text. The default value is **false**.<br>**true** to select; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether all text is selected in the initial state.|

## NODE_TEXT_INPUT_INPUT_FILTER

```c
NODE_TEXT_INPUT_INPUT_FILTER = 7021
```

Regular expression for input filtering. Only inputs that comply with the regular expression can be displayed. Other inputs are filtered out. For single-character input scenarios, only single-character matching is supported; for multi-character input scenarios (such as pasting), string matching is supported.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Regular expression.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Regular expression.|

## NODE_TEXT_INPUT_STYLE

```c
NODE_TEXT_INPUT_STYLE = 7022
```

Text box style (default style or inline input style). The inline input style is only available when [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_NORMAL**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text input style. The parameter type is [ArkUI_TextInputStyle](capi-native-type-h.md#arkui_textinputstyle). The default value is **ARKUI_TEXTINPUT_STYLE_DEFAULT**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text input style. The parameter type is [ArkUI_TextInputStyle](capi-native-type-h.md#arkui_textinputstyle).|

## NODE_TEXT_INPUT_CARET_OFFSET

```c
NODE_TEXT_INPUT_CARET_OFFSET = 7023
```

Caret position.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
Sets the position of the caret.<br>
Returns the position information of the caret. If this API is called when the caret position is updated in the current frame, it will not take effect.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Length from the start of the string to the position where the caret is located.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Index of the caret position.|
| .value[1].f32 | X coordinate of the caret relative to the text box.|
| .value[2].f32 | Y coordinate of the caret relative to the text box.|

## NODE_TEXT_INPUT_CONTENT_RECT

```c
NODE_TEXT_INPUT_CONTENT_RECT = 7024
```

Position of the edited text area relative to the component and its size.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 12


**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate.|
| .value[1].f32 | Y-coordinate.|
| .value[2].f32 | Content width.|
| .value[3].f32 | Content height.|

## NODE_TEXT_INPUT_CONTENT_LINE_COUNT

```c
NODE_TEXT_INPUT_CONTENT_LINE_COUNT = 7025
```

Number of lines of the edited text.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 12


**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of lines of the edited text.|

## NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_INPUT_SELECTION_MENU_HIDDEN = 7026
```

Whether to hide the text selection menu when the text box is long-pressed, double-tapped, or right-clicked. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to hide the text selection menu when the text box is long-pressed, double-tapped, or right-clicked. The default value is **false**.<br>**true**: The system text selection menu is hidden when a user clicks the text box cursor, long-presses the text box, double-taps the text box, triple-taps the text box, or right-clicks the text box.<br>**false**: The system text selection menu is displayed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the text selection menu is hidden when the text box is long-pressed, double-tapped, or right-clicked.|

## NODE_TEXT_INPUT_BLUR_ON_SUBMIT

```c
NODE_TEXT_INPUT_BLUR_ON_SUBMIT = 7027
```

Whether the text box loses focus after the **Enter** key is pressed to submit information.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the text box loses focus after the **Enter** key is pressed to submit information. The default value is **true**.<br>**true**: The text box loses focus. **false**: The text box does not lose focus.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the text box loses focus after the **Enter** key is pressed to submit information.|

## NODE_TEXT_INPUT_CUSTOM_KEYBOARD

```c
NODE_TEXT_INPUT_CUSTOM_KEYBOARD = 7028
```

Custom keyboard.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0]?.i32 | Whether the custom keyboard supports avoidance. The default value is **false**.<br>**true** to support; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0].i32 | Whether the custom keyboard supports avoidance.|

## NODE_TEXT_INPUT_WORD_BREAK

```c
NODE_TEXT_INPUT_WORD_BREAK = 7029
```

Line break rule. This attribute can be set, reset, and obtained as required through APIs. It takes effect only when the component is in the inline input editing state.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Line break rule. The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak). The default value is **ARKUI_WORD_BREAK_BREAK_WORD**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Line break rule. The parameter type is [ArkUI_WordBreak](capi-native-type-h.md#arkui_wordbreak).|

## NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_INPUT_SHOW_KEYBOARD_ON_FOCUS = 7030
```

Whether to show the keyboard when the text box obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to show the keyboard. **true** to show; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the keyboard is shown.|

## NODE_TEXT_INPUT_NUMBER_OF_LINES

```c
NODE_TEXT_INPUT_NUMBER_OF_LINES = 7031
```

Number of lines in the [TextInput](arkui-ts/ts-basic-components-textinput.md) component, which can be used to work out the height of the component. For example, if **numberOfLines** is set to **3**, the component displays three lines of text by default.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Number of lines.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of lines.|

## NODE_TEXT_INPUT_LETTER_SPACING

```c
NODE_TEXT_INPUT_LETTER_SPACING = 7032
```

Letter spacing of the [TextInput](arkui-ts/ts-basic-components-textinput.md) component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | [Letter spacing](arkui-ts/ts-basic-components-text.md#letterspacing). The default unit is fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Letter spacing. The default unit is fp.|

## NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_INPUT_ENABLE_PREVIEW_TEXT = 7033
```

Whether to enable preview text for the [TextInput](arkui-ts/ts-basic-components-textinput.md) component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable preview text. The default value is **true**.<br>**true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether preview text is enabled.|

## NODE_TEXT_INPUT_HALF_LEADING

```c
NODE_TEXT_INPUT_HALF_LEADING = 7034
```

Whether to enable half leading.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable half leading. The default value is **false**.<br>**true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether half leading is enabled.|

## NODE_TEXT_INPUT_KEYBOARD_APPEARANCE

```c
NODE_TEXT_INPUT_KEYBOARD_APPEARANCE = 7035
```

Appearance of the keyboard when the text box is started.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance). The default value is **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**.|

## NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION

```c
NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036
```

Whether to enable the autofill animation.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the autofill animation.<br>**true** to enable; **false** otherwise.<br>The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the autofill animation is enabled. When enabled, the animation only takes effect for text boxes whose [ArkUI_TextInputType](capi-native-type-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_PASSWORD**, **ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD**, or **ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD**.|

## NODE_TEXT_INPUT_LINE_HEIGHT

```c
NODE_TEXT_INPUT_LINE_HEIGHT = 7037
```

Line height of text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Numeric value for the text line height. Default value: adaptive to the font size. If this parameter is set to **undefined**, the text line height is **5**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Numeric value for the text line height.|

## NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR = 7038
```

Whether to enable entity recognition for selected text.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable entity recognition for selected text. **true** to enable; **false** otherwise. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether entity recognition for selected text is enabled.|

## NODE_TEXT_INPUT_SHOW_COUNTER

```c
NODE_TEXT_INPUT_SHOW_COUNTER = 7040
```

Whether to show a counter and its style when the number of input characters exceeds a threshold. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to show a counter. **true** to show; **false** otherwise.|
| .value[1]?.f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100]. If the value is a decimal, it is rounded down. If the value is out of the range, the attribute setting does not take effect.|
| .value[2]?.i32 | Whether to highlight the border when the number of entered characters exceeds the maximum. **true** means to highlight; **false** otherwise.|
| .object | Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the counter is shown.|
| .value[1].f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100].|
| .value[2].i32 | Whether the border is highlighted when the number of entered characters exceeds the maximum. **true** indicates that the border is highlighted; **false** otherwise. The default value is **true**.|
| .object | Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).|

## NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE

```c
NODE_TEXT_INPUT_TEXT_CONTENT_CONTROLLER_BASE = 7041
```

Text input controller.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .object | Basic controller for text. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Basic controller for text. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).|

## NODE_TEXT_INPUT_ELLIPSIS_MODE

```c
NODE_TEXT_INPUT_ELLIPSIS_MODE = 7042
```

Text ellipsis position of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode). The default value is **ARKUI_ELLIPSIS_MODE_END**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode).|

## NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION = 7044
```

Whether to enable the feature of compressing punctuations at the beginning of a text line. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the feature of compressing punctuations at the beginning of a text line.<br>**true** to enable; **false** otherwise. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the feature of compressing punctuations is enabled at the beginning of a text line.|

## NODE_TEXT_INPUT_INCLUDE_FONT_PADDING

```c
NODE_TEXT_INPUT_INCLUDE_FONT_PADDING = 7045
```

Whether to add spacing to the top of the first line and the bottom of the last line of text in a single-line text box to avoid text truncation.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to add spacing to the top of the first line and the bottom of the last line of text in a single-line text box to avoid text truncation. **true** to add; **false** otherwise. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether spacing is added to the top of the first line and the bottom of the last line. **true** indicates spacing is added; **false** otherwise.|

## NODE_TEXT_INPUT_FALLBACK_LINE_SPACING

```c
NODE_TEXT_INPUT_FALLBACK_LINE_SPACING = 7046
```

Whether the line height can be automatically adjusted based on the actual text height for multi-line text overlay. This enumerated value takes effect only when the line height is smaller than the actual text height.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **true** to be adjusted; **false** otherwise. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **true** means that the line height can be automatically adjusted; **false** otherwise.|

## NODE_TEXT_INPUT_DIRECTION

```c
NODE_TEXT_INPUT_DIRECTION = 7047
```

Text layout direction of the single-line text box.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text layout direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). The default value is **ARKUI_TEXT_DIRECTION_DEFAULT**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text layout direction. For details about the values and meanings, see the enumerated values of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).|

## NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_INPUT_SELECTED_DRAG_PREVIEW_STYLE = 7048
```

Drag preview style when the text in the text box is selected.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .object | Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).|

## NODE_TEXT_INPUT_TEXT_OVERFLOW

```c
NODE_TEXT_INPUT_TEXT_OVERFLOW = 7049
```

Display mode when the text is too long in the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Display mode when the text is too long, specified using the [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow) enum. The default value is **ARKUI_TEXT_OVERFLOW_ELLIPSIS** in the non-editing state for the inline mode and **ARKUI_TEXT_OVERFLOW_CLIP** in the editing state for the inline mode.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Display mode when the text is too long, specified using the [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow) enum.|

## NODE_TEXT_INPUT_DECORATION

```c
NODE_TEXT_INPUT_DECORATION = 7050
```

Text decorative line style and color of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24


**Parameters**

| Name| Description|
| -- | -- |
| .object | Decoration style options. This parameter is optional. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).|


## NODE_TEXT_AREA_PLACEHOLDER

```c
NODE_TEXT_AREA_PLACEHOLDER = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA = 8000
```

Default placeholder text of the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Default placeholder text.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Default placeholder text.|

## NODE_TEXT_AREA_TEXT

```c
NODE_TEXT_AREA_TEXT = 8001
```

Default text content of the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Default text content.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Default text content.|

## NODE_TEXT_AREA_MAX_LENGTH

```c
NODE_TEXT_AREA_MAX_LENGTH = 8002
```

Maximum number of characters in the text input. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Maximum number of characters in the text input.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Maximum number of characters in the text input.|

## NODE_TEXT_AREA_PLACEHOLDER_COLOR

```c
NODE_TEXT_AREA_PLACEHOLDER_COLOR = 8003
```

Default placeholder text color when there is no input. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format.|

## NODE_TEXT_AREA_PLACEHOLDER_FONT

```c
NODE_TEXT_AREA_PLACEHOLDER_FONT = 8004
```

Default placeholder text font (including the size, weight, style, and font family) when there is no input. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | Font size, in fp. This parameter is optional. The default value is **16.0**.|
| .value[1]?.i32 | Font style, specified using the [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle) enum. This parameter is optional. The default value is **ARKUI_FONT_STYLE_NORMAL**.|
| .value[2]?.i32 | Font weight, specified using the [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) enum. This parameter is optional. The default value is **ARKUI_FONT_WEIGHT_NORMAL**.|
| ?.string | Font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2".|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Font size, in fp.|
| .value[1].i32 | Font style, specified using the [ArkUI_FontStyle](capi-native-type-h.md#arkui_fontstyle) enum.|
| .value[2].i32 | Font weight, specified using the [ArkUI_FontWeight](capi-native-type-h.md#arkui_fontweight) enum.|
| .string | Font family. Multiple font families are separated by commas (,).|

## NODE_TEXT_AREA_CARET_COLOR

```c
NODE_TEXT_AREA_CARET_COLOR = 8005
```

Caret color attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Background color, in 0xARGB format.|

## NODE_TEXT_AREA_EDITING

```c
NODE_TEXT_AREA_EDITING = 8006
```

Editable state for the multi-line text box. This attribute can be set and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to remain in the editable state. **true** means to remain in the editable state, and **false** means to exit the editable state.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether to remain in the editable state. **true** means to remain in the editable state, and **false** means to exit the editable state.|

## NODE_TEXT_AREA_TYPE

```c
NODE_TEXT_AREA_TYPE = 8007
```

Text area type. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text area type, specified using the [ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype) enum. The default value is **ARKUI_TEXTAREA_TYPE_NORMAL**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text area type, specified using the [ArkUI_TextAreaType](capi-native-type-h.md#arkui_textareatype) enum.|

## NODE_TEXT_AREA_SHOW_COUNTER

```c
NODE_TEXT_AREA_SHOW_COUNTER = 8008
```

Whether to show a counter and its style when the number of input characters exceeds a threshold. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to show the counter. **true** to show; **false** otherwise. The default value is **false**.|
| .value[1]?.f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100]. If the value is a decimal, it is rounded down. If the value is out of the range, the attribute setting does not take effect.|
| .value[2]?.i32 | Whether to highlight the border when the number of entered characters exceeds the maximum. **true** to highlight; **false** otherwise. The default value is **true**.|
| .object | Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the counter is shown. **true** indicates the counter is shown; **false** otherwise.|
| .value[1].f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100].|
| .value[2].i32 | Whether the border is highlighted when the number of entered characters exceeds the maximum. **true** indicates that the border is highlighted.|
| .object | Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).|

## NODE_TEXT_AREA_SELECTION_MENU_HIDDEN

```c
NODE_TEXT_AREA_SELECTION_MENU_HIDDEN = 8009
```

Whether to hide the text selection menu when the text box is long-pressed, double-tapped, or right-clicked. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to hide the text selection menu when the text box is long-pressed, double-tapped, or right-clicked. The default value is **false**.<br>**true**: The system text selection menu is hidden when a user clicks the text box cursor, long-presses the text box, double-taps the text box, triple-taps the text box, or right-clicks the text box.<br>**false**: The system text selection menu is displayed.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the text selection menu is hidden when the text box is long-pressed, double-tapped, or right-clicked.|

## NODE_TEXT_AREA_BLUR_ON_SUBMIT

```c
NODE_TEXT_AREA_BLUR_ON_SUBMIT = 8010
```

Whether the multi-line text box loses focus after the **Enter** key is pressed to submit information.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the text box loses focus after the **Enter** key is pressed to submit information. **true**: The text box loses focus. **false**: The text box does not lose focus.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the text box loses focus after the **Enter** key is pressed to submit information.|

## NODE_TEXT_AREA_INPUT_FILTER

```c
NODE_TEXT_AREA_INPUT_FILTER = 8011
```

Regular expression for input filtering. Only inputs that comply with the regular expression can be displayed. Other inputs are filtered out. For single-character input scenarios, only single-character matching is supported; for multi-character input scenarios (such as pasting), string matching is supported.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .string | Regular expression.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Regular expression.|

## NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR

```c
NODE_TEXT_AREA_SELECTED_BACKGROUND_COLOR = 8012
```

Background color of the selected text. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format.|

## NODE_TEXT_AREA_ENTER_KEY_TYPE

```c
NODE_TEXT_AREA_ENTER_KEY_TYPE = 8013
```

Type of the **Enter** key. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Type of the **Enter** key, specified using the [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype) enum. The default value is **ARKUI_ENTER_KEY_TYPE_DONE**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the **Enter** key, specified using the [ArkUI_EnterKeyType](capi-native-type-h.md#arkui_enterkeytype) enum.|

## NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_ENABLE_KEYBOARD_ON_FOCUS = 8014
```

Whether to enable the input method when the **TextArea** component obtains focus in a way other than clicking. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the input method when the **TextArea** component obtains focus in a way other than clicking. **true** means to enable. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the input method is enabled when the component obtains focus. The value **1** means that the input method is enabled when the component obtains focus, and **0** means the opposite.|

## NODE_TEXT_AREA_CARET_OFFSET

```c
NODE_TEXT_AREA_CARET_OFFSET = 8015
```

Caret position.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>
Sets the position of the caret.<br>
Returns the position information of the caret. If this API is called when the caret position is updated in the current frame, it will not take effect.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Length from the start of the string to the position where the caret is located.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Index of the caret position.|
| .value[1].f32 | X coordinate of the caret relative to the text box.|
| .value[2].f32 | Y coordinate of the caret relative to the text box.|

## NODE_TEXT_AREA_CONTENT_RECT

```c
NODE_TEXT_AREA_CONTENT_RECT = 8016
```

Position of the edited text area relative to the component and its size.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 12


**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | X-coordinate.|
| .value[1].f32 | Y-coordinate.|
| .value[2].f32 | Content width.|
| .value[3].f32 | Content height.|

## NODE_TEXT_AREA_CONTENT_LINE_COUNT

```c
NODE_TEXT_AREA_CONTENT_LINE_COUNT = 8017
```

Number of lines of the edited text.<br>
The format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) is as follows.<br>

**Since**: 12


**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of lines of the edited text.|

## NODE_TEXT_AREA_TEXT_SELECTION

```c
NODE_TEXT_AREA_TEXT_SELECTION = 8018
```

Text selection range, which will be highlighted, when the component is focused. This enumerated value works only when the value of **selectionStart** is less than that of **selectionEnd**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Start position of the text selection.|
| .value[1].i32 | End position of the text selection.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Start position of the text selection.|
| .value[1].i32 | End position of the text selection.|

## NODE_TEXT_AREA_ENABLE_AUTO_FILL

```c
NODE_TEXT_AREA_ENABLE_AUTO_FILL = 8019
```

Whether to enable autofill.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable autofill. The default value is **true**.<br>**true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether autofill is enabled.|

## NODE_TEXT_AREA_CONTENT_TYPE

```c
NODE_TEXT_AREA_CONTENT_TYPE = 8020
```

Autofill type.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-native-type-h.md#arkui_textinputcontenttype).|

## NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS

```c
NODE_TEXT_AREA_SHOW_KEYBOARD_ON_FOCUS = 8021
```

Whether to show the keyboard when the text box obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to show the keyboard. The default value is **true**.<br>**true** to show; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the keyboard is shown.|

## NODE_TEXT_AREA_NUMBER_OF_LINES

```c
NODE_TEXT_AREA_NUMBER_OF_LINES = 8022
```

Number of lines in the **TextArea** component, which can be used to work out the height of the component.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Number of lines.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of lines.|

## NODE_TEXT_AREA_LETTER_SPACING

```c
NODE_TEXT_AREA_LETTER_SPACING = 8023
```

Letter spacing of the **TextArea** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | [Letter spacing](arkui-ts/ts-basic-components-text.md#letterspacing). The default unit is fp.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | [Letter spacing](arkui-ts/ts-basic-components-text.md#letterspacing). The default unit is fp.|

## NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024
```

Whether to enable preview text for the **TextArea** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable preview text. **true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether preview text is enabled.|

## NODE_TEXT_AREA_HALF_LEADING

```c
NODE_TEXT_AREA_HALF_LEADING = 8025
```

Whether to enable half leading.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable half leading. The default value is **false**.<br>**true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether half leading is enabled.|

## NODE_TEXT_AREA_KEYBOARD_APPEARANCE

```c
NODE_TEXT_AREA_KEYBOARD_APPEARANCE = 8026
```

Appearance of the keyboard when the text box is started.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Appearance of the keyboard. The parameter type is [ArkUI_KeyboardAppearance](capi-native-type-h.md#arkui_keyboardappearance).|

## NODE_TEXT_AREA_MAX_LINES

```c
NODE_TEXT_AREA_MAX_LINES = 8027
```

Maximum number of lines that can be displayed with the inline style in the editing state. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Maximum number of lines that can be displayed with the inline style in the editing state. With the inline style, the default value is **3**.<br>With the non-inline style, the default value is +∞, indicating that there is no limit on the maximum number of lines. If this parameter is set to **undefined**, the maximum number of lines is **5**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Number of maximum lines.|

## NODE_TEXT_AREA_LINE_SPACING

```c
NODE_TEXT_AREA_LINE_SPACING = 8028
```

Letter spacing of text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Numeric value for the letter spacing. The default value is **0**, in fp. If this parameter is set to **undefined**, the letter spacing is **5**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Numeric value for the letter spacing, in fp.|

## NODE_TEXT_AREA_MIN_LINES

```c
NODE_TEXT_AREA_MIN_LINES = 8029
```

Minimum number of lines for the node. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Number of minimum lines.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Number of minimum lines.|

## NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL

```c
NODE_TEXT_AREA_MAX_LINES_WITH_SCROLL = 8030
```

Maximum number of lines for the node when scrolling is enabled. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Maximum number of lines when scrolling is enabled.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Maximum number of lines when scrolling is enabled.|

## NODE_TEXT_AREA_LINE_HEIGHT

```c
NODE_TEXT_AREA_LINE_HEIGHT = 8031
```

Line height of text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Numeric value for the text line height. Default value: adaptive to the font size. The unit is fp. If this parameter is set to **undefined**, the text line height is **5**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Numeric value for the text line height, in fp.|

## NODE_TEXT_AREA_BAR_STATE

```c
NODE_TEXT_AREA_BAR_STATE = 8032
```

Scrollbar status of the text input box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Scrollbar status of the text input box. The parameter type is [ArkUI_BarState](capi-native-type-h.md#arkui_barstate). The default value is **ARKUI_BAR_STATE_AUTO**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Scrollbar status of the text input box. The parameter type is [ArkUI_BarState](capi-native-type-h.md#arkui_barstate).|

## NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR = 8033
```

Whether to enable entity recognition for selected text.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable entity recognition for selected text. **true** to enable; **false** otherwise. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether entity recognition for selected text is enabled.|

## NODE_TEXT_AREA_SCROLL_BAR_COLOR

```c
NODE_TEXT_AREA_SCROLL_BAR_COLOR = 8035
```

Scrollbar color of the text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the scrollbar, in 0xARGB format. The default value is **0x66182431**, which indicates gray.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the scrollbar.|

## NODE_TEXT_AREA_CUSTOM_KEYBOARD

```c
NODE_TEXT_AREA_CUSTOM_KEYBOARD = 8036
```

Custom keyboard of the text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22


**Parameters**

| Name| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0]?.i32 | Whether the custom keyboard supports avoidance.<br>**true** to support; **false** otherwise.<br>The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0].i32 | Whether the custom keyboard supports avoidance.|

## NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE

```c
NODE_TEXT_AREA_TEXT_CONTENT_CONTROLLER_BASE = 8037
```

Text area controller.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .object | Basic controller of the text content. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Basic controller of the text content. The parameter type is [ArkUI_TextContentBaseController](capi-arkui-nativemodule-arkui-textcontentbasecontroller.md).|

## NODE_TEXT_AREA_ELLIPSIS_MODE

```c
NODE_TEXT_AREA_ELLIPSIS_MODE = 8038
```

Text ellipsis position of the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode). The default value is **ARKUI_ELLIPSIS_MODE_END**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Ellipsis position. The parameter type is [ArkUI_EllipsisMode](capi-native-type-h.md#arkui_ellipsismode).|

## NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_AREA_COMPRESS_LEADING_PUNCTUATION = 8040
```

Whether to enable the feature of compressing punctuations at the beginning of a text line. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the feature of compressing punctuations at the beginning of a text line.<br>**true** to enable; **false** otherwise. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the feature of compressing punctuations is enabled at the beginning of a text line.|

## NODE_TEXT_AREA_INCLUDE_FONT_PADDING

```c
NODE_TEXT_AREA_INCLUDE_FONT_PADDING = 8041
```

Whether to add spacing to the first and last lines of text in a multi-line text box to avoid text truncation.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to add spacing to the first and last lines of text in a text box to avoid text truncation. **true** to add; **false** otherwise. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether spacing is added to the first and last lines of text in a text box. **true** indicates spacing is added; **false** otherwise.|

## NODE_TEXT_AREA_FALLBACK_LINE_SPACING

```c
NODE_TEXT_AREA_FALLBACK_LINE_SPACING = 8042
```

Whether the line height can be automatically adjusted based on the actual text height for multi-line text overlay. This enumerated value takes effect only when the line height is smaller than the actual text height.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **true** to be adjusted; **false** otherwise. The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **true** means that the line height can be automatically adjusted; **false** otherwise.|

## NODE_TEXT_AREA_HORIZONTAL_SCROLLING

```c
NODE_TEXT_AREA_HORIZONTAL_SCROLLING = 8043
```

Whether to enable horizontal scrolling for a multi-line text box when the text width exceeds the width of the content area in the text box. The default value is **false**, meaning that the text will be automatically wrapped by the text box.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable horizontal scrolling. **true** to enable; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether horizontal scrolling is enabled.|

## NODE_TEXT_AREA_DIRECTION

```c
NODE_TEXT_AREA_DIRECTION = 8044
```

Text layout direction of the multi-line text box.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text layout direction. The value is an enumerated value of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection). The default value is **ARKUI_TEXT_DIRECTION_DEFAULT**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text layout direction. For details about the values and meanings, see the enumerated values of [ArkUI_TextDirection](capi-native-type-h.md#arkui_textdirection).|

## NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE

```c
NODE_TEXT_AREA_SELECTED_DRAG_PREVIEW_STYLE = 8045
```

Drag preview style when the text in the multi-line text box is selected.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23


**Parameters**

| Name| Description|
| -- | -- |
| .object | Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Drag preview style when the text is selected. The parameter type is [ArkUI_SelectedDragPreviewStyle](capi-arkui-nativemodule-arkui-textselecteddragpreviewstyle.md).|

## NODE_TEXT_AREA_TEXT_OVERFLOW

```c
NODE_TEXT_AREA_TEXT_OVERFLOW = 8046
```

Display mode when the text is too long in the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Display mode when the text is too long, specified using the [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow) enum. The default value is **ARKUI_TEXT_OVERFLOW_CLIP**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Display mode when the text is too long, specified using the [ArkUI_TextOverflow](capi-native-type-h.md#arkui_textoverflow) enum.|

## NODE_TEXT_AREA_DECORATION

```c
NODE_TEXT_AREA_DECORATION = 8047
```

Text decorative line style and color of the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24


**Parameters**

| Name| Description|
| -- | -- |
| .object | Decoration style options. This parameter is optional. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| .object | Decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).|
