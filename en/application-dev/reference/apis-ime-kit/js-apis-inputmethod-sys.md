# @ohos.inputMethod (Input Method Framework) (System API)
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=87ecd313da7eaf9820ea21ed983e70c5f013ee1a translatedAt=2026-09-02T11:45:35.859Z pushedAt=2026-09-09T03:54:41.359Z -->

The **inputMethod** module is oriented to common foreground applications (system applications such as Notes, Messaging, and Settings). It provides input method control and management capabilities, including displaying or hiding the soft keyboard, switching between input methods, and obtaining the list of all input methods.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

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
| Promise&lt;void&gt;  | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails.  |
| 202      | not system application.  |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
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
  try {
    // 2. Switch input method.
    await inputMethod.switchInputMethod(currentIme.name);
    console.info('Succeeded in switching inputMethod.');
  } catch (err) {
    console.error(`Failed to switchInputMethod. Code: ${err.code}, message: ${err.message}`);
  }
  // 3. Obtain the current input method subtype.
  const currentSubtype: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
  if (!currentSubtype) {
    console.error("Failed to get current input subtype");
    return;
  }
  try {
    // 4. Switch input method subtype.
    await inputMethod.switchInputMethod(currentIme.name, currentSubtype.id);
    console.info('Succeeded in switching inputMethod.');
  } catch (err) {
    console.error(`Failed to switchInputMethod. Code: ${err.code}, message: ${err.message}`);
  }
}

switchInputMethodWithSubtype();
```

## InputMethodSetting<sup>9+</sup>

In the following API examples, you must first use [getSetting](./js-apis-inputmethod.md#inputmethodgetsetting9) to obtain an **InputMethodSetting** instance, and then call the APIs using the obtained instance.

### on('imeShow')<sup>10+</sup>

on(type: 'imeShow', callback: (info: Array\<InputWindowInfo>) => void): void

Subscribes to the soft keyboard show event of the [input method panel](js-apis-inputmethodengine.md#panel10) in the fixed state. This API uses an asynchronous callback to return the result.

Paired calls:
- After subscribing to events by calling **on('imeShow')**, you must call the corresponding **off('imeShow')** to unsubscribe when finished using it.
- When unsubscribing, you can pass the callback parameter to cancel the specified callback, or pass no parameter to cancel all callbacks corresponding to **type**.
- Failing to unsubscribe may lead to continuous callback invocations and memory leaks.

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

Paired calls:
- After subscribing to events by calling **on('imeHide')**, you must call the corresponding **off('imeHide')** to unsubscribe when finished using it.
- When unsubscribing, you can pass the callback parameter to cancel the specified callback, or pass no parameter to cancel all callbacks corresponding to **type**.
- Failing to unsubscribe may lead to continuous callback invocations and memory leaks.

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
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';

let info: PanelInfo = {
  type: PanelType.SOFT_KEYBOARD,
  flag: PanelFlag.FLAG_FIXED
}

try {
  let result: boolean = inputMethod.getSetting().isPanelShown(info);
  console.info('Succeeded in querying isPanelShown, result: ' + result);
} catch (err) {
  console.error(`Failed to query isPanelShown. Code: ${err.code}, message: ${err.message}`);
}
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
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';

let displayId: number = 10;
let info: PanelInfo = {
  type: PanelType.SOFT_KEYBOARD,
  flag: PanelFlag.FLAG_FIXED
}

try {
  let result: boolean = inputMethod.getSetting().isPanelShown(info, displayId);
  console.info('Succeeded in querying isPanelShown, result: ' + result);
} catch (err) {
  console.error(`Failed to query isPanelShown. Code: ${err.code}, message: ${err.message}`);
}
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
  | enabledState |  [EnabledState](js-apis-inputmethod.md#enabledstate15) | Yes | Input method enabled state. The value **BASIC_MODE** enables basic mode, and **FULL_EXPERIENCE_MODE** enables full experience mode. |

**Return value**

  | Type          | Description                    |
  | -------------- | ----------------------- |
  | Promise&lt;void&gt;  | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                            |
| -------- | -------------------------------------- |
| 201      | permissions check fails. |
| 202      | not system application. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception.  |
| 12800018 | input method is not found. |
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
    .catch((err) => {
      if (err instanceof BusinessError) {
        console.error(`Failed to enableInputMethod. Code: ${err.code}, message: ${err.message}`);
      } else {
        console.error(`Failed to enableInputMethod. Error: ${err}`);
      }
    });
}

enableInputMethodSafely();
```

### getCursorInfo

getCursorInfo(userId?: number): CursorInfo

Obtains the cursor information of a specified user. If the edit box does not notify the input method service of the cursor information, all attribute values returned are **0**.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| userId |  number | No| User ID.<br>If the caller is not an application of user 0, the value of this parameter is the user ID of the caller by default.<br> If the caller is an application of user 0, the value of this parameter is the foreground user ID of the home screen.|

**Return value**

| Type| Description|
| -------- | -------- |
| [CursorInfo](js-apis-inputmethod.md#cursorinfo10) | Cursor information of the specified user.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------------------------------------- |
| 202      | not system application. |
| 12800003 | input method client error. Possible causes: 1. No edit box is bound to the current input method application under the specified user. |
| 12800008 | input method manager service error. Possible causes: a system error, such as null pointer, IPC exception. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let cursorInfo: inputMethod.CursorInfo = inputMethod.getSetting().getCursorInfo();
  console.info(`get cursorInfo success, left: ${cursorInfo.left}, top: ${cursorInfo.top}, width: ${cursorInfo.width}, height: ${cursorInfo.height}, displayId: ${cursorInfo.displayId}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get cursorInfo. Code: ${error.code}, message: ${error.message}`);
}
```

### getDefaultInputMethodAbility

getDefaultInputMethodAbility(): InputMethodProperty

Obtains the default input method capabilities. To optimize performance, the returned **InputMethodProperty** object ensures that only the `name` and `id` attributes that uniquely identify the input method capability are correct. Other attributes may be empty.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**Return value**

| Type| Description|
| -------- | -------- |
| [InputMethodProperty](js-apis-inputmethod.md#inputmethodproperty8) | Default input method attributes. Only the `name` and `id` attributes are guaranteed to be correct. Other attributes may be empty.|

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------------------------------------- |
| 202      | not system application. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const defaultAbility: inputMethod.InputMethodProperty = inputMethod.getSetting().getDefaultInputMethodAbility();
  console.info('Succeeded in getting default input method ability, name: ' + defaultAbility.name + ', id: ' + defaultAbility.id);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getDefaultInputMethodAbility. Code: ${error.code}, message: ${error.message}`);
}
```

## InputMethodController

A control class that encapsulates APIs for input method management, which can only be invoked after an **InputMethodController** instance is obtained via [getController](./js-apis-inputmethod.md#inputmethodgetcontroller9).

### showSoftKeyboard<sup>23+</sup>

showSoftKeyboard(displayId: number): Promise&lt;void&gt;

Shows the soft keyboard on a specified screen. This API uses a promise to return the result.

Paired calls:
- This method is used together with **hideSoftKeyboard** to control the showing and hiding of the soft keyboard.
- Generally, after calling **showSoftKeyboard** to display the soft keyboard, you can call **hideSoftKeyboard** to hide the soft keyboard when needed.
- This API can be called only when the edit box is attached to the input method.

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
| 12800003 | input method client error. Possible causes: 1. the edit box is not focused. 2. no edit box is bound to current input method application. 3. ipc failed due to the large amount of data transferred or other reasons.|
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

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
| 12800003 | input method client error. Possible causes: 1. the edit box is not focused. 2. no edit box is bound to current input method application. 3. ipc failed due to the large amount of data transferred or other reasons.|
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

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

## inputMethod.getDefaultInputMethod

getDefaultInputMethod(userId?: number): InputMethodProperty

Obtains the default input method of a specified user.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| userId | number | No | User ID. The value is the ID of a valid user. If this parameter is not provided:<br>- If the caller is not an application of user 0, the value defaults to the caller's user ID.<br>- If the caller is an application of user 0, the value defaults to the foreground user ID of the home screen. |

**Return value**

| Type                                         | Description                     |
| -------------------------------------------- | ------------------------ |
| [InputMethodProperty](js-apis-inputmethod.md#inputmethodproperty8) | Returns the default input method property object. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 202 | not system application. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let defaultIme: inputMethod.InputMethodProperty = inputMethod.getDefaultInputMethod(100);
  console.info('Succeeded in getting default input method, name: ' + defaultIme.name + ', id: ' + defaultIme.id);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getDefaultInputMethod. Code: ${error.code}, message: ${error.message}`);
}
```

## inputMethod.getSystemInputMethodConfigAbility

getSystemInputMethodConfigAbility(userId?: number): ElementName

Obtains ability information for the system input method settings UI of a specified user. Used to launch the system input method configuration page.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| userId | number | No | User ID. The value is the ID of a valid user. If not provided:<br>- If the caller is not an application of user 0, this value defaults to the caller's user ID.<br>- If the caller is an application of user 0, this value defaults to the foreground user ID of the home screen. |

**Return value**

| Type                                         | Description                     |
| -------------------------------------------- | ------------------------ |
| [ElementName](../apis-ability-kit/js-apis-bundleManager-elementName.md) | **ElementName** of the ability for the system input method settings UI. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 202 | not system application. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let inputMethodConfig: bundleManager.ElementName = inputMethod.getSystemInputMethodConfigAbility(100);
  console.info('Succeeded in getting system input method config ability, bundleName: ' + inputMethodConfig.bundleName);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getSystemInputMethodConfigAbility. Code: ${error.code}, message: ${error.message}`);
}
```

## inputMethod.switchInputMethodWithUserId

switchInputMethodWithUserId(bundleName: string, subtypeId?: string, userId?: number): Promise&lt;void&gt;

Switches the input method. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes | Bundle name of the target input method. |
| subtypeId | string | No | ID of the input method subtype. If this parameter is not set, the system switches to the target input method that uses the default subtype. |
| userId | number | No | User ID. The value is the ID of a valid user. If this parameter is not provided:<br>- If the caller is not an application of user 0, this value defaults to the caller's user ID.<br>- If the caller is an application of user 0, this value defaults to the foreground user ID of the home screen. |

**Return value**

| Type                                      | Description                         |
| ----------------------------------------- | ---------------------------- |
| Promise&lt;void&gt;  | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 201 | permissions check fails. |
| 202 | not system application. |
| 12800005 | configuration persistence error. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.switchInputMethodWithUserId('com.example.keyboard', 'subtype_001', 100).then(() => {
  console.info('Succeeded in switching input method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to switchInputMethodWithUserId, code: ${err.code}, message: ${err.message}`);
});
```

## inputMethod.getCurrentInputMethod

getCurrentInputMethod(userId?: number): InputMethodProperty

Obtains the current input method of a specified user.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| userId | number | No | User ID. The value is the ID of a valid user. If not provided:<br>- If the caller is not an application of user 0, this value defaults to the caller's user ID.<br>- If the caller is an application of user 0, this value defaults to the foreground user ID of the home screen. |

**Return value**

| Type                                         | Description                     |
| -------------------------------------------- | ------------------------ |
| [InputMethodProperty](js-apis-inputmethod.md#inputmethodproperty8) | Returns the property object of the current input method. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 202 | not system application. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod(100);
  console.info('Succeeded in getting current input method, name: ' + currentIme.name + ', id: ' + currentIme.id);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getCurrentInputMethod. Code: ${error.code}, message: ${error.message}`);
}
```

## inputMethod.getCurrentInputMethodSubtype

getCurrentInputMethodSubtype(userId?: number): InputMethodSubtype

Obtains the current input method subtype of a specified user.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| userId | number | No | User ID. The value is the ID of a valid user. If this parameter is not provided:<br>- If the caller is not an application of user 0, this value defaults to the caller's user ID.<br>- If the caller is an application of user 0, this value defaults to the foreground user ID of the home screen. |

**Return value**

| Type                                         | Description                     |
| -------------------------------------------- | ------------------------ |
| [InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype) | Returns the current input method subtype object. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 202 | not system application. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let currentImeSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype(100);
  console.info('Succeeded in getting current input method subtype, id: ' + currentImeSubType.id);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getCurrentInputMethodSubtype. Code: ${error.code}, message: ${error.message}`);
}
```

### enableInputMethod

enableInputMethod(bundleName: string, extensionName: string, enabledState: EnabledState, userId?: number): Promise&lt;void&gt;

Modifies the enabled state of the input method for a specified user.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes | Bundle name of the input method. |
| extensionName | string | Yes | Extension name of the input method. |
| enabledState | [EnabledState](js-apis-inputmethod.md#enabledstate15) | Yes | Enabled state to be modified. |
| userId | number | No | User ID. The value is the ID of a valid user. If this parameter is not provided:<br>- If the caller is not an application of user 0, this value defaults to the caller's user ID.<br>- If the caller is an application of user 0, this value defaults to the foreground user ID of the home screen. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 201 | permissions check fails. |
| 202 | not system application. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800018 | input method is not found. |
| 12800019 | current operation cannot be applied to the preconfigured default input method. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().enableInputMethod('com.example.keyboard', 'InputMethodExtAbility', inputMethod.EnabledState.FULL_EXPERIENCE_MODE, 100).then(() => {
  console.info('Succeeded in enabling input method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to enableInputMethod, code: ${err.code}, message: ${err.message}`);
});
```

### getAllInputMethodsSync

getAllInputMethodsSync(userId?: number): Array&lt;InputMethodProperty&gt;

Obtains the list of all input method applications of a specified user. This is a synchronous API.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------- | ---- | ----------------------- |
| userId | number | No | User ID. The value is the ID of a valid user. If this parameter is not provided:<br>- If the caller is not an application of user 0, this value defaults to the caller's user ID.<br>- If the caller is an application of user 0, this value defaults to the foreground user ID of the home screen. |

**Return value**

| Type | Description |
| ---------------------------------------------------- | ------------------ |
| Array\<[InputMethodProperty](js-apis-inputmethod.md#inputmethodproperty8)> | Returns the list of all input methods. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 202 | not system application. |
| 12800001 | bundle manager error. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getAllInputMethodsSync(100);
  console.info('Succeeded in getting all input methods, count: ' + imeProperty.length);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getAllInputMethodsSync. Code: ${error.code}, message: ${error.message}`);
}
```

### getInputMethodSubtypes

getInputMethodSubtypes(bundleName: string, userId?: number): Array&lt;InputMethodSubtype&gt;

Obtains the list of input method subtypes for a specified user. This is a synchronous API.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes | Bundle name of the specified input method. |
| userId | number | No | User ID. The value is the ID of a valid user. If this parameter is not provided:<br>- If the caller is not an application of user 0, this value defaults to the caller's user ID.<br>- If the caller is an application of user 0, this value defaults to the foreground user ID of the home screen. |

**Return value**

| Type                                                        | Description                   |
| ----------------------------------------------------------- | ---------------------- |
| Array<[InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype)> | Returns the list of specified input method subtypes. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 202 | not system application. |
| 12800001 | bundle manager error. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();
try {
  let subtypes: Array<InputMethodSubtype> = inputMethodSetting.getInputMethodSubtypes('com.example.keyboard', 100);
  console.info('Succeeded in getting input method subtypes, count: ' + subtypes.length);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getInputMethodSubtypes. Code: ${error.code}, message: ${error.message}`);
}
```

### getInputMethodsSync

getInputMethodsSync(enable: boolean, userId?: number): Array&lt;InputMethodProperty&gt;

Obtains the list of activated/deactivated input method applications for a specified user. This is a synchronous API.

> **NOTE**
>
> An activated input method is an enabled input method application. The default input method is enabled by default, and other input methods can be set to enabled or disabled.
>
> The activated input method list includes the default input method and input method applications that have been enabled, while the deactivated input method list includes other installed input methods except the enabled ones.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type    | Mandatory | Description                    |
| ------ | ------- | ---- | ----------------------- |
| enable | boolean | Yes   |Whether to activate the input method list:<br>- **true** indicates returning the activated input method list.<br>- **false** indicates returning the deactivated input method list. |
| userId | number | No | User ID. The value is the ID of a valid user. If this parameter is not provided:<br>- If the caller is not an application of user 0, this value defaults to the caller's user ID.<br>- If the caller is an application of user 0, this value defaults to the foreground user ID of the home screen. |

**Return value**

| Type                                                 | Description                          |
| ---------------------------------------------------- | ----------------------------- |
| Array\<[InputMethodProperty](js-apis-inputmethod.md#inputmethodproperty8)> | Returns the activated/deactivated input method list. |

**Error codes**

For details about the error codes, see [Input Method Framework Error Codes](errorcode-inputmethod-framework.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 202 | not system application. |
| 12800001 | bundle manager error. |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800023 | the specified user does not exist. |
| 12800024 | the specified user is not in the foreground. |
| 12800025 | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getInputMethodsSync(true, 100);
  console.info('Succeeded in getting enabled input methods, count: ' + imeProperty.length);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getInputMethodsSync. Code: ${error.code}, message: ${error.message}`);
}
```

### onImeChangeWithUserId

onImeChangeWithUserId(callback: ImeChangeWithUserIdCallback): void

Subscribes to input method and subtype change events, carrying the user ID of the input method change. This API uses an asynchronous callback.

Paired calls:
- After subscribing to events by calling **onImeChangeWithUserId**, you must call **offImeChangeWithUserId** to unsubscribe upon completion of the subscription.
- When unsubscribing, you can pass the callback parameter to cancel the specified callback, or pass no parameter to cancel all corresponding listener events.
- Failing to unsubscribe may lead to continuous callback invocations and memory leaks.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type                            | Mandatory | Description                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [ImeChangeWithUserIdCallback](#imechangewithuseridcallback)  | Yes | Callback, returning the input method property object, subtype object, and user ID. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 202      | not system application.  |

**Example**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';

inputMethod.getSetting()
  .onImeChangeWithUserId((inputMethodProperty: inputMethod.InputMethodProperty, inputMethodSubtype: InputMethodSubtype, userId: number) => {
    console.info(`Succeeded in subscribing imeChange: inputMethodProperty.name: ${inputMethodProperty.name}, inputMethodSubtype.id: ${inputMethodSubtype.id}, userId: ${userId}`);
  });
```

### offImeChangeWithUserId

offImeChangeWithUserId(callback?: ImeChangeWithUserIdCallback): void

Unsubscribes from the input method and subtype change listener events, carrying the user ID of the input method change. This API uses an asynchronous callback.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type                            | Mandatory | Description                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [ImeChangeWithUserIdCallback](#imechangewithuseridcallback)  | No | Callback that returns the unsubscribed input method property object, subtype object, and user ID.<br>When the parameter is not specified, all callback events are unsubscribed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                             |
| -------- | -------------------------------------- |
| 202      | not system application.  |

**Example**

```ts
inputMethod.getSetting().offImeChangeWithUserId();
```

## ImeChangeWithUserIdCallback

type ImeChangeWithUserIdCallback = (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype, userId: number) => void

Callback for input method change events, carrying the user ID where the input method change occurs.

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name                    | Type                                                         | Mandatory | Description             |
| ------------------------- | ------------------------------------------------------------ | ---- | ---------------- |
| inputMethodProperty | [InputMethodProperty](js-apis-inputmethod.md#inputmethodproperty8) | Yes   | Property of the current input method. |
| inputMethodSubtype | [InputMethodSubtype](./js-apis-inputmethod-subtype.md#inputmethodsubtype) | Yes   | Subtype of the current input method. |
| userId | number | Yes | User ID where the input method change occurs. |

## InputWindowInfo

Window information of the input method soft keyboard (system API extended properties).

**Since:** 26.0.0

**System capability**: SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Model restriction:** This API can be used only in the stage model.

For more properties of the input method soft keyboard window information, see [InputWindowInfo](js-apis-inputmethod.md#inputwindowinfo10).

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| userId | number | No | Yes | User ID for displaying the input method window.<br>This property is available only to system applications.|