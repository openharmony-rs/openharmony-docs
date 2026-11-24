# native_avcodec_videobase.h

## Overview

Declare the Native API used for basic video encoding and decoding functions, as well as video-specific configurations and parameters.

**Library**: libnative_media_codecbase.so

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 26.0.0

**Related module**: [CodecBase](capi-avcodec-kit-codecbase.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_VideoMetadataRoiSemanticLabel](#oh_videometadataroisemanticlabel) | OH_VideoMetadataRoiSemanticLabel | The semantic labels for Region of Interest (ROI) in video encoding. |

### Functions

| Name | Description |
| -- | -- |
| [OH_AVErrCode OH_VideoMetadata_AppendRoiString(char **roiStrInOut, OH_AVFormat *format)](#oh_videometadata_appendroistring) | Formats the region of interest (ROI) configuration from an OH_AVFormat handle into a string and appends it to the target string.<br> This function extracts ROI properties (such as coordinates, delta quantization parameter, and semantic label) from the provided format handle, constructs the standard ROI string representation, and seamlessly appends it to the string pointed to by roiStrInOut. If *roiStrInOut is NULL, a new string is allocated; if not NULL, the existing string is reallocated to append the new configuration. |
| [OH_AVErrCode OH_VideoMetadata_GetRoiCount(const char *roiStr, uint32_t *outCount)](#oh_videometadata_getroicount) | Pre-parse the ROI string to retrieve the number of valid ROI regions it contains.<br> This API is not affected by specific backend capacity limits and identifies the number of ROI regions that meet the rule requirements in the ROI string based on the syntax rules. |
| [OH_AVErrCode OH_VideoMetadata_ParseRoiString(const char *roiStr, OH_AVFormat **outOwnedFormats, uint32_t maxCapacity, uint32_t *outCount)](#oh_videometadata_parseroistring) | Parses the ROI string and populates the caller-provided OH_AVFormat array. |

### Variables

| Name | Description |
| -- | -- |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_TOP | Key for describing the top-coordinate (y) of a single ROI rectangle, value type is int32_t.<br> The origin of the coordinate system is the top-left corner of the video. The value range is [0, [OH_MD_KEY_VIDEO_METADATA_ROI_BOTTOM](capi-native-avcodec-videobase-h.md#variables)). This is a mandatory key used when configuring ROI parameters.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.Multimedia.Media.CodecBase<br><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_TOP--><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_TOP-End--> |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_LEFT | Key for describing the left-coordinate (x) of a single ROI rectangle, value type is int32_t.<br> The origin of the coordinate system is the top-left corner of the video. The value range is [0, [OH_MD_KEY_VIDEO_METADATA_ROI_RIGHT](capi-native-avcodec-videobase-h.md#variables)). This is a mandatory key used when configuring ROI parameters.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.Multimedia.Media.CodecBase<br><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_LEFT--><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_LEFT-End--> |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_BOTTOM | Key for describing the bottom-coordinate (y) of a single ROI rectangle, value type is int32_t.<br> The origin of the coordinate system is the top-left corner of the video. The value range is ([OH_MD_KEY_VIDEO_METADATA_ROI_TOP](capi-native-avcodec-videobase-h.md#variables), OH_MD_KEY_VIDEO_HEIGHT]. This is a mandatory key used when configuring ROI parameters.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.Multimedia.Media.CodecBase<br><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_BOTTOM--><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_BOTTOM-End--> |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_RIGHT | Key for describing the right-coordinate (x) of a single ROI rectangle, value type is int32_t.<br> The origin of the coordinate system is the top-left corner of the video. The value range is ([OH_MD_KEY_VIDEO_METADATA_ROI_LEFT](capi-native-avcodec-videobase-h.md#variables), OH_MD_KEY_VIDEO_WIDTH]. This is a mandatory key used when configuring ROI parameters.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.Multimedia.Media.CodecBase<br><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_RIGHT--><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_RIGHT-End--> |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_DELTA_QP | Pointer to the key that describes the relative quantization parameter (QP) offset value of a single ROI. The value type is int32_t. The value range is [-51, 51]. This key is optional for ROI configuration. If this key is not set, the encoder will use its default quantization parameter strategy for this region.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.Multimedia.Media.CodecBase<br><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_DELTA_QP--><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_DELTA_QP-End--> |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_SEM_LABEL | Key for describing the semantic label of a single ROI, value type is int32_t.<br> The value must correspond to [OH_VideoMetadataRoiSemanticLabel](capi-native-avcodec-videobase-h.md#oh_videometadataroisemanticlabel). This is an optional key used when configuring ROI parameters. If this key is not set, the region is treated with the default semantic processing strategy.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.Multimedia.Media.CodecBase<br><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_SEM_LABEL--><!--Device-const char *OH_MD_KEY_VIDEO_METADATA_ROI_SEM_LABEL-End--> |
| const char *OH_MD_KEY_VIDEO_ENCODER_WITH_LOWPOWER_CAMERA | Key that defines the enabling of joint capture and encoding low-power optimization.<br> This key is the configuration switch for joint capture and encoding low-power optimization.<br> Use [OH_AVFormat_SetIntValue](capi-native-avformat-h.md#oh_avformat_setintvalue) to set the enabling status: **1** indicates that joint capture and encoding low-power optimization is enabled, and **0** (default) indicates that this capability is disabled.<br> Usage constraints: This key is valid only for the video encoder and is an optional parameter. You can configure it during initialization through [OH_VideoEncoder_Configure](capi-native-avcodec-videoencoder-h.md#oh_videoencoder_configure), or enable it at runtime through [OH_VideoEncoder_SetParameter](capi-native-avcodec-videoencoder-h.md#oh_videoencoder_setparameter). Once enabled, the capture side adjusts the capture configuration policy based on the encoding information to reduce overall power consumption.<br>**Since**: 26.0.1<br>**System capability**: SystemCapability.Multimedia.Media.CodecBase<br><!--Device-const char *OH_MD_KEY_VIDEO_ENCODER_WITH_LOWPOWER_CAMERA--><!--Device-const char *OH_MD_KEY_VIDEO_ENCODER_WITH_LOWPOWER_CAMERA-End--> |

## Enum type description

### OH_VideoMetadataRoiSemanticLabel

```c
enum OH_VideoMetadataRoiSemanticLabel
```

**Description**

The semantic labels for Region of Interest (ROI) in video encoding.

<!--Device-enum OH_VideoMetadataRoiSemanticLabel--><!--Device-enum OH_VideoMetadataRoiSemanticLabel-End-->

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_VIDEO_METADATA_ROI_SEM_LABEL_OTHER = 0 | Indicates an unspecified or unknown region.<br>**Since**: 26.0.0<br><!--Device-OH_VIDEO_METADATA_ROI_SEM_LABEL_OTHER = 0--><!--Device-OH_VIDEO_METADATA_ROI_SEM_LABEL_OTHER = 0-End--> |
| OH_VIDEO_METADATA_ROI_SEM_LABEL_FACE = 1 | Indicates that the ROI contains a human face.<br>**Since**: 26.0.0<br><!--Device-OH_VIDEO_METADATA_ROI_SEM_LABEL_FACE = 1--><!--Device-OH_VIDEO_METADATA_ROI_SEM_LABEL_FACE = 1-End--> |


## Function description

### OH_VideoMetadata_AppendRoiString()

```c
OH_AVErrCode OH_VideoMetadata_AppendRoiString(char **roiStrInOut, OH_AVFormat *format)
```

**Description**

Formats the region of interest (ROI) configuration from an OH_AVFormat handle into a string and appends it to the target string.<br> This function extracts ROI properties (such as coordinates, delta quantization parameter, and semantic label) from the provided format handle, constructs the standard ROI string representation, and seamlessly appends it to the string pointed to by roiStrInOut. If *roiStrInOut is NULL, a new string is allocated; if not NULL, the existing string is reallocated to append the new configuration.

> **Note**:
>
> The caller takes ownership of the memory allocated for *roiStrInOut. The memory is allocated using the standard C library allocator (malloc/realloc). The caller must free the string using the matching standard C library deallocator (free) when it is no longer needed, and set the pointer to NULL to prevent double-free.

<!--Device-OH_AVErrCode OH_VideoMetadata_AppendRoiString(char **roiStrInOut, OH_AVFormat *format)--><!--Device-OH_AVErrCode OH_VideoMetadata_AppendRoiString(char **roiStrInOut, OH_AVFormat *format)-End-->

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 26.0.0

**Resource release**: free {roiStrInOut}

**Parameters**:

| Parameter | Description |
| -- | -- |
| char **roiStrInOut | A double pointer to the target string. The pointer itself must not be NULL. If *roiStrInOut is NULL, a new string is allocated. |
| [OH_AVFormat](capi-core-oh-avformat.md) *format | The OH_AVFormat handle containing the ROI parameters to be appended, must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | Result code. <br>Returns [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode) if the string is successfully formatted and appended. <br>Returns [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode) if the roiStrInOut pointer or format handle is NULL, or if the format lacks required ROI keys. <br>Returns [AV_ERR_NO_MEMORY](capi-native-averrors-h.md#oh_averrcode) if internal memory allocation or reallocation fails. |

### OH_VideoMetadata_GetRoiCount()

```c
OH_AVErrCode OH_VideoMetadata_GetRoiCount(const char *roiStr, uint32_t *outCount)
```

**Description**

Pre-parse the ROI string to retrieve the number of valid ROI regions it contains.<br> This API is not affected by specific backend capacity limits and identifies the number of ROI regions that meet the rule requirements in the ROI string based on the syntax rules.

<!--Device-OH_AVErrCode OH_VideoMetadata_GetRoiCount(const char *roiStr, uint32_t *outCount)--><!--Device-OH_AVErrCode OH_VideoMetadata_GetRoiCount(const char *roiStr, uint32_t *outCount)-End-->

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *roiStr | Input ROI configuration string. |
| uint32_t *outCount | Returns the number of valid ROI regions parsed from the string. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode): The operation is successful. <br>[AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode): roiStr or outCount is NULL. |

### OH_VideoMetadata_ParseRoiString()

```c
OH_AVErrCode OH_VideoMetadata_ParseRoiString(const char *roiStr, OH_AVFormat **outOwnedFormats, uint32_t maxCapacity, uint32_t *outCount)
```

**Description**

Parses the ROI string and populates the caller-provided OH_AVFormat array.

> **Note**:
>
> The caller takes ownership of every successfully created OH_AVFormat handle. Upon return, the valid handles are stored in the first *outCount elements of the outOwnedFormats array. - On full or partial success (*outCount > 0), the caller must individually destroy each valid handle using [OH_AVFormat_Destroy](capi-native-avformat-h.md#oh_avformat_destroy) to prevent memory leaks. - On total failure (*outCount == 0), no handles are created and no destruction is needed.

<!--Device-OH_AVErrCode OH_VideoMetadata_ParseRoiString(const char *roiStr, OH_AVFormat **outOwnedFormats, uint32_t maxCapacity, uint32_t *outCount)--><!--Device-OH_AVErrCode OH_VideoMetadata_ParseRoiString(const char *roiStr, OH_AVFormat **outOwnedFormats, uint32_t maxCapacity, uint32_t *outCount)-End-->

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 26.0.0

**Resource release**: [OH_AVFormat_Destroy](capi-native-avformat-h.md#oh_avformat_destroy)

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *roiStr | The input ROI configuration string. |
| [OH_AVFormat](capi-core-oh-avformat.md) **outOwnedFormats | [OUT] A pointer array allocated by the caller to receive the parsed OH_AVFormat handles. The caller owns each non-NULL handle in this array. |
| uint32_t maxCapacity | [IN] Indicates the maximum physical capacity of the outOwnedFormats array to prevent out-of-bounds writes. |
| uint32_t *outCount | [OUT] Returns the actual number of ROIs successfully parsed and populated into the array. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | Result code. <br>Returns [AV_ERR_OK](capi-native-averrors-h.md#oh_averrcode) if the operation is successful. <br>Returns [AV_ERR_INVALID_VAL](capi-native-averrors-h.md#oh_averrcode) if roiStr, outOwnedFormats, or outCount is NULL. |


