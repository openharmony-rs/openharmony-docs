# setEthEapConfig

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## setEthEapConfig

```TypeScript
function setEthEapConfig(config: EthEapConfig): void
```

Sets the 802.1X EAP configuration for Ethernet. The configuration is persisted and encrypted.

Any field change triggers one auto-auth cycle unless the feature is disabled or the authentication is occupied by an enterprise app (then the config is only persisted; the enterprise app keeps control). The auth result is delivered via the stateChange callback, not by this API's return.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_EAP

**Model restriction:** This API can be used only in the stage model.

<!--Device-eap-function setEthEapConfig(config: EthEapConfig): void--><!--Device-eap-function setEthEapConfig(config: EthEapConfig): void-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [EthEapConfig](arkts-network-eap-etheapconfig-i.md) | Yes | 802.1X EAP configuration to set. Sensitive fields (password, certPassword, certEntry) passed as empty string/empty array mean "keep the original value". |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
