# inputmethod_types_capi.h

## Overview

Defines the types related to the input method.

**File to Include**: <inputmethod/inputmethod_types_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-ime-kit-inputmethod.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_KeyboardStatus](#inputmethod_keyboardstatus) | InputMethod_KeyboardStatus | Enumerates the keyboard status. |
| [InputMethod_EnterKeyType](#inputmethod_enterkeytype) | InputMethod_EnterKeyType | Enumerates the Enter key types. |
| [InputMethod_Direction](#inputmethod_direction) | InputMethod_Direction | Enumerates the moving directions. |
| [InputMethod_ExtendAction](#inputmethod_extendaction) | InputMethod_ExtendAction | Enumerates the types of the extended edit action on the text box. |
| [InputMethod_TextInputType](#inputmethod_textinputtype) | InputMethod_TextInputType | Enumerates the text input types. |
| [InputMethod_CommandValueType](#inputmethod_commandvaluetype) | InputMethod_CommandValueType | Enumerates the private data types. |
| [InputMethod_ErrorCode](#inputmethod_errorcode) | InputMethod_ErrorCode | Enumeration of error codes of the input method, which defines the error codes that may occur in the input method framework, covering various error scenarios such as parameter check failure, package management exception, input method application exception, and text box client exception. Developers need to determine the error type based on the specific error code and take corresponding measures to rectify the error. For details, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md). <br> <br>Function: Identifies the execution results and error types of various operations in the input method framework, which is used to determine interface return values and handle errors. <br> <br>Suggested value: After invoking the input method C API, check whether the return value is IME_ERR_OK(0). If a value other than IME_ERR_OK is returned, rectify the fault based on the error code: IME_ERR_NULL_POINTER checks whether the parameter value is NULL. IME_ERR_PARAMCHECK checks the parameter type and range. The IME_ERR_IMCLIENT/IME_ERR_DETACHED checks the connection between the input box and the input method service. IME_ERR_IMENGINE checks the running status of the input method application. IME_ERR_QUERY_FAILED checks the query conditions and data status. <br> <br> Relationship between enumerated values: Enumerated values are classified into three groups: common error codes(0, 1, 401), framework service error codes(12800001-12800029), and C API error codes(12802000-12802001). Common error codes are applicable to all interfaces. Framework service error codes are related to system service status. Error codes dedicated to C APIs apply to null pointers and query failure scenarios specific to C language interfaces. IME_ERR_OK(0) indicates success, and other values indicate error. |
| [InputMethod_RequestKeyboardReason](#inputmethod_requestkeyboardreason) | InputMethod_RequestKeyboardReason | Enumerates the reasons for requesting the keyboard. |
| [OH_InputMethod_UnderlineStyle](#oh_inputmethod_underlinestyle) | OH_InputMethod_UnderlineStyle | Pre-screen text underline style enumeration. |
| [OH_InputMethod_InputCapabilityType](#oh_inputmethod_inputcapabilitytype) | OH_InputMethod_InputCapabilityType | Input capability type enumeration. |

### Macros

| Name | Description |
| -- | -- |
| OHOS_INPUTMETHOD_TYPES_CAPI_H | Defines the types related to the input method.<br>**Since**: 12<br>**System capability**: SystemCapability.MiscServices.InputMethodFramework |

## Enum type description

### InputMethod_KeyboardStatus

```c
enum InputMethod_KeyboardStatus
```

**Description**

Enumerates the keyboard status.

<!--Device-enum InputMethod_KeyboardStatus--><!--Device-enum InputMethod_KeyboardStatus-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_KEYBOARD_STATUS_NONE = 0 | NONE.<br><!--Device-IME_KEYBOARD_STATUS_NONE = 0--><!--Device-IME_KEYBOARD_STATUS_NONE = 0-End--> |
| IME_KEYBOARD_STATUS_HIDE = 1 | Invisible.<br><!--Device-IME_KEYBOARD_STATUS_HIDE = 1--><!--Device-IME_KEYBOARD_STATUS_HIDE = 1-End--> |
| IME_KEYBOARD_STATUS_SHOW = 2 | Visible.<br><!--Device-IME_KEYBOARD_STATUS_SHOW = 2--><!--Device-IME_KEYBOARD_STATUS_SHOW = 2-End--> |

### InputMethod_EnterKeyType

```c
enum InputMethod_EnterKeyType
```

**Description**

Enumerates the Enter key types.

<!--Device-enum InputMethod_EnterKeyType--><!--Device-enum InputMethod_EnterKeyType-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_ENTER_KEY_UNSPECIFIED = 0 | Unspecified.<br><!--Device-IME_ENTER_KEY_UNSPECIFIED = 0--><!--Device-IME_ENTER_KEY_UNSPECIFIED = 0-End--> |
| IME_ENTER_KEY_NONE = 1 | NONE.<br><!--Device-IME_ENTER_KEY_NONE = 1--><!--Device-IME_ENTER_KEY_NONE = 1-End--> |
| IME_ENTER_KEY_GO = 2 | Go.<br><!--Device-IME_ENTER_KEY_GO = 2--><!--Device-IME_ENTER_KEY_GO = 2-End--> |
| IME_ENTER_KEY_SEARCH = 3 | Search.<br><!--Device-IME_ENTER_KEY_SEARCH = 3--><!--Device-IME_ENTER_KEY_SEARCH = 3-End--> |
| IME_ENTER_KEY_SEND = 4 | Send.<br><!--Device-IME_ENTER_KEY_SEND = 4--><!--Device-IME_ENTER_KEY_SEND = 4-End--> |
| IME_ENTER_KEY_NEXT = 5 | Next.<br><!--Device-IME_ENTER_KEY_NEXT = 5--><!--Device-IME_ENTER_KEY_NEXT = 5-End--> |
| IME_ENTER_KEY_DONE = 6 | Done.<br><!--Device-IME_ENTER_KEY_DONE = 6--><!--Device-IME_ENTER_KEY_DONE = 6-End--> |
| IME_ENTER_KEY_PREVIOUS = 7 | Previous.<br><!--Device-IME_ENTER_KEY_PREVIOUS = 7--><!--Device-IME_ENTER_KEY_PREVIOUS = 7-End--> |
| IME_ENTER_KEY_NEWLINE = 8 | Line break.<br><!--Device-IME_ENTER_KEY_NEWLINE = 8--><!--Device-IME_ENTER_KEY_NEWLINE = 8-End--> |

### InputMethod_Direction

```c
enum InputMethod_Direction
```

**Description**

Enumerates the moving directions.

<!--Device-enum InputMethod_Direction--><!--Device-enum InputMethod_Direction-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_DIRECTION_NONE = 0 | NONE.<br><!--Device-IME_DIRECTION_NONE = 0--><!--Device-IME_DIRECTION_NONE = 0-End--> |
| IME_DIRECTION_UP = 1 | Upward.<br><!--Device-IME_DIRECTION_UP = 1--><!--Device-IME_DIRECTION_UP = 1-End--> |
| IME_DIRECTION_DOWN = 2 | Downward.<br><!--Device-IME_DIRECTION_DOWN = 2--><!--Device-IME_DIRECTION_DOWN = 2-End--> |
| IME_DIRECTION_LEFT = 3 | Leftward.<br><!--Device-IME_DIRECTION_LEFT = 3--><!--Device-IME_DIRECTION_LEFT = 3-End--> |
| IME_DIRECTION_RIGHT = 4 | Rightward.<br><!--Device-IME_DIRECTION_RIGHT = 4--><!--Device-IME_DIRECTION_RIGHT = 4-End--> |

### InputMethod_ExtendAction

```c
enum InputMethod_ExtendAction
```

**Description**

Enumerates the types of the extended edit action on the text box.

<!--Device-enum InputMethod_ExtendAction--><!--Device-enum InputMethod_ExtendAction-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_EXTEND_ACTION_SELECT_ALL = 0 | Select all.<br><!--Device-IME_EXTEND_ACTION_SELECT_ALL = 0--><!--Device-IME_EXTEND_ACTION_SELECT_ALL = 0-End--> |
| IME_EXTEND_ACTION_CUT = 3 | Cut.<br><!--Device-IME_EXTEND_ACTION_CUT = 3--><!--Device-IME_EXTEND_ACTION_CUT = 3-End--> |
| IME_EXTEND_ACTION_COPY = 4 | Copy.<br><!--Device-IME_EXTEND_ACTION_COPY = 4--><!--Device-IME_EXTEND_ACTION_COPY = 4-End--> |
| IME_EXTEND_ACTION_PASTE = 5 | Paste.<br><!--Device-IME_EXTEND_ACTION_PASTE = 5--><!--Device-IME_EXTEND_ACTION_PASTE = 5-End--> |

### InputMethod_TextInputType

```c
enum InputMethod_TextInputType
```

**Description**

Enumerates the text input types.

<!--Device-enum InputMethod_TextInputType--><!--Device-enum InputMethod_TextInputType-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_TEXT_INPUT_TYPE_NONE = -1 | NONE.<br><!--Device-IME_TEXT_INPUT_TYPE_NONE = -1--><!--Device-IME_TEXT_INPUT_TYPE_NONE = -1-End--> |
| IME_TEXT_INPUT_TYPE_TEXT = 0 | Text.<br><!--Device-IME_TEXT_INPUT_TYPE_TEXT = 0--><!--Device-IME_TEXT_INPUT_TYPE_TEXT = 0-End--> |
| IME_TEXT_INPUT_TYPE_MULTILINE = 1 | Multi-line.<br><!--Device-IME_TEXT_INPUT_TYPE_MULTILINE = 1--><!--Device-IME_TEXT_INPUT_TYPE_MULTILINE = 1-End--> |
| IME_TEXT_INPUT_TYPE_NUMBER = 2 | Number.<br><!--Device-IME_TEXT_INPUT_TYPE_NUMBER = 2--><!--Device-IME_TEXT_INPUT_TYPE_NUMBER = 2-End--> |
| IME_TEXT_INPUT_TYPE_PHONE = 3 | Phone number.<br><!--Device-IME_TEXT_INPUT_TYPE_PHONE = 3--><!--Device-IME_TEXT_INPUT_TYPE_PHONE = 3-End--> |
| IME_TEXT_INPUT_TYPE_DATETIME = 4 | Date.<br><!--Device-IME_TEXT_INPUT_TYPE_DATETIME = 4--><!--Device-IME_TEXT_INPUT_TYPE_DATETIME = 4-End--> |
| IME_TEXT_INPUT_TYPE_EMAIL_ADDRESS = 5 | Email address.<br><!--Device-IME_TEXT_INPUT_TYPE_EMAIL_ADDRESS = 5--><!--Device-IME_TEXT_INPUT_TYPE_EMAIL_ADDRESS = 5-End--> |
| IME_TEXT_INPUT_TYPE_URL = 6 | URL.<br><!--Device-IME_TEXT_INPUT_TYPE_URL = 6--><!--Device-IME_TEXT_INPUT_TYPE_URL = 6-End--> |
| IME_TEXT_INPUT_TYPE_VISIBLE_PASSWORD = 7 | Password.<br><!--Device-IME_TEXT_INPUT_TYPE_VISIBLE_PASSWORD = 7--><!--Device-IME_TEXT_INPUT_TYPE_VISIBLE_PASSWORD = 7-End--> |
| IME_TEXT_INPUT_TYPE_NUMBER_PASSWORD = 8 | Numeric password.<br><!--Device-IME_TEXT_INPUT_TYPE_NUMBER_PASSWORD = 8--><!--Device-IME_TEXT_INPUT_TYPE_NUMBER_PASSWORD = 8-End--> |
| IME_TEXT_INPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | Lock screen password.<br><!--Device-IME_TEXT_INPUT_TYPE_SCREEN_LOCK_PASSWORD = 9--><!--Device-IME_TEXT_INPUT_TYPE_SCREEN_LOCK_PASSWORD = 9-End--> |
| IME_TEXT_INPUT_TYPE_USER_NAME = 10 | Username.<br><!--Device-IME_TEXT_INPUT_TYPE_USER_NAME = 10--><!--Device-IME_TEXT_INPUT_TYPE_USER_NAME = 10-End--> |
| IME_TEXT_INPUT_TYPE_NEW_PASSWORD = 11 | New password.<br><!--Device-IME_TEXT_INPUT_TYPE_NEW_PASSWORD = 11--><!--Device-IME_TEXT_INPUT_TYPE_NEW_PASSWORD = 11-End--> |
| IME_TEXT_INPUT_TYPE_NUMBER_DECIMAL = 12 | Decimal number.<br><!--Device-IME_TEXT_INPUT_TYPE_NUMBER_DECIMAL = 12--><!--Device-IME_TEXT_INPUT_TYPE_NUMBER_DECIMAL = 12-End--> |
| IME_TEXT_INPUT_TYPE_ONE_TIME_CODE = 13 | Verification code.<br>**Since**: 20<br><!--Device-IME_TEXT_INPUT_TYPE_ONE_TIME_CODE = 13--><!--Device-IME_TEXT_INPUT_TYPE_ONE_TIME_CODE = 13-End--> |

### InputMethod_CommandValueType

```c
enum InputMethod_CommandValueType
```

**Description**

Enumerates the private data types.

<!--Device-enum InputMethod_CommandValueType--><!--Device-enum InputMethod_CommandValueType-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_COMMAND_VALUE_TYPE_NONE = 0 | NONE.<br><!--Device-IME_COMMAND_VALUE_TYPE_NONE = 0--><!--Device-IME_COMMAND_VALUE_TYPE_NONE = 0-End--> |
| IME_COMMAND_VALUE_TYPE_STRING = 1 | String.<br><!--Device-IME_COMMAND_VALUE_TYPE_STRING = 1--><!--Device-IME_COMMAND_VALUE_TYPE_STRING = 1-End--> |
| IME_COMMAND_VALUE_TYPE_BOOL = 2 | Boolean.<br><!--Device-IME_COMMAND_VALUE_TYPE_BOOL = 2--><!--Device-IME_COMMAND_VALUE_TYPE_BOOL = 2-End--> |
| IME_COMMAND_VALUE_TYPE_INT32 = 3 | 32-bit signed integer.<br><!--Device-IME_COMMAND_VALUE_TYPE_INT32 = 3--><!--Device-IME_COMMAND_VALUE_TYPE_INT32 = 3-End--> |

### InputMethod_ErrorCode

```c
enum InputMethod_ErrorCode
```

**Description**

Enumeration of error codes of the input method, which defines the error codes that may occur in the input method framework, covering various error scenarios such as parameter check failure, package management exception, input method application exception, and text box client exception. Developers need to determine the error type based on the specific error code and take corresponding measures to rectify the error. For details, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md). <br> <br>Function: Identifies the execution results and error types of various operations in the input method framework, which is used to determine interface return values and handle errors. <br> <br>Suggested value: After invoking the input method C API, check whether the return value is IME_ERR_OK(0). If a value other than IME_ERR_OK is returned, rectify the fault based on the error code: IME_ERR_NULL_POINTER checks whether the parameter value is NULL. IME_ERR_PARAMCHECK checks the parameter type and range. The IME_ERR_IMCLIENT/IME_ERR_DETACHED checks the connection between the input box and the input method service. IME_ERR_IMENGINE checks the running status of the input method application. IME_ERR_QUERY_FAILED checks the query conditions and data status. <br> <br> Relationship between enumerated values: Enumerated values are classified into three groups: common error codes(0, 1, 401), framework service error codes(12800001-12800029), and C API error codes(12802000-12802001). Common error codes are applicable to all interfaces. Framework service error codes are related to system service status. Error codes dedicated to C APIs apply to null pointers and query failure scenarios specific to C language interfaces. IME_ERR_OK(0) indicates success, and other values indicate error.

<!--Device-enum InputMethod_ErrorCode--><!--Device-enum InputMethod_ErrorCode-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_ERR_OK = 0 | &nbsp;Success.<br><!--Device-IME_ERR_OK = 0--><!--Device-IME_ERR_OK = 0-End--> |
| IME_ERR_UNDEFINED = 1 | &nbsp;Undefined error.<br><!--Device-IME_ERR_UNDEFINED = 1--><!--Device-IME_ERR_UNDEFINED = 1-End--> |
| OH_INPUTMETHOD_ERR_PERMISSION_DENIED = 201 | Permission verification failed.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_ERR_PERMISSION_DENIED = 201--><!--Device-OH_INPUTMETHOD_ERR_PERMISSION_DENIED = 201-End--> |
| IME_ERR_PARAMCHECK = 401 | &nbsp;Parameter check failed.<br><!--Device-IME_ERR_PARAMCHECK = 401--><!--Device-IME_ERR_PARAMCHECK = 401-End--> |
| OH_INPUTMETHOD_ERR_DEVICE_NOT_SUPPORTED = 801 | The current device does not support this interface.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_ERR_DEVICE_NOT_SUPPORTED = 801--><!--Device-OH_INPUTMETHOD_ERR_DEVICE_NOT_SUPPORTED = 801-End--> |
| IME_ERR_PACKAGEMANAGER = 12800001 | &nbsp;Package management error.<br><!--Device-IME_ERR_PACKAGEMANAGER = 12800001--><!--Device-IME_ERR_PACKAGEMANAGER = 12800001-End--> |
| IME_ERR_IMENGINE = 12800002 | &nbsp;Input method application error.<br><!--Device-IME_ERR_IMENGINE = 12800002--><!--Device-IME_ERR_IMENGINE = 12800002-End--> |
| IME_ERR_IMCLIENT = 12800003 | &nbsp;Text box client error.<br><!--Device-IME_ERR_IMCLIENT = 12800003--><!--Device-IME_ERR_IMCLIENT = 12800003-End--> |
| IME_ERR_CONFIG_PERSIST = 12800005 | &nbsp;Configuration persistence failed. This error code is reported when the configuration fails to be saved.<br><!--Device-IME_ERR_CONFIG_PERSIST = 12800005--><!--Device-IME_ERR_CONFIG_PERSIST = 12800005-End--> |
| IME_ERR_CONTROLLER = 12800006 | &nbsp;Input method controller error.<br><!--Device-IME_ERR_CONTROLLER = 12800006--><!--Device-IME_ERR_CONTROLLER = 12800006-End--> |
| IME_ERR_SETTINGS = 12800007 | &nbsp;Input method setter error.<br><!--Device-IME_ERR_SETTINGS = 12800007--><!--Device-IME_ERR_SETTINGS = 12800007-End--> |
| IME_ERR_IMMS = 12800008 | &nbsp;Input method manager service error.<br><!--Device-IME_ERR_IMMS = 12800008--><!--Device-IME_ERR_IMMS = 12800008-End--> |
| IME_ERR_DETACHED = 12800009 | &nbsp;Text box unbound.<br><!--Device-IME_ERR_DETACHED = 12800009--><!--Device-IME_ERR_DETACHED = 12800009-End--> |
| OH_INPUTMETHOD_ERR_NOT_DEFAULT_IME = 12800010 | Error code when the current input method is not the default input method preset in the system.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_ERR_NOT_DEFAULT_IME = 12800010--><!--Device-OH_INPUTMETHOD_ERR_NOT_DEFAULT_IME = 12800010-End--> |
| OH_INPUTMETHOD_ERR_EDITABLE = 12800016 | The text box is in the non-editing state. The text box may still be bound. This error cannot be equated with unbound.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_ERR_EDITABLE = 12800016--><!--Device-OH_INPUTMETHOD_ERR_EDITABLE = 12800016-End--> |
| OH_INPUTMETHOD_ERR_INPUT_CAPABILITY_TYPE_NOT_SUPPORTED = 12800029 | Error code when the input capability type is not supported.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_ERR_INPUT_CAPABILITY_TYPE_NOT_SUPPORTED = 12800029--><!--Device-OH_INPUTMETHOD_ERR_INPUT_CAPABILITY_TYPE_NOT_SUPPORTED = 12800029-End--> |
| IME_ERR_NULL_POINTER = 12802000 | &nbsp;Null pointer.<br><!--Device-IME_ERR_NULL_POINTER = 12802000--><!--Device-IME_ERR_NULL_POINTER = 12802000-End--> |
| IME_ERR_QUERY_FAILED = 12802001 | &nbsp;Query failed.<br><!--Device-IME_ERR_QUERY_FAILED = 12802001--><!--Device-IME_ERR_QUERY_FAILED = 12802001-End--> |

### InputMethod_RequestKeyboardReason

```c
enum InputMethod_RequestKeyboardReason
```

**Description**

Enumerates the reasons for requesting the keyboard.

<!--Device-enum InputMethod_RequestKeyboardReason--><!--Device-enum InputMethod_RequestKeyboardReason-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 15

| Enum item | Description |
| -- | -- |
| IME_REQUEST_REASON_NONE = 0 | No reason.<br><!--Device-IME_REQUEST_REASON_NONE = 0--><!--Device-IME_REQUEST_REASON_NONE = 0-End--> |
| IME_REQUEST_REASON_MOUSE = 1 | Mouse operation.<br><!--Device-IME_REQUEST_REASON_MOUSE = 1--><!--Device-IME_REQUEST_REASON_MOUSE = 1-End--> |
| IME_REQUEST_REASON_TOUCH = 2 | Touch operation.<br><!--Device-IME_REQUEST_REASON_TOUCH = 2--><!--Device-IME_REQUEST_REASON_TOUCH = 2-End--> |
| IME_REQUEST_REASON_OTHER = 20 | Other reasons.<br><!--Device-IME_REQUEST_REASON_OTHER = 20--><!--Device-IME_REQUEST_REASON_OTHER = 20-End--> |

### OH_InputMethod_UnderlineStyle

```c
enum OH_InputMethod_UnderlineStyle
```

**Description**

Pre-screen text underline style enumeration.

<!--Device-enum OH_InputMethod_UnderlineStyle--><!--Device-enum OH_InputMethod_UnderlineStyle-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_INPUTMETHOD_UNDERLINE_STYLE_NONE = 0 | No underline.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_UNDERLINE_STYLE_NONE = 0--><!--Device-OH_INPUTMETHOD_UNDERLINE_STYLE_NONE = 0-End--> |
| OH_INPUTMETHOD_UNDERLINE_STYLE_SOLID = 1 | Solid underline.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_UNDERLINE_STYLE_SOLID = 1--><!--Device-OH_INPUTMETHOD_UNDERLINE_STYLE_SOLID = 1-End--> |
| OH_INPUTMETHOD_UNDERLINE_STYLE_WAVY = 2 | Wavy lines underline.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_UNDERLINE_STYLE_WAVY = 2--><!--Device-OH_INPUTMETHOD_UNDERLINE_STYLE_WAVY = 2-End--> |
| OH_INPUTMETHOD_UNDERLINE_STYLE_DASHED = 3 | Dotted underline.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_UNDERLINE_STYLE_DASHED = 3--><!--Device-OH_INPUTMETHOD_UNDERLINE_STYLE_DASHED = 3-End--> |

### OH_InputMethod_InputCapabilityType

```c
enum OH_InputMethod_InputCapabilityType
```

**Description**

Input capability type enumeration.

<!--Device-enum OH_InputMethod_InputCapabilityType--><!--Device-enum OH_InputMethod_InputCapabilityType-End-->

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_INPUTMETHOD_INPUT_CAPABILITY_TYPE_TRANSLATION = 0 | Set Capability Type to Translation.<br>**Since**: 26.1.0<br><!--Device-OH_INPUTMETHOD_INPUT_CAPABILITY_TYPE_TRANSLATION = 0--><!--Device-OH_INPUTMETHOD_INPUT_CAPABILITY_TYPE_TRANSLATION = 0-End--> |


