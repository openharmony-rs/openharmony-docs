# AudioLoopbackAvailableStatus (System API)

```TypeScript
interface AudioLoopbackAvailableStatus
```

Defines the availability status of global audio loopback.

**Since:** 26.0.1

<!--Device-audio-interface AudioLoopbackAvailableStatus--><!--Device-audio-interface AudioLoopbackAvailableStatus-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## available

```TypeScript
available: boolean
```

Indicates the availability status. The playback control application can determine whether to display the audio separation switch button based on the status.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopbackAvailableStatus-available: boolean--><!--Device-AudioLoopbackAvailableStatus-available: boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.

## unavailableReason

```TypeScript
unavailableReason?: AudioLoopbackUnavailableReason
```

Unavailable reason. The playback control application determines the prompt information based on the information. <br>This parameter is available only when Status is unavailable.

**Type:** [AudioLoopbackUnavailableReason](arkts-audio-audio-audioloopbackunavailablereason-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioLoopbackAvailableStatus-unavailableReason?: AudioLoopbackUnavailableReason--><!--Device-AudioLoopbackAvailableStatus-unavailableReason?: AudioLoopbackUnavailableReason-End-->

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**System API:** This is a system API.
