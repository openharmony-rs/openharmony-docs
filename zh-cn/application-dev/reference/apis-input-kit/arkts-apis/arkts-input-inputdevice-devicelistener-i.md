# DeviceListener

描述输入设备热插拔的信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputDevice-interface DeviceListener--><!--Device-inputDevice-interface DeviceListener-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## deviceId

```TypeScript
deviceId: int
```

输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DeviceListener-deviceId: int--><!--Device-DeviceListener-deviceId: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

## type

```TypeScript
type: ChangedType
```

输入设备插入或者移除。

**类型：** [ChangedType](arkts-input-inputdevice-changedtype-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DeviceListener-type: ChangedType--><!--Device-DeviceListener-type: ChangedType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

