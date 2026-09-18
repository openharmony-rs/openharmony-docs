# avcodec_audio_channel_layout.h

## Overview

Audio AudioChannel Layout

**Include**: <multimedia/player_framework/avcodec_audio_channel_layout.h>

**Library**: libnative_media_codecbase.so

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 9

**Related module**: [CodecBase](capi-codecbase.md)

## Summary

### Enum

| Name | Description |
| -- | -- |
| [AudioChannelSet](#audiochannelset) | Enumerates the audio channels. Each channel is mapped to a variable of uint64_t.(Deprecated in API11) |
| [AudioChannelLayout](#audiochannellayout) | Enumerates the layouts of audio channels. The output format of the decoder is described using the channel layout of the codec.(Deprecated in API11) |

## Enum type description

### AudioChannelSet

```c
enum AudioChannelSet
```

**Description**

Enumerates the audio channels. Each channel is mapped to a variable of uint64_t.

**Since**: 10

**Deprecated**: 11

**Replaced by**: OH_AudioChannelSet

| Enum item | Description |
| -- | -- |
| AMBISONICS_ACN1 = 1ULL << 42U,  /** first-order ambisonics channel number 1. */ | AMBISONICS_ACN0 = 1ULL << 41U,  /** 0th ambisonics channel number 0. |
| AMBISONICS_ACN2 = 1ULL << 43U,  /** first-order ambisonics channel number 2. */ | AMBISONICS_ACN1 = 1ULL << 42U,  /** first-order ambisonics channel number 1. |
| AMBISONICS_ACN3 = 1ULL << 44U,  /** first-order ambisonics channel number 3. */ | AMBISONICS_ACN2 = 1ULL << 43U,  /** first-order ambisonics channel number 2. |
| AMBISONICS_W = AMBISONICS_ACN0, /** same as 0th ambisonics channel number 0. */ | AMBISONICS_ACN3 = 1ULL << 44U,  /** first-order ambisonics channel number 3. |
| AMBISONICS_Y = AMBISONICS_ACN1, /** same as first-order ambisonics channel number 1. */ | AMBISONICS_W = AMBISONICS_ACN0, /** same as 0th ambisonics channel number 0. |
| AMBISONICS_Z = AMBISONICS_ACN2, /** same as first-order ambisonics channel number 2. */ | AMBISONICS_Y = AMBISONICS_ACN1, /** same as first-order ambisonics channel number 1. |
| AMBISONICS_X = AMBISONICS_ACN3, /** same as first-order ambisonics channel number 3. */ | AMBISONICS_Z = AMBISONICS_ACN2, /** same as first-order ambisonics channel number 2. |
|  | AMBISONICS_X = AMBISONICS_ACN3, /** same as first-order ambisonics channel number 3. |
| AMBISONICS_ACN5 = 1ULL << 46U, /** second-order ambisonics channel number 5. */ | AMBISONICS_ACN4 = 1ULL << 45U, /** second-order ambisonics channel number 4. |
| AMBISONICS_ACN6 = 1ULL << 47U, /** second-order ambisonics channel number 6. */ | AMBISONICS_ACN5 = 1ULL << 46U, /** second-order ambisonics channel number 5. |
| AMBISONICS_ACN7 = 1ULL << 48U, /** second-order ambisonics channel number 7. */ | AMBISONICS_ACN6 = 1ULL << 47U, /** second-order ambisonics channel number 6. |
| AMBISONICS_ACN8 = 1ULL << 49U, /** second-order ambisonics channel number 8. */ | AMBISONICS_ACN7 = 1ULL << 48U, /** second-order ambisonics channel number 7. |
|  | AMBISONICS_ACN8 = 1ULL << 49U, /** second-order ambisonics channel number 8. |
| AMBISONICS_ACN10 = 1ULL << 51U, /** third-order ambisonics channel number 10. */ | AMBISONICS_ACN9 = 1ULL << 50U,  /** third-order ambisonics channel number 9. |
| AMBISONICS_ACN11 = 1ULL << 52U, /** third-order ambisonics channel number 11. */ | AMBISONICS_ACN10 = 1ULL << 51U, /** third-order ambisonics channel number 10. |
| AMBISONICS_ACN12 = 1ULL << 53U, /** third-order ambisonics channel number 12. */ | AMBISONICS_ACN11 = 1ULL << 52U, /** third-order ambisonics channel number 11. |
| AMBISONICS_ACN13 = 1ULL << 54U, /** third-order ambisonics channel number 13. */ | AMBISONICS_ACN12 = 1ULL << 53U, /** third-order ambisonics channel number 12. |
| AMBISONICS_ACN14 = 1ULL << 55U, /** third-order ambisonics channel number 14. */ | AMBISONICS_ACN13 = 1ULL << 54U, /** third-order ambisonics channel number 13. |
| AMBISONICS_ACN15 = 1ULL << 56U, /** third-order ambisonics channel number 15. */ | AMBISONICS_ACN14 = 1ULL << 55U, /** third-order ambisonics channel number 14. |
| }; | AMBISONICS_ACN15 = 1ULL << 56U, /** third-order ambisonics channel number 15. |

### AudioChannelLayout

```c
enum AudioChannelLayout
```

**Description**

Enumerates the layouts of audio channels. The output format of the decoder is described using the channel layout of the codec.

**Since**: 10

**Deprecated**: 11

**Replaced by**: OH_AudioChannelLayout

| Enum item | Description |
| -- | -- |


