# media_asset_base_capi.h

## Overview

The file declares the structs and enums for the media asset manager.

**Library**: libmedia_asset_manager.so

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Since**: 12

**Related module**: [MediaAssetManager](capi-mediaassetmanager.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [MediaLibrary_RequestId](capi-mediaassetmanager-medialibrary-requestid.md) | MediaLibrary_RequestId | Defines a struct for the request ID. |
| [MediaLibrary_RequestOptions](capi-mediaassetmanager-medialibrary-requestoptions.md) | MediaLibrary_RequestOptions | The struct defines how media assets are requested and processed. |
| [OH_MediaAssetManager](capi-mediaassetmanager-oh-mediaassetmanager.md) | OH_MediaAssetManager | The struct describes the media asset manager. |
| [OH_MediaAssetChangeRequest](capi-mediaassetmanager-oh-mediaassetchangerequest.md) | OH_MediaAssetChangeRequest | The struct describes a media asset change request. |
| [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md) | OH_MovingPhoto | The struct describes a moving photo. |
| [OH_MediaAsset](capi-mediaassetmanager-oh-mediaasset.md) | OH_MediaAsset | The struct describes a media asset. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [MediaLibrary_ErrorCode](#medialibrary_errorcode) | MediaLibrary_ErrorCode | Enumerates the error codes of the media library. |
| [MediaLibrary_DeliveryMode](#medialibrary_deliverymode) | MediaLibrary_DeliveryMode | Enumerates the delivery modes of the requested media asset. |
| [MediaLibrary_MediaType](#medialibrary_mediatype) | MediaLibrary_MediaType | Enumerates the media asset types. |
| [MediaLibrary_MediaSubType](#medialibrary_mediasubtype) | MediaLibrary_MediaSubType | Enumerates the media asset subtypes. |
| [MediaLibrary_ResourceType](#medialibrary_resourcetype) | MediaLibrary_ResourceType | Enumerates the media library resource types. |
| [MediaLibrary_ImageFileType](#medialibrary_imagefiletype) | MediaLibrary_ImageFileType | Enumerates the image file types. |
| [MediaLibrary_MediaQuality](#medialibrary_mediaquality) | MediaLibrary_MediaQuality | Enumerates the media resource quality, |
| [MediaLibrary_MediaContentType](#medialibrary_mediacontenttype) | MediaLibrary_MediaContentType | Enumerates the media content types. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_MediaLibrary_OnDataPrepared)(int32_t result, MediaLibrary_RequestId requestId)](#oh_medialibrary_ondataprepared) | OH_MediaLibrary_OnDataPrepared | Called when the requested media asset is ready. |
| [typedef void (\*OH_MediaLibrary_OnImageDataPrepared)(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_ImageSourceNative* imageSourceNative)](#oh_medialibrary_onimagedataprepared) | OH_MediaLibrary_OnImageDataPrepared | Called when the requested image is ready. |
| [typedef void (\*OH_MediaLibrary_OnMovingPhotoDataPrepared)(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_MovingPhoto* movingPhoto)](#oh_medialibrary_onmovingphotodataprepared) | OH_MediaLibrary_OnMovingPhotoDataPrepared | Called when the requested moving photo is ready. |
| [typedef void (\*OH_MediaLibrary_OnQuickImageDataPrepared)(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_ImageSourceNative* imageSourceNative, OH_PictureNative* pictureNative)](#oh_medialibrary_onquickimagedataprepared) | OH_MediaLibrary_OnQuickImageDataPrepared | This callback is called when the requested image source is ready. If an image buffer exists in the system, an image object is returned, reducing the encoding time. |

### Variable

| Name | Description |
| -- | -- |
| static const int32_t UUID_STR_MAX_LENGTH = 37 | Maximum length of a request ID.<br>**Since**: 12 |
| void (*OH_MediaLibrary_OnDataPrepared)(int32_t result, MediaLibrary_RequestId requestId) | Called when the requested media asset is ready.<br>**Since**: 12 |
| void (*OH_MediaLibrary_OnImageDataPrepared)(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_ImageSourceNative* imageSourceNative) | Called when the requested image is ready.<br>**Since**: 12 |
| void (*OH_MediaLibrary_OnMovingPhotoDataPrepared)(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_MovingPhoto* movingPhoto) | Called when the requested moving photo is ready.<br>**Since**: 13 |
| void (*OH_MediaLibrary_OnQuickImageDataPrepared)(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_ImageSourceNative* imageSourceNative, OH_PictureNative* pictureNative) | This callback is called when the requested image source is ready. If an image buffer exists in the system, an image object is returned, reducing the encoding time.<br>**Since**: 23 |

## Enum type description

### MediaLibrary_ErrorCode

```c
enum MediaLibrary_ErrorCode
```

**Description**

Enumerates the error codes of the media library.

**Since**: 12

| Enum item | Description |
| -- | -- |
| MEDIA_LIBRARY_OK = 0 | Operation success. |
| MEDIA_LIBRARY_PERMISSION_DENIED = 201 | No access permission. |
| MEDIA_LIBRARY_PARAMETER_ERROR = 401 | A mandatory parameter is not specified, the parameter type is incorrect, or parameter verification failed. |
| MEDIA_LIBRARY_NO_SUCH_FILE = 23800101 | The file does not exist. |
| MEDIA_LIBRARY_INVALID_DISPLAY_NAME = 23800102 | Invalid display name. |
| MEDIA_LIBRARY_INVALID_ASSET_URI = 23800103 | Invalid asset URI. |
| MEDIA_LIBRARY_INVALID_PHOTO_KEY = 23800104 | Invalid PhotoKey. |
| MEDIA_LIBRARY_OPERATION_NOT_SUPPORTED = 23800201 | Unsupported operation. |
| MEDIA_LIBRARY_INTERNAL_SYSTEM_ERROR = 23800301 | Internal system error. Retry the operation and check logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

### MediaLibrary_DeliveryMode

```c
enum MediaLibrary_DeliveryMode
```

**Description**

Enumerates the delivery modes of the requested media asset.

**Since**: 12

| Enum item | Description |
| -- | -- |
| MEDIA_LIBRARY_FAST_MODE = 0 | delivery fast mode |
| MEDIA_LIBRARY_HIGH_QUALITY_MODE = 1 | delivery high quality mode |
| MEDIA_LIBRARY_BALANCED_MODE = 2 | delivery balanced mode |

### MediaLibrary_MediaType

```c
enum MediaLibrary_MediaType
```

**Description**

Enumerates the media asset types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| MEDIA_LIBRARY_IMAGE = 1 | image asset |
| MEDIA_LIBRARY_VIDEO = 2 | video asset |

### MediaLibrary_MediaSubType

```c
enum MediaLibrary_MediaSubType
```

**Description**

Enumerates the media asset subtypes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| MEDIA_LIBRARY_DEFAULT = 0 | default Photo Type |
| MEDIA_LIBRARY_MOVING_PHOTO = 3 | moving Photo Type |
| MEDIA_LIBRARY_BURST = 4 | burst Photo Type |

### MediaLibrary_ResourceType

```c
enum MediaLibrary_ResourceType
```

**Description**

Enumerates the media library resource types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| MEDIA_LIBRARY_IMAGE_RESOURCE = 1 | image resource |
| MEDIA_LIBRARY_VIDEO_RESOURCE = 2 | video resource |

### MediaLibrary_ImageFileType

```c
enum MediaLibrary_ImageFileType
```

**Description**

Enumerates the image file types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| MEDIA_LIBRARY_IMAGE_JPEG = 1 | JPEG type |
| MEDIA_LIBRARY_IMAGE_HEIF = 2 | HEIF.<br>**Since**: 23 |
| MEDIA_LIBRARY_FILE_VIDEO = 3 | MPEG.<br>**Since**: 19 |

### MediaLibrary_MediaQuality

```c
enum MediaLibrary_MediaQuality
```

**Description**

Enumerates the media resource quality,

**Since**: 12

| Enum item | Description |
| -- | -- |
| MEDIA_LIBRARY_QUALITY_FAST = 1 | fast quality |
| MEDIA_LIBRARY_QUALITY_FULL = 2 | full quality |

### MediaLibrary_MediaContentType

```c
enum MediaLibrary_MediaContentType
```

**Description**

Enumerates the media content types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| MEDIA_LIBRARY_COMPRESSED = 1 | compressed media content type |
| MEDIA_LIBRARY_PICTURE_OBJECT = 2 | picture object media content type |


## Function description

### OH_MediaLibrary_OnDataPrepared()

```c
typedef void (*OH_MediaLibrary_OnDataPrepared)(int32_t result, MediaLibrary_RequestId requestId)
```

**Description**

Called when the requested media asset is ready.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t result | Request processing result. |
| [MediaLibrary_RequestId](capi-mediaassetmanager-medialibrary-requestid.md) requestId | Request ID. |

### OH_MediaLibrary_OnImageDataPrepared()

```c
typedef void (*OH_MediaLibrary_OnImageDataPrepared)(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_ImageSourceNative* imageSourceNative)
```

**Description**

Called when the requested image is ready.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode) result | Request processing result, which is specified by [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode). |
| [MediaLibrary_RequestId](capi-mediaassetmanager-medialibrary-requestid.md) requestId | Request ID, which is specified by [MediaLibrary_RequestId](capi-mediaassetmanager-medialibrary-requestid.md). |
| [MediaLibrary_MediaQuality](capi-media-asset-base-capi-h.md#medialibrary_mediaquality) mediaQuality | Quality of the requested source, which is specified by [MediaLibrary_MediaQuality](capi-media-asset-base-capi-h.md#medialibrary_mediaquality). |
| [MediaLibrary_MediaContentType](capi-media-asset-base-capi-h.md#medialibrary_mediacontenttype) type | Media content type of the requested source, which is specified by [MediaLibrary_MediaContentType](capi-media-asset-base-capi-h.md#medialibrary_mediacontenttype). |
| OH_ImageSourceNative\* imageSourceNative | Pointer to the {@link OH_ImageSourceNative} instance obtained when the requested image is ready. |

### OH_MediaLibrary_OnMovingPhotoDataPrepared()

```c
typedef void (*OH_MediaLibrary_OnMovingPhotoDataPrepared)(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_MovingPhoto* movingPhoto)
```

**Description**

Called when the requested moving photo is ready.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode) result | Request processing result, which is specified by [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode). |
| [MediaLibrary_RequestId](capi-mediaassetmanager-medialibrary-requestid.md) requestId | Request ID, which is specified by [MediaLibrary_RequestId](capi-mediaassetmanager-medialibrary-requestid.md). |
| [MediaLibrary_MediaQuality](capi-media-asset-base-capi-h.md#medialibrary_mediaquality) mediaQuality | Quality of the requested resource, which is specified by [MediaLibrary_MediaQuality](capi-media-asset-base-capi-h.md#medialibrary_mediaquality). |
| [MediaLibrary_MediaContentType](capi-media-asset-base-capi-h.md#medialibrary_mediacontenttype) type | Media content type of the requested resource, which is specified by [MediaLibrary_MediaContentType](capi-media-asset-base-capi-h.md#medialibrary_mediacontenttype). |
| [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md)\* movingPhoto | Pointer to the [OH_MovingPhoto](capi-mediaassetmanager-oh-movingphoto.md) instance obtained when the requested moving photo is ready. |

### OH_MediaLibrary_OnQuickImageDataPrepared()

```c
typedef void (*OH_MediaLibrary_OnQuickImageDataPrepared)(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_ImageSourceNative* imageSourceNative, OH_PictureNative* pictureNative)
```

**Description**

This callback is called when the requested image source is ready. If an image buffer exists in the system, an image object is returned, reducing the encoding time.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [MediaLibrary_ErrorCode](capi-media-asset-base-capi-h.md#medialibrary_errorcode) result | Result of processing the requested resource. |
| [MediaLibrary_RequestId](capi-mediaassetmanager-medialibrary-requestid.md) requestId | **MediaLibrary_RequestId** of the requested resource. |
| [MediaLibrary_MediaQuality](capi-media-asset-base-capi-h.md#medialibrary_mediaquality) mediaQuality | **MediaLibrary_MediaQuality** of the requested resource. |
| [MediaLibrary_MediaContentType](capi-media-asset-base-capi-h.md#medialibrary_mediacontenttype) type | **MediaLibrary_MediaContentType** of the requested resource. |
| OH_ImageSourceNative\* imageSourceNative | Used to obtain the **OH_ImageSourceNative** information when preparing the image file. Otherwise, **imageSourceNative** is null. |
| OH_PictureNative\* pictureNative | Used to obtain the **OH_PictureNative** information when preparing the image source. Otherwise, **pictureNative** is null. |


