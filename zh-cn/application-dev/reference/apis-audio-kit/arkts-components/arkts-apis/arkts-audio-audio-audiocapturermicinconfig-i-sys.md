# AudioCapturerMicInConfig（系统接口）

音频采集器选项信息，可采集未经任何处理的麦克风输入（mic-in）音频数据。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## capturerInfo

```TypeScript
capturerInfo: AudioCapturerInfo
```

音频采集器信息。

**类型：** [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## ecStreamInfo

```TypeScript
ecStreamInfo?: AudioStreamInfo
```

回声消除音频流信息。

若未设置此属性，采集器将仅录制麦克风输入的音频流。

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## micInStreamInfo

```TypeScript
micInStreamInfo: AudioStreamInfo
```

麦克风音频流信息。

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## processedStreamInfo

```TypeScript
processedStreamInfo?: AudioStreamInfo
```

处理后的音频流信息。

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。
