# startEthEap

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## startEthEap

```TypeScript
function startEthEap(netId: number, profile: EthEapProfile): void
```

Starts EAP authentication on an Ethernet NIC.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.NetManager.Eap

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netId | number | Yes | ID of the Ethernet NIC. If the default value **-1** is specified, the system automatically matches the Ethernet NIC to initiate EAP authentication. |
| profile | [EthEapProfile](arkts-network-eap-etheapprofile-i.md) | Yes | EAP profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [33200001](../errorcode-net-eap.md#33200001-invalid-netid) | Invalid netId |
| [33200003](../errorcode-net-eap.md#33200003-invalid-eth-eap-configuration) | Invalid profile |
| [33200009](../errorcode-net-eap.md#33200009-netmanager-not-exist) | netmanager stop |
| [33200010](../errorcode-net-eap.md#33200010-invalid-eap-status) | invalid eth state |
| [33200099](../errorcode-net-eap.md#33200099-internal-program-error) | internal error |

**Examples**

```TypeScript
import {eap} from '@kit.NetworkKit';
let netId = 100;
let profile: eap.EthEapProfile = {
  eapMethod: eap.EapMethod.EAP_TTLS,
  phase2Method: eap.Phase2Method.PHASE2_AKA_PRIME,
  identity: "identity",
  anonymousIdentity: "anonymousIdentity",
  password: "password",
  caCertAliases: "caCertAliases",
  caPath: "caPath",
  clientCertAliases: "clientCertAliases",
  certEntry: new Uint8Array([5,6,7,8,9,10]),
  certPassword: "certPassword",
  altSubjectMatch: "altSubjectMatch",
  domainSuffixMatch: "domainSuffixMatch",
  realm: "realm",
  plmn: "plmn",
  eapSubId: 1
};
    
try {
  eap.startEthEap(netId, profile);
  console.info('startEthEap success');
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```
