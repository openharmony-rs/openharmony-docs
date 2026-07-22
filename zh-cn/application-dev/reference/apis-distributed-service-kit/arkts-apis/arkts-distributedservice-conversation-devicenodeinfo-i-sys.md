# DeviceNodeInfo（系统接口）

设备节点信息，包括networkId、设备名称、设备类型标识符、近场状态和UDID。

**起始版本：** 26.1.0

<!--Device-conversation-interface DeviceNodeInfo--><!--Device-conversation-interface DeviceNodeInfo-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## deviceName

```TypeScript
deviceName: string
```

设备名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceNodeInfo-deviceName: string--><!--Device-DeviceNodeInfo-deviceName: string-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## deviceTypeId

```TypeScript
deviceTypeId: number
```

设备类型标识符，表示设备的类别，取值为整数，例如：0x0E-手机，0x11-平板，0x9C-电视，0x0C-PC等（具体数值以系统定义为准）。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceNodeInfo-deviceTypeId: int--><!--Device-DeviceNodeInfo-deviceTypeId: int-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## nearby

```TypeScript
nearby: boolean
```

设备是否在近场。true表示设备在近场，false表示设备不在近场。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceNodeInfo-nearby: boolean--><!--Device-DeviceNodeInfo-nearby: boolean-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
networkId: string
```

设备的networkId，在分布式网络中唯一标识一台设备，用于发送数据时的设备寻址。与UDID互为替代，发送数据时可任选其一。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceNodeInfo-networkId: string--><!--Device-DeviceNodeInfo-networkId: string-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

## udid

```TypeScript
udid: string
```

设备的UDID，唯一标识一台设备，用于发送数据时的设备寻址。与networkId不同，UDID为设备的永久唯一标识，不随网络拓扑变化而改变，两者互为替代，发送数据时可任选其一。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceNodeInfo-udid: string--><!--Device-DeviceNodeInfo-udid: string-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

