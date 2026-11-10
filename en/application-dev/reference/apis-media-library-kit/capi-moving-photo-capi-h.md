# moving_photo_capi.h

<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6a96f2b8f99f158608ec5045488b853b4cc6044f translatedAt=2026-11-03T07:18:13.114Z pushedAt=2026-11-04T03:11:19.988Z nl=1 -->

## Overview

The file declares the APIs related to moving photos. You can use the APIs to obtain moving photo information.

**Library**: libmedia_asset_manager.so

**File to include**: <multimedia/media_library/moving_photo_capi.h>

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 13

**Related module**: [MediaAssetManager](capi-mediaassetmanager.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [MediaLibrary_ErrorCode OH_MovingPhoto_GetUri(OH_MovingPhoto* movingPhoto, const char** uri)](#oh_movingphoto_geturi) | Obtains the URI of a moving photo.|
| [MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithUris(OH_MovingPhoto* movingPhoto, char* imageUri, char* videoUri)](#oh_movingphoto_requestcontentwithuris) | Requests both the image content and the video content of a moving photo, and writes them to the URIs specified by the parameters.    |
| [MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithUri(OH_MovingPhoto* movingPhoto, MediaLibrary_ResourceType resourceType, char* uri)](#oh_movingphoto_requestcontentwithuri) | Requests the moving photo content of the specified resource type and writes it to the specified URI.|
| [MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithBuffer(OH_MovingPhoto* movingPhoto, MediaLibrary_ResourceType resourceType, const uint8_t** buffer, uint32_t* size)](#oh_movingphoto_requestcontentwithbuffer) | Requests the moving photo content of the specified resource type and returns it in ArrayBuffer format.|
| [MediaLibrary_ErrorCode OH_MovingPhoto_Release(OH_MovingPhoto* movingPhoto)](#oh_movingphoto_release) | Releases the [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md) instance.       |

## Function Description

### OH_MovingPhoto_GetUri()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_GetUri(OH_MovingPhoto* movingPhoto, const char** uri)
```

**Description**

Obtains the URI of a moving photo.

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md)* movingPhoto | Pointer to an [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md) instance.|
| const char** uri | Pointer to the URI that identifies the moving photo object. |

**Return value**

| Type| Description|
| -- | -- |
| [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode) | **MEDIA_LIBRARY_OK**: operation success.<br>      **MEDIA_LIBRARY_PARAMETER_ERROR**: incorrect parameters. Possible causes:<br>                                      1. A mandatory parameter is not specified.<br>                                      2. A parameter type is incorrect.<br>                                      3. Parameter verification fails.<br>      **MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR**: internal system error.|

### OH_MovingPhoto_RequestContentWithUris()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithUris(OH_MovingPhoto* movingPhoto, char* imageUri,char* videoUri)
```

**Description**

Requests both the image content and video content of a moving photo and writes them to the URIs specified by the parameters.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md)* movingPhoto | Pointer to an [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md) instance.|
| char* imageUri | Pointer to the target file URI for saving the image data. |
| char* videoUri | Pointer to the target file URI for saving the video data. |

**Return value**

| Type| Description|
| -- | -- |
| [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode) | **MEDIA_LIBRARY_OK**: operation success.<br>      **MEDIA_LIBRARY_PARAMETER_ERROR**: incorrect parameters. Possible causes:<br>                                      1. A mandatory parameter is not specified.<br>                                      2. A parameter type is incorrect.<br>                                      3. Parameter verification fails.<br>      **MEDIA_LIBRARY_PERMISSION_DENIED**: no access permission.<br>      **MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR**: internal system error.|

### OH_MovingPhoto_RequestContentWithUri()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithUri(OH_MovingPhoto* movingPhoto,MediaLibrary_ResourceType resourceType, char* uri)
```

**Description**

Requests the moving photo content of the specified resource type and writes the content to the specified URI.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md)* movingPhoto | Pointer to an [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md) instance.|
| [MediaLibrary_ResourceType](capi-media-asset-base-capi-h.md#medialibrary_resourcetype) resourceType | Resource type, which is specified by [MediaLibrary_ResourceType](capi-media-asset-base-capi-h.md#medialibrary_resourcetype).|
| char* uri | Pointer to the URI of the file, to which the data is written.|

**Return value**

| Type| Description|
| -- | -- |
| [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode) | **MEDIA_LIBRARY_OK**: operation success.<br>      **MEDIA_LIBRARY_PARAMETER_ERROR**: incorrect parameters. Possible causes:<br>                                      1. A mandatory parameter is not specified.<br>                                      2. A parameter type is incorrect.<br>                                      3. Parameter verification fails.<br>      **MEDIA_LIBRARY_PERMISSION_DENIED**: no access permission.<br>      **MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR**: internal system error.|

### OH_MovingPhoto_RequestContentWithBuffer()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_RequestContentWithBuffer(OH_MovingPhoto* movingPhoto,MediaLibrary_ResourceType resourceType, const uint8_t** buffer, uint32_t* size)
```

**Description**

Requests the moving photo content of the specified resource type and returns it in ArrayBuffer format.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md)* movingPhoto | Pointer to an [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md) instance.|
| [MediaLibrary_ResourceType](capi-media-asset-base-capi-h.md#medialibrary_resourcetype) resourceType | Resource type, which is specified by [MediaLibrary_ResourceType](capi-media-asset-base-capi-h.md#medialibrary_resourcetype).|
| const uint8_t** buffer | Pointer to the buffer that stores the target file data, used to receive the requested resource content data. |
| uint32_t* size | Output parameter, which returns the size of the buffer data, in bytes. |

**Return value**

| Type| Description|
| -- | -- |
| [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode) | **MEDIA_LIBRARY_OK**: operation success.<br>      **MEDIA_LIBRARY_PARAMETER_ERROR**: incorrect parameters. Possible causes:<br>                                      1. A mandatory parameter is not specified.<br>                                      2. A parameter type is incorrect.<br>                                      3. Parameter verification fails.<br>      **MEDIA_LIBRARY_PERMISSION_DENIED**: no access permission.<br>      **MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR**: internal system error.|

### OH_MovingPhoto_Release()

```c
MediaLibrary_ErrorCode OH_MovingPhoto_Release(OH_MovingPhoto* movingPhoto)
```

**Description**

Releases the [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md) instance.

**Since**: 13


**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md)* movingPhoto | Pointer to an [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md) instance.|

**Return value**

| Type| Description|
| -- | -- |
| [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode) | **MEDIA_LIBRARY_OK**: operation success.<br>      **MEDIA_LIBRARY_PARAMETER_ERROR**: incorrect parameters. Possible causes:<br>                                      1. A mandatory parameter is not specified.<br>                                      2. A parameter type is incorrect.<br>                                      3. Parameter verification fails.|


