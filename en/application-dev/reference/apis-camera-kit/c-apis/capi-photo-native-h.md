# photo_native.h

## Overview

The file declares the camera photo concepts.

**Library**: libohcamera.so

**Since**: 12

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md) | OH_PhotoNative | The struct describes the photo object, which is a full-quality image object. |

### Function

| Name | Description |
| -- | -- |
| [Camera_ErrorCode OH_PhotoNative_GetMainImage(OH_PhotoNative* photo, OH_ImageNative** mainImage)](#oh_photonative_getmainimage) | Obtains a full-quality image. |
| [Camera_ErrorCode OH_PhotoNative_GetUncompressedImage(OH_PhotoNative* photo, OH_PictureNative** picture)](#oh_photonative_getuncompressedimage) | Obtains an uncompressed image. |
| [Camera_ErrorCode OH_PhotoNative_GetAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_ImageNative** outImage)](#oh_photonative_getauxiliaryimage) | Obtains an auxiliary image. |
| [Camera_ErrorCode OH_PhotoNative_GetUncompressedAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_PictureNative** outImage)](#oh_photonative_getuncompressedauxiliaryimage) | Obtains an uncompressed auxiliary image. |
| [Camera_ErrorCode OH_PhotoNative_Release(OH_PhotoNative* photo)](#oh_photonative_release) | Releases a full-quality image. |
| [Camera_ErrorCode OH_PhotoNative_ReleasePicture(OH_PictureNative* picture)](#oh_photonative_releasepicture) | Releases an allocated native picture instance. |
| [Camera_ErrorCode OH_PhotoNative_ReleaseImage(OH_ImageNative* image)](#oh_photonative_releaseimage) | Releases an allocated native image instance. |

## Function description

### OH_PhotoNative_GetMainImage()

```c
Camera_ErrorCode OH_PhotoNative_GetMainImage(OH_PhotoNative* photo, OH_ImageNative** mainImage)
```

**Description**

Obtains a full-quality image.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to an **OH_PhotoNative** instance. |
| [OH_ImageNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-imagenative.md)** mainImage | Double pointer to the full-quality image, which is an **OH_ImageNative** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful. <br>**CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoNative_GetUncompressedImage()

```c
Camera_ErrorCode OH_PhotoNative_GetUncompressedImage(OH_PhotoNative* photo, OH_PictureNative** picture)
```

**Description**

Obtains an uncompressed image.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to an **OH_PhotoNative** instance. |
| [OH_PictureNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-picturenative.md)** picture | Double pointer to the uncompressed image, which is an **OH_PictureNative** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful. <br>**CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoNative_GetAuxiliaryImage()

```c
Camera_ErrorCode OH_PhotoNative_GetAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_ImageNative** outImage)
```

**Description**

Obtains an auxiliary image.

**Since**: 26.0.1

**Resource release**: OH_PhotoNative_ReleaseImage {outImage}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | [in] Pointer to an **OH_PhotoNative** instance. |
| [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype) type | [in] The auxiliary photo type. |
| [OH_ImageNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-imagenative.md)** outImage | [out] Double pointer to the auxiliary image, which is an **OH_ImageNative** instance. On success, points to a valid image instance. On failure, may be set to NULLThe caller is responsible for releasing the allocated memory using the appropriate release function. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | <ul> <li>**CAMERA_OK**: The operation is successful.</li> <li>**CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect.</li> <li>**CAMERA_ERROR_PARAM_OUT_OF_RANGE**: A parameter is out of the range.</li> </ul> |

### OH_PhotoNative_GetUncompressedAuxiliaryImage()

```c
Camera_ErrorCode OH_PhotoNative_GetUncompressedAuxiliaryImage(const OH_PhotoNative* photo, OH_Camera_AuxiliaryPhotoType type, OH_PictureNative** outImage)
```

**Description**

Obtains an uncompressed auxiliary image.

**Since**: 26.0.1

**Resource release**: OH_PhotoNative_ReleasePicture {outImage}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | [in] Pointer to an **OH_PhotoNative** instance. |
| [OH_Camera_AuxiliaryPhotoType](capi-camera-h.md#oh_camera_auxiliaryphototype) type | [in] The auxiliary photo type. |
| [OH_PictureNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-picturenative.md)** outImage | [out] Double pointer to the uncompressed auxiliary image, which is an **OH_PictureNative** instance. On success, points to a valid image instance. On failure, may be set to NULL. The caller is responsible for releasing the allocated memory using the appropriate release function. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | <ul> <li>**CAMERA_OK**: The operation is successful.</li> <li>**CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect.</li> <li>**CAMERA_ERROR_PARAM_OUT_OF_RANGE**: A parameter is out of the range.</li> </ul> |

### OH_PhotoNative_Release()

```c
Camera_ErrorCode OH_PhotoNative_Release(OH_PhotoNative* photo)
```

**Description**

Releases a full-quality image.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to the **OH_PhotoNative** instance to release. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | **CAMERA_OK**: The operation is successful. <br>**CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoNative_ReleasePicture()

```c
Camera_ErrorCode OH_PhotoNative_ReleasePicture(OH_PictureNative* picture)
```

**Description**

Releases an allocated native picture instance.

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PictureNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-picturenative.md)* picture | [in] Pointer to the **OH_PictureNative** instance to release. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | <ul> <li>**CAMERA_OK**: The operation is successful.</li> <li>**CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect.</li> </ul> |

### OH_PhotoNative_ReleaseImage()

```c
Camera_ErrorCode OH_PhotoNative_ReleaseImage(OH_ImageNative* image)
```

**Description**

Releases an allocated native image instance.

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ImageNative](../../apis-image-kit/c-apis/capi-image-nativemodule-oh-imagenative.md)* image | [in] Pointer to the **OH_ImageNative** instance to release. |

**Returns**:

| Type | Description |
| -- | -- |
| [Camera_ErrorCode](capi-camera-h.md#camera_errorcode) | <ul> <li>**CAMERA_OK**: The operation is successful.</li> <li>**CAMERA_INVALID_ARGUMENT**: A parameter is missing or the parameter type is incorrect.</li> </ul> |


