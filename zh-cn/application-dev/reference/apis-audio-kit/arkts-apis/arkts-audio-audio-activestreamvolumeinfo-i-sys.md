# ActiveStreamVolumeInfo（系统接口）

用于激活音频流的音量信息。

**起始版本：** 24

<!--Device-audio-interface ActiveStreamVolumeInfo--><!--Device-audio-interface ActiveStreamVolumeInfo-End-->

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

应用的音量。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActiveStreamVolumeInfo-appVolume: int--><!--Device-ActiveStreamVolumeInfo-appVolume: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## clientUid

```TypeScript
clientUid: number
```

音频应用的Uid。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActiveStreamVolumeInfo-clientUid: int--><!--Device-ActiveStreamVolumeInfo-clientUid: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## volumeType

```TypeScript
volumeType: AudioVolumeType
```

当前音频流的音量类型。

**类型：** AudioVolumeType

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActiveStreamVolumeInfo-volumeType: AudioVolumeType--><!--Device-ActiveStreamVolumeInfo-volumeType: AudioVolumeType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

