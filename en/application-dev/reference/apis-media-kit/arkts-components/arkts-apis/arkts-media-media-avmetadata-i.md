# AVMetadata

Defines the audio and video metadata. Parameters that are not declared as read-only in [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md) can be used as input parameters for recording of [AVRecorder](arkts-media-media-avrecorder-i.md).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## album

```TypeScript
album?: string
```

Title of the album. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## albumArtist

```TypeScript
albumArtist?: string
```

Artist of the album. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## artist

```TypeScript
artist?: string
```

Artist of the media asset. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## author

```TypeScript
author?: string
```

Author of the media asset. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## composer

```TypeScript
composer?: string
```

Composer of the media asset. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## customInfo

```TypeScript
customInfo?: Record<string, string>
```

Custom key-value mappings obtained from **moov.meta.list**.

**Type:** Record&lt;string, string&gt;

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## dateTime

```TypeScript
dateTime?: string
```

Time when the media asset is created. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## dateTimeFormat

```TypeScript
dateTimeFormat?: string
```

Time when the media asset is created. The value is in the YYYY-MM-DD HH:mm:ss format. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## description

```TypeScript
description?: string
```

Description of the media asset. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## duration

```TypeScript
duration?: string
```

Duration of the media asset. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## encoder

```TypeScript
encoder?: string
```

The identifier that represents the software or hardware and settings used for encoding. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## genre

```TypeScript
genre?: string
```

Type or genre of the media asset.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## hasAudio

```TypeScript
hasAudio?: string
```

Whether the media asset contains audio. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## hasVideo

```TypeScript
hasVideo?: string
```

Whether the media asset contains a video. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## hdrType

```TypeScript
hdrType?: HdrType
```

HDR type of the media asset. This parameter is not supported in AVRecorder settings.

**Type:** [HdrType](arkts-media-media-hdrtype-e.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## location

```TypeScript
location?: Location
```

Geographical location of the media asset.

**Type:** [Location](arkts-media-media-location-i.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## mimeType

```TypeScript
mimeType?: string
```

MIME type of the media asset. This parameter is not supported in AVRecorder settings. Some example mime types include: "video/mp4", "audio/mp4", "audio/amr-wb".

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## sampleRate

```TypeScript
sampleRate?: string
```

Audio sampling rate, in Hz. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## title

```TypeScript
title?: string
```

Title of the media asset. This parameter is not supported in AVRecorder settings. This parameter is read-only in the current version.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## trackCount

```TypeScript
trackCount?: string
```

Number of tracks of the media asset. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## tracks

```TypeScript
tracks?: Array<MediaDescription>
```

Tracks info of the media asset. This parameter is not supported in AVRecorder settings.

**Type:** Array&lt;[MediaDescription](arkts-media-media-mediadescription-i.md)&gt;

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## videoHeight

```TypeScript
videoHeight?: string
```

Video height, in px. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## videoOrientation

```TypeScript
videoOrientation?: string
```

Video rotation direction, in degrees.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor

## videoWidth

```TypeScript
videoWidth?: string
```

Video width, in px. This parameter is not supported in AVRecorder settings.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVMetadataExtractor
