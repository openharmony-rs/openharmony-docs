# metadata_output.h

## Overview

The file declares the metadata output concepts.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [MetadataOutput_Callbacks](capi-oh-camera-metadataoutput-callbacks.md) | MetadataOutput_Callbacks | The struct describes the callbacks related to metadata output. |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md) | Camera_MetadataOutput | Defines a struct for the metadata output object.<br>You can use the {@link OH_CameraManager_CreateMetadataOutput} method and **OH_CameraManager_CreateMetadataOutputWithObjectTypes** method (supported since API version 23) to create a pointer. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_MetadataOutput_OnMetadataObjectAvailable)(Camera_MetadataOutput* metadataOutput, Camera_MetadataObject* metadataObject, uint32_t size)](#oh_metadataoutput_onmetadataobjectavailable) | OH_MetadataOutput_OnMetadataObjectAvailable | Defines the callback defined in the [MetadataOutput_Callbacks](capi-oh-camera-metadataoutput-callbacks.md) struct and used to report metadata output data. |
| [typedef void (\*OH_MetadataOutput_OnMetadataObjectExtAvailable)(void* context, OH_Camera_MetadataObjectExt** metadataObjectExt, uint32_t size)](#oh_metadataoutput_onmetadataobjectextavailable) | OH_MetadataOutput_OnMetadataObjectExtAvailable | Defines the callback used to listen for metadata object ext available. |
| [typedef void (\*OH_MetadataOutput_OnError)(Camera_MetadataOutput* metadataOutput, Camera_ErrorCode errorCode)](#oh_metadataoutput_onerror) | OH_MetadataOutput_OnError | Defines the callback defined in the [MetadataOutput_Callbacks](capi-oh-camera-metadataoutput-callbacks.md) struct and used to report metadata output errors. |
| [typedef void (\*OH_MetadataOutput_OnErrorExt)(void* context, Camera_ErrorCode errorCode)](#oh_metadataoutput_onerrorext) | OH_MetadataOutput_OnErrorExt | Defines the callback used to listen for error ext event. |
| [Camera_ErrorCode OH_MetadataOutput_RegisterCallback(Camera_MetadataOutput* metadataOutput, MetadataOutput_Callbacks* callback)](#oh_metadataoutput_registercallback) | - | Registers a callback to listen for metadata output events. |
| [Camera_ErrorCode OH_MetadataOutput_UnregisterCallback(Camera_MetadataOutput* metadataOutput, MetadataOutput_Callbacks* callback)](#oh_metadataoutput_unregistercallback) | - | Unregisters the callback used to listen for metadata output events. |
| [Camera_ErrorCode OH_MetadataOutput_RegisterMetadataObjectExtAvailableCallback(Camera_MetadataOutput* metadataOutput, void* context, OH_MetadataOutput_OnMetadataObjectExtAvailable callback)](#oh_metadataoutput_registermetadataobjectextavailablecallback) | - | Registers a callback to listen for {@link OH_Camera_MetadataObjectExt} events. The callback can be unregistered by [OH_MetadataOutput_UnregisterMetadataObjectExtAvailableCallback](capi-metadata-output-h.md#oh_metadataoutput_unregistermetadataobjectextavailablecallback). |
| [Camera_ErrorCode OH_MetadataOutput_UnregisterMetadataObjectExtAvailableCallback(Camera_MetadataOutput* metadataOutput, void* context, OH_MetadataOutput_OnMetadataObjectExtAvailable callback)](#oh_metadataoutput_unregistermetadataobjectextavailablecallback) | - | Unregisters the callback used to listen for metadata object ext events. |
| [Camera_ErrorCode OH_MetadataOutput_RegisterErrorExtCallback(Camera_MetadataOutput* metadataOutput, void* context, OH_MetadataOutput_OnErrorExt callback)](#oh_metadataoutput_registererrorextcallback) | - | Registers a callback to listen for error ext events. The callback can be unregistered by [OH_MetadataOutput_UnregisterErrorExtCallback](capi-metadata-output-h.md#oh_metadataoutput_unregistererrorextcallback). |
| [Camera_ErrorCode OH_MetadataOutput_UnregisterErrorExtCallback(Camera_MetadataOutput* metadataOutput, void* context, OH_MetadataOutput_OnErrorExt callback)](#oh_metadataoutput_unregistererrorextcallback) | - | Unregisters the callback used to listen for error ext events. |
| [Camera_ErrorCode OH_MetadataOutput_Start(Camera_MetadataOutput* metadataOutput)](#oh_metadataoutput_start) | - | Starts metadata output. |
| [Camera_ErrorCode OH_MetadataOutput_Stop(Camera_MetadataOutput* metadataOutput)](#oh_metadataoutput_stop) | - | Stops metadata output. |
| [Camera_ErrorCode OH_MetadataOutput_Release(Camera_MetadataOutput* metadataOutput)](#oh_metadataoutput_release) | - | Releases a MetadataOutput instance. |
| [Camera_ErrorCode OH_MetadataOutput_AddMetadataObjectTypes (Camera_MetadataOutput* metadataOutput, Camera_MetadataObjectType* types, uint32_t size)](#) | - | Adds the metadata object types. |
| [Camera_ErrorCode OH_MetadataOutput_RemoveMetadataObjectTypes (Camera_MetadataOutput* metadataOutput, Camera_MetadataObjectType* types, uint32_t size)](#) | - | Removes the metadata object types. |
| [bool OH_MetadataOutput_IsLockMetadataObjectTrackingSupported(const Camera_MetadataOutput* metadataOutput)](#oh_metadataoutput_islockmetadataobjecttrackingsupported) | - | Checks whether the lock metadata object tracking is supported. |
| [Camera_ErrorCode OH_MetadataOutput_LockMetadataObjectTracking(Camera_MetadataOutput* metadataOutput, Camera_Point* pointOfInterest)](#oh_metadataoutput_lockmetadataobjecttracking) | - | Lock metadata object tracking, can be unlocked by [OH_MetadataOutput_UnlockMetadataObjectTracking](capi-metadata-output-h.md#oh_metadataoutput_unlockmetadataobjecttracking). |
| [Camera_ErrorCode OH_MetadataOutput_UnlockMetadataObjectTracking(Camera_MetadataOutput* metadataOutput)](#oh_metadataoutput_unlockmetadataobjecttracking) | - | Unlock metadata object tracking. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_MetadataOutput_OnMetadataObjectAvailable)(Camera_MetadataOutput* metadataOutput, Camera_MetadataObject* metadataObject, uint32_t size) | Defines the callback defined in the [MetadataOutput_Callbacks](capi-oh-camera-metadataoutput-callbacks.md) struct and used to report metadata output data.<br>**Since**: 11 |
| void (*OH_MetadataOutput_OnMetadataObjectExtAvailable)(void* context, OH_Camera_MetadataObjectExt** metadataObjectExt, uint32_t size) | Defines the callback used to listen for metadata object ext available.<br>**Since**: 26.0.0 |
| void (*OH_MetadataOutput_OnError)(Camera_MetadataOutput* metadataOutput, Camera_ErrorCode errorCode) | Defines the callback defined in the [MetadataOutput_Callbacks](capi-oh-camera-metadataoutput-callbacks.md) struct and used to report metadata output errors.<br>**Since**: 11 |
| void (*OH_MetadataOutput_OnErrorExt)(void* context, Camera_ErrorCode errorCode) | Defines the callback used to listen for error ext event.<br>**Since**: 26.0.0 |

## Function description

### OH_MetadataOutput_OnMetadataObjectAvailable()

```c
typedef void (*OH_MetadataOutput_OnMetadataObjectAvailable)(Camera_MetadataOutput* metadataOutput, Camera_MetadataObject* metadataObject, uint32_t size)
```

**Description**

Defines the callback defined in the [MetadataOutput_Callbacks](capi-oh-camera-metadataoutput-callbacks.md) struct and used to report metadata output data.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)\* metadataOutput | Pointer to the MetadataOutput instance that transfers the callback. |
| Camera_MetadataObject\* metadataObject | Pointer to the metadata output data. |
| uint32_t size | Size of the metadata object. |

### OH_MetadataOutput_OnMetadataObjectExtAvailable()

```c
typedef void (*OH_MetadataOutput_OnMetadataObjectExtAvailable)(void* context, OH_Camera_MetadataObjectExt** metadataObjectExt, uint32_t size)
```

**Description**

Defines the callback used to listen for metadata object ext available.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| void\* context | Pointer to the context provided by user. |
| OH_Camera_MetadataObjectExt\*\* metadataObjectExt | Pointer to the metadata output data. |
| uint32_t size | Size of the metadata object ext. |

### OH_MetadataOutput_OnError()

```c
typedef void (*OH_MetadataOutput_OnError)(Camera_MetadataOutput* metadataOutput, Camera_ErrorCode errorCode)
```

**Description**

Defines the callback defined in the [MetadataOutput_Callbacks](capi-oh-camera-metadataoutput-callbacks.md) struct and used to report metadata output errors.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)\* metadataOutput | Pointer to the MetadataOutput instance that transfers the callback. |
| Camera_ErrorCode errorCode | Error code reported during metadata output. |

**Reference**:

CAMERA_SERVICE_FATAL_ERROR


### OH_MetadataOutput_OnErrorExt()

```c
typedef void (*OH_MetadataOutput_OnErrorExt)(void* context, Camera_ErrorCode errorCode)
```

**Description**

Defines the callback used to listen for error ext event.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| void\* context | Pointer to the context provided by user. |
| Camera_ErrorCode errorCode | Error code reported during metadata output. |

**Reference**:

CAMERA_SERVICE_FATAL_ERROR


### OH_MetadataOutput_RegisterCallback()

```c
Camera_ErrorCode OH_MetadataOutput_RegisterCallback(Camera_MetadataOutput* metadataOutput, MetadataOutput_Callbacks* callback)
```

**Description**

Registers a callback to listen for metadata output events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to a MetadataOutput instance. |
| [MetadataOutput_Callbacks](capi-oh-camera-metadataoutput-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_MetadataOutput_UnregisterCallback()

```c
Camera_ErrorCode OH_MetadataOutput_UnregisterCallback(Camera_MetadataOutput* metadataOutput, MetadataOutput_Callbacks* callback)
```

**Description**

Unregisters the callback used to listen for metadata output events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to a MetadataOutput instance. |
| [MetadataOutput_Callbacks](capi-oh-camera-metadataoutput-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_MetadataOutput_RegisterMetadataObjectExtAvailableCallback()

```c
Camera_ErrorCode OH_MetadataOutput_RegisterMetadataObjectExtAvailableCallback(Camera_MetadataOutput* metadataOutput, void* context, OH_MetadataOutput_OnMetadataObjectExtAvailable callback)
```

**Description**

Registers a callback to listen for {@link OH_Camera_MetadataObjectExt} events. The callback can be unregistered by [OH_MetadataOutput_UnregisterMetadataObjectExtAvailableCallback](capi-metadata-output-h.md#oh_metadataoutput_unregistermetadataobjectextavailablecallback).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to the [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md) instance. |
| void* context | Pointer to the context provided by user. |
| [OH_MetadataOutput_OnMetadataObjectExtAvailable](capi-metadata-output-h.md#oh_metadataoutput_onmetadataobjectextavailable) callback | Pointer to the [OH_MetadataOutput_OnMetadataObjectExtAvailable](capi-metadata-output-h.md#oh_metadataoutput_onmetadataobjectextavailable) callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_MetadataOutput_UnregisterMetadataObjectExtAvailableCallback()

```c
Camera_ErrorCode OH_MetadataOutput_UnregisterMetadataObjectExtAvailableCallback(Camera_MetadataOutput* metadataOutput, void* context, OH_MetadataOutput_OnMetadataObjectExtAvailable callback)
```

**Description**

Unregisters the callback used to listen for metadata object ext events.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to a MetadataOutput instance. |
| void* context | Pointer to the context provided by user. |
| [OH_MetadataOutput_OnMetadataObjectExtAvailable](capi-metadata-output-h.md#oh_metadataoutput_onmetadataobjectextavailable) callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_MetadataOutput_RegisterErrorExtCallback()

```c
Camera_ErrorCode OH_MetadataOutput_RegisterErrorExtCallback(Camera_MetadataOutput* metadataOutput, void* context, OH_MetadataOutput_OnErrorExt callback)
```

**Description**

Registers a callback to listen for error ext events. The callback can be unregistered by [OH_MetadataOutput_UnregisterErrorExtCallback](capi-metadata-output-h.md#oh_metadataoutput_unregistererrorextcallback).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to the [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md) instance. |
| void* context | Pointer to the context provided by user. |
| [OH_MetadataOutput_OnErrorExt](capi-metadata-output-h.md#oh_metadataoutput_onerrorext) callback | Pointer to the [OH_MetadataOutput_OnErrorExt](capi-metadata-output-h.md#oh_metadataoutput_onerrorext) callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_MetadataOutput_UnregisterErrorExtCallback()

```c
Camera_ErrorCode OH_MetadataOutput_UnregisterErrorExtCallback(Camera_MetadataOutput* metadataOutput, void* context, OH_MetadataOutput_OnErrorExt callback)
```

**Description**

Unregisters the callback used to listen for error ext events.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to a MetadataOutput instance. |
| void* context | Pointer to the context provided by user. |
| [OH_MetadataOutput_OnErrorExt](capi-metadata-output-h.md#oh_metadataoutput_onerrorext) callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_MetadataOutput_Start()

```c
Camera_ErrorCode OH_MetadataOutput_Start(Camera_MetadataOutput* metadataOutput)
```

**Description**

Starts metadata output.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to the MetadataOutput instance to start. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_MetadataOutput_Stop()

```c
Camera_ErrorCode OH_MetadataOutput_Stop(Camera_MetadataOutput* metadataOutput)
```

**Description**

Stops metadata output.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to the MetadataOutput instance to stop. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_MetadataOutput_Release()

```c
Camera_ErrorCode OH_MetadataOutput_Release(Camera_MetadataOutput* metadataOutput)
```

**Description**

Releases a MetadataOutput instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to the MetadataOutput instance to release. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### ()

```c
Camera_ErrorCode OH_MetadataOutput_AddMetadataObjectTypes (Camera_MetadataOutput* metadataOutput, Camera_MetadataObjectType* types, uint32_t size)
```

**Description**

Adds the metadata object types.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to a MetadataOutput instance. |
| Camera_MetadataObjectType* types | Array of metadata object types to be added to the **Camera_MetadataOutput** instance. |
| uint32_t size | Length of the metadata object type array. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode OH_MetadataOutput_AddMetadataObjectTypes | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### ()

```c
Camera_ErrorCode OH_MetadataOutput_RemoveMetadataObjectTypes (Camera_MetadataOutput* metadataOutput, Camera_MetadataObjectType* types, uint32_t size)
```

**Description**

Removes the metadata object types.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to a MetadataOutput instance. |
| Camera_MetadataObjectType* types | Array of metadata object types removed from the **Camera_MetadataOutput** instance. |
| uint32_t size | Length of the metadata object type array. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode OH_MetadataOutput_RemoveMetadataObjectTypes | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_MetadataOutput_IsLockMetadataObjectTrackingSupported()

```c
bool OH_MetadataOutput_IsLockMetadataObjectTrackingSupported(const Camera_MetadataOutput* metadataOutput)
```

**Description**

Checks whether the lock metadata object tracking is supported.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to a MetadataOutput instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if supported, false otherwise. |

### OH_MetadataOutput_LockMetadataObjectTracking()

```c
Camera_ErrorCode OH_MetadataOutput_LockMetadataObjectTracking(Camera_MetadataOutput* metadataOutput, Camera_Point* pointOfInterest)
```

**Description**

Lock metadata object tracking, can be unlocked by [OH_MetadataOutput_UnlockMetadataObjectTracking](capi-metadata-output-h.md#oh_metadataoutput_unlockmetadataobjecttracking).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to a MetadataOutput instance. |
| Camera_Point* pointOfInterest | Pointer to the point of interest. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_MetadataOutput_UnlockMetadataObjectTracking()

```c
Camera_ErrorCode OH_MetadataOutput_UnlockMetadataObjectTracking(Camera_MetadataOutput* metadataOutput)
```

**Description**

Unlock metadata object tracking.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_MetadataOutput](capi-oh-camera-camera-metadataoutput.md)* metadataOutput | Pointer to a MetadataOutput instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |


