# AudioCapturerMicInConfig（系统接口）

Describes audio capturer configuration options that can capture microphone input (mic-in) audio data before any processing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-audio-interface AudioCapturerMicInConfig--><!--Device-audio-interface AudioCapturerMicInConfig-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## capturerInfo

```TypeScript
capturerInfo: AudioCapturerInfo
```

Capturer attribute information.

**类型：** [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInConfig-capturerInfo: AudioCapturerInfo--><!--Device-AudioCapturerMicInConfig-capturerInfo: AudioCapturerInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## ecStreamInfo

```TypeScript
ecStreamInfo?: AudioStreamInfo
```

Stream information that describe echo reference signal. If not set this attribute, the capturer will only record Mic-In audio stream.

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInConfig-ecStreamInfo?: AudioStreamInfo--><!--Device-AudioCapturerMicInConfig-ecStreamInfo?: AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## micInStreamInfo

```TypeScript
micInStreamInfo: AudioStreamInfo
```

Stream information that describe Mic-In audio stream.

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInConfig-micInStreamInfo: AudioStreamInfo--><!--Device-AudioCapturerMicInConfig-micInStreamInfo: AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## processedStreamInfo

```TypeScript
processedStreamInfo?: AudioStreamInfo
```

描述处理后的音频流的流信息。

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioCapturerMicInConfig-processedStreamInfo?: AudioStreamInfo--><!--Device-AudioCapturerMicInConfig-processedStreamInfo?: AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

