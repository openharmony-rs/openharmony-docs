# photo_native.h

## Overview

The file declares the camera photo concepts.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

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
| [Camera_ErrorCode OH_PhotoNative_Release(OH_PhotoNative* photo)](#oh_photonative_release) | Releases a full-quality image. |

## Function description

### OH_PhotoNative_GetMainImage()

```c
Camera_ErrorCode OH_PhotoNative_GetMainImage(OH_PhotoNative* photo, OH_ImageNative** mainImage)
```

**Description**

Obtains a full-quality image.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to an **OH_PhotoNative** instance. |
| OH_ImageNative** mainImage | Double pointer to the full-quality image, which is an **OH_ImageNative** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoNative_GetUncompressedImage()

```c
Camera_ErrorCode OH_PhotoNative_GetUncompressedImage(OH_PhotoNative* photo, OH_PictureNative** picture)
```

**Description**

Obtains an uncompressed image.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to an **OH_PhotoNative** instance. |
| OH_PictureNative** picture | Double pointer to the uncompressed image, which is an **OH_PictureNative** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoNative_Release()

```c
Camera_ErrorCode OH_PhotoNative_Release(OH_PhotoNative* photo)
```

**Description**

Releases a full-quality image.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_PhotoNative](capi-oh-camera-oh-photonative.md)* photo | Pointer to the **OH_PhotoNative** instance to release. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |


