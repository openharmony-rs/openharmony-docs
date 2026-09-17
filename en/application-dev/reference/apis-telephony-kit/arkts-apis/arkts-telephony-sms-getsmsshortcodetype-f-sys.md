# getSmsShortCodeType (System API)

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## getSmsShortCodeType

```TypeScript
function getSmsShortCodeType(slotId: number, destAddr: string): Promise<SmsShortCodeType>
```

Get the SMS short code type of the destination address.

**Since:** 23

**Required permissions:** ohos.permission.SEND_MESSAGES

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the ID of the slot holding the SIM card for sending SMS messages. The value `0` indicates card slot 1, and the value `1` indicates card slot 2. |
| destAddr | string | Yes | Indicates the destination address of the sending SMS.<br>Value range:[0,+∞) |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SmsShortCodeType](arkts-telephony-sms-smsshortcodetype-e-sys.md)&gt; | Returns the SMS short code type of the sending destination address. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Nonsystem applications use system APIs. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | Do not have sim card. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |
