# createRunningLock

## Modules to Import

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## createRunningLock

```TypeScript
function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void
```

Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [create](arkts-basicservices-runninglock-create-f.md)

**Required permissions:** ohos.permission.RUNNING_LOCK

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Indicates the [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) name. A recommended name consists of the package or class name and a suffix. |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | Yes | Indicates the [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md). |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[RunningLock](arkts-basicservices-runninglock-runninglock-c.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and data is the created **RunningLock** object. Otherwise, **err** is an error object. **AsyncCallback** has encapsulated an API of the **RunningLock** class. |

**Examples**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND, (err: Error, lock: runningLock.RunningLock) => {
    if (typeof err === 'undefined') {
        console.info('created running lock: ' + lock);
    } else {
        console.error('create running lock failed, err: ' + err);
    }
});
```

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    console.info('created running lock: ' + lock);
})
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
});
```


## createRunningLock

```TypeScript
function createRunningLock(name: string, type: RunningLockType): Promise<RunningLock>
```

Creates a [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [create](arkts-basicservices-runninglock-create-f.md)

**Required permissions:** ohos.permission.RUNNING_LOCK

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Indicates the [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) name. A recommended name consists of the package or class name and a suffix. |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | Yes | Indicates the [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RunningLock](arkts-basicservices-runninglock-runninglock-c.md)&gt; | Promise used to return the [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) object. |

**Examples**

See [createRunningLock](#createrunninglock)
