# InterfaceSharingStateInfo (System API)

Wakes up the listener for network sharing state changes of an NIC.

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## iface

```TypeScript
iface: string
```

NIC name.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

## state

```TypeScript
state: SharingIfaceState
```

Network sharing state of the NIC.

**Type:** [SharingIfaceState](arkts-network-sharing-sharingifacestate-e-sys.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

## type

```TypeScript
type: SharingIfaceType
```

Enumerates the network sharing types of an NIC.

**Type:** [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.
