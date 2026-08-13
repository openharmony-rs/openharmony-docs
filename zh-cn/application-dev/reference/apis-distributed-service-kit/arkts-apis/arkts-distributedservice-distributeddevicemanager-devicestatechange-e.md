# DeviceStateChange

表示设备状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-distributedDeviceManager-enum DeviceStateChange--><!--Device-distributedDeviceManager-enum DeviceStateChange-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

设备物理上线，此时状态未知，在状态更改为可用之前，分布式业务无法使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DeviceStateChange-UNKNOWN = 0--><!--Device-DeviceStateChange-UNKNOWN = 0-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## AVAILABLE

```TypeScript
AVAILABLE = 1
```

设备可用状态，表示设备间信息已在分布式数据中同步完成，可以运行分布式业务。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DeviceStateChange-AVAILABLE = 1--><!--Device-DeviceStateChange-AVAILABLE = 1-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

## UNAVAILABLE

```TypeScript
UNAVAILABLE = 2
```

设备物理下线，此时状态未知。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DeviceStateChange-UNAVAILABLE = 2--><!--Device-DeviceStateChange-UNAVAILABLE = 2-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

