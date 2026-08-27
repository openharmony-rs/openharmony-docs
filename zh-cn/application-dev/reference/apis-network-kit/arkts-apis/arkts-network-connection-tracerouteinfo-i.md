# TraceRouteInfo

路由跟踪信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## address

```TypeScript
address: string
```

该跳的IP地址。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## jumpNo

```TypeScript
jumpNo: number
```

跳数序号。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## rtt

```TypeScript
rtt: number[]
```

往返时间（RTT），单位为毫秒。每一跳发送5个探测报文，数组元素依次为这些探测报文RTT中的最小值、平均值、最大值、标准差。

**类型：** number[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core
