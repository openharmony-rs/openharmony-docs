# AudioPersonalizedSpatialEnabledChangeForAnyDevice (System API)

This interface is used to notify the listener of personalized spatialization enabled state change of any device.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## deviceDescriptor

```TypeScript
deviceDescriptor: AudioDeviceDescriptor
```

Audio device description.

**Type:** [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

## enabled

```TypeScript
enabled: boolean
```

Personalized spatialization enable state.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.
