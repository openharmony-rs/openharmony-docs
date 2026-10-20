# InputMethodController

```TypeScript
interface InputMethodController
```

In the following API examples, you must first use [getController](arkts-ime-inputmethod-getcontroller-f.md) to obtain an **InputMethodController** instance, and then call the APIs using the obtained instance. <br> <br>**InputMethodController** is the input method client controller, which provides foreground applications with core capabilities for interacting with the input method. After obtaining an instance through `inputMethod.getController()`, you can perform the following operations: <br> <br>- Attachment management: Use [attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach) to establish attachment to the input method, and use [detach](arkts-ime-inputmethod-inputmethodcontroller-i.md#detach) to perform detachment. **attach** and **detach** must be used in pairs. <br>- Keyboard control: Use [showTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#showtextinput) to start the soft keyboard and enter the editing state, and use [hideTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#hidetextinput) to hide the soft keyboard and exit the editing state. **showTextInput** and **hideTextInput** must be used in pairs. <br>- Edit box state synchronization: Use APIs such as [updateCursor](arkts-ime-inputmethod-inputmethodcontroller-i.md#updatecursor), <br> <br>[changeSelection](arkts-ime-inputmethod-inputmethodcontroller-i.md#changeselection), and [updateAttribute](arkts-ime-inputmethod-inputmethodcontroller-i.md#updateattribute) to synchronize edit box state information such as the cursor, selection, and attributes with the input method. <br>- Event subscription: Use APIs such as **on('insertText')** and **on('deleteLeft')** to subscribe to text operation events sent by the input method application. <br> <br>Typical call sequence: `getController()` → `attach()` → `showTextInput()`/`hideTextInput()` → `detach()` <br> <br>  
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

## hideSoftKeyboard

```TypeScript
hideSoftKeyboard(displayId: number): Promise<void>
```

Hides the soft keyboard on a specified screen. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to <br>
> hide the soft keyboard only when the edit box is focused.

**Since:** 23

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodController-hideSoftKeyboard(displayId: long): Promise<void>--><!--Device-InputMethodController-hideSoftKeyboard(displayId: long): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | Yes | Screen ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: number = 30;
inputMethod.getController().hideSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in hiding softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

<!--DelEnd-->

## showSoftKeyboard

```TypeScript
showSoftKeyboard(displayId: number): Promise<void>
```

Shows the soft keyboard on a specified screen. This API uses a promise to return the result. <br> <br>Paired calls: <br> <br>- This method is used together with **hideSoftKeyboard** to control the showing and hiding of the soft keyboard. <br>- Generally, after calling **showSoftKeyboard** to show the soft keyboard, you can call **hideSoftKeyboard** to hide the soft keyboard when needed. <br>- This API can be called only when the edit box is attached to the input method. <br> <br>  
> **NOTE:** <br>
> <br>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to <br>
> show the soft keyboard only when the edit box is focused.

**Since:** 23

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodController-showSoftKeyboard(displayId: long): Promise<void>--><!--Device-InputMethodController-showSoftKeyboard(displayId: long): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayId | number | Yes | Screen ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: number = 20;
inputMethod.getController().showSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in showing softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

<!--DelEnd-->
