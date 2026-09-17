# isImsSwitchEnabledSync (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## isImsSwitchEnabledSync

```TypeScript
function isImsSwitchEnabledSync(slotId: number): boolean
```

Checks whether the IMS service is enabled. This API returns the result synchronously.

**Since:** 12

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value indicating whether the IMS service is enabled. The value **true** indicates that the IMS service is enabled, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
let slotId: number = 0;
try {
    let isEnabled: boolean = call.isImsSwitchEnabledSync(slotId);
    console.info(`isImsSwitchEnabledSync success : ${isEnabled}`);
} catch (error) {
    console.error(`isImsSwitchEnabledSync fail : err->${JSON.stringify(error)}`);  
}
```
