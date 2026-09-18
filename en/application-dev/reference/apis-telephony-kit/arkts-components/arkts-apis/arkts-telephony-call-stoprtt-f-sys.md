# stopRtt (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## stopRtt

```TypeScript
function stopRtt(callId: number, type: ImsRttMode): Promise<void>
```

Stop rtt.

**Since:** 22

**Required permissions:** ohos.permission.PLACE_CALL

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Indicates the identifier of the call. |
| type | [ImsRttMode](arkts-telephony-call-imsrttmode-e-sys.md) | Yes | Indicates the type of operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the stopRtt. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| 8400001 | Invalid parameter value. |
| 8400002 | Operation failed. Cannot connect to service. |
| 8400003 | System internal error. |
| 8400999 | Unknown error code. |
