# getEthEapStateInfo

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## getEthEapStateInfo

```TypeScript
function getEthEapStateInfo(): EthEapStateInfo
```

Queries the current 802.1X EAP authentication state information.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_EAP

**Model restriction:** This API can be used only in the stage model.

<!--Device-eap-function getEthEapStateInfo(): EthEapStateInfo--><!--Device-eap-function getEthEapStateInfo(): EthEapStateInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

**Return value:**

| Type | Description |
| --- | --- |
| [EthEapStateInfo](arkts-network-eap-etheapstateinfo-i.md) | Current authentication state, retry count and supplementary message. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
