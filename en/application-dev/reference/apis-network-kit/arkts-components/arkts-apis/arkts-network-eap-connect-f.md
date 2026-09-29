# connect

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## connect

```TypeScript
function connect(action: EthEapConnectAction): Promise<void>
```

Manually triggers or disconnects the 802.1X EAP authentication of Ethernet.

When **action** is **ACTION_CONNECT**, authentication is re-triggered with the saved configuration (manual counterpart of the auto-auth trigger; fails if no configuration has been stored). If the authentication is occupied by an enterprise app, this API does not interrupt it; the result is delivered via the stateChange callback. When **action** is **ACTION_DISCONNECT**, auto authentication is stopped and the underlying 802.1X authentication is logged off.

**Since:** 26.2.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_EAP

**Model restriction:** This API can be used only in the stage model.

<!--Device-eap-function connect(action: EthEapConnectAction): Promise<void>--><!--Device-eap-function connect(action: EthEapConnectAction): Promise<void>-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| action | [EthEapConnectAction](arkts-network-eap-etheapconnectaction-e.md) | Yes | Manual connect action: re-trigger authentication (**ACTION_CONNECT**) or disconnect (**ACTION_DISCONNECT**). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
