# NetSpecifier

Provides an instance that bears data network capabilities.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## bearerPrivateIdentifier

```TypeScript
bearerPrivateIdentifier?: string
```

Network identifier. The identifier of the cellular network is **slot0** for SIM card 1 and **slot1** for SIM card
2. Since API version 12, you can pass the registered WLAN hotspot to the API to specify the WLAN network to be
activated.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## netCapabilities

```TypeScript
netCapabilities: NetCapabilities
```

Network transmission capabilities and bearer types of the data network.

**Type:** [NetCapabilities](arkts-network-connection-netcapabilities-i.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core
