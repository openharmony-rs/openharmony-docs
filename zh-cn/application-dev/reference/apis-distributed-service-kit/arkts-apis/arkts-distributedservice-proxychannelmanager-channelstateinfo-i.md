# ChannelStateInfo

当代理通道状态变化时，用于表示代理通道的连接状态。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-proxyChannelManager-interface ChannelStateInfo--><!--Device-proxyChannelManager-interface ChannelStateInfo-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## channelId

```TypeScript
channelId: int
```

代理通道的channelId，取值范围为1~2147483647。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChannelStateInfo-channelId: int--><!--Device-ChannelStateInfo-channelId: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## state

```TypeScript
state: ChannelState
```

通道的连接状态，取值范围见[ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md#channelstate)。建议根据不同状态值调整业务策略，如通道断开时暂停数据发送、通道恢复后重试业务。

**类型：** [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md)

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChannelStateInfo-state: ChannelState--><!--Device-ChannelStateInfo-state: ChannelState-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

