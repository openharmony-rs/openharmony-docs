# metadata_object_ext.h

## Overview

The file declares the metadata object ext concepts.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md) | OH_Camera_MetadataObjectExt | The struct describes the camera metadata object ext. |

### Function

| Name | Description |
| -- | -- |
| [Camera_ErrorCode OH_MetadataObjectExt_GetMetadataObjectType(const OH_Camera_MetadataObjectExt* metadataObjectExt, Camera_MetadataObjectType* type)](#oh_metadataobjectext_getmetadataobjecttype) | Obtains metadata object type. |
| [Camera_ErrorCode OH_MetadataObjectExt_GetTimestamp(const OH_Camera_MetadataObjectExt* metadataObjectExt, int64_t* timestamp)](#oh_metadataobjectext_gettimestamp) | Obtains the timestamp of the metadata object extension. |
| [Camera_ErrorCode OH_MetadataObjectExt_GetBoundingBox(const OH_Camera_MetadataObjectExt* metadataObjectExt, OH_Camera_Rect_Ext* boundingBox)](#oh_metadataobjectext_getboundingbox) | Obtains the bounding box of the metadata object extension. |
| [Camera_ErrorCode OH_MetadataObjectExt_GetPitchAngle(const OH_Camera_MetadataObjectExt* metadataObjectExt, float* pitchAngle)](#oh_metadataobjectext_getpitchangle) | Obtains the pitch angle of the metadata object extension. |
| [Camera_ErrorCode OH_MetadataObjectExt_GetYawAngle(const OH_Camera_MetadataObjectExt* metadataObjectExt, float* yawAngle)](#oh_metadataobjectext_getyawangle) | Obtains the yaw angle of the metadata object extension. |
| [Camera_ErrorCode OH_MetadataObjectExt_GetRollAngle(const OH_Camera_MetadataObjectExt* metadataObjectExt, float* rollAngle)](#oh_metadataobjectext_getrollangle) | Obtains the roll angle of the metadata object extension. |
| [Camera_ErrorCode OH_MetadataObjectExt_GetLeftEyeBoundingBox(const OH_Camera_MetadataObjectExt* metadataObjectExt, OH_Camera_Rect_Ext* boundingBox)](#oh_metadataobjectext_getlefteyeboundingbox) | Obtains the left eye bounding box of the metadata object extension. |
| [Camera_ErrorCode OH_MetadataObjectExt_GetRightEyeBoundingBox(const OH_Camera_MetadataObjectExt* metadataObjectExt, OH_Camera_Rect_Ext* boundingBox)](#oh_metadataobjectext_getrighteyeboundingbox) | Obtains the right eye bounding box of the metadata object extension. |
| [Camera_ErrorCode OH_MetadataObjectExt_GetEmotion(const OH_Camera_MetadataObjectExt* metadataObjectExt, OH_Camera_MetadataObjectEmotion* emotion)](#oh_metadataobjectext_getemotion) | Obtains the emotion of the metadata object extension. |
| [void OH_MetadataObjectExt_Destroy(OH_Camera_MetadataObjectExt** metadataObjectExt, uint32_t objectCount)](#oh_metadataobjectext_destroy) | Destroys an array of [OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md) instances. |
| [bool OH_MetadataObjectExt_IsLockFocusTracked(const OH_Camera_MetadataObjectExt* metadataObjectExt)](#oh_metadataobjectext_islockfocustracked) | Checks if focus is locked and tracked. |

## Function description

### OH_MetadataObjectExt_GetMetadataObjectType()

```c
Camera_ErrorCode OH_MetadataObjectExt_GetMetadataObjectType(const OH_Camera_MetadataObjectExt* metadataObjectExt, Camera_MetadataObjectType* type)
```

**Description**

Obtains metadata object type.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |
| Camera_MetadataObjectType* type | Pointer to the metadata object type, which is an **Camera_MetadataObjectType** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_MetadataObjectExt_GetTimestamp()

```c
Camera_ErrorCode OH_MetadataObjectExt_GetTimestamp(const OH_Camera_MetadataObjectExt* metadataObjectExt, int64_t* timestamp)
```

**Description**

Obtains the timestamp of the metadata object extension.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |
| int64_t* timestamp | Pointer to store the timestamp. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_MetadataObjectExt_GetBoundingBox()

```c
Camera_ErrorCode OH_MetadataObjectExt_GetBoundingBox(const OH_Camera_MetadataObjectExt* metadataObjectExt, OH_Camera_Rect_Ext* boundingBox)
```

**Description**

Obtains the bounding box of the metadata object extension.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |
| OH_Camera_Rect_Ext* boundingBox | Pointer to the metadata object bounding box, which is an **OH_Camera_Rect_Ext** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_MetadataObjectExt_GetPitchAngle()

```c
Camera_ErrorCode OH_MetadataObjectExt_GetPitchAngle(const OH_Camera_MetadataObjectExt* metadataObjectExt, float* pitchAngle)
```

**Description**

Obtains the pitch angle of the metadata object extension.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |
| float* pitchAngle | Pointer to store the pitch angle. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST: The optional property does not exist. |

### OH_MetadataObjectExt_GetYawAngle()

```c
Camera_ErrorCode OH_MetadataObjectExt_GetYawAngle(const OH_Camera_MetadataObjectExt* metadataObjectExt, float* yawAngle)
```

**Description**

Obtains the yaw angle of the metadata object extension.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |
| float* yawAngle | Pointer to store the yaw angle. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST: The optional property does not exist. |

### OH_MetadataObjectExt_GetRollAngle()

```c
Camera_ErrorCode OH_MetadataObjectExt_GetRollAngle(const OH_Camera_MetadataObjectExt* metadataObjectExt, float* rollAngle)
```

**Description**

Obtains the roll angle of the metadata object extension.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |
| float* rollAngle | Pointer to store the roll angle. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST: The optional property does not exist. |

### OH_MetadataObjectExt_GetLeftEyeBoundingBox()

```c
Camera_ErrorCode OH_MetadataObjectExt_GetLeftEyeBoundingBox(const OH_Camera_MetadataObjectExt* metadataObjectExt, OH_Camera_Rect_Ext* boundingBox)
```

**Description**

Obtains the left eye bounding box of the metadata object extension.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |
| OH_Camera_Rect_Ext* boundingBox | Pointer to the metadata object bounding box, which is an **OH_Camera_Rect_Ext** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST: The optional property does not exist. |

### OH_MetadataObjectExt_GetRightEyeBoundingBox()

```c
Camera_ErrorCode OH_MetadataObjectExt_GetRightEyeBoundingBox(const OH_Camera_MetadataObjectExt* metadataObjectExt, OH_Camera_Rect_Ext* boundingBox)
```

**Description**

Obtains the right eye bounding box of the metadata object extension.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |
| OH_Camera_Rect_Ext* boundingBox | Pointer to the metadata object bounding box, which is an **OH_Camera_Rect_Ext** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST: The optional property does not exist. |

### OH_MetadataObjectExt_GetEmotion()

```c
Camera_ErrorCode OH_MetadataObjectExt_GetEmotion(const OH_Camera_MetadataObjectExt* metadataObjectExt, OH_Camera_MetadataObjectEmotion* emotion)
```

**Description**

Obtains the emotion of the metadata object extension.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |
| OH_Camera_MetadataObjectEmotion* emotion | Pointer to store the emotion type. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_ERROR_OPTIONAL_PROPERTY_NOT_EXIST: The optional property does not exist. |

### OH_MetadataObjectExt_Destroy()

```c
void OH_MetadataObjectExt_Destroy(OH_Camera_MetadataObjectExt** metadataObjectExt, uint32_t objectCount)
```

**Description**

Destroys an array of [OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md) instances.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)** metadataObjectExt | Pointer to the array of [OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md) instances. |
| uint32_t objectCount | Indicates the number of metadata objects to be destroyed. |

### OH_MetadataObjectExt_IsLockFocusTracked()

```c
bool OH_MetadataObjectExt_IsLockFocusTracked(const OH_Camera_MetadataObjectExt* metadataObjectExt)
```

**Description**

Checks if focus is locked and tracked.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_Camera_MetadataObjectExt](capi-oh-camera-oh-camera-metadataobjectext.md)* metadataObjectExt | Pointer to a OH_Camera_MetadataObjectExt instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if locked and tracked, false otherwise. |


