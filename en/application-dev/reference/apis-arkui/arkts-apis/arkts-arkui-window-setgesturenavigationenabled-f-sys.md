# setGestureNavigationEnabled (System API)

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## setGestureNavigationEnabled

```TypeScript
function setGestureNavigationEnabled(enable: boolean, callback: AsyncCallback<void>): void
```

Enables or disables gesture navigation. This API uses an asynchronous callback to return the result. For security purposes, the system does not interfere with the disabling and enabling of gesture navigation. If an application exits abnormally after it disables gesture navigation and wants to restore gesture navigation, it must implement automatic launch and call this API again to enable gesture navigation.

**Since:** 10

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable gesture navigation. **true** to enable, **false** otherwise. Currently, only the pull-down gesture is disabled. Other gestures remain enabled. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  window.setGestureNavigationEnabled(true, (err: BusinessError) => {
    const errCode: number = err.code;
    if (errCode) {
      console.error(`Failed to set gesture navigation enabled. Cause code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting gesture navigation enabled.');
  });
} catch (exception) {
  console.error(`Failed to set gesture navigation enabled. Cause code: ${exception.code}, message: ${exception.message}`);
}
```


<a id="setgesturenavigationenabled-1"></a>

## setGestureNavigationEnabled

```TypeScript
function setGestureNavigationEnabled(enable: boolean): Promise<void>
```

Enables or disables gesture navigation. This API uses a promise to return the result. For security purposes, the system does not interfere with the disabling and enabling of gesture navigation. If an application exits abnormally after it disables gesture navigation and wants to restore gesture navigation, it must implement automatic launch and call this API again to enable gesture navigation.

**Since:** 10

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable gesture navigation. **true** to enable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [1300002](../errorcode-window.md#1300002-abnormal-window-state) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-abnormal-window-manager-service) | This window manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise = window.setGestureNavigationEnabled(true);
  promise.then(() => {
    console.info('Succeeded in setting gesture navigation enabled.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set gesture navigation enabled. Cause code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to set gesture navigation enabled. Cause code: ${exception.code}, message: ${exception.message}`);
}
```
