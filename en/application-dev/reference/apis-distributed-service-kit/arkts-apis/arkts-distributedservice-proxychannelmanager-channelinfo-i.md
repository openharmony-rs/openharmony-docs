# ChannelInfo

Input parameters of the function for opening a proxy channel, including the link type of the proxy channel, the MAC address of the peer device, and the UUID of the listening service.

**Since:** 20

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## linkType

```TypeScript
linkType: LinkType
```

Link type of the proxy channel. For details about the value range, see [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md). Currently, only **LINK_BR** (Bluetooth BR protocol) is supported.

**Type:** [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## peerDevAddr

```TypeScript
peerDevAddr: string
```

MAC address of the peer device, in the format of XX:XX:XX:XX:XX:XX, where XX is a hexadecimal character (0-9, A- F, or a-f). The peer device must be paired. Error code 32390002 is returned if the device is not paired. Error code 32390006 is returned if the format does not meet the requirements.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## peerUuid

```TypeScript
peerUuid: string
```

UUID of the service listened on by the peer device, in the standard UUID string format, for example, xxxxxxxx- xxxx-xxxx-xxxx-xxxxxxxxxxxx. Error code 32390006 is returned if the format does not meet the requirements.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration
