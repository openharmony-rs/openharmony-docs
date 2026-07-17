# ChannelInfo

打开代理通道函数的入参，包括对端设备的MAC地址和监听服务的UUID。

**起始版本：** 20

<!--Device-proxyChannelManager-interface ChannelInfo--><!--Device-proxyChannelManager-interface ChannelInfo-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## linkType

```TypeScript
linkType: LinkType
```

代理通道的链路类型。

**类型：** LinkType

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChannelInfo-linkType: LinkType--><!--Device-ChannelInfo-linkType: LinkType-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## peerDevAddr

```TypeScript
peerDevAddr: string
```

对端设备的MAC地址。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChannelInfo-peerDevAddr: string--><!--Device-ChannelInfo-peerDevAddr: string-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## peerUuid

```TypeScript
peerUuid: string
```

对端监听的服务的UUID。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChannelInfo-peerUuid: string--><!--Device-ChannelInfo-peerUuid: string-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

