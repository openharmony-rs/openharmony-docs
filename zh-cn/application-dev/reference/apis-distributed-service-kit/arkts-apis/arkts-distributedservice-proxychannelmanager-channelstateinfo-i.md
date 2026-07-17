# ChannelStateInfo

当代理通道状态变化时，用于表示代理通道的连接状态。

**起始版本：** 20

<!--Device-proxyChannelManager-interface ChannelStateInfo--><!--Device-proxyChannelManager-interface ChannelStateInfo-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## channelId

```TypeScript
channelId: number
```

代理通道的channelId。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChannelStateInfo-channelId: int--><!--Device-ChannelStateInfo-channelId: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## state

```TypeScript
state: ChannelState
```

通道的连接状态。

**类型：** ChannelState

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChannelStateInfo-state: ChannelState--><!--Device-ChannelStateInfo-state: ChannelState-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

