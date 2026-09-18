# onSystemEvent (System API)

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

## onSystemEvent

```TypeScript
function onSystemEvent(callback: Callback<SystemEvent>): boolean
```

Register system event related to screen lock service.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[SystemEvent](arkts-basicservices-screenlock-systemevent-i-sys.md)&gt; | Yes | the callback of onSystemEvent. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | returns true if register system event is success, returns false otherwise. |

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

try {
  let isSuccess = screenLock.onSystemEvent((event: screenLock.SystemEvent) => {
    console.info(`Succeeded in Registering the system event which related to screenlock. eventType: ${event.eventType}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to register the system event which related to screenlock, Code: ${error.code}, message: ${error.message}`);
}
```
