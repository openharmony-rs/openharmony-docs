# makeCallWithToken

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## makeCallWithToken

```TypeScript
function makeCallWithToken(phoneNumber: string, options?: MakeCallOptions): Promise<string>
```

Go to the dial screen and the called number is displayed.The authentication challenge value is returned.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.Contacts

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| phoneNumber | string | Yes | Indicates the called number. |
| options | [MakeCallOptions](arkts-telephony-call-makecalloptions-i.md) | No | Indicates additional information carried in the call. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return access token by the makeCall. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |
