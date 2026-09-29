# KeyboardController

```TypeScript
interface KeyboardController
```

You must first use [on('inputStart')](arkts-ime-inputmethodengine-inputmethodability-i.md#oninputstart) to obtain a **KeyboardController** instance, and then use this instance to call the following APIs.

**Since:** 8

<!--Device-inputMethodEngine-interface KeyboardController--><!--Device-inputMethodEngine-interface KeyboardController-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## exitCurrentInputType

```TypeScript
exitCurrentInputType(callback: AsyncCallback<void>): void
```

Exits this input type. This API can be called only by the preconfigured default input method. This API uses an asynchronous callback to return the result.

**Since:** 11

<!--Device-KeyboardController-exitCurrentInputType(callback: AsyncCallback<void>): void--><!--Device-KeyboardController-exitCurrentInputType(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800010](../errorcode-inputmethod-framework.md#12800010-not-preconfigured-default-input-method) | not the preconfigured default input method. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.exitCurrentInputType((err: BusinessError) => {
  if (err) {
    console.error(`Failed to exit current input type. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info('Succeeded in exiting current input type.');
});
```

<a id="exitcurrentinputtype-1"></a>

## exitCurrentInputType

```TypeScript
exitCurrentInputType(): Promise<void>
```

Exits this input type. This API can be called only by the preconfigured default input method. This API uses a promise to return the result.

**Since:** 11

<!--Device-KeyboardController-exitCurrentInputType(): Promise<void>--><!--Device-KeyboardController-exitCurrentInputType(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800010](../errorcode-inputmethod-framework.md#12800010-not-preconfigured-default-input-method) | not the preconfigured default input method. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.exitCurrentInputType().then(() => {
  console.info('Succeeded in exiting current input type.');
}).catch((err: BusinessError) => {
  console.error(`Failed to exit current input type. Code:${err.code}, message:${err.message}`);
});
```

## hide

```TypeScript
hide(callback: AsyncCallback<void>): void
```

Hides the keyboard. This API uses an asynchronous callback to return the result.

**Since:** 9

<!--Device-KeyboardController-hide(callback: AsyncCallback<void>): void--><!--Device-KeyboardController-hide(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hide((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hide. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info('Succeeded in hiding keyboard.');
});
```

<a id="hide-1"></a>

## hide

```TypeScript
hide(): Promise<void>
```

Hides the keyboard. This API uses a promise to return the result.

**Since:** 9

<!--Device-KeyboardController-hide(): Promise<void>--><!--Device-KeyboardController-hide(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-input-method-client-error) | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. 3.ipc failed due to the large amount of data transferred or other reasons. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hide().then(() => {
  console.info('Succeeded in hiding keyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide. Code:${err.code}, message:${err.message}`);
});
```

## hideKeyboard

```TypeScript
hideKeyboard(callback: AsyncCallback<void>): void
```

Hides the keyboard. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [hide](#hide)(callback: AsyncCallback&lt;void&gt;)

<!--Device-KeyboardController-hideKeyboard(callback: AsyncCallback<void>): void--><!--Device-KeyboardController-hideKeyboard(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hideKeyboard((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hideKeyboard. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding keyboard.');
});
```

<a id="hidekeyboard-1"></a>

## hideKeyboard

```TypeScript
hideKeyboard(): Promise<void>
```

Hides the keyboard. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [hide](#hide)()

<!--Device-KeyboardController-hideKeyboard(): Promise<void>--><!--Device-KeyboardController-hideKeyboard(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hideKeyboard().then(() => {
  console.info('Succeeded in hiding keyboard.');
}).catch((err: BusinessError) => {
  console.info(`Failed to hideKeyboard. Code is ${err.code}, message is ${err.message}`);
});
```
