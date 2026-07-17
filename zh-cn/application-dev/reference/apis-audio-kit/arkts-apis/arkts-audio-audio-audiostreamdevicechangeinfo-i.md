# AudioStreamDeviceChangeInfo

流设备变更时，应用接收到的事件。

**起始版本：** 11

<!--Device-audio-interface AudioStreamDeviceChangeInfo--><!--Device-audio-interface AudioStreamDeviceChangeInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## changeReason

```TypeScript
changeReason: AudioStreamDeviceChangeReason
```

流设备变更原因。

**类型：** AudioStreamDeviceChangeReason

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioStreamDeviceChangeInfo-changeReason: AudioStreamDeviceChangeReason--><!--Device-AudioStreamDeviceChangeInfo-changeReason: AudioStreamDeviceChangeReason-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## devices

```TypeScript
devices: AudioDeviceDescriptors
```

设备信息。

**类型：** AudioDeviceDescriptors

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AudioStreamDeviceChangeInfo-devices: AudioDeviceDescriptors--><!--Device-AudioStreamDeviceChangeInfo-devices: AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

## preDevices

```TypeScript
preDevices?: AudioDeviceDescriptors
```

应用流设备变更前的设备信息。

**类型：** AudioDeviceDescriptors

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AudioStreamDeviceChangeInfo-preDevices?: AudioDeviceDescriptors--><!--Device-AudioStreamDeviceChangeInfo-preDevices?: AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Device

