# @ohos.inputMethod(Input Method Framework)

**Since:** 6

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Constant

<br><br>Provides the constants.<br>

 | Name| Type| Value| Description|  
 | -------- | -------- | -------- | -------- |  
| MAX_TYPE_NUM&lt;sup&gt;8+&lt;/sup&gt; | number | 128 | Maximum number of supported input methods.|

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getController](arkts-ime-inputmethod-getcontroller-f.md) | Obtains an [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) instance. |
| [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md) | Obtains the current input method. This API returns the result synchronously. |
| [getCurrentInputMethodSubtype](arkts-ime-inputmethod-getcurrentinputmethodsubtype-f.md) | Obtains the current input method subtype. |
| [getDefaultInputMethod](arkts-ime-inputmethod-getdefaultinputmethod-f.md) | Obtains the default input method. |
| [getInputMethodController](arkts-ime-inputmethod-getinputmethodcontroller-f.md) | Obtains an [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) instance. |
| [getInputMethodSetting](arkts-ime-inputmethod-getinputmethodsetting-f.md) | Obtains an [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) instance. |
| [getSetting](arkts-ime-inputmethod-getsetting-f.md) | Obtains an [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) instance. |
| [getSystemInputMethodConfigAbility](arkts-ime-inputmethod-getsysteminputmethodconfigability-f.md) | Obtains the information about the input method configuration page ability. |
| [offAttachmentDidFail](arkts-ime-inputmethod-offattachmentdidfail-f.md) | Unsubscribes from attachment failure events. This API uses an asynchronous callback to return the result. |
| [onAttachmentDidFail](arkts-ime-inputmethod-onattachmentdidfail-f.md) | Subscribes to attachment failure events. This API uses an asynchronous callback to return the result. |
| [setSimpleKeyboardEnabled](arkts-ime-inputmethod-setsimplekeyboardenabled-f.md) | Enables or disables the simple keyboard. |
| [switchCurrentInputMethodAndSubtype](arkts-ime-inputmethod-switchcurrentinputmethodandsubtype-f.md) | Switches to a specified subtype of a specified input method. This API uses an asynchronous callback to return the result.<br> <br> |
| [switchCurrentInputMethodAndSubtype](arkts-ime-inputmethod-switchcurrentinputmethodandsubtype-f.md) | Switches to a specified subtype of a specified input method. This API uses a promise to return the result.<br> <br> |
| [switchCurrentInputMethodSubtype](arkts-ime-inputmethod-switchcurrentinputmethodsubtype-f.md) | Switches to another subtype of this input method. This API uses an asynchronous callback to return the result.<br> <br> |
| [switchCurrentInputMethodSubtype](arkts-ime-inputmethod-switchcurrentinputmethodsubtype-f.md) | Switches to another subtype of this input method. This API uses a promise to return the result.<br> <br> |
| [switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md) | Switches to another input method. This API uses an asynchronous callback to return the result.<br> <br> |
| [switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md) | Switches to another input method. This API uses a promise to return the result.<br> <br> |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f-sys.md) | Get the current input method of a specified user. |
| [getCurrentInputMethodSubtype](arkts-ime-inputmethod-getcurrentinputmethodsubtype-f-sys.md) | Get the current input method subtype of a specified user. |
| [getDefaultInputMethod](arkts-ime-inputmethod-getdefaultinputmethod-f-sys.md) | Get the default input method of a specified user. |
| [getSystemInputMethodConfigAbility](arkts-ime-inputmethod-getsysteminputmethodconfigability-f-sys.md) | Get the system input method config ability of a specified user. |
| [switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f-sys.md) | Switches to another input method. This API uses a promise to return the result. |
| [switchInputMethodWithUserId](arkts-ime-inputmethod-switchinputmethodwithuserid-f-sys.md) | Switch input method and subtype of a specified user. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AttachOptions](arkts-ime-inputmethod-attachoptions-i.md) | Defines additional options for binding an input method. |
| [CursorInfo](arkts-ime-inputmethod-cursorinfo-i.md) | Represents the cursor information. |
| [FunctionKey](arkts-ime-inputmethod-functionkey-i.md) | Describes the type of the input method function key. |
| [InputAttribute](arkts-ime-inputmethod-inputattribute-i.md) | Describes the attributes of the edit box, including the text input type and Enter key function type. |
| [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) | In the following API examples, you must first use [getController](arkts-ime-inputmethod-getcontroller-f.md) to obtain an **InputMethodController** instance, and then call the APIs using the obtained instance. |
| [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | Describes the input method application attributes. |
| [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) | In the following API examples, you must first use [getSetting](arkts-ime-inputmethod-getsetting-f.md) to obtain an **InputMethodSetting** instance, and then call the APIs using the obtained instance. |
| [InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i.md) | Describes the window information of the input method keyboard. |
| [MessageHandler](arkts-ime-inputmethod-messagehandler-i.md) | Represents a custom communication object.<br> <br> |
| [Movement](arkts-ime-inputmethod-movement-i.md) | Describes the direction in which the cursor moves when the text is selected. |
| [Range](arkts-ime-inputmethod-range-i.md) | Describes the range of the selected text. |
| [TextConfig](arkts-ime-inputmethod-textconfig-i.md) | Describes the configuration of the edit box. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i-sys.md) | In the following API examples, you must first use [getController](arkts-ime-inputmethod-getcontroller-f.md) to obtain an **InputMethodController** instance, and then call the APIs using the obtained instance. |
| [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i-sys.md) | In the following API examples, you must first use [getSetting](arkts-ime-inputmethod-getsetting-f.md) to obtain an **InputMethodSetting** instance, and then call the APIs using the obtained instance. |
| [InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i-sys.md) | Describes the window information of the input method keyboard. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AttachFailureReason](arkts-ime-inputmethod-attachfailurereason-e.md) | Enumerates the reasons for attachment failure. |
| [CapitalizeMode](arkts-ime-inputmethod-capitalizemode-e.md) | Enumerates the modes of capitalizing the first letter of a text.<br> |
| [Direction](arkts-ime-inputmethod-direction-e.md) | Enumerates the directions of cursor movement of the input method. |
| [EnabledState](arkts-ime-inputmethod-enabledstate-e.md) | Indicates whether the input method is enabled. |
| [EnterKeyType](arkts-ime-inputmethod-enterkeytype-e.md) | Enumerates the function types represented by the Enter key of the input method. |
| [ExtendAction](arkts-ime-inputmethod-extendaction-e.md) | Describes the type of the extended edit action on the text box. |
| [KeyboardStatus](arkts-ime-inputmethod-keyboardstatus-e.md) | Enumerates the soft keyboard states of the input method. |
| [RequestKeyboardReason](arkts-ime-inputmethod-requestkeyboardreason-e.md) | Enumerates the reasons for requesting the keyboard. |
| [TextInputType](arkts-ime-inputmethod-textinputtype-e.md) | Enumerates the text input types. |

### Types

| Name | Description |
| --- | --- |
| [SetPreviewTextCallback](arkts-ime-inputmethod-setpreviewtextcallback-t.md) | Callback triggered when the input method framework needs to display the text preview. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [ImeChangeWithUserIdCallback](arkts-ime-inputmethod-imechangewithuseridcallback-t-sys.md) | The callback of the inputmethod change event which carries the user ID whose inputmethod is changed. |
<!--DelEnd-->

### Constants

| Name | Description |
| --- | --- |
| [MAX_TYPE_NUM](arkts-ime-inputmethod-con.md#max_type_num) | Keyboard max number. Max value is 128. |
