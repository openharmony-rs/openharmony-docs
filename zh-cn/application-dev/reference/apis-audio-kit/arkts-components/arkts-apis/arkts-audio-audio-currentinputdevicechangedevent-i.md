# CurrentInputDeviceChangedEvent

应用接收到输入设备的变更事件。

**起始版本：** 21

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

**类型：** [AudioStreamDeviceChangeReason](arkts-audio-audio-audiostreamdevicechangereason-e.md)

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.Core

## devices

```TypeScript
devices: AudioDeviceDescriptors
```

设备信息。

**类型：** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Audio.Core
