# onLaunchServiceObserver (System API)

## Modules to Import

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## onLaunchServiceObserver

```TypeScript
function onLaunchServiceObserver(observer: LaunchServiceObserver): number
```

Register an observer to listen to the LaunchService status and process status changes.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_DAEMON_SERVICE

**Model restriction:** This API can be used only in the stage model.

<!--Device-launchServiceManager-function onLaunchServiceObserver(observer: LaunchServiceObserver): int--><!--Device-launchServiceManager-function onLaunchServiceObserver(observer: LaunchServiceObserver): int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [LaunchServiceObserver](arkts-ability-launchservicemanager-launchserviceobserver-t-sys.md) | Yes | Watcher for the LaunchService status and process status changes. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the observer registered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | System service connection failed. |
| 16000165 | The number of registered observers for the current application has reached the upper limit. |
