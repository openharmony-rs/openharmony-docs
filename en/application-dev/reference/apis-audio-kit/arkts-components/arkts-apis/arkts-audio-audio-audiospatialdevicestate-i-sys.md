# AudioSpatialDeviceState (System API)

```TypeScript
interface AudioSpatialDeviceState
```

Describes spatial device state.

**Since:** 11

<!--Device-audio-interface AudioSpatialDeviceState--><!--Device-audio-interface AudioSpatialDeviceState-End-->

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## address

```TypeScript
address: string
```

Spatial device address.

**Type:** string

**Since:** 11

<!--Device-AudioSpatialDeviceState-address: string--><!--Device-AudioSpatialDeviceState-address: string-End-->

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

## isHeadTrackingSupported

```TypeScript
isHeadTrackingSupported: boolean
```

Whether the spatial device supports head tracking.

**Type:** boolean

**Since:** 11

<!--Device-AudioSpatialDeviceState-isHeadTrackingSupported: boolean--><!--Device-AudioSpatialDeviceState-isHeadTrackingSupported: boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

## isSpatializationSupported

```TypeScript
isSpatializationSupported: boolean
```

Whether the spatial device supports spatial rendering.

**Type:** boolean

**Since:** 11

<!--Device-AudioSpatialDeviceState-isSpatializationSupported: boolean--><!--Device-AudioSpatialDeviceState-isSpatializationSupported: boolean-End-->

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.

## spatialDeviceType

```TypeScript
spatialDeviceType: AudioSpatialDeviceType
```

Spatial device type.

**Type:** [AudioSpatialDeviceType](arkts-audio-audio-audiospatialdevicetype-e-sys.md)

**Since:** 11

<!--Device-AudioSpatialDeviceState-spatialDeviceType: AudioSpatialDeviceType--><!--Device-AudioSpatialDeviceState-spatialDeviceType: AudioSpatialDeviceType-End-->

**System capability:** SystemCapability.Multimedia.Audio.Spatialization

**System API:** This is a system API.
