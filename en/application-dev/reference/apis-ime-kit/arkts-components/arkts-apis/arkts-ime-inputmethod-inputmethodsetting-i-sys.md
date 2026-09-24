# InputMethodSetting

```TypeScript
interface InputMethodSetting
```

In the following API examples, you must first use [getSetting](arkts-ime-inputmethod-getsetting-f.md) to obtain an **InputMethodSetting** instance, and then call the APIs using the obtained instance.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## enableInputMethod

```TypeScript
enableInputMethod(bundleName: string, extensionName: string, enabledState: EnabledState): Promise<void>
```

Enables or disables an input method. This API uses a promise to return the result. <br> <br>**Example** <br> <br>```ts <br>import { BusinessError } from '@kit.BasicServicesKit'; <br> <br>function enableInputMethodSafely() {<br> const currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod(); <br> if (!currentIme) {<br> console.error("Failed to get current input method"); <br> return; <br> } <br> <br> inputMethod.getSetting() <br> .enableInputMethod(currentIme.name, currentIme.id, inputMethod.EnabledState.BASIC_MODE) <br> .then(() =&gt; {<br> console.info('Succeeded in enable inputmethod.'); <br> }) <br> .catch((err: BusinessError) =&gt; {<br> console.error(`Failed to enableInputMethod. Code: ${err.code}, message: ${err.message}`); <br> }); <br>} <br> <br>enableInputMethodSafely(); <br>```

**Since:** 20

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the input method. |
| extensionName | string | Yes | Extension name of the input method. |
| enabledState | [EnabledState](arkts-ime-inputmethod-enabledstate-e.md) | Yes | Whether the input method is enabled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800018](../errorcode-inputmethod-framework.md#12800018-input-method-not-found) | input method is not found. |
| [12800019](../errorcode-inputmethod-framework.md#12800019-unsupported-operation-by-default-input-method) | current operation cannot be applied to the preconfigured default input method. |

**Examples**

```TypeScript
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

<a id="enableinputmethod-1"></a>

## enableInputMethod

```TypeScript
enableInputMethod(
      bundleName: string, extensionName: string, enabledState: EnabledState, userId?: number): Promise<void>
```

Change the enabled state of an input method of a specified user.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CONNECT_IME_ABILITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Indicates the bundle name of the input method. |
| extensionName | string | Yes | Indicates the extension name of the input method. |
| enabledState | [EnabledState](arkts-ime-inputmethod-enabledstate-e.md) | Yes | Indicates the enabledState to be changed. |
| userId | number | No | the user ID. If not provided: If the caller is not a user 0 application, the value defaults to the caller's user ID. If the caller is a user 0 application, the value defaults to the foreground user ID of the main screen. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800018](../errorcode-inputmethod-framework.md#12800018-input-method-not-found) | input method is not found. |
| [12800019](../errorcode-inputmethod-framework.md#12800019-unsupported-operation-by-default-input-method) | current operation cannot be applied to the preconfigured default input method. |
| [12800023](../errorcode-inputmethod-framework.md#12800023-specified-user-not-exist) | the specified user does not exist. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-specified-user-not-in-the-foreground) | the specified user is not in the foreground. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-cross-user-operation-denied) | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().enableInputMethod('com.example.keyboard', 'InputMethodExtAbility', inputMethod.EnabledState.FULL_EXPERIENCE_MODE, 100).then(() => {
  console.info('Succeeded in enabling input method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to enableInputMethod, code: ${err.code}, message: ${err.message}`);
});
```

<a id="getallinputmethodssync-1"></a>

## getAllInputMethodsSync

```TypeScript
getAllInputMethodsSync(userId?: number): Array<InputMethodProperty>
```

Get all input methods sync of a specified user.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | No | the user ID. If not provided: If the caller is not a user 0 application, the value defaults to the caller's user ID. If the caller is a user 0 application, the value defaults to the foreground user ID of the main screen. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt; | the list of all input methods. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800023](../errorcode-inputmethod-framework.md#12800023-specified-user-not-exist) | the specified user does not exist. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-specified-user-not-in-the-foreground) | the specified user is not in the foreground. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-cross-user-operation-denied) | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getAllInputMethodsSync(100);
  console.info('Succeeded in getting all input methods, count: ' + imeProperty.length);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getAllInputMethodsSync. Code: ${error.code}, message: ${error.message}`);
}
```

## getCursorInfo

```TypeScript
getCursorInfo(userId?: number): CursorInfo
```

Obtains the cursor information of a specified user. If the edit box does not notify the input method service of the cursor information, all attribute values returned are **0**. <br> <br>**Example** <br> <br>```ts <br>import { BusinessError } from '@kit.BasicServicesKit'; <br> <br>try {<br> let cursorInfo: inputMethod.CursorInfo = inputMethod.getSetting().getCursorInfo(); <br> console.info(`get cursorInfo success, left: ${cursorInfo.left}, top: ${cursorInfo.top}, width: ${cursorInfo.width}, height: ${cursorInfo.height}, displayId: ${cursorInfo.displayId}`); <br>} catch (err) {<br> let error = err as BusinessError; <br> console.error(`Failed to get cursorInfo. Code: ${error.code}, message: ${error.message}`); <br>} <br>```

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | No | User ID.<br>If the caller is not an application of user 0, the value of this parameter is the user ID of the caller by default. <br> If the caller is an application of user 0, the value of this parameter is the foreground user ID of the main screen. |

**Return value:**

| Type | Description |
| --- | --- |
| [CursorInfo](arkts-ime-inputmethod-cursorinfo-i.md) | Cursor information of the specified user. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1. No edit box is bound to the current input method application under the specified user. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible causes: a system error, such as null pointer, IPC exception. |
| [12800023](../errorcode-inputmethod-framework.md#12800023-specified-user-not-exist) | the specified user does not exist. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-specified-user-not-in-the-foreground) | the specified user is not in the foreground. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-cross-user-operation-denied) | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let cursorInfo: inputMethod.CursorInfo = inputMethod.getSetting().getCursorInfo();
  console.info(`get cursorInfo success, left: ${cursorInfo.left}, top: ${cursorInfo.top}, width: ${cursorInfo.width}, height: ${cursorInfo.height}, displayId: ${cursorInfo.displayId}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get cursorInfo. Code: ${error.code}, message: ${error.message}`);
}
```

## getDefaultInputMethodAbility

```TypeScript
getDefaultInputMethodAbility(): InputMethodProperty
```

Obtains the default input method capabilities. To optimize performance, the returned **InputMethodProperty** object ensures that only the `name` and `id` attributes that uniquely identify the input method capability are correct. Other attributes may be empty. <br> <br>**Example** <br> <br>```ts <br>try {<br> const defaultAbility: inputMethod.InputMethodProperty = inputMethod.getSetting().getDefaultInputMethodAbility(); <br> console.info('Succeeded in getting default input method ability, name: ' + defaultAbility.name + ', id: ' + defaultAbility.id); <br>} catch (err) {<br> console.error(`Failed to getDefaultInputMethodAbility. Code: ${err.code}, message: ${err.message}`); <br>} <br>```

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | Default input method attributes. Only the `name` and `id` attributes are guaranteed to be correct. Other attributes may be empty. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const defaultAbility: inputMethod.InputMethodProperty = inputMethod.getSetting().getDefaultInputMethodAbility();
  console.info('Succeeded in getting default input method ability, name: ' + defaultAbility.name + ', id: ' + defaultAbility.id);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getDefaultInputMethodAbility. Code: ${error.code}, message: ${error.message}`);
}
```

<a id="getinputmethodssync-1"></a>

## getInputMethodsSync

```TypeScript
getInputMethodsSync(enable: boolean, userId?: number): Array<InputMethodProperty>
```

List enabled or disabled input methods sync of a specified user.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | If true, collect enabled input methods. If false, collect disabled input methods. |
| userId | number | No | the user ID. If not provided: If the caller is not a user 0 application, the value defaults to the caller's user ID. If the caller is a user 0 application, the value defaults to the foreground user ID of the main screen. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt; | the list of input methods. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800023](../errorcode-inputmethod-framework.md#12800023-specified-user-not-exist) | the specified user does not exist. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-specified-user-not-in-the-foreground) | the specified user is not in the foreground. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-cross-user-operation-denied) | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getInputMethodsSync(true, 100);
  console.info('Succeeded in getting enabled input methods, count: ' + imeProperty.length);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getInputMethodsSync. Code: ${error.code}, message: ${error.message}`);
}
```

## getInputMethodSubtypes

```TypeScript
getInputMethodSubtypes(bundleName: string, userId?: number): Array<InputMethodSubtype>
```

Get subtypes of a specified input method of a specified user.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | the bundle name of the specified input method. |
| userId | number | No | the user ID. If not provided: If the caller is not a user 0 application, the value defaults to the caller's user ID. If the caller is a user 0 application, the value defaults to the foreground user ID of the main screen. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md)&gt; | the subtype of target input method. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800023](../errorcode-inputmethod-framework.md#12800023-specified-user-not-exist) | the specified user does not exist. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-specified-user-not-in-the-foreground) | the specified user is not in the foreground. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-cross-user-operation-denied) | cross-user operation denied. Only user 0 applications are authorized for this operation. |

**Examples**

```TypeScript
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

## isPanelShown

```TypeScript
isPanelShown(panelInfo: PanelInfo): boolean
```

Checks whether the input method panel of a specified type is shown.

**Since:** 11

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| panelInfo | [PanelInfo](arkts-ime-inputmethod-panel-panelinfo-i.md) | Yes | Information about the input method panel. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the input method panel is shown.<br>- The value **true** means that the input method panel is shown. <br>- The value **false** means that the input method panel is hidden. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
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

<a id="ispanelshown-1"></a>

## isPanelShown

```TypeScript
isPanelShown(panelInfo: PanelInfo, displayId: number): boolean
```

Checks whether the input method panel of a specified type is shown on a specified screen.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| panelInfo | [PanelInfo](arkts-ime-inputmethod-panel-panelinfo-i.md) | Yes | Information about the input method panel. |
| displayId | number | Yes | Display ID. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the input method panel is shown.<br>- The value **true** means that the input method panel is shown. <br>- The value **false** means that the input method panel is hidden. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
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

## off('imeShow')

```TypeScript
off(type: 'imeShow', callback?: (info: Array<InputWindowInfo>) => void): void
```

Unsubscribes from the soft keyboard show event of the [input method panel](arkts-ime-inputmethodengine-panel-i.md) in the fixed state.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'imeShow' | Yes | Event type, which is **'imeShow'**. |
| callback | (info: Array&lt;[InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i.md)&gt;) =&gt; void | No | Callback to unregister.<br>If this parameter is not specified, this API unregisters all callbacks for the specified event type. |

**Examples**

```TypeScript
inputMethod.getSetting().off('imeShow');
```

## off('imeHide')

```TypeScript
off(type: 'imeHide', callback?: (info: Array<InputWindowInfo>) => void): void
```

Unsubscribes from the soft keyboard hide event of the [input method panel](arkts-ime-inputmethodengine-panel-i.md) in the fixed state.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'imeHide' | Yes | Event type, which is **'imeHide'**. |
| callback | (info: Array&lt;[InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i.md)&gt;) =&gt; void | No | Callback to unregister.<br>If this parameter is not specified, this API unregisters all callbacks for the specified event type. |

**Examples**

```TypeScript
inputMethod.getSetting().off('imeHide');
```

## offImeChangeWithUserId

```TypeScript
offImeChangeWithUserId(callback?: ImeChangeWithUserIdCallback): void
```

Unsubscribe from the input method change event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ImeChangeWithUserIdCallback](arkts-ime-inputmethod-imechangewithuseridcallback-t-sys.md) | No | the callback called when the current input method changes, when the subscriber unsubscribes all callbacks, this parameter can be left blank. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
inputMethod.getSetting().offImeChangeWithUserId();
```

## on('imeShow')

```TypeScript
on(type: 'imeShow', callback: (info: Array<InputWindowInfo>) => void): void
```

Subscribes to the soft keyboard show event of the [input method panel](arkts-ime-inputmethodengine-panel-i.md) in the fixed state. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'imeShow' | Yes | Event type, which is **'imeShow'**. |
| callback | (info: Array&lt;[InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i.md)&gt;) =&gt; void | Yes | Callback used to return the soft keyboard information of the input method panel in the fixed state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
inputMethod.getSetting().on('imeShow', (info: Array<inputMethod.InputWindowInfo>) => {
  console.info('Succeeded in subscribing imeShow event.');
});
```

## on('imeHide')

```TypeScript
on(type: 'imeHide', callback: (info: Array<InputWindowInfo>) => void): void
```

Subscribes to the soft keyboard hide event of the [input method panel](arkts-ime-inputmethodengine-panel-i.md) in the fixed state. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'imeHide' | Yes | Event type, which is **'imeHide'**. |
| callback | (info: Array&lt;[InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i.md)&gt;) =&gt; void | Yes | Callback used to return the soft keyboard information of the input method panel in the fixed state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
inputMethod.getSetting().on('imeHide', (info: Array<inputMethod.InputWindowInfo>) => {
  console.info('Succeeded in subscribing imeHide event.');
});
```

## onImeChangeWithUserId

```TypeScript
onImeChangeWithUserId(callback: ImeChangeWithUserIdCallback): void
```

Subscribe to the input method change event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ImeChangeWithUserIdCallback](arkts-ime-inputmethod-imechangewithuseridcallback-t-sys.md) | Yes | the callback called when the current input method changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';

inputMethod.getSetting()
  .onImeChangeWithUserId((inputMethodProperty: inputMethod.InputMethodProperty, inputMethodSubtype: InputMethodSubtype, userId: number) => {
    console.info(`Succeeded in subscribing imeChange: inputMethodProperty.name: ${inputMethodProperty.name}, inputMethodSubtype.id: ${inputMethodSubtype.id}, userId: ${userId}`);
  });
```
