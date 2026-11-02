# @ohos.runningLock (RunningLock)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

This module provides APIs for performing operations related to the running locks, such as preventing the system from sleeping and turning the screen on or off by using the proximity sensor. It is applicable to scenarios where the background app needs to keep running after the screen is turned off, the proximity sensor is used to turn the screen on or off, and the system is prevented from automatically sleeping during idle hours. This ensures the continuous execution of key tasks. This includes operations such as creating, querying, holding, and releasing locks. For details about the lock types, see [RunningLockType](#runninglocktype).

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import {runningLock} from '@kit.BasicServicesKit';
```

## runningLock.isSupported<sup>9+</sup>

isSupported(type: RunningLockType): boolean

Checks whether a specified type of **RunningLock** is supported.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name| Type                               | Mandatory| Description                |
| ------ | ----------------------------------- | ---- | -------------------- |
| type   | [RunningLockType](#runninglocktype) | Yes  | Type of the running lock.|

**Returns**

| Type   | Description                                   |
| ------- | --------------------------------------- |
| boolean | The value **true** indicates that the specified type of the running lock is supported, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Example**

```js
try {
    let isSupported = runningLock.isSupported(runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL);
    console.info('PROXIMITY_SCREEN_CONTROL type supported: ' + isSupported);
} catch (err) {
    console.error(`Failed to check supported. Code: ${err.code}, message: ${err.message}`);
}
```

## runningLock.create<sup>9+</sup>

create(name: string, type: RunningLockType, callback: AsyncCallback&lt;RunningLock&gt;): void

Creates a **RunningLock** object. This API uses an asynchronous callback to return the result. After creating a lock object, you need to call the **hold()** method to lock and hold the lock for the lock function to take effect.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Parameters**

| Name  | Type                                      | Mandatory| Description                                                        |
| -------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| name     | string                                     | Yes  | Name of the **RunningLock** object. A recommended name consists of the package or class name and a suffix.                                                  |
| type | [RunningLockType](#runninglocktype) | Yes| Type of the **RunningLock** object to be created. The precautions for using different lock types vary. For details, see [RunningLockType](#runninglocktype).|
| callback | AsyncCallback<[RunningLock](#runninglock)> | Yes  | Callback used to return the result. If a lock is successfully created, **err** is **undefined** and **data** is the created **RunningLock**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| 201     | If the permission is denied.|

**Example**

```js

runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: BusinessError, lock: runningLock.RunningLock) => {
    if (err) {
        console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('created running lock: ' + lock); // After creating and saving a lock object, you need to use the hold and unhold methods.
    }
});
```

## runningLock.create<sup>9+</sup>

create(name: string, type: RunningLockType): Promise&lt;RunningLock&gt;

Creates a **RunningLock** object. This API uses a promise to return the result. After creating a lock object, you need to call the **hold()** method to lock and hold the lock for the lock function to take effect.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Parameters**

| Name| Type                               | Mandatory| Description              |
| ------ | ----------------------------------- | ---- | ------------------ |
| name   | string                              | Yes  | Name of the **RunningLock** object. A recommended name consists of the package or class name and a suffix.|
| type | [RunningLockType](#runninglocktype) | Yes| Type of the **RunningLock** object to be created. The precautions for using different lock types vary. For details, see [RunningLockType](#runninglocktype).|


**Returns**

| Type                                      | Description                                |
| ------------------------------------------ | ------------------------------------ |
| Promise&lt;[RunningLock](#runninglock)&gt; | Promise used to return the result. If the object is created successfully, a **RunningLock** object is returned. Otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| 201     | If the permission is denied.|

**Example**

```js

runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL)
.then((lock: runningLock.RunningLock) => {
    console.info('created running lock: ' + lock); // After creating and saving a lock object, you need to use the hold and unhold methods.
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```

## runningLock.isRunningLockTypeSupported<sup>(deprecated)</sup>

isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a specified type of **RunningLock** is supported. This API uses an asynchronous callback to return the result.

> **NOTE**<br>This API is supported since API version 7 and deprecated since API version 9. You are advised to use [runningLock.isSupported](#runninglockissupported9) instead.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name  | Type                               | Mandatory| Description                                                        |
| -------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [RunningLockType](#runninglocktype) | Yes  | Type of the running lock.|
| callback | AsyncCallback&lt;boolean&gt;        | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the query result obtained, where the value **true** indicates that the specified type of the running lock is supported and **false** indicates the opposite. Otherwise, **err** is an error object.|

**Example**

```js
runningLock.isRunningLockTypeSupported(runningLock.RunningLockType.BACKGROUND, (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`Failed to check BACKGROUND lock support status. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('BACKGROUND lock support status: ' + data);
    }
});
```

## runningLock.isRunningLockTypeSupported<sup>(deprecated)</sup>

isRunningLockTypeSupported(type: RunningLockType): Promise&lt;boolean>

Checks whether a specified type of **RunningLock** is supported. This API uses a promise to return the result.

> **NOTE**<br>This API is supported since API version 7 and deprecated since API version 9. You are advised to use [runningLock.isSupported](#runninglockissupported9) instead.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Parameters**

| Name| Type                               | Mandatory| Description                |
| ------ | ----------------------------------- | ---- | -------------------- |
| type   | [RunningLockType](#runninglocktype) | Yes  | Type of the running lock.|

**Returns**

| Type                  | Description                                                |
| ---------------------- | ---------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the specified type of the running lock is supported, and the value **false** indicates the opposite.|

**Example**

```js
runningLock.isRunningLockTypeSupported(runningLock.RunningLockType.BACKGROUND)
.then((data: boolean) => {
    console.info('BACKGROUND lock support status: ' + data);
})
.catch((err: BusinessError) => {
    console.error(`Failed to check BACKGROUND lock support status. Code: ${err.code}, message: ${err.message}`);
});
```

## runningLock.createRunningLock<sup>(deprecated)</sup>

createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback&lt;RunningLock&gt;): void

Creates a **RunningLock** object. This API uses an asynchronous callback to return the result.

> **NOTE**<br>This API is supported since API version 7 and deprecated since API version 9. You are advised to use [runningLock.create](#runninglockcreate9) instead.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Parameters**

| Name  | Type                                      | Mandatory| Description                                                        |
| -------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| name     | string                                     | Yes  | Name of the **RunningLock** object. A recommended name consists of the package or class name and a suffix.                  |
| type     | [RunningLockType](#runninglocktype)        | Yes  | Type of the **RunningLock** object to be created.                                          |
| callback | AsyncCallback&lt;[RunningLock](#runninglock)&gt; | Yes| Callback used to return the result. If a lock is successfully created, **err** is **undefined** and **data** is the created **RunningLock**. Otherwise, **err** is an error object.|

**Example**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND, (err: BusinessError, lock: runningLock.RunningLock) => {
    if (err) {
        console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('created running lock: ' + lock);
    }
});
```

## runningLock.createRunningLock<sup>(deprecated)</sup>

createRunningLock(name: string, type: RunningLockType): Promise&lt;RunningLock&gt;

Creates a **RunningLock** object. This API uses a promise to return the result.

> **NOTE**<br>This API is supported since API version 7 and deprecated since API version 9. You are advised to use [runningLock.create](#runninglockcreate9) instead.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Parameters**

| Name| Type                               | Mandatory| Description              |
| ------ | ----------------------------------- | ---- | ------------------ |
| name   | string                              | Yes  | Name of the **RunningLock** object. A recommended name consists of the package or class name and a suffix.|
| type   | [RunningLockType](#runninglocktype) | Yes  | Type of the **RunningLock** object to be created.|

**Returns**

| Type                                      | Description                                |
| ------------------------------------------ | ------------------------------------ |
| Promise&lt;[RunningLock](#runninglock)&gt; | Promise used to return the result.|

**Example**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    console.info('created running lock: ' + lock);
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```

## RunningLock

Defines a lock that prevents the system from sleeping or turns on or off the screen by using the proximity sensor. Different lock types have different functions. For details, see [RunningLockType](#runninglocktype).

This method must be used together with [create](#runninglockcreate9), [hold](#hold9), and [unhold](#unhold9). For details, see the example.

### hold<sup>9+</sup>

hold(timeout: number): void

Locks and holds a **RunningLock** object. This method is applicable to scenarios where the system needs to be prevented from sleeping when an app needs to run continuously in the background (for example, background download or long-time location tracking) or when the proximity sensor needs to be used to turn the screen on or off during a call. After this method is called, you must call the **unhold()** method to release the lock when the lock is no longer needed, or set a timeout interval for automatic release by the system when calling this method. This method is used in pairs with the **unhold()** method. If the lock is not released, the sleep prevention or screen on/off control function will continue to take effect.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Parameters**

| Name | Type  | Mandatory| Description                                     |
| ------- | ------ | ---- | ----------------------------------------- |
| timeout | number | Yes  | Duration for locking and holding the **RunningLock** object, in ms.<br>**-1**: The lock is permanently held and needs to be released automatically.<br>**0**: The lock is released 3 seconds after the timer expires by default.<br>> 0: The lock is released based on the input value after the timer expires.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message    |
|---------|----------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| 201     | If the permission is denied.|

**Example**

```ts
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static holdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            try {
                RunningLockTest.recordLock.hold(500);
                console.info('hold running lock success');
            } catch(err) {
                console.error(`Failed to hold running lock. Code: ${err.code}, message: ${err.message}`);
            }
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: BusinessError, lock: runningLock.RunningLock) => {
                if (err) {
                    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
                } else {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    try {
                        lock.hold(500);
                        console.info('hold running lock success');
                    } catch(err) {
                        console.error(`Failed to hold running lock. Code: ${err.code}, message: ${err.message}`);
                    }
                }
            });
        }
    }
}
```

### unhold<sup>9+</sup>

unhold(): void

Releases a **RunningLock** object. This method is used together with **hold()**. After calling **hold()** to lock a **RunningLock** object, call this method to release the lock.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message    |
|---------|----------|
| 201     | If the permission is denied.|


**Example**

```ts
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static unholdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            try {
                RunningLockTest.recordLock.unhold();
                console.info('unhold running lock success');
            } catch(err) {
                console.error(`Failed to unhold running lock. Code: ${err.code}, message: ${err.message}`);
            }
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: BusinessError, lock: runningLock.RunningLock) => {
                if (err) {
                    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
                } else {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    try {
                        lock.unhold();
                        console.info('unhold running lock success');
                    } catch(err) {
                        console.error(`Failed to unhold running lock. Code: ${err.code}, message: ${err.message}`);
                    }
                }
            });
        }
    }
}
```

### isHolding<sup>9+</sup>

isHolding(): boolean

Checks the hold status of the **RunningLock** object.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Returns**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | The value **true** indicates that the **RunningLock** object is held; and the value **false** indicates that the **RunningLock** object is released.|

**Example**

```ts
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static isHoldingRunningLock(): void {
        if (RunningLockTest.recordLock) {
            let isHolding = RunningLockTest.recordLock.isHolding();
            console.info('check running lock holding status: ' + isHolding);
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: BusinessError, lock: runningLock.RunningLock) => {
                if (err) {
                    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
                } else {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    let isHolding = lock.isHolding();
                    console.info('check running lock holding status: ' + isHolding);
                }
            });
        }
    }
}
```

### lock<sup>(deprecated)</sup>

lock(timeout: number): void

Holds a **RunningLock** object.

> **NOTE**<br>This API is supported since API version 7 and deprecated since API version 9. You are advised to use [RunningLock.hold](#hold9) instead.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Parameters**

| Name | Type  | Mandatory| Description                                     |
| ------- | ------ | ---- | ----------------------------------------- |
| timeout | number | Yes  | Duration for locking and holding the **RunningLock** object, in ms.|

**Example**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    lock.lock(500);
    console.info('create running lock and lock success');
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```

### unlock<sup>(deprecated)</sup>

unlock(): void

Releases a **RunningLock** object.

> **NOTE**<br>This API is supported since API version 7 and deprecated since API version 9. You are advised to use [RunningLock.unhold](#unhold9) instead.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Example**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    lock.unlock();
    console.info('create running lock and unlock success');
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```

### isUsed<sup>(deprecated)</sup>

isUsed(): boolean

Checks the hold status of the **RunningLock** object.

> **NOTE**<br>This API is supported since API version 7 and deprecated since API version 9. You are advised to use [RunningLock.isHolding](#isholding9) instead.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Returns**
| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | The value **true** indicates that the **RunningLock** object is held; and the value **false** indicates that the **RunningLock** object is released.|

**Example**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    let isUsed = lock.isUsed();
    console.info('check running lock used status: ' + isUsed);
})
.catch((err: BusinessError) => {
    console.error(`Failed to check running lock used status. Code: ${err.code}, message: ${err.message}`);
});
```

## RunningLockType

Enumerates the types of **RunningLock** objects.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

| Name                             | Value  | Description                                                        |
| --------------------------------- | ---- | ------------------------------------------------------------ |
| BACKGROUND<sup>(deprecated)</sup> | 1    | A lock that prevents the system from hibernating when the screen is off.<br>**NOTE**<br>This parameter is supported since API version 7 and deprecated since API version 10.|
| PROXIMITY_SCREEN_CONTROL          | 2    | A lock that enables the proximity sensor and turns on or off the screen based on the distance between the sensor and the obstacle. |
| BACKGROUND_USER_IDLE<sup>23+</sup>| 129  | A background lock that prevents the system from automatically entering sleep mode when the user is inactive for a period of time.<br>Note: This lock cannot prevent the system from entering the forced sleep state in scenarios such as closing the PC lid. The user must listen for the [COMMON_EVENT_ENTER_FORCE_SLEEP](./common_event/commonEventManager-definitions.md#common_event_enter_force_sleep12) event and release this lock after receiving the event. The behavior of this lock varies with devices. For details about how to use this type of lock, see [Preventing the Idle System from Entering Sleep Mode](../../basic-services/powermgr/runningLock/runningLock-dev.md).|
