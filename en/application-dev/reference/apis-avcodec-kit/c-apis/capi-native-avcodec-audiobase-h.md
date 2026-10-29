# native_avcodec_audiobase.h

## Overview

Declare the Native API used for basic audio encoding and decoding functions, as well as audio-specific configurations and parameters.

**Include**: <multimedia/player_framework/native_avcodec_audiobase.h>

**Library**: libnative_media_codecbase.so

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 26.1.0

**Related module**: [CodecBase](capi-codecbase.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVCodec_DSDCodecType](#oh_avcodec_dsdcodectype) | OH_AVCodec_DSDCodecType | DSD codec type. |

### Variable

| Name | Description |
| -- | -- |
| const char *OH_MD_KEY_AUDIO_DSD_CODEC_TYPE | DSD decoding key ID. The value is of the int32_t type from [OH_AVCodec_DSDCodecType](capi-native-avcodec-audiobase-h.md#oh_avcodec_dsdcodectype). This key is optional for audio decoders. It is used to identify the DSD decoding type parameter. The default value is OH_AVCODEC_DSD_CODEC_LSBF_PLANAR(0).<br>**Since**: 26.1.0<br>**System capability**: SystemCapability.Multimedia.Media.CodecBase |

## Enum type description

### OH_AVCodec_DSDCodecType

```c
enum OH_AVCodec_DSDCodecType
```

**Description**

DSD codec type.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_AVCODEC_DSD_CODEC_LSBF_PLANAR = 0 | dsf container format for LSB first and flat layout.<br>**Since**: 26.1.0 |
| OH_AVCODEC_DSD_CODEC_MSBF_PLANAR = 1 | MSB first and flat layout of the dsf container format.<br>**Since**: 26.1.0 |
| OH_AVCODEC_DSD_CODEC_MSBF = 2 | MSB first and interleaved dff container format.<br>**Since**: 26.1.0 |


