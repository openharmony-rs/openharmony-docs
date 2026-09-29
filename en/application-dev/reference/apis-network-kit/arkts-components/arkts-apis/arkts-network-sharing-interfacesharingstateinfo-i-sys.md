# InterfaceSharingStateInfo (System API)

```TypeScript
export interface InterfaceSharingStateInfo
```

Wakes up the listener for network sharing state changes of an NIC.

**Since:** 11

<!--Device-sharing-export interface InterfaceSharingStateInfo--><!--Device-sharing-export interface InterfaceSharingStateInfo-End-->

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

<!--Device-InterfaceSharingStateInfo-iface: string--><!--Device-InterfaceSharingStateInfo-iface: string-End-->

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

## state

```TypeScript
state: SharingIfaceState
```

Network sharing state of the NIC.

**Type:** [SharingIfaceState](arkts-network-sharing-sharingifacestate-e-sys.md)

**Since:** 11

<!--Device-InterfaceSharingStateInfo-state: SharingIfaceState--><!--Device-InterfaceSharingStateInfo-state: SharingIfaceState-End-->

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.

## type

```TypeScript
type: SharingIfaceType
```

Enumerates the network sharing types of an NIC.

**Type:** [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md)

**Since:** 11

<!--Device-InterfaceSharingStateInfo-type: SharingIfaceType--><!--Device-InterfaceSharingStateInfo-type: SharingIfaceType-End-->

**System capability:** SystemCapability.Communication.NetManager.NetSharing

**System API:** This is a system API.
