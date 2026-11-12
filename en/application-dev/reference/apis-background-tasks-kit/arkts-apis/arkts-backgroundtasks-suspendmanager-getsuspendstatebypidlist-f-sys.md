# getSuspendStateByPidList (System API)

## Modules to Import

```TypeScript
import { suspendManager } from '@ohos.resourceschedule.suspendManager';
```

## getSuspendStateByPidList

```TypeScript
function getSuspendStateByPidList(pidList: Array<number>): Array<FreezeState>
```

Queries the frozen state list by the PID list of processes.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_SUSPEND_STATE

**Model restriction:** This API can be used only in the stage model.

<!--Device-suspendManager-function getSuspendStateByPidList(pidList: Array<int>): Array<FreezeState>--><!--Device-suspendManager-function getSuspendStateByPidList(pidList: Array<int>): Array<FreezeState>-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pidList | Array&lt;number&gt; | Yes | The PID list to query. Each PID must be a positive integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[FreezeState](arkts-backgroundtasks-suspendmanager-freezestate-e-sys.md)&gt; | The freeze state list. Returns an empty array if no matching states are found. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| 31800005 | Parameter error. |
| 31800006 | Failed to get suspend manager service. |
