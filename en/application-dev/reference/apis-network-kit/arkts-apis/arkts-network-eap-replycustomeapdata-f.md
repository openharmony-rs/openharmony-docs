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
