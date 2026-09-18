# AudioSpatialEnabledStateForDevice (System API)

This interface is used to notify the listener of any device Spatialization or Head Tracking enable or Adaptive Spatial Rendering state change.

**Since:** 12

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

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

## enabled

```TypeScript
enabled: boolean
```

Spatialization or Head Tracking or Adaptive Spatial Rendering enable state.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.
