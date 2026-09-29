# DeviceBlockStatusInfo

```TypeScript
interface DeviceBlockStatusInfo
```

Describes the audio device blocked status and device information.

**Since:** 13

<!--Device-audio-interface DeviceBlockStatusInfo--><!--Device-audio-interface DeviceBlockStatusInfo-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## blockStatus

```TypeScript
blockStatus: DeviceBlockStatus
```

Blocked status of the audio device.

**Type:** [DeviceBlockStatus](arkts-audio-audio-deviceblockstatus-e.md)

**Since:** 13

<!--Device-DeviceBlockStatusInfo-blockStatus: DeviceBlockStatus--><!--Device-DeviceBlockStatusInfo-blockStatus: DeviceBlockStatus-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device

## devices

```TypeScript
devices: AudioDeviceDescriptors
```

Device information.

**Type:** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**Since:** 13

<!--Device-DeviceBlockStatusInfo-devices: AudioDeviceDescriptors--><!--Device-DeviceBlockStatusInfo-devices: AudioDeviceDescriptors-End-->

**System capability:** SystemCapability.Multimedia.Audio.Device
