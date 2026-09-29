# CurrentInputDeviceChangedEvent

```TypeScript
interface CurrentInputDeviceChangedEvent
```

Describes the event indicating that the input device changes.

**Since:** 21

<!--Device-audio-interface CurrentInputDeviceChangedEvent--><!--Device-audio-interface CurrentInputDeviceChangedEvent-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## changeReason

```TypeScript
changeReason: AudioStreamDeviceChangeReason
```

Audio input device change reason.

**Type:** [AudioStreamDeviceChangeReason](arkts-audio-audio-audiostreamdevicechangereason-e.md)

**Since:** 21

<!--Device-CurrentInputDeviceChangedEvent-changeReason: AudioStreamDeviceChangeReason--><!--Device-CurrentInputDeviceChangedEvent-changeReason: AudioStreamDeviceChangeReason-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core

## devices

```TypeScript
devices: AudioDeviceDescriptors
```

Audio input device descriptors after change.

**Type:** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**Since:** 21

<!--Device-CurrentInputDeviceChangedEvent-devices: AudioDeviceDescriptors--><!--Device-CurrentInputDeviceChangedEvent-devices: AudioDeviceDescriptors-End-->

**System capability:** SystemCapability.Multimedia.Audio.Core
