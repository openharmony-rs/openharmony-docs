# getCallTransferInfo

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## getCallTransferInfo

```TypeScript
function getCallTransferInfo(type: CallTransferType, number: string): Promise<CallTransferResult>
```

Obtains call transfer information with the phone number. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_CALL_TRANSFER_INFO

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Telephony.CallManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [CallTransferType](arkts-telephony-call-calltransfertype-e.md) | Yes | Type of call forwarding to be obtained. |
| number | string | Yes | Number used to obtain the call forwarding status. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CallTransferResult](arkts-telephony-call-calltransferresult-i.md)&gt; | Promise used to return the call forwarding result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8401002](../errorcode-telephony.md#8401002-incorrect-number) | Invalid input call number. |
| [8401003](../errorcode-telephony.md#8401003-frequent-operations) | Operation too frequent. |

**Examples**

```TypeScript
import { call } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let type: call.CallTransferType = call.CallTransferType.TRANSFER_TYPE_UNCONDITIONAL;
let number: string = "138xxxxxxxx";

call.getCallTransferInfo(type, number)
    .then((data: call.CallTransferResult) => {
        console.info(`getCallTransferInfo success, data->${JSON.stringify(data)}`);
    })
    .catch((err:BusinessError) => {
        console.error(`getCallTransferInfo fail, err->${JSON.stringify(err)}`);
    });
```
