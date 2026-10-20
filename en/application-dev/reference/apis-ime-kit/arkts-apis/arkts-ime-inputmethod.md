# @ohos.inputMethod(Input Method Framework)

**Since:** 6

<!--Device-unnamed-declare namespace inputMethod--><!--Device-unnamed-declare namespace inputMethod-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Constant

<br><br>Provides the constants.<br>

 | Name | Type | Value | Description |  
 | -------- | -------- | -------- | -------- |  
 | MAX_TYPE_NUM<sup>8+</sup> | number | 128 | Maximum number of supported input methods. |

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getController](arkts-ime-inputmethod-getcontroller-f.md#getcontroller) | Obtains an [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) instance. <br> <br>Meaning/Function: Obtains the input method client controller instance of the current application, which is used for subsequent interaction with the input method (such as attaching to the input method, showing/hiding the keyboard, and synchronizing the edit box status). <br> <br>Usage scenarios: When a foreground application (such as a memo or chat application) needs to control the showing/ hiding of the input method, attach to or detach from the input method, or synchronize edit box information, it must first obtain the **InputMethodController** instance through this API. <br> <br>Use effect: Returns an **InputMethodController** instance. Subsequently, the instance can be used to call a series of APIs such as **attach**, **showTextInput**, **hideTextInput**, and **detach** to interact with the input method. |
| [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md#getcurrentinputmethod) | Obtains the current input method. This API returns the result synchronously. <br> <br>Meaning/Function: Obtains the property information of the input method currently in use. <br> <br>Usage scenarios: Used when an application needs to know which input method is currently active (for example, to determine the input method name or obtain the input method ID for subsequent switching operations). <br> <br>Use effect: Returns the **InputMethodProperty** object of the current input method. |
| [getCurrentInputMethodSubtype](arkts-ime-inputmethod-getcurrentinputmethodsubtype-f.md#getcurrentinputmethodsubtype) | Obtains the current input method subtype. |
| [getDefaultInputMethod](arkts-ime-inputmethod-getdefaultinputmethod-f.md#getdefaultinputmethod) | Obtains the default input method. |
| [getSetting](arkts-ime-inputmethod-getsetting-f.md#getsetting) | Obtains an [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) instance. <br> <br>Meaning/Function: Obtains the input method setting instance, which is used for configuration management operations such as querying the input method list, subscribing to input method change events, and querying panel visibility. <br> <br>Usage scenarios: When an application needs to query the installed/activated input method list, subscribe to input method switching events, or display the input method selection dialog, it must first obtain the **InputMethodSetting** instance through this API. <br> <br>Use effect: Returns an **InputMethodSetting** instance. Subsequently, the instance can be used to call APIs such as **getInputMethods**, **listInputMethodSubtype**, and **on('imeChange')**. |
| [getSystemInputMethodConfigAbility](arkts-ime-inputmethod-getsysteminputmethodconfigability-f.md#getsysteminputmethodconfigability) | Obtains the information about the system input method configuration ability. |
| [offAttachmentDidFail](arkts-ime-inputmethod-offattachmentdidfail-f.md#offattachmentdidfail) | Unsubscribes from attachment failure events. This API uses an asynchronous callback to return the result. |
| [onAttachmentDidFail](arkts-ime-inputmethod-onattachmentdidfail-f.md#onattachmentdidfail) | Subscribes to attachment failure events. This API uses an asynchronous callback to return the result. |
| [setSimpleKeyboardEnabled](arkts-ime-inputmethod-setsimplekeyboardenabled-f.md#setsimplekeyboardenabled) | Enables or disables the simple keyboard. |
| [switchCurrentInputMethodAndSubtype](arkts-ime-inputmethod-switchcurrentinputmethodandsubtype-f.md#switchcurrentinputmethodandsubtype) | Switches to a specified subtype of a specified input method. This API uses an asynchronous callback to return the result. |
| [switchCurrentInputMethodAndSubtype](arkts-ime-inputmethod-switchcurrentinputmethodandsubtype-f.md#switchcurrentinputmethodandsubtype) | Switches to a specified subtype of a specified input method. This API uses a promise to return the result. |
| [switchCurrentInputMethodSubtype](arkts-ime-inputmethod-switchcurrentinputmethodsubtype-f.md#switchcurrentinputmethodsubtype) | Switches to another subtype of this input method. This API uses an asynchronous callback to return the result. |
| [switchCurrentInputMethodSubtype](arkts-ime-inputmethod-switchcurrentinputmethodsubtype-f.md#switchcurrentinputmethodsubtype) | Switches to another subtype of this input method. This API uses a promise to return the result. |
| [switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md#switchinputmethod) | Switches the input method. This API uses an asynchronous callback to return the result. <br> <br>Meaning/Function: Switches the current input method to the specified target input method. <br> <br>Usage scenarios: Used when the current input method application needs to switch to another input method (for example, when the user selects a new input method in the input method settings). <br> <br>Use effect: On success, the system switches the current input method to the target input method, and the target input method becomes the new current input method; on failure, the current input method remains unchanged. |
| [switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md#switchinputmethod) | Switches the input method. This API uses a promise to return the result. <br> <br>Meaning/Function: Switches the current input method to the specified target input method. <br> <br>Usage scenarios: Used when the current input method application needs to switch to another input method. <br> <br>Use effect: On success, the system switches the current input method to the target input method; on failure, the current input method remains unchanged. |
| [getInputMethodController](arkts-ime-inputmethod-getinputmethodcontroller-f.md#getinputmethodcontroller) | Obtains an [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) instance. |
| [getInputMethodSetting](arkts-ime-inputmethod-getinputmethodsetting-f.md#getinputmethodsetting) | Obtains an [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) instance. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f-sys.md#getcurrentinputmethod) | Obtains the current input method of a specified user. |
| [getCurrentInputMethodSubtype](arkts-ime-inputmethod-getcurrentinputmethodsubtype-f-sys.md#getcurrentinputmethodsubtype) | Obtains the current input method subtype of a specified user. |
| [getDefaultInputMethod](arkts-ime-inputmethod-getdefaultinputmethod-f-sys.md#getdefaultinputmethod) | Obtains the default input method of a specified user. |
| [getSystemInputMethodConfigAbility](arkts-ime-inputmethod-getsysteminputmethodconfigability-f-sys.md#getsysteminputmethodconfigability) | Obtains ability information for the system input method configuration page of a specified user. Used to launch the system input method configuration page. |
| [switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f-sys.md#switchinputmethod) | Switches the input method. This API uses a promise to return the result. |
| [switchInputMethodWithUserId](arkts-ime-inputmethod-switchinputmethodwithuserid-f-sys.md#switchinputmethodwithuserid) | Switches the input method. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AttachOptions](arkts-ime-inputmethod-attachoptions-i.md) | Defines additional options for binding an input method. |
| [CursorInfo](arkts-ime-inputmethod-cursorinfo-i.md) | Cursor information. |
| [FunctionKey](arkts-ime-inputmethod-functionkey-i.md) | Describes the type of the input method function key. |
| [InputAttribute](arkts-ime-inputmethod-inputattribute-i.md) | Describes the attributes of the edit box, including the text input type and Enter key function type. |
| [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) | In the following API examples, you must first use [getController](arkts-ime-inputmethod-getcontroller-f.md) to obtain an **InputMethodController** instance, and then call the APIs using the obtained instance. <br> <br>**InputMethodController** is the input method client controller, which provides foreground applications with core capabilities for interacting with the input method. After obtaining an instance through `inputMethod.getController()`, you can perform the following operations: <br> <br>- Attachment management: Use [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach) to establish attachment to the input method, and use [detach](arkts-ime-inputmethod-inputmethodcontroller-i.md#detach) to perform detachment. **attach** and **detach** must be used in pairs. <br>- Keyboard control: Use [showTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#showtextinput) to start the soft keyboard and enter the editing state, and use [hideTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#hidetextinput) to hide the soft keyboard and exit the editing state. **showTextInput** and **hideTextInput** must be used in pairs. <br>- Edit box state synchronization: Use APIs such as [updateCursor](arkts-ime-inputmethod-inputmethodcontroller-i.md#updatecursor), <br> <br>[changeSelection](arkts-ime-inputmethod-inputmethodcontroller-i.md#changeselection), and [updateAttribute](arkts-ime-inputmethod-inputmethodcontroller-i.md#updateattribute) to synchronize edit box state information such as the cursor, selection, and attributes with the input method. <br>- Event subscription: Use APIs such as **on('insertText')** and **on('deleteLeft')** to subscribe to text operation events sent by the input method application. <br> <br>Typical call sequence: `getController()` → `attach()` → `showTextInput()`/`hideTextInput()` → `detach()` <br> <br> |
| [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | Describes the input method application properties. |
| [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) | **InputMethodSetting** provides input method configuration and query capabilities, and offers the following features for foreground applications: <br> <br>- Input method change subscription: subscribe to input method and subtype change events through [on('imeChange')](arkts-ime-inputmethod-inputmethodsetting-i.md#onimechange), and receive a notification when the user switches the input method. <br>- Input method list query: query the list of enabled/disabled input methods through [getInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getinputmethods), query the list of all installed input methods through [getAllInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getallinputmethods), and query the subtype list of a specified input method through [listInputMethodSubtype](arkts-ime-inputmethod-inputmethodsetting-i.md#listinputmethodsubtype). <br>- Panel visibility query: query whether the input method panel is displayed through **isPanelShown**. <br>- Input method selection dialog: display the input method selection dialog through **showOptionalInputMethods** (deprecated; **InputMethodListDialog** is recommended). <br> <br>It must be used after you obtain the **InputMethodSetting** instance through [getSetting](arkts-ime-inputmethod-getsetting-f.md). <br> <br>For the following APIs, you must first use [getSetting](arkts-ime-inputmethod-getsetting-f.md) to obtain an **InputMethodSetting** instance, and then call the APIs using the obtained instance. |
| [InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i.md) | Window information of the input method soft keyboard (system API extended properties). |
| [MessageHandler](arkts-ime-inputmethod-messagehandler-i.md) | Represents a custom communication object. <br> <br> |
| [Movement](arkts-ime-inputmethod-movement-i.md) | Describes the direction in which the cursor moves when the text is selected. |
| [Range](arkts-ime-inputmethod-range-i.md) | Describes the range of the selected text. |
| [TextConfig](arkts-ime-inputmethod-textconfig-i.md) | Describes the configuration of the edit box. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i-sys.md) | In the following API examples, you must first use [getController](arkts-ime-inputmethod-getcontroller-f.md) to obtain an **InputMethodController** instance, and then call the APIs using the obtained instance. <br> <br>**InputMethodController** is the input method client controller, which provides foreground applications with core capabilities for interacting with the input method. After obtaining an instance through `inputMethod.getController()`, you can perform the following operations: <br> <br>- Attachment management: Use [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach) to establish attachment to the input method, and use [detach](arkts-ime-inputmethod-inputmethodcontroller-i.md#detach) to perform detachment. **attach** and **detach** must be used in pairs. <br>- Keyboard control: Use [showTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#showtextinput) to start the soft keyboard and enter the editing state, and use [hideTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#hidetextinput) to hide the soft keyboard and exit the editing state. **showTextInput** and **hideTextInput** must be used in pairs. <br>- Edit box state synchronization: Use APIs such as [updateCursor](arkts-ime-inputmethod-inputmethodcontroller-i.md#updatecursor), <br> <br>[changeSelection](arkts-ime-inputmethod-inputmethodcontroller-i.md#changeselection), and [updateAttribute](arkts-ime-inputmethod-inputmethodcontroller-i.md#updateattribute) to synchronize edit box state information such as the cursor, selection, and attributes with the input method. <br>- Event subscription: Use APIs such as **on('insertText')** and **on('deleteLeft')** to subscribe to text operation events sent by the input method application. <br> <br>Typical call sequence: `getController()` → `attach()` → `showTextInput()`/`hideTextInput()` → `detach()` <br> <br> |
| [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i-sys.md) | **InputMethodSetting** provides input method configuration and query capabilities, and offers the following features for foreground applications: <br> <br>- Input method change subscription: subscribe to input method and subtype change events through [on('imeChange')](arkts-ime-inputmethod-inputmethodsetting-i.md#onimechange), and receive a notification when the user switches the input method. <br>- Input method list query: query the list of enabled/disabled input methods through [getInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getinputmethods), query the list of all installed input methods through [getAllInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getallinputmethods), and query the subtype list of a specified input method through [listInputMethodSubtype](arkts-ime-inputmethod-inputmethodsetting-i.md#listinputmethodsubtype). <br>- Panel visibility query: query whether the input method panel is displayed through **isPanelShown**. <br>- Input method selection dialog: display the input method selection dialog through **showOptionalInputMethods** (deprecated; **InputMethodListDialog** is recommended). <br> <br>It must be used after you obtain the **InputMethodSetting** instance through [getSetting](arkts-ime-inputmethod-getsetting-f.md). <br> <br>For the following APIs, you must first use [getSetting](arkts-ime-inputmethod-getsetting-f.md) to obtain an **InputMethodSetting** instance, and then call the APIs using the obtained instance. |
| [InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i-sys.md) | Window information of the input method soft keyboard (system API extended properties). |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [SetPreviewTextCallback](arkts-ime-inputmethod-setpreviewtextcallback-t.md) | Callback triggered when the input method framework needs to display the text preview. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [ImeChangeWithUserIdCallback](arkts-ime-inputmethod-imechangewithuseridcallback-t-sys.md) | Callback for input method change events, carrying the user ID where the input method change occurs. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AttachFailureReason](arkts-ime-inputmethod-attachfailurereason-e.md) | Enumerates the reasons for attachment failure. |
| [CapitalizeMode](arkts-ime-inputmethod-capitalizemode-e.md) | Enumerates the modes of capitalizing the first letter of a text. <br> |
| [Direction](arkts-ime-inputmethod-direction-e.md) | Enumerates the directions of cursor movement of the input method. |
| [EnabledState](arkts-ime-inputmethod-enabledstate-e.md) | Indicates whether the input method is enabled. |
| [EnterKeyType](arkts-ime-inputmethod-enterkeytype-e.md) | Enumerates the function types represented by the Enter key of the input method. |
| [ExtendAction](arkts-ime-inputmethod-extendaction-e.md) | Enumerates the types of extended edit actions on the edit box. |
| [KeyboardStatus](arkts-ime-inputmethod-keyboardstatus-e.md) | Enumerates the soft keyboard states of the input method. |
| [RequestKeyboardReason](arkts-ime-inputmethod-requestkeyboardreason-e.md) | Enumerates the reasons for requesting the keyboard. |
| [TextInputType](arkts-ime-inputmethod-textinputtype-e.md) | Enumerates the text input types. |

### Constants

| Name | Description |
| --- | --- |
| [MAX_TYPE_NUM](arkts-ime-inputmethod-con.md#max_type_num) | Keyboard max number. Max value is 128. |
