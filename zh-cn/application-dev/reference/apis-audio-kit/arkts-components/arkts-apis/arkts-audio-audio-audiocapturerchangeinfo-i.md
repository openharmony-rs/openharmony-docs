# AudioCapturerChangeInfo

描述音频采集器更改信息。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## capturerInfo

```TypeScript
readonly capturerInfo: AudioCapturerInfo
```

音频采集器信息。

**类型：** [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## deviceDescriptors

```TypeScript
readonly deviceDescriptors: AudioDeviceDescriptors
```

音频设备信息。

**类型：** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## muted

```TypeScript
readonly muted?: boolean
```

音频采集器是否处于静音状态。true表示静音，false表示非静音。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## streamId

```TypeScript
readonly streamId: number
```

音频流唯一id。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Capturer
