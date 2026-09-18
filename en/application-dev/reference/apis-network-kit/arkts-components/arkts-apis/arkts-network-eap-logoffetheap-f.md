# logOffEthEap

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## logOffEthEap

```TypeScript
function logOffEthEap(netId: number): void
```

Revokes the EAP-authenticated state of an Ethernet NIC.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.NetManager.Eap

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netId | number | Yes | ID of the Ethernet NIC. If the default value **-1** is specified, the system automatically matches the Ethernet NIC to initiate EAP authentication. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [33200001](../errorcode-net-eap.md#33200001-invalid-netid) | Invalid netId |
| [33200002](../errorcode-net-eap.md#33200002-failed-to-exit-extended-authentication-of-the-specified-nic) | Log off fail |
| [33200009](../errorcode-net-eap.md#33200009-netmanager-not-exist) | netmanager stop |
| [33200010](../errorcode-net-eap.md#33200010-invalid-eap-status) | invalid eth state |
| [33200099](../errorcode-net-eap.md#33200099-internal-program-error) | internal error |

**Examples**

```TypeScript
import {eap} from '@kit.NetworkKit';
let netId = 100;    
try{
  eap.logOffEthEap(netId);
  console.info("logOffEthEap success");
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```
