# AudioDevicePair

```TypeScript
interface AudioDevicePair
```

Describes an audio device pair including both input and output devices.

**Since:** 26.0.0

<!--Device-audio-interface AudioDevicePair--><!--Device-audio-interface AudioDevicePair-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## inputDevice

```TypeScript
inputDevice: AudioDeviceDescriptor
```

Input audio device descriptor.

**Type:** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioDevicePair-inputDevice: AudioDeviceDescriptor--><!--Device-AudioDevicePair-inputDevice: AudioDeviceDescriptor-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## outputDevice

```TypeScript
outputDevice: AudioDeviceDescriptor
```

Output audio device descriptor.

**Type:** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AudioDevicePair-outputDevice: AudioDeviceDescriptor--><!--Device-AudioDevicePair-outputDevice: AudioDeviceDescriptor-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device
