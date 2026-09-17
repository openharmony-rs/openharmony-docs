# VolumeLimitExceededEvent（系统接口）

描述表示音量超过阈值的通知事件。在收到通知后，应用必须发送确认结果。在继续调整音量之前，通过 [confirmVolumeLimitExceeded](arkts-audio-audio-audiovolumemanager-i-sys.md#confirmvolumelimitexceeded) 进行确认。

**起始版本：** 26.0.0

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

当前音量等级。该值介于通过 [getMinSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getminsystemvolume) 和 [getMaxSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getmaxsystemvolume) 获取的值之间。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## volumeThreshold

```TypeScript
volumeThreshold: number
```

当前卷音量型的音量大小阈值。该值介于通过 [getMinSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getminsystemvolume) 和 [getMaxSystemVolume](arkts-audio-audio-audiovolumemanager-i-sys.md#getmaxsystemvolume) 获取的值之间。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。

## volumeType

```TypeScript
volumeType: AudioVolumeType
```

当前音量类型。

**类型：** [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

**系统接口：** 此接口为系统接口。
