# avmetakeys.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Overview

Defines audio and video metadata keys.

**File to include**: <multimedia/player_framework/avmetakeys.h>

**Library**: libavmedia_base.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 23

**Related module**: [AVMediaBase](capi-avmediabase.md)

## Total

### Variables

| Name| Description|
| -- | -- |
| const char * OH_AVMETA_KEY_TRACK_INDEX | Track index. The value type is int32_t.<br>**Since**: 23<br>**System capability**: SystemCapability.Multimedia.Media.Core|
| const char * OH_AVMETA_KEY_TRACK_TYPE | Track type. The value type is int32_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_MIME_TYPE | MIME type of the codec. The value type is string.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_DURATION | Media duration, in microseconds. The value type is int64_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_BITRATE | Bit rate, in bit/s. The value type is int64_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_FRAME_RATE | Video frame rate (number of frames per 100 seconds). The value type is double.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_WIDTH | Video width. The value type is int32_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_HEIGHT | Video height. The value type is int32_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_CHANNEL_COUNT | Number of audio channels. The value type is int32_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_SAMPLE_RATE | Audio sampling rate (Hz). The value type is int32_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_SAMPLE_DEPTH | Audio sampling bit depth. The value type is int32_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_LANGUAGE | Language ID. The value type is string.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_TRACK_NAME | Track name. The value type is string.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_HDR_TYPE | HDR type. The value type is int32_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_ORIGINAL_WIDTH | Original video width. The value type is int32_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_ORIGINAL_HEIGHT | Original video height. The value type is int32_t.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_REF_TRACK_IDS | List of referenced track IDs, which is used only for the metadata extractor.<br>**Since**: 23|
| const char * OH_AVMETA_KEY_TRACK_REF_TYPE | Track reference type, which is used only for the metadata extractor.<br>**Since**: 23|
