# moving_photo_capi.h

## Overview

The file declares the APIs related to moving photos. You can use the APIs to obtain moving photo information.

**Library**: libmedia_asset_manager.so

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Related module**: [MediaAssetManager](capi-mediaassetmanager.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [MediaLibrary_ErrorCode OH_MovingPhoto_GetUri(OH_MovingPhoto* movingPhoto, const char** uri)](#oh_movingphoto_geturi) | Obtains the URI of a moving photo. |
| [MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithUris(OH_MovingPhoto* movingPhoto, char* imageUri, char* videoUri)](#oh_movingphoto_requestcontentwithuris) | Requests the image data and video data of a moving photo and writes them to the specified URIs, respectively. |
| [MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithUri(OH_MovingPhoto* movingPhoto, MediaLibrary_ResourceType resourceType, char* uri)](#oh_movingphoto_requestcontentwithuri) | Requests the moving photo content of the specified resource type and writes it to the specified URI. |
| [MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithBuffer(OH_MovingPhoto* movingPhoto, MediaLibrary_ResourceType resourceType, const uint8_t** buffer, uint32_t* size)](#oh_movingphoto_requestcontentwithbuffer) | Requests the moving photo content of the specified resource type and returns it in ArrayBuffer format. |
| [MediaLibrary_ErrorCode OH_MovingPhoto_Release(OH_MovingPhoto* movingPhoto)](#oh_movingphoto_release) | Releases an {@link OH_MovingPhoto} instance. |

## Function description

### OH_MovingPhoto_GetUri()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_GetUri(OH_MovingPhoto* movingPhoto, const char** uri)
```

**Description**

Obtains the URI of a moving photo.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MovingPhoto* movingPhoto | Pointer to an {@link OH_MovingPhoto} instance. |
| const char** uri | Double pointer to the URI of the moving photo obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error. |

### OH_MovingPhoto_RequestContentWithUris()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithUris(OH_MovingPhoto* movingPhoto, char* imageUri, char* videoUri)
```

**Description**

Requests the image data and video data of a moving photo and writes them to the specified URIs, respectively.

**Required permission**: ohos.permission.READ_IMAGEVIDEO

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MovingPhoto* movingPhoto | Pointer to an {@link OH_MovingPhoto} instance. |
| char* imageUri | Pointer to the URI of the file, to which the image data is written. |
| char* videoUri | Pointer to the URI of the file, to which the video data is written. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_PERMISSION_DENIED if permission is denied.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error. |

### OH_MovingPhoto_RequestContentWithUri()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithUri(OH_MovingPhoto* movingPhoto, MediaLibrary_ResourceType resourceType, char* uri)
```

**Description**

Requests the moving photo content of the specified resource type and writes it to the specified URI.

**Required permission**: ohos.permission.READ_IMAGEVIDEO

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MovingPhoto* movingPhoto | Pointer to an {@link OH_MovingPhoto} instance. |
| MediaLibrary_ResourceType resourceType | Resource type, which is specified by {@link MediaLibrary_ResourceType}. |
| char* uri | Pointer to the URI of the file, to which the data is written. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_PERMISSION_DENIED if permission is denied.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error. |

### OH_MovingPhoto_RequestContentWithBuffer()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithBuffer(OH_MovingPhoto* movingPhoto, MediaLibrary_ResourceType resourceType, const uint8_t** buffer, uint32_t* size)
```

**Description**

Requests the moving photo content of the specified resource type and returns it in ArrayBuffer format.

**Required permission**: ohos.permission.READ_IMAGEVIDEO

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MovingPhoto* movingPhoto | Pointer to an {@link OH_MovingPhoto} instance. |
| MediaLibrary_ResourceType resourceType | Resource type, which is specified by {@link MediaLibrary_ResourceType}. |
| const uint8_t** buffer | Double pointer to the buffer for storing the target file data. |
| uint32_t* size | Pointer to the buffer size. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_PERMISSION_DENIED if permission is denied.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error. |

### OH_MovingPhoto_Release()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_Release(OH_MovingPhoto* movingPhoto)
```

**Description**

Releases an {@link OH_MovingPhoto} instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MovingPhoto* movingPhoto | Pointer to an {@link OH_MovingPhoto} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed. |


