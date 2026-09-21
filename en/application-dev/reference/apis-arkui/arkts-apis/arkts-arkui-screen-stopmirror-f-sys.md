# stopMirror (System API)

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## stopMirror

```TypeScript
function stopMirror(mirrorScreen:Array<number>, callback: AsyncCallback<void>): void
```

Stops mirror mode. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mirrorScreen | Array&lt;number&gt; | Yes | Array of IDs of secondary screens. Each ID must be an integer. The size of the **mirrorScreen** array cannot exceed 1000. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If mirror mode is stopped, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the screen ID using getAllScreens().
let mirrorScreenIds: Array<number> = [1, 2, 3]; // ID array of mirrored screens.
// Stop the mirror mode.
screen.stopMirror(mirrorScreenIds, (err: BusinessError) => {
  const errCode: number = err.code;
  if (errCode) {
    console.error(`Failed to stop mirror screens. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in stopping mirror screens.');
});
```


<a id="stopmirror-1"></a>

## stopMirror

```TypeScript
function stopMirror(mirrorScreen:Array<number>): Promise<void>
```

Stops mirror mode. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mirrorScreen | Array&lt;number&gt; | Yes | Array of IDs of secondary screens. Each ID must be an integer. The size of the **mirrorScreen** array cannot exceed 1000. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the screen ID using getAllScreens().
let mirrorScreenIds: Array<number> = [1, 2, 3]; // ID array of mirrored screens.
// Stop the mirror mode.
screen.stopMirror(mirrorScreenIds).then(() => {
  console.info('Succeeded in stopping mirror screens.');
}).catch((err: BusinessError) => {
  console.error(`Failed to stop mirror screens. Code: ${err.code}, message: ${err.message}`);
});
```
