# inputmethod_types_capi.h
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4c244f2ed12456a4c6059eccff764e442d7872b9 translatedAt=2026-08-31T10:48:28.839Z pushedAt=2026-09-02T07:39:12.586Z -->

## Overview

Provides type definitions related to the input method, including keyboard status, Enter key function type, cursor movement direction, and more. These type definitions are used to describe the interaction behavior between the input method app and the edit box client. The keyboard status defines the shown and hidden states of the soft keyboard; the Enter key function type defines the triggering behavior of the Enter key in different input scenarios; the cursor movement direction defines the movement operations of the cursor in the edit box.

**File to include**: <inputmethod/inputmethod_types_capi.h>

**Library**: libohinputmethod.so

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Since**: 12

**Related module**: [InputMethod](capi-inputmethod.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [InputMethod_KeyboardStatus](#inputmethod_keyboardstatus) | InputMethod_KeyboardStatus | Keyboard status. Defines the shown and hidden states of the soft keyboard, used to identify the current keyboard status in the **OH_TextEditorProxy_SendKeyboardStatusFunc** callback. |
| [InputMethod_EnterKeyType](#inputmethod_enterkeytype) | InputMethod_EnterKeyType | Enter key function type. Defines the trigger behavior of the Enter key in different input scenarios, used to configure the function semantics of the Enter key in the edit box. |
| [InputMethod_Direction](#inputmethod_direction) | InputMethod_Direction | Movement direction. Defines the movement direction of the cursor or selection area in the edit box, used to support the input method app in implementing editing operations such as cursor movement and text selection. |
| [InputMethod_ExtendAction](#inputmethod_extendaction) | InputMethod_ExtendAction | Extended edit action type for text in the edit box. Defines common editing operations that can be performed on edit box text, including select all, cut, copy, and paste. These operations work in coordination with the system clipboard to implement the text editing functions of the input method app. |
| [InputMethod_TextInputType](#inputmethod_textinputtype) | InputMethod_TextInputType | Text input type. Used to specify the input types supported by the text edit box so that the system can adapt the corresponding input method keyboard to the given scenario. For example: the **NUMBER** type is used for numeric input scenarios (such as password input boxes and age input boxes); the **EMAIL_ADDRESS** type is used for email address input scenarios; the URL type is used for website address input scenarios. |
| [InputMethod_CommandValueType](#inputmethod_commandvaluetype) | InputMethod_CommandValueType | Private data type of the extended features of the input method. Defines the data type of value in **InputMethod_PrivateCommand**, used to support private parameter passing between the input method app and the client. |
| [InputMethod_ErrorCode](#inputmethod_errorcode) | InputMethod_ErrorCode | Input method error code. Defines the error codes that may occur in the input method framework, covering various error scenarios such as parameter check failure, package management exception, input method app exception, and input box client exception. You should determine the error type according to the specific error code and handle the error accordingly. For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md). |
| [InputMethod_RequestKeyboardReason](#inputmethod_requestkeyboardreason) | InputMethod_RequestKeyboardReason | Reason for requesting keyboard input. Used to distinguish different keyboard trigger scenarios so that the input method can perform targeted adaptation. |

## Enum Description

### InputMethod_KeyboardStatus

```c
enum InputMethod_KeyboardStatus
```

**Description**

Enumerates keyboard states, defining the shown and hidden states of the soft keyboard. This enum is used in the **OH_TextEditorProxy_SendKeyboardStatusFunc** callback to identify the current keyboard status change. The edit box client can adjust the UI layout according to the keyboard status (for example, avoiding the edit box area when the keyboard pops up).

Purpose: Identifies the current status of the soft keyboard, used for the edit box client to respond to keyboard shown or hidden events.

Value suggestion: When processing the **SendKeyboardStatusFunc** callback, adjust the interface to avoid the keyboard area according to **IME_KEYBOARD_STATUS_SHOW**, and restore the original layout according to **IME_KEYBOARD_STATUS_HIDE**. **IME_KEYBOARD_STATUS_NONE** usually appears as an initial state or transitional state and generally does not require special handling.

Relationship between enum values: The enum values start from 0 and increase consecutively (**NONE** → **HIDE** → **SHOW**), indicating the progressive change of keyboard status from no state to hidden, and then to shown.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| IME_KEYBOARD_STATUS_NONE = 0 | Indicates that the keyboard status is **NONE**, meaning the keyboard status has not been determined or is in the initial state. This value is usually used during the initialization phase of the input method framework, indicating that the keyboard has not yet been shown or hidden. It rarely appears in actual interaction, and the edit box client generally does not need to perform special handling for the **NONE** status. |
| IME_KEYBOARD_STATUS_HIDE = 1 | The keyboard status is hidden, indicating that the soft keyboard has been collapsed or not popped up. After receiving this status, the edit box client can restore the UI layout (for example, cancel the avoidance area and restore the original position of the edit box), because the keyboard no longer occupies the bottom area of the screen. |
| IME_KEYBOARD_STATUS_SHOW = 2 | The keyboard status is shown, indicating that the soft keyboard has popped up and occupies the bottom area of the screen. After receiving this status, the edit box client should adjust the UI layout (for example, avoid the keyboard area and move the edit box upward) to ensure that the input area is not covered by the keyboard. |

### InputMethod_EnterKeyType

```c
enum InputMethod_EnterKeyType
```

**Description**

Enumerates Enter key function types, defining the triggering behavior of the Enter key in different input scenarios. This enum is used to configure the Enter key function semantics of the edit box. The input method framework displays the corresponding function label on the keyboard according to **EnterKeyType** (such as "Search", "Send", and "Next") and triggers the corresponding interaction behavior.

Purpose: Specifies the Enter key function semantics of the edit box, affecting the label and behavior of the Enter key on the input method keyboard.

Value suggestion: Select the corresponding **EnterKeyType** according to the actual interaction scenario of the edit box. Use **IME_ENTER_KEY_SEARCH** for search scenarios, **IME_ENTER_KEY_SEND** for message sending scenarios, **IME_ENTER_KEY_NEXT** or **IME_ENTER_KEY_DONE** for form filling scenarios, and **IME_ENTER_KEY_NEWLINE** for multiline text input scenarios. Use **IME_ENTER_KEY_UNSPECIFIED** for uncertain scenarios, and the system will use the default behavior.

Relationship between enum values: The enum values start from 0 and increase consecutively (from **0** to **8**), with a total of 9 enum items. There is no mutual exclusion relationship between the values, and each edit box can independently configure one **EnterKeyType**. The difference between **IME_ENTER_KEY_UNSPECIFIED** (**0**) and **IME_ENTER_KEY_NONE** (**1**) lies in that: **UNSPECIFIED** indicates unspecified Enter key type (the system uses the default behavior), while **NONE** indicates that the Enter key is explicitly specified to have no special function.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| IME_ENTER_KEY_UNSPECIFIED = 0 | Unspecified, indicating that the edit box has not explicitly set the Enter key function type. The system will use the default Enter key behavior (usually equivalent to a newline). Applicable to ordinary text input scenarios that do not require special Enter key behavior. |
| IME_ENTER_KEY_NONE = 1 | The Enter key function type is **NONE**, explicitly specifying that the Enter key has no special function. The Enter key will not trigger any specific behavior and is handled only as an ordinary key. Applicable to scenarios where the Enter key does not need to trigger any action. |
| IME_ENTER_KEY_GO = 2 | Go, indicating that the Enter key function is "Go". Pressing the Enter key will trigger navigation to the target address. Applicable to scenarios such as URL input boxes and browser address bars that need to jump to a specified link. The Enter key label on the keyboard is displayed as "Go". |
| IME_ENTER_KEY_SEARCH = 3 | Search, indicating that the Enter key function is "Search". Pressing the Enter key will trigger a search operation. Applicable to scenarios such as search input boxes and search engines that need to execute a search query. The Enter key label on the keyboard is displayed as "Search". |
| IME_ENTER_KEY_SEND = 4 | Send, indicating that the Enter key function is "Send". Pressing the Enter key will trigger the operation of sending a message or data. Applicable to scenarios such as instant message input boxes and email sending that need to submit content. The Enter key label on the keyboard is displayed as "Send". |
| IME_ENTER_KEY_NEXT = 5 | Next, indicating that the Enter key function is "Next". Pressing the Enter key moves the focus to the next input box. Applicable to multi-field form filling scenarios (such as registration forms and address filling), where the user automatically jumps to the next input item after pressing Enter. The Enter key label on the keyboard is displayed as "Next". |
| IME_ENTER_KEY_DONE = 6 | Done, indicating that the Enter key function is "Done". Pressing the Enter key ends the current input and closes the keyboard. Applicable to scenarios such as the last input box of a form and input confirmation that need to indicate input completion. The Enter key label on the keyboard is displayed as "Done". |
| IME_ENTER_KEY_PREVIOUS = 7 | Previous, indicating that the Enter key function is "Previous". Pressing the Enter key moves the focus to the previous input box. Applicable to scenarios in multi-field forms where the user needs to return to the previous input item. The Enter key label on the keyboard is displayed as "Previous". |
| IME_ENTER_KEY_NEWLINE = 8 | Newline, indicating that the Enter key function is "Newline". Pressing the Enter key inserts a new line in the text. Applicable to multiline text editing scenarios (such as memos and note editing), where the user needs to add a line break in the text through the Enter key. The Enter key label on the keyboard is displayed as "Newline". |

### InputMethod_Direction

```c
enum InputMethod_Direction
```

**Description**

Enumerates movement directions of the cursor or selection area in the edit box, used to support the input method app in implementing editing operations such as cursor movement and text selection. This enum acts as a parameter passed to the **OH_TextEditorProxy_MoveCursorFunc** callback, indicating the direction in which the input method requests the cursor to move.

Purpose: Specifies the movement direction of the cursor in the edit box, used by the input method app to control the cursor position.

Value suggestion: When implementing the **MoveCursorFunc** callback, move the cursor according to the direction value. **IME_DIRECTION_NONE** usually indicates no movement is required, **IME_DIRECTION_UP** and **IME_DIRECTION_DOWN** are used for vertical movement (multiline text scenarios), and **IME_DIRECTION_LEFT** and **IME_DIRECTION_RIGHT** are used for horizontal movement (single-line or multiline text scenarios).

Relationship between enum values: The enum values start from 0 and increase consecutively (from **0** to **4**), with 5 enum items in total. The four direction values (**UP**/**DOWN**/**LEFT**/**RIGHT**) cover the basic movement directions on a two-dimensional plane, and **NONE** serves as the identifier for no movement. **UP** and **DOWN** are opposite to each other, and **LEFT** and **RIGHT** are opposite to each other.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| IME_DIRECTION_NONE = 0 | No movement direction, indicating that the cursor does not need to move. This value is usually used as a default value or placeholder value, and the input method app passes this value when the cursor does not need to be moved. |
| IME_DIRECTION_UP = 1 | Upward, indicating that the cursor moves up one line. Applicable to multiline text editing scenarios, the input method app uses this value to request moving the cursor from the current line to the previous line. In single-line text scenarios, upward movement usually has no actual effect. |
| IME_DIRECTION_DOWN = 2 | Downward, indicating that the cursor moves down one line. Applicable to multiline text editing scenarios, the input method app uses this value to request moving the cursor from the current line to the next line. In single-line text scenarios, downward movement usually has no actual effect. |
| IME_DIRECTION_LEFT = 3 | Leftward, indicating that the cursor moves left by one character position. Applicable to all text editing scenarios, the input method app uses this value to request moving the cursor forward by one character. Commonly used for cursor rollback after preceding text deletion. |
| IME_DIRECTION_RIGHT = 4 | Rightward, indicating that the cursor moves right by one character position. Applicable to all text editing scenarios, the input method app uses this value to request moving the cursor backward by one character. Commonly used for cursor advancement after text insertion. |

### InputMethod_ExtendAction

```c
enum InputMethod_ExtendAction
```

**Description**

Enumerates the types of extended edit actions on the text in the edit box, defining the common edit operations that can be performed on the edit box content, including select all, cut, copy, and paste. These operations work in coordination with the system clipboard to implement the text editing functions of the input method app. This enum is passed as a parameter of the **OH_TextEditorProxy_HandleExtendActionFunc** callback, indicating the edit operation requested by the input method.

Purpose: Specifies the type of text edit operation that the input method requests the edit box to perform.

Value suggestion: When implementing the **HandleExtendActionFunc** callback, perform the corresponding edit operation according to the action value. **IME_EXTEND_ACTION_SELECT_ALL** selects all text, **IME_EXTEND_ACTION_CUT** cuts the selected text to the clipboard and deletes the original text, **IME_EXTEND_ACTION_COPY** copies the selected text to the clipboard (without deleting the original text), and **IME_EXTEND_ACTION_PASTE** inserts the clipboard content at the cursor position.

Relationship between enum values: The enum values are non-consecutive (**0**, **3**, **4**, **5**). **SELECT_ALL** has a value of **0**, and **CUT**, **COPY**, and **PASTE** have values of **3**–**5**. This non-consecutive design is because **CUT**, **COPY**, and **PASTE** belong to the clipboard operation group (with consecutive values), while **SELECT_ALL** is an independent operation. Select all usually serves as a preceding operation for cut or copy operations—the user selects all content before performing a cut or copy action. Cut and copy are mutually exclusive: cut removes the original text, while copy preserves it.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| IME_EXTEND_ACTION_SELECT_ALL = 0 | Selects all text content in the edit box. This operation does not involve the clipboard and only changes the text selection range. It is usually used as a preceding step for the cut or copy operation—the user selects all content before performing a cut or copy action. After execution, all text in the edit box is in the selected state, and the user can perform further operations (such as cut or copy). |
| IME_EXTEND_ACTION_CUT = 3 | Cuts the currently selected text in the edit box to the system clipboard and deletes the selected text from the edit box. This operation requires that text is already selected in the edit box before it can be executed. After the cut operation is performed, the deleted text content is saved in the clipboard and can be pasted to another location through the paste operation. Applicable to scenarios where text needs to be moved. |
| IME_EXTEND_ACTION_COPY = 4 | Copies the currently selected text in the edit box to the system clipboard, while the original text in the edit box remains unchanged. This operation requires that text is already selected in the edit box before it can be executed. After the copy operation is performed, a copy of the text is saved in the clipboard and can be pasted to another location through the paste operation. Applicable to scenarios where text needs to be duplicated. The difference from cut lies in that copy retains the original text, while cut deletes the original text. |
| IME_EXTEND_ACTION_PASTE = 5 | Pastes the text content from the system clipboard at the cursor position in the edit box. This operation requires that the system clipboard contains text content before it can be executed. After the paste operation is performed, the clipboard content is inserted at the cursor position, and the text after the original cursor position automatically shifts backward. Applicable to scenarios where clipboard text needs to be inserted into the edit box. |

### InputMethod_TextInputType

```c
enum InputMethod_TextInputType
```

**Description**

Enumerates the text input types, used to specify the input types supported by the edit box so that the system can adapt the corresponding input method keyboard. Different **TextInputType** values will trigger the input method framework to display different keyboard layouts (such as numeric keyboard, email keyboard, and URL keyboard) and set corresponding input filtering rules. This enum, serving as the **inputType** attribute of **InputMethod_TextConfig**, is set through **OH_TextConfig_SetInputType** and obtained through **OH_TextConfig_GetInputType**.

Purpose: Specifies the text input type of the edit box, affecting the input method keyboard layout and input filtering rules.

Value suggestion: Select the most appropriate **TextInputType** according to the actual input content of the edit box. Use **IME_TEXT_INPUT_TYPE_TEXT** for ordinary text, **IME_TEXT_INPUT_TYPE_MULTILINE** for multiline text, **IME_TEXT_INPUT_TYPE_NUMBER** for pure numeric input, **IME_TEXT_INPUT_TYPE_VISIBLE_PASSWORD** or **IME_TEXT_INPUT_TYPE_NEW_PASSWORD** for passwords, **IME_TEXT_INPUT_TYPE_EMAIL_ADDRESS** for email, and **IME_TEXT_INPUT_TYPE_ONE_TIME_CODE** for verification codes. Use **IME_TEXT_INPUT_TYPE_NONE** (**–1**) when the type is uncertain, and the system will use the default keyboard layout.

Relationship between enum values: Enum values start from -1, with **NONE** being **-1**, and the remaining values increment consecutively from 0 (**0**–**13**), totaling 14 enum items. **NONE** (**-1**) is a special value indicating that no input type is specified. The difference from **TEXT** (**0**) lies in that **NONE** does not trigger specific keyboard adaptation, while **TEXT** triggers the normal text keyboard. Password-related types (**VISIBLE_PASSWORD = 7**, **NUMBER_PASSWORD = 8**, **SCREEN_LOCK_PASSWORD = 9**, **NEW_PASSWORD = 11**) form a group of their own, and the system may enable secure input mode for password-type input boxes. Numeric-related types (**NUMBER = 2**, **NUMBER_PASSWORD = 8**, **NUMBER_DECIMAL = 12**) will trigger the numeric keyboard layout.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| IME_TEXT_INPUT_TYPE_NONE = -1 | The text input type is **NONE**, indicating that the edit box does not specify a particular input type. The system will use the default keyboard layout without optimizing for a specific input scenario. Applicable to scenarios that do not require special keyboard adaptation or as a placeholder value. |
| IME_TEXT_INPUT_TYPE_TEXT = 0 | Text type, indicating that the edit box accepts ordinary text input. The system will display the standard text keyboard layout, supporting letters, numbers, and symbols. Applicable to general text input scenarios (such as remarks and comments). |
| IME_TEXT_INPUT_TYPE_MULTILINE = 1 | Multiline type, indicating that the edit box supports multiline text input. The system will display a text keyboard layout that supports line breaks, where the Enter key function is a line break rather than completion. Applicable to scenarios requiring input of multiple paragraphs of text (such as memos and note editing). |
| IME_TEXT_INPUT_TYPE_NUMBER = 2 | Numeric type, indicating that the edit box accepts only numeric input. The system will display a numeric keyboard layout containing only the 0–9 number keys. Applicable to pure numeric input scenarios (such as age, quantity, and password input boxes). |
| IME_TEXT_INPUT_TYPE_PHONE = 3 | Phone number type, indicating that the edit box accepts phone number input. The system will display a phone number keyboard layout containing the 0–9 number keys and common phone number symbols (such as +, -, *, #). Applicable to phone number input scenarios. |
| IME_TEXT_INPUT_TYPE_DATETIME = 4 | Date type, indicating that the edit box accepts date and time input. The system will display a date input keyboard layout containing numbers and date-related symbols. Applicable to date and time input scenarios (such as date picker input boxes). |
| IME_TEXT_INPUT_TYPE_EMAIL_ADDRESS = 5 | Email address type, indicating that the edit box accepts email address input. The system will display an email keyboard layout, providing shortcut keys for common email address symbols such as @ and .com on the keyboard. Applicable to email address input scenarios (such as email login, email fields in registration forms). |
| IME_TEXT_INPUT_TYPE_URL = 6 | URL type, indicating that the edit box accepts URL input. The system will display a URL keyboard layout, providing shortcut keys for common URL symbols such as /, .com, and .cn on the keyboard. Applicable to URL input scenarios (such as browser address bars and link input boxes). |
| IME_TEXT_INPUT_TYPE_VISIBLE_PASSWORD = 7 | Password type, indicating that the edit box accepts password input, and the password content is visible (not hidden). The system will display a text keyboard layout, but may enable secure input mode (such as disabling screenshots and preview text). Applicable to scenarios where the entered password needs to be viewed (such as password confirmation input boxes). |
| IME_TEXT_INPUT_TYPE_NUMBER_PASSWORD = 8 | Numeric password type, indicating that the edit box accepts only numeric password input. The system will display a numeric keyboard layout and may enable secure input mode. Applicable to scenarios requiring only numeric passwords (such as PIN code input boxes and 4-digit/6-digit numeric password input boxes). |
| IME_TEXT_INPUT_TYPE_SCREEN_LOCK_PASSWORD = 9 | Screen lock password type, indicating that the edit box accepts screen lock password input. The system will display a dedicated password keyboard layout and enable the highest level of secure input mode. Applicable to device screen lock password input scenarios. |
| IME_TEXT_INPUT_TYPE_USER_NAME = 10 | Username type, indicating that the edit box accepts username input. The system will display a text keyboard layout and may provide optimizations for username input (such as autocomplete suggestions). Applicable to username input boxes in login and registration scenarios. |
| IME_TEXT_INPUT_TYPE_NEW_PASSWORD = 11 | New password type, indicating that the edit box accepts new password input (such as registration or password change scenarios). The system will display a password keyboard layout and may enable secure input mode and password strength hints. Applicable to input scenarios for creating a new password or changing a password. |
| IME_TEXT_INPUT_TYPE_NUMBER_DECIMAL = 12 | Decimal number type, indicating that the edit box accepts numeric input with a decimal point. The system will display a numeric keyboard layout and additionally provide a decimal point key. Applicable to scenarios requiring decimal input (such as amount input and numeric parameter input). |
| IME_TEXT_INPUT_TYPE_ONE_TIME_CODE = 13 | Verification code type, indicating that the edit box accepts one-time verification code input. The system will display a numeric keyboard layout and may automatically extract the verification code from SMS messages to fill in. Applicable to auto-fill scenarios such as SMS verification codes and OTP verification codes. **Since:** 20 |

### InputMethod_CommandValueType

```c
enum InputMethod_CommandValueType
```

**Description**

Enumerates private data types, which defines the data type of the value in **InputMethod_PrivateCommand** and is used to support private parameter passing between the input method app and the client. Each **PrivateCommand** instance can hold only one type of value. After obtaining the current value type through **OH_PrivateCommand_GetValueType**, call the corresponding **GetValue** function to obtain the actual value.

Purpose: Identifies the data type of value in a **PrivateCommand** instance, guiding the receiver to select the correct **GetValue** function.

Value suggestion: Before obtaining the value of a **PrivateCommand** instance, you must first obtain the type through **OH_PrivateCommand_GetValueType**, and then select the corresponding **GetValue** function according to the type: **IME_COMMAND_VALUE_TYPE_BOOL** calls **OH_PrivateCommand_GetBoolValue**, **IME_COMMAND_VALUE_TYPE_INT32** calls **OH_PrivateCommand_GetIntValue**, and **IME_COMMAND_VALUE_TYPE_STRING** calls **OH_PrivateCommand_GetStrValue**. **IME_COMMAND_VALUE_TYPE_NONE** indicates that no value is set, in which case no **GetValue** function should be called.

Relationship between enum values: Enum values increase consecutively from 0 to 3, for a total of four enum items. **NONE** (**0**) is the initial state, indicating that no value is set since **PrivateCommand** is created. The three value types—**STRING**, **BOOL**, and **INT32**—are mutually exclusive, and a single **PrivateCommand** instance can hold only one of these value types at any given time. When you set a value of one type, any previously stored value and its type are overwritten.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| IME_COMMAND_VALUE_TYPE_NONE = 0 | The private data type is **NONE**, indicating that the **PrivateCommand** instance has not set any value yet. This value is the default type state after the **PrivateCommand** is created. Calling any **GetValue** function (**GetBoolValue**/**GetIntValue**/**GetStrValue**) will return the **IME_ERR_QUERY_FAILED** error code. |
| IME_COMMAND_VALUE_TYPE_STRING = 1 | String type, indicating that the value of the **PrivateCommand** instance is string data. The corresponding setter function is **OH_PrivateCommand_SetStrValue**, and the getter function is **OH_PrivateCommand_GetStrValue**. It is applicable to passing data with string semantics such as text configuration, URLs, and JSON format parameters. |
| IME_COMMAND_VALUE_TYPE_BOOL = 2 | Boolean type, indicating that the value of the **PrivateCommand** instance is boolean data (**true** or **false**). The corresponding setter function is **OH_PrivateCommand_SetBoolValue**, and the getter function is **OH_PrivateCommand_GetBoolValue**. It is applicable to passing data with boolean semantics such as switch states and whether a feature is enabled. |
| IME_COMMAND_VALUE_TYPE_INT32 = 3 | 32-bit signed integer type, indicating that the value of the **PrivateCommand** instance is int32_t data. The corresponding setter function is **OH_PrivateCommand_SetIntValue**, and the getter function is **OH_PrivateCommand_GetIntValue**. It is applicable to passing data with integer semantics such as numeric parameters, counts, and version numbers. |

### InputMethod_ErrorCode

```c
enum InputMethod_ErrorCode
```

**Description**

Enumerates input method error codes that may occur in the input method framework, covering various error scenarios such as parameter check failure, package management exception, input method app exception, and input box client exception. You should determine the error type according to the specific error code and take corresponding error handling measures. For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

Purpose: Identifies the execution result and error type of various operations in the input method framework, for use in return value checks and error handling.

Value suggestion: After calling an input method C API, check whether the return value is **IME_ERR_OK** (**0**). If a value other than **IME_ERR_OK** is returned, handle it according to the specific error code: for **IME_ERR_NULL_POINTER**, check whether the parameter is **NULL**; for **IME_ERR_PARAMCHECK**, check the parameter type and range; for **IME_ERR_IMCLIENT** or **IME_ERR_DETACHED**, check the connection status between the input box and the input method service; for **IME_ERR_IMENGINE**, check the running status of the input method app; for **IME_ERR_QUERY_FAILED**, check the query conditions and data status.

Relationship between enum values: Enum values are divided into three groups: general error codes (**0**, **1**, and **401**), framework service error codes (from 12800001 to 12800009), and C API error codes (from 12802000 to 12802001). General error codes apply to all APIs; framework service error codes are related to system service status; C API error codes target the null pointer and query failure scenarios specific to C APIs. **IME_ERR_OK** (**0**) is the success indicator, and other values are error indicators.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| IME_ERR_OK = 0 | Success. Indicates that the operation is complete and no additional handling is required. All C APIs of the input method return this value after normal execution. You do not need to perform any error handling logic for this error code. |
| IME_ERR_UNDEFINED = 1 | Undefined error. It may be caused by an internal system exception. It is recommended that you check the system logs and contact technical support. This error code indicates that an internal exception occurred in the input method framework that cannot be classified into any other specific error code. |
| IME_ERR_PARAMCHECK = 401 | Parameter check failed. The parameter type, range, or format may be incorrect. Check whether the input parameters meet the API requirements. This error code is returned when the passed parameters do not conform to the API specification (for example, incorrect parameter type or string length exceeding the limit). |
| IME_ERR_PACKAGEMANAGER = 12800001 | Package management exception. The input method app may not be installed correctly or the package information may be abnormal. Check the input method app status and reinstall it. This error code is returned when the system package management service cannot correctly obtain the input method app information. |
| IME_ERR_IMENGINE = 12800002 | Input method app exception. The input method app may have crashed or is not running. It is recommended that you restart the input method app or switch to another input method. This error code is returned when the input method engine cannot work normally. |
| IME_ERR_IMCLIENT = 12800003 | Input box client exception. The connection between the input box and the input method service may be abnormal. Check whether the app is correctly attached to the input method service. This error code is returned when the communication between the edit box client and the input method service is abnormal. |
| IME_ERR_CONFIG_PERSIST = 12800005 | Configuration persistence failed. This error code is reported when the input method configuration fails to be saved to persistent storage. Examples include saving input method settings and switching input methods. This error code is returned when the input method framework cannot persist configuration changes. Check whether storage permissions are granted and sufficient storage space is available, or retry the operation later. |
| IME_ERR_CONTROLLER = 12800006 | Input method controller exception. The input method controller may have failed to initialize or the service may be abnormal. It is recommended that you check the system service status or restart the device. This error code is returned when the input method controller cannot work normally. |
| IME_ERR_SETTINGS = 12800007 | Input method settings exception. The input method setting parameters may be invalid or the permission may be insufficient. Check the setting parameters and permission configuration. This error code is returned when the input method setting service cannot normally process configuration changes. |
| IME_ERR_IMMS = 12800008 | Input method management service exception. The input method management service may not be started or may have terminated abnormally. It is recommended that you check the system service status or restart the input method management service (IMMS). This error code is returned when the IMMS cannot work normally. |
| IME_ERR_DETACHED = 12800009 | Input box not attached. The connection between the input box and the input method service may not be established. Call the attach interface to re-establish the connection. This error code is returned when an API that requires attachment is called while the edit box is not attached to the input method service through **OH_InputMethodController_Attach**. |
| IME_ERR_NULL_POINTER = 12802000 | Null pointer exception. The passed parameter may be a null pointer. Check whether the input parameters are correctly initialized. This error code is returned when a C API receives a null pointer parameter, and it is a parameter error type specific to the C language. You should ensure that all pointer parameters are non-**NULL** before calling the API. |
| IME_ERR_QUERY_FAILED = 12802001 | Query failed. The query condition may be invalid or the target data may not exist. Check the query parameters and data status. This error code is returned when the query condition of a **Get**-type API does not match the actual data. For example, calling **OH_PrivateCommand_GetBoolValue** holding an int32_t value triggers this error to report a type mismatch as there is no boolean value in the command. |

### InputMethod_RequestKeyboardReason

```c
enum InputMethod_RequestKeyboardReason
```

**Description**

Enumerates the reasons for requesting keyboard input. It defines the different trigger sources that initiate keyboard requests and distinguishes different keyboard trigger scenarios, allowing the input method to perform targeted adaptation. This enum acts as the **requestKeyboardReason** attribute of **InputMethod_AttachOptions** and is passed to the input method framework through **OH_InputMethodProxy_ShowTextInput**. Distinguishing trigger reasons can help the input method app optimize keyboard behavior and input experience for different interaction scenarios.

Purpose: Identifies the reason that triggers the keyboard to pop up (mouse click, touch operation, or others), for targeted optimization by the input method app.

Value suggestion: Select the corresponding **RequestKeyboardReason** according to the actual trigger scenario. Use **IME_REQUEST_REASON_MOUSE** when a user clicks the input box with a mouse, **IME_REQUEST_REASON_TOUCH** when a user touches the input box, and **IME_REQUEST_REASON_OTHER** for other trigger methods (such as API calls and focus switching). Use **IME_REQUEST_REASON_NONE** when the trigger reason is uncertain, and the input method will use the default behavior.

Relationship between enum values: The enum values are non-consecutive (**0**, **1**, **2**, **20**). **NONE**, **MOUSE**, and **TOUCH** are regular trigger sources (values **0**-**2**, consecutive), and **OTHER** is a special trigger source (value **20**). **MOUSE** and **TOUCH** respectively represent the two most common direct user interaction trigger methods, while **OTHER** covers all non-direct interaction trigger scenarios. **NONE** does not indicate any trigger reason and is usually used as the default value.

**Since**: 15

| Enum Item| Description|
| -- | -- |
| IME_REQUEST_REASON_NONE = 0 | Indicates that no specific reason triggers the keyboard request. This value is usually used as the default value, and the input method framework will use the default keyboard pop-up behavior. It is applicable to scenarios where the trigger reason does not need to be distinguished or as the initial value of **AttachOptions**. |
| IME_REQUEST_REASON_MOUSE = 1 | Indicates that the keyboard request is triggered by a mouse operation. The user clicks the input box area with the mouse to trigger the keyboard pop-up, and the input method app can optimize keyboard behavior for mouse interaction scenarios (such as providing more precise cursor positioning and a keyboard layout adapted to mouse operation habits). It is applicable to desktop devices or tablet scenarios that support mouse input. |
| IME_REQUEST_REASON_TOUCH = 2 | Indicates that the keyboard request is triggered by a touch operation. The user touches the input box area with a finger to trigger the keyboard pop-up, and the input method app can optimize keyboard behavior for touch interaction scenarios (such as providing larger key spacing and a keyboard layout adapted to touch operations). It is applicable to finger touch interaction scenarios on mobile devices. |
| IME_REQUEST_REASON_OTHER = 20 | Indicates that the keyboard request is triggered by other reasons, including but not limited to: the program actively calling the **ShowKeyboard** or **ShowTextInput** API, automatic focus switching, configuration change triggering, and other non-direct user interaction scenarios. The input method app can make special adaptations for such scenarios (such as not displaying transition animations and using a compact keyboard layout). |
