# NetCapabilities

网络的能力集。

**起始版本：** 23

<!--Device-connection-export interface NetCapabilities--><!--Device-connection-export interface NetCapabilities-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## bearerTypes

```TypeScript
bearerTypes: Array<NetBearType>
```

网络类型。数组里面只包含了一种网络类型。

**类型：** Array&lt;NetBearType&gt;

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetCapabilities-bearerTypes: Array<NetBearType>--><!--Device-NetCapabilities-bearerTypes: Array<NetBearType>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## linkDownBandwidthKbps

```TypeScript
linkDownBandwidthKbps?: int
```

下行（网络到设备）带宽，单位(kb/s)。0表示无法评估当前网络带宽。

**类型：** int

**起始版本：** 23

<!--Device-NetCapabilities-linkDownBandwidthKbps?: int--><!--Device-NetCapabilities-linkDownBandwidthKbps?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## linkUpBandwidthKbps

```TypeScript
linkUpBandwidthKbps?: int
```

上行（设备到网络）带宽，单位(kb/s)。0表示无法评估当前网络带宽。

**类型：** int

**起始版本：** 23

<!--Device-NetCapabilities-linkUpBandwidthKbps?: int--><!--Device-NetCapabilities-linkUpBandwidthKbps?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## networkCap

```TypeScript
networkCap?: Array<NetCap>
```

网络具体能力。

**类型：** Array&lt;[NetCap](arkts-network-connection-netcap-e.md)&gt;

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NetCapabilities-networkCap?: Array<NetCap>--><!--Device-NetCapabilities-networkCap?: Array<NetCap>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

