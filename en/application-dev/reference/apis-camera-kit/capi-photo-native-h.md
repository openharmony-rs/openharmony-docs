# photo_native.h
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=cfbdf7078f905314893a0975124c4a78ff4672a0 translatedAt=2026-11-18T03:42:08.586Z pushedAt=2026-11-20T08:17:21.304Z nl=1 -->

## Overview

The file declares the camera photo concepts.

**File to include**: <ohcamera/photo_native.h>

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md) | OH_PhotoNative | Describes the photo object, which is a full-quality image object.|

### Functions

| Name| Description|
| -- | -- |
| [Camera_ErrorCode OH_PhotoNative_GetMainImage(OH_PhotoNative* photo, OH_ImageNative** mainImage)](#oh_photonative_getmainimage) | Obtains a full-quality image.|
| [Camera_ErrorCode OH_PhotoNative_GetUncompressedImage(OH_PhotoNative* photo, OH_PictureNative** picture)](#oh_photonative_getuncompressedimage) | Obtains an uncompressed image.|
| [Camera_ErrorCode OH_PhotoNative_GetAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_ImageNative** outImage)](#oh_photonative_getauxiliaryimage) | Obtains an auxiliary image of the specified type. |
| [Camera_ErrorCode OH_PhotoNative_GetUncompressedAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_PictureNative** outImage)](#oh_photonative_getuncompressedauxiliaryimage) | Obtains an uncompressed auxiliary image of the specified type. |
| [Camera_ErrorCode OH_PhotoNative_Release(OH_PhotoNative* photo)](#oh_photonative_release) | Releases a full-quality image.|
| [Camera_ErrorCode OH_PhotoNative_ReleasePicture(OH_PictureNative* picture)](#oh_photonative_releasepicture) | Releases an OH_PictureNative instance. |
| [Camera_ErrorCode OH_PhotoNative_ReleaseImage(OH_ImageNative* image)](#oh_photonative_releaseimage) | Releases an OH_ImageNative instance. |

## Function Description

### OH_PhotoNative_GetMainImage()

```c
Camera_ErrorCode OH_PhotoNative_GetMainImage(OH_PhotoNative* photo, OH_ImageNative** mainImage)
```

**Description**

Obtains a full-quality image.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to an **OH_PhotoNative** instance.|
| [OH_ImageNative](../apis-image-kit/capi-image-nativemodule-oh-imagenative.md)** mainImage | Double pointer to the full-quality image, which is an **OH_ImageNative** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful.<br>         **CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect.|

### OH_PhotoNative_GetUncompressedImage()

```c
Camera_ErrorCode OH_PhotoNative_GetUncompressedImage(OH_PhotoNative* photo, OH_PictureNative** picture)
```

**Description**

Obtains an uncompressed image.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to an **OH_PhotoNative** instance.|
| [OH_PictureNative](../apis-image-kit/capi-image-nativemodule-oh-picturenative.md)** picture | Double pointer to the uncompressed image, which is an **OH_PictureNative** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful.<br>         **CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect.|

### OH_PhotoNative_Release()

```c
Camera_ErrorCode OH_PhotoNative_Release(OH_PhotoNative* photo)
```

**Description**

Releases a full-quality image.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to the **OH_PhotoNative** instance to release.|

**Returns**

| Type| Description|
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful.<br>         **CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect.|

### OH_PhotoNative_GetAuxiliaryImage()

```c
Camera_ErrorCode OH_PhotoNative_GetAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_ImageNative** outImage)
```

**Description**

Obtains an auxiliary image of the specified type.

Use scenarios: Before using this API, you need to call [OH_PhotoOutput_SetAutoAuxiliaryPhotosDeliveryEnabled()](capi-photo-output-h.md#oh_photooutput_setautoauxiliaryphotosdeliveryenabled) to enable automatic callback of auxiliary images of the specified type. Only then does the OH_PhotoNative object obtained by taking a photo contain auxiliary images, which can be obtained by type through this API for subsequent analysis and processing. For the supported auxiliary image types and their purposes, see [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype).

**Since:** 26.0.1

**Resource release:** [OH_PhotoNative_ReleaseImage()](#oh_photonative_releaseimage)

**Parameters**

| Name | Description |
| -- | -- |
| const [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to the **OH_PhotoNative** instance. |
| [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype) type | Type of the auxiliary picture. |
| [OH_ImageNative](../apis-image-kit/capi-image-nativemodule-oh-imagenative.md)** outImage | Double pointer to the **OH_ImageNative** instance, used to receive the obtained auxiliary image. When the call succeeds, it points to a valid auxiliary image instance; when the call fails, this parameter returns NULL. The instance is managed by the caller. After use, you should call **OH_PhotoNative_ReleaseImage()** to release it. |

**Return**

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | Result code.<br>         **CAMERA_OK**: The operation is successful.<br>         **CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect.<br>         **CAMERA_ERROR_PARAM_OUT_OF_RANGE**: The parameter is out of range. |

### OH_PhotoNative_GetUncompressedAuxiliaryImage()

```c
Camera_ErrorCode OH_PhotoNative_GetUncompressedAuxiliaryImage(const OH_PhotoNative* photo,
    OH_Camera_AuxiliaryPhotoType type, OH_PictureNative** outImage)
```

**Description**

Obtains an uncompressed auxiliary image of the specified type.

Use case: Before using this API, you need to call [OH_PhotoOutput_SetAutoAuxiliaryPhotosDeliveryEnabled()](capi-photo-output-h.md#oh_photooutput_setautoauxiliaryphotosdeliveryenabled) to enable automatic callback of auxiliary images of the specified type. The **OH_PhotoNative** object obtained by taking a photo contains auxiliary images only when this feature is enabled. Then, obtain the uncompressed auxiliary image by type through this API for subsequent analysis and processing. For the supported auxiliary image types and their purposes, see [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype).

**Since:** 26.0.1

**Resource release:** [OH_PhotoNative_ReleasePicture()](#oh_photonative_releasepicture)

**Parameters:**

| Name | Description |
| -- | -- |
| const [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to the OH_PhotoNative instance. |
| [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype) type | Type of the auxiliary picture. |
| [OH_PictureNative](../apis-image-kit/capi-image-nativemodule-oh-picturenative.md)** outImage | Double pointer to the **OH_PictureNative** instance, used to receive the obtained uncompressed auxiliary image. When the call succeeds, it points to a valid auxiliary image instance; when the call fails, this parameter returns NULL. The instance is managed by the caller. After use, you should call **OH_PhotoNative_ReleasePicture()** to release it. |

**Returns:**

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful.<br>         **CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect.<br>         **CAMERA_ERROR_PARAM_OUT_OF_RANGE**: The parameter is out of range. |

### OH_PhotoNative_ReleasePicture()

```c
Camera_ErrorCode OH_PhotoNative_ReleasePicture(OH_PictureNative* picture)
```

**Description**

Releases an OH_PictureNative instance.

**Since:** 26.0.1

**Parameters:**

| Name | Description |
| -- | -- |
| [OH_PictureNative](../apis-image-kit/capi-image-nativemodule-oh-picturenative.md)* picture | Pointer to the **OH_PictureNative** instance. |

**Returns:**

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful.<br>         **CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoNative_ReleaseImage()

```c
Camera_ErrorCode OH_PhotoNative_ReleaseImage(OH_ImageNative* image)
```

**Description**

Releases the **OH_ImageNative** instance.

**Since:** 26.0.1

**Parameters**

| Name | Description |
| -- | -- |
| [OH_ImageNative](../apis-image-kit/capi-image-nativemodule-oh-imagenative.md)* image | Pointer to the **OH_ImageNative** instance to be released. |

**Return**

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful.<br>         **CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect. |


