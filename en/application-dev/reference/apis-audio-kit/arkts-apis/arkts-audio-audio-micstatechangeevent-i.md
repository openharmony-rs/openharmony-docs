# MicStateChangeEvent

```TypeScript
interface MicStateChangeEvent
```

Describes the event received by the application when the microphone mute status is changed.

**Since:** 9

<!--Device-audio-interface MicStateChangeEvent--><!--Device-audio-interface MicStateChangeEvent-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## mute

```TypeScript
mute: boolean
```

Mute status of the microphone **true** if muted, **false** otherwise.

**Type:** boolean

**Since:** 9

<!--Device-MicStateChangeEvent-mute: boolean--><!--Device-MicStateChangeEvent-mute: boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device
