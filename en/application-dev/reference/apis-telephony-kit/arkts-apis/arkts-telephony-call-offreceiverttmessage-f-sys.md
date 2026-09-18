# offReceiveRttMessage (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## offReceiveRttMessage

```TypeScript
function offReceiveRttMessage(callback?: Callback<RttMessageInfo>): void
```

Unsubscribe from the rtt message event.

**Since:** 22

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RttMessageInfo](arkts-telephony-call-rttmessageinfo-i-sys.md)&gt; | No | Indicates the callback for getting the rtt message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| 8400001 | Invalid parameter value. |
| 8400002 | Operation failed. Cannot connect to service. |
| 8400003 | System internal error. |
| 8400999 | Unknown error code. |
