# native_avcodec_videobase.h

## Overview

Declare the Native API used for basic video encoding and decoding functions, as well as video-specific configurations and parameters.

**Library**: libnative_media_codecbase.so

**System capability**: SystemCapability.Multimedia.Media.CodecBase

**Since**: 9

**Related module**: [CodecBase](capi-codecbase.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_VideoMetadataRoiSemanticLabel](#oh_videometadataroisemanticlabel) | OH_VideoMetadataRoiSemanticLabel | The semantic labels for Region of Interest (ROI) in video encoding. |

### Function

| Name | Description |
| -- | -- |
| [OH_AVErrCode OH_VideoMetadata_AppendRoiString(char **roiStrInOut, OH_AVFormat *format)](#oh_videometadata_appendroistring) | Formats the region of interest (ROI) configuration from an OH_AVFormat handle into a string and appends it to the target string.<br> This function extracts ROI properties (such as coordinates, delta quantization parameter, and semantic label) from the provided format handle, constructs the standard ROI string representation, and seamlessly appends it to the string pointed to by roiStrInOut. If *roiStrInOut is NULL, a new string is allocated; if not NULL, the existing string is reallocated to append the new configuration. |
| [OH_AVErrCode OH_VideoMetadata_GetRoiCount(const char *roiStr, uint32_t *outCount)](#oh_videometadata_getroicount) | Pre-parses the ROI string to obtain the number of valid ROI regions contained within it.<br> This interface is decoupled from specific backend capacity limits and accurately returns the number of valid regions identified in the string based on syntax rules. |
| [OH_AVErrCode OH_VideoMetadata_ParseRoiString(const char *roiStr, OH_AVFormat **outOwnedFormats, uint32_t maxCapacity, uint32_t *outCount)](#oh_videometadata_parseroistring) | Parses the ROI string and populates the caller-provided OH_AVFormat array. |

### Variable

| Name | Description |
| -- | -- |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_TOP | Key for describing the top-coordinate (y) of a single ROI rectangle, value type is int32_t.<br> The origin of the coordinate system is the top-left corner of the video. The value range is [0, {@link OH_MD_KEY_VIDEO_METADATA_ROI_BOTTOM}). This is a mandatory key used when configuring ROI parameters.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_LEFT | Key for describing the left-coordinate (x) of a single ROI rectangle, value type is int32_t.<br> The origin of the coordinate system is the top-left corner of the video. The value range is [0, {@link OH_MD_KEY_VIDEO_METADATA_ROI_RIGHT}). This is a mandatory key used when configuring ROI parameters.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_BOTTOM | Key for describing the bottom-coordinate (y) of a single ROI rectangle, value type is int32_t.<br> The origin of the coordinate system is the top-left corner of the video. The value range is ({@link OH_MD_KEY_VIDEO_METADATA_ROI_TOP}, {@link OH_MD_KEY_VIDEO_HEIGHT}]. This is a mandatory key used when configuring ROI parameters.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_RIGHT | Key for describing the right-coordinate (x) of a single ROI rectangle, value type is int32_t.<br> The origin of the coordinate system is the top-left corner of the video. The value range is ({@link OH_MD_KEY_VIDEO_METADATA_ROI_LEFT}, {@link OH_MD_KEY_VIDEO_WIDTH}]. This is a mandatory key used when configuring ROI parameters.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_DELTA_QP | Key for describing the quantization parameter offset of a single ROI, value type is int32_t.<br> The value range is [-51, 51]. This is an optional key used when configuring ROI parameters. If this key is not set, the encoder uses its default quantization parameter strategy for this region.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_METADATA_ROI_SEM_LABEL | Key for describing the semantic label of a single ROI, value type is int32_t.<br> The value must correspond to [OH_VideoMetadataRoiSemanticLabel](capi-native-avcodec-videobase-h.md#oh_videometadataroisemanticlabel). This is an optional key used when configuring ROI parameters. If this key is not set, the region is treated with the default semantic processing strategy.<br>**Since**: 26.0.0 |
| const char *OH_MD_KEY_VIDEO_ENCODER_WITH_LOWPOWER_CAMERA | Key that describes whether to enable joint capture and editing low-power optimization. This key is the configuration toggle for joint capture and encoding low-power optimization. Use {@link OH_AVFormat_SetIntValue} to set the enabling status:<br>-**1**: Enables joint capture and encoding low-power optimization.<br>-**0** (default value): Disables this capability.<br>Usage restrictions:<br>This key is valid only for the video encoder.<br>This key is optional. This key can be configured in the encoder,<br>initialized via {@link OH_AVCodec_Configure}, or<br>enabled at runtime via {@link OH_AVCodec_SetParameter}. After this capability is enabled, the capture side adjusts its configuration strategy based on encoding information to reduce overall power consumption.<br>**Since**: 26.1.0 |

## Enum type description

### OH_VideoMetadataRoiSemanticLabel

```c
enum OH_VideoMetadataRoiSemanticLabel
```

**Description**

The semantic labels for Region of Interest (ROI) in video encoding.

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_VIDEO_METADATA_ROI_SEM_LABEL_OTHER = 0 | Indicates an unspecified or unknown region.<br>**Since**: 26.0.0 |
| OH_VIDEO_METADATA_ROI_SEM_LABEL_FACE = 1 | Indicates that the ROI contains a human face.<br>**Since**: 26.0.0 |


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

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| char **roiStrInOut | A double pointer to the target string. The pointer itself must not be NULL. If *roiStrInOut is NULL, a new string is allocated. |
| OH_AVFormat *format | The OH_AVFormat handle containing the ROI parameters to be appended, must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Result code.      <br>Returns {@link AV_ERR_OK} if the string is successfully formatted and appended.<br>    <br>Returns {@link AV_ERR_INVALID_VAL} if the roiStrInOut pointer or format handle is NULL,<br>    or if the format lacks required ROI keys.<br>    <br>Returns {@link AV_ERR_NO_MEMORY} if internal memory allocation or reallocation fails. |

### OH_VideoMetadata_GetRoiCount()

```c
OH_AVErrCode OH_VideoMetadata_GetRoiCount(const char *roiStr, uint32_t *outCount)
```

**Description**

Pre-parses the ROI string to obtain the number of valid ROI regions contained within it.<br> This interface is decoupled from specific backend capacity limits and accurately returns the number of valid regions identified in the string based on syntax rules.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *roiStr | The input ROI configuration string. |
| uint32_t *outCount | [OUT] Returns the number of valid ROI regions parsed from the string. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Result code.      <br>Returns {@link AV_ERR_OK} if the operation is successful.<br>    <br>Returns {@link AV_ERR_INVALID_VAL} if the roiStr or outCount pointer is NULL. |

### OH_VideoMetadata_ParseRoiString()

```c
OH_AVErrCode OH_VideoMetadata_ParseRoiString(const char *roiStr, OH_AVFormat **outOwnedFormats, uint32_t maxCapacity, uint32_t *outCount)
```

**Description**

Parses the ROI string and populates the caller-provided OH_AVFormat array.

> **Note**:
>
> The caller takes ownership of every successfully created OH_AVFormat handle. Upon return, the valid handles are stored in the first *outCount elements of the outOwnedFormats array. - On full or partial success (*outCount > 0), the caller must individually destroy each valid handle using {@link OH_AVFormat_Destroy} to prevent memory leaks. - On total failure (*outCount == 0), no handles are created and no destruction is needed.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *roiStr | The input ROI configuration string. |
| OH_AVFormat **outOwnedFormats | [OUT] A pointer array allocated by the caller to receive the parsed OH_AVFormat handles. The caller owns each non-NULL handle in this array. |
| uint32_t maxCapacity | [IN] Indicates the maximum physical capacity of the outOwnedFormats array to prevent out-of-bounds writes. |
| uint32_t *outCount | [OUT] Returns the actual number of ROIs successfully parsed and populated into the array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Result code.      <br>Returns {@link AV_ERR_OK} if the operation is successful.<br>    <br>Returns {@link AV_ERR_INVALID_VAL} if roiStr, outOwnedFormats, or outCount is NULL. |


