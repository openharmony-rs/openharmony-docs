# @ohos.inputMethod (Input Method Framework) (System API)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

The **inputMethod** module is oriented to common foreground applications (system applications such as Notes, Messaging, and Settings). It provides input method control and management capabilities, including displaying or hiding the soft keyboard, switching between input methods, and obtaining the list of all input methods.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { inputMethod } from '@kit.IMEKit';
```

## inputMethod.switchInputMethod<sup>11+</sup>
switchInputMethod(bundleName: string, subtypeId?: string): Promise&lt;void&gt;

Switches to another input method. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  |bundleName |  string| Yes| Bundle name of the target input method.|
  |subtypeId |  string| No| Input method subtype.|

**Return value**

  | Type          | Description                    |
  | -------------- | ----------------------- |
  | Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails.  |
| 202      | not system application.  |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800005 | configuration persistence error.        |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';

async function switchInputMethodWithSubtype() {
  // 1. Obtain the current input method.
  const currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
  if (!currentIme) {
    console.error("Failed to get current input method");
    return;
  }
  // 2. Switch the input method.
  await inputMethod.switchInputMethod(currentIme.name);
  console.info('Succeeded in switching inputmethod.');
  // 3. Obtain the current input method subtype.
  const currentSubtype: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
  if (!currentSubtype) {
    console.error("Failed to get current input subtype");
    return;
  }
  // 4. Switch the input method subtype.
  await inputMethod.switchInputMethod(currentIme.name, currentSubtype.id);
  console.info('Succeeded in switching inputmethod.');
}

switchInputMethodWithSubtype();
```

## InputMethodSetting<sup>

In the following API examples, you must first use [getSetting](./js-apis-inputmethod.md#inputmethodgetsetting9) to obtain an **InputMethodSetting** instance, and then call the APIs using the obtained instance.

### on('imeShow')<sup>10+</sup>

on(type: 'imeShow', callback: (info: Array\<InputWindowInfo>) => void): void

Subscribes to the soft keyboard show event of the [input method panel](js-apis-inputmethodengine.md#panel10) in the fixed state. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | ---- | ---- | ---- |
| type     | string | Yes| Event type, which is **'imeShow'**.|
| callback | (info: Array<[InputWindowInfo](js-apis-inputmethod.md#inputwindowinfo10)>) => void | Yes| Callback used to return the soft keyboard information of the input method panel in the fixed state.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 202      | not system application.  |

**Example**

```ts
inputMethod.getSetting().on('imeShow', (info: Array<inputMethod.InputWindowInfo>) => {
  console.info('Succeeded in subscribing imeShow event.');
});
```

### on('imeHide')<sup>10+</sup>

on(type: 'imeHide', callback: (info: Array\<InputWindowInfo>) => void): void

Subscribes to the soft keyboard hide event of the [input method panel](js-apis-inputmethodengine.md#panel10) in the fixed state. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | ---- | ---- | ---- |
| type     | string | Yes| Event type, which is **'imeHide'**.|
| callback | (info: Array<[InputWindowInfo](js-apis-inputmethod.md#inputwindowinfo10)>) => void | Yes| Callback used to return the soft keyboard information of the input method panel in the fixed state.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 202      | not system application.  |


**Example**

```ts
inputMethod.getSetting().on('imeHide', (info: Array<inputMethod.InputWindowInfo>) => {
  console.info('Succeeded in subscribing imeHide event.');
});
```

### off('imeShow')<sup>10+</sup>

off(type: 'imeShow', callback?: (info: Array\<InputWindowInfo>) => void): void

Unsubscribes from the soft keyboard show event of the [input method panel](js-apis-inputmethodengine.md#panel10) in the fixed state.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type| Mandatory| Description  |
| -------- | ---- | ---- | ------ |
| type     | string | Yes| Event type, which is **'imeShow'**.|
| callback | (info: Array<[InputWindowInfo](js-apis-inputmethod.md#inputwindowinfo10)>) => void  | No| Callback to unregister.<br>If this parameter is not specified, this API unregisters all callbacks for the specified event type.|

**Example**

```ts
inputMethod.getSetting().off('imeShow');
```

### off('imeHide')<sup>10+</sup>

off(type: 'imeHide', callback?: (info: Array\<InputWindowInfo>) => void): void

Unsubscribes from the soft keyboard hide event of the [input method panel](js-apis-inputmethodengine.md#panel10) in the fixed state.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name  | Type| Mandatory| Description  |
| -------- | ---- | ---- | ------ |
| type     | string | Yes| Event type, which is **'imeHide'**.|
| callback | (info: Array<[InputWindowInfo](js-apis-inputmethod.md#inputwindowinfo10)>) => void  | No| Callback to unregister.<br>If this parameter is not specified, this API unregisters all callbacks for the specified event type.|

**Example**

```ts
inputMethod.getSetting().off('imeHide');
```

### isPanelShown<sup>11+</sup>

isPanelShown(panelInfo: PanelInfo): boolean

Checks whether the input method panel of a specified type is shown.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name   | Type                                                 | Mandatory| Description              |
| --------- | ----------------------------------------------------- | ---- | ------------------ |
| panelInfo | [PanelInfo](./js-apis-inputmethod-panel.md#panelinfo) | Yes  | Information about the input method panel.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Whether the input method panel is shown.<br>- The value **true** means that the input method panel is shown.<br>- The value **false** means that the input method panel is hidden.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 202      | not system application.  |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';

let info: PanelInfo = {
  type: PanelType.SOFT_KEYBOARD,
  flag: PanelFlag.FLAG_FIXED
}

let result: boolean = inputMethod.getSetting().isPanelShown(info);
console.info('Succeeded in querying isPanelShown, result: ' + result);
```

### isPanelShown<sup>23+</sup>

isPanelShown(panelInfo: PanelInfo, displayId: number): boolean

Checks whether the input method panel of a specified type is shown on a specified screen.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name   | Type                                                 | Mandatory| Description              |
| --------- | ----------------------------------------------------- | ---- | ------------------ |
| panelInfo | [PanelInfo](./js-apis-inputmethod-panel.md#panelinfo) |  Yes | Information about the input method panel.|
| displayId | number | Yes| Display ID.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Whether the input method panel is shown.<br>- The value **true** means that the input method panel is shown.<br>- The value **false** means that the input method panel is hidden.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                           |
| -------- | ----------------------------------- |
| 202      | not system application.  |
| 12800008 | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';

let displayId: number = 10;
let info: PanelInfo = {
  type: PanelType.SOFT_KEYBOARD,
  flag: PanelFlag.FLAG_FIXED
}

let result: boolean = inputMethod.getSetting().isPanelShown(info, displayId);
console.info('Succeeded in querying isPanelShown, result: ' + result);
```

### enableInputMethod<sup>20+</sup>

enableInputMethod(bundleName: string, extensionName: string, enabledState: EnabledState): Promise&lt;void&gt;

Enables or disables an input method. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | bundleName |  string | Yes| Bundle name of the input method.|
  | extensionName |  string | Yes| Extension name of the input method.|
  | enabledState |  [EnabledState](js-apis-inputmethod.md#enabledstate15) | Yes| Whether the input method is enabled.|

**Return value**

  | Type          | Description                    |
  | -------------- | ----------------------- |
  | Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails. |
| 202      | not system application. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception.  |
| 12800018 | the input method is not found. |
| 12800019 | current operation cannot be applied to the preconfigured default input method. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function enableInputMethodSafely() {
  const currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
  if (!currentIme) {
    console.error("Failed to get current input method");
    return;
  }

  inputMethod.getSetting()
    .enableInputMethod(currentIme.name, currentIme.id, inputMethod.EnabledState.BASIC_MODE)
    .then(() => {
      console.info('Succeeded in enable inputmethod.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to enableInputMethod. Code: ${err.code}, message: ${err.message}`);
    });
}

enableInputMethodSafely();
```

## InputMethodController

A control class that encapsulates APIs for input method management, which can only be invoked after an **InputMethodController** instance is obtained via [getController](./js-apis-inputmethod.md#inputmethodgetcontroller9).

### showSoftKeyboard<sup>23+</sup>

showSoftKeyboard(displayId: number): Promise&lt;void&gt;

Shows the soft keyboard on a specified screen. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to show the soft keyboard only when the edit box is focused.

**Model restriction**: This API can be used only in the stage model.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY (for system applications only)

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name  | Type | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| displayId | number | Yes  | Display ID.|

**Return value**

| Type          | Description                    |
| -------------- | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails.  |
| 202      | not system application.  |
| 12800003 | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons.|
| 12800008 | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: number = 20;
inputMethod.getController().showSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in showing softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

### hideSoftKeyboard<sup>23+</sup>

hideSoftKeyboard(displayId: number): Promise&lt;void&gt;

Hides the soft keyboard on a specified screen. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called only when the edit box is attached to the input method. That is, it can be called to hide the soft keyboard only when the edit box is focused.

**Model restriction**: This API can be used only in the stage model.

**Required permissions**: ohos.permission.CONNECT_IME_ABILITY (for system applications only)

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API**: This is a system API.

**Parameters**

| Name  | Type | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| displayId | number | Yes  | Display ID.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails.  |
| 202      | not system application.  |
| 12800003 | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons.|
| 12800008 | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: number = 30;
inputMethod.getController().hideSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in hiding softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```
