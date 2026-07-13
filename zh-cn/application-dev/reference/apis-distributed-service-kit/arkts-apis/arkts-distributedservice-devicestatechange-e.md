# DeviceStateChange

表示设备状态。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

设备物理上线，此时状态未知，在状态更改为可用之前，分布式业务无法使用。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## AVAILABLE

```TypeScript
AVAILABLE = 1
```

设备可用状态，表示设备间信息已在分布式数据中同步完成，可以运行分布式业务。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## UNAVAILABLE

```TypeScript
UNAVAILABLE = 2
```

设备物理下线，此时状态未知。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

