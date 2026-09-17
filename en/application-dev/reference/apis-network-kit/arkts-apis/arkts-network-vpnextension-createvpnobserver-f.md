# createVpnObserver

## Modules to Import

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## createVpnObserver

```TypeScript
function createVpnObserver(): VpnObserver
```

Creates a VPN observer object. It is used to listen for VPN-related events.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Vpn

**Return value:**

| Type | Description |
| --- | --- |
| [VpnObserver](arkts-network-vpnextension-vpnobserver-i.md) | VPN observer object. |

**Examples**

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';

let vpnObserver: vpnExtension.VpnObserver = vpnExtension.createVpnObserver();
```
