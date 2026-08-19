# DeviceStateChangeAction（系统接口）

表示设备状态变化的枚举。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [DeviceStateChange](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md)

<!--Device-deviceManager-enum DeviceStateChangeAction--><!--Device-deviceManager-enum DeviceStateChangeAction-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## ONLINE

```TypeScript
ONLINE = 0
```

设备物理上线状态。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [UNKNOWN](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md#unknown)

<!--Device-DeviceStateChangeAction-ONLINE = 0--><!--Device-DeviceStateChangeAction-ONLINE = 0-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## READY

```TypeScript
READY = 1
```

设备可用状态，表示设备间信息已在分布式数据中同步完成, 可以运行分布式业务。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [AVAILABLE](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md#available)

<!--Device-DeviceStateChangeAction-READY = 1--><!--Device-DeviceStateChangeAction-READY = 1-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## OFFLINE

```TypeScript
OFFLINE = 2
```

设备物理下线状态。

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [UNAVAILABLE](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md#unavailable)

<!--Device-DeviceStateChangeAction-OFFLINE = 2--><!--Device-DeviceStateChangeAction-OFFLINE = 2-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## CHANGE

```TypeScript
CHANGE = 3
```

设备信息更改。

**起始版本：** 7

**废弃版本：** 11

<!--Device-DeviceStateChangeAction-CHANGE = 3--><!--Device-DeviceStateChangeAction-CHANGE = 3-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

