# AudioDeviceDescriptor

Describes an audio device.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Audio.Device

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## dmDeviceInfo

```TypeScript
readonly dmDeviceInfo?: string
```

Extended information for distributed device, includes whether the device supports stereo, Device SN, etc.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## dmDeviceType

```TypeScript
readonly dmDeviceType?: number
```

Only [SPEAKER](arkts-audio-audio-devicetype-e.md#speaker) with networkId、[REMOTE_CAST](arkts-audio-audio-devicetype-e.md#remote_cast) or [REMOTE_DAUDIO](arkts-audio-audio-devicetype-e.md#remote_daudio) has dmDeviceType which indicated deviceTypeId.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## highQualityRecordingSupported

```TypeScript
readonly highQualityRecordingSupported?: boolean
```

whether supports high-quality recording.

**Type:** boolean

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Core

**System API:** This is a system API.

## interruptGroupId

```TypeScript
readonly interruptGroupId: number
```

Interrupt group id

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

## networkId

```TypeScript
readonly networkId: string
```

Device network id

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

## volumeGroupId

```TypeScript
readonly volumeGroupId: number
```

Volume group id

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.
