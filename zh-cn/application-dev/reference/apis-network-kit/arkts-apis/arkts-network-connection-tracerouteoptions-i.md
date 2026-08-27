# TraceRouteOptions

路由跟踪的选项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## maxJumpNumber

```TypeScript
maxJumpNumber?: number
```

最大跳数，取值范围[1, 30]，默认值为30。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## packetsType

```TypeScript
packetsType?: PacketsType
```

探测使用的数据包类型，默认为NETCONN_PACKETS_ICMP。

**类型：** [PacketsType](arkts-network-connection-packetstype-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core
