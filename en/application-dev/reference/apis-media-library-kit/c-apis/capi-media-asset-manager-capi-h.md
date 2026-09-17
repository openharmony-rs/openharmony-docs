# media_asset_manager_capi.h

## Overview

The file declares the APIs of the media asset manager. You can use the functions to request media assets in the media library.

**Library**: libmedia_asset_manager.so

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Related module**: [MediaAssetManager](capi-mediaassetmanager.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_MediaAssetManager* OH_MediaAssetManager_Create(void)](#oh_mediaassetmanager_create) | Creates an **OH_MediaAssetManager** instance. |
| [MediaLibrary_RequestId OH_MediaAssetManager_RequestImageForPath(OH_MediaAssetManager* manager, const char* uri, MediaLibrary_RequestOptions requestOptions, const char* destPath, OH_MediaLibrary_OnDataPrepared callback)](#oh_mediaassetmanager_requestimageforpath) | Requests an image in the specified directory. |
| [MediaLibrary_RequestId OH_MediaAssetManager_RequestVideoForPath(OH_MediaAssetManager* manager, const char* uri, MediaLibrary_RequestOptions requestOptions, const char* destPath, OH_MediaLibrary_OnDataPrepared callback)](#oh_mediaassetmanager_requestvideoforpath) | Requests a video in the specified directory. |
| [bool OH_MediaAssetManager_CancelRequest(OH_MediaAssetManager* manager, const MediaLibrary_RequestId requestId)](#oh_mediaassetmanager_cancelrequest) | Cancels a request based on the request ID. |
| [MediaLibrary_ErrorCode OH_MediaAssetManager_RequestMovingPhoto(OH_MediaAssetManager* manager, OH_MediaAsset* mediaAsset, MediaLibrary_RequestOptions requestOptions, MediaLibrary_RequestId* requestId, OH_MediaLibrary_OnMovingPhotoDataPrepared callback)](#oh_mediaassetmanager_requestmovingphoto) | Requests a moving photo based on different policies. |
| [MediaLibrary_ErrorCode OH_MediaAssetManager_RequestImage(OH_MediaAssetManager* manager, OH_MediaAsset* mediaAsset, MediaLibrary_RequestOptions requestOptions, MediaLibrary_RequestId* requestId, OH_MediaLibrary_OnImageDataPrepared callback)](#oh_mediaassetmanager_requestimage) | Requests an image based on different policies. |
| [MediaLibrary_ErrorCode OH_MediaAssetManager_Release(OH_MediaAssetManager* manager)](#oh_mediaassetmanager_release) | Releases an {@link OH_MediaAssetManager} instance. |
| [MediaLibrary_ErrorCode OH_MediaAssetManager_QuickRequestImage(OH_MediaAssetManager* manager, OH_MediaAsset* mediaAsset, MediaLibrary_RequestOptions requestOptions, MediaLibrary_RequestId* requestId, OH_MediaLibrary_OnQuickImageDataPrepared callback)](#oh_mediaassetmanager_quickrequestimage) | Requests an image based on different policies. |

## Function description

### OH_MediaAssetManager_Create()

```c
OH_MediaAssetManager* OH_MediaAssetManager_Create(void)
```

**Description**

Creates an **OH_MediaAssetManager** instance.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| OH_MediaAssetManager* | Returns a pointer to an OH_MediaAssetManager instance. |

### OH_MediaAssetManager_RequestImageForPath()

```c
MediaLibrary_RequestId OH_MediaAssetManager_RequestImageForPath(OH_MediaAssetManager* manager, const char* uri, MediaLibrary_RequestOptions requestOptions, const char* destPath, OH_MediaLibrary_OnDataPrepared callback)
```

**Description**

Requests an image in the specified directory.

**Required permission**: ohos.permission.READ_IMAGEVIDEO

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetManager* manager | Pointer to an **OH_MediaAssetManager** instance. |
| const char* uri | Pointer to the URI of the requested image. |
| MediaLibrary_RequestOptions requestOptions | Options related to the media asset quality and delivery mode. |
| const char* destPath | Pointer to the destination directory of the requested image. |
| OH_MediaLibrary_OnDataPrepared callback | Callback to be invoked when the requested image is ready. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_RequestId | Return Request id. |

### OH_MediaAssetManager_RequestVideoForPath()

```c
MediaLibrary_RequestId OH_MediaAssetManager_RequestVideoForPath(OH_MediaAssetManager* manager, const char* uri, MediaLibrary_RequestOptions requestOptions, const char* destPath, OH_MediaLibrary_OnDataPrepared callback)
```

**Description**

Requests a video in the specified directory.

**Required permission**: ohos.permission.READ_IMAGEVIDEO

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetManager* manager | Pointer to an **OH_MediaAssetManager** instance. |
| const char* uri | Pointer to the URI of the requested video. |
| MediaLibrary_RequestOptions requestOptions | Options related to the media asset quality and delivery mode. |
| const char* destPath | Pointer to the destination directory of the requested video. |
| OH_MediaLibrary_OnDataPrepared callback | Callback to be invoked when the requested video is ready. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_RequestId | Return Request id. |

### OH_MediaAssetManager_CancelRequest()

```c
bool OH_MediaAssetManager_CancelRequest(OH_MediaAssetManager* manager, const MediaLibrary_RequestId requestId)
```

**Description**

Cancels a request based on the request ID.

**Required permission**: ohos.permission.READ_IMAGEVIDEO

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetManager* manager | Pointer to an **OH_MediaAssetManager** instance. |
| const MediaLibrary_RequestId requestId | ID of the request to cancel. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the request is canceled successfully; returns false otherwise. |

### OH_MediaAssetManager_RequestMovingPhoto()

```c
MediaLibrary_ErrorCode OH_MediaAssetManager_RequestMovingPhoto(OH_MediaAssetManager* manager, OH_MediaAsset* mediaAsset, MediaLibrary_RequestOptions requestOptions, MediaLibrary_RequestId* requestId, OH_MediaLibrary_OnMovingPhotoDataPrepared callback)
```

**Description**

Requests a moving photo based on different policies.

**Required permission**: ohos.permission.READ_IMAGEVIDEO

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetManager* manager | Pointer to an {@link OH_MediaAssetManager} instance. |
| OH_MediaAsset* mediaAsset | Pointer to the {@link OH_MediaAsset} instance to be requested. |
| MediaLibrary_RequestOptions requestOptions | Options related to the media asset quality and delivery mode. The options are specified by {@link MediaLibrary_RequestOptions}. |
| MediaLibrary_RequestId* requestId | Pointer to the request ID, which is specified by {@link MediaLibrary_RequestId}. |
| OH_MediaLibrary_OnMovingPhotoDataPrepared callback | Callback to be invoked when the requested moving photo is ready. The callback is specified by {@link OH_MediaLibrary_OnMovingPhotoDataPrepared}. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_OPERATION_NOT_SUPPORTED if operation is not supported.      <br>MEDIA_LIBRARY_PERMISSION_DENIED if permission is denied.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error. |

### OH_MediaAssetManager_RequestImage()

```c
MediaLibrary_ErrorCode OH_MediaAssetManager_RequestImage(OH_MediaAssetManager* manager, OH_MediaAsset* mediaAsset, MediaLibrary_RequestOptions requestOptions, MediaLibrary_RequestId* requestId, OH_MediaLibrary_OnImageDataPrepared callback)
```

**Description**

Requests an image based on different policies.

**Required permission**: ohos.permission.READ_IMAGEVIDEO

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetManager* manager | Pointer to an {@link OH_MediaAssetManager} instance. |
| OH_MediaAsset* mediaAsset | Pointer to the {@link OH_MediaAsset} instance to be requested. |
| MediaLibrary_RequestOptions requestOptions | Options related to the media asset quality and delivery mode. The options are specified by {@link MediaLibrary_RequestOptions}. |
| MediaLibrary_RequestId* requestId | Pointer to the request ID, which is specified by {@link MediaLibrary_RequestId}. |
| OH_MediaLibrary_OnImageDataPrepared callback | Callback to be invoked when the requested image is ready. The callback is specified by {@link OH_MediaLibrary_OnImageDataPrepared}. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed.      <br>MEDIA_LIBRARY_OPERATION_NOT_SUPPORTED if operation is not supported.      <br>MEDIA_LIBRARY_PERMISSION_DENIED if permission is denied.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error. |

### OH_MediaAssetManager_Release()

```c
MediaLibrary_ErrorCode OH_MediaAssetManager_Release(OH_MediaAssetManager* manager)
```

**Description**

Releases an {@link OH_MediaAssetManager} instance.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetManager* manager | Pointer to an {@link OH_MediaAssetManager} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_PARAMETER_ERROR Parameter error. Possible causes:      <br>1. Mandatory parameters are left unspecified.      <br>2. Incorrect parameter types.      <br>3. Parameter verification failed. |

### OH_MediaAssetManager_QuickRequestImage()

```c
MediaLibrary_ErrorCode OH_MediaAssetManager_QuickRequestImage(OH_MediaAssetManager* manager, OH_MediaAsset* mediaAsset, MediaLibrary_RequestOptions requestOptions, MediaLibrary_RequestId* requestId, OH_MediaLibrary_OnQuickImageDataPrepared callback)
```

**Description**

Requests an image based on different policies.

**Required permission**: ohos.permission.READ_IMAGEVIDEO

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MediaAssetManager* manager | Pointer to an **OH_MediaAssetManager** instance. |
| OH_MediaAsset* mediaAsset | Pointer to the **OH_MediaAsset** instance to be requested. |
| MediaLibrary_RequestOptions requestOptions | **MediaLibrary_RequestOptions** used for the image request policy mode. |
| MediaLibrary_RequestId* requestId | Pointer to the **MediaLibrary_RequestId** instance of the request. This parameter is an output parameter. |
| OH_MediaLibrary_OnQuickImageDataPrepared callback | The **OH_MediaLibrary_OnQuickImageDataPrepared** method called when the requested source data is ready. |

**Returns**:

| Type | Description |
| -- | -- |
| MediaLibrary_ErrorCode | MEDIA_LIBRARY_OK if the method call succeeds.      <br>MEDIA_LIBRARY_OPERATION_NOT_SUPPORTED if operation is not supported.      <br>MEDIA_LIBRARY_PERMISSION_DENIED if permission is denied.      <br>MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR if internal system error. |


