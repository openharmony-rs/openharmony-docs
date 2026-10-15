# offCallTransferChange (System API)

## Modules to Import

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## offCallTransferChange

```TypeScript
function offCallTransferChange(callback?: Callback<boolean>): void
```

Cancel callback when the call forwarding status is updated.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-observer-function offCallTransferChange(callback?: Callback<boolean>): void--><!--Device-observer-function offCallTransferChange(callback?: Callback<boolean>): void-End-->

**System capability:** SystemCapability.Telephony.StateRegistry

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Indicates the callback to unsubscribe from the callTransferChange event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |
