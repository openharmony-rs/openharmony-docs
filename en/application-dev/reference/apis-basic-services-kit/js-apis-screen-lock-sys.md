# @ohos.screenLock (Screen Lock) (System API)
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @jiayunpeng2-->
<!--Designer: @starrylight; @jiayunpeng2-->
<!--Tester: @yaoruijiang-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=e42d019f7d65b854d2b5b2dffa7cc1519be0ff55 translatedAt=2026-11-10T04:13:43.475Z pushedAt=2026-11-10T07:04:34.690Z nl=1 -->

The **screenLock** module is a system module in OpenHarmony. It provides APIs for screen lock applications to subscribe to screen lock status changes as well as callbacks for them to receive the results. It also provides APIs for third-party applications to unlock the screen, obtain the screen locked status, and check whether a lock screen password has been set.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.screenLock (Screen Lock)](js-apis-screen-lock.md).

## Modules to Import

```ts
import { screenLock } from '@kit.BasicServicesKit';
```

## EventType<sup>9+</sup>

type EventType = beginWakeUp | endWakeUp | beginScreenOn | endScreenOn | beginScreenOff | endScreenOff | unlockScreen |
lockScreen | beginExitAnimation | beginSleep | endSleep | changeUser | screenlockEnabled | serviceRestart |
strongAuthChanged | screenLockDisabledChanged | unlockPolicyChanged

Defines the system event type.

**System capability**: SystemCapability.MiscServices.ScreenLock

**System API**: This is a system API.

| Type           | Description                    |
| ------------------ | ------------------------ |
| beginWakeUp        | Wakeup starts.|
| endWakeUp          | Wakeup ends.|
| beginScreenOn      | Screen turn-on starts.|
| endScreenOn        | Screen turn-on ends.|
| beginScreenOff     | Screen turn-off starts.|
| endScreenOff       | Screen turn-off ends.|
| unlockScreen       | The screen is unlocked.      |
| lockScreen         | The screen is locked.      |
| beginExitAnimation | Exit animation starts.      |
| beginSleep         | The device enters sleep mode.          |
| endSleep           | The device exits sleep mode.          |
| changeUser         | The user is switched.          |
| screenlockEnabled  | Screen lock is enabled.      |
| serviceRestart     | The screen lock service is restarted.  |
| strongAuthChanged  | The strong authentication state of the screen lock is changed.      |
| screenLockDisabledChanged     | The enabling state of the screen lock is changed.  |
| unlockPolicyChanged     | Indicates the event type when the screen lock unlock policy changes.<br> **Since Version:** 26.0.0   |

## SystemEvent<sup>9+</sup>

Defines the structure of the system event callback.

**System capability**: SystemCapability.MiscServices.ScreenLock

**System API**: This is a system API.

| Name   | Type  | Read-Only| Optional|       Description       |
| --------- | ------ | ---- | ---- | ------------- |
| eventType   | [EventType](#eventtype9) | No  | No  | System event type.|
| params | string | No  | No  | System event parameters.|

## StrongAuthReasonFlags<sup>12+</sup>

Indicates the reason flags for requesting strong authentication.

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API**: This is a system API.

| Name | Value | Description |
| -------- | -------- | -------- |
| NONE | 0x00000000 | Indicates no strong authentication. |
| AFTER_BOOT | 0x00000001 | Indicates strong authentication after boot. |
| AFTER_TIMEOUT | 0x00000002 | Indicates strong authentication after a timeout. |
| ACTIVE_REQUEST | 0x00000004 | Indicates strong authentication requested proactively. |
| POLICY_RESTRICTION | 0x00000008 | Indicates strong authentication requested due to policy restrictions. |

## AuthState<sup>12+</sup>

Enumerates the authentication states of the screen lock.

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API**: This is a system API.

| Name | Value | Description |
| -------- | -------- | -------- |
| NOT_AUTHED | 0 | The screen lock is not authenticated. |
| PRE_AUTHED_BY_CREDENTIAL | 1 | The screen lock is pre-authenticated by credential. |
| PRE_AUTHED_BY_FINGERPRINT | 2 | The screen lock is pre-authenticated by fingerprint. |
| PRE_AUTHED_BY_FACE | 3 | The screen lock is pre-authenticated by face. |
| AUTHED_BY_CREDENTIAL | 4 | The screen lock is authenticated by credential. |
| AUTHED_BY_FINGERPRINT | 5 | The screen lock is authenticated by fingerprint. |
| AUTHED_BY_FACE | 6 | The screen lock is authenticated by face. |

## UnlockPolicy

Indicates the screen lock authentication policy used to unlock the screen.

**Since**: 26.0.0

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| DEFAULT | 0 | Uses the default system authentication method to unlock the screen. |
| EXTENDED_AUTH_ONLY | 1 | Uses only the extended authentication method to unlock the screen. |
| EXTENDED_AUTH_AND_SYSTEM | 2 | Uses both the extended authentication and system authentication methods to unlock the screen. |

## screenLock.isLocked<sup>9+</sup>

isLocked(): boolean

Checks whether the screen is locked.

**System capability**: SystemCapability.MiscServices.ScreenLock

**System API**: This is a system API.

**Return value** 

| Type   | Description                                             |
| ------- | ------------------------------------------------- |
| boolean | true if the screen is locked; false otherwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message|
| -------- | ---------------------------------------- |
| 202  | permission verification failed, application which is not a system application uses system API.         |

**Example** 

```ts
let isLocked = screenLock.isLocked();
```

## screenLock.unlock<sup>9+</sup>

unlock(callback: AsyncCallback&lt;boolean&gt;): void

Unlocks the screen. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.ScreenLock

**System API**: This is a system API.

**Parameters** 

| Name  | Type         | Mandatory| Description                                |
| -------- | --------------------- | ---- | ------------------------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. The value **true** means that the screen is unlocked successfully, and **false** means that screen unlocked is canceled.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| Error Code| Error Message|
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |
| 13200003  | Invalid use.         |

**Example** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.unlock((err: BusinessError, data: Boolean) => {
    if (err) {
      console.error(`Failed to unlock the screen, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in unlocking the screen. result: ${data}`);
  });
  ```

> **NOTE**
>
> Error code `13200003 Invalid use` is added in API version 11.

## screenLock.unlock<sup>9+</sup>

unlock(): Promise&lt;boolean&gt;

Unlocks the screen. This API uses a promise to return the result.

**System capability**: SystemCapability.MiscServices.ScreenLock

**System API**: This is a system API.

**Return value** 

| Type               | Description                                                        |
| ------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the screen is unlocked successfully, and **false** means that screen unlocked is canceled.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| Error Code| Error Message|
| -------- | ---------------------------------------- |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |
| 13200003  | Invalid use.       |

**Example** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.unlock().then((data: Boolean) => {
    console.info(`Succeeded in unlocking the screen. result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to unlock the screen, Code: ${err.code}, message: ${err.message}`);
  });
  ```

> **NOTE**
>
> Error code `13200003 Invalid use` is added in API version 11.

## screenLock.lock<sup>9+</sup>

lock(callback: AsyncCallback&lt;boolean&gt;): void

Locks the screen. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Required permissions**: ohos.permission.ACCESS_SCREEN_LOCK_INNER

**System API**: This is a system API.

**Parameters** 

| Name  | Type         | Mandatory| Description                     |
| -------- | ---------------------- | ---- | ---------------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. The value **true** means that the screen is locked successfully, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| Error Code| Error Message|
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |

**Example** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.lock((err: BusinessError, data: Boolean) => {
    if (err) {
      console.error(`Failed to lock the screen, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in locking the screen. result: ${data}`);
  });
  ```

## screenLock.lock<sup>9+</sup>

lock(): Promise&lt;boolean&gt;

Locks the screen. This API uses a promise to return the result.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Required permissions**: ohos.permission.ACCESS_SCREEN_LOCK_INNER

**System API**: This is a system API.

**Return value** 

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the screen is locked successfully, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| Error Code| Error Message|
| -------- | ---------------------------------------- |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |

**Example** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.lock().then((data: Boolean) => {
    console.info(`Succeeded in locking the screen. result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to lock the screen, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## screenLock.onSystemEvent<sup>9+</sup>

onSystemEvent(callback: Callback&lt;SystemEvent&gt;): boolean

Registers a callback for system events related to screen locking. This API can be called only by screen lock applications.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Required permissions**: ohos.permission.ACCESS_SCREEN_LOCK_INNER

**System API**: This is a system API.

**Parameters** 

| Name  | Type                       | Mandatory| Description              |
| -------- | ------------------------- | ---- | ----------------- |
| callback | Callback\<[SystemEvent](#systemevent9)> | Yes  | Callback for system events related to screen locking.|

**Return value** 

| Type   | Description                                             |
| ------- | ------------------------------------------------- |
| boolean | Whether the screen lock related system event is registered successfully. The value true indicates that the screen lock related system event is registered successfully, and false indicates the opposite. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| Error Code| Error Message|
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |

**Example** 

  ```ts
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

## screenLock.sendScreenLockEvent<sup>9+</sup>

sendScreenLockEvent(event: String, parameter: number, callback: AsyncCallback&lt;boolean&gt;): void

Sends an event to the screen lock service. This API can be called only by screen lock applications. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Required permissions**: ohos.permission.ACCESS_SCREEN_LOCK_INNER

**System API**: This is a system API.

**Parameters** 

| Name   | Type           | Mandatory| Description                                                                                                               |
| --------- | ------------------------ | ---- |-------------------------------------------------------------------------------------------------------------------|
| event     | String                   | Yes  | Event type. Options are as follows:<br>- **"unlockScreenResult"**: Screen unlock result.<br>- **"lockScreenResult"**: Screen lock result.<br>- **"screenDrawDone"**: Screen drawing is complete.|
| parameter | number                   | Yes  | Result.<br>- **0**: The operation is successful. For example, the screen is locked or unlocked successfully.<br>- **1**: The operation fails. For example, screen locking or unlocking fails.<br>- **2**: The operation is canceled. For example, screen locking or unlocking is canceled.|
| callback  | AsyncCallback\<boolean> | Yes  | Callback used to return the result. The **value** true means that the event is sent successfully, and **false** means the opposite.                                                                             |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| Error Code| Error Message|
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  |the screenlock management service is abnormal.         |

**Example** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.sendScreenLockEvent('unlockScreenResult', 0, (err: BusinessError, result: Boolean) => {
    if (err) {
      console.error(`Failed to send screenlock event, Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in Sending screenlock event. result: ${result}`);
  });
  ```

## screenLock.sendScreenLockEvent<sup>9+</sup>

sendScreenLockEvent(event: String, parameter: number): Promise&lt;boolean&gt;

Sends an event to the screen lock service. This API can be called only by screen lock applications. This API uses a promise to return the result.

**System capability**: SystemCapability.MiscServices.ScreenLock

**Required permissions**: ohos.permission.ACCESS_SCREEN_LOCK_INNER

**System API**: This is a system API.

**Parameters** 

| Name   | Type  | Mandatory| Description                                                                                                               |
| --------- | ------ | ---- |-------------------------------------------------------------------------------------------------------------------|
| event     | String | Yes  | Event type. Options are as follows:<br>- **"unlockScreenResult"**: Screen unlock result.<br>- **"lockScreenResult"**: Screen lock result.<br>- **"screenDrawDone"**: Screen drawing is complete.|
| parameter | number | Yes  | Result.<br>- **0**: The operation is successful. For example, the screen is locked or unlocked successfully.<br>- **1**: The operation fails. For example, screen locking or unlocking fails.<br>- **2**: The operation is canceled. For example, screen locking or unlocking is canceled.|

**Return value** 

| Type              | Description                                          |
| ----------------- | ---------------------------------------------- |
| Promise\<boolean> | Promise used to return the result. The **value** true means that the event is sent successfully, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| Error Code| Error Message|
| -------- | ---------------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201  | permission denied.         |
| 202  | permission verification failed, application which is not a system application uses system API.         |
| 13200002  | the screenlock management service is abnormal.         |

**Example** 

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  screenLock.sendScreenLockEvent('unlockScreenResult', 0).then((result: Boolean) => {
    console.info(`Succeeded in Sending screenlock event. result: ${result}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to send screenlock event, Code: ${err.code}, message: ${err.message}`);
  });
  ```

## screenLock.requestStrongAuth<sup>12+</sup>

requestStrongAuth(reasonFlag: StrongAuthReasonFlags, userId: number): Promise&lt;void&gt;

Requests strong authentication for the specified user.

**System capability:** SystemCapability.MiscServices.ScreenLock

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| reasonFlag | [StrongAuthReasonFlags](#strongauthreasonflags12) | Yes | Flag indicating the reason for strong authentication. |
| userId | number | Yes | User ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| ID | Error Message |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed. A non-system application calls a system API. |
| 13200002 | the screenlock management service is abnormal. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

screenLock.requestStrongAuth(screenLock.StrongAuthReasonFlags.AFTER_BOOT, 100).then(() => {
  console.info('Succeeded in requesting strong auth.');
}).catch((err: BusinessError) => {
  console.error(`Failed to request strong auth, Code: ${err.code}, message: ${err.message}`);
});
```

## screenLock.getStrongAuth<sup>12+</sup>

getStrongAuth(userId: number): number

Obtains the strong authentication reason flag of the specified user.

**System capability:** SystemCapability.MiscServices.ScreenLock

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| userId | number | Yes | User ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| number | Strong authentication reason flag. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| ID | Error Message |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed. A non-system application calls a system API. |
| 13200002 | the screenlock management service is abnormal. |

**Example**

```ts
let strongAuth = screenLock.getStrongAuth(100);
console.info(`Strong auth flags: ${strongAuth}`);
```

## screenLock.setScreenLockDisabled<sup>12+</sup>

setScreenLockDisabled(disable: boolean, userId: number): Promise&lt;boolean&gt;

Disables or enables the screen lock for a specified user. This API takes effect only when no password is set.

**System capability:** SystemCapability.MiscServices.ScreenLock

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| disable | boolean | Yes | Whether to disable the screen lock. The value **true** means to disable the screen lock, and **false** means to enable it. |
| userId | number | Yes | User ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise object. Returning **true** indicates that the setting is successful, and returning **false** indicates that the setting fails. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| ID | Error Message |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 13200002 | the screenlock management service is abnormal. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

screenLock.setScreenLockDisabled(true, 100).then((result: boolean) => {
  console.info(`Succeeded in setting screen lock disabled. result: ${result}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen lock disabled, Code: ${err.code}, message: ${err.message}`);
});
```

## screenLock.isScreenLockDisabled<sup>12+</sup>

isScreenLockDisabled(userId: number): boolean

Queries whether the screen lock of a specified user is disabled.

**System capability:** SystemCapability.MiscServices.ScreenLock

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| userId | number | Yes | User ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| boolean | Whether the screen lock is disabled. The value **true** indicates that the screen lock is disabled, and **false** indicates the opposite. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| ID | Error Message |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 13200002 | the screenlock management service is abnormal. |

**Example**

```ts
let isDisabled = screenLock.isScreenLockDisabled(100);
console.info(`Screen lock disabled: ${isDisabled}`);
```

## screenLock.setScreenLockAuthState<sup>12+</sup>

setScreenLockAuthState(state: AuthState, userId: number, authToken: Uint8Array): Promise&lt;boolean&gt;

Sets the screen lock authentication state for the specified user.

**System capability:** SystemCapability.MiscServices.ScreenLock

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK_INNER

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| state | [AuthState](#authstate12) | Yes | Screen lock authentication state. |
| userId | number | Yes | User ID. |
| authToken | Uint8Array | Yes | Authentication token corresponding to the state. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise object. Returning true indicates that the setting is successful, and returning false indicates that the setting fails. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| ID | Error Message |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 13200002 | the screenlock management service is abnormal. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let authToken = new Uint8Array([1, 2, 3, 4]);
screenLock.setScreenLockAuthState(screenLock.AuthState.AUTHED_BY_CREDENTIAL, 100, authToken).then((result: boolean) => {
  console.info(`Succeeded in setting screen lock auth state. result: ${result}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set screen lock auth state, Code: ${err.code}, message: ${err.message}`);
});
```

## screenLock.getScreenLockAuthState<sup>12+</sup>

getScreenLockAuthState(userId: number): AuthState

Obtains the screen lock authentication state of the specified user.

**System capability:** SystemCapability.MiscServices.ScreenLock

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| userId | number | Yes | User ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| [AuthState](#authstate12) | Screen lock authentication state. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| ID | Error Message |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 201 | permission denied. |
| 202 | permission verification failed, application which is not a system application uses system API. |
| 13200002 | the screenlock management service is abnormal. |

**Example**

```ts
let authState = screenLock.getScreenLockAuthState(100);
console.info(`Screen lock auth state: ${authState}`);
```

## screenLock.isDeviceLocked<sup>20+</sup>

isDeviceLocked(userId: number): boolean

Checks whether the device is locked and requires identity authentication to unlock.

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| userId | number | Yes | User ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| boolean | Whether the device is locked. The value **true** indicates that the device is locked, and **false** indicates the opposite. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| ID | Error Message |
| -------- | -------- |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 13200002 | The screenlock management service is abnormal. |
| 13200004 | The userId is not same as the caller, and is not allowed for the caller. |

**Example**

```ts
let isDeviceLocked = screenLock.isDeviceLocked(100);
console.info(`Device locked: ${isDeviceLocked}`);
```

## screenLock.getUnlockPolicy

getUnlockPolicy(userId: number): UnlockPolicy

Obtains the authentication policy used to unlock the screen.

**Since**: 26.0.0

**System capability:** SystemCapability.MiscServices.ScreenLock

**Required permissions:** ohos.permission.ACCESS_SCREEN_LOCK

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | ---- | -------- |
| userId | number | Yes | User ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| [UnlockPolicy](#unlockpolicy) | Unlock policy. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Screen Lock Service Error Codes](errorcode-screenlock.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Permission verification failed: applications that are not system applications cannot use system API. |
| 13200002 | The screen lock management service is abnormal. |
| 13200004 | The userId is not the same as the caller, and the caller is not authorized. |

**Example**

```ts
let unlockPolicy = screenLock.getUnlockPolicy(100);
console.info(`Unlock policy: ${unlockPolicy}`);
```

