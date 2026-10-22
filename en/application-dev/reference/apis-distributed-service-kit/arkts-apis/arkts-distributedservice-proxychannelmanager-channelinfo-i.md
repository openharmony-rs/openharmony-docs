# ChannelInfo

```TypeScript
interface ChannelInfo
```

Represents the proxy channel information, including the link type of the proxy channel, MAC address of the peer device, and service UUID.

**Since:** 20

<!--Device-proxyChannelManager-interface ChannelInfo--><!--Device-proxyChannelManager-interface ChannelInfo-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## linkType

```TypeScript
linkType: LinkType
```

Link type of the proxy channel. For details about the value range, see [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md). Currently, only **LINK_BR** (BR protocol) is supported.

**Type:** [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChannelInfo-linkType: LinkType--><!--Device-ChannelInfo-linkType: LinkType-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## peerDevAddr

```TypeScript
peerDevAddr: string
```

MAC address of the peer device, in the format of **XX:XX:XX:XX:XX:XX**, where **XX** is a hexadecimal character (0 to 9, A to F, or a to f). The peer device must have been paired. If not, error code 32390002 will be returned. If the format does not meet requirements, error code 32390006 will be returned.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChannelInfo-peerDevAddr: string--><!--Device-ChannelInfo-peerDevAddr: string-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## peerUuid

```TypeScript
peerUuid: string
```

Service UUID of the peer device. The value is a standard UUID string, for example, **xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx**. If the format does not meet requirements, error code 32390006 will be returned.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChannelInfo-peerUuid: string--><!--Device-ChannelInfo-peerUuid: string-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration
