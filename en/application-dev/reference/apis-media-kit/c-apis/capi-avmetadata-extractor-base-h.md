# avmetadata_extractor_base.h

## Overview

The file declares the constants used by the AVMetadataExtractor.

**Library**: libavmetadata_extractor.so

**Since**: 18

**Related module**: [AVMetadataExtractor](capi-media-kit-avmetadataextractor.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVMetadataExtractor_FrameInfo](capi-avmetadataextractor-oh-avmetadataextractor-frameinfo.md) | OH_AVMetadataExtractor_FrameInfo | Defines the information about a frame extracted from a video. |
| [OH_AVMetadataExtractor_OutputParam](capi-avmetadataextractor-oh-avmetadataextractor-outputparam.md) | OH_AVMetadataExtractor_OutputParam | Defines a struct for the output parameters of a frame extracted by **AVMetadataExtractor**. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVMetadataExtractor_FetchState](#oh_avmetadataextractor_fetchstate) | OH_AVMetadataExtractor_FetchState | Enumerates the result status of the frame extraction operation. |

### Variables

| Name | Description |
| -- | -- |
| static const char *OH_AVMETADATA_EXTRACTOR_ALBUM = "album" | Pointer to the key for obtaining the title of the album. The value type is const char*.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_ALBUM = "album"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_ALBUM = "album"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_ALBUM_ARTIST = "albumArtist" | Pointer to the key for obtaining the artist of the album. The value type is const char*.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_ALBUM_ARTIST = "albumArtist"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_ALBUM_ARTIST = "albumArtist"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_ARTIST = "artist" | Pointer to the key for obtaining the artist of the media asset. The value type is const char*.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_ARTIST = "artist"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_ARTIST = "artist"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_AUTHOR = "author" | Pointer to the key for obtaining the author of the media asset. The value type is const char*.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_AUTHOR = "author"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_AUTHOR = "author"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_DATE_TIME = "dateTime" | Pointer to the key for obtaining the creation time of the media asset. The value type is const char*.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_DATE_TIME = "dateTime"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_DATE_TIME = "dateTime"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_DATE_TIME_FORMAT = "dateTimeFormat" | Pointer to the key for obtaining the creation time of the media asset. The value type is const char* and the output format is YYYY-MM-DD HH:mm:ss.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_DATE_TIME_FORMAT = "dateTimeFormat"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_DATE_TIME_FORMAT = "dateTimeFormat"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_COMPOSER = "composer" | Pointer to the key for obtaining the composer of the media asset. The value type is const char*.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_COMPOSER = "composer"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_COMPOSER = "composer"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_DURATION = "duration" | Pointer to the key for obtaining the duration of the media asset, in ms. The value type is int64_t.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_DURATION = "duration"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_DURATION = "duration"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_GENRE = "genre" | Pointer to the key for obtaining the type or genre of the media asset. The value type is const char*.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_GENRE = "genre"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_GENRE = "genre"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_HAS_AUDIO = "hasAudio" | Pointer to the key for obtaining the flag indicating whether the media asset contains audio. The value type is int32_t.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_HAS_AUDIO = "hasAudio"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_HAS_AUDIO = "hasAudio"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_HAS_VIDEO = "hasVideo" | Pointer to the key for obtaining the flag indicating whether the media asset contains video. The value type is int32_t.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_HAS_VIDEO = "hasVideo"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_HAS_VIDEO = "hasVideo"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_MIME_TYPE = "mimeType" | Pointer to the key for obtaining the MIME type of the media asset. The value type is const char*, for example, video/mp4, audio/mp4, and audio/amr wb.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_MIME_TYPE = "mimeType"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_MIME_TYPE = "mimeType"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_TRACK_COUNT = "trackCount" | Pointer to the key for obtaining the number of tracks of the media asset. The value type is int32_t.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_TRACK_COUNT = "trackCount"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_TRACK_COUNT = "trackCount"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_SAMPLE_RATE = "sampleRate" | Pointer to the key for obtaining the audio sample rate, in Hz. The value type is int32_t.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_SAMPLE_RATE = "sampleRate"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_SAMPLE_RATE = "sampleRate"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_TITLE = "title" | Pointer to the key for obtaining the title of the media asset. The value type is const char*.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_TITLE = "title"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_TITLE = "title"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_HEIGHT = "videoHeight" | Pointer to the key for obtaining the video height, in px. The value type is int32_t.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_HEIGHT = "videoHeight"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_HEIGHT = "videoHeight"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_WIDTH = "videoWidth" | Pointer to the key for obtaining the video weight, in px. The value type is int32_t.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_WIDTH = "videoWidth"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_WIDTH = "videoWidth"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_ORIENTATION = "videoOrientation" | Pointer to the key for obtaining the video rotation direction, in degrees (°). The value type is int32_t.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_ORIENTATION = "videoOrientation"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_ORIENTATION = "videoOrientation"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_IS_HDR_VIVID = "hdrType" | Pointer to the key for obtaining the flag indicating whether the video is an HDR Vivid video. The value type is int32_t. For details, see [OH_Core_HdrType](../../apis-avcodec-kit/c-apis/capi-media-types-h.md#oh_core_hdrtype) in **media_types.h**.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_IS_HDR_VIVID = "hdrType"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_VIDEO_IS_HDR_VIVID = "hdrType"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_LOCATION_LATITUDE = "latitude" | Pointer to the key for obtaining the latitude in the geographical location. The value type is float.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_LOCATION_LATITUDE = "latitude"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_LOCATION_LATITUDE = "latitude"-End--> |
| static const char *OH_AVMETADATA_EXTRACTOR_LOCATION_LONGITUDE = "longitude" | Pointer to the key for obtaining the longitude in the geographical location. The value type is float.<br>**Since**: 18<br><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_LOCATION_LONGITUDE = "longitude"--><!--Device-static const char *OH_AVMETADATA_EXTRACTOR_LOCATION_LONGITUDE = "longitude"-End--> |

## Enum type description

### OH_AVMetadataExtractor_FetchState

```c
enum OH_AVMetadataExtractor_FetchState
```

**Description**

Enumerates the result status of the frame extraction operation.

<!--Device-enum OH_AVMetadataExtractor_FetchState--><!--Device-enum OH_AVMetadataExtractor_FetchState-End-->

**Since**: 23

| Enum item | Description |
| -- | -- |
| OH_AVMETADATA_EXTRACTOR_FETCH_FAILED = 0 | The extraction operation failed.<br><!--Device-OH_AVMETADATA_EXTRACTOR_FETCH_FAILED = 0--><!--Device-OH_AVMETADATA_EXTRACTOR_FETCH_FAILED = 0-End--> |
| OH_AVMETADATA_EXTRACTOR_FETCH_SUCCEEDED = 1 | The extraction operation succeeded.<br><!--Device-OH_AVMETADATA_EXTRACTOR_FETCH_SUCCEEDED = 1--><!--Device-OH_AVMETADATA_EXTRACTOR_FETCH_SUCCEEDED = 1-End--> |
| OH_AVMETADATA_EXTRACTOR_FETCH_CANCELED = 2 | The extraction operation was canceled by the user.<br><!--Device-OH_AVMETADATA_EXTRACTOR_FETCH_CANCELED = 2--><!--Device-OH_AVMETADATA_EXTRACTOR_FETCH_CANCELED = 2-End--> |


