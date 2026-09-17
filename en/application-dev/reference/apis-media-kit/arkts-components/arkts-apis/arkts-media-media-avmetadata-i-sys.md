# AVMetadata

Defines the audio and video metadata. Parameters that are not declared as read-only in [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md) can be used as input parameters for recording of [AVRecorder](arkts-media-media-avrecorder-i.md).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## gltf_offset

```TypeScript
gltf_offset?: string
```

The offset value of GLTF 3D model in media file. This parameter is not supported in AVRecorder settings. If the media file has no GLTF 3D model, gltf_offset is undefined.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

**System API:** This is a system API.
