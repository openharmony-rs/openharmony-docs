# AVMetadata

Defines the audio and video metadata. Parameters that are not declared as read-only in
[AVRecorderConfig](#AVRecorderConfig) can be used as input parameters for recording of
[AVRecorder](#AVRecorder).

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## gltf_offset

```TypeScript
gltf_offset?: string
```

The offset value of GLTF 3D model in media file. This parameter is not supported in AVRecorder settings.
If the media file has no GLTF 3D model, gltf_offset is undefined.

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**系统接口：** 此接口为系统接口。

