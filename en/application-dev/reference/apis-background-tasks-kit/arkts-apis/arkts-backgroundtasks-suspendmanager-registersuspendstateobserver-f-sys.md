# registerSuspendStateObserver (System API)

## Modules to Import

```TypeScript
import { suspendManager } from '@ohos.resourceschedule.suspendManager';
```

## registerSuspendStateObserver

```TypeScript
function registerSuspendStateObserver(observer: SuspendStateObserver, stateList: Array<FreezeState>, pidList?: Array<number>): void
```

Registers a suspend state observer to listen for application freeze state changes.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_SUSPEND_STATE

**Model restriction:** This API can be used only in the stage model.

<!--Device-suspendManager-function registerSuspendStateObserver(observer: SuspendStateObserver, stateList: Array<FreezeState>, pidList?: Array<int>): void--><!--Device-suspendManager-function registerSuspendStateObserver(observer: SuspendStateObserver, stateList: Array<FreezeState>, pidList?: Array<int>): void-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| observer | [SuspendStateObserver](arkts-backgroundtasks-suspendmanager-suspendstateobserver-i-sys.md) | Yes | The observer to register. |
| stateList | Array&lt;[FreezeState](arkts-backgroundtasks-suspendmanager-freezestate-e-sys.md)&gt; | Yes | List of the status type of the subscription. |
| pidList | Array&lt;number&gt; | No | Optional list of PIDs to filter. If not specified or empty, all processes state changes will trigger the callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| 31800005 | Parameter error. |
| 31800006 | Failed to get suspend manager service. |
