# native_image.h

## Overview

Defines the functions for obtaining and using a native image.

**Library**: libnative_image.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 9

**Related module**: [OH_NativeImage](capi-oh-nativeimage.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_OnFrameAvailableListener](capi-oh-nativeimage-oh-onframeavailablelistener.md) | OH_OnFrameAvailableListener | A listener for native image, use <b>OH_NativeImage_SetOnFrameAvailableListener</b> to register the listener object to <b>OH_NativeImage</b>, the callback will be triggered when there is available frame |
| [NativeWindow](capi-oh-nativeimage-nativewindow.md) | OHNativeWindow | Defines the native window. |
| [NativeWindowBuffer](capi-oh-nativeimage-nativewindowbuffer.md) | OHNativeWindowBuffer | define the new type name OHNativeWindowBuffer for struct NativeWindowBuffer. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_OnFrameAvailable)(void *context)](#oh_onframeavailable) | OH_OnFrameAvailable | The callback function of frame available. |
| [OH_NativeImage* OH_NativeImage_Create(uint32_t textureId, uint32_t textureTarget)](#oh_nativeimage_create) | - | Create a <b>OH_NativeImage</b> related to an Opengl ES texture and target. This interface needs to be used in conjunction with <b>OH_NativeImage_Destroy</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface. |
| [OHNativeWindow* OH_NativeImage_AcquireNativeWindow(OH_NativeImage* image)](#oh_nativeimage_acquirenativewindow) | - | Acquire the OHNativeWindow for the OH_NativeImage. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_AttachContext(OH_NativeImage* image, uint32_t textureId)](#oh_nativeimage_attachcontext) | - | Attach the OH_NativeImage to Opengl ES context, and the Opengl ES texture is bound to the GL_TEXTURE_EXTERNAL_OES, which will update by the OH_NativeImage. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_DetachContext(OH_NativeImage* image)](#oh_nativeimage_detachcontext) | - | Detach the OH_NativeImage from the Opengl ES context. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_UpdateSurfaceImage(OH_NativeImage* image)](#oh_nativeimage_updatesurfaceimage) | - | Update the related Opengl ES texture with the OH_NativeImage acquired buffer. This interface needs to be called in the Opengl ES context thread. This interface needs to be called after receiving the <b>OH_OnFrameAvailableListener</b> callback. This interface is a non-thread-safe type interface. |
| [int64_t OH_NativeImage_GetTimestamp(OH_NativeImage* image)](#oh_nativeimage_gettimestamp) | - | Get the timestamp of the texture image set by the most recent call to OH_NativeImage_UpdateSurfaceImage. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_GetTransformMatrix(OH_NativeImage* image, float matrix[16])](#oh_nativeimage_gettransformmatrix) | - | Return the transform matrix of the texture image set by the most recent call to OH_NativeImage_UpdateSurfaceImage.(Deprecated in API12) |
| [int32_t OH_NativeImage_GetSurfaceId(OH_NativeImage* image, uint64_t* surfaceId)](#oh_nativeimage_getsurfaceid) | - | Return the native image's surface id. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_SetOnFrameAvailableListener(OH_NativeImage* image, OH_OnFrameAvailableListener listener)](#oh_nativeimage_setonframeavailablelistener) | - | Set the frame available callback. Not allow calling other interfaces in the callback function. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_UnsetOnFrameAvailableListener(OH_NativeImage* image)](#oh_nativeimage_unsetonframeavailablelistener) | - | Unset the frame available callback. This interface is a non-thread-safe type interface. |
| [void OH_NativeImage_Destroy(OH_NativeImage** image)](#oh_nativeimage_destroy) | - | Destroy the <b>OH_NativeImage</b> created by OH_NativeImage_Create, and the pointer to <b>OH_NativeImage</b> will be null after this operation. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_GetTransformMatrixV2(OH_NativeImage* image, float matrix[16])](#oh_nativeimage_gettransformmatrixv2) | - | Obtains the transform matrix of the texture image by producer transform type. The matrix will not be update until <b>OH_NativeImage_UpdateSurfaceImage</b> is called. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_GetBufferMatrix(OH_NativeImage* image, float matrix[16])](#oh_nativeimage_getbuffermatrix) | - | Obtains the transform matrix that combines with crop rect.<br> This API returns a transform matrix that combines the crop rect. Note that the matrix will not be updated until <b>OH_NativeImage_UpdateSurfaceImage</b> is called. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_AcquireNativeWindowBuffer(OH_NativeImage* image, OHNativeWindowBuffer** nativeWindowBuffer, int* fenceFd)](#oh_nativeimage_acquirenativewindowbuffer) | - | Acquire an <b>OHNativeWindowBuffer</b> through an <b>OH_NativeImage</b> instance for content consumer. This method can not be used at the same time with <b>OH_NativeImage_UpdateSurfaceImage</b>. This method will create an <b>OHNativeWindowBuffer</b>. When using <b>OHNativeWindowBuffer</b>, need to increase its reference count by <b>OH_NativeWindow_NativeObjectReference</b>. When the <b>OHNativeWindowBuffer</b> is used up, its reference count needs to be decremented by <b>OH_NativeWindow_NativeObjectUnreference</b>. This interface needs to be used in conjunction with <b>OH_NativeImage_ReleaseNativeWindowBuffer</b>, otherwise memory leaks will occur. When the fenceFd is used up, you need to close it. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_ReleaseNativeWindowBuffer(OH_NativeImage* image, OHNativeWindowBuffer* nativeWindowBuffer, int fenceFd)](#oh_nativeimage_releasenativewindowbuffer) | - | Release the <b>OHNativeWindowBuffer</b> to the buffer queue through an <b>OH_NativeImage</b> instance for reuse. The fenceFd will be closed by system. This interface is a non-thread-safe type interface. |
| [OH_NativeImage* OH_ConsumerSurface_Create(void)](#oh_consumersurface_create) | - | Create a <b>OH_NativeImage</b> as a consumerSurface. This interface is only used for memory rotation on the surface consumer, the <b>OH_NativeImage</b> will not actively perform memory rendering processing. This method can not be used at the same time with <b>OH_NativeImage_UpdateSurfaceImage</b>. This interface is used in conjunction with <b>OH_NativeImage_AcquireNativeWindowBuffer</b> and <b>OH_NativeImage_ReleaseNativeWindowBuffer</b>. This interface needs to be used in conjunction with <b>OH_NativeImage_Destroy</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface. |
| [int32_t OH_ConsumerSurface_SetDefaultUsage(OH_NativeImage* image, uint64_t usage)](#oh_consumersurface_setdefaultusage) | - | Set the default usage of the <b>OH_NativeImage</b>. This interface is a non-thread-safe type interface. |
| [int32_t OH_ConsumerSurface_SetDefaultSize(OH_NativeImage* image, int32_t width, int32_t height)](#oh_consumersurface_setdefaultsize) | - | Set the default size of the <b>OH_NativeImage</b>. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_SetDropBufferMode(OH_NativeImage* image, bool isOpen)](#oh_nativeimage_setdropbuffermode) | - | Set the rendering in drop buffer mode of the <b>OH_NativeImage</b>. In this mode, most of the buffers produced by the producer will be discarded, and the latest buffer will be selected for rending. This mode can not simultaneously guarantee high frame rate requirements. This interface suggest be called after the <b>OH_NativeImage_Create</b> call immediately. This interface will only take effect when used together with the <b>OH_NativeImage_UpdateSurfaceImage</b>. The listener callback set through <b>OH-NativeImage_SetOnFrameAvailableListener</b> will not decrease due to the frame loss mode being set. This interface is a non-thread-safe type interface. |
| [OH_NativeImage* OH_NativeImage_CreateWithSingleBufferMode(uint32_t textureId, uint32_t textureTarget, bool singleBufferMode)](#oh_nativeimage_createwithsinglebuffermode) | - | Create a <b>OH_NativeImage</b> related to an Opengl ES texture and target with textureId, and choose whether to set single buffer mode. |
| [OH_NativeImage* OH_ConsumerSurface_CreateWithSingleBufferMode(bool singleBufferMode)](#oh_consumersurface_createwithsinglebuffermode) | - | Create a <b>OH_NativeImage</b> as consumerSurface, and choose whether to set single buffer mode. This method can not be used at the same time with <b>OH_NativeImage_UpdateSurfaceImage</b>. This interface needs to be used in conjunction with <b>OH_NativeImage_Destroy</b>, otherwise memory leaks will occur. |
| [int32_t OH_NativeImage_ReleaseTextImage(OH_NativeImage* image)](#oh_nativeimage_releasetextimage) | - | Release the <b>OH_NativeImage</b> in single buffer mode. This interface suggest be called after the producer flushes the buffer to let the buffer queue rotate, in the single buffer mode. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_GetColorSpace(OH_NativeImage* image, OH_NativeBuffer_ColorSpace* colorSpace)](#oh_nativeimage_getcolorspace) | - | Get the colorSpace of <b>OH_NativeImage</b>. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_AcquireLatestNativeWindowBuffer(OH_NativeImage* image, OHNativeWindowBuffer** nativeWindowBuffer, int* fenceFd)](#oh_nativeimage_acquirelatestnativewindowbuffer) | - | Acquire a latest <b>OHNativeWindowBuffer</b> through an <b>OH_NativeImage</b> instance for content consumer. This method can get the latest <b>OHNativeWindowBuffer</b> and drop other <b>OHNativeWindowBuffers</b>, but consumer can receive the callbacks of all available buffers. This method can not be used at the same time with <b>OH_NativeImage_UpdateSurfaceImage</b>. This method will create an <b>OHNativeWindowBuffer</b>. If there is a situation when <b>OHNativeWindowBuffer</b> is still used after calling <b>OH_NativeImage_ReleaseNativeWindowBuffer</b>, you must pay attention to the following two points. 1) When using <b>OHNativeWindowBuffer</b>, need to increase its reference count by <b>OH_NativeWindow_NativeObjectReference</b>. 2) When the <b>OHNativeWindowBuffer</b> is used up, its reference count needs to be decremented by <b>OH_NativeWindow_NativeObjectUnreference</b>. This interface needs to be used in conjunction with <b>OH_NativeImage_ReleaseNativeWindowBuffer</b>, otherwise memory leaks will occur. When the fenceFd is used up, you need to close it. |
| [int32_t OH_NativeImage_IsReleased(OH_NativeImage* image, bool* isReleased)](#oh_nativeimage_isreleased) | - | Check whether the texture releated to the <b>OH_NativeImage</b> has been released. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeImage_Release(OH_NativeImage* image)](#oh_nativeimage_release) | - | Clean all <b>OHNativeWindowBuffer</b> caches of the <b>OHNativeWindow</b> for the <b>OH_NativeImage</b>, and detach the OH_NativeImage from the Opengl ES context. This interface is a non-thread-safe type interface. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_OnFrameAvailable)(void *context) | The callback function of frame available.<br>**Since**: 11<br>**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage |

## Function description

### OH_OnFrameAvailable()

```c
typedef void (*OH_OnFrameAvailable)(void *context)
```

**Description**

The callback function of frame available.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*context | User defined context, returned to the user in the callback function |

### OH_NativeImage_Create()

```c
OH_NativeImage* OH_NativeImage_Create(uint32_t textureId, uint32_t textureTarget)
```

**Description**

Create a <b>OH_NativeImage</b> related to an Opengl ES texture and target. This interface needs to be used in conjunction with <b>OH_NativeImage_Destroy</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t textureId | Indicates the id of the Opengl ES texture which the native image attached to. |
| uint32_t textureTarget | Indicates the Opengl ES target. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NativeImage* | Returns the pointer to the <b>OH_NativeImage</b> instance created if the operation is successful, \n  returns <b>NULL</b> otherwise. |

### OH_NativeImage_AcquireNativeWindow()

```c
OHNativeWindow* OH_NativeImage_AcquireNativeWindow(OH_NativeImage* image)
```

**Description**

Acquire the OHNativeWindow for the OH_NativeImage. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| [OHNativeWindow*](capi-oh-nativeimage-nativewindow.md) | Returns the pointer to the OHNativeWindow if the operation is successful, returns <b>NULL</b> otherwise. |

### OH_NativeImage_AttachContext()

```c
int32_t OH_NativeImage_AttachContext(OH_NativeImage* image, uint32_t textureId)
```

**Description**

Attach the OH_NativeImage to Opengl ES context, and the Opengl ES texture is bound to the GL_TEXTURE_EXTERNAL_OES, which will update by the OH_NativeImage. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| uint32_t textureId | Indicates the id of the Opengl ES texture which the native image attached to. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeImage_DetachContext()

```c
int32_t OH_NativeImage_DetachContext(OH_NativeImage* image)
```

**Description**

Detach the OH_NativeImage from the Opengl ES context. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeImage_UpdateSurfaceImage()

```c
int32_t OH_NativeImage_UpdateSurfaceImage(OH_NativeImage* image)
```

**Description**

Update the related Opengl ES texture with the OH_NativeImage acquired buffer. This interface needs to be called in the Opengl ES context thread. This interface needs to be called after receiving the <b>OH_OnFrameAvailableListener</b> callback. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeImage_GetTimestamp()

```c
int64_t OH_NativeImage_GetTimestamp(OH_NativeImage* image)
```

**Description**

Get the timestamp of the texture image set by the most recent call to OH_NativeImage_UpdateSurfaceImage. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | Returns the timestamp associated to the texture image. |

### OH_NativeImage_GetTransformMatrix()

```c
int32_t OH_NativeImage_GetTransformMatrix(OH_NativeImage* image, float matrix[16])
```

**Description**

Return the transform matrix of the texture image set by the most recent call to OH_NativeImage_UpdateSurfaceImage.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 9

**Deprecated**: 12

**Replaced by**: OH_NativeImage_GetTransformMatrixV2

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| float matrix[16] | Indicates the retrieved 4*4 transform matrix . |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeImage_GetSurfaceId()

```c
int32_t OH_NativeImage_GetSurfaceId(OH_NativeImage* image, uint64_t* surfaceId)
```

**Description**

Return the native image's surface id. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| uint64_t* surfaceId | Indicates the surface id. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeImage_SetOnFrameAvailableListener()

```c
int32_t OH_NativeImage_SetOnFrameAvailableListener(OH_NativeImage* image, OH_OnFrameAvailableListener listener)
```

**Description**

Set the frame available callback. Not allow calling other interfaces in the callback function. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| [OH_OnFrameAvailableListener](capi-oh-nativeimage-oh-onframeavailablelistener.md) listener | Indicates the callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeImage_UnsetOnFrameAvailableListener()

```c
int32_t OH_NativeImage_UnsetOnFrameAvailableListener(OH_NativeImage* image)
```

**Description**

Unset the frame available callback. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeImage_Destroy()

```c
void OH_NativeImage_Destroy(OH_NativeImage** image)
```

**Description**

Destroy the <b>OH_NativeImage</b> created by OH_NativeImage_Create, and the pointer to <b>OH_NativeImage</b> will be null after this operation. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage** image | Indicates the pointer to a <b>OH_NativeImage</b> pointer. |

### OH_NativeImage_GetTransformMatrixV2()

```c
int32_t OH_NativeImage_GetTransformMatrixV2(OH_NativeImage* image, float matrix[16])
```

**Description**

Obtains the transform matrix of the texture image by producer transform type. The matrix will not be update until <b>OH_NativeImage_UpdateSurfaceImage</b> is called. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| float matrix[16] | Indicates the retrieved 4*4 transform matrix . |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 - Success.      40001000 - image is NULL. |

### OH_NativeImage_GetBufferMatrix()

```c
int32_t OH_NativeImage_GetBufferMatrix(OH_NativeImage* image, float matrix[16])
```

**Description**

Obtains the transform matrix that combines with crop rect.<br> This API returns a transform matrix that combines the crop rect. Note that the matrix will not be updated until <b>OH_NativeImage_UpdateSurfaceImage</b> is called. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| float matrix[16] | Indicates the retrieved 4*4 transform matrix . |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image is NULL.<br>    {@link NATIVE_ERROR_MEM_OPERATION_ERROR} 30001000 - Memory operation error, failed to get transform matrix. |

### OH_NativeImage_AcquireNativeWindowBuffer()

```c
int32_t OH_NativeImage_AcquireNativeWindowBuffer(OH_NativeImage* image, OHNativeWindowBuffer** nativeWindowBuffer, int* fenceFd)
```

**Description**

Acquire an <b>OHNativeWindowBuffer</b> through an <b>OH_NativeImage</b> instance for content consumer. This method can not be used at the same time with <b>OH_NativeImage_UpdateSurfaceImage</b>. This method will create an <b>OHNativeWindowBuffer</b>. When using <b>OHNativeWindowBuffer</b>, need to increase its reference count by <b>OH_NativeWindow_NativeObjectReference</b>. When the <b>OHNativeWindowBuffer</b> is used up, its reference count needs to be decremented by <b>OH_NativeWindow_NativeObjectUnreference</b>. This interface needs to be used in conjunction with <b>OH_NativeImage_ReleaseNativeWindowBuffer</b>, otherwise memory leaks will occur. When the fenceFd is used up, you need to close it. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| [OHNativeWindowBuffer](capi-oh-nativeimage-nativewindowbuffer.md)** nativeWindowBuffer | Indicates the pointer to an <b>OHNativeWindowBuffer</b> point. |
| int* fenceFd | Indicates the pointer to a file descriptor handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image, nativeWindowBuffer, fenceFd is NULL.<br>    {@link NATIVE_ERROR_NO_BUFFER} 40601000 - No buffer for consume. |

### OH_NativeImage_ReleaseNativeWindowBuffer()

```c
int32_t OH_NativeImage_ReleaseNativeWindowBuffer(OH_NativeImage* image, OHNativeWindowBuffer* nativeWindowBuffer, int fenceFd)
```

**Description**

Release the <b>OHNativeWindowBuffer</b> to the buffer queue through an <b>OH_NativeImage</b> instance for reuse. The fenceFd will be closed by system. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| [OHNativeWindowBuffer](capi-oh-nativeimage-nativewindowbuffer.md)* nativeWindowBuffer | Indicates the pointer to an <b>OHNativeWindowBuffer</b> instance. |
| int fenceFd | Indicates a file descriptor handle, which is used for timing synchronization. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image, nativeWindowBuffer is NULL.<br>    {@link NATIVE_ERROR_BUFFER_STATE_INVALID} 41207000 - nativeWindowBuffer state invalid.<br>    {@link NATIVE_ERROR_BUFFER_NOT_IN_CACHE} 41210000 - nativeWindowBuffer not in cache. |

### OH_ConsumerSurface_Create()

```c
OH_NativeImage* OH_ConsumerSurface_Create(void)
```

**Description**

Create a <b>OH_NativeImage</b> as a consumerSurface. This interface is only used for memory rotation on the surface consumer, the <b>OH_NativeImage</b> will not actively perform memory rendering processing. This method can not be used at the same time with <b>OH_NativeImage_UpdateSurfaceImage</b>. This interface is used in conjunction with <b>OH_NativeImage_AcquireNativeWindowBuffer</b> and <b>OH_NativeImage_ReleaseNativeWindowBuffer</b>. This interface needs to be used in conjunction with <b>OH_NativeImage_Destroy</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| OH_NativeImage* | Returns the pointer to the <b>OH_NativeImage</b> instance created if the operation is successful, \n  returns <b>NULL</b> otherwise. |

### OH_ConsumerSurface_SetDefaultUsage()

```c
int32_t OH_ConsumerSurface_SetDefaultUsage(OH_NativeImage* image, uint64_t usage)
```

**Description**

Set the default usage of the <b>OH_NativeImage</b>. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| uint64_t usage | Indicates the usage of the <b>OH_NativeImage</b>.Refer to the enum <b>OH_NativeBuffer_Usage</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image is NULL. |

### OH_ConsumerSurface_SetDefaultSize()

```c
int32_t OH_ConsumerSurface_SetDefaultSize(OH_NativeImage* image, int32_t width, int32_t height)
```

**Description**

Set the default size of the <b>OH_NativeImage</b>. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| int32_t width | Indicates the width of the <b>OH_NativeImage</b>, and it should be greater than 0. |
| int32_t height | Indicates the height of the <b>OH_NativeImage</b>, and it should be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image is NULL or width, height less than or equal to 0. |

### OH_NativeImage_SetDropBufferMode()

```c
int32_t OH_NativeImage_SetDropBufferMode(OH_NativeImage* image, bool isOpen)
```

**Description**

Set the rendering in drop buffer mode of the <b>OH_NativeImage</b>. In this mode, most of the buffers produced by the producer will be discarded, and the latest buffer will be selected for rending. This mode can not simultaneously guarantee high frame rate requirements. This interface suggest be called after the <b>OH_NativeImage_Create</b> call immediately. This interface will only take effect when used together with the <b>OH_NativeImage_UpdateSurfaceImage</b>. The listener callback set through <b>OH-NativeImage_SetOnFrameAvailableListener</b> will not decrease due to the frame loss mode being set. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| bool isOpen | Indicates the switch of drop buffer mode. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image is NULL. |

### OH_NativeImage_CreateWithSingleBufferMode()

```c
OH_NativeImage* OH_NativeImage_CreateWithSingleBufferMode(uint32_t textureId, uint32_t textureTarget, bool singleBufferMode)
```

**Description**

Create a <b>OH_NativeImage</b> related to an Opengl ES texture and target with textureId, and choose whether to set single buffer mode.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t textureId | Indicates the id of the Opengl ES texture which the native image attached to. |
| uint32_t textureTarget | Indicates the Opengl ES target. |
| bool singleBufferMode | Whether to set single buffer mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NativeImage* | Returns the pointer to the <b>OH_NativeImage</b> instance created if the operation is successful, \n  returns <b>NULL</b> otherwise. |

### OH_ConsumerSurface_CreateWithSingleBufferMode()

```c
OH_NativeImage* OH_ConsumerSurface_CreateWithSingleBufferMode(bool singleBufferMode)
```

**Description**

Create a <b>OH_NativeImage</b> as consumerSurface, and choose whether to set single buffer mode. This method can not be used at the same time with <b>OH_NativeImage_UpdateSurfaceImage</b>. This interface needs to be used in conjunction with <b>OH_NativeImage_Destroy</b>, otherwise memory leaks will occur.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool singleBufferMode | Whether to set single buffer mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NativeImage* | Returns the pointer to the <b>OH_NativeImage</b> instance created if the operation is successful, \n  returns <b>NULL</b> otherwise. |

### OH_NativeImage_ReleaseTextImage()

```c
int32_t OH_NativeImage_ReleaseTextImage(OH_NativeImage* image)
```

**Description**

Release the <b>OH_NativeImage</b> in single buffer mode. This interface suggest be called after the producer flushes the buffer to let the buffer queue rotate, in the single buffer mode. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image is NULL. |

### OH_NativeImage_GetColorSpace()

```c
int32_t OH_NativeImage_GetColorSpace(OH_NativeImage* image, OH_NativeBuffer_ColorSpace* colorSpace)
```

**Description**

Get the colorSpace of <b>OH_NativeImage</b>. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| OH_NativeBuffer_ColorSpace* colorSpace | Indicates the colorSpace of <b>OH_NativeImage</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success. |

### OH_NativeImage_AcquireLatestNativeWindowBuffer()

```c
int32_t OH_NativeImage_AcquireLatestNativeWindowBuffer(OH_NativeImage* image, OHNativeWindowBuffer** nativeWindowBuffer, int* fenceFd)
```

**Description**

Acquire a latest <b>OHNativeWindowBuffer</b> through an <b>OH_NativeImage</b> instance for content consumer. This method can get the latest <b>OHNativeWindowBuffer</b> and drop other <b>OHNativeWindowBuffers</b>, but consumer can receive the callbacks of all available buffers. This method can not be used at the same time with <b>OH_NativeImage_UpdateSurfaceImage</b>. This method will create an <b>OHNativeWindowBuffer</b>. If there is a situation when <b>OHNativeWindowBuffer</b> is still used after calling <b>OH_NativeImage_ReleaseNativeWindowBuffer</b>, you must pay attention to the following two points. 1) When using <b>OHNativeWindowBuffer</b>, need to increase its reference count by <b>OH_NativeWindow_NativeObjectReference</b>. 2) When the <b>OHNativeWindowBuffer</b> is used up, its reference count needs to be decremented by <b>OH_NativeWindow_NativeObjectUnreference</b>. This interface needs to be used in conjunction with <b>OH_NativeImage_ReleaseNativeWindowBuffer</b>, otherwise memory leaks will occur. When the fenceFd is used up, you need to close it.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| [OHNativeWindowBuffer](capi-oh-nativeimage-nativewindowbuffer.md)** nativeWindowBuffer | Indicates the pointer to an <b>OHNativeWindowBuffer</b> point. |
| int* fenceFd | Indicates the pointer to a file descriptor handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image, nativeWindowBuffer, fenceFd is NULL.<br>    {@link NATIVE_ERROR_NO_BUFFER} 40601000 - No buffer for consume. |

### OH_NativeImage_IsReleased()

```c
int32_t OH_NativeImage_IsReleased(OH_NativeImage* image, bool* isReleased)
```

**Description**

Check whether the texture releated to the <b>OH_NativeImage</b> has been released. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |
| bool* isReleased | Indicates whether the texture releated to the <b>OH_NativeImage</b> has been released. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image or isReleased is NULL. |

### OH_NativeImage_Release()

```c
int32_t OH_NativeImage_Release(OH_NativeImage* image)
```

**Description**

Clean all <b>OHNativeWindowBuffer</b> caches of the <b>OHNativeWindow</b> for the <b>OH_NativeImage</b>, and detach the OH_NativeImage from the Opengl ES context. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeImage* image | Indicates the pointer to a <b>OH_NativeImage</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - image is NULL. |


