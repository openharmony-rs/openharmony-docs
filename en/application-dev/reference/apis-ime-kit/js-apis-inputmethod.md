# @ohos.inputMethod (Input Method Framework)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=87ecd313da7eaf9820ea21ed983e70c5f013ee1a translatedAt=2026-09-02T11:49:01.282Z pushedAt=2026-09-09T10:21:57.293Z -->

The **@ohos.inputMethod** module is the input method client module for common foreground applications (such as Notes, Messaging, and Settings). It provides input method control and management capabilities.

This module is the client interface of the input method framework. It provides edit box applications with the ability to interact with the input method service, including input method attachment/detachment, soft keyboard showing/hiding, input method switching, input method list query, edit box attribute and cursor update, text selection and operation event listening, and custom message communication.

This module provides two core capability sets: (1) Through `InputMethodController`, it enables attachment, interaction, and event listening between edit box applications and the input method. After an edit box application attaches to the input method, it can control the showing and hiding of the keyboard, update the cursor and edit attributes, listen to text operation events sent by the input method (insert/delete/select text, move cursor, send function keys and extended actions, etc.), and communicate bidirectionally with the input method application through a custom message channel. (2) Through `InputMethodSetting`, it implements input method management, including obtaining the input method list, querying the current input method and subtype, subscribing to input method switching events, switching input methods and subtypes, and querying the panel display status.

Use this module when developing applications with text edit boxes (which need to interact with the input method) or system applications (which need to manage input methods). Typical scenarios include: attaching to the input method and showing the keyboard when an edit box in the application gains focus, detaching from the input method and hiding the keyboard when the edit box loses focus, and switching and configuring input methods in the system Settings application.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

This module is the client control module in IME Kit. It works together with other modules in IME Kit:
- **@ohos.inputMethodEngine**: A server-side module for input method applications. It provides capabilities such as soft keyboard window creation, text insertion/deletion, and physical key listening. Requests sent by the **@ohos.inputMethod** module, such as showing the keyboard and switching input methods, are ultimately responded to and processed by the input method application on the **@ohos.inputMethodEngine** side.
- **@ohos.inputMethodList**: Provides the display and management capabilities of the input method list dialog.
- **@ohos.inputMethod.Panel**: Defines the input method panel type and status information, used to query panel visibility and more information.

The typical call sequence for a client application (such as Notes or Settings) to interact with the input method is as follows:
1. Obtain the client controller instance `InputMethodController` through `inputMethod.getController()`.
2. Attach to the input method through `InputMethodController.attach()` (for self-drawn control scenarios), or rely on the system native edit box to attach automatically.
3. Bring up the soft keyboard through `InputMethodController.showTextInput()` to enter the text editing state.
4. During editing, synchronize the edit box state to the input method through APIs such as `updateCursor`, `changeSelection`, and `updateAttribute`.
5. Hide the soft keyboard through `InputMethodController.hideTextInput()` to exit the editing state.
6. Detach from the input method through `InputMethodController.detach()`.

Pairing constraints:
- `attach` and `detach` must be used in pairs. Exiting directly without calling `detach` may cause resource leaks.
- `showTextInput` and `hideTextInput` must be used in pairs to avoid inconsistent input method states.

The core open capabilities of this module are implemented by the following key interfaces:

| Interface | Description |
|---|---|
| InputMethodController | The input method controller, which is the core object for interaction between the edit box application and the input method. It provides capabilities such as attaching to or detaching from the input method (**attach**/**detach**), showing/hiding the keyboard (**showTextInput**/**hideTextInput**), updating the cursor and edit attributes (**updateCursor**/**updateAttribute**/**changeSelection**), listening for input method operation events (**insertText**/**deleteLeft**/**deleteRight**/**selectByRange**/**selectByMovement**/**moveCursor**/**sendFunctionKey**/**sendKeyboardStatus**/**handleExtendAction**/**setPreviewText**/**finishTextPreview**), custom message communication (**sendMessage**/**recvMessage**), and stopping the input session. Obtain an instance through `getController()`. |
| InputMethodSetting | The input method setting management object, which provides input method query and management capabilities. It includes obtaining the list of enabled/disabled/all input methods (**getInputMethods**/**getAllInputMethods**), querying the subtype list of a specified input method (**listInputMethodSubtype**), obtaining the current input method and subtype, subscribing to input method switching events (**on('imeChange')**), subscribing to panel showing/hiding events (**on('imeShow')**/**on('imeHide')**), querying the panel display state (**isPanelShown**), enabling/disabling an input method (**enableInputMethod**), and obtaining the enabled state of the input method itself (**getInputMethodState**). Obtain an instance through `getSetting()`. |

In addition, this module defines multiple key data types:

| Type | Description |
|---|---|
| InputMethodProperty | Input method property information, describing the name, ID, label, icon, enabled status, and other properties of an input method. |
| InputMethodSubtype | Input method subtype, describing the language, mode, and other subtype properties of an input method. |
| TextConfig | Text configuration of the edit box, including the input attribute (**InputAttribute**), cursor information (**CursorInfo**), selection information, window ID, and more. |
| InputAttribute | Input attribute, defining the text input type (**TextInputType**) and the Enter key type (**EnterKeyType**). |
| CursorInfo | Cursor information, defining the position and size of the cursor. |
| MessageHandler | Custom message handler, used to receive messages sent by the input method application and provide termination notifications. |

The typical process of interaction between an edit box application and the input method involves the combined invocation of multiple APIs of **InputMethodController**: obtain the controller -> attach to the input method -> subscribe to input method operation events -> process text operations in the callback -> detach from the input method.

```javascript
// The following is pseudocode illustrating the calling logic.

// 1. Obtain the input method controller and setting object.
let controller = inputMethod.getController();
let setting = inputMethod.getSetting();

// 2. Subscribe to input method operation events (subscribe before the attach API is called to ensure no events are missed).
controller.on('insertText', (text) => { /*Handle text insertion*/ });
controller.on('deleteLeft', (length) => { /*Handle backward deletion*/ });
controller.on('deleteRight', (length) => { /*Handle forward deletion*/ });
controller.on('selectByRange', (range) => { /*Handle text selection by range*/ });
controller.on('selectByMovement', (movement) => { /*Handle text selection by direction*/ });
controller.on('moveCursor', (direction) => { /*Handle cursor movement*/ });
controller.on('sendFunctionKey', (functionKey) => { /*Handle function keys*/ });
controller.on('handleExtendAction', (action) => { /*Handle extended actions*/ });

// 3. Attach the input method (called when the edit box gains focus).
let textConfig = {
  inputAttribute: { textInputType: TextInputType.TEXT, enterKeyType: EnterKeyType.NONE },
  cursorInfo: { left: 100, top: 200, width: 2, height: 20 },
  selection: { start: 0, end: 0 },
  windowId: 1
};
controller.attach(true, textConfig);

// 4. Show the keyboard.
controller.showTextInput();

// 5. Update the cursor and edit attributes (called when the edit box state changes).
controller.updateCursor(cursorInfo);
controller.updateAttribute(inputAttribute);
controller.changeSelection(text, start, end);

// 6. When the keyboard needs to be hidden.
controller.hideTextInput();

// 7. Detach the input method when the edit box loses focus.
controller.detach();

// 8. Switch the input method for system applications.
setting.getInputMethods(true);  // Obtain the list of enabled input methods.
inputMethod.switchInputMethod(targetProperty);  // Switch to the target input method.
```
> **NOTE:**
>
> Subscription to input method operation events (such as **insertText** and **deleteLeft**) should be completed before `attach` is called to avoid missing events. `attach` is the prerequisite for an edit box application to use input method capabilities. The input method must be attached before subsequent operations can be performed.

## Modules to Import

```ts
import { inputMethod } from '@kit.IMEKit';
```

## Constant

Provides the constants.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Value| Description|
| -------- | -------- | -------- | -------- |
| MAX_TYPE_NUM<sup>8+</sup> | number | 128 | Maximum number of supported input methods.|

## InputMethodProperty<sup>8+</sup>

Describes the input method application properties.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

<!--Table: 20%; 20%; 10%; 10%; 40%-->
| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| name<sup>9+</sup>  | string | Yes| No| Mandatory. Name of the input method package.|
| id<sup>9+</sup>    | string | Yes| No| Mandatory. Unique identifier of an input method extension in an app. **id** and **name** form a globally unique identifier of the input method extension.|
| label<sup>9+</sup>    | string | Yes| Yes| Optional.<br>- When **InputMethodProperty** is used as the input parameter of an API for switching or querying, you do not need to set this field. You can use name and ID to uniquely specify an input method extension.<br>- When **InputMethodProperty** is used as the return value of an API for querying (for example, [getCurrentInputMethod](#inputmethodgetcurrentinputmethod9)), this field indicates the name of the input method extension displayed externally. Use the label configured for the **InputMethodExtensionAbility**. If no label is configured, the label of the application entry ability is automatically used. If no label is configured for the application entry ability, the label configured in **AppScope** is automatically used.|
| labelId<sup>10+</sup>    | number | Yes| Yes| Optional.<br>- When **InputMethodProperty** is used as the input parameter of an API for switching or querying, you do not need to set this field. You can use name and ID to uniquely specify an input method extension.<br>- When **InputMethodProperty** is used as the return value of an API for querying (for example, [getCurrentInputMethod](#inputmethodgetcurrentinputmethod9)), this field indicates the resource ID of the **label** field.|
| icon<sup>9+</sup>    | string | Yes| Yes| Optional.<br>- When **InputMethodProperty** is used as the input parameter of an API for switching or querying, you do not need to set this field. You can use name and ID to uniquely specify an input method extension.<br>- When **InputMethodProperty** is used as the return value of an API for querying (for example, [getCurrentInputMethod](#inputmethodgetcurrentinputmethod9)), this field indicates the input method icon data, which can be obtained through icon ID.|
| iconId<sup>9+</sup>    | number | Yes| Yes| Optional.<br>- When **InputMethodProperty** is used as the input parameter of an API for switching or querying, you do not need to set this field. You can use name and ID to uniquely specify an input method extension.<br>- When **InputMethodProperty** is used as the return value of an API for querying (for example, [getCurrentInputMethod](#inputmethodgetcurrentinputmethod9)), this field indicates the resource ID of the **icon** field.|
| enabledState<sup>20+</sup>    | [EnabledState](#enabledstate15) | Yes | Yes | Optional.<br>- When **InputMethodProperty** is used as an input parameter for switching, querying, and other APIs, you may omit this field, and an input method extension can be uniquely specified by **name** and **id**.<br>- When **InputMethodProperty** is used as the return value of a query API (such as [getCurrentInputMethod](#inputmethodgetcurrentinputmethod9)), this field indicates the enabled state of the input method.|
| extra<sup>9+</sup>    | object | No | Yes | Extended information of the input method.<br/>- Since API version 10: optional;<br/>- API version 9: mandatory.|
| packageName<sup>(deprecated)</sup> | string | Yes| No| Name of the input method package. Mandatory.<br>**Note**: This API is supported since API version 8 and deprecated since API version 9. You are advised to use **name** instead.|
| methodId<sup>(deprecated)</sup> | string | Yes| No| Unique ID of the input method. Mandatory.<br>**Note**: This API is supported since API version 8 and deprecated since API version 9. You are advised to use **id** instead.|

## CapitalizeMode<sup>20+</sup>

Enumerates the modes of capitalizing the first letter of a text.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value| Description|
| -------- | -- | -------- |
| NONE | 0 | No initial capitalization is performed.<br/>Usage scenarios: Applicable to input boxes that do not require automatic capitalization, such as password input and verification code input.|
| SENTENCES | 1 | The first letter of each sentence is capitalized.<br/>Usage scenarios: Applicable to ordinary text input boxes, such as chat and memo, where the first letter is automatically capitalized following punctuation marks such as a period.|
| WORDS | 2 | The first letter of each word is capitalized.<br/>Usage scenarios: Applicable to scenarios where the first letter of each word needs to be capitalized, such as titles and personal names.|
| CHARACTERS | 3 | Every letter is capitalized.<br/>Usage scenarios: Applicable to all uppercase input scenarios, such as abbreviation input (for example, the domain name part in a URL).|

## inputMethod.getController<sup>9+</sup>

getController(): InputMethodController

Obtains an [InputMethodController](#inputmethodcontroller) instance.

Meaning/Function: Obtains the input method client controller instance of the current application, which is used for subsequent interaction with the input method (such as attaching to the input method, showing/hiding the keyboard, and synchronizing the edit box status).

Usage scenarios: When a foreground application (such as a memo or chat application) needs to control the showing/hiding of the input method, attach to or detach from the input method, or synchronize edit box information, it must first obtain the **InputMethodController** instance through this API.

Use effect: Returns an **InputMethodController** instance. Subsequently, the instance can be used to call a series of APIs such as **attach**, **showTextInput**, **hideTextInput**, and **detach** to interact with the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                           | Description                  |
| ----------------------------------------------- | ---------------------- |
| [InputMethodController](#inputmethodcontroller) | **InputMethodController** instance.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                    |
| -------- | ------------------------------ |
| 12800006 | input method controller error. Possible cause: create InputMethodController object failed. |

**Example**

```ts
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
```

## inputMethod.getDefaultInputMethod<sup>11+</sup>

getDefaultInputMethod(): InputMethodProperty

Obtains the default input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                        | Description                    |
| -------------------------------------------- | ------------------------ |
| [InputMethodProperty](#inputmethodproperty8) | Default input method property object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
let defaultIme: inputMethod.InputMethodProperty = inputMethod.getDefaultInputMethod();
```

## inputMethod.getSystemInputMethodConfigAbility<sup>11+</sup>

getSystemInputMethodConfigAbility(): ElementName

Obtains the information about the system input method configuration ability.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                        | Description                    |
| -------------------------------------------- | ------------------------ |
| [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md) | Element name of the input method configuration page ability.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { bundleManager } from '@kit.AbilityKit';

let inputMethodConfig: bundleManager.ElementName = inputMethod.getSystemInputMethodConfigAbility();
```

## inputMethod.getSetting<sup>9+</sup>

getSetting(): InputMethodSetting

Obtains an [InputMethodSetting](#inputmethodsetting8) instance.

Meaning/Function: Obtains the input method setting instance, which is used for configuration management operations such as querying the input method list, subscribing to input method change events, and querying panel visibility.

Usage scenarios: When an application needs to query the installed/activated input method list, subscribe to input method switching events, or display the input method selection dialog, it must first obtain the **InputMethodSetting** instance through this API.

Use effect: Returns an **InputMethodSetting** instance. Subsequently, the instance can be used to call APIs such as **getInputMethods**, **listInputMethodSubtype**, and **on('imeChange')**.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                     | Description                      |
| ----------------------------------------- | -------------------------- |
| [InputMethodSetting](#inputmethodsetting8) | **InputMethodSetting** instance.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800007 |  input method setter error. Possible cause: create InputMethodSetting object failed. |

**Example**

```ts
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();
```

## inputMethod.switchInputMethod<sup>9+</sup>

switchInputMethod(target: InputMethodProperty, callback: AsyncCallback&lt;boolean&gt;): void

Switches the input method. This API uses an asynchronous callback to return the result.

Meaning/Function: Switches the current input method to the specified target input method.

Usage scenarios: Used when the current input method application needs to switch to another input method (for example, when the user selects a new input method in the input method settings).

Use effect: On success, the system switches the current input method to the target input method, and the target input method becomes the new current input method; on failure, the current input method remains unchanged.

**Required permissions:**
- API versions 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**Required permissions:**
- API versions 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| target | [InputMethodProperty](#inputmethodproperty8) | Yes | Target input method.<br/>Usage scenarios: Specifies the target input method to switch to, uniquely identified by **name** and **id**.<br/>Note: only the **name** and **id** fields need to be filled in to uniquely specify an input method; optional fields such as **label** and **icon** are not required. |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201 | permissions check fails. [since 9 - 10].        |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800005 | configuration persistence error.        |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
inputMethod.switchInputMethod(currentIme, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to switchInputMethod, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in switching input method.');
  } else {
    console.error('Failed to switch input method.');
  }
});
```

> **NOTE**
>
> In API version 11, the error code `201 permissions check fails.` has been removed.

## inputMethod.switchInputMethod<sup>9+</sup>
switchInputMethod(target: InputMethodProperty): Promise&lt;boolean&gt;

Switches the input method. This API uses a promise to return the result.

Meaning/Function: Switches the current input method to the specified target input method.

Usage scenarios: Used when the current input method application needs to switch to another input method.

Use effect: On success, the system switches the current input method to the target input method; on failure, the current input method remains unchanged.

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | target | [InputMethodProperty](#inputmethodproperty8) | Yes | Target input method.<br/>Usage scenarios: Specifies the target input method to switch to, uniquely determined by **name** and **id**.<br/>Note: only the **name** and **id** fields need to be filled in to uniquely specify an input method. |

**Return value**

  | Type                                     | Description                        |
  | ----------------------------------------- | ---------------------------- |
  | Promise&lt;boolean&gt; | Promise object. When resolved, returns **true** if the input method is switched successfully, and returns **false** if the input method fails to be switched; when rejected, returns an error object, indicating that an error occurs during input method switching. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201 | permissions check fails. [since 9 - 10]       |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800005 | configuration persistence error.        |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
inputMethod.switchInputMethod(currentIme).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in switching input method.');
  } else {
    console.error('Failed to switch input method.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to switchInputMethod, code: ${err.code}, message: ${err.message}`);
});
```

> **NOTE:**
>
> In API 11, the error code `201 permissions check fails.` is removed.

## inputMethod.getCurrentInputMethod<sup>9+</sup>

getCurrentInputMethod(): InputMethodProperty

Obtains the current input method. This API returns the result synchronously.

Meaning/Function: Obtains the property information of the input method currently in use.

Usage scenarios: Used when an application needs to know which input method is currently active (for example, to determine the input method name or obtain the input method ID for subsequent switching operations).

Use effect: Returns the **InputMethodProperty** object of the current input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                        | Description                    |
| -------------------------------------------- | ------------------------ |
| [InputMethodProperty](#inputmethodproperty8) | Input method property object.|

**Example**

```ts
let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
```

## inputMethod.switchCurrentInputMethodSubtype<sup>9+</sup>

switchCurrentInputMethodSubtype(target: InputMethodSubtype, callback: AsyncCallback\<boolean>): void

Switches to another subtype of this input method. This API uses an asynchronous callback to return the result.

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| target |  [InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)| Yes| Target input method subtype.|
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201 | permissions check fails. [since 9 - 10]       |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800005 | configuration persistence error.        |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let extra: Record<string, string> = {}
// For details, see the parameter description of **InputMethodSubtype**.
inputMethod.switchCurrentInputMethodSubtype({
  id: "ServiceExtAbility",
  label: "",
  name: "com.example.keyboard",
  mode: "upper",
  locale: "",
  language: "",
  icon: "",
  iconId: 0,
  extra: extra
}, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to switchCurrentInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in switching currentInputMethodSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodSubtype');
  }
});
```

> **NOTE**
>
> In API 11, the error code `201 permissions check fails.` is removed.

## inputMethod.switchCurrentInputMethodSubtype<sup>9+</sup>

switchCurrentInputMethodSubtype(target: InputMethodSubtype): Promise&lt;boolean&gt;

Switches to another subtype of this input method. This API uses a promise to return the result.

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
|target |  [InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)| Yes| Target input method subtype.|

**Return value**

| Type                                     | Description                        |
| ----------------------------------------- | ---------------------------- |
| Promise&lt;boolean&gt; | Promise object. When resolved, **true** indicates that the current input method subtype is switched successfully, and **false** indicates that the current input method subtype fails to be switched; when rejected, an error object is returned, indicating that an error occurs during input method subtype switching. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201 | permissions check fails. [since 9 - 10]       |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800005 | configuration persistence error.        |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let extra: Record<string, string> = {}
// For details, see the parameter description of **InputMethodSubtype**.
inputMethod.switchCurrentInputMethodSubtype({
  id: "ServiceExtAbility",
  label: "",
  name: "com.example.keyboard",
  mode: "upper",
  locale: "",
  language: "",
  icon: "",
  iconId: 0,
  extra: extra
}).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in switching currentInputMethodSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodSubtype.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to switchCurrentInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
});
```

> **NOTE**
>
> In API 11, the error code `201 permissions check fails.` is removed.

## inputMethod.getCurrentInputMethodSubtype<sup>9+</sup>

getCurrentInputMethodSubtype(): InputMethodSubtype

Obtains the current input method subtype.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                        | Description                    |
| -------------------------------------------- | ------------------------ |
| [InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype) | Current input method subtype.|

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';

let currentImeSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
```

## inputMethod.switchCurrentInputMethodAndSubtype<sup>9+</sup>

switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype, callback: AsyncCallback\<boolean>): void

Switches to a specified subtype of a specified input method. This API uses an asynchronous callback to return the result.

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
|inputMethodProperty |  [InputMethodProperty](#inputmethodproperty8)| Yes| Target input method.|
|inputMethodSubtype |  [InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)| Yes| Target input method subtype.|
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201 | permissions check fails. [since 9 - 10].        |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800005 | configuration persistence error.        |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
let imSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
inputMethod.switchCurrentInputMethodAndSubtype(currentIme, imSubType, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to switchCurrentInputMethodAndSubtype, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in switching currentInputMethodAndSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodAndSubtype.');
  }
});
```

> **NOTE:**
>
> In API 11, the error code `201 permissions check fails.` is removed.

## inputMethod.switchCurrentInputMethodAndSubtype<sup>9+</sup>

switchCurrentInputMethodAndSubtype(inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype): Promise&lt;boolean&gt;

Switches to a specified subtype of a specified input method. This API uses a promise to return the result.

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**Required permissions:**
- API version 9–10: **ohos.permission.CONNECT_IME_ABILITY**
- API version 11+: N/A

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
|inputMethodProperty |  [InputMethodProperty](#inputmethodproperty8)| Yes| Target input method.|
|inputMethodSubtype |  [InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)| Yes| Target input method subtype.|

**Return value**

| Type                                     | Description                        |
| ----------------------------------------- | ---------------------------- |
| Promise&lt;boolean&gt; | Promise object. When resolved, **true** is returned if switching to the specified subtype of the specified input method succeeds, and **false** is returned if switching to the specified subtype of the specified input method fails; when rejected, an error object is returned, indicating that an error occurred while switching to the specified subtype of the specified input method. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201 | permissions check fails. [since 9 - 10].        |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800005 | configuration persistence error.        |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
let imSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
inputMethod.switchCurrentInputMethodAndSubtype(currentIme, imSubType).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in switching currentInputMethodAndSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodAndSubtype.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to switchCurrentInputMethodAndSubtype, code: ${err.code}, message: ${err.message}`);
});
```

> **NOTE**
>
> In API 11, the error code `201 permissions check fails.` is removed.

## inputMethod.getInputMethodController<sup>(deprecated)</sup>

getInputMethodController(): InputMethodController

Obtains an [InputMethodController](#inputmethodcontroller) instance.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [getController](#inputmethodgetcontroller9) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                           | Description                    |
| ----------------------------------------------- | ------------------------ |
| [InputMethodController](#inputmethodcontroller) | Current **InputMethodController** instance.|

**Example**

```ts
let inputMethodController: inputMethod.InputMethodController = inputMethod.getInputMethodController();
```

## inputMethod.getInputMethodSetting<sup>(deprecated)</sup>

getInputMethodSetting(): InputMethodSetting

Obtains an [InputMethodSetting](#inputmethodsetting8) instance.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [getSetting](#inputmethodgetsetting9) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                     | Description                      |
| ----------------------------------------- | -------------------------- |
| [InputMethodSetting](#inputmethodsetting8) | **InputMethodSetting** instance.|

**Example**

```ts
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getInputMethodSetting();
```

## inputMethod.setSimpleKeyboardEnabled<sup>20+</sup>

setSimpleKeyboardEnabled(enable: boolean): void

Enables or disables the simple keyboard.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| enable | boolean | Yes| Whether to enable the simple keyboard. The value **true** indicates that the simple keyboard is enabled; the value **false** indicates the opposite.<br> The native edit box takes effect when it is focused next time, while the self-drawn component takes effect when the input method is attached by calling [attach](#attach10) next time.|

**Example**

```ts
  let enable: boolean = false;
  inputMethod.setSimpleKeyboardEnabled(enable);
```

## inputMethod.onAttachmentDidFail<sup>22+</sup>

onAttachmentDidFail(callback: Callback&lt;AttachFailureReason&gt;): void

Subscribes to attachment failure events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[AttachFailureReason](#attachfailurereason22)&gt; | Yes| Callback used to return the reason for attachment failure. This callback is only invoked when the attachment failure is triggered by the registrant's process.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let attachmentDidFailCallback: Callback<inputMethod.AttachFailureReason> = 
  (reason: inputMethod.AttachFailureReason): void => {
    console.error(`Attachment failed with reason: ${reason}.`);
  if (reason === inputMethod.AttachFailureReason.CALLER_NOT_FOCUSED) {
    console.error(`Failure reason is CALLER_NOT_FOCUSED.`);
  }
  };
inputMethod.onAttachmentDidFail(attachmentDidFailCallback);
```

## inputMethod.offAttachmentDidFail<sup>22+</sup>

offAttachmentDidFail(callback?:  Callback&lt;AttachFailureReason&gt;): void

Unsubscribes from attachment failure events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[AttachFailureReason](#attachfailurereason22)&gt; | No| Callback used for unsubscription, which must be the same as that passed by the subscription API. If no parameter is specified, all callback functions for this event will be unsubscribed.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let attachmentDidFailCallback: Callback<inputMethod.AttachFailureReason> = 
  (reason: inputMethod.AttachFailureReason): void => {
    console.error(`Attachment failed with reason: ${reason}.`);
  if (reason === inputMethod.AttachFailureReason.CALLER_NOT_FOCUSED) {
    console.error(`Failure reason is CALLER_NOT_FOCUSED.`);
  }
  };
inputMethod.onAttachmentDidFail(attachmentDidFailCallback);
inputMethod.offAttachmentDidFail(attachmentDidFailCallback);
```

## TextInputType<sup>10+</sup>

Enumerates the text input types.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value|Description|
| -------- | -------- |-------- |
| NONE  | -1 |NONE.<br/>Usage scenarios: used when the edit box does not want to specify a particular input type, and the input method uses the default keyboard layout. |
| TEXT  | 0 |Text type.<br/>Usage scenarios: applicable to ordinary text input boxes, such as chat and memo, and the input method displays a full-featured keyboard. |
| MULTILINE  | 1 |Multiline type.<br/>Usage scenarios: applicable to scenarios that require multiline text input, such as long text editing and comment boxes. |
| NUMBER  | 2 |Number type.<br/>Usage scenarios: applicable to scenarios that require only numeric input, such as quantity input and age input, and the input method displays a numeric keyboard. |
| PHONE  | 3 |Phone number type.<br/>Usage scenarios: applicable to phone number input boxes, and the input method displays a phone number keyboard (including digits and common phone symbols). |
| DATETIME  | 4 |Date type.<br/>Usage scenarios: applicable to date and time input boxes, and the input method displays a date-related keyboard layout. |
| EMAIL_ADDRESS  | 5 |Email address type.<br/>Usage scenarios: applicable to email input boxes, and the input method keyboard highlights common email symbols such as "@" and ".". |
| URL  | 6 |Link type.<br/>Usage scenarios: applicable to URL input boxes, and the input method keyboard highlights common URL symbols such as "/" and ".". |
| VISIBLE_PASSWORD  | 7 |Password type.<br/>Usage scenarios: applicable to password input boxes, and the input method displays a visible password keyboard without automatic suggestions. |
| NUMBER_PASSWORD<sup>11+</sup> | 8 |Numeric password type.<br/>Usage scenarios: applicable to scenarios that require only numeric password input, such as PIN code input. |
| SCREEN_LOCK_PASSWORD<sup>20+</sup> | 9 |Screen lock password type.<br/>Usage scenarios: applicable to the password input box on the lock screen. |
| USER_NAME<sup>20+</sup> | 10 |Username type.<br/>Usage scenarios: applicable to username input boxes, and the input method can provide optimized suggestions based on username characteristics. |
| NEW_PASSWORD<sup>20+</sup> | 11 |New password type.<br/>Usage scenarios: applicable to input boxes for setting a new password, and the input method can provide password strength hints. |
| NUMBER_DECIMAL<sup>20+</sup> | 12 |Number type with a decimal point.<br/>Usage scenarios: applicable to scenarios that require input of numbers with a decimal point, such as amount input. |
| ONE_TIME_CODE<sup>20+</sup> | 13 |Verification code type.<br/>Usage scenarios: applicable to verification code input boxes, and the input method can optimize the verification code input experience. |

## EnterKeyType<sup>10+</sup>

Enumerates the function types represented by the Enter key of the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value|Description|
| -------- | -------- |-------- |
| UNSPECIFIED  | 0 |Unspecified.<br/>Usage scenarios: used when the edit box does not specify a specific function for the Enter key. |
| NONE  | 1 |NONE.<br/>Usage scenarios: the Enter key has no specific behavior and is used only as a line break or a normal key. |
| GO  | 2 |Go.<br/>Usage scenarios: applicable to URL input boxes, where the Enter key triggers the "Go" action, such as opening a link. |
| SEARCH  | 3 |Search.<br/>Usage scenarios: applicable to search boxes, where the Enter key triggers the search action. |
| SEND  | 4 |Send.<br/>Usage scenarios: applicable to message sending boxes, where the Enter key triggers the send action. |
| NEXT  | 5 |Next.<br/>Usage scenarios: applicable to multi-step forms, where the Enter key jumps to the next input box. |
| DONE  | 6 |Done.<br/>Usage scenarios: applicable to the last input box of a single-step form, where the Enter key indicates that input is complete. |
| PREVIOUS  | 7 |Previous.<br/>Usage scenarios: applicable to multi-step forms, where the Enter key jumps to the previous input box. |
| NEWLINE<sup>12+</sup>  | 8 | Line break.<br/>Usage scenarios: applicable to multi-line text edit boxes, where the Enter key inserts a line break.|

## KeyboardStatus<sup>10+</sup>

Enumerates the soft keyboard states of the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value|Description|
| -------- | -------- |-------- |
| NONE  | 0 |NONE.<br/>Usage scenarios: used when the keyboard status is not determined or cannot be determined. |
| HIDE  | 1 |Hidden state.<br/>Usage scenarios: indicates that the soft keyboard is currently hidden. |
| SHOW  | 2 |Shown state.<br/>Usage scenarios: indicates that the soft keyboard is currently shown. |

## Direction<sup>10+</sup>

Enumerates the directions of cursor movement of the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value|Description|
| -------- | -------- |-------- |
| CURSOR_UP  | 1 |Upward.<br/>Usage scenarios: Used when the input method requests to move the cursor upward, such as moving the cursor up in multi-line text. |
| CURSOR_DOWN  | 2 |Downward.<br/>Usage scenarios: Used when the input method requests to move the cursor downward. |
| CURSOR_LEFT  | 3 |Leftward.<br/>Usage scenarios: Used when the input method requests to move the cursor leftward, such as moving the cursor before deleting the character to the left of the cursor. |
| CURSOR_RIGHT  | 4 |Rightward.<br/>Usage scenarios: Used when the input method requests to move the cursor rightward. |

## ExtendAction<sup>10+</sup>

Enumerates the types of extended edit actions on the edit box.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value|Description|
| -------- | -------- |-------- |
| SELECT_ALL  | 0 |Select all.<br/>Usage scenarios: used when the input method requests to select all text in the edit box. |
| CUT  | 3 |Cut.<br/>Usage scenarios: used when the input method requests to cut the selected text, copying the selected text to the clipboard and deleting the original text. |
| COPY  | 4 |Copy.<br/>Usage scenarios: used when the input method requests to copy the selected text, copying the selected text to the clipboard. |
| PASTE  | 5 |Paste.<br/>Usage scenarios: used when the input method requests to paste the clipboard content. |

## FunctionKey<sup>10+</sup>

Describes the type of the input method function key.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| enterKeyType  | [EnterKeyType](#enterkeytype10) | No| No| Function type represented by the Enter key of the input method.|

## InputAttribute<sup>10+</sup>

Describes the attributes of the edit box, including the text input type and Enter key function type.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

<!--Table: 20%; 20%; 10%; 10%; 40%-->
| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| textInputType  | [TextInputType](#textinputtype10) | No| No| Enumerates the text input types.|
| enterKeyType  | [EnterKeyType](#enterkeytype10) | No| No| Function type represented by the Enter key.|
| placeholder<sup>20+</sup> | string | No| Yes| Placeholder information set for the edit box.<br>- When placeholder information is set for the edit box, the length cannot exceed 255 characters (a placeholder longer than 255 characters will be automatically truncated to 255 characters). It is used to prompt or guide users to enter temporary text or symbols. (For example, the placeholder indicates whether the input item is mandatory.)<br>- If no placeholder is set for the edit box, the value is an empty string by default.<br>- This field is provided for the input method application when [attach](#attach10) is called.|
| abilityName<sup>20+</sup> | string | No| Yes| Ability name set for the edit box.<br>- If the ability name is set for the edit box, the length cannot exceed 127 characters. (A name longer than 127 characters will be automatically truncated to 127 characters.)<br>- If the ability name is not set for the edit box, the value is an empty string by default.<br>- This field is provided for the input method application when [attach](#attach10) is called.|
| consumeKeyEvents | boolean | No | Yes | Whether the edit box has the full capability to handle keys such as letters, characters, and function keys. The default value is **false**.<br/>- The value **true** means the edit box has this capability.<br/>- The value **false** means the edit box does not have this capability.<br/>- This field is provided to the input method application when [attach](#attach10) / [InputAttribute](#inputattribute10) is called.  <br/>**Since:** 26.0.0<br/>**Model restriction:** This parameter can be used only in the stage model. |

## TextConfig<sup>10+</sup>

Describes the configuration of the edit box.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

<!--Table: 20%; 20%; 10%; 10%; 40%-->
| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| inputAttribute  | [InputAttribute](#inputattribute10) | No| No| Edit box attribute.|
| cursorInfo  | [CursorInfo](#cursorinfo10) | No| Yes| Cursor information.|
| selection  | [Range](#range10) | No| Yes| Text selection range.|
| windowId  | number | No| Yes| ID of the window where the edit box is located. The value must be an integer.<br>You are advised to call [getWindowProperties](../apis-arkui/arkts-apis-window-Window.md#getwindowproperties9) to obtain the window ID.|
| newEditBox<sup>20+</sup> | boolean | No| Yes| Whether the edit box is new. The value **true** means the edit box is new; the value **false** means the opposite.|
| capitalizeMode<sup>20+</sup> | [CapitalizeMode](#capitalizemode20) | No| Yes| Capitalization mode set for the edit box. If it is not set or is set to an invalid value, no initial capitalization is performed by default.|

## CursorInfo<sup>10+</sup>

Represents the cursor information.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| left  | number | No| No| Horizontal coordinate of the cursor, in px. The value must be an integer. The minimum value is 0 and the maximum value is the width of the current screen.|
| top  | number | No| No| Vertical coordinate of the cursor, in px. The value must be an integer. The minimum value is 0 and the maximum value is the height of the current screen.|
| width  | number | No| No| Width of the cursor, in px. The value must be an integer. The minimum value is 0 and the maximum value is the width of the current screen.|
| height  | number | No| No| Height of the cursor, in px. The value must be an integer. The minimum value is 0 and the maximum value is the height of the current screen.|
| displayId  | number | No | Yes | ID of the display where the cursor is located.<br/>**Since:** 26.0.0<br/>**Model restriction:** This parameter can be used only in the stage model. |

## Range<sup>10+</sup>

Describes the range of the selected text.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| start  | number | No| No| Index of the first selected character in the edit box. The value is an integer greater than or equal to 0, and cannot exceed the actual text length.|
| end  | number | No| No| Index of the last selected character in the edit box. The value is an integer greater than or equal to 0, and cannot exceed the actual text length. The **end** value must be greater than the **start** value.|

## Movement<sup>10+</sup>

Describes the direction in which the cursor moves when the text is selected.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| direction  | [Direction](#direction10) | No| No| Direction in which the cursor moves when the text is selected.|

## InputWindowInfo<sup>10+</sup>

Describes the window information of the input method keyboard.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| name  | string | No| No| Name of the input method keyboard window.|
| left  | number | No| No| Horizontal coordinate of the upper left corner of the input method keyboard window, in px. The value must be an integer. The minimum value is 0 and the maximum value is the width of the current screen.|
| top  | number | No| No| Vertical coordinate of the upper left corner of the input method keyboard window, in px. The value must be an integer. The minimum value is 0 and the maximum value is the height of the current screen.|
| width  | number | No| No| Width of the input method keyboard window, in px. The value must be an integer. The minimum value is 0 and the maximum value is the width of the current screen.|
| height  | number | No| No| Height of the input method keyboard window, in px. The value must be an integer. The minimum value is 0 and the maximum value is the height of the current screen.|
| displayId<sup>23+</sup> | number | No| Yes| ID of the display where the soft keyboard window is located.<br>**Model restriction**: This parameter can be used only in the stage model.|

## EnabledState<sup>15+</sup>

Indicates whether the input method is enabled.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value|Description|
| -------- | -------- |-------- |
| DISABLED   | 0 |Not enabled.<br/>Usage scenarios: The input method is disabled and cannot be used as the current input method. |
| BASIC_MODE  | 1 |Basic mode.<br/>Usage scenarios: The input method is enabled but in basic mode, providing only basic input capabilities and not supporting advanced features (such as custom communication). |
| FULL_EXPERIENCE_MODE  | 2 |Full experience mode.<br/>Usage scenarios: The input method is enabled and in full experience mode, supporting all features (including custom communication and text preview). |

## RequestKeyboardReason<sup>15+</sup>

Enumerates the reasons for requesting the keyboard.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value|Description|
| -------- | -------- |-------- |
| NONE   | 0 |Indicates that no specific reason triggers the keyboard request.<br/>Usage scenarios: default value, used when no specific trigger reason is specified. |
| MOUSE  | 1 |Indicates that the keyboard request is triggered by a mouse operation.<br/>Usage scenarios: used when the user clicks the edit box with a mouse to trigger the keyboard to pop up. |
| TOUCH  | 2 |Indicates that the keyboard request is triggered by a touch operation.<br/>Usage scenarios: used when the user taps the edit box to trigger the keyboard to pop up. |
| OTHER  | 20 |Indicates that the keyboard request is triggered by other reasons.<br/>Usage scenarios: used when the trigger reason for the keyboard to pop up is neither mouse nor touch. |

## MessageHandler<sup>15+</sup>

Represents a custom communication object.

> **NOTE**
>
> You can register this object to receive custom communication data sent by the input method application. When the custom communication data is received, the [onMessage](#onmessage15) callback in this object is triggered.
>
> This object is globally unique. After multiple registrations, only the last registered object is valid and retained, and the [onTerminated](#onterminated15) callback of the penultimate registered object is triggered.
>
> If this object is unregistered, its [onTerminated](#onterminated15) callback will be triggered.

### onMessage<sup>15+</sup>

onMessage(msgId: string, msgParam?: ArrayBuffer): void

Receives custom data sent by the input method application.

> **NOTE**
>
> This callback is triggered when the registered **MessageHandler** receives custom communication data sent by the input method application.
>
> The **msgId** parameter is mandatory, and the **msgParam** parameter is optional. If only the custom **msgId** data is received, confirm it with the data sender.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type       | Mandatory| Description                            |
| -------- | ----------- | ---- | -------------------------------- |
| msgId    | string      | Yes  | Identifier of the received custom communication data.|
| msgParam | ArrayBuffer | No  | Message body of the received custom communication data.|

**Example**

```ts
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();

let messageHandler: inputMethod.MessageHandler = {
  onTerminated(): void {
    console.info('OnTerminated.');
  },
  onMessage(msgId: string, msgParam?: ArrayBuffer): void {
    console.info(`recv message, msg: ${msgId}, msgParam: ${JSON.stringify(msgParam)}`);
  }
};
inputMethodController.recvMessage(messageHandler);
```

### onTerminated<sup>15+</sup>

onTerminated(): void

Listens for MessageHandler termination.

> **NOTE**
>
> When an application registers a new MessageHandler object, the **OnTerminated** callback of the previous registered MessageHandler object is triggered.
>
> When an application unregisters a MessageHandler object, the **OnTerminated** callback of the current registered MessageHandler object is triggered.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Example**

```ts
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();

let messageHandler: inputMethod.MessageHandler = {
  onTerminated(): void {
    console.info('OnTerminated.');
  },
  onMessage(msgId: string, msgParam?: ArrayBuffer): void {
    console.info(`recv message, msg: ${msgId}, msgParam: ${JSON.stringify(msgParam)}`);
  }
};
inputMethodController.recvMessage(messageHandler);
```

## SetPreviewTextCallback<sup>17+</sup>

type SetPreviewTextCallback = (text: string, range: Range) => void

Callback triggered when the input method framework needs to display the text preview.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name      | Type         | Mandatory| Description                         |
| ------- | ----------------- | ---- | ----------------------------- |
| text    | string            | Yes  | Preview text content.                |
| range   | [Range](#range10) | Yes  | Describes the range of the selected text.|

## AttachFailureReason<sup>22+</sup>

Enumerates the reasons for attachment failure.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Value|Description|
| -------- | -------- |-------- |
| CALLER_NOT_FOCUSED    | 0 |Indicates a failure caused because the caller is not the application that owns the focused window.<br/>Usage scenarios: When **attach** is called while the application window is not focused, this failure reason is returned.<br/>Note: Ensure that the application window is focused before calling attach. |
| IME_ABNORMAL  | 1 |Indicates a failure caused by an input method application exception.<br/>Usage scenarios: When the input method application process crashes or is not running normally, **attach** returns this failure reason. |
| SERVICE_ABNORMAL  | 2 |Indicates a failure caused by an input method framework service exception.<br/>Usage scenarios: When the input method framework service process is abnormal, **attach** returns this failure reason. |

## AttachOptions<sup>23+</sup>

Defines additional options for binding an input method.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| requestKeyboardReason | [RequestKeyboardReason](#requestkeyboardreason15) | No| Yes|Reason for requesting the keyboard.|
| showKeyboard | boolean | No| Yes| Whether to start the input method keyboard after the input method attachment is complete.<br>- **true** means to start the input method keyboard.<br>- **false** means not to start the input method keyboard.|

## InputMethodController

In the following API examples, you must first use [getController](#inputmethodgetcontroller9) to obtain an **InputMethodController** instance, and then call the APIs using the obtained instance.

**InputMethodController** is the input method client controller, which provides foreground applications with core capabilities for interacting with the input method. After obtaining an instance through `inputMethod.getController()`, you can perform the following operations:

- Attachment management: Use [attach](#attach10) to establish attachment to the input method, and use [detach](#detach10) to perform detachment. **attach** and **detach** must be used in pairs.
- Keyboard control: Use [showTextInput](#showtextinput10) to start the soft keyboard and enter the editing state, and use [hideTextInput](#hidetextinput10) to hide the soft keyboard and exit the editing state. **showTextInput** and **hideTextInput** must be used in pairs.
- Edit box state synchronization: Use APIs such as [updateCursor](#updatecursor10), [changeSelection](#changeselection10), and [updateAttribute](#updateattribute10) to synchronize edit box state information such as the cursor, selection, and attributes with the input method.
- Event subscription: Use APIs such as **on('insertText')** and **on('deleteLeft')** to subscribe to text operation events sent by the input method application.

Typical call sequence: `getController()` → `attach()` → `showTextInput()`/`hideTextInput()` → `detach()`

> **NOTE**
>
> **attach** and **detach** must be used in pairs, and **showTextInput** and **hideTextInput** must be used in pairs. Otherwise, resource leaks or inconsistent states may occur.

### attach<sup>10+</sup>

attach(showKeyboard: boolean, textConfig: TextConfig, callback: AsyncCallback&lt;void&gt;): void

Attaches a self-drawn component to the input method. This API uses an asynchronous callback to return the result.

Meaning/Function: Establishes attachment between a self-drawn control and the input method application. This is the prerequisite for a self-drawn control to use input method features.

Usage scenarios: When a self-drawn control (not a system native edit box) needs to interact with the input method, this API must be called first to establish attachment. When a native edit box gains focus, the system performs attachment automatically, and there is no need to call this API.

Use effect: After the attachment succeeds, the self-drawn control can call **showTextInput**/**hideTextInput** to control the keyboard visibility, and call **updateCursor**/**changeSelection** to synchronize the edit box state, subscribe to input method events, and implement more features.

Preconditions: The window where the self-drawn control resides must be in the focused state; otherwise, the attachment fails.

Usage with related APIs: **attach** must be used in pairs with **detach**. Only after **attach** is called can APIs such as **showTextInput**, **hideTextInput**, and **updateCursor** be called.

Differences between similar APIs and selection principles:
- **attach**: does not require passing in a UIContext, and is applicable to self-drawn control attachment scenarios of API version 10+.
- **attachWithUIContext**: requires passing in a UIContext, and is applicable to stage model scenarios of API version 23+, supporting more attachment options.
- Selection principle: For stage model applications of API version 23+, use **attachWithUIContext** first to obtain more complete attachment option support.

> **NOTE**
>
> An input method can use the following features only when it has a self-drawn component attached to it: showing or hiding the keyboard, updating the cursor information, changing the selection range of the edit box, saving the configuration information, and listening for and processing information or commands sent by the input method.
>
> If the window where the self-drawn component is located is set to be non-focusable via [setWindowFocusable](../apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9), the system cannot guarantee proper interaction between the self-drawing input component and the input method. If you want to draw an input box in a non-focusable window, refer to [Input Box and Input Method Interaction in Non-Focusable Windows](../../inputmethod/use-inputmethod-in-not-focusable-window.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| showKeyboard | boolean | Yes| Whether to start the input method keyboard after the input method is successfully attached.<br>- **true** means to start the input method keyboard.<br>- **false** means not to start the input method keyboard.|
| textConfig | [TextConfig](#textconfig10) | Yes| Configuration of the edit box.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the input method is successfully attached, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = {
  textInputType: inputMethod.TextInputType.TEXT,
  enterKeyType: inputMethod.EnterKeyType.GO
}
let textConfig: inputMethod.TextConfig = { inputAttribute: inputAttribute };
inputMethod.getController().attach(true, textConfig, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to attach, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in attaching the inputMethod.');
});
```

### attach<sup>10+</sup>

attach(showKeyboard: boolean, textConfig: TextConfig): Promise&lt;void&gt;

Attaches a self-drawn component to the input method. This API uses a promise to return the result.

> **NOTE**
>
> An input method can use the following features only when it has a self-drawn component attached to it: showing or hiding the keyboard, updating the cursor information, changing the selection range of the edit box, saving the configuration information, and listening for and processing the information or commands sent by the input method.
>
> If the window where the self-drawn component is located is set to be non-focusable via [setWindowFocusable](../apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9), the system cannot guarantee proper interaction between the self-drawing input component and the input method. If you want to draw an input box in a non-focusable window, refer to [Input Box and Input Method Interaction in Non-Focusable Windows](../../inputmethod/use-inputmethod-in-not-focusable-window.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| showKeyboard | boolean | Yes| Whether to start the input method keyboard after the input method is successfully attached.<br>- **true** means to start the input method keyboard.<br>- **false** means not to start the input method keyboard.|
| textConfig | [TextConfig](#textconfig10) | Yes| Configuration of the edit box.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = {
  textInputType: inputMethod.TextInputType.TEXT,
  enterKeyType: inputMethod.EnterKeyType.GO
}
let textConfig: inputMethod.TextConfig = { inputAttribute: inputAttribute };
inputMethod.getController().attach(true, textConfig).then(() => {
  console.info('Succeeded in attaching inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to attach, code: ${err.code}, message: ${err.message}`);
});
```

### attach<sup>15+</sup>

attach(showKeyboard: boolean, textConfig: TextConfig, requestKeyboardReason: RequestKeyboardReason): Promise&lt;void&gt;

Attaches a self-drawn component to the input method. This API uses a promise to return the result.

> **NOTE**
>
> An input method can use the following features only when it has a self-drawn component attached to it: showing or hiding the keyboard, updating the cursor information, changing the selection range of the edit box, saving the configuration information, and listening for and processing the information or commands sent by the input method.
>
> If the window where the self-drawn component is located is set to be non-focusable via [setWindowFocusable](../apis-arkui/arkts-apis-window-Window.md#setwindowfocusable9), the system cannot guarantee proper interaction between the self-drawing input component and the input method. If you want to draw an input box in a non-focusable window, refer to [Input Box and Input Method Interaction in Non-Focusable Windows](../../inputmethod/use-inputmethod-in-not-focusable-window.md).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| showKeyboard | boolean | Yes| Whether to start the input method keyboard after the input method is successfully attached.<br>- **true** means to start the input method keyboard.<br>- **false** means not to start the input method keyboard.|
| textConfig | [TextConfig](#textconfig10) | Yes| Configuration of the edit box.|
| requestKeyboardReason | [RequestKeyboardReason](#requestkeyboardreason15) | Yes| Reason for requesting the keyboard.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = {
  textInputType: inputMethod.TextInputType.TEXT,
  enterKeyType: inputMethod.EnterKeyType.GO
}
let textConfig: inputMethod.TextConfig = { inputAttribute: inputAttribute };
let requestKeyboardReason: inputMethod.RequestKeyboardReason = inputMethod.RequestKeyboardReason.MOUSE;

inputMethod.getController().attach(true, textConfig, requestKeyboardReason).then(() => {
  console.info('Succeeded in attaching inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to attach, code: ${err.code}, message: ${err.message}`);
});
```

### attachWithUIContext<sup>23+</sup>

attachWithUIContext(uiContext: UIContext, textConfig: TextConfig, attachOptions?: AttachOptions): Promise&lt;void&gt;

Attaches a self-drawn component to the input method. This API uses a promise to return the result.

> **NOTE**
>
> An input method can use the following features only when it has a self-drawn component attached to it: showing or hiding the keyboard, updating the cursor information, changing the selection range of the edit box, saving the configuration information, and listening for and processing the information or commands sent by the input method.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

|  Name |    Type |   Mandatory  |   Description  |
| -------- | -------- | -------- | -------- |
| uiContext | [UIContext](../apis-arkui/arkts-apis-uicontext-uicontext.md) | Yes| **UIContext** instance.|
| textConfig | [TextConfig](#textconfig10) | Yes| Configuration of the edit box.|
| attachOptions | [AttachOptions](#attachoptions23) | No| Additional options for attachment.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { UIContext } from '@kit.ArkUI';

let uiContext: UIContext | undefined = UIContext.getCallingScopeUIContext();
let inputAttribute: inputMethod.InputAttribute = {
  textInputType: inputMethod.TextInputType.TEXT,
  enterKeyType: inputMethod.EnterKeyType.GO
}
let textConfig: inputMethod.TextConfig = { inputAttribute: inputAttribute };
let attachOptions: inputMethod.AttachOptions = { showKeyboard: true };
inputMethod.getController().attachWithUIContext(uiContext, textConfig, attachOptions).then(() => {
  console.info('Succeeded in attaching inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to attach, code: ${err.code}, message: ${err.message}`);
});
```

### discardTypingText<sup>20+</sup>

discardTypingText(): Promise&lt;void&gt;

Discards the text that is being typed. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called after the edit box is attached to an input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise object that returns no value.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800009 | input method client detached. |
| 12800015 | the other side does not accept the request. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().discardTypingText().then(() => {
  console.info('Succeeded discardTypingText.');
}).catch((err: BusinessError) => {
  console.error(`Failed to discardTypingText, code: ${err.code}, message: ${err.message}`);
});
```

### showTextInput<sup>10+</sup>

showTextInput(callback: AsyncCallback&lt;void&gt;): void

Enters the text editing mode. This API uses an asynchronous callback to return the result.

Meaning/Function: Pulls up the soft keyboard and puts the edit box into the text editing state.

Usage scenarios: Called when a self-drawn control needs to display the soft keyboard to start text input after being attached to the input method.

Use effect: The soft keyboard is displayed, and the edit box enters the editable text input state.

Preconditions: Call [attach](#attach10) to complete the attachment first. Otherwise, error code 12800009 is reported.

Usage with related APIs: **showTextInput** and **hideTextInput** must be used in pairs. After **hideTextInput** is called to exit the editing state, **showTextInput** must be called again to re-enter the editing state.

Differences between similar APIs and selection principles:
- **showTextInput**: For self-drawn controls. It must be called after **attach** completes the binding. It applies to self-drawn control scenarios and is the standard way to display the keyboard.
- **showSoftKeyboard**: For system applications. It requires the **ohos.permission.CONNECT_IME_ABILITY** permission. It applies to scenarios where a system application needs to forcibly display the keyboard.
- Selection principle: For self-drawn controls, use **showTextInput** preferentially. Use **showSoftKeyboard** only for system applications with special requirements.

> **NOTE**
>
> After the edit box is attached to an input method, this API can be called to start the soft keyboard and enter the text editing state.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showTextInput((err: BusinessError) => {
  if (err) {
    console.error(`Failed to showTextInput, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in showing the inputMethod.');
});
```

### showTextInput<sup>10+</sup>

showTextInput(): Promise&lt;void&gt;

Enters the text editing mode. This API uses a promise to return the result.

> **NOTE**
>
> After the edit box is attached to an input method, this API can be called to start the soft keyboard and enter the text editing state.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showTextInput().then(() => {
  console.info('Succeeded in showing text input.');
}).catch((err: BusinessError) => {
  console.error(`Failed to showTextInput, code: ${err.code}, message: ${err.message}`);
});
```

### showTextInput<sup>15+</sup>

showTextInput(requestKeyboardReason: RequestKeyboardReason): Promise&lt;void&gt;

Enters the text editing mode. This API uses a promise to return the result.

> **NOTE**
>
> After the edit box is attached to an input method, this API can be called to start the soft keyboard and enter the text editing state.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| requestKeyboardReason | [RequestKeyboardReason](#requestkeyboardreason15) | Yes| Reason for requesting the keyboard.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let requestKeyboardReason: inputMethod.RequestKeyboardReason = inputMethod.RequestKeyboardReason.MOUSE;

inputMethod.getController().showTextInput(requestKeyboardReason).then(() => {
  console.info('Succeeded in showing text input.');
}).catch((err: BusinessError) => {
  console.error(`Failed to showTextInput, code: ${err.code}, message: ${err.message}`);
});
```

### hideTextInput<sup>10+</sup>

hideTextInput(callback: AsyncCallback&lt;void&gt;): void

Exits the text editing mode. This API uses an asynchronous callback to return the result.

Meaning/Function: Hides the soft keyboard and makes the edit box exit the text editing state.

Usage scenarios: Called when a self-drawn control no longer needs input, for example, when the user taps an area outside the edit box or switches to another page.

Use effect: The soft keyboard is hidden, and the edit box exits the editing state. Calling this API does not unbind the input method. Calling **showTextInput** again can re-enter the editing state.

Preconditions: Call [attach](#attach10) to complete the attachment first, and call **showTextInput** to enter the editing state.

Usage with related APIs: **hideTextInput** and **showTextInput** must be used in pairs. If input is needed again after **hideTextInput** is called, you must call **showTextInput** first to re-enter the editing state; other editing operations cannot be called directly.

Differences between similar APIs and selection principles:
- **hideTextInput**: For self-drawn controls, exits the editing state without detachment, and can re-enter via **showTextInput**. It is suitable for scenarios where a self-drawn control needs to temporarily hide the keyboard.
- **hideSoftKeyboard**: For system applications, requires the **ohos.permission.CONNECT_IME_ABILITY** permission. It only hides the keyboard without changing the editing state.
- Selection principle: Self-drawn controls should preferentially use **hideTextInput**; system applications with special requirements should use **hideSoftKeyboard**.

> **NOTE**
>
> If the soft keyboard is displayed when this API is called, it will be hidden.
>
> Calling this API does not detach the edit box from the input method. The edit box can call [showTextInput](#showtextinput10) again to reenter the text editing mode.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached.             |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideTextInput((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hideTextInput, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding text input.');
});
```

### hideTextInput<sup>10+</sup>

hideTextInput(): Promise&lt;void&gt;

Exits the text editing mode. This API uses a promise to return the result.

> **NOTE**
>
> If the soft keyboard is displayed when this API is called, it will be hidden.
>
> Calling this API does not detach the edit box from the input method. The edit box can call [showTextInput](#showtextinput10) again to reenter the text editing mode.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideTextInput().then(() => {
  console.info('Succeeded in hiding inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hideTextInput, code: ${err.code}, message: ${err.message}`);
})
```

### detach<sup>10+</sup>

detach(callback: AsyncCallback&lt;void&gt;): void

Detaches the self-drawn component from the input method. This API uses an asynchronous callback to return the result.

Meaning/Function: Detaches the self-drawn control from the input method application and releases related resources.

Usage scenarios: Called when the self-drawn control no longer needs to interact with the input method (for example, page switching, edit box destruction, etc.).

Use effect: After detachment, APIs that require the attached state, such as **showTextInput**, **hideTextInput**, and **updateCursor**, can no longer be called. The input method soft keyboard will be hidden.

Usage with related APIs: **detach** must be used in pairs with **attach**. It is recommended that you call **detach** after **hideTextInput**. The complete flow is: **attach** → **showTextInput** → **hideTextInput** → **detach**.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().detach((err: BusinessError) => {
  if (err) {
    console.error(`Failed to detach, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in detaching inputMethod.');
});
```

### detach<sup>10+</sup>

detach(): Promise&lt;void&gt;

Detaches the self-drawn component from the input method. This API uses a promise to return the result.

Meaning/Function: Detaches the self-drawn control from the input method application and releases related resources.

Usage scenarios: Called when the self-drawn control no longer needs to interact with the input method.

Use effect: After detachment, APIs that require the attached state can no longer be called. The input method soft keyboard will be hidden.

Usage with related APIs: **detach** must be used in pairs with **attach**.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().detach().then(() => {
  console.info('Succeeded in detaching inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to detach, code: ${err.code}, message: ${err.message}`);
});
```

### setCallingWindow<sup>10+</sup>

setCallingWindow(windowId: number, callback: AsyncCallback&lt;void&gt;): void

Sets the window to be avoided by the input method. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API can be called to set the window that avoids the soft keyboard only after the edit box is attached to the input method.
>
> Pass in the window ID of the application attached to the input method. This window can avoid the input method window.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| windowId | number | Yes| Window ID of the application bound to the input method. The value must be an integer.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached.             |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let windowId: number = 2000;
inputMethod.getController().setCallingWindow(windowId, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to setCallingWindow, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting callingWindow.');
});
```

### setCallingWindow<sup>10+</sup>

setCallingWindow(windowId: number): Promise&lt;void&gt;

Sets the window to avoid the soft keyboard. This API uses a promise to return the result.

> **NOTE**
>
> After the window ID of the application bound to the input method is passed in the API, the input method window will not cover the window holding the application.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| windowId | number | Yes| Window ID of the application bound to the input method. The value must be an integer.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let windowId: number = 2000;
inputMethod.getController().setCallingWindow(windowId).then(() => {
  console.info('Succeeded in setting callingWindow.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setCallingWindow, code: ${err.code}, message: ${err.message}`);
});
```

### updateCursor<sup>10+</sup>

updateCursor(cursorInfo: CursorInfo, callback: AsyncCallback&lt;void&gt;): void

Updates the cursor information in this edit box. This API can be called to notify the input method of the cursor changes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API can be called to update the cursor information only after the edit box is attached to the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| cursorInfo | [CursorInfo](#cursorinfo10) | Yes| Cursor information.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached.             |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let cursorInfo: inputMethod.CursorInfo = {
  left: 0,
  top: 0,
  width: 600,
  height: 800
};
inputMethod.getController().updateCursor(cursorInfo, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to updateCursor, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in updating cursorInfo.');
});

```

### updateCursor<sup>10+</sup>

updateCursor(cursorInfo: CursorInfo): Promise&lt;void&gt;

Updates the cursor information in this edit box. This API can be called to notify the input method of the cursor changes. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called to update the cursor information only after the edit box is attached to the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| cursorInfo | [CursorInfo](#cursorinfo10) | Yes| Cursor information.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let cursorInfo: inputMethod.CursorInfo = {
  left: 0,
  top: 0,
  width: 600,
  height: 800
};
inputMethod.getController().updateCursor(cursorInfo).then(() => {
  console.info('Succeeded in updating cursorInfo.');
}).catch((err: BusinessError) => {
  console.error(`Failed to updateCursor, code: ${err.code}, message: ${err.message}`);
});
```

### changeSelection<sup>10+</sup>

changeSelection(text: string, start: number, end: number, callback: AsyncCallback&lt;void&gt;): void

Updates the information about the selected text in this edit box, to notify the input method when the selected text content or text range changes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API can be called to update the text selection information only after the edit box is attached to the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| text | string | Yes| All input text.|
| start | number | Yes| Start position of the selected text. The value is an integer greater than or equal to 0.|
| end | number | Yes| End position of the selected text. The value is an integer greater than or equal to 0.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached.             |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().changeSelection('text', 0, 5, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to changeSelection, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in changing selection.');
});
```

### changeSelection<sup>10+</sup>

changeSelection(text: string, start: number, end: number): Promise&lt;void&gt;

Updates the information about the selected text in this edit box, to notify the input method when the selected text content or text range changes. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called to update the text selection information only after the edit box is attached to the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| text | string | Yes| All input text.|
| start | number | Yes| Start position of the selected text. The value is an integer greater than or equal to 0.|
| end | number | Yes| End position of the selected text. The value is an integer greater than or equal to 0.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().changeSelection('test', 0, 5).then(() => {
  console.info('Succeeded in changing selection.');
}).catch((err: BusinessError) => {
  console.error(`Failed to changeSelection, code: ${err.code}, message: ${err.message}`);
});
```

### updateAttribute<sup>10+</sup>

updateAttribute(attribute: InputAttribute, callback: AsyncCallback&lt;void&gt;): void

Updates the attribute information of this edit box. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| attribute | [InputAttribute](#inputattribute10) | Yes| Attribute information.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached.             |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = { textInputType: 0, enterKeyType: 1 };
inputMethod.getController().updateAttribute(inputAttribute, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to updateAttribute, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in updating attribute.');
});
```

### updateAttribute<sup>10+</sup>

updateAttribute(attribute: InputAttribute): Promise&lt;void&gt;

Updates the attribute information of this edit box. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called to update the edit box attribute information only after the edit box is attached to the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| attribute | [InputAttribute](#inputattribute10) | Yes|  Attribute information.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800009 | input method client detached. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = { textInputType: 0, enterKeyType: 1 };
inputMethod.getController().updateAttribute(inputAttribute).then(() => {
  console.info('Succeeded in updating attribute.');
}).catch((err: BusinessError) => {
  console.error(`Failed to updateAttribute, code: ${err.code}, message: ${err.message}`);
});
```

### stopInputSession<sup>9+</sup>

stopInputSession(callback: AsyncCallback&lt;boolean&gt;): void

Ends this input session. This API uses an asynchronous callback to return the result.

Meaning/Function: Ends the current input session and hides the soft keyboard.

Usage scenarios: Called when an application needs to proactively end the input session (for example, when the user has completed the input operation).

Use effect: The soft keyboard is hidden and the input session ends.

Preconditions: This API can be called only when the edit box is attached to the input method, that is, after the edit control is tapped.

Usage with related APIs: **stopInputSession** hides the soft keyboard and ends the input session. If the **attach**/**showTextInput**/**hideTextInput**/**detach** flow of a self-drawn control is used, it is recommended that you use **hideTextInput** instead of **stopInputSession**.

> **NOTE**
>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to end the input session only when the edit box is focused.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes | Callback. When the input session ends successfully, **err** is **undefined** and **data** is **true**; when it fails, **err** is an error object. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().stopInputSession((err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to stopInputSession, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in stopping inputSession.');
  } else {
    console.error('Failed to stopInputSession.');
  }
});
```

### stopInputSession<sup>9+</sup>

stopInputSession(): Promise&lt;boolean&gt;

Ends this input session. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to end the input session only when the edit box is focused.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the input session is ended successfully, and **false** indicates the opposite.

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().stopInputSession().then((result: boolean) => {
  if (result) {
    console.info('Succeeded in stopping inputSession.');
  } else {
    console.error('Failed to stopInputSession.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to stopInputSession, code: ${err.code}, message: ${err.message}`);
});
```

### showSoftKeyboard<sup>9+</sup>

showSoftKeyboard(callback: AsyncCallback&lt;void&gt;): void

Shows the soft keyboard. This API uses an asynchronous callback to return the result.

Meaning/Function: Forcibly displays the soft keyboard of the current input method.

Usage scenarios: Used when a system application needs to forcibly display the input method soft keyboard (for example, a Settings application testing an input method).

Use effect: The input method soft keyboard is displayed.

Preconditions: This API can be called only when the edit box is attached to the input method.

Differences between similar APIs and selection principles:
- **showSoftKeyboard**: for system applications, requires the **ohos.permission.CONNECT_IME_ABILITY** permission, and only displays the keyboard without changing the editing state.
- **showTextInput**: for self-drawn controls, requires attachment first, and pulls up the keyboard and enters the editing state.
- Selection principle: use **showTextInput** for self-drawn controls; use **showSoftKeyboard** for system applications with the required permission.

> **NOTE**
>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to show the soft keyboard only when the edit box is focused.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY (for system applications only)

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                 | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails.  |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showSoftKeyboard((err: BusinessError) => {
  if (!err) {
    console.info('Succeeded in showing softKeyboard.');
  } else {
    console.error(`Failed to show softKeyboard, ${err.code}, message: ${err.message}`);
  }
});
```

### showSoftKeyboard<sup>9+</sup>

showSoftKeyboard(): Promise&lt;void&gt;

Shows the soft keyboard. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to show the soft keyboard only when the edit box is focused.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY (for system applications only)

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails.  |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showSoftKeyboard().then(() => {
  console.info('Succeeded in showing softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

### hideSoftKeyboard<sup>9+</sup>

hideSoftKeyboard(callback: AsyncCallback&lt;void&gt;): void

Hides the soft keyboard. This API uses an asynchronous callback to return the result.

Meaning/Function: Forcibly hides the soft keyboard of the current input method.

Usage scenarios: Used when a system application needs to forcibly hide the input method soft keyboard.

Use effect: The input method soft keyboard is hidden.

Preconditions: This API can be called only when the edit box is attached to the input method.

Differences between similar APIs and selection principles:
- **hideSoftKeyboard**: for system applications, requires the **ohos.permission.CONNECT_IME_ABILITY** permission, and only hides the keyboard without exiting the editing state.
- **hideTextInput**: for self-drawn controls, hides the keyboard and exits the editing state, and can re-enter the editing state by calling **showTextInput** again.
- Selection principle: self-drawn controls use **hideTextInput**; system applications with the required permission use **hideSoftKeyboard**.

> **NOTE**
>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to hide the soft keyboard only when the edit box is focused.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY (for system applications only)

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                 | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails.  |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideSoftKeyboard((err: BusinessError) => {
  if (!err) {
    console.info('Succeeded in hiding softKeyboard.');
  } else {
    console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
  }
})
```

### hideSoftKeyboard<sup>9+</sup>

hideSoftKeyboard(): Promise&lt;void&gt;

Hides the soft keyboard. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to hide the soft keyboard only when the edit box is focused.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY (for system applications only)

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails.  |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideSoftKeyboard().then(() => {
  console.info('Succeeded in hiding softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

### sendMessage<sup>15+</sup>

sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise&lt;void&gt;

Sends the custom communication to the input method application. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called only when the edit box is attached to the input method and enters the edit mode, and the input method application is in full experience mode.
>
> The maximum length of **msgId** is 256 B, and the maximum length of **msgParam** is 128 KB.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type       | Mandatory| Description                                      |
| -------- | ----------- | ---- | ------------------------------------------ |
| msgId    | string      | Yes  | Identifier of the custom data to be sent to the input method application.|
| msgParam | ArrayBuffer | No  | Message body of the custom data to be sent to the input method application.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Incorrect parameter length.  |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| 12800009 | input method client detached.               |
| 12800014 | the input method is in basic mode.          |
| 12800015 | the other side does not accept the request. |
| 12800016 | input method client is not editable.        |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let msgId: string = "testMsgId";
let msgParam: ArrayBuffer = new ArrayBuffer(128);
inputMethod.getController().sendMessage(msgId, msgParam).then(() => {
  console.info('Succeeded send message.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send message, code: ${err.code}, message: ${err.message}`);
});
```

### recvMessage<sup>15+</sup>

recvMessage(msgHandler?: MessageHandler): void

Registers or unregisters MessageHandler.

> **NOTE**
>
> The [MessageHandler](#messagehandler15) object is globally unique. After multiple registrations, only the last registered object is valid and retained, and the [onTerminated](#onterminated15) callback of the penultimate registered object is triggered.
>
> If no parameter is set, unregister [MessageHandler](#messagehandler15). Its [onTerminated](#onterminated15) callback will be triggered.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name    | Type                               | Mandatory| Description                                                        |
| ---------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| msgHandler | [MessageHandler](#messagehandler15) | No  | This object receives custom communication data from the input method application through [onMessage](#onmessage15) and receives a message for terminating the subscription to this object through [onTerminated](#onterminated15).<br>If no parameter is set, unregister [MessageHandler](#messagehandler15). Its [onTerminated](#onterminated15) callback will be triggered.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message        |
| -------- | ---------------- |
| 401      | Parameter error. Possible causes: 1. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let messageHandler: inputMethod.MessageHandler = {
  onTerminated(): void {
    console.info('OnTerminated.');
  },
  onMessage(msgId: string, msgParam?: ArrayBuffer): void {
    console.info('recv message.');
  }
};
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.recvMessage(messageHandler);
// Unregister the MessageHandler.
inputMethodController.recvMessage();
```

### stopInput<sup>(deprecated)</sup>

stopInput(callback: AsyncCallback&lt;boolean&gt;): void

Ends this input session. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> This API can be called only when the edit box is attached to the input method. That is, it can be called to end the input session only when the edit box is focused.
> 
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [stopInputSession](#stopinputsession9) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true**. Otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().stopInput((err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to stopInput, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in stopping input.');
  } else {
    console.error('Failed to stopInput.');
  }
});
```

### stopInput<sup>(deprecated)</sup>

stopInput(): Promise&lt;boolean&gt;

Ends this input session. This API uses a promise to return the result.

> **NOTE**
> 
> This API can be called only when the edit box is attached to the input method. That is, it can be called to end the input session only when the edit box is focused.
> 
> This API is supported since API version 6 and deprecated since API version 9. You are advised to use [stopInputSession](#stopinputsession9) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the operation is successful, and **false** means the opposite.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().stopInput().then((result: boolean) => {
  if (result) {
    console.info('Succeeded in stopping input.');
  } else {
    console.error('Failed to stopInput.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to stopInput, code: ${err.code}, message: ${err.message}`);
});
```

### on('insertText')<sup>10+</sup>

on(type: 'insertText', callback: (text: string) => void): void

Enables listening for the text insertion event of the input method. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Listening type. The value is fixed at **'insertText'**.|
| callback | (text: string) => void | Yes  | Callback used to return the text to be inserted.<br>The application needs to operate the content in the edit box based on the text content returned in the callback.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
const callback1 = (text: string): void => {
  console.info(`Succeeded in getting callback1, data: ${text}`);
}

const callback2 = (text: string): void => {
  console.info(`Succeeded in getting callback2, data: ${text}`);
}

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
// Register a callback.
inputMethodController.on('insertText', callback1);
inputMethodController.on('insertText', callback2);
// Cancel only callback1 of insertText.
inputMethodController.off('insertText', callback1);
// Cancel all callbacks of insertText.
inputMethodController.off('insertText');
```

### off('insertText')<sup>10+</sup>

off(type: 'insertText', callback?: (text: string) => void): void

Disables listening for the text insertion event of the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| type     | string                 | Yes  | Listening type. The value is fixed at **'insertText'**.|
| callback | (text: string) => void | No  | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let onInsertTextCallback: Callback<string> = (text: string): void => {
  console.info(`Succeeded in subscribing insertText: ${text}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('insertText', onInsertTextCallback);
inputMethodController.off('insertText');
```

### on('deleteLeft')<sup>10+</sup>

on(type: 'deleteLeft', callback: (length: number) => void): void

Enables listening for the leftward delete event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | ----- | ---- | ----- |
| type     | string  | Yes  | Listening type. The value is fixed at **'deleteLeft'**.|
| callback | (length: number) => void | Yes  | Callback used to return the length of the text to be deleted leftward.<br>The application needs to operate the content in the edit box based on the length returned in the callback.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
inputMethod.getController().on('deleteLeft', (length: number) => {
  console.info(`Succeeded in subscribing deleteLeft, length: ${length}`);
});
```

### off('deleteLeft')<sup>10+</sup>

off(type: 'deleteLeft', callback?: (length: number) => void): void

Disables listening for the leftward delete event.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                    | Mandatory| Description                                                        |
| -------- | ------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                   | Yes  | Listening type. The value is fixed at **'deleteLeft'**.|
| callback | (length: number) => void | No  | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let onDeleteLeftCallback: Callback<number> = (length: number): void => {
  console.info(`Succeeded in subscribing deleteLeft, length: ${length}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('deleteLeft', onDeleteLeftCallback);
inputMethodController.off('deleteLeft');
```

### on('deleteRight')<sup>10+</sup>

on(type: 'deleteRight', callback: (length: number) => void): void

Enables listening for the rightward delete event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | ----- | ---- | ----- |
| type     | string  | Yes  | Listening type. The value is fixed at **'deleteRight'**.|
| callback | (length: number) => void | Yes  | Callback used to return the length of the text to be deleted rightward.<br>The application needs to operate the content in the edit box based on the length returned in the callback.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
inputMethod.getController().on('deleteRight', (length: number) => {
  console.info(`Succeeded in subscribing deleteRight, length: ${length}`);
});
```

### off('deleteRight')<sup>10+</sup>

off(type: 'deleteRight', callback?: (length: number) => void): void

Disables listening for the rightward delete event.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                    | Mandatory| Description                                                        |
| -------- | ------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                   | Yes  | Listening type. The value is fixed at `deleteRight`.|
| callback | (length: number) => void | No  | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let onDeleteRightCallback: Callback<number> = (length: number): void => {
  console.info(`Succeeded in subscribing deleteRight, length: ${length}`);
};
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('deleteRight', onDeleteRightCallback);
inputMethodController.off('deleteRight');
```

### on('sendKeyboardStatus')<sup>10+</sup>

on(type: 'sendKeyboardStatus', callback: (keyboardStatus: KeyboardStatus) => void): void

Enables listening for the soft keyboard status event of the input method. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type | Mandatory| Description   |
| -------- | ------ | ---- | ---- |
| type     | string  | Yes  | Listening type. The value is fixed at **'sendKeyboardStatus'**.|
| callback | (keyboardStatus: [KeyboardStatus](#keyboardstatus10)) => void | Yes  | Callback used to return the soft keyboard status.<br>The application needs to perform operations based on the soft keyboard state returned in the callback.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
inputMethod.getController().on('sendKeyboardStatus', (keyboardStatus: inputMethod.KeyboardStatus) => {
  console.info(`Succeeded in subscribing sendKeyboardStatus, keyboardStatus: ${keyboardStatus}`);
});
```

### off('sendKeyboardStatus')<sup>10+</sup>

off(type: 'sendKeyboardStatus', callback?: (keyboardStatus: KeyboardStatus) => void): void

Disables listening for the input method soft keyboard status event of the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Listening type. The value is fixed at **'sendKeyboardStatus'**.|
| callback | (keyboardStatus: [KeyboardStatus](#keyboardstatus10)) => void | No  | Callback used to disable listening. If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let onSendKeyboardStatus: Callback<inputMethod.KeyboardStatus> = (keyboardStatus: inputMethod.KeyboardStatus): void => {
  console.info(`Succeeded in subscribing sendKeyboardStatus, keyboardStatus: ${keyboardStatus}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('sendKeyboardStatus', onSendKeyboardStatus);
inputMethodController.off('sendKeyboardStatus');
```

### on('sendFunctionKey')<sup>10+</sup>

on(type: 'sendFunctionKey', callback: (functionKey: FunctionKey) => void): void

Enables listening for the function key sending event of the input method. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type | Mandatory| Description    |
| -------- | -------- | ---- | ----- |
| type     | string  | Yes  | Listening type. The value is fixed at **'sendFunctionKey'**.|
| callback | (functionKey: [FunctionKey](#functionkey10)) => void | Yes  | Callback used to return the function key information sent by the input method.<br>The application needs to perform operations based on the function key information returned in the callback.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
inputMethod.getController().on('sendFunctionKey', (functionKey: inputMethod.FunctionKey) => {
  console.info(`Succeeded in subscribing sendFunctionKey, functionKey.enterKeyType: ${functionKey.enterKeyType}`);
});
```

### off('sendFunctionKey')<sup>10+</sup>

off(type: 'sendFunctionKey', callback?: (functionKey: FunctionKey) => void): void

Disables listening for the function key sending event of the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                        |
| -------- | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                               | Yes  | Listening type. The value is fixed at **'sendFunctionKey'**.|
| callback | (functionKey: [FunctionKey](#functionkey10)) => void | No  | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let onSendFunctionKey: Callback<inputMethod.FunctionKey> = (functionKey: inputMethod.FunctionKey): void => {
  console.info(`Succeeded in subscribing sendFunctionKey, functionKey: ${functionKey.enterKeyType}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('sendFunctionKey', onSendFunctionKey);
inputMethodController.off('sendFunctionKey');
```

### on('moveCursor')<sup>10+</sup>

on(type: 'moveCursor', callback: (direction: Direction) => void): void

Enables listening for the cursor movement event of the input method. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type| Mandatory| Description  |
| -------- | ------ | ---- | ------ |
| type     | string | Yes  | Listening type. The value is fixed at **'moveCursor'**.|
| callback | (direction: [Direction](#direction10)) => void | Yes  | Callback used to return the cursor movement direction.<br>The application needs to change the cursor position based on the cursor movement direction returned in the callback. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                          |
| -------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
inputMethod.getController().on('moveCursor', (direction: inputMethod.Direction) => {
  console.info(`Succeeded in subscribing moveCursor, direction: ${direction}`);
});
```

### off('moveCursor')<sup>10+</sup>

off(type: 'moveCursor', callback?: (direction: Direction) => void): void

Disables listening for the cursor movement event of the input method.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name | Type   | Mandatory| Description |
| ------ | ------ | ---- | ---- |
| type   | string | Yes  | Listening type. The value is fixed at **'moveCursor'**.|
| callback | (direction: [Direction](#direction10)) => void | No| Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let onMoveCursorCallback: Callback<inputMethod.Direction> = (direction: inputMethod.Direction): void => {
  console.info(`Succeeded in subscribing moveCursor, direction: ${direction}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('moveCursor', onMoveCursorCallback);
inputMethodController.off('moveCursor');
```

### on('handleExtendAction')<sup>10+</sup>

on(type: 'handleExtendAction', callback: (action: ExtendAction) => void): void

Enables listening for the extended action handling event of the input method. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type | Mandatory| Description  |
| -------- | ------ | ---- | -------- |
| type     | string    | Yes  | Listening type. The value is fixed at **'handleExtendAction'**.|
| callback | (action: [ExtendAction](#extendaction10)) => void | Yes  | Callback used to return the extended action type.<br>The application needs to perform operations based on the extended action type returned in the callback.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
inputMethod.getController().on('handleExtendAction', (action: inputMethod.ExtendAction) => {
  console.info(`Succeeded in subscribing handleExtendAction, action: ${action}`);
});
```

### off('handleExtendAction')<sup>10+</sup>

off(type: 'handleExtendAction', callback?: (action: ExtendAction) => void): void

Disables listening for the extended action handling event of the input method. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type  | Mandatory| Description |
| ------ | ------ | ---- | ------- |
| type   | string | Yes  | Listening type. The value is fixed at **'handleExtendAction'**.|
| callback | (action: [ExtendAction](#extendaction10)) => void | No| Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let onHandleExtendActionCallback: Callback<inputMethod.ExtendAction> = (action: inputMethod.ExtendAction): void => {
  console.info(`Succeeded in subscribing handleExtendAction, action: ${action}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('handleExtendAction', onHandleExtendActionCallback);
inputMethodController.off('handleExtendAction');
```

### on('selectByRange')<sup>10+</sup>

on(type: 'selectByRange', callback: Callback&lt;Range&gt;): void

Enables listening for the select-by-range event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type    | Mandatory| Description    |
| -------- | ---- | ---- | ------- |
| type     | string  | Yes  | Listening type. The value is fixed at **'selectByRange'**.|
| callback | Callback&lt;[Range](#range10)&gt; | Yes  | Callback used to return the range of the text to be selected.<br>The application needs to select the text based on the range returned in the callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**Example**

```ts
inputMethod.getController().on('selectByRange', (range: inputMethod.Range) => {
  console.info(`Succeeded in subscribing selectByRange: start: ${range.start} , end: ${range.end}`);
});
```

### off('selectByRange')<sup>10+</sup>

off(type: 'selectByRange', callback?:  Callback&lt;Range&gt;): void

Disables listening for the select-by-range event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                             | Mandatory| Description                                                        |
| -------- | --------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                            | Yes  | Listening type. The value is fixed at **'selectByRange'**.|
| callback | Callback&lt;[Range](#range10)&gt; | No  | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let onSelectByRangeCallback: Callback<inputMethod.Range> = (range: inputMethod.Range): void => {
  console.info(`Succeeded in subscribing selectByRange, start: ${range.start} , end: ${range.end}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('selectByRange', onSelectByRangeCallback);
inputMethodController.off('selectByRange');
```

### on('selectByMovement')<sup>10+</sup>

on(type: 'selectByMovement', callback: Callback&lt;Movement&gt;): void

Enables listening for the select-by-cursor-movement event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type  | Mandatory| Description    |
| -------- | ----- | ---- | ------ |
| type     | string  | Yes  | Listening type. The value is fixed at **'selectByMovement'**.|
| callback | Callback&lt;[Movement](#movement10)&gt; | Yes  | Callback used to return the direction in which the cursor moves.<br>The application needs to select the text based on the direction returned in the callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                               |
| -------- | ------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**Example**

```ts
inputMethod.getController().on('selectByMovement', (movement: inputMethod.Movement) => {
  console.info('Succeeded in subscribing selectByMovement: direction: ' + movement.direction);
});
```

### off('selectByMovement')<sup>10+</sup>

off(type: 'selectByMovement', callback?: Callback&lt;Movement&gt;): void

Disables listening for the select-by-cursor-movement event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                | Mandatory| Description                                                        |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                               | Yes  | Listening type. The value is fixed at **'selectByMovement'**.|
| callback | Callback&lt;[Movement](#movement10)> | No  | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let onSelectByMovementCallback: Callback<inputMethod.Movement> = (movement: inputMethod.Movement): void => {
  console.info(`Succeeded in subscribing selectByMovement, movement.direction: ${movement.direction}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('selectByMovement', onSelectByMovementCallback);
inputMethodController.off('selectByMovement');
```

### on('getLeftTextOfCursor')<sup>10+</sup>

on(type: 'getLeftTextOfCursor', callback: (length: number) => string): void

Enables listening for the event of obtaining the length of text deleted leftward. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type  | Mandatory| Description    |
| -------- | ----- | ---- | ------ |
| type     | string  | Yes  | Listening type. The value is fixed at **'getLeftTextOfCursor'**.|
| callback | (length: number) => string | Yes  | Callback used to obtain the text of the specified length deleted leftward.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
inputMethod.getController().on('getLeftTextOfCursor', (length: number) => {
  console.info(`Succeeded in subscribing getLeftTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
});
```

### off('getLeftTextOfCursor')<sup>10+</sup>

off(type: 'getLeftTextOfCursor', callback?: (length: number) => string): void

Disables listening for the event of obtaining the length of text deleted leftward. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| type   | string | Yes  | Listening type. The value is fixed at **'getLeftTextOfCursor'**.|
| callback | (length: number) => string | No | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
let getLeftTextOfCursorCallback: (length: number) => string = (length: number): string => {
  console.info(`Succeeded in unsubscribing getLeftTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('getLeftTextOfCursor', getLeftTextOfCursorCallback);
inputMethodController.off('getLeftTextOfCursor');
```

### on('getRightTextOfCursor')<sup>10+</sup>

on(type: 'getRightTextOfCursor', callback: (length: number) => string): void

Enables listening for the event of obtaining the length of text deleted rightward. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type  | Mandatory| Description    |
| -------- | ----- | ---- | ------ |
| type     | string  | Yes  | Listening type. The value is fixed at **'getRightTextOfCursor'**.|
| callback | (length: number) => string | Yes  | Callback used to obtain the text of the specified length deleted rightward.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
inputMethod.getController().on('getRightTextOfCursor', (length: number) => {
  console.info(`Succeeded in subscribing getRightTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
});
```

### off('getRightTextOfCursor')<sup>10+</sup>

off(type: 'getRightTextOfCursor', callback?: (length: number) => string): void

Disables listening for the event of obtaining the length of text deleted rightward. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| type   | string | Yes  | Listening type. The value is fixed at **'getRightTextOfCursor'**.|
| callback | (length: number) => string | No |Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
let getRightTextOfCursorCallback: (length: number) => string = (length: number): string => {
  console.info(`Succeeded in unsubscribing getRightTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('getRightTextOfCursor', getRightTextOfCursorCallback);
inputMethodController.off('getRightTextOfCursor');
```

### on('getTextIndexAtCursor')<sup>10+</sup>

on(type: 'getTextIndexAtCursor', callback: () => number): void

Enables listening for the event of obtaining the index of text at the cursor. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type  | Mandatory| Description    |
| -------- | ----- | ---- | ------ |
| type     | string  | Yes  | Listening type. The value is fixed at **'getTextIndexAtCursor'**.|
| callback | () => number | Yes  | Callback used to obtain the index of text at the cursor.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800009 | input method client detached. |

**Example**

```ts
inputMethod.getController().on('getTextIndexAtCursor', () => {
  console.info(`Succeeded in subscribing getTextIndexAtCursor.`);
  let index: number = 0;
  return index;
});
```

### off('getTextIndexAtCursor')<sup>10+</sup>

off(type: 'getTextIndexAtCursor', callback?: () => number): void

Disables listening for the event of obtaining the index of text at the cursor. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| type   | string | Yes  | Listening type. The value is fixed at **'getTextIndexAtCursor'**.|
| callback | () => number | No | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
let getTextIndexAtCursorCallback: () => number = (): number => {
  console.info(`Succeeded in unsubscribing getTextIndexAtCursor.`);
  let index: number = 0;
  return index;
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('getTextIndexAtCursor', getTextIndexAtCursorCallback);
inputMethodController.off('getTextIndexAtCursor');
```

### on('setPreviewText')<sup>17+</sup>

on(type: 'setPreviewText', callback: SetPreviewTextCallback): void

Subscribes to the event for text preview operations in an input method application. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> To use the text preview function, you need to subscribe to this event before calling [attach](#attach10) and subscribe to this event together with [on('finishTextPreview')](#onfinishtextpreview17).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type  | Mandatory| Description    |
| -------- | ----- | ---- | ------ |
| type     | string  | Yes  | Event type, which is **'setPreviewText'**.|
| callback | [SetPreviewTextCallback](#setpreviewtextcallback17) | Yes  | Callback used to return the result. It is used to receive and return the text preview.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**Example**

```ts
let setPreviewTextCallback1: inputMethod.SetPreviewTextCallback = (text: string, range: inputMethod.Range): void => {
  console.info(`SetPreviewTextCallback1: Received text - ${text}, Received range - start: ${range.start}, end: ${range.end}`);
};

let setPreviewTextCallback2: inputMethod.SetPreviewTextCallback = (text: string, range: inputMethod.Range): void => {
  console.info(`setPreviewTextCallback2: Received text - ${text}, Received range - start: ${range.start}, end: ${range.end}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.on('setPreviewText', setPreviewTextCallback1);
console.info(`SetPreviewTextCallback1 subscribed to setPreviewText`);
inputMethodController.on('setPreviewText', setPreviewTextCallback2);
console.info(`SetPreviewTextCallback2 subscribed to setPreviewText`);
// Cancel only the callback1 of setPreviewText.
inputMethodController.off('setPreviewText', setPreviewTextCallback1);
console.info(`SetPreviewTextCallback1 unsubscribed from setPreviewText`);
// Cancel all callbacks of setPreviewText.
inputMethodController.off('setPreviewText');
console.info(`All callbacks unsubscribed from setPreviewText`);
```

### off('setPreviewText')<sup>17+</sup>

off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void

Unsubscribes from the event for text preview operations in an input method application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| type   | string | Yes  | Event type, which is **'setPreviewText'**.|
| callback | [SetPreviewTextCallback](#setpreviewtextcallback17) | No | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
let setPreviewTextCallback1: inputMethod.SetPreviewTextCallback = (text: string, range: inputMethod.Range): void => {
  console.info(`SetPreviewTextCallback1: Received text - ${text}, Received range - start: ${range.start}, end: ${range.end}`);
};

let setPreviewTextCallback2: inputMethod.SetPreviewTextCallback = (text: string, range: inputMethod.Range): void => {
  console.info(`setPreviewTextCallback2: Received text - ${text}, Received range - start: ${range.start}, end: ${range.end}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.on('setPreviewText', setPreviewTextCallback1);
console.info(`SetPreviewTextCallback1 subscribed to setPreviewText`);
inputMethodController.on('setPreviewText', setPreviewTextCallback2);
console.info(`SetPreviewTextCallback2 subscribed to setPreviewText`);
// Cancel only the callback1 of setPreviewText.
inputMethodController.off('setPreviewText', setPreviewTextCallback1);
console.info(`SetPreviewTextCallback1 unsubscribed from setPreviewText`);
// Cancel all callbacks of setPreviewText.
inputMethodController.off('setPreviewText');
console.info(`All callbacks unsubscribed from setPreviewText`);
```

### on('finishTextPreview')<sup>17+</sup>

on(type: 'finishTextPreview', callback: Callback&lt;void&gt;): void

Subscribes to the event of finishing text preview. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> To use the text preview function, you need to subscribe to this event before calling [attach](#attach10) and subscribe to this event together with [on('setPreviewText')](#onsetpreviewtext17).

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type  | Mandatory| Description    |
| -------- | ----- | ---- | ------ |
| type     | string  | Yes  | Event type, which is **'finishTextPreview'**.|
| callback | Callback&lt;void&gt; | Yes  | Callback used to return the result. It is used to process the logic of finishing text preview. Return type: void|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let finishTextPreviewCallback1: Callback<void> = (): void => {
  console.info(`FinishTextPreviewCallback1: finishTextPreview event triggered`);
};
let finishTextPreviewCallback2: Callback<void> = (): void => {
  console.info(`FinishTextPreviewCallback2: finishTextPreview event triggered`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.on('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 subscribed to finishTextPreview`);
inputMethodController.on('finishTextPreview', finishTextPreviewCallback2);
console.info(`FinishTextPreviewCallback2 subscribed to finishTextPreview`);
// Cancel only the callback1 of finishTextPreview.
inputMethodController.off('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 unsubscribed from finishTextPreview`);
// Cancel all callbacks of finishTextPreview.
inputMethodController.off('finishTextPreview');
console.info(`All callbacks unsubscribed from finishTextPreview`);
```

### off('finishTextPreview')<sup>17+</sup>

off(type: 'finishTextPreview', callback?: Callback&lt;void&gt;): void

Unsubscribes from the event of finishing text preview. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| type   | string | Yes  | Event type, which is **'finishTextPreview'**.|
| callback | Callback&lt;void&gt; | No | Callback used to disable listening, which must be the same as that passed by the **on** API.<br>If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let finishTextPreviewCallback1: Callback<void> = (): void => {
  console.info(`FinishTextPreviewCallback1: finishTextPreview event triggered`);
};
let finishTextPreviewCallback2: Callback<void> = (): void => {
  console.info(`FinishTextPreviewCallback2: finishTextPreview event triggered`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.on('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 subscribed to finishTextPreview`);
inputMethodController.on('finishTextPreview', finishTextPreviewCallback2);
console.info(`FinishTextPreviewCallback2 subscribed to finishTextPreview`);
// Cancel only the callback1 of finishTextPreview.
inputMethodController.off('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 unsubscribed from finishTextPreview`);
// Cancel all callbacks of finishTextPreview.
inputMethodController.off('finishTextPreview');
console.info(`All callbacks unsubscribed from finishTextPreview`);
```

## InputMethodSetting<sup>8+</sup>

**InputMethodSetting** provides input method configuration and query capabilities, and offers the following features for foreground applications:

- Input method change subscription: subscribe to input method and subtype change events through [on('imeChange')](#onimechange9), and receive a notification when the user switches the input method.
- Input method list query: query the list of enabled/disabled input methods through [getInputMethods](#getinputmethods9), query the list of all installed input methods through [getAllInputMethods](js-apis-inputmethod.md#getallinputmethods11), and query the subtype list of a specified input method through [listInputMethodSubtype](#listinputmethodsubtype9).
- Panel visibility query: query whether the input method panel is displayed through **isPanelShown**.
- Input method selection dialog: display the input method selection dialog through **showOptionalInputMethods** (deprecated; **InputMethodListDialog** is recommended).

It must be used after you obtain the **InputMethodSetting** instance through [getSetting](#inputmethodgetsetting9).

For the following APIs, you must first use [getSetting](#inputmethodgetsetting9) to obtain an **InputMethodSetting** instance, and then call the APIs using the obtained instance.

### on('imeChange')<sup>9+</sup>

on(type: 'imeChange', callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void

Enables listening for the input method and subtype change event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                           | Mandatory| Description                                                        |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                        | Yes  | Listening type. The value is fixed at **'imeChange'**.|
| callback | (inputMethodProperty: [InputMethodProperty](#inputmethodproperty8), inputMethodSubtype: [InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)) => void  | Yes| Callback used to return the input method attributes and subtype.|

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';

inputMethod.getSetting()
  .on('imeChange', (inputMethodProperty: inputMethod.InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => {
    console.info(`Succeeded in subscribing imeChange: inputMethodProperty.name: ${inputMethodProperty.name} ` +
      `, inputMethodSubtype.id: ${inputMethodSubtype.id}`);
  });
```

### off('imeChange')<sup>9+</sup>

off(type: 'imeChange', callback?: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void): void

Disables listening for the input method and subtype change event. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type   | Mandatory| Description         |
| -------- | --------- | ---- | --------------- |
| type     | string    | Yes  | Listening type. The value is fixed at **'imeChange'**.|
| callback | (inputMethodProperty: [InputMethodProperty](#inputmethodproperty8), inputMethodSubtype: [InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)) => void  | No| Callback used to return the input method attributes and subtype.|

**Example**

```ts
inputMethod.getSetting().off('imeChange');
```

### listInputMethodSubtype<sup>9+</sup>

listInputMethodSubtype(inputMethodProperty: InputMethodProperty, callback: AsyncCallback&lt;Array&lt;InputMethodSubtype&gt;&gt;): void

Obtains all subtypes of a specified input method. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                              | Mandatory| Description                  |
| -------- | -------------------------------------------------- | ---- | ---------------------- |
| inputMethodProperty | [InputMethodProperty](#inputmethodproperty8)| Yes| Input method.|
| callback | AsyncCallback&lt;Array<[InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)>&gt; | Yes| Callback used to return all subtypes of the specified input method.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800001 | bundle manager error.                 |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodProperty: inputMethod.InputMethodProperty = {
  name: 'com.example.keyboard',
  id: 'propertyId',
  packageName: 'com.example.keyboard',
  methodId: 'propertyId'
}
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();

inputMethodSetting.listInputMethodSubtype(inputMethodProperty,
  (err: BusinessError, data: Array<InputMethodSubtype>) => {
    if (err) {
      console.error(`Failed to listInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in listing inputMethodSubtype.');
  });
```

### listInputMethodSubtype<sup>9+</sup>

listInputMethodSubtype(inputMethodProperty: InputMethodProperty): Promise&lt;Array&lt;InputMethodSubtype&gt;&gt;

Obtains all subtypes of a specified input method. This API uses a promise to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                              | Mandatory| Description                  |
| -------- | -------------------------------------------------- | ---- | ---------------------- |
| inputMethodProperty | [InputMethodProperty](#inputmethodproperty8)| Yes| Input method.|

**Return value**

| Type                                                       | Description                  |
| ----------------------------------------------------------- | ---------------------- |
| Promise&lt;Array&lt;[InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)&gt;&gt; | Promise object, which returns all subtypes of the specified input method application. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800001 | bundle manager error.                 |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodProperty: inputMethod.InputMethodProperty = {
  name: 'com.example.keyboard',
  id: 'propertyId',
  packageName: 'com.example.keyboard',
  methodId: 'propertyId'
}
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();

inputMethodSetting.listInputMethodSubtype(inputMethodProperty).then((data: Array<InputMethodSubtype>) => {
  console.info('Succeeded in listing inputMethodSubtype.');
}).catch((err: BusinessError) => {
  console.error(`Failed to listInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
})
```

### listCurrentInputMethodSubtype<sup>9+</sup>

listCurrentInputMethodSubtype(callback: AsyncCallback&lt;Array&lt;InputMethodSubtype&gt;&gt;): void

Obtains all subtypes of this input method. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                              | Mandatory| Description                  |
| -------- | -------------------------------------------------- | ---- | ---------------------- |
| callback | AsyncCallback&lt;Array<[InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)>&gt; | Yes  | Callback used to return all subtypes of the current input method.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800001 | bundle manager error.                 |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();
inputMethodSetting.listCurrentInputMethodSubtype((err: BusinessError, data: Array<InputMethodSubtype>) => {
  if (err) {
    console.error(`Failed to listCurrentInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in listing currentInputMethodSubtype.');
});
```

### listCurrentInputMethodSubtype<sup>9+</sup>

listCurrentInputMethodSubtype(): Promise&lt;Array&lt;InputMethodSubtype&gt;&gt;

Obtains all subtypes of this input method. This API uses a promise to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                                       | Description                  |
| ----------------------------------------------------------- | ---------------------- |
| Promise&lt;Array&lt;[InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)&gt;&gt;| Promise object, which returns all subtypes of the current input method application. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800001 | bundle manager error.                 |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();

inputMethodSetting.listCurrentInputMethodSubtype().then((data: Array<InputMethodSubtype>) => {
  console.info('Succeeded in listing currentInputMethodSubtype.');
}).catch((err: BusinessError) => {
  console.error(`Failed to listCurrentInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
})

```

### getInputMethods<sup>9+</sup>

getInputMethods(enable: boolean, callback: AsyncCallback&lt;Array&lt;InputMethodProperty&gt;&gt;): void

Obtains a list of activated or deactivated input methods. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> An activated input method refers to an input method that is enabled. The default input method is enabled by default. Other input methods can be enabled or disabled as needed.
> 
> The list of activated input methods includes the default input method and enabled input methods. The list of deactivated input methods includes all installed input methods except the enabled ones.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                               | Mandatory| Description                         |
| -------- | --------------------------------------------------- | ---- | ----------------------------- |
| enable   | boolean                                             | Yes  |Whether to return a list of activated input methods. The value **true** means to return a list of activated input methods, and **false** means to return a list of deactivated input methods.|
| callback | AsyncCallback&lt;Array<[InputMethodProperty](#inputmethodproperty8)>&gt; |  Yes | Callback used to return a list of activated or deactivated input methods.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800001 | bundle manager error.               |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getInputMethods(true, (err: BusinessError, data: Array<inputMethod.InputMethodProperty>) => {
  if (err) {
    console.error(`Failed to getInputMethods, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting inputMethods.');
});
```

### getInputMethods<sup>9+</sup>

getInputMethods(enable: boolean): Promise&lt;Array&lt;InputMethodProperty&gt;&gt;

Obtains a list of activated or deactivated input methods. This API uses a promise to return the result.

> **NOTE**
> 
> An activated input method refers to an input method that is enabled. The default input method is enabled by default. Other input methods can be enabled or disabled as needed.
> 
> The list of activated input methods includes the default input method and enabled input methods. The list of deactivated input methods includes all installed input methods except the enabled ones.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type   | Mandatory| Description                   |
| ------ | ------- | ---- | ----------------------- |
| enable | boolean | Yes  |Whether to return a list of activated input methods. The value **true** means to return a list of activated input methods, and **false** means to return a list of deactivated input methods.|

**Return value**

| Type                                                        | Description                                      |
| ------------------------------------------------------------ | ------------------------------------------ |
| Promise&lt;Array&lt;[InputMethodProperty](#inputmethodproperty8)&gt;&gt; | Promise object, returns the list of activated/inactivated input methods. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800001 | bundle manager error.               |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getInputMethods(true).then((data: Array<inputMethod.InputMethodProperty>) => {
  console.info('Succeeded in getting inputMethods.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getInputMethods, code: ${err.code}, message: ${err.message}`);
})

```

### getInputMethodsSync<sup>11+</sup>

getInputMethodsSync(enable: boolean): Array&lt;InputMethodProperty&gt;

Obtains a list of activated or deactivated input methods. This API returns the result synchronously.

> **NOTE**
>
> The synchronous API blocks the main thread and may easily affect UI interaction. Use it with caution.
>
> Enabled input methods are input method applications that are enabled. The default input method is enabled by default, and other input methods can be set to enabled or disabled.
>
> The enabled input method list includes the default input method and input method applications that have been set to enabled. The disabled input method list includes other installed input methods except the enabled input methods.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type   | Mandatory| Description                   |
| ------ | ------- | ---- | ----------------------- |
| enable | boolean | Yes  |Whether to return a list of activated input methods. The value **true** means to return a list of activated input methods, and **false** means to return a list of deactivated input methods.|

**Return value**

| Type                                                | Description                         |
| ---------------------------------------------------- | ----------------------------- |
| Array\<[InputMethodProperty](#inputmethodproperty8)> | List of activated or deactivated input methods.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800001 | bundle manager error.                 |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getInputMethodsSync(true);
```

### getAllInputMethods<sup>11+</sup>

getAllInputMethods(callback: AsyncCallback&lt;Array&lt;InputMethodProperty&gt;&gt;): void

Obtains a list of all input methods. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                                        | Mandatory| Description                          |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | AsyncCallback&lt;Array<[InputMethodProperty](#inputmethodproperty8)>&gt; | Yes  | Callback used to return a list of all input methods.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 12800001 | bundle manager error.               |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getAllInputMethods((err: BusinessError, data: Array<inputMethod.InputMethodProperty>) => {
  if (err) {
    console.error(`Failed to getAllInputMethods, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting all inputMethods.');
});
```

### getAllInputMethods<sup>11+</sup>

getAllInputMethods(): Promise&lt;Array&lt;InputMethodProperty&gt;&gt;

Obtains a list of all input methods. This API uses a promise to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                                        | Description                             |
| ------------------------------------------------------------ | --------------------------------- |
| Promise&lt;Array&lt;[InputMethodProperty](#inputmethodproperty8)&gt;&gt; | Promise object, returns the list of all input methods. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 12800001 | bundle manager error.              |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getAllInputMethods().then((data: Array<inputMethod.InputMethodProperty>) => {
  console.info('Succeeded in getting all inputMethods.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getAllInputMethods, code: ${err.code}, message: ${err.message}`);
})
```

### getAllInputMethodsSync<sup>11+</sup>

getAllInputMethodsSync(): Array&lt;InputMethodProperty&gt;

Obtains a list of all input methods. This API returns the result synchronously.

> **NOTE**
>
> The synchronous API blocks the main thread and may easily affect UI interaction. Use it with caution.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                                | Description              |
| ---------------------------------------------------- | ------------------ |
| Array\<[InputMethodProperty](#inputmethodproperty8)> | List of all input methods.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 12800001 | bundle manager error.              |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getAllInputMethodsSync();
```

### showOptionalInputMethods<sup>(deprecated)</sup>

showOptionalInputMethods(callback: AsyncCallback&lt;boolean&gt;): void

Displays a dialog box for selecting an input method. This API uses an asynchronous callback to return the result.
> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [InputMethodListDialog](js-apis-inputmethodlist.md#inputmethodlistdialog) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().showOptionalInputMethods((err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to showOptionalInputMethods, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in showing optionalInputMethods.');
  } else {
    console.error(`Failed to showOptionalInputMethods.`);
  }
});
```

### showOptionalInputMethods<sup>(deprecated)</sup>

showOptionalInputMethods(): Promise&lt;boolean&gt;

Displays a dialog box for selecting an input method. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 18. You are advised to use [InputMethodListDialog](js-apis-inputmethodlist.md#inputmethodlistdialog) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise object. Returns **true** if the input method selection dialog is displayed successfully, and **false** otherwise. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().showOptionalInputMethods().then((result: boolean) => {
  if (result) {
    console.info('Succeeded in showing optionalInputMethods.');
  } else {
    console.error(`Failed to showOptionalInputMethods.`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to showOptionalInputMethods, code: ${err.code}, message: ${err.message}`);
})
```

### listInputMethod<sup>(deprecated)</sup>

listInputMethod(callback: AsyncCallback&lt;Array&lt;InputMethodProperty&gt;&gt;): void

Obtains a list of installed input methods. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [getInputMethods](#getinputmethods9) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type                                              | Mandatory| Description                  |
| -------- | -------------------------------------------------- | ---- | ---------------------- |
| callback | AsyncCallback&lt;Array<[InputMethodProperty](#inputmethodproperty8)>&gt; | Yes  | Callback used to return the list of installed input methods.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().listInputMethod((err: BusinessError, data: Array<inputMethod.InputMethodProperty>) => {
  if (err) {
    console.error(`Failed to listInputMethod, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in listing inputMethod.');
});
```

### listInputMethod<sup>(deprecated)</sup>

listInputMethod(): Promise&lt;Array&lt;InputMethodProperty&gt;&gt;

Obtains a list of installed input methods. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [getInputMethods](#getinputmethods9-1) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                                       | Description                  |
| ----------------------------------------------------------- | ---------------------- |
| Promise&lt;Array&lt;[InputMethodProperty](#inputmethodproperty8)&gt;&gt; | Promise object, which returns the list of installed input methods. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().listInputMethod().then((data: Array<inputMethod.InputMethodProperty>) => {
  console.info('Succeeded in listing inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to listInputMethod, code: ${err.code}, message: ${err.message}`);
})
```

### displayOptionalInputMethod<sup>(deprecated)</sup>

displayOptionalInputMethod(callback: AsyncCallback&lt;void&gt;): void

Displays a dialog box for selecting an input method. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [InputMethodListDialog](js-apis-inputmethodlist.md#inputmethodlistdialog) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().displayOptionalInputMethod((err: BusinessError) => {
  if (err) {
    console.error(`Failed to displayOptionalInputMethod, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in displaying optionalInputMethod.');
});
```

### displayOptionalInputMethod<sup>(deprecated)</sup>

displayOptionalInputMethod(): Promise&lt;void&gt;

Displays a dialog box for selecting an input method. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [InputMethodListDialog](js-apis-inputmethodlist.md#inputmethodlistdialog) instead.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().displayOptionalInputMethod().then(() => {
  console.info('Succeeded in displaying optionalInputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to displayOptionalInputMethod, code: ${err.code}, message: ${err.message}`);
})
```

### getInputMethodState<sup>15+</sup>

getInputMethodState(): Promise&lt;EnabledState&gt;

Obtains the input method state. This API uses a promise to return the result.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type                                   | Description                                                        |
| --------------------------------------- | ------------------------------------------------------------ |
| Promise&lt;[EnabledState](#enabledstate15)&gt; | Promise object. Returns **EnabledState.DISABLED** if the input method is not enabled; returns **EnabledState.BASIC_MODE** if in basic mode; returns **EnabledState.FULL_EXPERIENCE_MODE** if in full experience mode. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 12800004 | not an input method application.    |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getInputMethodState().then((status: inputMethod.EnabledState) => {
  console.info(`Succeeded in getInputMethodState, status: ${status}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getInputMethodState, code: ${err.code}, message: ${err.message}`);
});
```