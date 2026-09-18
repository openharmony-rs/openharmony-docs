# createVpnConnection

## Modules to Import

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## createVpnConnection

```TypeScript
function createVpnConnection(context: VpnExtensionContext): VpnConnection
```

Creates a **VpnConnection** object.

> **NOTE:** 
> 
> Before calling **createVpnConnection**, call **startVpnExtensionAbility** to enable the VPN function.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Vpn

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [VpnExtensionContext](arkts-network-vpnextension-vpnextensioncontext-t.md) | Yes | Specified context. |

**Return value:**

| Type | Description |
| --- | --- |
| [VpnConnection](arkts-network-vpnextension-vpnconnection-i.md) | VPN connection object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
