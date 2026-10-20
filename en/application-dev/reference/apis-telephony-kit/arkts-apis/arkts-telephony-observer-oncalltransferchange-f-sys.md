# onCallTransferChange (System API)

## Modules to Import

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## onCallTransferChange

```TypeScript
function onCallTransferChange(slotId: number, callback: Callback<boolean>): void
```

Callback when the call forwarding status is updated. This callback is invoked when the unconditional call forwarding status of a specified card updates and the observer is added to monitor the updates.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-observer-function onCallTransferChange(slotId: int, callback: Callback<boolean>): void--><!--Device-observer-function onCallTransferChange(slotId: int, callback: Callback<boolean>): void-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID. <br>The value should be an integer. <br>- **0**: card slot 1. <br>- **1**: card slot 2. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates calltransfer enabled, and **false** indicates calltransfer disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |
