# @ohos.runningLock (RunningLock)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b026b3aeef31e5c2ac5c14f8507bb3fa0dee1101 translatedAt=2026-11-10T04:11:34.322Z pushedAt=2026-11-10T07:03:46.145Z nl=1 -->

The **runningLock** module provides APIs for creating, querying, holding, and releasing running locks. A running lock enables the proximity sensor to turn on or off the screen, or prevents the device from entering sleep mode when the screen is off. For details about the running lock types, see [RunningLockType](#runninglocktype).

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
| type   | [RunningLockType](#runninglocktype) | Yes  | Type of the running lock. The value must be an enum.|

**Returns**

| Type   | Description                                   |
| ------- | --------------------------------------- |
| boolean | The value **true** indicates that the specified type of the running lock is supported, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Example**

```js
try {
    let isSupported = runningLock.isSupported(runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL);
    console.info('BACKGROUND type supported: ' + isSupported);
} catch(err) {
    console.error('check supported failed, err: ' + err);
}
```

## runningLock.create<sup>9+</sup>

create(name: string, type: RunningLockType, callback: AsyncCallback&lt;RunningLock&gt;): void

Creates a **RunningLock** object. This API uses an asynchronous callback to return the result. After the lock object is created, call **hold()** to lock and hold the lock so that the lock takes effect. It is not recommended to call **create** concurrently in multiple Worker/TaskPool threads to create lock objects.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Parameters**

| Name  | Type                                      | Mandatory| Description                                                        |
| -------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| name     | string                                     | Yes  | Name of the **RunningLock** object. The value must be a string.                                                  |
| type     | [RunningLockType](#runninglocktype)        | Yes  | Type of the **RunningLock** object. The value must be an enum.                                          |
| callback | AsyncCallback<[RunningLock](#runninglock)> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and data is the created **RunningLock** object. Otherwise, **err** is an error object. **AsyncCallback** has encapsulated an API of the **RunningLock** class.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Parameter verification failed. |
| 201     | If the permission is denied.|

**Example**

```js

runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error, lock: runningLock.RunningLock) => {
    if (typeof err === 'undefined') {
        console.info('created running lock: ' + lock);
    } else {
        console.error('create running lock failed, err: ' + err);
    }
});
```

## runningLock.create<sup>9+</sup>

create(name: string, type: RunningLockType): Promise&lt;RunningLock&gt;

Creates a **RunningLock** object. This API uses a promise to return the result. After the lock object is created, call **hold()** to lock and hold the lock so that the lock takes effect. It is not recommended to call **create** concurrently in multiple Worker/TaskPool threads to create lock objects.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Parameters**

| Name| Type                               | Mandatory| Description              |
| ------ | ----------------------------------- | ---- | ------------------ |
| name   | string                              | Yes  | Name of the **RunningLock** object. The value must be a string.|
| type   | [RunningLockType](#runninglocktype) | Yes  | Type of the **RunningLock** object. The value must be an enum.|

**Returns**

| Type                                      | Description                                |
| ------------------------------------------ | ------------------------------------ |
| Promise&lt;[RunningLock](#runninglock)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message   |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Parameter verification failed. |
| 201     | If the permission is denied.|

**Example**

```js

runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL)
.then((lock: runningLock.RunningLock) => {
    console.info('created running lock: ' + lock);
})
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
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
| type     | [RunningLockType](#runninglocktype) | Yes  | Type of the running lock.                                        |
| callback | AsyncCallback&lt;boolean&gt;        | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the query result obtained, where the value **true** indicates that the specified type of the running lock is supported and **false** indicates the opposite. Otherwise, **err** is an error object.|

**Example**

```js
runningLock.isRunningLockTypeSupported(runningLock.RunningLockType.BACKGROUND, (err: Error, data: boolean) => {
    if (typeof err === 'undefined') {
        console.info('BACKGROUND lock support status: ' + data);
    } else {
        console.error('check BACKGROUND lock support status failed, err: ' + err);
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
.catch((err: Error) => {
    console.error('check BACKGROUND lock support status failed, err: ' + err);
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
| callback | AsyncCallback<[RunningLock](#runninglock)> | Yes  | Callback used to return the result. If a lock is successfully created, **err** is **undefined** and **data** is the created **RunningLock**. Otherwise, **err** is an error object. **AsyncCallback** has encapsulated an API of the **RunningLock** class.|

**Example**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND, (err: Error, lock: runningLock.RunningLock) => {
    if (typeof err === 'undefined') {
        console.info('created running lock: ' + lock);
    } else {
        console.error('create running lock failed, err: ' + err);
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
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
});
```

## RunningLock

Defines a lock that prevents the system from sleeping or turns on or off the screen by using the proximity sensor. Different lock types have different functions. For details, see [RunningLockType](#runninglocktype).
 
This method must be used together with [create](#runninglockcreate9), [hold](#hold9), and [unhold](#unhold9). For details, see the example.
 
A **RunningLock** object cannot be shared across multiple Worker/TaskPool threads. The **hold()**, **unhold()**, and **isHolding()** methods of the same **RunningLock** instance must be called in the same thread. Sharing the instance across threads may cause inconsistent lock states without reporting an error. After the power service restarts abnormally, the created **RunningLock** object remains valid, but the holding state of the lock may be lost. It is recommended to check the lock state using **isHolding()** in the service restart scenario and call **hold()** again if necessary. When the JS object of **RunningLock** is garbage collected, the lock held at the underlying layer is automatically released. To hold the lock for a long time, keep a reference to the **RunningLock** object.

### hold<sup>9+</sup>

hold(timeout: number): void

Locks and holds a **RunningLock** object. This API applies to scenarios where an app needs to run continuously in the background (such as background download and long-time location tracking) and needs to prevent the system from sleeping, or scenarios where proximity light control of screen on/off is required during a call. After this API is called, call **unhold()** to release the lock when it is no longer needed, or set a timeout release time so that the system releases the lock automatically upon timeout. This API is used in pair with **unhold()**. Failure to release the lock keeps the sleep prevention or screen on/off control in effect. Repeated calls to **hold()** do not report an error. Note: If **hold(-1)** (permanent lock) is called first and then **hold(timeout)** (timed lock) is called, the lock is released after timeout (in milliseconds), that is, the **timeout** parameter of the later call overrides the previous one. To update the timeout, you are advised to call **unhold()** to release the lock first and then call **hold(newTimeout)**.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Parameters**

| Name | Type  | Mandatory| Description                                     |
| ------- | ------ | ---- | ----------------------------------------- |
| timeout | number | Yes  | Duration for locking and holding the **RunningLock** object, in ms.<br>The value must be a number:<br>**-1**: The lock is permanently held and needs to be released automatically.<br>**0**: The lock is released 3 seconds after the timer expires by default.<br>> 0: The lock is released based on the input value after the timer expires.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message    |
|---------|----------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 201     | If the permission is denied.|

**Example**

```ts
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static holdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            RunningLockTest.recordLock.hold(500);
            console.info('hold running lock success');
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error, lock: runningLock.RunningLock) => {
                if (typeof err === 'undefined') {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    try {
                        lock.hold(500);
                        console.info('hold running lock success');
                    } catch(err) {
                        console.error('hold running lock failed, err: ' + err);
                    }
                } else {
                    console.error('create running lock failed, err: ' + err);
                }
            });
        }
    }
}
```

### unhold<sup>9+</sup>

unhold(): void

Releases a **RunningLock** object. This API is used in pair with **hold()**. After **hold()** is called to lock the object, call this API to release the object. Calling **unhold()** on a lock that is not held does not report an error and is treated as  no operation. You are advised to confirm the holding state of the lock using **isHolding()** before calling **unhold()**.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

**Required permission**: ohos.permission.RUNNING_LOCK

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code  | Error Message    |
|---------|----------|
| 201     | If the permission is denied.|


**Example**

```ts
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static unholdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            RunningLockTest.recordLock.unhold();
            console.info('unhold running lock success');
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error, lock: runningLock.RunningLock) => {
                if (typeof err === 'undefined') {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    try {
                        lock.unhold();
                        console.info('unhold running lock success');
                    } catch(err) {
                        console.error('unhold running lock failed, err: ' + err);
                    }
                } else {
                    console.error('create running lock failed, err: ' + err);
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
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error, lock: runningLock.RunningLock) => {
                if (typeof err === 'undefined') {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    let isHolding = lock.isHolding();
                    console.info('check running lock holding status: ' + isHolding);
                } else {
                    console.error('create running lock failed, err: ' + err);
                }
            });
        }
    }
}
```

### lock<sup>(deprecated)</sup>

lock(timeout: number): void

Locks and holds a **RunningLock** object.

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
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
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
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
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
.catch((err: Error) => {
    console.error('check running lock used status failed, err: ' + err);
});
```

## RunningLockType

Enumerates the types of **RunningLock** objects.

**System capability**: SystemCapability.PowerManager.PowerManager.Core

| Name                             | Value  | Description                                                        |
| --------------------------------- | ---- | ------------------------------------------------------------ |
| BACKGROUND<sup>(deprecated)</sup> | 1    | A lock that prevents the system from hibernating when the screen is off.<br>**NOTE**<br>This parameter is supported since API version 7 and deprecated since API version 10.|
| PROXIMITY_SCREEN_CONTROL          | 2    | A lock that enables the proximity sensor and turns on or off the screen based on the distance between the sensor and the obstacle. |
| BACKGROUND_USER_IDLE<sup>23+</sup>| 129  | Background idle task lock that prevents the system from entering sleep automatically. Holding the lock ensures that the system does not enter automatic sleep after a period of user inactivity.<br>**Note:** It cannot prevent the system from entering forced sleep in scenarios such as closing the lid of a PC. The user must listen for [COMMON_EVENT_ENTER_FORCE_SLEEP](./common_event/commonEventManager-definitions.md#common_event_enter_force_sleep12) and release the lock after the event is received. The behavior of this lock type varies by device. For details, see [Preventing the System from Entering Sleep When Idle Development Guide](../../basic-services/powermgr/runningLock/runningLock-dev.md). When the device does not support the **BACKGROUND_USER_IDLE** type, **create()** still returns success, but the subsequent **hold()** call does not take effect and no error is reported. You are advised to call **isSupported()** after **create()** to check whether the device supports this type.|
