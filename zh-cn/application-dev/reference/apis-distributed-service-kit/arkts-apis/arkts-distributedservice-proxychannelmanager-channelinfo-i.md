# ChannelInfo

打开代理通道函数的入参，包括代理通道的链路类型、对端设备的MAC地址和监听服务的UUID。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## linkType

```TypeScript
linkType: LinkType
```

代理通道的链路类型，取值范围见[LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md)，目前仅支持LINK_BR（蓝牙BR协议）。

**类型：** [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## peerDevAddr

```TypeScript
peerDevAddr: string
```

对端设备的MAC地址，格式为XX:XX:XX:XX:XX:XX，其中XX为十六进制字符（0~9、A~F或a~f）。对端设备必须已配对，未配对时返回错误码32390002。格式不符合要求时返回错误码32390006。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## peerUuid

```TypeScript
peerUuid: string
```

对端监听的服务的UUID，格式为标准UUID字符串，如xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx。格式不符合要求时返回错误码32390006。

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration
