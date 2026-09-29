# AudioStreamDeviceChangeInfo

```TypeScript
interface AudioStreamDeviceChangeInfo
```

Describes the event received by the application when the audio stream device is changed.

**Since:** 11

<!--Device-audio-interface AudioStreamDeviceChangeInfo--><!--Device-audio-interface AudioStreamDeviceChangeInfo-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioStreamDeviceChangeInfo-changeReason: AudioStreamDeviceChangeReason--><!--Device-AudioStreamDeviceChangeInfo-changeReason: AudioStreamDeviceChangeReason-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## devices

```TypeScript
devices: AudioDeviceDescriptors
```

Audio device descriptors after change.

**Type:** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AudioStreamDeviceChangeInfo-devices: AudioDeviceDescriptors--><!--Device-AudioStreamDeviceChangeInfo-devices: AudioDeviceDescriptors-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## preDevices

```TypeScript
preDevices?: AudioDeviceDescriptors
```

Audio device descriptors before change.

**Type:** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-AudioStreamDeviceChangeInfo-preDevices?: AudioDeviceDescriptors--><!--Device-AudioStreamDeviceChangeInfo-preDevices?: AudioDeviceDescriptors-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device
