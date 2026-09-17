# @ohos.inputMethodEngine(Input Method Service)

The **inputMethodEngine** module is oriented to input method applications (including system and third-party input method applications). With the APIs of this module, input method applications are able to create soft keyboard windows, insert or delete characters, select text, and listen for physical keyboard events. <br> <br>  
> **NOTE:** <br>
> <br> &gt;The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createKeyboardDelegate](arkts-ime-inputmethodengine-createkeyboarddelegate-f.md) | Obtains a [KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md) instance for the input method. The input method can use the obtained instance to subscribe to a physical keyboard event, text selection change event, and more. |
| [getInputMethodAbility](arkts-ime-inputmethodengine-getinputmethodability-f.md) | Obtains an [InputMethodAbility](arkts-ime-inputmethodengine-inputmethodability-i.md) instance for the input method. This API can be called only by an input method. <br> <br>The input method can use the obtained instance to subscribe to a soft keyboard display/hide request event, create/ destroy an input method panel, and the like. |
| [getInputMethodEngine](arkts-ime-inputmethodengine-getinputmethodengine-f.md) | Obtains an [InputMethodEngine](arkts-ime-inputmethodengine-inputmethodengine-i.md) instance for the input method. <br> <br>The input method can use the obtained instance to subscribe to a soft keyboard display/hide request event. |
| [getKeyboardDelegate](arkts-ime-inputmethodengine-getkeyboarddelegate-f.md) | Obtains a [KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md) instance for the input method. <br> <br>The input method can use the obtained instance to subscribe to a physical keyboard event, text selection change event, and more. |

### Interfaces

| Name | Description |
| --- | --- |
| [AttachOptions](arkts-ime-inputmethodengine-attachoptions-i.md) | Defines additional options for binding an input method. |
| [EditorAttribute](arkts-ime-inputmethodengine-editorattribute-i.md) | Represents the attributes of the edit box. |
| [EnhancedPanelRect](arkts-ime-inputmethodengine-enhancedpanelrect-i.md) | Indicates the size of the enhanced input method panel, including the custom avoid area and touch area. |
| [ImmersiveEffect](arkts-ime-inputmethodengine-immersiveeffect-i.md) | Describes the immersive effect. |
| [InputClient](arkts-ime-inputmethodengine-inputclient-i.md) | You must first use [on('inputStart')](arkts-ime-inputmethodengine-inputmethodability-i.md#oninputstart) to obtain a **InputClient** instance, and then use this instance to call the following APIs. |
| [InputMethodAbility](arkts-ime-inputmethodengine-inputmethodability-i.md) | In the following API examples, you must first use [getInputMethodAbility](arkts-ime-inputmethodengine-getinputmethodability-f.md) to obtain an **InputMethodAbility** instance, and then call the APIs using the obtained instance. |
| [InputMethodEngine](arkts-ime-inputmethodengine-inputmethodengine-i.md) | In the following API examples, you must first use [getInputMethodEngine](arkts-ime-inputmethodengine-getinputmethodengine-f.md) to obtain an **InputMethodEngine** instance, and then call the APIs using the obtained instance. |
| [KeyboardArea](arkts-ime-inputmethodengine-keyboardarea-i.md) | Represents the keyboard area on the panel. |
| [KeyboardController](arkts-ime-inputmethodengine-keyboardcontroller-i.md) | You must first use [on('inputStart')](arkts-ime-inputmethodengine-inputmethodability-i.md#oninputstart) to obtain a **KeyboardController** instance, and then use this instance to call the following APIs. |
| [KeyboardDelegate](arkts-ime-inputmethodengine-keyboarddelegate-i.md) | In the following API examples, you must first use [getKeyboardDelegate](arkts-ime-inputmethodengine-getkeyboarddelegate-f.md) to obtain a **KeyboardDelegate** instance, and then call the APIs using the obtained instance. |
| [KeyEvent](arkts-ime-inputmethodengine-keyevent-i.md) | Represents the attributes of a key. |
| [MessageHandler](arkts-ime-inputmethodengine-messagehandler-i.md) | Represents a custom communication object.<br> <br> |
| [Movement](arkts-ime-inputmethodengine-movement-i.md) | Describes the direction in which the cursor moves when the text is selected. |
| [Panel](arkts-ime-inputmethodengine-panel-i.md) | You need to use [createPanel](arkts-ime-inputmethodengine-inputmethodability-i.md#createpanel) to obtain the panel instance and then call the following APIs through the instance. |
| [PanelInfo](arkts-ime-inputmethodengine-panelinfo-i.md) | Describes the attributes of the input method panel. |
| [PanelRect](arkts-ime-inputmethodengine-panelrect-i.md) | Represents the size of the input method panel. |
| [Range](arkts-ime-inputmethodengine-range-i.md) | Describes the range of the selected text. |
| [SystemPanelInsets](arkts-ime-inputmethodengine-systempanelinsets-i.md) | Defines the offset area between the input method soft keyboard and the system panel. |
| [TextInputClient](arkts-ime-inputmethodengine-textinputclient-i.md) | In the following API examples, you must first use [on('inputStart')](arkts-ime-inputmethodengine-inputmethodengine-i.md#oninputstart) to obtain a **TextInputClient** instance, and then call the APIs using the obtained instance. |
| [WindowInfo](arkts-ime-inputmethodengine-windowinfo-i.md) | Represents window information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [EditorAttribute](arkts-ime-inputmethodengine-editorattribute-i-sys.md) | Represents the attributes of the edit box. |
| [ImmersiveEffect](arkts-ime-inputmethodengine-immersiveeffect-i-sys.md) | Describes the immersive effect. |
| [Panel](arkts-ime-inputmethodengine-panel-i-sys.md) | You need to use [createPanel](arkts-ime-inputmethodengine-inputmethodability-i.md#createpanel) to obtain the panel instance and then call the following APIs through the instance. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [CapitalizeMode](arkts-ime-inputmethodengine-capitalizemode-e.md) | Enumerates the modes of capitalizing the first letter of a text.<br> <br> |
| [Direction](arkts-ime-inputmethodengine-direction-e.md) | Enumerates the directions of cursor movement of the input method. |
| [ExtendAction](arkts-ime-inputmethodengine-extendaction-e.md) | Describes the type of the extended edit action on the text box. |
| [GradientMode](arkts-ime-inputmethodengine-gradientmode-e.md) | Enumerates the gradient modes of the input method.<br> <br> |
| [ImmersiveMode](arkts-ime-inputmethodengine-immersivemode-e.md) | Enumerates the immersive modes of the input method.<br> <br> |
| [PanelFlag](arkts-ime-inputmethodengine-panelflag-e.md) | Enumerates the state types of the input method panel.<br> <br> |
| [PanelType](arkts-ime-inputmethodengine-paneltype-e.md) | Enumerates the types of the input method panel.<br> <br> |
| [RequestKeyboardReason](arkts-ime-inputmethodengine-requestkeyboardreason-e.md) | Enumerates the reasons for requesting keyboard input.<br> <br> |
| [SecurityMode](arkts-ime-inputmethodengine-securitymode-e.md) | Describes the security mode. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [FluidLightMode](arkts-ime-inputmethodengine-fluidlightmode-e-sys.md) | Enumerates the fluid light modes of the input method.<br> <br> |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [CommandDataType](arkts-ime-inputmethodengine-commanddatatype-t.md) | Defines the private data type, which varies depending on its function. |
| [SizeChangeCallback](arkts-ime-inputmethodengine-sizechangecallback-t.md) | Callback triggered when the size of the input method panel changes. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [SizeUpdateCallback](arkts-ime-inputmethodengine-sizeupdatecallback-t-sys.md) | Callback triggered when the size of the input method panel changes. |
<!--DelEnd-->

### Constants

| Name | Description |
| --- | --- |
| [CURSOR_DOWN](arkts-ime-inputmethodengine-con.md#cursor_down) | The caret moves downward. |
| [CURSOR_LEFT](arkts-ime-inputmethodengine-con.md#cursor_left) | The caret moves leftward. |
| [CURSOR_RIGHT](arkts-ime-inputmethodengine-con.md#cursor_right) | The caret moves rightward. |
| [CURSOR_UP](arkts-ime-inputmethodengine-con.md#cursor_up) | The caret moves upward. |
| [DISPLAY_MODE_FULL](arkts-ime-inputmethodengine-con.md#display_mode_full) | The edit box is displayed in full screen. |
| [DISPLAY_MODE_PART](arkts-ime-inputmethodengine-con.md#display_mode_part) | The edit box is displayed in half-screen mode. |
| [ENTER_KEY_TYPE_DONE](arkts-ime-inputmethodengine-con.md#enter_key_type_done) | Key that indicates that a task or input is complete. |
| [ENTER_KEY_TYPE_GO](arkts-ime-inputmethodengine-con.md#enter_key_type_go) | Key that executes a command or navigates to a specific location. |
| [ENTER_KEY_TYPE_NEWLINE](arkts-ime-inputmethodengine-con.md#enter_key_type_newline) | Key that inserts a new line. |
| [ENTER_KEY_TYPE_NEXT](arkts-ime-inputmethodengine-con.md#enter_key_type_next) | Key that moves the focus to the next item in a sequence. |
| [ENTER_KEY_TYPE_PREVIOUS](arkts-ime-inputmethodengine-con.md#enter_key_type_previous) | Key that moves the focus to the previous item in a sequence. |
| [ENTER_KEY_TYPE_SEARCH](arkts-ime-inputmethodengine-con.md#enter_key_type_search) | Key that initiates a search operation. |
| [ENTER_KEY_TYPE_SEND](arkts-ime-inputmethodengine-con.md#enter_key_type_send) | Key that sends the text to its target. |
| [ENTER_KEY_TYPE_UNSPECIFIED](arkts-ime-inputmethodengine-con.md#enter_key_type_unspecified) | No function is specified for the key. |
| [FLAG_SELECTING](arkts-ime-inputmethodengine-con.md#flag_selecting) | The edit box is being selected. |
| [FLAG_SINGLE_LINE](arkts-ime-inputmethodengine-con.md#flag_single_line) | The edit box allows only single-line input. |
| [OPTION_ASCII](arkts-ime-inputmethodengine-con.md#option_ascii) | ASCII values are allowed. |
| [OPTION_AUTO_CAP_CHARACTERS](arkts-ime-inputmethodengine-con.md#option_auto_cap_characters) | Characters are allowed. |
| [OPTION_AUTO_CAP_SENTENCES](arkts-ime-inputmethodengine-con.md#option_auto_cap_sentences) | Sentences are allowed. |
| [OPTION_AUTO_WORDS](arkts-ime-inputmethodengine-con.md#option_auto_words) | Words are allowed. |
| [OPTION_MULTI_LINE](arkts-ime-inputmethodengine-con.md#option_multi_line) | Multiple lines are allowed. |
| [OPTION_NO_FULLSCREEN](arkts-ime-inputmethodengine-con.md#option_no_fullscreen) | Half-screen style. |
| [OPTION_NONE](arkts-ime-inputmethodengine-con.md#option_none) | No input attribute is specified. |
| [PATTERN_DATETIME](arkts-ime-inputmethodengine-con.md#pattern_datetime) | Date edit box. |
| [PATTERN_EMAIL](arkts-ime-inputmethodengine-con.md#pattern_email) | Email edit box. |
| [PATTERN_NEW_PASSWORD](arkts-ime-inputmethodengine-con.md#pattern_new_password) | New password edit box. |
| [PATTERN_NULL](arkts-ime-inputmethodengine-con.md#pattern_null) | Any type of edit box. |
| [PATTERN_NUMBER](arkts-ime-inputmethodengine-con.md#pattern_number) | Number edit box. |
| [PATTERN_NUMBER_DECIMAL](arkts-ime-inputmethodengine-con.md#pattern_number_decimal) | Edit box for numbers with decimal points. |
| [PATTERN_ONE_TIME_CODE](arkts-ime-inputmethodengine-con.md#pattern_one_time_code) | Verification code edit box. |
| [PATTERN_PASSWORD](arkts-ime-inputmethodengine-con.md#pattern_password) | Password edit box. |
| [PATTERN_PASSWORD_NUMBER](arkts-ime-inputmethodengine-con.md#pattern_password_number) | Numeric password edit box. |
| [PATTERN_PASSWORD_SCREEN_LOCK](arkts-ime-inputmethodengine-con.md#pattern_password_screen_lock) | Screen lock password edit box. |
| [PATTERN_PHONE](arkts-ime-inputmethodengine-con.md#pattern_phone) | Phone number edit box. |
| [PATTERN_TEXT](arkts-ime-inputmethodengine-con.md#pattern_text) | Text edit box. |
| [PATTERN_URI](arkts-ime-inputmethodengine-con.md#pattern_uri) | URI edit box. |
| [PATTERN_USER_NAME](arkts-ime-inputmethodengine-con.md#pattern_user_name) | User name edit box. |
| [WINDOW_TYPE_INPUT_METHOD_FLOAT](arkts-ime-inputmethodengine-con.md#window_type_input_method_float) | The input method is displayed in a floating window. |
