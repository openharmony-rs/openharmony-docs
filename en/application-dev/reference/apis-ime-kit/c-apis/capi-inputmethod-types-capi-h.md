# inputmethod_types_capi.h

## Overview

Provides the input method types.

**Include**: <inputmethod/inputmethod_types_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputMethod_KeyboardStatus](#inputmethod_keyboardstatus) | InputMethod_KeyboardStatus | Enumerates the keyboard status. |
| [InputMethod_EnterKeyType](#inputmethod_enterkeytype) | InputMethod_EnterKeyType | Enumerates the Enter key types. |
| [InputMethod_Direction](#inputmethod_direction) | InputMethod_Direction | Enumerates the moving directions. |
| [InputMethod_ExtendAction](#inputmethod_extendaction) | InputMethod_ExtendAction | Enumerates the types of the extended edit action on the text box. |
| [InputMethod_TextInputType](#inputmethod_textinputtype) | InputMethod_TextInputType | Enumerates the text input types. |
| [InputMethod_CommandValueType](#inputmethod_commandvaluetype) | InputMethod_CommandValueType | Enumerates the private data types. |
| [InputMethod_ErrorCode](#inputmethod_errorcode) | InputMethod_ErrorCode | Enumerates the input method error codes. |
| [InputMethod_RequestKeyboardReason](#inputmethod_requestkeyboardreason) | InputMethod_RequestKeyboardReason | Enumerates the reasons for requesting the keyboard. |

### Macro

| Name | Description |
| -- | -- |
| OHOS_INPUTMETHOD_TYPES_CAPI_H | Provides the input method types.<br>**Since**: 12<br>**System capability**: SystemCapability.MiscServices.InputMethodFramework |

## Enum type description

### InputMethod_KeyboardStatus

```c
enum InputMethod_KeyboardStatus
```

**Description**

Enumerates the keyboard status.

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_KEYBOARD_STATUS_NONE = 0 | The keyboard status is none. |
| IME_KEYBOARD_STATUS_HIDE = 1 | The keyboard status is hide. |
| IME_KEYBOARD_STATUS_SHOW = 2 | The keyboard status is show. |

### InputMethod_EnterKeyType

```c
enum InputMethod_EnterKeyType
```

**Description**

Enumerates the Enter key types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_ENTER_KEY_UNSPECIFIED = 0 | The enter key type is UNSPECIFIED. |
| IME_ENTER_KEY_NONE = 1 | The enter key type is NONE. |
| IME_ENTER_KEY_GO = 2 | The enter key type is GO. |
| IME_ENTER_KEY_SEARCH = 3 | The enter key type is SEARCH. |
| IME_ENTER_KEY_SEND = 4 | The enter key type is SEND. |
| IME_ENTER_KEY_NEXT = 5 | The enter key type is NEXT. |
| IME_ENTER_KEY_DONE = 6 | The enter key type is DONE. |
| IME_ENTER_KEY_PREVIOUS = 7 | The enter key type is PREVIOUS. |
| IME_ENTER_KEY_NEWLINE = 8 | The enter key type is NEWLINE. |

### InputMethod_Direction

```c
enum InputMethod_Direction
```

**Description**

Enumerates the moving directions.

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_DIRECTION_NONE = 0 | The direction is NONE. |
| IME_DIRECTION_UP = 1 | The direction is UP. |
| IME_DIRECTION_DOWN = 2 | The direction is DOWN. |
| IME_DIRECTION_LEFT = 3 | The direction is LEFT. |
| IME_DIRECTION_RIGHT = 4 | The direction is RIGHT. |

### InputMethod_ExtendAction

```c
enum InputMethod_ExtendAction
```

**Description**

Enumerates the types of the extended edit action on the text box.

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_EXTEND_ACTION_SELECT_ALL = 0 | Select all text. |
| IME_EXTEND_ACTION_CUT = 3 | Cut selected text. |
| IME_EXTEND_ACTION_COPY = 4 | Copy selected text. |
| IME_EXTEND_ACTION_PASTE = 5 | Paste from paste board. |

### InputMethod_TextInputType

```c
enum InputMethod_TextInputType
```

**Description**

Enumerates the text input types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_TEXT_INPUT_TYPE_NONE = -1 | The text input type is NONE. |
| IME_TEXT_INPUT_TYPE_TEXT = 0 | The text input type is TEXT. |
| IME_TEXT_INPUT_TYPE_MULTILINE = 1 | The text input type is MULTILINE. |
| IME_TEXT_INPUT_TYPE_NUMBER = 2 | The text input type is NUMBER. |
| IME_TEXT_INPUT_TYPE_PHONE = 3 | The text input type is PHONE. |
| IME_TEXT_INPUT_TYPE_DATETIME = 4 | The text input type is DATETIME. |
| IME_TEXT_INPUT_TYPE_EMAIL_ADDRESS = 5 | The text input type is EMAIL ADDRESS. |
| IME_TEXT_INPUT_TYPE_URL = 6 | The text input type is URL. |
| IME_TEXT_INPUT_TYPE_VISIBLE_PASSWORD = 7 | The text input type is VISIBLE PASSWORD. |
| IME_TEXT_INPUT_TYPE_NUMBER_PASSWORD = 8 | The text input type is NUMBER PASSWORD. |
| IME_TEXT_INPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | The text input type is SCREEN LOCK PASSWORD. |
| IME_TEXT_INPUT_TYPE_USER_NAME = 10 | The text input type is USER NAME. |
| IME_TEXT_INPUT_TYPE_NEW_PASSWORD = 11 | The text input type is NEW PASSWORD. |
| IME_TEXT_INPUT_TYPE_NUMBER_DECIMAL = 12 | The text input type is NUMBER DECIMAL. |
| IME_TEXT_INPUT_TYPE_ONE_TIME_CODE = 13 | The text input type is ONE TIME CODE.<br>**Since**: 20 |

### InputMethod_CommandValueType

```c
enum InputMethod_CommandValueType
```

**Description**

Enumerates the private data types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_COMMAND_VALUE_TYPE_NONE = 0 | Value type is NONE. |
| IME_COMMAND_VALUE_TYPE_STRING = 1 | Value type is STRING. |
| IME_COMMAND_VALUE_TYPE_BOOL = 2 | Value type is BOOL. |
| IME_COMMAND_VALUE_TYPE_INT32 = 3 | Value type is INT32. |

### InputMethod_ErrorCode

```c
enum InputMethod_ErrorCode
```

**Description**

Enumerates the input method error codes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| IME_ERR_OK = 0 | The error code in the correct case. |
| IME_ERR_UNDEFINED = 1 | The error code when error is undefined. |
| IME_ERR_PARAMCHECK = 401 | The error code when parameter check failed. |
| IME_ERR_PACKAGEMANAGER = 12800001 | The error code when the bundle manager error. |
| IME_ERR_IMENGINE = 12800002 | The error code when input method engine error. |
| IME_ERR_IMCLIENT = 12800003 | The error code when input method client error. |
| IME_ERR_CONFIG_PERSIST = 12800005 | The error code when configuration persistence error. This error code is reported when the configuration fails to be saved. |
| IME_ERR_CONTROLLER = 12800006 | The error code when input method controller error. |
| IME_ERR_SETTINGS = 12800007 | The error code when input method setting error. |
| IME_ERR_IMMS = 12800008 | The error code when input method manager service error. |
| IME_ERR_DETACHED = 12800009 | The error code when input method client detached. |
| IME_ERR_NULL_POINTER = 12802000 | The error code when unexpected null pointer. |
| IME_ERR_QUERY_FAILED = 12802001 | The error code when query failed. |

### InputMethod_RequestKeyboardReason

```c
enum InputMethod_RequestKeyboardReason
```

**Description**

Enumerates the reasons for requesting the keyboard.

**Since**: 15

| Enum item | Description |
| -- | -- |
| IME_REQUEST_REASON_NONE = 0 | The request keyboard reason is NONE. |
| IME_REQUEST_REASON_MOUSE = 1 | The request keyboard reason is MOUSE. |
| IME_REQUEST_REASON_TOUCH = 2 | The request keyboard reason is TOUCH. |
| IME_REQUEST_REASON_OTHER = 20 | The request keyboard reason is OTHER. |


