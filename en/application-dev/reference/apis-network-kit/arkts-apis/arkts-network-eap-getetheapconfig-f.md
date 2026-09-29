# getEthEapConfig

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## getEthEapConfig

```TypeScript
function getEthEapConfig(): Promise<EthEapConfig>
```

Gets the 802.1X EAP configuration for Ethernet. Sensitive fields (password, certPassword, certEntry) are always returned empty.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_EAP

**Model restriction:** This API can be used only in the stage model.

<!--Device-eap-function getEthEapConfig(): Promise<EthEapConfig>--><!--Device-eap-function getEthEapConfig(): Promise<EthEapConfig>-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[EthEapConfig](arkts-network-eap-etheapconfig-i.md)&gt; | Promise used to return EthEapConfig. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
