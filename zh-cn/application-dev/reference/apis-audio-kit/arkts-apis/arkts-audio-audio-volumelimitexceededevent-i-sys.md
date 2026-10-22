# VolumeLimitExceededEvent（系统接口）

```TypeScript
interface VolumeLimitExceededEvent
```

描述音量超过阈值时的通知事件。收到通知后，应用在继续调整音量前必须通过[confirmVolumeLimitExceeded](arkts-audio-audio-audiovolumemanager-i-sys.md#confirmvolumelimitexceeded) 发送确认结果。

**起始版本：** 26.0.1

<!--Device-audio-interface VolumeLimitExceededEvent--><!--Device-audio-interface VolumeLimitExceededEvent-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## currentVolume

```TypeScript
currentVolume: number
```

当前音量等级。

取值范围在 [getMinSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getminsystemvolume) 和 [getMaxSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getmaxsystemvolume) 获取的值之间。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VolumeLimitExceededEvent-currentVolume: int--><!--Device-VolumeLimitExceededEvent-currentVolume: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

指示触发音量越限的进程的UID。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VolumeLimitExceededEvent-uid: int--><!--Device-VolumeLimitExceededEvent-uid: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## volumeThreshold

```TypeScript
volumeThreshold: number
```

当前音量类型的音量阈值。

取值范围在 [getMinSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getminsystemvolume) 和 [getMaxSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getmaxsystemvolume) 获取的值之间。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VolumeLimitExceededEvent-volumeThreshold: int--><!--Device-VolumeLimitExceededEvent-volumeThreshold: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## volumeType

```TypeScript
volumeType: AudioVolumeType
```

当前音量类型。

**类型：** [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VolumeLimitExceededEvent-volumeType: AudioVolumeType--><!--Device-VolumeLimitExceededEvent-volumeType: AudioVolumeType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。
