# native_cencinfo.h

## Overview

The file declares the native APIs used to set decryption parameters.

**Library**: libnative_media_avcencinfo.so

**System capability**: SystemCapability.Multimedia.Media.Spliter

**Since**: 12

**Related module**: [Multimedia_Drm](capi-multimedia-drm.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [DrmSubsample](capi-multimedia-drm-drmsubsample.md) | DrmSubsample | The struct describes the subsample type. |
| [OH_AVBuffer](capi-multimedia-drm-oh-avbuffer.md) | OH_AVBuffer | The struct describes a native object for the media memory interface. |
| [OH_AVCencInfo](capi-multimedia-drm-oh-avcencinfo.md) | OH_AVCencInfo | The struct describes the audio/video Common Encryption Scheme (CENC) information. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [DrmCencAlgorithm](#drmcencalgorithm) | DrmCencAlgorithm | Enumerates the DRM CENC algorithm types. |
| [DrmCencInfoMode](#drmcencinfomode) | DrmCencInfoMode | Enumerates the modes for setting the key ID, IV, and subsample in the CENC information. |

### Macro

| Name | Description |
| -- | -- |
| DRM_KEY_ID_SIZE 16 | The length of the key ID is 16 bytes.<br>**Since**: 12 |
| DRM_KEY_IV_SIZE 16 | The length of the Initialization Vector (IV) is 16 bytes.<br>**Since**: 12 |
| DRM_KEY_MAX_SUB_SAMPLE_NUM 64 | The maximum number of subsamples is 64.<br>**Since**: 12 |

### Function

| Name | Description |
| -- | -- |
| [OH_AVCencInfo *OH_AVCencInfo_Create()](#oh_avcencinfo_create) | Creates an OH_AVCencInfo instance for setting the CENC information. |
| [OH_AVErrCode OH_AVCencInfo_Destroy(OH_AVCencInfo *cencInfo)](#oh_avcencinfo_destroy) | Destroys an OH_AVCencInfo instance and clears internal resources.<br> An instance can be destroyed only once. Do not use the instance until it is created again. You are advised to set the instance pointer to nullptr once the instance is destroyed. |
| [OH_AVErrCode OH_AVCencInfo_SetAlgorithm(OH_AVCencInfo *cencInfo, enum DrmCencAlgorithm algo)](#oh_avcencinfo_setalgorithm) | Sets an encryption algorithm of the CENC information. |
| [OH_AVErrCode OH_AVCencInfo_SetKeyIdAndIv(OH_AVCencInfo *cencInfo, uint8_t *keyId, uint32_t keyIdLen, uint8_t *iv, uint32_t ivLen)](#oh_avcencinfo_setkeyidandiv) | Sets the key ID and IV in the CENC information. |
| [OH_AVErrCode OH_AVCencInfo_SetSubsampleInfo(OH_AVCencInfo *cencInfo, uint32_t encryptedBlockCount, uint32_t skippedBlockCount, uint32_t firstEncryptedOffset, uint32_t subsampleCount, DrmSubsample *subsamples)](#oh_avcencinfo_setsubsampleinfo) | Sets the subsample information in the CENC information. |
| [OH_AVErrCode OH_AVCencInfo_SetMode(OH_AVCencInfo *cencInfo, enum DrmCencInfoMode mode)](#oh_avcencinfo_setmode) | Sets the CENC information mode. |
| [OH_AVErrCode OH_AVCencInfo_SetAVBuffer(OH_AVCencInfo *cencInfo, OH_AVBuffer *buffer)](#oh_avcencinfo_setavbuffer) | Sets the CENC information to an AVBuffer. |

## Enum type description

### DrmCencAlgorithm

```c
enum DrmCencAlgorithm
```

**Description**

Enumerates the DRM CENC algorithm types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| DRM_ALG_CENC_UNENCRYPTED = 0x0 | Unencrypted. |
| DRM_ALG_CENC_AES_CTR = 0x1 | Aes ctr. |
| DRM_ALG_CENC_AES_WV = 0x2 | Aes wv. |
| DRM_ALG_CENC_AES_CBC = 0x3 | Aes cbc. |
| DRM_ALG_CENC_SM4_CBC = 0x4 | Sm4 cbc. |
| DRM_ALG_CENC_SM4_CTR = 0x5 | Sm4 ctr. |

### DrmCencInfoMode

```c
enum DrmCencInfoMode
```

**Description**

Enumerates the modes for setting the key ID, IV, and subsample in the CENC information.

**Since**: 12

| Enum item | Description |
| -- | -- |
| DRM_CENC_INFO_KEY_IV_SUBSAMPLES_SET = 0x0 | key/iv/subsample set. |
| DRM_CENC_INFO_KEY_IV_SUBSAMPLES_NOT_SET = 0x1 | key/iv/subsample not set. |


## Function description

### OH_AVCencInfo_Create()

```c
OH_AVCencInfo *OH_AVCencInfo_Create()
```

**Description**

Creates an OH_AVCencInfo instance for setting the CENC information.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVCencInfo *](capi-multimedia-drm-oh-avcencinfo.md) | Pointer to the OH_AVCencInfo instance created. If the operation fails, nullptr is returned.      <br>The possible causes of an operation failure are as follows: The application address space is full,      or the data in the object fails to be initialized. |

### OH_AVCencInfo_Destroy()

```c
OH_AVErrCode OH_AVCencInfo_Destroy(OH_AVCencInfo *cencInfo)
```

**Description**

Destroys an OH_AVCencInfo instance and clears internal resources.<br> An instance can be destroyed only once. Do not use the instance until it is created again. You are advised to set the instance pointer to nullptr once the instance is destroyed.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCencInfo](capi-multimedia-drm-oh-avcencinfo.md) *cencInfo | Pointer to an OH_AVCencInfo instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The value of cencInfo is null. |

### OH_AVCencInfo_SetAlgorithm()

```c
OH_AVErrCode OH_AVCencInfo_SetAlgorithm(OH_AVCencInfo *cencInfo, enum DrmCencAlgorithm algo)
```

**Description**

Sets an encryption algorithm of the CENC information.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCencInfo](capi-multimedia-drm-oh-avcencinfo.md) *cencInfo | Pointer to an OH_AVCencInfo instance. |
| enum DrmCencAlgorithm algo | Encryption algorithm. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The value of cencInfo is null. |

### OH_AVCencInfo_SetKeyIdAndIv()

```c
OH_AVErrCode OH_AVCencInfo_SetKeyIdAndIv(OH_AVCencInfo *cencInfo, uint8_t *keyId, uint32_t keyIdLen, uint8_t *iv, uint32_t ivLen)
```

**Description**

Sets the key ID and IV in the CENC information.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCencInfo](capi-multimedia-drm-oh-avcencinfo.md) *cencInfo | Pointer to an OH_AVCencInfo instance. |
| uint8_t *keyId | Pointer to the key ID. |
| uint32_t keyIdLen | Length of the key ID. |
| uint8_t *iv | Pointer to the IV. |
| uint32_t ivLen | Length of the IV. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The value of cencInfo, keyId, or iv is null,      keyIdLen is not equal to DRM_KEY_ID_SIZE, ivLen is not equal to DRM_KEY_IV_SIZE,      the key ID or IV fails to be copied. |

### OH_AVCencInfo_SetSubsampleInfo()

```c
OH_AVErrCode OH_AVCencInfo_SetSubsampleInfo(OH_AVCencInfo *cencInfo, uint32_t encryptedBlockCount, uint32_t skippedBlockCount, uint32_t firstEncryptedOffset, uint32_t subsampleCount, DrmSubsample *subsamples)
```

**Description**

Sets the subsample information in the CENC information.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCencInfo](capi-multimedia-drm-oh-avcencinfo.md) *cencInfo | Pointer to an OH_AVCencInfo instance. |
| uint32_t encryptedBlockCount | Number of encrypted blocks. |
| uint32_t skippedBlockCount | Number of non-encrypted blocks. |
| uint32_t firstEncryptedOffset | Offset of the first encrypted payload. |
| uint32_t subsampleCount | Number of subsamples. |
| [DrmSubsample](capi-multimedia-drm-drmsubsample.md) *subsamples | Pointer to the subsamples. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The value of cencInfo is null, subsampleCount is greater than      DRM_KEY_MAX_SUB_SAMPLE_NUM, or subsamples is null. |

### OH_AVCencInfo_SetMode()

```c
OH_AVErrCode OH_AVCencInfo_SetMode(OH_AVCencInfo *cencInfo, enum DrmCencInfoMode mode)
```

**Description**

Sets the CENC information mode.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCencInfo](capi-multimedia-drm-oh-avcencinfo.md) *cencInfo | Pointer to an OH_AVCencInfo instance. |
| enum DrmCencInfoMode mode | CENC information mode, indicating whether the key ID, IV, and subsample are set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The value of cencInfo is null. |

### OH_AVCencInfo_SetAVBuffer()

```c
OH_AVErrCode OH_AVCencInfo_SetAVBuffer(OH_AVCencInfo *cencInfo, OH_AVBuffer *buffer)
```

**Description**

Sets the CENC information to an AVBuffer.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCencInfo](capi-multimedia-drm-oh-avcencinfo.md) *cencInfo | Pointer to an OH_AVCencInfo instance. |
| [OH_AVBuffer](capi-multimedia-drm-oh-avbuffer.md) *buffer | Pointer to the frame buffer that carries data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The value of cencInfo, buffer, buffer->buffer_,      or buffer->buffer_->meta_ is null. |


