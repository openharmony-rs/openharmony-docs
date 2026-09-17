# AudioStreamDeviceChangeInfo

Describes the event received by the application when the audio stream device is changed.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Device

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## changeReason

```TypeScript
changeReason: AudioStreamDeviceChangeReason
```

Audio stream device change reason.

**Type:** [AudioStreamDeviceChangeReason](arkts-audio-audio-audiostreamdevicechangereason-e.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## devices

```TypeScript
devices: AudioDeviceDescriptors
```

Audio device descriptors after change.

**Type:** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Device

## preDevices

```TypeScript
preDevices?: AudioDeviceDescriptors
```

Audio device descriptors before change.

**Type:** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Device
