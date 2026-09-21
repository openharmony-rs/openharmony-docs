# create

## Modules to Import

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## create

```TypeScript
function create(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void
```

Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.RUNNING_LOCK

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the **RunningLock** object. The value must be a string. |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | Yes | Type of the **RunningLock** object. The value must be an enum. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[RunningLock](arkts-basicservices-runninglock-runninglock-c.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and data is the created **RunningLock** object. Otherwise, **err** is an error object. **AsyncCallback** has encapsulated an API of the **RunningLock** class. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | If the permission is denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |

**Examples**

```TypeScript
runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error, lock: runningLock.RunningLock) => {
    if (typeof err === 'undefined') {
        console.info('created running lock: ' + lock);
    } else {
        console.error('create running lock failed, err: ' + err);
    }
});
```


<a id="create-1"></a>

## create

```TypeScript
function create(name: string, type: RunningLockType): Promise<RunningLock>
```

Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.RUNNING_LOCK

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the **RunningLock** object. The value must be a string. |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | Yes | Type of the **RunningLock** object. The value must be an enum. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RunningLock](arkts-basicservices-runninglock-runninglock-c.md)&gt; | Promise used to return the [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | If the permission is denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |

**Examples**

```TypeScript
runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL)
.then((lock: runningLock.RunningLock) => {
    console.info('created running lock: ' + lock);
})
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
});
```
