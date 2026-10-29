# offFocusedApplicationChanged

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## offFocusedApplicationChanged

```TypeScript
function offFocusedApplicationChanged(observerId: number): void
```

Unregisters the observer used to listen for focused application changes.

**Since:** 26.1.0

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**Model restriction:** This API can be used only in the stage model.

<!--Device-appManager-function offFocusedApplicationChanged(observerId: int): void--><!--Device-appManager-function offFocusedApplicationChanged(observerId: int): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observerId | number | Yes | ID of the observer registered, which is the listener ID returned by [onFocusedApplicationChanged](arkts-ability-appmanager-onfocusedapplicationchanged-f.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Connect to system server failed. |
| [16300004](../errorcode-ability.md#16300004-observer-does-not-exist) | The observer does not exist. |
