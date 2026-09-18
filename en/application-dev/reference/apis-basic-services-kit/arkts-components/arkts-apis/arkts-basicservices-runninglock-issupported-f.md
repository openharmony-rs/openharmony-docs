# isSupported

## Modules to Import

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## isSupported

```TypeScript
function isSupported(type: RunningLockType): boolean
```

Checks whether a specified type of [RunningLock](arkts-basicservices-runninglock-runninglock-c.md) is supported.

**Since:** 9

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | Yes | Type of the running lock. The value must be an enum. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that the specified type of the running lock is supported, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**Examples**

```TypeScript
try {
    let isSupported = runningLock.isSupported(runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL);
    console.info('BACKGROUND type supported: ' + isSupported);
} catch(err) {
    console.error('check supported failed, err: ' + err);
}
```
