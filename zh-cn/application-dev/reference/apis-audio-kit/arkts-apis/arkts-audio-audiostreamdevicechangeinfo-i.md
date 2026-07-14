# AudioStreamDeviceChangeInfo

流设备变更时，应用接收到的事件。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Device

## changeReason

```TypeScript
changeReason: AudioStreamDeviceChangeReason
```

流设备变更原因。

**类型：** AudioStreamDeviceChangeReason

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## devices

```TypeScript
devices: AudioDeviceDescriptors
```

设备信息。

**类型：** AudioDeviceDescriptors

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

## preDevices

```TypeScript
preDevices?: AudioDeviceDescriptors
```

应用流设备变更前的设备信息。

**类型：** AudioDeviceDescriptors

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

