# AudioCapturerMicInData (System API)

```TypeScript
interface AudioCapturerMicInData
```

Describes audio capturer data that contains processed audio data and microphone input (mic-in) audio data before any processing.

**Since:** 24

<!--Device-audio-interface AudioCapturerMicInData--><!--Device-audio-interface AudioCapturerMicInData-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## data

```TypeScript
data: ArrayBuffer
```

Processed audio data buffer.

**Type:** ArrayBuffer

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioCapturerMicInData-data: ArrayBuffer--><!--Device-AudioCapturerMicInData-data: ArrayBuffer-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## ecData

```TypeScript
ecData?: ArrayBuffer
```

Echo reference audio data buffer. If capturer config does not set ecStreamInfo, this buffer will be null. See [AudioCapturerMicInConfig](arkts-audio-audio-audiocapturermicinconfig-i-sys.md) for details.

**Type:** ArrayBuffer

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioCapturerMicInData-ecData?: ArrayBuffer--><!--Device-AudioCapturerMicInData-ecData?: ArrayBuffer-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## micInData

```TypeScript
micInData: ArrayBuffer
```

Microphone input audio data buffer.

**Type:** ArrayBuffer

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioCapturerMicInData-micInData: ArrayBuffer--><!--Device-AudioCapturerMicInData-micInData: ArrayBuffer-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.
