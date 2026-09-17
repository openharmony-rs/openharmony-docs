# HidDeviceQos

描述HID设备服务质量（Qos）参数。该结构定义了HID数据传输通道的流量控制、延迟保证和可靠性策略，用于优化蓝牙传输性能，确保设备的实时响应性。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## delayVariation

```TypeScript
delayVariation?: number
```

允许的延迟波动范围，单位为μs，默认为-1，表示没有延迟波动范围限制。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## latency

```TypeScript
latency?: number
```

最大允许延迟时间，单位为μs，默认为-1，表示没有延迟限制。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## peakBandwidth

```TypeScript
peakBandwidth?: number
```

最大传输速率限制，取值范围[0, +∞)，单位为Byte/s，默认为0，表示没有传输速率限制。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## serviceType

```TypeScript
serviceType?: ServiceType
```

服务类型，默认为SERVICE_BEST_EFFORT。

**类型：** [ServiceType](arkts-connectivity-hid-servicetype-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## tokenBucketSize

```TypeScript
tokenBucketSize?: number
```

允许短时间内超过tokenRate的最大数据量，单位为Byte，默认为0，表示没有最大数据量限制。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## tokenRate

```TypeScript
tokenRate?: number
```

单位时间内允许传输的平均数据量，单位为Byte/s，默认为0，表示没有平均数据量限制。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core
