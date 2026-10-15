# replyCustomEapData

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## replyCustomEapData

```TypeScript
function replyCustomEapData(result: CustomResult, data: EapData): void
```

Notifies the system of the extensible authentication result.

> **NOTE:** 
> 
> - If this callback is used to process received EAP data packets, the customized portion added by the server must be removed from the EAP data transmitted to the system.
> 
> - If this callback is used to process sent EAP data packets, the EAP data transmitted to the system is the EAP data with the customized portion added by the server.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

<!--Device-eap-function replyCustomEapData(result: CustomResult, data: EapData): void--><!--Device-eap-function replyCustomEapData(result: CustomResult, data: EapData): void-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [CustomResult](arkts-network-eap-customresult-e.md) | Yes | Extensible authentication result. |
| data | [EapData](arkts-network-eap-eapdata-i.md) | Yes | EAP data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [33200004](../errorcode-net-eap.md#33200004-invalid-eap-result-value) | Invalid result |
| [33200005](../errorcode-net-eap.md#33200005-invalid-data-length) | Invalid size of eap data |
| [33200009](../errorcode-net-eap.md#33200009-netmanager-not-exist) | netmanager stop |
| [33200099](../errorcode-net-eap.md#33200099-internal-program-error) | internal error |

**Examples**

```TypeScript
import {eap} from '@kit.NetworkKit';
let eapData:eap.EapData= {
  msgId: 1,
  eapBuffer: new Uint8Array([1, 2, 3, 4, 5]),
  bufferLen: 5,
};
let result = 1;

try {
  eap.replyCustomEapData(result, eapData);
  console.info('replyCustomEapData success');
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```
