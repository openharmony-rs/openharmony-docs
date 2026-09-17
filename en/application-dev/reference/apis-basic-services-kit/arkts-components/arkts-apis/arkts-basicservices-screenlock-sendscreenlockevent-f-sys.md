# sendScreenLockEvent (System API)

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

## sendScreenLockEvent

```TypeScript
function sendScreenLockEvent(event: String, parameter: number, callback: AsyncCallback<boolean>): void
```

The screen lock app sends the event to the screen lock service.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | String | Yes | event type. |
| parameter | number | Yes | operation result of the event. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | the callback of sendScreenLockEvent. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | permission verification failed, application which is not a system application uses system API. |
| [13200002](../errorcode-screenlock.md#13200002-screen-lock-management-service-is-abnormal) | the screenlock management service is abnormal. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

screenLock.sendScreenLockEvent('unlockScreenResult', 0, (err: BusinessError, result: Boolean) => {
  if (err) {
    console.error(`Failed to send screenlock event, Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in Sending screenlock event. result: ${result}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

screenLock.sendScreenLockEvent('unlockScreenResult', 0).then((result: Boolean) => {
  console.info(`Succeeded in Sending screenlock event. result: ${result}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to send screenlock event, Code: ${err.code}, message: ${err.message}`);
});
```


## sendScreenLockEvent

```TypeScript
function sendScreenLockEvent(event: String, parameter: number): Promise<boolean>
```

The screen lock app sends the event to the screen lock service.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | String | Yes | event type. |
| parameter | number | Yes | operation result of the event. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | permission verification failed, application which is not a system application uses system API. |
| [13200002](../errorcode-screenlock.md#13200002-screen-lock-management-service-is-abnormal) | the screenlock management service is abnormal. |

**Examples**

See [sendScreenLockEvent](#sendscreenlockevent)
