# getContractInfo (System API)

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## getContractInfo

```TypeScript
function getContractInfo(slotId: number, requestData: ContractRequestData) : Promise<string>
```

Obtains the encrypted eSIM ID and other information required for enabling eSIM.

**Since:** 20

**Required permissions:** ohos.permission.GET_TELEPHONY_ESIM_STATE

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |
| requestData | [ContractRequestData](arkts-telephony-esim-contractrequestdata-i-sys.md) | Yes | Information to be encrypted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the encrypted information in the Tag-Length-Value (TLV) format. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3120001](../errorcode-telephony.md#3120001-service-connection-error) | Service connection failed. |
| [3120002](../errorcode-telephony.md#3120002-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
try {
    let request: eSIM.ContractRequestData = {
        publicKey: "",
        nonce: "",
        pkid: ""
    }
    let contractInfo: string = await eSIM.getContractInfo(1, request);
    console.info(`contract info is:` + contractInfo);
} catch (err) {
    console.error(`getContractInfo, promise: err->${JSON.stringify(err)}`)
}
```
