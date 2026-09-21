# isRunningLockTypeSupported

## Modules to Import

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## isRunningLockTypeSupported

```TypeScript
function isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback<boolean>): void
```

Checks whether a specified type of [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) is supported. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isSupported](arkts-basicservices-runninglock-issupported-f.md)

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | Yes | Type of the running lock. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the query result obtained, where the value **true** indicates that the specified type of the running lock is supported and **false** indicates the opposite. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
runningLock.isRunningLockTypeSupported(runningLock.RunningLockType.BACKGROUND, (err: Error, data: boolean) => {
    if (typeof err === 'undefined') {
        console.info('BACKGROUND lock support status: ' + data);
    } else {
        console.error('check BACKGROUND lock support status failed, err: ' + err);
    }
});
```


<a id="isrunninglocktypesupported-1"></a>

## isRunningLockTypeSupported

```TypeScript
function isRunningLockTypeSupported(type: RunningLockType): Promise<boolean>
```

Checks whether a specified type of [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) is supported. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isSupported](arkts-basicservices-runninglock-issupported-f.md)

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | Yes | Type of the running lock. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the specified type of the running lock is supported, and the value **false** indicates the opposite. |

**Examples**

```TypeScript
runningLock.isRunningLockTypeSupported(runningLock.RunningLockType.BACKGROUND)
.then((data: boolean) => {
    console.info('BACKGROUND lock support status: ' + data);
})
.catch((err: Error) => {
    console.error('check BACKGROUND lock support status failed, err: ' + err);
});
```
