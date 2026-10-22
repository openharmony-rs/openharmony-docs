# InputMethodController

```TypeScript
interface InputMethodController
```

In the following API examples, you must first use [getController](arkts-ime-inputmethod-getcontroller-f.md) to obtain an **InputMethodController** instance, and then call the APIs using the obtained instance. <br> <br>**InputMethodController** is the input method client controller, which provides foreground applications with core capabilities for interacting with the input method. After obtaining an instance through `inputMethod.getController()`, you can perform the following operations: <br> <br>- Attachment management: Use [attach](#attach-1) to establish attachment to the input method, and use [detach](#detach-1) to perform detachment. **attach** and **detach** must be used in pairs. <br>- Keyboard control: Use [showTextInput](#showtextinput-1) to start the soft keyboard and enter the editing state, and use [hideTextInput](#hidetextinput-1) to hide the soft keyboard and exit the editing state. **showTextInput** and **hideTextInput** must be used in pairs. <br>- Edit box state synchronization: Use APIs such as [updateCursor](#updatecursor-1), <br> <br>[changeSelection](#changeselection), and [updateAttribute](#updateattribute-1) to synchronize edit box state information such as the cursor, selection, and attributes with the input method. <br>- Event subscription: Use APIs such as **on('insertText')** and **on('deleteLeft')** to subscribe to text operation events sent by the input method application. <br> <br>Typical call sequence: `getController()` → `attach()` → `showTextInput()`/`hideTextInput()` → `detach()` <br> <br>  
> **NOTE:** <br>
> <br>
> **attach** and **detach** must be used in pairs, and **showTextInput** and **hideTextInput** must be used in <br>
> pairs. Otherwise, resource leaks or inconsistent states may occur.

**Since:** 6

<!--Device-inputMethod-interface InputMethodController--><!--Device-inputMethod-interface InputMethodController-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## attach

```TypeScript
attach(showKeyboard: boolean, textConfig: TextConfig, callback: AsyncCallback<void>): void
```

Attaches a self-drawn component to the input method. This API uses an asynchronous callback to return the result. <br> <br>Meaning/Function: Establishes attachment between a self-drawn control and the input method application. This is the prerequisite for a self-drawn control to use input method features. <br> <br>Usage scenarios: When a self-drawn control (not a system native edit box) needs to interact with the input method, this API must be called first to establish attachment. When a native edit box gains focus, the system performs attachment automatically, and there is no need to call this API. <br> <br>Use effect: After the attachment succeeds, the self-drawn control can call **showTextInput**\/**hideTextInput** to control the keyboard visibility, and call **updateCursor**\/**changeSelection** to synchronize the edit box state, subscribe to input method events, and implement more features. <br> <br>Preconditions: The window where the self-drawn control resides must be in the focused state; otherwise, the attachment fails. <br> <br>Usage with related APIs: **attach** must be used in pairs with **detach**. Only after **attach** is called can APIs such as **showTextInput**, **hideTextInput**, and **updateCursor** be called. <br> <br>Differences between similar APIs and selection principles: <br> <br>- **attach**: does not require passing in a UIContext, and is applicable to self-drawn control attachment scenarios of API version 10 and later. <br>- **attachWithUIContext**: requires passing in a UIContext, and is applicable to stage model scenarios of API version 23 and later, supporting more attachment options. <br>- Selection principle: For stage model applications of API version 23 and later, use **attachWithUIContext** first to obtain more complete attachment option support. <br> <br>  
> **NOTE:** <br>
> <br>
> An input method can use the following features only when it has a self-drawn component attached to it: showing <br>
> or hiding the keyboard, updating the cursor information, changing the selection range of the edit box, saving <br>
> the configuration information, and listening for and processing information or commands sent by the input <br>
> method. <br>
> <br>
> If the window where the self-drawn component is located is set to be non-focusable via <br>
> [setWindowFocusable](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md#setwindowfocusable-2), <br>
> the system cannot guarantee proper interaction between the self-drawing input component and the input method. <br>
> If you want to draw an input box in a non-focusable window, refer to <br>
> [Input Box and Input Method Interaction in Non-Focusable Windows](../../../inputmethod/use-inputmethod-in-not-focusable-window.md).

**Since:** 10

<!--Device-InputMethodController-attach(showKeyboard: boolean, textConfig: TextConfig, callback: AsyncCallback<void>): void--><!--Device-InputMethodController-attach(showKeyboard: boolean, textConfig: TextConfig, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| showKeyboard | boolean | Yes | Whether to show the input method keyboard after the input method is bound. <br> - true: show the keyboard. <br> - false: do not show the keyboard. |
| textConfig | [TextConfig](arkts-ime-inputmethod-textconfig-i.md) | Yes | Configuration information of the text box. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the input method is bound successfully, err is undefined; otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
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

## attach

```TypeScript
attach(showKeyboard: boolean, textConfig: TextConfig): Promise<void>
```

Attaches a self-drawn component to the input method. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> An input method can use the following features only when it has a self-drawn component attached to it: showing <br>
> or hiding the keyboard, updating the cursor information, changing the selection range of the edit box, saving <br>
> the configuration information, and listening for and processing information or commands sent by the input <br>
> method. <br>
> <br>
> If the window where the self-drawn component is located is set to be non-focusable via <br>
> [setWindowFocusable](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md#setwindowfocusable-2), <br>
> the system cannot guarantee proper interaction between the self-drawing input component and the input method. <br>
> If you want to draw an input box in a non-focusable window, refer to <br>
> [Input Box and Input Method Interaction in Non-Focusable Windows](../../../inputmethod/use-inputmethod-in-not-focusable-window.md).

**Since:** 10

<!--Device-InputMethodController-attach(showKeyboard: boolean, textConfig: TextConfig): Promise<void>--><!--Device-InputMethodController-attach(showKeyboard: boolean, textConfig: TextConfig): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| showKeyboard | boolean | Yes | Whether to show the input method keyboard after the input method is bound successfully. <br> - **true**: Show the keyboard. <br> - **false**: Do not show the keyboard. |
| textConfig | [TextConfig](arkts-ime-inputmethod-textconfig-i.md) | Yes | Configuration information of the text box. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
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

## attach

```TypeScript
attach(showKeyboard: boolean, textConfig: TextConfig, requestKeyboardReason: RequestKeyboardReason): Promise<void>
```

Attaches a self-drawn component to the input method. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> An input method can use the following features only when it has a self-drawn component attached to it: showing <br>
> or hiding the keyboard, updating the cursor information, changing the selection range of the edit box, saving <br>
> the configuration information, and listening for and processing information or commands sent by the input <br>
> method. <br>
> <br>
> If the window where the self-drawn component is located is set to be non-focusable via <br>
> [setWindowFocusable](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md#setwindowfocusable-2), <br>
> the system cannot guarantee proper interaction between the self-drawing input component and the input method. <br>
> If you want to draw an input box in a non-focusable window, refer to <br>
> [Input Box and Input Method Interaction in Non-Focusable Windows](../../../inputmethod/use-inputmethod-in-not-focusable-window.md).

**Since:** 15

<!--Device-InputMethodController-attach(showKeyboard: boolean, textConfig: TextConfig, requestKeyboardReason: RequestKeyboardReason): Promise<void>--><!--Device-InputMethodController-attach(showKeyboard: boolean, textConfig: TextConfig, requestKeyboardReason: RequestKeyboardReason): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| showKeyboard | boolean | Yes | Whether to show the input method keyboard after the input method is bound successfully. <br> - **true**: Show the keyboard. <br> - **false**: Do not show the keyboard. |
| textConfig | [TextConfig](arkts-ime-inputmethod-textconfig-i.md) | Yes | Configuration information of the text box. |
| requestKeyboardReason | [RequestKeyboardReason](arkts-ime-inputmethod-requestkeyboardreason-e.md) | Yes | Reason for requesting keyboard input. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
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

## attachWithUIContext

```TypeScript
attachWithUIContext(uiContext: UIContext, textConfig: TextConfig, attachOptions?: AttachOptions): Promise<void>
```

Attaches a self-drawn component to the input method. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> An input method can use the following features only when it has a self-drawn component attached to it: showing <br>
> or hiding the keyboard, updating the cursor information, changing the selection range of the edit box, saving <br>
> the configuration information, and listening for and processing the information or commands sent by the input <br>
> method.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodController-attachWithUIContext(uiContext: UIContext, textConfig: TextConfig, attachOptions?: AttachOptions): Promise<void>--><!--Device-InputMethodController-attachWithUIContext(uiContext: UIContext, textConfig: TextConfig, attachOptions?: AttachOptions): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | UIContext instance. |
| textConfig | [TextConfig](arkts-ime-inputmethod-textconfig-i.md) | Yes | Configuration information of the text box. |
| attachOptions | [AttachOptions](arkts-ime-inputmethod-attachoptions-i.md) | No | Additional options for attaching. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
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

## changeSelection

```TypeScript
changeSelection(text: string, start: number, end: number, callback: AsyncCallback<void>): void
```

Updates the information about the selected text in this edit box, to notify the input method when the selected text content or text range changes. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called to update the text selection information only after the edit box is attached to the <br>
> input method.

**Since:** 10

<!--Device-InputMethodController-changeSelection(text: string, start: int, end: int, callback: AsyncCallback<void>): void--><!--Device-InputMethodController-changeSelection(text: string, start: int, end: int, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Entire input text. |
| start | number | Yes | Start position of the selected text. This parameter must be an integer greater than or equal to 0. |
| end | number | Yes | End position of the selected text. This parameter must be an integer greater than or equal to 0. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. If the text information is updated successfully, err is undefined; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().changeSelection('text', 0, 5, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to changeSelection, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in changing selection.');
});
```

## changeSelection

```TypeScript
changeSelection(text: string, start: number, end: number): Promise<void>
```

Updates the information about the selected text in this edit box, to notify the input method when the selected text content or text range changes. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called to update the text selection information only after the edit box is attached to the <br>
> input method.

**Since:** 10

<!--Device-InputMethodController-changeSelection(text: string, start: int, end: int): Promise<void>--><!--Device-InputMethodController-changeSelection(text: string, start: int, end: int): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Entire input text. |
| start | number | Yes | Start position of the selected text. This parameter must be an integer greater than or equal to 0. |
| end | number | Yes | End position of the selected text. This parameter must be an integer greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().changeSelection('test', 0, 5).then(() => {
  console.info('Succeeded in changing selection.');
}).catch((err: BusinessError) => {
  console.error(`Failed to changeSelection, code: ${err.code}, message: ${err.message}`);
});
```

## detach

```TypeScript
detach(callback: AsyncCallback<void>): void
```

Detaches the self-drawn component from the input method. This API uses an asynchronous callback to return the result. <br> <br>Meaning/Function: Detaches the self-drawn control from the input method application and releases related resources. <br> <br>Usage scenarios: Called when the self-drawn control no longer needs to interact with the input method (for example, page switching, edit box destruction, etc.). <br> <br>Use effect: After detachment, APIs that require the attached state, such as **showTextInput**, **hideTextInput**, and **updateCursor**, can no longer be called. The input method soft keyboard will be hidden. <br> <br>Usage with related APIs: **detach** must be used in pairs with **attach**. It is recommended that you call **detach** after **hideTextInput**. The complete flow is: **attach** → **showTextInput** → **hideTextInput** → **detach**.

**Since:** 10

<!--Device-InputMethodController-detach(callback: AsyncCallback<void>): void--><!--Device-InputMethodController-detach(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. When the input method is unbound successfully, err is undefined; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().detach((err: BusinessError) => {
  if (err) {
    console.error(`Failed to detach, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in detaching inputMethod.');
});
```

## detach

```TypeScript
detach(): Promise<void>
```

Detaches the self-drawn component from the input method. This API uses a promise to return the result. <br> <br>Meaning/Function: Detaches the self-drawn control from the input method application and releases related resources. <br> <br>Usage scenarios: Called when the self-drawn control no longer needs to interact with the input method. <br> <br>Use effect: After detachment, APIs that require the attached state can no longer be called. The input method soft keyboard will be hidden. <br> <br>Usage with related APIs: **detach** must be used in pairs with **attach**.

**Since:** 10

<!--Device-InputMethodController-detach(): Promise<void>--><!--Device-InputMethodController-detach(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().detach().then(() => {
  console.info('Succeeded in detaching inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to detach, code: ${err.code}, message: ${err.message}`);
});
```

## discardTypingText

```TypeScript
discardTypingText(): Promise<void>
```

Discards the text that is being typed. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called after the edit box is attached to an input method.

**Since:** 20

<!--Device-InputMethodController-discardTypingText(): Promise<void>--><!--Device-InputMethodController-discardTypingText(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |
| [12800015](../errorcode-inputmethod-framework.md#12800015-message-receiver-unable-to-receive-custom-communication-data) | the other side does not accept the request. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().discardTypingText().then(() => {
  console.info('Succeeded discardTypingText.');
}).catch((err: BusinessError) => {
  console.error(`Failed to discardTypingText, code: ${err.code}, message: ${err.message}`);
});
```

## hideSoftKeyboard

```TypeScript
hideSoftKeyboard(callback: AsyncCallback<void>): void
```

Hides the soft keyboard. This API uses an asynchronous callback to return the result. <br> <br>Meaning/Function: Forcibly hides the soft keyboard of the current input method. <br> <br>Usage scenarios: Used when a system application needs to forcibly hide the input method soft keyboard. <br> <br>Use effect: The input method soft keyboard is hidden. <br> <br>Preconditions: This API can be called only when the edit box is attached to the input method. <br> <br>Differences between similar APIs and selection principles: <br> <br>- **hideSoftKeyboard**: for system applications, requires the **ohos.permission.CONNECT_IME_ABILITY** permission, and only hides the keyboard without exiting the editing state. <br>- **hideTextInput**: for self-drawn controls, hides the keyboard and exits the editing state, and can re-enter the editing state by calling **showTextInput** again. <br>- Selection principle: self-drawn controls use **hideTextInput**; system applications with the required permission use **hideSoftKeyboard**. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the text box is attached to the input method. That is, it can be called to <br>
> hide the soft keyboard only when the text box is focused.

**Since:** 9

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

<!--Device-InputMethodController-hideSoftKeyboard(callback: AsyncCallback<void>): void--><!--Device-InputMethodController-hideSoftKeyboard(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the soft keyboard is hidden successfully, err is undefined. Otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideSoftKeyboard((err: BusinessError) => {
  if (!err) {
    console.info('Succeeded in hiding softKeyboard.');
  } else {
    console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
  }
})
```

## hideSoftKeyboard

```TypeScript
hideSoftKeyboard(): Promise<void>
```

Hides the soft keyboard. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to <br>
> hide the soft keyboard only when the edit box is focused.

**Since:** 9

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

<!--Device-InputMethodController-hideSoftKeyboard(): Promise<void>--><!--Device-InputMethodController-hideSoftKeyboard(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideSoftKeyboard().then(() => {
  console.info('Succeeded in hiding softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

## hideTextInput

```TypeScript
hideTextInput(callback: AsyncCallback<void>): void
```

Exits the text editing mode. This API uses an asynchronous callback to return the result. <br> <br>Meaning/Function: Hides the soft keyboard and makes the edit box exit the text editing state. <br> <br>Usage scenarios: Called when a self-drawn control no longer needs input, for example, when the user taps an area outside the edit box or switches to another page. <br> <br>Use effect: The soft keyboard is hidden, and the edit box exits the editing state. Calling this API does not unbind the input method. Calling **showTextInput** again can re-enter the editing state. <br> <br>Preconditions: Call [attach](#attach-1) to complete the attachment first, and call **showTextInput** to enter the editing state. <br> <br>Usage with related APIs: **hideTextInput** and **showTextInput** must be used in pairs. If input is needed again after **hideTextInput** is called, you must call **showTextInput** first to re-enter the editing state; other editing operations cannot be called directly. <br> <br>Differences between similar APIs and selection principles: <br> <br>- **hideTextInput**: For self-drawn controls, exits the editing state without detachment, and can re-enter via **showTextInput**. It is suitable for scenarios where a self-drawn control needs to temporarily hide the keyboard. <br>- **hideSoftKeyboard**: For system applications, requires the **ohos.permission.CONNECT_IME_ABILITY** permission. It only hides the keyboard without changing the editing state. <br>- Selection principle: Self-drawn controls should preferentially use **hideTextInput**; system applications with special requirements should use **hideSoftKeyboard**. <br> <br>  
> **NOTE:** <br>
> <br>
> If the soft keyboard is displayed when this API is called, it will be hidden. <br>
> <br>
> Calling this API does not detach the edit box from the input method. The edit box can call <br>
> [showTextInput](#showtextinput-1) again to <br>
> reenter the text editing mode.

**Since:** 10

<!--Device-InputMethodController-hideTextInput(callback: AsyncCallback<void>): void--><!--Device-InputMethodController-hideTextInput(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideTextInput((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hideTextInput, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding text input.');
});
```

## hideTextInput

```TypeScript
hideTextInput(): Promise<void>
```

Exits the text editing mode. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> If the soft keyboard is displayed when this API is called, it will be hidden. <br>
> <br>
> Calling this API does not detach the edit box from the input method. The edit box can call <br>
> [showTextInput](#showtextinput-1) again to <br>
> reenter the text editing mode.

**Since:** 10

<!--Device-InputMethodController-hideTextInput(): Promise<void>--><!--Device-InputMethodController-hideTextInput(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideTextInput().then(() => {
  console.info('Succeeded in hiding inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hideTextInput, code: ${err.code}, message: ${err.message}`);
})
```

## off('selectByRange')

```TypeScript
off(type: 'selectByRange', callback?: Callback<Range>): void
```

Disables listening for the select-by-range event. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-off(type: 'selectByRange', callback?: Callback<Range>): void--><!--Device-InputMethodController-off(type: 'selectByRange', callback?: Callback<Range>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'selectByRange' | Yes | Sets the listening type. The value is fixed at 'selectByRange'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Range](arkts-ime-inputmethod-range-i.md)&gt; | No | Callback function to unsubscribe from. It must be the same as the one passed to the on API. If this parameter is not specified, all callback events corresponding to the type are unsubscribed from. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onSelectByRangeCallback: Callback<inputMethod.Range> = (range: inputMethod.Range): void => {
  console.info(`Succeeded in subscribing selectByRange, start: ${range.start} , end: ${range.end}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('selectByRange', onSelectByRangeCallback);
inputMethodController.off('selectByRange');
```

## off('selectByMovement')

```TypeScript
off(type: 'selectByMovement', callback?: Callback<Movement>): void
```

Disables listening for the select-by-cursor-movement event. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-off(type: 'selectByMovement', callback?: Callback<Movement>): void--><!--Device-InputMethodController-off(type: 'selectByMovement', callback?: Callback<Movement>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'selectByMovement' | Yes | Sets the listening type. The value is fixed to 'selectByMovement'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Movement](arkts-ime-inputmethod-movement-i.md)&gt; | No | Callback to unsubscribe. It must be the same as the one passed in the on API. If this parameter is not specified, all callback events corresponding to the type are unsubscribed. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onSelectByMovementCallback: Callback<inputMethod.Movement> = (movement: inputMethod.Movement): void => {
  console.info(`Succeeded in subscribing selectByMovement, movement.direction: ${movement.direction}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('selectByMovement', onSelectByMovementCallback);
inputMethodController.off('selectByMovement');
```

## off('insertText')

```TypeScript
off(type: 'insertText', callback?: (text: string) => void): void
```

Disables listening for the text insertion event of the input method.

**Since:** 10

<!--Device-InputMethodController-off(type: 'insertText', callback?: (text: string) => void): void--><!--Device-InputMethodController-off(type: 'insertText', callback?: (text: string) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'insertText' | Yes | Sets the listening type. The value is fixed to 'insertText'. |
| callback | (text: string) =&gt; void | No | Callback function to unsubscribe from. It must be the same as the one passed to the on API.<br>If this parameter is not specified, all callback events corresponding to the type are unsubscribed from. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onInsertTextCallback: Callback<string> = (text: string): void => {
  console.info(`Succeeded in subscribing insertText: ${text}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('insertText', onInsertTextCallback);
inputMethodController.off('insertText');
```

## off('deleteLeft')

```TypeScript
off(type: 'deleteLeft', callback?: (length: number) => void): void
```

Disables listening for the leftward delete event.

**Since:** 10

<!--Device-InputMethodController-off(type: 'deleteLeft', callback?: (length: number) => void): void--><!--Device-InputMethodController-off(type: 'deleteLeft', callback?: (length: number) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deleteLeft' | Yes | Sets the listener. The value is fixed to 'deleteLeft'. |
| callback | (length: number) =&gt; void | No | Callback function to unsubscribe from. It must be the same as the one passed to the on API. If this parameter is not specified, all callback events corresponding to type are unsubscribed from. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onDeleteLeftCallback: Callback<number> = (length: number): void => {
  console.info(`Succeeded in subscribing deleteLeft, length: ${length}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('deleteLeft', onDeleteLeftCallback);
inputMethodController.off('deleteLeft');
```

## off('deleteRight')

```TypeScript
off(type: 'deleteRight', callback?: (length: number) => void): void
```

Disables listening for the rightward delete event.

**Since:** 10

<!--Device-InputMethodController-off(type: 'deleteRight', callback?: (length: number) => void): void--><!--Device-InputMethodController-off(type: 'deleteRight', callback?: (length: number) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deleteRight' | Yes | Listening type. The value is fixed to `deleteRight`. |
| callback | (length: number) =&gt; void | No | Callback function to unsubscribe. It must be the same as the one passed to the on API. If this parameter is not specified, all callback events corresponding to the type are unsubscribed. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onDeleteRightCallback: Callback<number> = (length: number): void => {
  console.info(`Succeeded in subscribing deleteRight, length: ${length}`);
};
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('deleteRight', onDeleteRightCallback);
inputMethodController.off('deleteRight');
```

## off('sendKeyboardStatus')

```TypeScript
off(type: 'sendKeyboardStatus', callback?: (keyboardStatus: KeyboardStatus) => void): void
```

Disables listening for the input method soft keyboard status event of the input method.

**Since:** 10

<!--Device-InputMethodController-off(type: 'sendKeyboardStatus', callback?: (keyboardStatus: KeyboardStatus) => void): void--><!--Device-InputMethodController-off(type: 'sendKeyboardStatus', callback?: (keyboardStatus: KeyboardStatus) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sendKeyboardStatus' | Yes | Sets the listening type. The value is fixed to 'sendKeyboardStatus'. |
| callback | (keyboardStatus: KeyboardStatus) =&gt; void | No | Callback function to unsubscribe from. If this parameter is not specified, all callback events corresponding to the type are unsubscribed from. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onSendKeyboardStatus: Callback<inputMethod.KeyboardStatus> = (keyboardStatus: inputMethod.KeyboardStatus): void => {
  console.info(`Succeeded in subscribing sendKeyboardStatus, keyboardStatus: ${keyboardStatus}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('sendKeyboardStatus', onSendKeyboardStatus);
inputMethodController.off('sendKeyboardStatus');
```

## off('sendFunctionKey')

```TypeScript
off(type: 'sendFunctionKey', callback?: (functionKey: FunctionKey) => void): void
```

Disables listening for the function key sending event of the input method.

**Since:** 10

<!--Device-InputMethodController-off(type: 'sendFunctionKey', callback?: (functionKey: FunctionKey) => void): void--><!--Device-InputMethodController-off(type: 'sendFunctionKey', callback?: (functionKey: FunctionKey) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sendFunctionKey' | Yes | Sets the listening type, which is fixed to 'sendFunctionKey'. |
| callback | (functionKey: FunctionKey) =&gt; void | No | Callback function to unsubscribe from. It must be the same as the one passed in the on interface. If this parameter is not specified, all callback events corresponding to the type are unsubscribed from. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onSendFunctionKey: Callback<inputMethod.FunctionKey> = (functionKey: inputMethod.FunctionKey): void => {
  console.info(`Succeeded in subscribing sendFunctionKey, functionKey: ${functionKey.enterKeyType}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('sendFunctionKey', onSendFunctionKey);
inputMethodController.off('sendFunctionKey');
```

## off('moveCursor')

```TypeScript
off(type: 'moveCursor', callback?: (direction: Direction) => void): void
```

Disables listening for the cursor movement event of the input method.

**Since:** 10

<!--Device-InputMethodController-off(type: 'moveCursor', callback?: (direction: Direction) => void): void--><!--Device-InputMethodController-off(type: 'moveCursor', callback?: (direction: Direction) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'moveCursor' | Yes | Type of the listener to set. The value is fixed at 'moveCursor'. |
| callback | (direction: Direction) =&gt; void | No | Callback function to unsubscribe from. It must be the same as the one passed to the on API. If this parameter is not specified, all callback events corresponding to the type are unsubscribed from. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onMoveCursorCallback: Callback<inputMethod.Direction> = (direction: inputMethod.Direction): void => {
  console.info(`Succeeded in subscribing moveCursor, direction: ${direction}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('moveCursor', onMoveCursorCallback);
inputMethodController.off('moveCursor');
```

## off('handleExtendAction')

```TypeScript
off(type: 'handleExtendAction', callback?: (action: ExtendAction) => void): void
```

Disables listening for the extended action handling event of the input method. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-off(type: 'handleExtendAction', callback?: (action: ExtendAction) => void): void--><!--Device-InputMethodController-off(type: 'handleExtendAction', callback?: (action: ExtendAction) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'handleExtendAction' | Yes | Sets the listening type. The value is fixed at 'handleExtendAction'. |
| callback | (action: ExtendAction) =&gt; void | No | Callback function to unsubscribe. It must be the same as the one passed to the on API. If this parameter is not specified, all callback events corresponding to the type are unsubscribed. |

**Examples**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onHandleExtendActionCallback: Callback<inputMethod.ExtendAction> = (action: inputMethod.ExtendAction): void => {
  console.info(`Succeeded in subscribing handleExtendAction, action: ${action}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('handleExtendAction', onHandleExtendActionCallback);
inputMethodController.off('handleExtendAction');
```

## off('getLeftTextOfCursor')

```TypeScript
off(type: 'getLeftTextOfCursor', callback?: (length: number) => string): void
```

Disables listening for the event of obtaining the length of text deleted leftward. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-off(type: 'getLeftTextOfCursor', callback?: (length: number) => string): void--><!--Device-InputMethodController-off(type: 'getLeftTextOfCursor', callback?: (length: number) => string): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'getLeftTextOfCursor' | Yes | Sets the listening type. The value is fixed to 'getLeftTextOfCursor'. |
| callback | (length: number) =&gt; string | No | Callback function to unsubscribe from. It must be the same as the one passed to the on API. If this parameter is not specified, all callback events corresponding to the type are unsubscribed from. |

**Examples**

```TypeScript
let getLeftTextOfCursorCallback: (length: number) => string = (length: number): string => {
  console.info(`Succeeded in unsubscribing getLeftTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('getLeftTextOfCursor', getLeftTextOfCursorCallback);
inputMethodController.off('getLeftTextOfCursor');
```

## off('getRightTextOfCursor')

```TypeScript
off(type: 'getRightTextOfCursor', callback?: (length: number) => string): void
```

Disables listening for the event of obtaining the length of text deleted rightward. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-off(type: 'getRightTextOfCursor', callback?: (length: number) => string): void--><!--Device-InputMethodController-off(type: 'getRightTextOfCursor', callback?: (length: number) => string): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'getRightTextOfCursor' | Yes | Sets the listening type. The value is fixed to 'getRightTextOfCursor'. |
| callback | (length: number) =&gt; string | No | Callback function to unsubscribe from. It must be the same as the one passed to the on API. If this parameter is not specified, all callback events corresponding to the type are unsubscribed from. |

**Examples**

```TypeScript
let getRightTextOfCursorCallback: (length: number) => string = (length: number): string => {
  console.info(`Succeeded in unsubscribing getRightTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('getRightTextOfCursor', getRightTextOfCursorCallback);
inputMethodController.off('getRightTextOfCursor');
```

## off('getTextIndexAtCursor')

```TypeScript
off(type: 'getTextIndexAtCursor', callback?: () => number): void
```

Disables listening for the event of obtaining the index of text at the cursor. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-off(type: 'getTextIndexAtCursor', callback?: () => number): void--><!--Device-InputMethodController-off(type: 'getTextIndexAtCursor', callback?: () => number): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'getTextIndexAtCursor' | Yes | Type of the listener to set. The value is fixed to 'getTextIndexAtCursor'. |
| callback | () =&gt; number | No | Callback function to unsubscribe from. It must be the same as the one passed to the on API. If this parameter is not specified, all callback events corresponding to the type are unsubscribed from. |

**Examples**

```TypeScript
let getTextIndexAtCursorCallback: () => number = (): number => {
  console.info(`Succeeded in unsubscribing getTextIndexAtCursor.`);
  let index: number = 0;
  return index;
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('getTextIndexAtCursor', getTextIndexAtCursorCallback);
inputMethodController.off('getTextIndexAtCursor');
```

## off('setPreviewText')

```TypeScript
off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void
```

Unsubscribes from the event for text preview operations in an input method application. This API uses an asynchronous callback to return the result.

**Since:** 17

<!--Device-InputMethodController-off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void--><!--Device-InputMethodController-off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'setPreviewText' | Yes | Listening type. The value is fixed at 'setPreviewText'. |
| callback | [SetPreviewTextCallback](arkts-ime-inputmethod-setpreviewtextcallback-t.md) | No | Callback function to unsubscribe from. It must be the same as the one passed in the on API. If this parameter is not specified, all callback events of the corresponding type are unsubscribed from. |

**Examples**

```TypeScript
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
// Unsubscribe only from the callback1 of setPreviewText.
inputMethodController.off('setPreviewText', setPreviewTextCallback1);
console.info(`SetPreviewTextCallback1 unsubscribed from setPreviewText`);
// Unsubscribe from all callbacks of setPreviewText.
inputMethodController.off('setPreviewText');
console.info(`All callbacks unsubscribed from setPreviewText`);
```

## off('finishTextPreview')

```TypeScript
off(type: 'finishTextPreview', callback?: Callback<void>): void
```

Unsubscribes from the event of finishing text preview. This API uses an asynchronous callback to return the result.

**Since:** 17

<!--Device-InputMethodController-off(type: 'finishTextPreview', callback?: Callback<void>): void--><!--Device-InputMethodController-off(type: 'finishTextPreview', callback?: Callback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'finishTextPreview' | Yes | Sets the listening type. The value is fixed at 'finishTextPreview'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback function to unsubscribe from. It must be the same as the one passed in the on API. If this parameter is not specified, all callback events corresponding to the type are unsubscribed from. |

**Examples**

```TypeScript
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
// Unsubscribe only from the callback1 of finishTextPreview.
inputMethodController.off('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 unsubscribed from finishTextPreview`);
// Unsubscribe from all callbacks of finishTextPreview.
inputMethodController.off('finishTextPreview');
console.info(`All callbacks unsubscribed from finishTextPreview`);
```

## on('selectByRange')

```TypeScript
on(type: 'selectByRange', callback: Callback<Range>): void
```

Enables listening for the select-by-range event. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'selectByRange', callback: Callback<Range>): void--><!--Device-InputMethodController-on(type: 'selectByRange', callback: Callback<Range>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'selectByRange' | Yes | Type of the listener to set. The value is fixed at 'selectByRange'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Range](arkts-ime-inputmethod-range-i.md)&gt; | Yes | Callback used to return the text range to be selected.Based on the returned text range, the developer selects the corresponding text in the text box in the callback function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
inputMethod.getController().on('selectByRange', (range: inputMethod.Range) => {
  console.info(`Succeeded in subscribing selectByRange: start: ${range.start} , end: ${range.end}`);
});
```

## on('selectByMovement')

```TypeScript
on(type: 'selectByMovement', callback: Callback<Movement>): void
```

Enables listening for the select-by-cursor-movement event. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'selectByMovement', callback: Callback<Movement>): void--><!--Device-InputMethodController-on(type: 'selectByMovement', callback: Callback<Movement>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'selectByMovement' | Yes | Type of the listener to set. The value is fixed at 'selectByMovement'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Movement](arkts-ime-inputmethod-movement-i.md)&gt; | Yes | Callback used to return the direction of cursor movement.Selects the corresponding text in the text box based on the passed cursor movement direction. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Examples**

```TypeScript
inputMethod.getController().on('selectByMovement', (movement: inputMethod.Movement) => {
  console.info('Succeeded in subscribing selectByMovement: direction: ' + movement.direction);
});
```

## on('insertText')

```TypeScript
on(type: 'insertText', callback: (text: string) => void): void
```

Enables listening for the text insertion event of the input method. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'insertText', callback: (text: string) => void): void--><!--Device-InputMethodController-on(type: 'insertText', callback: (text: string) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'insertText' | Yes | Sets the listening type. The value is fixed to 'insertText'. |
| callback | (text: string) =&gt; void | Yes | Callback function that returns the text content to be inserted.Operate on the content in the text box based on the passed-in text. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
const callback1 = (text: string): void => {
  console.info(`Succeeded in getting callback1, data: ${text}`);
}

const callback2 = (text: string): void => {
  console.info(`Succeeded in getting callback2, data: ${text}`);
}

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
// Register the callback.
inputMethodController.on('insertText', callback1);
inputMethodController.on('insertText', callback2);
// Cancel only the callback of callback1 for insertText.
inputMethodController.off('insertText', callback1);
// Cancel all callbacks for insertText.
inputMethodController.off('insertText');
```

## on('deleteLeft')

```TypeScript
on(type: 'deleteLeft', callback: (length: number) => void): void
```

Enables listening for the leftward delete event. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'deleteLeft', callback: (length: number) => void): void--><!--Device-InputMethodController-on(type: 'deleteLeft', callback: (length: number) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deleteLeft' | Yes | Sets the listening type. The value is fixed to 'deleteLeft'. |
| callback | (length: number) =&gt; void | Yes | Callback function, which returns the length of text to be deleted to the left.<br/ <br> &gt;Based on the passed deletion length, operates on the text in the text box in the callback function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
inputMethod.getController().on('deleteLeft', (length: number) => {
  console.info(`Succeeded in subscribing deleteLeft, length: ${length}`);
});
```

## on('deleteRight')

```TypeScript
on(type: 'deleteRight', callback: (length: number) => void): void
```

Enables listening for the rightward delete event. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'deleteRight', callback: (length: number) => void): void--><!--Device-InputMethodController-on(type: 'deleteRight', callback: (length: number) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deleteRight' | Yes | Type of the listener to set. The value is fixed at 'deleteRight'. |
| callback | (length: number) =&gt; void | Yes | Callback used to return the length of text to be deleted to the right.Based on the returned deletion length, operate the text in the text box in the callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
inputMethod.getController().on('deleteRight', (length: number) => {
  console.info(`Succeeded in subscribing deleteRight, length: ${length}`);
});
```

## on('sendKeyboardStatus')

```TypeScript
on(type: 'sendKeyboardStatus', callback: (keyboardStatus: KeyboardStatus) => void): void
```

Enables listening for the soft keyboard status event of the input method. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'sendKeyboardStatus', callback: (keyboardStatus: KeyboardStatus) => void): void--><!--Device-InputMethodController-on(type: 'sendKeyboardStatus', callback: (keyboardStatus: KeyboardStatus) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sendKeyboardStatus' | Yes | Type of the listener to set. The value is fixed at 'sendKeyboardStatus'. |
| callback | (keyboardStatus: KeyboardStatus) =&gt; void | Yes | Callback used to return the soft keyboard status.Perform the corresponding operation in the callback based on the returned soft keyboard status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
inputMethod.getController().on('sendKeyboardStatus', (keyboardStatus: inputMethod.KeyboardStatus) => {
  console.info(`Succeeded in subscribing sendKeyboardStatus, keyboardStatus: ${keyboardStatus}`);
});
```

## on('sendFunctionKey')

```TypeScript
on(type: 'sendFunctionKey', callback: (functionKey: FunctionKey) => void): void
```

Enables listening for the function key sending event of the input method. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'sendFunctionKey', callback: (functionKey: FunctionKey) => void): void--><!--Device-InputMethodController-on(type: 'sendFunctionKey', callback: (functionKey: FunctionKey) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sendFunctionKey' | Yes | Sets the listening type. The value is fixed to 'sendFunctionKey'. |
| callback | (functionKey: FunctionKey) =&gt; void | Yes | Callback used to return the function key information sent by the input method application.<br>Performs the corresponding operation based on the returned function key information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
inputMethod.getController().on('sendFunctionKey', (functionKey: inputMethod.FunctionKey) => {
  console.info(`Succeeded in subscribing sendFunctionKey, functionKey.enterKeyType: ${functionKey.enterKeyType}`);
});
```

## on('moveCursor')

```TypeScript
on(type: 'moveCursor', callback: (direction: Direction) => void): void
```

Enables listening for the cursor movement event of the input method. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'moveCursor', callback: (direction: Direction) => void): void--><!--Device-InputMethodController-on(type: 'moveCursor', callback: (direction: Direction) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'moveCursor' | Yes | Type of the listener to set. The value is fixed at 'moveCursor'. |
| callback | (direction: Direction) =&gt; void | Yes | Callback used to return the cursor information.Changes the cursor position based on the returned cursor movement direction, for example, moving the cursor up or down. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
inputMethod.getController().on('moveCursor', (direction: inputMethod.Direction) => {
  console.info(`Succeeded in subscribing moveCursor, direction: ${direction}`);
});
```

## on('handleExtendAction')

```TypeScript
on(type: 'handleExtendAction', callback: (action: ExtendAction) => void): void
```

Enables listening for the extended action handling event of the input method. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'handleExtendAction', callback: (action: ExtendAction) => void): void--><!--Device-InputMethodController-on(type: 'handleExtendAction', callback: (action: ExtendAction) => void): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'handleExtendAction' | Yes | Type of the listener to set. The value is fixed at 'handleExtendAction'. |
| callback | (action: ExtendAction) =&gt; void | Yes | Callback used to return the extended editing operation type.Performs the corresponding operation, such as cut or copy, based on the passed extended editing operation type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
inputMethod.getController().on('handleExtendAction', (action: inputMethod.ExtendAction) => {
  console.info(`Succeeded in subscribing handleExtendAction, action: ${action}`);
});
```

## on('getLeftTextOfCursor')

```TypeScript
on(type: 'getLeftTextOfCursor', callback: (length: number) => string): void
```

Enables listening for the event of obtaining the length of text deleted leftward. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'getLeftTextOfCursor', callback: (length: number) => string): void--><!--Device-InputMethodController-on(type: 'getLeftTextOfCursor', callback: (length: number) => string): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'getLeftTextOfCursor' | Yes | Type of the listener to set. The value is fixed at 'getLeftTextOfCursor'. |
| callback | (length: number) =&gt; string | Yes | Callback used to obtain and return the text content of the specified length to the left of the cursor in the latest state of the text box. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
inputMethod.getController().on('getLeftTextOfCursor', (length: number) => {
  console.info(`Succeeded in subscribing getLeftTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
});
```

## on('getRightTextOfCursor')

```TypeScript
on(type: 'getRightTextOfCursor', callback: (length: number) => string): void
```

Enables listening for the event of obtaining the length of text deleted rightward. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'getRightTextOfCursor', callback: (length: number) => string): void--><!--Device-InputMethodController-on(type: 'getRightTextOfCursor', callback: (length: number) => string): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'getRightTextOfCursor' | Yes | Sets the listening type. The value is fixed to 'getRightTextOfCursor'. |
| callback | (length: number) =&gt; string | Yes | Callback function that obtains and returns the text content of the specified length to the right of the cursor in the latest state of the text box. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
inputMethod.getController().on('getRightTextOfCursor', (length: number) => {
  console.info(`Succeeded in subscribing getRightTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
});
```

## on('getTextIndexAtCursor')

```TypeScript
on(type: 'getTextIndexAtCursor', callback: () => number): void
```

Enables listening for the event of obtaining the index of text at the cursor. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-on(type: 'getTextIndexAtCursor', callback: () => number): void--><!--Device-InputMethodController-on(type: 'getTextIndexAtCursor', callback: () => number): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'getTextIndexAtCursor' | Yes | Type of the listener to set. The value is fixed at 'getTextIndexAtCursor'. |
| callback | () =&gt; number | Yes | Callback used to obtain and return the text index at the cursor in the latest state of the text box. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
inputMethod.getController().on('getTextIndexAtCursor', () => {
  console.info(`Succeeded in subscribing getTextIndexAtCursor.`);
  let index: number = 0;
  return index;
});
```

## on('setPreviewText')

```TypeScript
on(type: 'setPreviewText', callback: SetPreviewTextCallback): void
```

Subscribes to the event for text preview operations in an input method application. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> To use the text preview function, you need to subscribe to this event before calling <br>
> [attach](#attach-1) <br>
> and subscribe to this event together with <br>
> [on('finishTextPreview')](#onfinishtextpreview).

**Since:** 17

<!--Device-InputMethodController-on(type: 'setPreviewText', callback: SetPreviewTextCallback): void--><!--Device-InputMethodController-on(type: 'setPreviewText', callback: SetPreviewTextCallback): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'setPreviewText' | Yes | Type of the listener to set. The value is fixed at 'setPreviewText'. |
| callback | [SetPreviewTextCallback](arkts-ime-inputmethod-setpreviewtextcallback-t.md) | Yes | Callback used to receive the preview text content and return it. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
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

## on('finishTextPreview')

```TypeScript
on(type: 'finishTextPreview', callback: Callback<void>): void
```

Subscribes to the event of finishing text preview. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> To use the text preview function, you need to subscribe to this event before calling <br>
> [attach](#attach-1) <br>
> and subscribe to this event together with <br>
> [on('setPreviewText')](#onsetpreviewtext).

**Since:** 17

<!--Device-InputMethodController-on(type: 'finishTextPreview', callback: Callback<void>): void--><!--Device-InputMethodController-on(type: 'finishTextPreview', callback: Callback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'finishTextPreview' | Yes | Type of the listener to set. The value is fixed at 'finishTextPreview'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback function. When the logic for finishing preview text processing succeeds, err is undefined; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
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
// Unsubscribe only the callback1 of finishTextPreview.
inputMethodController.off('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 unsubscribed from finishTextPreview`);
// Unsubscribe all callbacks of finishTextPreview.
inputMethodController.off('finishTextPreview');
console.info(`All callbacks unsubscribed from finishTextPreview`);
```

## recvMessage

```TypeScript
recvMessage(msgHandler?: MessageHandler): void
```

Registers or unregisters MessageHandler. <br> <br>  
> **NOTE:** <br>
> <br>
> The [MessageHandler](arkts-ime-inputmethod-messagehandler-i.md) object is globally unique. After multiple registrations, <br>
> only the last registered object is valid and retained, and the <br>
> [onTerminated](arkts-ime-inputmethod-messagehandler-i.md#onterminated) callback of the penultimate registered object <br>
> is triggered. <br>
> <br>
> If no parameter is set, unregister [MessageHandler](arkts-ime-inputmethod-messagehandler-i.md). Its <br>
> [onTerminated](arkts-ime-inputmethod-messagehandler-i.md#onterminated) callback will be triggered.

**Since:** 15

<!--Device-InputMethodController-recvMessage(msgHandler?: MessageHandler): void--><!--Device-InputMethodController-recvMessage(msgHandler?: MessageHandler): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| msgHandler | [MessageHandler](arkts-ime-inputmethod-messagehandler-i.md) | No | This object receives custom communication data from the input method application through [onMessage](arkts-ime-inputmethod-messagehandler-i.md#onmessage-2) and receives a message for terminating the subscription to this object through [onTerminated](arkts-ime-inputmethod-messagehandler-i.md#onterminated). If no parameter is set, unregister [MessageHandler](arkts-ime-inputmethod-messagehandler-i.md). Its [onTerminated](arkts-ime-inputmethod-messagehandler-i.md#onterminated) callback will be triggered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |

**Examples**

```TypeScript
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
// Unregister the registered MessageHandler.
inputMethodController.recvMessage();
```

## sendMessage

```TypeScript
sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise<void>
```

Sends the custom communication to the input method application. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the edit box is attached to the input method and enters the edit mode, and the <br>
> input method application is in full experience mode. <br>
> <br>
> The maximum length of **msgId** is 256 B, and the maximum length of **msgParam** is 128 KB.

**Since:** 15

<!--Device-InputMethodController-sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise<void>--><!--Device-InputMethodController-sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| msgId | string | Yes | Identifier of the custom data to be sent to the input method application. |
| msgParam | ArrayBuffer | No | Message body of the custom data to be sent to the input method application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Incorrect parameter length. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |
| [12800014](../errorcode-inputmethod-framework.md#12800014-non-full-access-mode-of-the-input-method-application) | the input method is in basic mode. |
| [12800015](../errorcode-inputmethod-framework.md#12800015-message-receiver-unable-to-receive-custom-communication-data) | the other side does not accept the request. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-input-method-client-not-in-edit-mode) | input method client is not editable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let msgId: string = "testMsgId";
let msgParam: ArrayBuffer = new ArrayBuffer(128);
inputMethod.getController().sendMessage(msgId, msgParam).then(() => {
  console.info('Succeeded send message.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send message, code: ${err.code}, message: ${err.message}`);
});
```

## setCallingWindow

```TypeScript
setCallingWindow(windowId: number, callback: AsyncCallback<void>): void
```

Sets the window to be avoided by the input method. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called to set the window that avoids the soft keyboard only after the edit box is attached to <br>
> the input method. <br>
> <br>
> Pass in the window ID of the application attached to the input method. This window can avoid the input method <br>
> window.

**Since:** 10

<!--Device-InputMethodController-setCallingWindow(windowId: int, callback: AsyncCallback<void>): void--><!--Device-InputMethodController-setCallingWindow(windowId: int, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | Window ID of the application attached to the input method. This parameter must be an integer. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. If the setting is successful, err is undefined; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
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

## setCallingWindow

```TypeScript
setCallingWindow(windowId: number): Promise<void>
```

Sets the window to avoid the soft keyboard. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> After the window ID of the application bound to the input method is passed in the API, the input method window <br>
> will not cover the window holding the application.

**Since:** 10

<!--Device-InputMethodController-setCallingWindow(windowId: int): Promise<void>--><!--Device-InputMethodController-setCallingWindow(windowId: int): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| windowId | number | Yes | ID of the window holding the application bound to the input method application. The value must be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowId: number = 2000;
inputMethod.getController().setCallingWindow(windowId).then(() => {
  console.info('Succeeded in setting callingWindow.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setCallingWindow, code: ${err.code}, message: ${err.message}`);
});
```

## showSoftKeyboard

```TypeScript
showSoftKeyboard(callback: AsyncCallback<void>): void
```

Shows the soft keyboard. This API uses an asynchronous callback to return the result. <br> <br>Meaning/Function: Forcibly displays the soft keyboard of the current input method. <br> <br>Usage scenarios: Used when a system application needs to forcibly display the input method soft keyboard (for example, a Settings application testing an input method). <br> <br>Use effect: The input method soft keyboard is displayed. <br> <br>Preconditions: This API can be called only when the edit box is attached to the input method. <br> <br>Differences between similar APIs and selection principles: <br> <br>- **showSoftKeyboard**: for system applications, requires the **ohos.permission.CONNECT_IME_ABILITY** permission, and only displays the keyboard without changing the editing state. <br>- **showTextInput**: for self-drawn controls, requires attachment first, and pulls up the keyboard and enters the editing state. <br>- Selection principle: use **showTextInput** for self-drawn controls; use **showSoftKeyboard** for system applications with the required permission. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the text box is bound to the input method. That is, it can be called to show <br>
> the soft keyboard of the current input method only when the text box is focused.

**Since:** 9

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

<!--Device-InputMethodController-showSoftKeyboard(callback: AsyncCallback<void>): void--><!--Device-InputMethodController-showSoftKeyboard(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the soft keyboard is displayed successfully, err is undefined. Otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showSoftKeyboard((err: BusinessError) => {
  if (!err) {
    console.info('Succeeded in showing softKeyboard.');
  } else {
    console.error(`Failed to show softKeyboard, ${err.code}, message: ${err.message}`);
  }
});
```

## showSoftKeyboard

```TypeScript
showSoftKeyboard(): Promise<void>
```

Shows the soft keyboard. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to <br>
> show the soft keyboard only when the edit box is focused.

**Since:** 9

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

<!--Device-InputMethodController-showSoftKeyboard(): Promise<void>--><!--Device-InputMethodController-showSoftKeyboard(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showSoftKeyboard().then(() => {
  console.info('Succeeded in showing softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

## showTextInput

```TypeScript
showTextInput(callback: AsyncCallback<void>): void
```

Enters the text editing mode. This API uses an asynchronous callback to return the result. <br> <br>Meaning/Function: Pulls up the soft keyboard and puts the edit box into the text editing state. <br> <br>Usage scenarios: Called when a self-drawn control needs to display the soft keyboard to start text input after being attached to the input method. <br> <br>Use effect: The soft keyboard is displayed, and the edit box enters the editable text input state. <br> <br>Preconditions: Call [attach](#attach-1) to complete the attachment first. Otherwise, error code 12800009 is reported. <br> <br>Usage with related APIs: **showTextInput** and **hideTextInput** must be used in pairs. After **hideTextInput** is called to exit the editing state, **showTextInput** must be called again to re-enter the editing state. <br> <br>Differences between similar APIs and selection principles: <br> <br>- **showTextInput**: For self-drawn controls. It must be called after **attach** completes the binding. It applies to self-drawn control scenarios and is the standard way to display the keyboard. <br>- **showSoftKeyboard**: For system applications. It requires the **ohos.permission.CONNECT_IME_ABILITY** permission. It applies to scenarios where a system application needs to forcibly display the keyboard. <br>- Selection principle: For self-drawn controls, use **showTextInput** preferentially. Use **showSoftKeyboard** only for system applications with special requirements. <br> <br>  
> **NOTE:** <br>
> <br>
> After the edit box is attached to an input method, this API can be called to start the soft keyboard and enter <br>
> the text editing state.

**Since:** 10

<!--Device-InputMethodController-showTextInput(callback: AsyncCallback<void>): void--><!--Device-InputMethodController-showTextInput(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. If the editing state is entered successfully, err is undefined; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showTextInput((err: BusinessError) => {
  if (err) {
    console.error(`Failed to showTextInput, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in showing the inputMethod.');
});
```

## showTextInput

```TypeScript
showTextInput(): Promise<void>
```

Enters the text editing mode. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> After the edit box is attached to an input method, this API can be called to start the soft keyboard and enter <br>
> the text editing state.

**Since:** 10

<!--Device-InputMethodController-showTextInput(): Promise<void>--><!--Device-InputMethodController-showTextInput(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showTextInput().then(() => {
  console.info('Succeeded in showing text input.');
}).catch((err: BusinessError) => {
  console.error(`Failed to showTextInput, code: ${err.code}, message: ${err.message}`);
});
```

## showTextInput

```TypeScript
showTextInput(requestKeyboardReason: RequestKeyboardReason): Promise<void>
```

Enters the text editing mode. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> After the edit box is attached to an input method, this API can be called to start the soft keyboard and enter <br>
> the text editing state.

**Since:** 15

<!--Device-InputMethodController-showTextInput(requestKeyboardReason: RequestKeyboardReason): Promise<void>--><!--Device-InputMethodController-showTextInput(requestKeyboardReason: RequestKeyboardReason): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestKeyboardReason | [RequestKeyboardReason](arkts-ime-inputmethod-requestkeyboardreason-e.md) | Yes | Reason for requesting keyboard input. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let requestKeyboardReason: inputMethod.RequestKeyboardReason = inputMethod.RequestKeyboardReason.MOUSE;

inputMethod.getController().showTextInput(requestKeyboardReason).then(() => {
  console.info('Succeeded in showing text input.');
}).catch((err: BusinessError) => {
  console.error(`Failed to showTextInput, code: ${err.code}, message: ${err.message}`);
});
```

## stopInputSession

```TypeScript
stopInputSession(callback: AsyncCallback<boolean>): void
```

Ends this input session. This API uses an asynchronous callback to return the result. <br> <br>Meaning/Function: Ends the current input session and hides the soft keyboard. <br> <br>Usage scenarios: Called when an application needs to proactively end the input session (for example, when the user has completed the input operation). <br> <br>Use effect: The soft keyboard is hidden and the input session ends. <br> <br>Preconditions: This API can be called only when the edit box is attached to the input method, that is, after the edit control is tapped. <br> <br>Usage with related APIs: **stopInputSession** hides the soft keyboard and ends the input session. If the **attach**\/**showTextInput**\/**hideTextInput**\/**detach** flow of a self-drawn control is used, it is recommended that you use **hideTextInput** instead of **stopInputSession**. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the text box is bound to the input method. That is, it can be called to end <br>
> the input session only when the text box is focused.

**Since:** 9

<!--Device-InputMethodController-stopInputSession(callback: AsyncCallback<boolean>): void--><!--Device-InputMethodController-stopInputSession(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the input session is ended successfully, err is undefined and data is true. Otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
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

## stopInputSession

```TypeScript
stopInputSession(): Promise<boolean>
```

Ends this input session. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to end <br>
> the input session only when the edit box is focused.

**Since:** 9

<!--Device-InputMethodController-stopInputSession(): Promise<boolean>--><!--Device-InputMethodController-stopInputSession(): Promise<boolean>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the input session is ended successfully, and **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
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

## updateAttribute

```TypeScript
updateAttribute(attribute: InputAttribute, callback: AsyncCallback<void>): void
```

Updates the attribute information of this edit box. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-InputMethodController-updateAttribute(attribute: InputAttribute, callback: AsyncCallback<void>): void--><!--Device-InputMethodController-updateAttribute(attribute: InputAttribute, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| attribute | [InputAttribute](arkts-ime-inputmethod-inputattribute-i.md) | Yes | Text box attribute object. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. When the text box attribute information is updated successfully, err is undefined; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
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

## updateAttribute

```TypeScript
updateAttribute(attribute: InputAttribute): Promise<void>
```

Updates the attribute information of this edit box. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called to update the text box attribute information only after the text box is attached to the <br>
> input method.

**Since:** 10

<!--Device-InputMethodController-updateAttribute(attribute: InputAttribute): Promise<void>--><!--Device-InputMethodController-updateAttribute(attribute: InputAttribute): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| attribute | [InputAttribute](arkts-ime-inputmethod-inputattribute-i.md) | Yes | Text box attribute object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = { textInputType: 0, enterKeyType: 1 };
inputMethod.getController().updateAttribute(inputAttribute).then(() => {
  console.info('Succeeded in updating attribute.');
}).catch((err: BusinessError) => {
  console.error(`Failed to updateAttribute, code: ${err.code}, message: ${err.message}`);
});
```

## updateCursor

```TypeScript
updateCursor(cursorInfo: CursorInfo, callback: AsyncCallback<void>): void
```

Updates the cursor information in this edit box. This API can be called to notify the input method of the cursor changes. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called to update the cursor information only after the edit box is attached to the input <br>
> method.

**Since:** 10

<!--Device-InputMethodController-updateCursor(cursorInfo: CursorInfo, callback: AsyncCallback<void>): void--><!--Device-InputMethodController-updateCursor(cursorInfo: CursorInfo, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cursorInfo | [CursorInfo](arkts-ime-inputmethod-cursorinfo-i.md) | Yes | Cursor information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. If the cursor information is updated successfully, err is undefined; otherwise, it is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
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

## updateCursor

```TypeScript
updateCursor(cursorInfo: CursorInfo): Promise<void>
```

Updates the cursor information in this edit box. This API can be called to notify the input method of the cursor changes. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called to update the cursor information only after the edit box is attached to the input <br>
> method.

**Since:** 10

<!--Device-InputMethodController-updateCursor(cursorInfo: CursorInfo): Promise<void>--><!--Device-InputMethodController-updateCursor(cursorInfo: CursorInfo): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cursorInfo | [CursorInfo](arkts-ime-inputmethod-cursorinfo-i.md) | Yes | Cursor information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-input-method-client-detached) | input method client detached. |

**Examples**

```TypeScript
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

## stopInput

```TypeScript
stopInput(callback: AsyncCallback<boolean>): void
```

Ends this input session. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to end <br>
> the input session only when the edit box is focused.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [stopInputSession](#stopinputsession)

<!--Device-InputMethodController-stopInput(callback: AsyncCallback<boolean>): void--><!--Device-InputMethodController-stopInput(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback function. When the session ends successfully, err is undefined and data is true; otherwise, it is an error object. |

**Examples**

```TypeScript
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

## stopInput

```TypeScript
stopInput(): Promise<boolean>
```

Ends this input session. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to end <br>
> the input session only when the edit box is focused.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [stopInputSession](#stopinputsession)

<!--Device-InputMethodController-stopInput(): Promise<boolean>--><!--Device-InputMethodController-stopInput(): Promise<boolean>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the operation is successful, and **false** means the opposite. |

**Examples**

```TypeScript
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
