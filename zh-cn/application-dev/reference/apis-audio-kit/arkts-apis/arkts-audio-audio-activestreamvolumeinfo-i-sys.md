# ActiveStreamVolumeInfo（系统接口）

活动音频流的音量信息。

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## appVolume

```TypeScript
appVolume: number
```

应用程序的音量。 取值限定为整数。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## clientUid

```TypeScript
clientUid: number
```

应用程序的UID。 取值限定为整数。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## volumeType

```TypeScript
volumeType: AudioVolumeType
```

当前流的音量类型。

**类型：** [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。
