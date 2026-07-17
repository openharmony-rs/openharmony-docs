# CurrentInputDeviceChangedEvent

应用接收到输入设备的变更事件。

**起始版本：** 21

<!--Device-audio-interface CurrentInputDeviceChangedEvent--><!--Device-audio-interface CurrentInputDeviceChangedEvent-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## changeReason

```TypeScript
changeReason: AudioStreamDeviceChangeReason
```

设备变更原因。

**类型：** AudioStreamDeviceChangeReason

**起始版本：** 21

<!--Device-CurrentInputDeviceChangedEvent-changeReason: AudioStreamDeviceChangeReason--><!--Device-CurrentInputDeviceChangedEvent-changeReason: AudioStreamDeviceChangeReason-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

## devices

```TypeScript
devices: AudioDeviceDescriptors
```

设备信息。

**类型：** AudioDeviceDescriptors

**起始版本：** 21

<!--Device-CurrentInputDeviceChangedEvent-devices: AudioDeviceDescriptors--><!--Device-CurrentInputDeviceChangedEvent-devices: AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

