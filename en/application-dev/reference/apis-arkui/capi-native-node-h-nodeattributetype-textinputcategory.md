# ArkUI_NodeAttributeType (Text Input Component Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6; @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=b9a7c339aff114212b4730e0945a2d00427fb022 translatedAt=2026-08-04T11:05:15.710Z pushedAt=2026-08-10T08:24:10.469Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for text input components including **TextInput** and **TextArea**. This attribute set supports various style and interaction configurations such as caret styles, placeholder text, input filtering, auto-fill, text selection, and counters. It is applicable to scenarios such as form input, search boxes, password input, and multi-line text editing, making it easier for you to uniformly manage the appearance and behavior of text input components.

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
| .string | Default placeholder text. Set this parameter when you need to display prompt information in the input box to guide user input, for example, "Enter username", "Enter password", etc. When not set, the input box has no placeholder text. |

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
| .string | Default text content, used to set the text initially displayed in the input box. Set this parameter when you need to preset text in the input box, for example, form default values, initial editing content, etc. When not set, the input box is empty. |

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
| .value[0].f32 | Caret width, in vp. Value range: [0, +∞). |

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
| .value[0].i32 | Whether to show an underline. **1** means to show an underline; **0** means the opposite. Default value: **0**. |

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
| .value[0].i32 | Maximum number of characters in the text input, without a unit. Value range: [0, +∞). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Maximum number of characters in the text input, without a unit. |

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
| .value[0].i32 | Type of the **Enter** key. The value is an enumerated value of [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype). The default value is **ARKUI_ENTER_KEY_TYPE_DONE**, which indicates the completion style. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the **Enter** key. The value is an enumerated value of [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype), used to determine the display style of the **Enter** key in the input box. |

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
| .value[0]?.f32 | Font size, in fp. This parameter is optional. The default value is **16.0**. Value range: [0, +∞). When a negative value is passed, the setting does not take effect. |
| .value[1]?.i32 | Font style. This parameter is optional. The value is an enumerated value of [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). Default value: **ARKUI_FONT_STYLE_NORMAL**, which indicates the normal font style. |
| .value[2]?.i32 | Font weight. This parameter is optional. The value is an enumerated value of [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). Default value: **ARKUI_FONT_WEIGHT_NORMAL**, which indicates the normal font weight. |
| ?.string | Font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2". When not passed, the system default font family is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Font size, in fp.|
| .value[1].i32 | Font style. The value is an enumerated value of [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).|
| .value[2].i32 | Font weight. The value is an enumerated value of [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).|
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
| .value[0].i32 | Whether to enable the input method when the component obtains focus. The value **1** indicates to enable, and **0** indicates the opposite. Default value: **1**.  |

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
| .value[0].i32 | Text input type. The value is an enumerated value of [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype). The default value is **ARKUI_TEXTINPUT_TYPE_NORMAL**, which indicates the basic input mode. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text input type. The value is an enumerated value of [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype), used to determine the input content and keyboard style of the input box. |

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
| .value[0].i32 | Whether to display the password icon. **1** means to display; **0** otherwise. Default value: **0**. |

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
| .value[0].i32 | Whether to remain in the editable state. **1** means to remain in the editable state, and **0** means to exit the editable state. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether to remain in the editable state. **1** means to remain in the editable state, and **0** means to exit the editable state. |

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
| .value[0].i32 | Button style. The value is an enumerated value of [ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle). The default value is **ARKUI_CANCELBUTTON_STYLE_INPUT**, which indicates the clear button input style. |
| .value[1]?.f32 | Icon size, in vp. Value range: [0, +∞). When a negative value is passed, the setting does not take effect. When not passed, the system default icon size is used. |
| .value[2]?.u32 | Button icon color, in 0xARGB format, for example, **0xFFFF0000** indicates red. When not passed, the system default icon color is used. |
| ?.string | Button icon address. The value is the local address of an image, for example, **/pages/icon.png**. When not passed, the system default clear icon is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Button style. The value is an enumerated value of [ArkUI_CancelButtonStyle](capi-text-input-h.md#arkui_cancelbuttonstyle).|
| .value[1].f32 | Button icon size, in vp.|
| .value[2].u32 | Button icon color, in 0xARGB format.|
| .string | Button icon address.|

## NODE_TEXT_INPUT_TEXT_SELECTION

```c
NODE_TEXT_INPUT_TEXT_SELECTION = 7015
```

Text selection area, which will be highlighted, for the component that obtains focus. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Start position of the text selection. The value range is [0, Text length]. The setting takes effect only when the value is earlier than the end position. |
| .value[1].i32 | End position of the text selection. The value range is [0, Text length]. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Start position of the text selection.|
| .value[1].i32 | End position of the text selection.|

## NODE_TEXT_INPUT_UNDERLINE_COLOR

```c
NODE_TEXT_INPUT_UNDERLINE_COLOR = 7016
```

Color of the underline when it is shown. This attribute takes effect only after **NODE_TEXT_INPUT_SHOW_UNDERLINE** is set to **1** to show the underline. The default underline color configured for the theme is **0x33182431**, which indicates dark gray with 20% opacity.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color of the underline applied to the text being typed in. This parameter is mandatory. The value is in 0xARGB format. |
| .value[1].u32 | Color of the underline applied to the text in the normal state. This parameter is mandatory. The value is in 0xARGB format. |
| .value[2].u32 | Color of the underline applied to the text when an error is detected. This parameter is mandatory. The value is in 0xARGB format. |
| .value[3].u32 | Color of the underline applied to the text when it is disabled. This parameter is mandatory. The value is in 0xARGB format. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color of the underline applied to the text being typed in. The value is in 0xARGB format. |
| .value[1].u32 | Color of the underline applied to the text in the normal state. The value is in 0xARGB format. |
| .value[2].u32 | Color of the underline applied to the text when an error is detected. The value is in 0xARGB format. |
| .value[3].u32 | Color of the underline applied to the text when it is disabled. The value is in 0xARGB format. |

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
| .value[0].i32 | Whether to enable autofill. The default value is **1**.<br>**1** indicates to enable, and **0** indicates the opposite. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether autofill is enabled. The value **1** means auto-fill is enabled, and **0** means the opposite. |

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
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype), used to specify the content type in autofill scenarios. For specific enumerated values and application scenarios, see [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype), used to determine the auto-filled content type. |

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
| .string | Rules for generating passwords, which are transparently passed to the password vault to control new password generation when autofill is triggered. |

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
| .value[0].i32 | Whether to select all text. Default value: **0**.<br>The value **1** means to select all text, and **0** means the opposite. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether all text is selected. **1** means all text is selected, and **0** means the opposite. |

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
| .string | Regular expression, used to filter user input. Input matching the expression is allowed to be displayed, and input not matching is filtered out. Set this parameter when you need to restrict users to inputting only characters in a specific format. For example, **"^[a-zA-Z]+$"** allows only letters, and **"^[0-9]+$"** allows only digits. When not set, all characters are allowed.|

**Returns**

| Type| Description|
| -- | -- |
| .string | Regular expression.|

## NODE_TEXT_INPUT_STYLE

```c
NODE_TEXT_INPUT_STYLE = 7022
```

Text box style (default style or inline input style). The inline input style is a borderless embedded input style where the input box blends directly into the page content. The inline input style is only available when [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_NORMAL**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text box style. The parameter type is [ArkUI_TextInputStyle](capi-text-input-h.md#arkui_textinputstyle). The inline input style is only available when [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_NORMAL**. The default value is **ARKUI_TEXTINPUT_STYLE_DEFAULT**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text box style. The parameter type is [ArkUI_TextInputStyle](capi-text-input-h.md#arkui_textinputstyle), used to determine the display style of the input box. |

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
| .value[0].i32 | Length from the start of the string to the position where the caret is located. The value range is [0, Text length]. If the value is out of range, it is automatically corrected to the boundary value. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Index of the caret position.|
| .value[1].f32 | X-coordinate of the caret relative to the input box, in px. |
| .value[2].f32 | Y-coordinate of the caret relative to the input box, in px. |

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
| .value[0].f32 | X-coordinate, in px. |
| .value[1].f32 | Y-coordinate, in px. |
| .value[2].f32 | Content width, in px. |
| .value[3].f32 | Content height, in px. |

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
| .value[0].i32 | Whether to hide the text selection menu when the text box is long-pressed, double-tapped, or right-clicked. The default value is **0**.<br>**1**: The system text selection menu is hidden when a user clicks the text box cursor, long-presses the text box, double-taps the text box, triple-taps the text box, or right-clicks the text box.<br>**0**: The system text selection menu is displayed. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the text selection menu is hidden when the text box is long-pressed, double-tapped, or right-clicked. The value **1** means the text selection menu is hidden, and **0** means the text selection menu is displayed. |

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
| .value[0].i32 | Whether the text box loses focus after the **Enter** key is pressed to submit information. The default value is **1**.<br>**1**: The text box loses focus. **0**: The text box does not lose focus.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the text box loses focus after the **Enter** key is pressed to submit information. The value **1** indicates the text box loses focus, and **0** indicates the text box does not lose focus. |

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
| .value[0]?.i32 | Whether the custom keyboard supports avoidance. The default value is **0**.<br>**1** to support; **0** otherwise. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0].i32 | Whether the custom keyboard supports avoidance. The value **1** indicates the custom keyboard supports avoidance, **0** indicates the opposite. |

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
| .value[0].i32 | Line break rule. The parameter type is [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak). The setting takes effect only in the editing state in the inline input style. Default value: **ARKUI_WORD_BREAK_BREAK_WORD**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Line break rule. The parameter type is [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak), used to determine the line break mode of text. |

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
| .value[0].i32 | Whether to show the keyboard. Default value: **1**.<br>**1** to show; **0** otherwise. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the keyboard is shown. The value **1** indicates the keyboard is shown, and 0 indicates the opposite. |

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
| .value[0].i32 | Number of lines, with a value range of [1, +∞). This parameter is used to calculate the height of the **TextInput** component. For example, when set to 3, the component displays a height sufficient to accommodate three lines of text content by default. |

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
"Preview text" describes a temporary text staging state. The preview text feature must be enabled in the input method. During text input, before a candidate word is confirmed, marked text is displayed in the text box. For example, when entering Chinese characters via Pinyin, the Pinyin letters are displayed in the input box before the candidate word is confirmed. This state is called preview.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable preview text. The default value is **1**.<br>**1** to enable; **0** otherwise. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether preview text is enabled. The value **1** indicates preview text is enabled, **0** indicates the opposite. |

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
| .value[0].i32 | Whether to enable half leading. The default value is **0**.<br>**1** to enable; **0** otherwise. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether half leading is enabled. The value **1** means half leading is enabled, and **0** means the opposite. |

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
| .value[0].i32 | Keyboard appearance. The parameter type is [ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance). For specific enumerated values, see **ArkUI_KeyboardAppearance**. The default value is **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**, which indicates no immersive style is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Keyboard appearance. The parameter type is [ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance). For specific enumerated values, see **ArkUI_KeyboardAppearance**. The default value is **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**. |

## NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION

```c
NODE_TEXT_INPUT_ENABLE_FILL_ANIMATION = 7036
```

Whether to enable the autofill animation. This animation takes effect only when the input box type [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype) is set to **ARKUI_TEXTINPUT_TYPE_PASSWORD**, **ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD**, or **ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable the autofill animation. When enabled, the animation takes effect during auto-fill only for the input box whose [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype) set to **ARKUI_TEXTINPUT_TYPE_PASSWORD**, **ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD**, or **ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD**.<br>**1** to enable;**0** otherwise.<br>Default value: **1**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the autofill animation is enabled. The value **1** means enabled, and **0** means disabled. When enabled, the animation takes effect during auto-fill only for the input box whose [ArkUI_TextInputType](capi-text-input-h.md#arkui_textinputtype) enumeration is set to **ARKUI_TEXTINPUT_TYPE_PASSWORD**, **ARKUI_TEXTINPUT_TYPE_NUMBER_PASSWORD**, or **ARKUI_TEXTINPUT_TYPE_NEW_PASSWORD**. |

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
| .value[0].i32 | Text height, in fp. The default value is adaptive font size. When this parameter is not passed, the text height is set to 5 fp. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text height, in fp. |

## NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_INPUT_ENABLE_SELECTED_DATA_DETECTOR = 7038
```

Whether to enable entity recognition for selected text. This attribute supports the recognition of entity information such as phone numbers, email addresses, and URLs in the selected text, making it convenient for users to quickly make calls, send emails, or open URLs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable entity recognition for selected text. **1** to enable; **0** otherwise. The default value is **1**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether entity recognition for selected text is enabled. The value **1** indicates entity recognition is enabled, and **0** indicates the opposite. |

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
| .value[0].i32 | Whether to show a counter. **1** to show; **0** otherwise. |
| .value[1]?.f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100]. If the value is a decimal, it is rounded down. If the value is out of the range, the attribute setting does not take effect. The default value is **-1**, meaning the counter is always shown. |
| .value[2]?.i32 | Whether to highlight the border when the number of entered characters exceeds the maximum. **1** means to highlight; **0** otherwise. |
| .object | Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the counter is shown. The value **1** means the counter is shown, and **0** means the opposite. |
| .value[1].f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100].|
| .value[2].i32 | Whether the border is highlighted when the number of entered characters exceeds the maximum. **1** indicates that the border is highlighted; **0** otherwise. |
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

Text ellipsis mode of the single-line text box. This attribute can be set, reset, and obtained as required through APIs.

This attribute has the following configuration dependencies:

- This attribute takes effect only when **NODE_TEXT_INPUT_TEXT_OVERFLOW** is set to **ARKUI_TEXT_OVERFLOW_ELLIPSIS**.

- When **TEXT_OVERFLOW** is set to **ARKUI_TEXT_OVERFLOW_CLIP**, the **ELLIPSIS_MODE** setting does not take effect.

- It is recommended to set **TEXT_OVERFLOW** to **ELLIPSIS** first, and then set **ELLIPSIS_MODE** to a specified ellipsis mode.<br>

The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Text ellipsis mode. The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode). For specific enumerated values, see the **ArkUI_EllipsisMode** description. The default value is **ARKUI_ELLIPSIS_MODE_END**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text ellipsis mode. The parameter type is [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode), used to determine the ellipsis position when text is too long. |

## NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_INPUT_ORPHAN_CHAR_OPTIMIZATION = 7043
```

Whether to enable orphan character optimization for text layout in the **TextInput** component. When set, the orphan character (the first character in the last line of a paragraph) is processed more efficiently to improve the text layout. When enabled, it adjusts line break points to avoid orphan characters as much as possible.<br>Note: The orphan character optimization feature takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not set to **ARKUI_WORD_BREAK_BREAK_ALL**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable orphan character optimization. This feature takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not set to **ARKUI_WORD_BREAK_BREAK_ALL**. **1** to enable; **0** otherwise. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether orphan character optimization is enabled. The value **1** means enabled, and **0** means the opposite. |

## NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION

```c
NODE_TEXT_INPUT_COMPRESS_LEADING_PUNCTUATION = 7044
```

Whether to enable leading punctuation compression of a text line. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable leading punctuation compression.<br>**1** to enable; **0** otherwise. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether leading punctuation compression is enabled. **1** indicates leading punctuation compression is enabled, and **0** indicates the opposite. |

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
| .value[0].i32 | Whether to add spacing to the top of the first line and the bottom of the last line of text in a single-line text box to avoid text truncation. **1** to add; **0** otherwise. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether spacing is added to the top of the first line and the bottom of the last line. **1** indicates spacing is added; **0** otherwise. |

## NODE_TEXT_INPUT_FALLBACK_LINE_SPACING

```c
NODE_TEXT_INPUT_FALLBACK_LINE_SPACING = 7046
```

Whether the line height can be automatically adjusted based on the actual text height for multi-line text display. This enumerated value takes effect only when the line height is smaller than the actual text height.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **1** to be adjusted; **0** otherwise. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **1** means that the line height can be automatically adjusted; **0** otherwise. |

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
| .value[0].i32 | Text layout direction. The value is an enumerated value of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). The default value is **ARKUI_TEXT_DIRECTION_DEFAULT**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text layout direction. For details about the values and meanings, see the enumerated values of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection).|

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

## NODE_TEXT_INPUT_LINEAR_GRADIENT

```c
NODE_TEXT_INPUT_LINEAR_GRADIENT = 7051
```

Linear gradient effect of the text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient, in degree. When the linear gradient direction is **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM** of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection), the start angle of the linear gradient takes effect. Otherwise, the linear gradient direction is used as the main layout mode. The value range is (-∞,+∞). A positive value indicates a clockwise rotation from the origin (0, 0). When the value exceeds 360, the remainder of 360 is used. The default value is **180**. |
| .value[1].i32 | Direction of the linear gradient. The value is an enumerated value of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection). If the linear gradient direction is set to a value other than **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM**, the start angle of the linear gradient does not take effect. Default value: **ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM**. |
| .value[2].i32 | Whether the gradient colors are repeated. The value **0** indicates that the gradient colors are not repeated, and **1** indicates that the gradient colors are repeated. The default value is **0**. |
| .object | Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md).<br>- **colors**: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.<br>- **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order.<br>- **size**: number of colors. If the value is smaller than the length of the **colors** array, only the first **size** colors take effect. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient. When the direction of the linear gradient is **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM** of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection), the start angle of the linear gradient is the set value. In other cases, the default value **0** is used. |
| .value[1].i32 | Direction of the linear gradient. For details about the values and meanings, see [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection).|
| .value[2].i32 | Whether the gradient colors are repeated. The value **0** indicates that the gradient colors are not repeated, and **1** indicates that the gradient colors are repeated. The default value is **0**. |
| .object | Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md).<br> **colors**: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end.<br> **size**: number of effective gradient colors.|

## NODE_TEXT_INPUT_RADIAL_GRADIENT

```c
NODE_TEXT_INPUT_RADIAL_GRADIENT = 7052
```

Radial gradient effect of the text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the radial gradient center relative to the upper left corner of the text box, in vp. The default value is half the width of the text box. |
| .value[1]?.f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the text box, in vp. The default value is half the height of the text box. |
| .value[2]?.f32 | Radius of the radial gradient, in vp. The value range is [0, +∞), and the default value is **0**. If a negative value is passed, the setting does not take effect. |
| .value[3]?.i32 | Whether the gradient colors are repeated. The value **0** indicates that the gradient colors are not repeated, and **1** indicates that the gradient colors are repeated. The default value is **0**. |
| .object | Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md).<br> **colors**: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red. <br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value. <br> **size**: number of colors. If the value is smaller than the length of the **colors** array, only the first **size** colors take effect. Invalid values are not recommended. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the radial gradient center relative to the upper left corner of the text box, in vp. |
| .value[1]?.f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the text box, in vp. |
| .value[2]?.f32 | Radius of the radial gradient, in vp. Default value: **0**. |
| .value[3]?.i32 | Whether the gradient colors are repeated. The value **0** indicates that the gradient colors are not repeated, and **1** indicates that the gradient colors are repeated. The default value is **0**. |
| .object | Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md).<br> **colors**: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end.<br> **size**: number of effective gradient colors.|

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
| .value[0].i32 | Display mode when the text is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). The default value is **ARKUI_TEXT_OVERFLOW_ELLIPSIS** in the non-editing state for the inline mode and **ARKUI_TEXT_OVERFLOW_CLIP** in the editing state for the inline mode.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Display mode when the text is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow).|

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
| .object | Decoration style options. This parameter is optional. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md). When not passed, no decoration line is added. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).|

## NODE_TEXT_INPUT_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_INPUT_PUNCTUATION_OVERFLOW = 7053
```

Whether to enable punctuation hanging at the end of a line for the **TextInput** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable punctuation hanging at the end of a line. The value **1** means to enable, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether punctuation hanging at the end of a line is enabled. The value **1** means punctuation hanging is enabled, and **0** means the opposite. |

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
| .string | Default placeholder text. Set this parameter when a prompt message needs to be displayed in the text box to guide user input, for example, "Enter username", "Enter content", etc. When not set, the text box has no placeholder text. |

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
| .value[0].i32 | Maximum number of characters in the text input. Value range: [0, +∞). |

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
| .value[0]?.f32 | Font size, in fp. This parameter is optional. The default value is **16.0**. Unit: fp. Value range: [0, +∞). |
| .value[1]?.i32 | Font style. This parameter is optional. The value is an enumerated value of [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle). For specific style values, see the enumeration of **ArkUI_FontStyle**. Default value: **ARKUI_FONT_STYLE_NORMAL**, indicating the standard font style. |
| .value[2]?.i32 | Font weight. This parameter is optional. The value is an enumerated value of [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight). For specific weight values, see the enumeration of **ArkUI_FontWeight**. Default value: **ARKUI_FONT_WEIGHT_NORMAL**, indicating the normal font weight. |
| ?.string | Font family. Multiple font families are separated by commas (,). For example, "font weight; font family 1, font family 2". When not passed, the system default font family is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Font size, in fp.|
| .value[1].i32 | Font style. The value is an enumerated value of [ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle).|
| .value[2].i32 | Font weight. The value is an enumerated value of [ArkUI_FontWeight](capi-text-h.md#arkui_fontweight).|
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
| .value[0].u32 | Caret color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Caret color, in 0xARGB format.|

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
| .value[0].i32 | Whether to remain in the editable state. **1** means to remain in the editable state, and **0** means to exit the editable state. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether to remain in the editable state. **1** means to remain in the editable state, and **0** means to exit the editable state. |

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
| .value[0].i32 | Text area type. The value is an enumerated value of [ArkUI_TextAreaType](capi-text-area-h.md#arkui_textareatype). For specific values, see the enumeration of **ArkUI_TextAreaType**. The default value is **ARKUI_TEXTAREA_TYPE_NORMAL**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text area type. The value is an enumerated value of [ArkUI_TextAreaType](capi-text-area-h.md#arkui_textareatype), used to determine the type of the multi-line text box. |

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
| .value[0].i32 | Whether to show the counter. **1** to show; **0** otherwise. The default value is **0**. |
| .value[1]?.f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100]. If the value is a decimal, it is rounded down. If the value is out of the range, the attribute setting does not take effect. The default value is **-1**, which means the counter is always shown. |
| .value[2]?.i32 | Whether to highlight the border when the number of entered characters exceeds the maximum. **1** to highlight; **0** otherwise. The default value is **1**. |
| .object | Counter configuration. The configuration attributes are the color of the counter when the number of characters entered in the text box does not reach the maximum and the color of the counter when the number of characters entered in the text box exceeds the maximum. The parameter type is [ArkUI_ShowCounterConfig](capi-arkui-nativemodule-arkui-textshowcounterconfig.md).|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the counter is shown. **1** indicates the counter is shown; **0** otherwise. |
| .value[1].f32 | Percentage of the number of characters that can be entered to the maximum number of characters allowed. When the percentage exceeds this value, the counter is shown. The value range is [1, 100].|
| .value[2].i32 | Whether the border is highlighted when the number of entered characters exceeds the maximum. **1** indicates that the border is highlighted, and **0** indicates the opposite. |
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
| .value[0].i32 | Whether to hide the text selection menu when the text box is long-pressed, double-tapped, or right-clicked.<br>**1**: The system text selection menu is hidden when a user clicks the text box cursor, long-presses the text box, double-taps the text box, triple-taps the text box, or right-clicks the text box.<br>**0**: The system text selection menu is displayed.<br>Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the text selection menu is hidden when the text box is long-pressed, double-tapped, or right-clicked. The value **1** indicates that the text selection menu is hidden, and **0** indicates the opposite. |

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
| .value[0].i32 | Whether the text box loses focus after the **Enter** key is pressed to submit information.<br>**1**: The text box loses focus. **0**: The text box does not lose focus.<br>Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the text box loses focus after the **Enter** key is pressed to submit information. **1**: The text box loses focus. **0**: The text box does not lose focus. |

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
| .string | Regular expression used to filter user input content. Input matching the expression is allowed to display, while non-matching input is filtered out. Set this parameter when you need to restrict users to input only characters in a specific format. For example, "^[a-zA-Z]+$" indicates that only letters are allowed, and "^[0-9]+$" indicates that only digits are allowed. When not set, all character input is allowed. |

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
| .value[0].i32 | Type of the Enter key. The value is an enumerated value of [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype). The default value is **ARKUI_ENTER_KEY_TYPE_DONE**, which indicates the completion style. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the **Enter** key. The value is an enumerated value of [ArkUI_EnterKeyType](capi-text-common-h.md#arkui_enterkeytype), used to determine the display style of the **Enter** key in the text box. |

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
| .value[0].i32 | Whether to enable the input method when the **TextArea** component obtains focus in a way other than clicking. **1** means to enable, and **0** to disable. Default value: **1**. |

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
| .value[0].i32 | Length from the start of the string to the position where the caret is located. The value range is [0, Text length]. Values out of range are automatically corrected to the boundary values. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Index of the caret position.|
| .value[1].f32 | X-coordinate of the caret relative to the text box, in px. |
| .value[2].f32 | Y-coordinate of the caret relative to the text box, in px. |

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
| .value[0].f32 | X-coordinate, in px. |
| .value[1].f32 | Y-coordinate, in px. |
| .value[2].f32 | Content width, in px. |
| .value[3].f32 | Content height, in px. |

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
| .value[0].i32 | Start position of the selected text. The value range is [0, Text length]. It takes effect only when it is less than the end position. |
| .value[1].i32 | End position of the selected text. The value range is [0, Text length]. |

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
| .value[0].i32 | Whether to enable autofill.<br>**1** indicates to enable, and **0** indicates the opposite.<br>Default value: **1**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether autofill is enabled. **1** indicates enabled, and **0** indicates disabled. |

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
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype). It is used to specify the auto filled content type so that the system can provide more accurate autofill suggestions. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Autofill type. The parameter type is [ArkUI_TextInputContentType](capi-text-input-h.md#arkui_textinputcontenttype). It is used to specify the auto filled content type so that the system can provide more accurate autofill suggestions. |

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
| .value[0].i32 | Whether to show the keyboard.<br>**1** to show; **0** otherwise.<br>Default value: **1**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the keyboard is shown. The value **1** means the keyboard is shown, and **0** means the opposite. |

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
| .value[0].i32 | Number of lines. The value range is [1, +∞). It is used to calculate the height of the **TextArea** component. For example, when set to 3, the component displays a height sufficient to accommodate three lines of text content by default. |

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
| .value[0].f32 | [Letter spacing](arkui-ts/ts-basic-components-text.md#letterspacing), in fp. The value range is (-∞, +∞). When the value is negative, the text is compressed. When the negative value is too small, the component content area size is compressed to 0, causing the content to be undisplayable. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | [Letter spacing](arkui-ts/ts-basic-components-text.md#letterspacing), in fp. The value range is (-∞, +∞). |

## NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT

```c
NODE_TEXT_AREA_ENABLE_PREVIEW_TEXT = 8024
```

Whether to enable preview text for the **TextArea** component. This attribute can be set, reset, and obtained as required through APIs.<br>
"Preview text" describes a temporary text staging state. The preview text feature must be enabled in the input method. During text input, before a candidate word is confirmed, marked text is displayed in the text box. For example, when entering Chinese characters via Pinyin, the Pinyin letters are displayed in the input box before the candidate word is confirmed. This state is called preview.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable preview text.<br>**1** to enable; **0** otherwise.<br>Default value: **1**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether preview text is enabled. The value **1** means enabled, and **0** means disabled. |

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
| .value[0].i32 | Whether to enable half leading.<br>**1** to enable; **0** otherwise.<br>Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether half leading is enabled. The value **1** means enabled, and **0** disabled. |

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
| .value[0].i32 | Keyboard appearance. The parameter type is [ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance). For specific enum values, see the enumeration of **ArkUI_KeyboardAppearance**. Default value: **ARKUI_KEYBOARD_APPEARANCE_NONE_IMMERSIVE**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Keyboard appearance. The parameter type is [ArkUI_KeyboardAppearance](capi-text-common-h.md#arkui_keyboardappearance).|

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
| .value[0].i32 | Maximum number of lines that can be displayed with the inline style in the editing state. Value range: [1, +∞).<br>With the inline style, the default value is **3**. With the non-inline style, the default value is +∞, indicating that there is no limit on the maximum number of lines.<br>When not passed, the default value is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Maximum number of lines. |

## NODE_TEXT_AREA_LINE_SPACING

```c
NODE_TEXT_AREA_LINE_SPACING = 8028
```

Line spacing of text in the text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Line spacing of the text, in fp. The value range is [0, +∞). The default value is **0**. A value out of range is automatically corrected to the boundary value. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Line spacing of the text, in fp. |

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
| .value[0].f32 | Minimum number of lines. The value range is [1, +∞). The setting does not take effect when 0 or a negative value is passed. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Minimum number of lines. The value range is [1, +∞). |

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
| .value[0].f32 | Maximum number of lines when scrolling is enabled. Value range: [1, +∞). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Maximum number of lines when scrolling is enabled. Value range: [1, +∞). |

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
| .value[0].i32 | Line height of the text, in fp. The default value is adaptive font size. When not passed, the text height is set to 5 fp. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Line height of the text, in fp. |

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
| .value[0].i32 | Scrollbar status of the text input box. The parameter type is [ArkUI_BarState](capi-scroll-h.md#arkui_barstate). The default value is **ARKUI_BAR_STATE_AUTO**, which indicates the scrollbar is displayed as needed (displayed upon touch and automatically disappears after 2 seconds). |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Scrollbar status of the text input box. The parameter type is [ArkUI_BarState](capi-scroll-h.md#arkui_barstate).|

## NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR

```c
NODE_TEXT_AREA_ENABLE_SELECTED_DATA_DETECTOR = 8033
```

Whether to enable entity recognition for selected text, supporting the recognition of entity information such as phone numbers, email addresses, and URLs in the selected text, making it convenient for users to quickly make calls, send emails, or open URLs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable entity recognition for selected text. **1** to enable; **0** otherwise. Default value: 1. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether entity recognition for selected text is enabled. **1** indicates enabled, and **0** indicates disabled. |

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
| .value[0].u32 | Color of the scrollbar, in 0xARGB format. |

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
| .value[0]?.i32 | Whether the custom keyboard supports the avoidance feature.<br>**1** indicates support for avoidance, and **0** indicates the opposite.<br>Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Custom keyboard. The parameter type is [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-node8h.md).|
| .value[0].i32 | Whether the custom keyboard supports the avoidance feature. **1** indicates support for avoidance, and **0** indicates the opposite. |

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

Text ellipsis mode of the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.

This attribute has the following configuration dependencies:

- This attribute takes effect only when **NODE_TEXT_AREA_TEXT_OVERFLOW** is set to **ARKUI_TEXT_OVERFLOW_ELLIPSIS**.

- When **TEXT_OVERFLOW** is set to **ARKUI_TEXT_OVERFLOW_CLIP**, the **ELLIPSIS_MODE** setting does not take effect.

- It is recommended to set **TEXT_OVERFLOW** to **ELLIPSIS** first, and then set **ELLIPSIS_MODE** to a specified ellipsis position.<br>

The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Ellipsis mode. The parameter type [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode). For details about the enumerated values, see the **ArkUI_EllipsisMode** description. The default value is **ARKUI_ELLIPSIS_MODE_END**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Enum for text ellipsis position [ArkUI_EllipsisMode](capi-text-common-h.md#arkui_ellipsismode), used to determine the ellipsis position when text exceeds the limit. |

## NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION

```c
NODE_TEXT_AREA_ORPHAN_CHAR_OPTIMIZATION = 8039
```

Whether to enable orphan character optimization for text layout in the **TextArea** component. When set, the orphan character (the first character in the last line of a paragraph) is processed more efficiently to improve the text layout. When enabled, it adjusts line break points to avoid orphan characters as much as possible. The orphan character optimization feature takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not set to **ARKUI_WORD_BREAK_BREAK_ALL**.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable orphan character optimization. This feature takes effect only when the [ArkUI_WordBreak](capi-text-common-h.md#arkui_wordbreak) attribute is not **ARKUI_WORD_BREAK_BREAK_ALL**. **1** to enable; **0** otherwise. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether orphan character optimization is enabled. The value **1** means enabled, and **0** means disabled. |

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
| .value[0].i32 | Whether to enable leading punctuation compression.<br>**1** indicates to enable, and **0** indicates the opposite. Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether leading punctuation compression is enabled. **1** indicates enabled, and **0** indicates disabled. |

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
| .value[0].i32 | Whether to add spacing to the first and last lines of text in a text box to avoid text truncation. **1** to add; **0** otherwise. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether spacing is added to the first and last lines of text in a text box. **1** indicates spacing is added; **0** otherwise. |

## NODE_TEXT_AREA_FALLBACK_LINE_SPACING

```c
NODE_TEXT_AREA_FALLBACK_LINE_SPACING = 8042
```

Whether the line height can be automatically adjusted based on the actual text height for multi-line text display. This enumerated value takes effect only when the line height is smaller than the actual text height.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **1** to be adjusted; **0** otherwise. The default value is 0. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the line height can be automatically adjusted based on the actual text height. **1** means that the line height can be automatically adjusted; **0** otherwise. |

## NODE_TEXT_AREA_HORIZONTAL_SCROLLING

```c
NODE_TEXT_AREA_HORIZONTAL_SCROLLING = 8043
```

Whether to enable horizontal scrolling for a multi-line text box when the text width exceeds the width of the content area in the text box. The default value is **0**, meaning that the text will be automatically wrapped by the text box.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable horizontal scrolling. **1** to enable; **0** otherwise. Default value: **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether horizontal scrolling is enabled. **1** indicates enabled, and **0** indicates disabled. |

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
| .value[0].i32 | Text layout direction. The value is an enumerated value of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection). The default value is **ARKUI_TEXT_DIRECTION_DEFAULT**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Text layout direction. For details about the values and meanings, see the enumerated values of [ArkUI_TextDirection](capi-text-common-h.md#arkui_textdirection).|

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
| .value[0].i32 | Display mode when the text is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow). The default value is **ARKUI_TEXT_OVERFLOW_CLIP**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Display mode when the text is too long. The value is an enumerated value of [ArkUI_TextOverflow](capi-text-common-h.md#arkui_textoverflow).|

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
| .object | Decoration style options. This parameter is optional. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md). When not passed, no decoration line is added. |

**Returns**

| Type| Description|
| -- | -- |
| .object | Decoration style options. The parameter type is [OH_ArkUI_DecorationStyleOptions](capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md).|

## NODE_TEXT_AREA_LINEAR_GRADIENT

```c
NODE_TEXT_AREA_LINEAR_GRADIENT = 8048
```

Linear gradient effect of the text in the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient, in degree. When the linear gradient direction is **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM** of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection), the start angle of the linear gradient takes effect. Otherwise, the linear gradient direction is used as the main layout mode. The value range is (-∞,+∞). A positive value indicates a clockwise rotation from the origin (0, 0). When the value exceeds 360, the remainder of 360 is used. The default value is **180**. |
| .value[1].i32 | Direction of the linear gradient. The value is an enumerated value of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection). If the linear gradient direction is set to a value other than **ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM** of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection), the start angle of the linear gradient does not take effect. Default value: **ARKUI_LINEAR_GRADIENT_DIRECTION_LEFT_BOTTOM** of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection)|
| .value[2].i32 | Whether the gradient colors are repeated. The value **0** indicates that the gradient colors are not repeated, and **1** indicates that the gradient colors are repeated. The default value is **0**. |
| .object | Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md).<br> **colors**: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value.<br> **size**: number of colors. If the value is smaller than the length of the **colors** array, only the first **size** colors take effect. Values greater than the **colors** array length, values less than or equal to 0, or invalid values are not recommended.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Start angle of the linear gradient, in degree. When the direction of the linear gradient is ARKUI_LINEAR_GRADIENT_DIRECTION_CUSTOM of [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection), the start angle is the set value. In other cases, the default value **0** is used. |
| .value[1].i32 | Direction of the linear gradient. For details about the values and meanings, see [ArkUI_LinearGradientDirection](capi-native-type-visual-h.md#arkui_lineargradientdirection).|
| .value[2].i32 | Whether the gradient colors are repeated. The value **0** indicates that the gradient colors are not repeated, and **1** indicates that the gradient colors are repeated. The default value is **0**. |
| .object | Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md).<br> **colors**: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end.<br> **size**: number of effective gradient colors.|

## NODE_TEXT_AREA_RADIAL_GRADIENT

```c
NODE_TEXT_AREA_RADIAL_GRADIENT = 8049
```

Radial gradient effect of the text in the multi-line text box. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the radial gradient center relative to the upper left corner of the multi-line text box, in vp. The default value is half the width of the multi-line text input box. |
| .value[1]?.f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the multi-line text box, in vp. The default value is half the height of the multi-line text input box. |
| .value[2]?.f32 | Radius of the radial gradient. The value range is [0, +∞), and the default value is **0**. If a negative value is passed, the setting does not take effect. |
| .value[3]?.i32 | Whether the gradient colors are repeated. The value **0** indicates that the gradient colors are not repeated, and **1** indicates that the gradient colors are repeated. The default value is **0**. |
| .object | Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md).<br> **colors**: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end. To create a gradient with multiple color stops, you are advised to set the array elements in ascending order. If a later element is smaller than a previous one, it will be treated as equal to the previous value.<br> **size**: number of colors. If the value is smaller than the length of the **colors** array, only the first **size** colors take effect. Values greater than the **colors** array length, values less than or equal to 0, or invalid values are not recommended.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0]?.f32 | X-coordinate of the radial gradient center relative to the upper left corner of the multi-line text box, in vp. |
| .value[1]?.f32 | Y-coordinate of the radial gradient center relative to the upper left corner of the multi-line text box, in vp. |
| .value[2]?.f32 | Radius of the radial gradient, in vp. Default value: **0**. |
| .value[3]?.i32 | Whether the gradient colors are repeated. The value **0** indicates that the gradient color is not repeated, and **1** indicates that the gradient color is repeated. The default value is **0**. |
| .object | Color stop. The parameter type is [ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md).<br> **colors**: colors of the color stops, in 0xARGB format. For example, **0xFFFF0000** indicates red.<br> **stops**: stop positions of the color stops. The value range is [0, 1.0]. **0** represents the start of the gradient container, and **1.0** represents the end.<br> **size**: number of effective gradient colors.|

## NODE_TEXT_AREA_PUNCTUATION_OVERFLOW

```c
NODE_TEXT_AREA_PUNCTUATION_OVERFLOW = 8050
```

Whether to enable punctuation hanging at the end of a line for the **TextArea** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable punctuation hanging at the end of a line. The value **1** means to enable, and **0** means the opposite. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether punctuation hanging at the end of a line is enabled. **1** indicates enabled, **0** indicates disabled. |