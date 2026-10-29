# onFocusedApplicationChanged

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## onFocusedApplicationChanged

```TypeScript
function onFocusedApplicationChanged(observer: FocusedApplicationObserver): number
```

Registers an observer to listen for focused application changes.

**Since:** 26.1.0

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**Model restriction:** This API can be used only in the stage model.

<!--Device-appManager-function onFocusedApplicationChanged(observer: FocusedApplicationObserver): int--><!--Device-appManager-function onFocusedApplicationChanged(observer: FocusedApplicationObserver): int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [FocusedApplicationObserver](arkts-ability-appmanager-focusedapplicationobserver-t.md) | Yes | Observer used to listen for focused application changes. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the observer registered. You can pass this ID to [offFocusedApplicationChanged](arkts-ability-appmanager-offfocusedapplicationchanged-f.md) to unregister the observer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Connect to system server failed. |
| 16000165 | The number of registered observers for the current application has reached the upper limit. |
