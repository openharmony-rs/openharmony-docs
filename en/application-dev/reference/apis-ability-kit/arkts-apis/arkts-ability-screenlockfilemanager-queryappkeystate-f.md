# queryAppKeyState

## Modules to Import

```TypeScript
import { screenLockFileManager } from '@kit.AbilityKit';
```

## queryAppKeyState

```TypeScript
function queryAppKeyState(): KeyStatus
```

Queries the status of the caller app's sensitive data key under the lock screen in synchronous mode.

**Since:** 18

**System capability:** SystemCapability.Security.ScreenLockFileManager

**Return value:**

| Type | Description |
| --- | --- |
| [KeyStatus](arkts-ability-screenlockfilemanager-keystatus-e.md) | Status of the key for sensitive data under lock screen. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | The specified SystemCapability name was not found. |
| [29300002](../errorcode-screenLockFileManager.md#29300002-system-service-abnormal) | The system ability works abnormally. |

**Examples**

```TypeScript
// Obtain the state of access permissions for sensitive data on the lock screen.
import { screenLockFileManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
    // Query the key status
    let keyStatus = screenLockFileManager.queryAppKeyState();
    // Determine the key status and handle different situations
    if (keyStatus === screenLockFileManager.KeyStatus.KEY_NOT_EXIST) {
        hilog.info(0x0000, 'testTag', 'Key does not exist.');
    } else if (keyStatus === screenLockFileManager.KeyStatus.KEY_RELEASED) {
        hilog.info(0x0000, 'testTag', 'Key has been released.');
    } else if (keyStatus === screenLockFileManager.KeyStatus.KEY_EXIST) {
        hilog.info(0x0000, 'testTag', 'Key exists.');
    }
} catch (err) {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'queryAppKeyState failed: %{public}s', message);
}
```
