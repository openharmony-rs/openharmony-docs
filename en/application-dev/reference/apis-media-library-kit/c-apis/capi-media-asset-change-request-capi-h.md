# media_asset_change_request_capi.h

## Overview

The file declares the APIs related to media asset change requests. You can use the APIs to change media assets.

**Library**: libmedia_asset_manager.so

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Related module**: [MediaAssetManager](capi-mediaassetmanager.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_MediaAssetChangeRequest* OH_MediaAssetChangeRequest_Create(OH_MediaAsset* mediaAsset)](#oh_mediaassetchangerequest_create) | Creates an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance. |
| [MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_AddResourceWithUri(OH_MediaAssetChangeRequest* changeRequest, MediaLibrary_ResourceType resourceType, char* fileUri)](#oh_mediaassetchangerequest_addresourcewithuri) | Adds a resource of the given URI. |
| [MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_AddResourceWithBuffer(OH_MediaAssetChangeRequest* changeRequest, MediaLibrary_ResourceType resourceType, uint8_t* buffer, uint32_t length)](#oh_mediaassetchangerequest_addresourcewithbuffer) | Adds a resource using ArrayBuffer data. |
| [MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_GetWriteCacheHandler(OH_MediaAssetChangeRequest* changeRequest, int32_t* fd)](#oh_mediaassetchangerequest_getwritecachehandler) | Obtains the handler used for writing a file to cache. |
| [MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_SaveCameraPhoto(OH_MediaAssetChangeRequest* changeRequest, MediaLibrary_ImageFileType imageFileType)](#oh_mediaassetchangerequest_savecameraphoto) | Saves the photo taken by the camera. |
| [MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_DiscardCameraPhoto(OH_MediaAssetChangeRequest* changeRequest)](#oh_mediaassetchangerequest_discardcameraphoto) | Discards the photo taken by the camera. |
| [MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_Release(OH_MediaAssetChangeRequest* changeRequest)](#oh_mediaassetchangerequest_release) | Releases an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance. |

## Function description

### OH_MediaAssetChangeRequest_Create()

```c
OH_MediaAssetChangeRequest* OH_MediaAssetChangeRequest_Create(OH_MediaAsset* mediaAsset)
```

**Description**

Creates an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAsset* mediaAsset | Pointer to an [OH_MediaAsset](capi-mediaassetmanager-oh-mediaasset.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MediaAssetChangeRequest* | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error. |

### OH_MediaAssetChangeRequest_AddResourceWithUri()

```c
MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_AddResourceWithUri(OH_MediaAssetChangeRequest* changeRequest, MediaLibrary_ResourceType resourceType, char* fileUri)
```

**Description**

Adds a resource of the given URI.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetChangeRequest* changeRequest | Pointer to an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance. |
| MediaLibrary_ResourceType resourceType | Type of the resource to add, which is specified by [MediaLibrary_ResourceType](capi-media-asset-base-capi-h.md#medialibrary_resourcetype). |
| char* fileUri | Pointer to the URI of the file. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_NO_SUCH_FILE if file does not exist.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error.      <br>MEDIA_LIBRARY_OPERATION_NOT_SUPPORTED if operation is not supported. |

### OH_MediaAssetChangeRequest_AddResourceWithBuffer()

```c
MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_AddResourceWithBuffer(OH_MediaAssetChangeRequest* changeRequest, MediaLibrary_ResourceType resourceType, uint8_t* buffer, uint32_t length)
```

**Description**

Adds a resource using ArrayBuffer data.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetChangeRequest* changeRequest | Pointer to an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance. |
| MediaLibrary_ResourceType resourceType | Type of the resource to add. |
| uint8_t* buffer | Pointer to the data buffer. |
| uint32_t length | Length of the data buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error.      <br>MEDIA_LIBRARY_OPERATION_NOT_SUPPORTED if operation is not supported. |

### OH_MediaAssetChangeRequest_GetWriteCacheHandler()

```c
MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_GetWriteCacheHandler(OH_MediaAssetChangeRequest* changeRequest, int32_t* fd)
```

**Description**

Obtains the handler used for writing a file to cache.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permission**: ohos.permission.WRITE_IMAGEVIDEO

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetChangeRequest* changeRequest | Pointer to an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance. |
| int32_t* fd | Pointer to the file descriptor (FD) obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error.      <br>MEDIA_LIBRARY_PERMISSION_DENIED if permission is denied.      <br>MEDIA_LIBRARY_OPERATION_NOT_SUPPORTED if operation is not supported. |

### OH_MediaAssetChangeRequest_SaveCameraPhoto()

```c
MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_SaveCameraPhoto(OH_MediaAssetChangeRequest* changeRequest, MediaLibrary_ImageFileType imageFileType)
```

**Description**

Saves the photo taken by the camera.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetChangeRequest* changeRequest | Pointer to an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance. |
| MediaLibrary_ImageFileType imageFileType | Type of the image file of the photo. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error.      <br>MEDIA_LIBRARY_OPERATION_NOT_SUPPORTED if operation is not supported. |

### OH_MediaAssetChangeRequest_DiscardCameraPhoto()

```c
MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_DiscardCameraPhoto(OH_MediaAssetChangeRequest* changeRequest)
```

**Description**

Discards the photo taken by the camera.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetChangeRequest* changeRequest | Pointer to an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error.      <br>MEDIA_LIBRARY_OPERATION_NOT_SUPPORTED if operation is not supported. |

### OH_MediaAssetChangeRequest_Release()

```c
MediaLibrary_ErrorCode OH_MediaAssetChangeRequest_Release(OH_MediaAssetChangeRequest* changeRequest)
```

**Description**

Releases an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetChangeRequest* changeRequest | Pointer to an [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed. |


