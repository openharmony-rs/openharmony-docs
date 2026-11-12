# NetworkMatchRule (System API)

```TypeScript
export interface NetworkMatchRule
```

Defines the network for which the quota policy is set.

**Since:** 10

<!--Device-policy-export interface NetworkMatchRule--><!--Device-policy-export interface NetworkMatchRule-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## identity

```TypeScript
identity: string
```

Used together with simId in the metered cellular network. <br>Used independently for Ethernet and Wi-Fi networks. <br>Used to mark the type.

**Type:** string

**Since:** 10

<!--Device-NetworkMatchRule-identity: string--><!--Device-NetworkMatchRule-identity: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## netType

```TypeScript
netType: NetBearType
```

Network type.

**Type:** [NetBearType](arkts-network-policy-netbeartype-t.md)

**Since:** 10

<!--Device-NetworkMatchRule-netType: NetBearType--><!--Device-NetworkMatchRule-netType: NetBearType-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## simId

```TypeScript
simId: string
```

Identifier value of the SIM card in the metered cellular network. <br>Not used for Ethernet and Wi-Fi networks.

**Type:** string

**Since:** 10

<!--Device-NetworkMatchRule-simId: string--><!--Device-NetworkMatchRule-simId: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
