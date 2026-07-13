# CurrentOutputDeviceChangedEvent

应用接收到输出设备的变更事件。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Core

## changeReason

```TypeScript
changeReason: AudioStreamDeviceChangeReason
```

设备变更原因。

**类型：** AudioStreamDeviceChangeReason

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Core

## devices

```TypeScript
devices: AudioDeviceDescriptors
```

设备信息。

**类型：** AudioDeviceDescriptors

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Core

## preDevices

```TypeScript
preDevices?: AudioDeviceDescriptors
```

应用输出设备变更前的设备信息。

**类型：** AudioDeviceDescriptors

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## recommendedAction

```TypeScript
recommendedAction: OutputDeviceChangeRecommendedAction
```

设备变更后推荐的操作。

**类型：** OutputDeviceChangeRecommendedAction

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Audio.Core

