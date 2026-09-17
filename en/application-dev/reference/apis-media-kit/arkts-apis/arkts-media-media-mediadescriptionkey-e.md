# MediaDescriptionKey

Enumerates the media description keys.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_TRACK_INDEX

```TypeScript
MD_KEY_TRACK_INDEX = 'track_index'
```

Track index. The corresponding key value type is number.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_TRACK_TYPE

```TypeScript
MD_KEY_TRACK_TYPE = 'track_type'
```

Track type. The corresponding key value type is number. For details, see [MediaType](arkts-media-media-mediatype-e.md).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_CODEC_MIME

```TypeScript
MD_KEY_CODEC_MIME = 'codec_mime'
```

Codec MIME type. The corresponding key value type is string.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_DURATION

```TypeScript
MD_KEY_DURATION = 'duration'
```

Media duration. The corresponding key value type is number, measured in ms.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_BITRATE

```TypeScript
MD_KEY_BITRATE = 'bitrate'
```

Bit rate. The corresponding key value type is number, measured in bit/s. If the value is **undefined** or **0**, the bit rate is abnormal.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_WIDTH

```TypeScript
MD_KEY_WIDTH = 'width'
```

Video width. The corresponding key value type is number, measured in px.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_HEIGHT

```TypeScript
MD_KEY_HEIGHT = 'height'
```

Video height. The corresponding key value type is number, measured in px.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_FRAME_RATE

```TypeScript
MD_KEY_FRAME_RATE = 'frame_rate'
```

Video frame rate. The corresponding key value type is number, measured in frames per 100 seconds.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_AUD_CHANNEL_COUNT

```TypeScript
MD_KEY_AUD_CHANNEL_COUNT = 'channel_count'
```

Audio channel count. The corresponding key value type is number.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_AUD_SAMPLE_RATE

```TypeScript
MD_KEY_AUD_SAMPLE_RATE = 'sample_rate'
```

Sample rate. The corresponding key value type is number, measured in Hz.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_AUD_SAMPLE_DEPTH

```TypeScript
MD_KEY_AUD_SAMPLE_DEPTH = 'sample_depth'
```

Bit depth. The corresponding key value type is number, measured in bits.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_LANGUAGE

```TypeScript
MD_KEY_LANGUAGE = 'language'
```

Subtitle language. The corresponding key value type is string.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_TRACK_NAME

```TypeScript
MD_KEY_TRACK_NAME = 'track_name'
```

Track name. The corresponding key value type is string.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_HDR_TYPE

```TypeScript
MD_KEY_HDR_TYPE = 'hdr_type'
```

Codec track type. The corresponding key value type is string.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_ORIGINAL_WIDTH

```TypeScript
MD_KEY_ORIGINAL_WIDTH = 'original_width'
```

Original video width. The corresponding key value type is number, measured in px.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_ORIGINAL_HEIGHT

```TypeScript
MD_KEY_ORIGINAL_HEIGHT = 'original_height'
```

Original video height. The corresponding key value type is number, measured in px.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_MIME_TYPE

```TypeScript
MD_KEY_MIME_TYPE = 'mime_type'
```

MIME type of the track. The corresponding key value type is string. For audio and video tracks, the value is the same as that of **MD_KEY_CODEC_MIME**.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_REFERENCE_TRACK_IDS

```TypeScript
MD_KEY_REFERENCE_TRACK_IDS = 'ref_track_ids'
```

Reference relationships between this track and other tracks. The corresponding key value type is string, with values separated by commas (,).

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Media.Core

## MD_KEY_TRACK_REFERENCE_TYPE

```TypeScript
MD_KEY_TRACK_REFERENCE_TYPE = 'track_ref_type'
```

Auxiliary type of this track when it acts as a reference track. The corresponding key value type is string.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Media.Core
