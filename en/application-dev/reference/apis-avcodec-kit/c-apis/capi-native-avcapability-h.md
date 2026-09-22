# native_avcapability.h

## Overview

Declare the Native API used for querying encoding and decoding capabilities.

**Library**: libnative_media_codecbase.so

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Related module**: [AVCapability](capi-avcapability.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVRange](capi-avcapability-oh-avrange.md) | OH_AVRange | Range contain min and max value |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) | OH_AVCapability | Forward declaration of OH_AVCapability. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVCodecCategory](#oh_avcodeccategory) | OH_AVCodecCategory | The codec category |
| [OH_AVCodecType](#oh_avcodectype) | OH_AVCodecType | The codec type |
| [OH_AVCapabilityFeature](#oh_avcapabilityfeature) | OH_AVCapabilityFeature | The enum of optional features that can be used in specific codec seenarios. |

### Function

| Name | Description |
| -- | -- |
| [OH_AVCapability *OH_AVCodec_GetCapability(const char *mime, bool isEncoder)](#oh_avcodec_getcapability) | Get a system-recommended codec's capability. |
| [OH_AVCapability *OH_AVCodec_GetCapabilityByCategory(const char *mime, bool isEncoder, OH_AVCodecCategory category)](#oh_avcodec_getcapabilitybycategory) | Get a codec's capability within the specified category. By specifying the category, the matched codec is limited to either hardware codecs or software codecs. |
| [OH_AVCapability **OH_AVCodec_GetCapabilityList(OH_AVCodecType codecType, uint32_t *count)](#oh_avcodec_getcapabilitylist) | Obtains a list of codec capabilities for a specified codec type.<br> This function retrieves all matching codec capabilities based on the provided codec type. |
| [bool OH_AVCapability_IsHardware(OH_AVCapability *capability)](#oh_avcapability_ishardware) | Check if the capability instance is describing a hardware codec. |
| [bool OH_AVCapability_IsSecure(OH_AVCapability *capability)](#oh_avcapability_issecure) | Check if the capability instance is describing a secure codec. |
| [const char *OH_AVCapability_GetName(OH_AVCapability *capability)](#oh_avcapability_getname) | Get the codec name. |
| [const char *OH_AVCapability_GetMimeType(OH_AVCapability *capability)](#oh_avcapability_getmimetype) | Get the codec mime type. |
| [bool OH_AVCapability_CheckMimeType(OH_AVCapability *capability, const char *mimeType)](#oh_avcapability_checkmimetype) | Check if the mime type of the codec of the capability matches the specified mime type. |
| [int32_t OH_AVCapability_GetMaxSupportedInstances(OH_AVCapability *capability)](#oh_avcapability_getmaxsupportedinstances) | Get the supported max instance number of the codec. |
| [OH_AVErrCode OH_AVCapability_GetEncoderBitrateRange(OH_AVCapability *capability, OH_AVRange *bitrateRange)](#oh_avcapability_getencoderbitraterange) | Get the encoder's supported bitrate range. |
| [bool OH_AVCapability_IsEncoderBitrateModeSupported(OH_AVCapability *capability, OH_BitrateMode bitrateMode)](#oh_avcapability_isencoderbitratemodesupported) | Check if the encoder supports the specific bitrate mode. |
| [OH_AVErrCode OH_AVCapability_GetEncoderQualityRange(OH_AVCapability *capability, OH_AVRange *qualityRange)](#oh_avcapability_getencoderqualityrange) | Get the encoder's supported quality range. |
| [OH_AVErrCode OH_AVCapability_GetEncoderComplexityRange(OH_AVCapability *capability, OH_AVRange *complexityRange)](#oh_avcapability_getencodercomplexityrange) | Get the encoder's supported encoder complexity range. |
| [OH_AVErrCode OH_AVCapability_GetAudioSupportedSampleRates(OH_AVCapability *capability, const int32_t **sampleRates, uint32_t *sampleRateNum)](#oh_avcapability_getaudiosupportedsamplerates) | Get the audio codec's supported sample rates. |
| [OH_AVErrCode OH_AVCapability_GetAudioSupportedSampleRateRanges(OH_AVCapability *capability, OH_AVRange **sampleRateRanges, uint32_t *rangesNum)](#oh_avcapability_getaudiosupportedsamplerateranges) | Get the audio codec's supported sample rate ranges. |
| [OH_AVErrCode OH_AVCapability_GetAudioChannelCountRange(OH_AVCapability *capability, OH_AVRange *channelCountRange)](#oh_avcapability_getaudiochannelcountrange) | Get the audio codec's supported audio channel count range. |
| [OH_AVErrCode OH_AVCapability_GetVideoWidthAlignment(OH_AVCapability *capability, int32_t *widthAlignment)](#oh_avcapability_getvideowidthalignment) | Get the video codec's supported video width alignment. |
| [OH_AVErrCode OH_AVCapability_GetVideoHeightAlignment(OH_AVCapability *capability, int32_t *heightAlignment)](#oh_avcapability_getvideoheightalignment) | Get the video codec's supported video height alignment. |
| [OH_AVErrCode OH_AVCapability_GetVideoWidthRangeForHeight(OH_AVCapability *capability, int32_t height, OH_AVRange *widthRange)](#oh_avcapability_getvideowidthrangeforheight) | Get the video codec's supported video width range for a specific height. |
| [OH_AVErrCode OH_AVCapability_GetVideoHeightRangeForWidth(OH_AVCapability *capability, int32_t width, OH_AVRange *heightRange)](#oh_avcapability_getvideoheightrangeforwidth) | Get the video codec's supported video height range for a specific width. |
| [OH_AVErrCode OH_AVCapability_GetVideoWidthRange(OH_AVCapability *capability, OH_AVRange *widthRange)](#oh_avcapability_getvideowidthrange) | Get the video codec's supported video width range. |
| [OH_AVErrCode OH_AVCapability_GetVideoHeightRange(OH_AVCapability *capability, OH_AVRange *heightRange)](#oh_avcapability_getvideoheightrange) | Get the video codec's supported video height range. |
| [bool OH_AVCapability_IsVideoSizeSupported(OH_AVCapability *capability, int32_t width, int32_t height)](#oh_avcapability_isvideosizesupported) | Check if the video codec supports the specific video size. |
| [OH_AVErrCode OH_AVCapability_GetVideoFrameRateRange(OH_AVCapability *capability, OH_AVRange *frameRateRange)](#oh_avcapability_getvideoframeraterange) | Get the video codec's supported video frame rate range. |
| [OH_AVErrCode OH_AVCapability_GetVideoFrameRateRangeForSize(OH_AVCapability *capability, int32_t width, int32_t height, OH_AVRange *frameRateRange)](#oh_avcapability_getvideoframeraterangeforsize) | Get the Video codec's supported video frame rate range for a specified video size. |
| [bool OH_AVCapability_AreVideoSizeAndFrameRateSupported(OH_AVCapability *capability, int32_t width, int32_t height, int32_t frameRate)](#oh_avcapability_arevideosizeandframeratesupported) | Check if the video codec supports the specific combination of video size and frame rate. |
| [OH_AVErrCode OH_AVCapability_GetVideoSupportedPixelFormats(OH_AVCapability *capability, const int32_t **pixelFormats, uint32_t *pixelFormatNum)](#oh_avcapability_getvideosupportedpixelformats) | Get the video codec's supported video pixel format. |
| [OH_AVErrCode OH_AVCapability_GetVideoSupportedNativeBufferFormats(OH_AVCapability *capability, const OH_NativeBuffer_Format **nativeBufferFormats, uint32_t *nativeBufferFormatNum)](#oh_avcapability_getvideosupportednativebufferformats) | Get the native buffer formats supported by the video codec.<br> This function provides information about the native buffer formats that the video codec can handle. |
| [OH_AVErrCode OH_AVCapability_GetSupportedProfiles(OH_AVCapability *capability, const int32_t **profiles, uint32_t *profileNum)](#oh_avcapability_getsupportedprofiles) | Get the codec's supported profiles. |
| [OH_AVErrCode OH_AVCapability_GetSupportedLevelsForProfile(OH_AVCapability *capability, int32_t profile, const int32_t **levels, uint32_t *levelNum)](#oh_avcapability_getsupportedlevelsforprofile) | Get codec's supported levels for a specific profile. |
| [bool OH_AVCapability_AreProfileAndLevelSupported(OH_AVCapability *capability, int32_t profile, int32_t level)](#oh_avcapability_areprofileandlevelsupported) | Check if the codec supports the specific combination of the profile and level. |
| [bool OH_AVCapability_IsFeatureSupported(OH_AVCapability *capability, OH_AVCapabilityFeature feature)](#oh_avcapability_isfeaturesupported) | Check if the codec supports the specified feature. |
| [OH_AVFormat *OH_AVCapability_GetFeatureProperties(OH_AVCapability *capability, OH_AVCapabilityFeature feature)](#oh_avcapability_getfeatureproperties) | Get the properties of the specified feature. It should be noted that the life cycle of the OH_AVFormat instance pointed to by the return value * needs to be manually released by the caller. |

## Enum type description

### OH_AVCodecCategory

```c
enum OH_AVCodecCategory
```

**Description**

The codec category

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

| Enum item | Description |
| -- | -- |

### OH_AVCodecType

```c
enum OH_AVCodecType
```

**Description**

The codec type

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_AVCODEC_TYPE_VIDEO_ENCODER = 0 |  |
| OH_AVCODEC_TYPE_VIDEO_DECODER = 1 |  |
| OH_AVCODEC_TYPE_AUDIO_ENCODER = 2 |  |
| OH_AVCODEC_TYPE_AUDIO_DECODER = 3 |  |

### OH_AVCapabilityFeature

```c
enum OH_AVCapabilityFeature
```

**Description**

The enum of optional features that can be used in specific codec seenarios.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 12

| Enum item | Description |
| -- | -- |
| VIDEO_ENCODER_TEMPORAL_SCALABILITY = 0 | Feature for codec supports temporal scalability. It is only used in video encoder. |
| VIDEO_ENCODER_LONG_TERM_REFERENCE = 1 | Feature for codec supports long-term reference. It is only used in video encoder. |
| VIDEO_LOW_LATENCY = 2 | Feature for codec supports low latency. It is only used in video decoder. |
| VIDEO_ENCODER_B_FRAME = 7 |  |
| VIDEO_DECODER_OUTPUT_IN_DECODING_ORDER = 8 |  |
| VIDEO_ENCODER_PREPROC_DOWNSAMPLING = 9 | Feature for codec supports downsampling preprocessing. It is only used in video encoder.<br>**Since**: 26.0.0 |
| VIDEO_ENCODER_PREPROC_CROP = 10 | Feature for codec supports Crop preprocessing. It is only used in video encoder.<br>**Since**: 26.0.0 |


## Function description

### OH_AVCodec_GetCapability()

```c
OH_AVCapability *OH_AVCodec_GetCapability(const char *mime, bool isEncoder)
```

**Description**

Get a system-recommended codec's capability.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *mime | Mime type |
| bool isEncoder | True for encoder, false for decoder |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVCapability *](capi-avcapability-oh-avcapability.md) | Returns a capability instance if an existing codec matches,  if the specified mime type doesn't match any existing codec, returns NULL. |

### OH_AVCodec_GetCapabilityByCategory()

```c
OH_AVCapability *OH_AVCodec_GetCapabilityByCategory(const char *mime, bool isEncoder, OH_AVCodecCategory category)
```

**Description**

Get a codec's capability within the specified category. By specifying the category, the matched codec is limited to either hardware codecs or software codecs.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *mime | Mime type |
| bool isEncoder | True for encoder, false for decoder |
| [OH_AVCodecCategory](capi-native-avcapability-h.md#oh_avcodeccategory) category | The codec category |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVCapability *](capi-avcapability-oh-avcapability.md) | Returns a capability instance if an existing codec matches,  if the specified mime type doesn't match any existing codec, returns NULL |

### OH_AVCodec_GetCapabilityList()

```c
OH_AVCapability **OH_AVCodec_GetCapabilityList(OH_AVCodecType codecType, uint32_t *count)
```

**Description**

Obtains a list of codec capabilities for a specified codec type.<br> This function retrieves all matching codec capabilities based on the provided codec type.

> **Note**:
>
> The memory for the codec capability list is managed internally. Developers MUST NOT manually allocate or free this memory.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCodecType](capi-native-avcapability-h.md#oh_avcodectype) codecType | The type of codec to filter by, refer to [OH_AVCodecType](capi-native-avcapability-h.md#oh_avcodectype). |
| uint32_t *count | Output parameter. A pointer to a uint32_t variable that will store the number of matched codec capabilities found. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVCapability **](capi-avcapability-oh-avcapability.md) | Returns a pointer to an array of [OH_AVCapability](capi-avcapability-oh-avcapability.md) instances if matches are found;          returns NULL if no matching codecs are found or if an error occurs. |

### OH_AVCapability_IsHardware()

```c
bool OH_AVCapability_IsHardware(OH_AVCapability *capability)
```

**Description**

Check if the capability instance is describing a hardware codec.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the capability instance is describing a hardware codec,  false if the capability instance is describing a software codec |

### OH_AVCapability_IsSecure()

```c
bool OH_AVCapability_IsSecure(OH_AVCapability *capability)
```

**Description**

Check if the capability instance is describing a secure codec.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the capability instance is describing a secure codec,  false if the capability instance is describing a non-secure codec |

### OH_AVCapability_GetName()

```c
const char *OH_AVCapability_GetName(OH_AVCapability *capability)
```

**Description**

Get the codec name.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns codec name string |

### OH_AVCapability_GetMimeType()

```c
const char *OH_AVCapability_GetMimeType(OH_AVCapability *capability)
```

**Description**

Get the codec mime type.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns codec mime type string |

### OH_AVCapability_CheckMimeType()

```c
bool OH_AVCapability_CheckMimeType(OH_AVCapability *capability, const char *mimeType)
```

**Description**

Check if the mime type of the codec of the capability matches the specified mime type.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |
| const char *mimeType | target mime type string to check |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the mime type matches, false otherwise |

### OH_AVCapability_GetMaxSupportedInstances()

```c
int32_t OH_AVCapability_GetMaxSupportedInstances(OH_AVCapability *capability)
```

**Description**

Get the supported max instance number of the codec.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the max supported codec instance number |

### OH_AVCapability_GetEncoderBitrateRange()

```c
OH_AVErrCode OH_AVCapability_GetEncoderBitrateRange(OH_AVCapability *capability, OH_AVRange *bitrateRange)
```

**Description**

Get the encoder's supported bitrate range.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Encoder capability pointer. If a decoder capability pointer is given, undefined behavior occurs |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *bitrateRange | Output parameter. Encoder bitrate range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, or the bitrateRange is nullptr. |

### OH_AVCapability_IsEncoderBitrateModeSupported()

```c
bool OH_AVCapability_IsEncoderBitrateModeSupported(OH_AVCapability *capability, OH_BitrateMode bitrateMode)
```

**Description**

Check if the encoder supports the specific bitrate mode.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Encoder capability pointer. If a decoder capability pointer is given, undefined behavior occurs |
| OH_BitrateMode bitrateMode | Bitrate mode |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the bitrate mode is supported, false if the bitrate mode is not supported |

### OH_AVCapability_GetEncoderQualityRange()

```c
OH_AVErrCode OH_AVCapability_GetEncoderQualityRange(OH_AVCapability *capability, OH_AVRange *qualityRange)
```

**Description**

Get the encoder's supported quality range.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Encoder capability pointer. If a decoder capability pointer is given, undefined behavior occurs |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *qualityRange | Output parameter. Encoder quality range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, or the qualityRange is nullptr. |

### OH_AVCapability_GetEncoderComplexityRange()

```c
OH_AVErrCode OH_AVCapability_GetEncoderComplexityRange(OH_AVCapability *capability, OH_AVRange *complexityRange)
```

**Description**

Get the encoder's supported encoder complexity range.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Encoder capability pointer. If a decoder capability pointer is given, undefined behavior occurs |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *complexityRange | Output parameter. Encoder complexity range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, or the complexityRange is nullptr. |

### OH_AVCapability_GetAudioSupportedSampleRates()

```c
OH_AVErrCode OH_AVCapability_GetAudioSupportedSampleRates(OH_AVCapability *capability, const int32_t **sampleRates, uint32_t *sampleRateNum)
```

**Description**

Get the audio codec's supported sample rates.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Audio codec capability pointer. If a video codec capability pointer is given, undefined behavior occurs |
| const int32_t **sampleRates | Output parameter. A pointer to the sample rates array |
| uint32_t *sampleRateNum | Output parameter. The element number of the sample rates array |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, the sampleRates is nullptr, or sampleRateNum is nullptr.  [AV_ERR_UNKNOWN](capi-native-averrors-h.md#oh_averrcode), unknown error.  [AV_ERR_NO_MEMORY](capi-native-averrors-h.md#oh_averrcode), internal use memory malloc failed. |

### OH_AVCapability_GetAudioSupportedSampleRateRanges()

```c
OH_AVErrCode OH_AVCapability_GetAudioSupportedSampleRateRanges(OH_AVCapability *capability, OH_AVRange **sampleRateRanges, uint32_t *rangesNum)
```

**Description**

Get the audio codec's supported sample rate ranges.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Audio codec capability pointer. Do not give a video codec capability pointer |
| [OH_AVRange](capi-avcapability-oh-avrange.md) **sampleRateRanges | Output parameter. A pointer to the sample rate ranges array |
| uint32_t *rangesNum | Output parameter. The element number of the sample rate ranges array |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, the sampleRateRanges is nullptr, or rangesNum is nullptr.  [AV_ERR_UNKNOWN](capi-native-averrors-h.md#oh_averrcode), unknown error.  [AV_ERR_NO_MEMORY](capi-native-averrors-h.md#oh_averrcode), internal use memory malloc failed. |

### OH_AVCapability_GetAudioChannelCountRange()

```c
OH_AVErrCode OH_AVCapability_GetAudioChannelCountRange(OH_AVCapability *capability, OH_AVRange *channelCountRange)
```

**Description**

Get the audio codec's supported audio channel count range.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Audio codec capability pointer. If a video codec capability pointer is given, undefined behavior occurs |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *channelCountRange | Output parameter. Audio channel count range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, or the channelCountRange is nullptr. |

### OH_AVCapability_GetVideoWidthAlignment()

```c
OH_AVErrCode OH_AVCapability_GetVideoWidthAlignment(OH_AVCapability *capability, int32_t *widthAlignment)
```

**Description**

Get the video codec's supported video width alignment.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| int32_t *widthAlignment | Output parameter. Video width alignment |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, or the widthAlignment is nullptr. |

### OH_AVCapability_GetVideoHeightAlignment()

```c
OH_AVErrCode OH_AVCapability_GetVideoHeightAlignment(OH_AVCapability *capability, int32_t *heightAlignment)
```

**Description**

Get the video codec's supported video height alignment.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| int32_t *heightAlignment | Output parameter. Video height alignment |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, or the heightAlignment is nullptr. |

### OH_AVCapability_GetVideoWidthRangeForHeight()

```c
OH_AVErrCode OH_AVCapability_GetVideoWidthRangeForHeight(OH_AVCapability *capability, int32_t height, OH_AVRange *widthRange)
```

**Description**

Get the video codec's supported video width range for a specific height.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| int32_t height | Vertical pixel number of the video |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *widthRange | Output parameter. Video width range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, the height is not within the supported range  obtained through [OH_AVCapability_GetVideoHeightRange](capi-native-avcapability-h.md#oh_avcapability_getvideoheightrange), or the widthRange is nullptr. |

### OH_AVCapability_GetVideoHeightRangeForWidth()

```c
OH_AVErrCode OH_AVCapability_GetVideoHeightRangeForWidth(OH_AVCapability *capability, int32_t width, OH_AVRange *heightRange)
```

**Description**

Get the video codec's supported video height range for a specific width.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| int32_t width | Horizontal pixel number of the video |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *heightRange | Output parameter. Video height range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, the width is not within the supported range  obtained through [OH_AVCapability_GetVideoWidthRange](capi-native-avcapability-h.md#oh_avcapability_getvideowidthrange), or the heightRange is nullptr. |

### OH_AVCapability_GetVideoWidthRange()

```c
OH_AVErrCode OH_AVCapability_GetVideoWidthRange(OH_AVCapability *capability, OH_AVRange *widthRange)
```

**Description**

Get the video codec's supported video width range.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *widthRange | Output parameter. Video width range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, or the widthRange is nullptr. |

### OH_AVCapability_GetVideoHeightRange()

```c
OH_AVErrCode OH_AVCapability_GetVideoHeightRange(OH_AVCapability *capability, OH_AVRange *heightRange)
```

**Description**

Get the video codec's supported video height range.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *heightRange | Output parameter. Video height range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, or the heightRange is nullptr. |

### OH_AVCapability_IsVideoSizeSupported()

```c
bool OH_AVCapability_IsVideoSizeSupported(OH_AVCapability *capability, int32_t width, int32_t height)
```

**Description**

Check if the video codec supports the specific video size.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| int32_t width | Horizontal pixel number of the video |
| int32_t height | Vertical pixel number of the video |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the video size is supported, false if the video size is not supported |

### OH_AVCapability_GetVideoFrameRateRange()

```c
OH_AVErrCode OH_AVCapability_GetVideoFrameRateRange(OH_AVCapability *capability, OH_AVRange *frameRateRange)
```

**Description**

Get the video codec's supported video frame rate range.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *frameRateRange | Output parameter. Video frame rate range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, or the frameRateRange is nullptr. |

### OH_AVCapability_GetVideoFrameRateRangeForSize()

```c
OH_AVErrCode OH_AVCapability_GetVideoFrameRateRangeForSize(OH_AVCapability *capability, int32_t width, int32_t height, OH_AVRange *frameRateRange)
```

**Description**

Get the Video codec's supported video frame rate range for a specified video size.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| int32_t width | Horizontal pixel number of the video |
| int32_t height | Vertical pixel number of the video |
| [OH_AVRange](capi-avcapability-oh-avrange.md) *frameRateRange | Output parameter. Frame rate range |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, the combination of width and height is  not supported, or the frameRateRange is nullptr. |

### OH_AVCapability_AreVideoSizeAndFrameRateSupported()

```c
bool OH_AVCapability_AreVideoSizeAndFrameRateSupported(OH_AVCapability *capability, int32_t width, int32_t height, int32_t frameRate)
```

**Description**

Check if the video codec supports the specific combination of video size and frame rate.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| int32_t width | Horizontal pixel number of the video |
| int32_t height | Vertical pixel number of the video |
| int32_t frameRate | Frame number per second |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the combination of video size and frame rate is supported,  false if it is not supported |

### OH_AVCapability_GetVideoSupportedPixelFormats()

```c
OH_AVErrCode OH_AVCapability_GetVideoSupportedPixelFormats(OH_AVCapability *capability, const int32_t **pixelFormats, uint32_t *pixelFormatNum)
```

**Description**

Get the video codec's supported video pixel format.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Video codec capability pointer. If an audio codec capability pointer is given, undefined behavior occurs |
| const int32_t **pixelFormats | Output parameter. A pointer to the video pixel format array |
| uint32_t *pixelFormatNum | Output parameter. The element number of the pixel format array |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, the pixelFormats is nullptr,  or the pixelFormatNum is nullptr.  [AV_ERR_UNKNOWN](capi-native-averrors-h.md#oh_averrcode), unknown error.  [AV_ERR_NO_MEMORY](capi-native-averrors-h.md#oh_averrcode), internal use memory malloc failed. |

### OH_AVCapability_GetVideoSupportedNativeBufferFormats()

```c
OH_AVErrCode OH_AVCapability_GetVideoSupportedNativeBufferFormats(OH_AVCapability *capability, const OH_NativeBuffer_Format **nativeBufferFormats, uint32_t *nativeBufferFormatNum)
```

**Description**

Get the native buffer formats supported by the video codec.<br> This function provides information about the native buffer formats that the video codec can handle.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | A pointer to a valid video codec capability instance. |
| const OH_NativeBuffer_Format **nativeBufferFormats | Output parameter. A pointer to the native buffer format array, refer to {@link OH_NativeBuffer_Format} |
| uint32_t *nativeBufferFormatNum | Output parameter. The element number of the native buffer format array |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, the capability is an audio codec capability pointer,  the nativeBufferFormats is nullptr, or the nativeBufferFormatNum is nullptr.  [AV_ERR_UNKNOWN](capi-native-averrors-h.md#oh_averrcode), unknown error.  [AV_ERR_NO_MEMORY](capi-native-averrors-h.md#oh_averrcode), internal use memory malloc failed. |

### OH_AVCapability_GetSupportedProfiles()

```c
OH_AVErrCode OH_AVCapability_GetSupportedProfiles(OH_AVCapability *capability, const int32_t **profiles, uint32_t *profileNum)
```

**Description**

Get the codec's supported profiles.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |
| const int32_t **profiles | Output parameter. A pointer to the profile array |
| uint32_t *profileNum | Output parameter. The element number of the profile array |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, the profiles is nullptr, or the profileNum is nullptr.  [AV_ERR_UNKNOWN](capi-native-averrors-h.md#oh_averrcode), unknown error.  [AV_ERR_NO_MEMORY](capi-native-averrors-h.md#oh_averrcode), internal use memory malloc failed. |

### OH_AVCapability_GetSupportedLevelsForProfile()

```c
OH_AVErrCode OH_AVCapability_GetSupportedLevelsForProfile(OH_AVCapability *capability, int32_t profile, const int32_t **levels, uint32_t *levelNum)
```

**Description**

Get codec's supported levels for a specific profile.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |
| int32_t profile | Codec profile |
| const int32_t **levels | Output parameter. A pointer to the level array |
| uint32_t *levelNum | Output parameter. The element number of the level array |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Returns AV_ERR_OK if the execution is successful,  otherwise returns a specific error code, refer to [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode)  [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode), the capability is invalid, the profile is not within the supported profile array  obtained through [OH_AVCapability_GetSupportedProfiles](capi-native-avcapability-h.md#oh_avcapability_getsupportedprofiles), the levels is nullptr, or the levelNum is nullptr.  [AV_ERR_UNKNOWN](capi-native-averrors-h.md#oh_averrcode), unknown error.  [AV_ERR_NO_MEMORY](capi-native-averrors-h.md#oh_averrcode), internal use memory malloc failed. |

### OH_AVCapability_AreProfileAndLevelSupported()

```c
bool OH_AVCapability_AreProfileAndLevelSupported(OH_AVCapability *capability, int32_t profile, int32_t level)
```

**Description**

Check if the codec supports the specific combination of the profile and level.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |
| int32_t profile | Codec profile |
| int32_t level | Codec level |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the combination of profile and level is supported,  false if it is not supported |

### OH_AVCapability_IsFeatureSupported()

```c
bool OH_AVCapability_IsFeatureSupported(OH_AVCapability *capability, OH_AVCapabilityFeature feature)
```

**Description**

Check if the codec supports the specified feature.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |
| [OH_AVCapabilityFeature](capi-native-avcapability-h.md#oh_avcapabilityfeature) feature | Feature enum, refer to [OH_AVCapabilityFeature](capi-native-avcapability-h.md#oh_avcapabilityfeature) for details |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the feature is supported, false if it is not supported |

### OH_AVCapability_GetFeatureProperties()

```c
OH_AVFormat *OH_AVCapability_GetFeatureProperties(OH_AVCapability *capability, OH_AVCapabilityFeature feature)
```

**Description**

Get the properties of the specified feature. It should be noted that the life cycle of the OH_AVFormat instance pointed to by the return value * needs to be manually released by the caller.

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCapability](capi-avcapability-oh-avcapability.md) *capability | Codec capability pointer |
| [OH_AVCapabilityFeature](capi-native-avcapability-h.md#oh_avcapabilityfeature) feature | Feature enum, refer to [OH_AVCapabilityFeature](capi-native-avcapability-h.md#oh_avcapabilityfeature) for details |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | Returns a pointer to an OH_AVFormat instance |


