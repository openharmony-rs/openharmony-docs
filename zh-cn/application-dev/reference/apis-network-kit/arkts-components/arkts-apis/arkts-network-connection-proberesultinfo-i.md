# ProbeResultInfo

网络探测结果信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## lossRate

```TypeScript
lossRate: number
```

丢包率，取值范围[0, 100]。例如，100表示100%丢包，50表示50%丢包。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## rtt

```TypeScript
rtt: number[]
```

往返时间（RTT），单位为毫秒。对目的主机发送多个探测报文，探测报文数量由[queryProbeResult](arkts-network-connection-queryproberesult-f.md)接口中duration参数决定。数组元素依次为这些探测报文RTT中最小值、平均值、最大值、标准差。

**类型：** number[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core
