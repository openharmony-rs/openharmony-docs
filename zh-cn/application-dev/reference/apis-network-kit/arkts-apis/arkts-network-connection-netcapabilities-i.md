# NetCapabilities

网络的能力集。

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## bearerTypes

```TypeScript
bearerTypes: Array<NetBearType>
```

网络类型。数组里面只包含了一种网络类型。

**类型：** Array&lt;NetBearType&gt;

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## linkDownBandwidthKbps

```TypeScript
linkDownBandwidthKbps?: number
```

下行（网络到设备）带宽，单位(kb/s)。0表示无法评估当前网络带宽。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## linkUpBandwidthKbps

```TypeScript
linkUpBandwidthKbps?: number
```

上行（设备到网络）带宽，单位(kb/s)。0表示无法评估当前网络带宽。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## networkCap

```TypeScript
networkCap?: Array<NetCap>
```

网络具体能力。

**类型：** Array&lt;[NetCap](arkts-network-connection-netcap-e.md)&gt;

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core
