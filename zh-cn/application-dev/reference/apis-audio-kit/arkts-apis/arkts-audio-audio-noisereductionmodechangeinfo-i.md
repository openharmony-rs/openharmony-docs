# NoiseReductionModeChangeInfo

```TypeScript
interface NoiseReductionModeChangeInfo
```

降噪模式变更信息。该接口作为[onNoiseReductionModeChanged](arkts-audio-audio-audiocapturer-i.md#onnoisereductionmodechanged)的回调参数。使用场景：当录音流的降噪模式发生变更时，该结构体携带最新的降噪模式和变更原因。

**起始版本：** 26.1.0

<!--Device-audio-interface NoiseReductionModeChangeInfo--><!--Device-audio-interface NoiseReductionModeChangeInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## noiseReductionMode

```TypeScript
noiseReductionMode: NoiseReductionMode
```

当前降噪模式，默认值为[FIDELITY](arkts-audio-audio-noisereductionmode-e.md#fidelity)。

**类型：** [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NoiseReductionModeChangeInfo-noiseReductionMode: NoiseReductionMode--><!--Device-NoiseReductionModeChangeInfo-noiseReductionMode: NoiseReductionMode-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## reason

```TypeScript
reason: NoiseReductionModeChangeReason
```

降噪模式变更原因。

**类型：** [NoiseReductionModeChangeReason](arkts-audio-audio-noisereductionmodechangereason-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NoiseReductionModeChangeInfo-reason: NoiseReductionModeChangeReason--><!--Device-NoiseReductionModeChangeInfo-reason: NoiseReductionModeChangeReason-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Capturer
