# makeDirectCall

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## makeDirectCall

```TypeScript
function makeDirectCall(phoneNumber: string): Promise<void>
```

Application make calls with one tap.

**Since:** 26.0.1

**Required permissions:** ohos.permission.DIRECT_CALL

**Model restriction:** This API can be used only in the stage model.

<!--Device-call-function makeDirectCall(phoneNumber: string): Promise<void>--><!--Device-call-function makeDirectCall(phoneNumber: string): Promise<void>-End-->

**System capability:** SystemCapability.Telephony.CallManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Indicates the called number. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| 8300005 | Airplane mode is on. |
| 8300006 | Network not in service. |
