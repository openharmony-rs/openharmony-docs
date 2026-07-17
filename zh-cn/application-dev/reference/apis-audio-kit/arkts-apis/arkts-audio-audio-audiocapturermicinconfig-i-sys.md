# AudioCapturerMicInConfig（系统接口）

Describes audio capturer configuration options that can capture microphone input (mic-in) audio data before any processing.

**起始版本：** 23

<!--Device-audio-interface AudioCapturerMicInConfig--><!--Device-audio-interface AudioCapturerMicInConfig-End-->

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

Capturer attribute information.

**类型：** AudioCapturerInfo

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInConfig-capturerInfo: AudioCapturerInfo--><!--Device-AudioCapturerMicInConfig-capturerInfo: AudioCapturerInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## ecStreamInfo

```TypeScript
ecStreamInfo?: AudioStreamInfo
```

Stream information that describe echo reference signal.If not set this attribute, the capturer will only record Mic-In audio stream.

**类型：** AudioStreamInfo

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInConfig-ecStreamInfo?: AudioStreamInfo--><!--Device-AudioCapturerMicInConfig-ecStreamInfo?: AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## micInStreamInfo

```TypeScript
micInStreamInfo: AudioStreamInfo
```

Stream information that describe Mic-In audio stream.

**类型：** AudioStreamInfo

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInConfig-micInStreamInfo: AudioStreamInfo--><!--Device-AudioCapturerMicInConfig-micInStreamInfo: AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## processedStreamInfo

```TypeScript
processedStreamInfo?: AudioStreamInfo
```

描述处理后的音频流的流信息。

**类型：** AudioStreamInfo

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInConfig-processedStreamInfo?: AudioStreamInfo--><!--Device-AudioCapturerMicInConfig-processedStreamInfo?: AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

