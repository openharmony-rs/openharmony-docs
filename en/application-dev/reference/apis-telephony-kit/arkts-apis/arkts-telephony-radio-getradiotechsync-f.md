# getRadioTechSync

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## getRadioTechSync

```TypeScript
function getRadioTechSync(slotId: number): NetworkRadioTech
```

Obtains the RAT used in the CS and PS domains for the SIM card in the specified slot. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 18

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| [NetworkRadioTech](arkts-telephony-radio-networkradiotech-i.md) | RAT used in the CS and PS domains. The CS domain refers to the Circuit Switched domain, and the PS domain refers to the Packet Switched domain. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
let slotId: number = 0;
let networkRadioTech: radio.NetworkRadioTech = radio.getRadioTechSync(slotId);
console.info(`getRadioTechSync success, NetworkRadioTech->${JSON.stringify(networkRadioTech)}`);
```
