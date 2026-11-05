# NoiseReductionModeChangeInfo

```TypeScript
interface NoiseReductionModeChangeInfo
```

Indicates the change information about the noise reduction mode. This interface is used as the callback parameter of [onNoiseReductionModeChanged](arkts-audio-audio-audiocapturer-i.md#onnoisereductionmodechanged). Application scenario: When the NR mode of a recording stream changes, this data structure carries the latest NR mode and change reason.

**Since:** 26.1.0

<!--Device-audio-interface NoiseReductionModeChangeInfo--><!--Device-audio-interface NoiseReductionModeChangeInfo-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## noiseReductionMode

```TypeScript
noiseReductionMode: NoiseReductionMode
```

Current noise reduction mode. The default value is [FIDELITY](arkts-audio-audio-noisereductionmode-e.md#fidelity).

**Type:** [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NoiseReductionModeChangeInfo-noiseReductionMode: NoiseReductionMode--><!--Device-NoiseReductionModeChangeInfo-noiseReductionMode: NoiseReductionMode-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## reason

```TypeScript
reason: NoiseReductionModeChangeReason
```

The reason for the noise reduction mode change.

**Type:** [NoiseReductionModeChangeReason](arkts-audio-audio-noisereductionmodechangereason-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NoiseReductionModeChangeInfo-reason: NoiseReductionModeChangeReason--><!--Device-NoiseReductionModeChangeInfo-reason: NoiseReductionModeChangeReason-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer
