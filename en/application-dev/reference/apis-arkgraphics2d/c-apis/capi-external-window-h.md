# external_window.h

## Overview

Defines the functions for obtaining and using a native window.

**Library**: libnative_window.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Related module**: [NativeWindow](capi-nativewindow.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Region](capi-nativewindow-region.md) | Region | indicates a dirty region where content is updated. |
| [OHHDRMetaData](capi-nativewindow-ohhdrmetadata.md) | OHHDRMetaData | Defines the HDR metadata. |
| [OHExtDataHandle](capi-nativewindow-ohextdatahandle.md) | OHExtDataHandle | Defines the ExtData Handle |
| [OH_NativeBuffer](capi-nativewindow-oh-nativebuffer.md) | OH_NativeBuffer | Provides native buffer capability. |
| [OHIPCParcel](capi-nativewindow-ohipcparcel.md) | OHIPCParcel | Defines the ipc parcel. |
| [NativeWindow](capi-nativewindow-nativewindow.md) | - | native window. |
| [NativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) | - | native window buffer. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [NativeWindowOperation](#nativewindowoperation) | NativeWindowOperation | Indicates the operation code in the function OH_NativeWindow_NativeWindowHandleOpt. |
| [OHScalingMode](#ohscalingmode) | OHScalingMode | Indicates Scaling Mode.(Deprecated in API10) |
| [OHScalingModeV2](#ohscalingmodev2) | OHScalingModeV2 | Indicates Scaling Mode. |
| [OHHDRMetadataKey](#ohhdrmetadatakey) | OHHDRMetadataKey | Enumerates the HDR metadata keys.(Deprecated in API10) |
| [OHSurfaceSource](#ohsurfacesource) | OHSurfaceSource | Indicates the source type of surface. |

### Function

| Name | Description |
| -- | -- |
| [OHNativeWindow* OH_NativeWindow_CreateNativeWindow(void* pSurface)](#oh_nativewindow_createnativewindow) | Creates a <b>OHNativeWindow</b> instance. A new <b>OHNativeWindow</b> instance is created each time this function is called.(Deprecated in API12) |
| [void OH_NativeWindow_DestroyNativeWindow(OHNativeWindow* window)](#oh_nativewindow_destroynativewindow) | Decreases the reference count of a <b>OHNativeWindow</b> instance by 1, and when the reference count reaches 0, destroys the instance. This interface is a non-thread-safe type interface. |
| [OHNativeWindowBuffer* OH_NativeWindow_CreateNativeWindowBufferFromSurfaceBuffer(void* pSurfaceBuffer)](#oh_nativewindow_createnativewindowbufferfromsurfacebuffer) | Creates a <b>OHNativeWindowBuffer</b> instance. A new <b>OHNativeWindowBuffer</b> instance is created each time this function is called.(Deprecated in API12) |
| [OHNativeWindowBuffer* OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer(OH_NativeBuffer* nativeBuffer)](#oh_nativewindow_createnativewindowbufferfromnativebuffer) | Creates a <b>OHNativeWindowBuffer</b> instance. A new <b>OHNativeWindowBuffer</b> instance is created each time this function is called. This interface needs to be used in conjunction with <b>OH_NativeWindow_DestroyNativeWindowBuffer</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface. |
| [void OH_NativeWindow_DestroyNativeWindowBuffer(OHNativeWindowBuffer* buffer)](#oh_nativewindow_destroynativewindowbuffer) | Decreases the reference count of a <b>OHNativeWindowBuffer</b> instance by 1 and, when the reference count reaches 0, destroys the instance. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_NativeWindowRequestBuffer(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd)](#oh_nativewindow_nativewindowrequestbuffer) | Requests a <b>OHNativeWindowBuffer</b> through a <b>OHNativeWindow</b> instance for content production. Before calling this interface, you need to set the width and height of <b>OHNativeWindow</b> through <b>SET_BUFFER_GEOMETRY</b>. This interface needs to be used in conjunction with <b>OH_NativeWindow_NativeWindowFlushBuffer</b>, otherwise buffer will be exhausted. When the fenceFd is used up, you need to close it. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_NativeWindowFlushBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer, int fenceFd, Region region)](#oh_nativewindow_nativewindowflushbuffer) | Flushes the <b>OHNativeWindowBuffer</b> filled with the content to the buffer queue through a <b>OHNativeWindow</b> instance for content consumption. The fenceFd will be close by system. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_GetLastFlushedBuffer(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd, float matrix[16])](#oh_nativewindow_getlastflushedbuffer) | Get the last flushed <b>OHNativeWindowBuffer</b> from a <b>OHNativeWindow</b> instance.(Deprecated in API12) |
| [int32_t OH_NativeWindow_NativeWindowAbortBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)](#oh_nativewindow_nativewindowabortbuffer) | Returns the <b>OHNativeWindowBuffer</b> to the buffer queue through a <b>OHNativeWindow</b> instance, without filling in any content. The <b>OHNativeWindowBuffer</b> can be used for another request. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_NativeWindowHandleOpt(OHNativeWindow *window, int code, ...)](#oh_nativewindow_nativewindowhandleopt) | Sets or obtains the attributes of a native window, including the width, height, and content format. This interface is a non-thread-safe type interface.<br> <p><strong>API Note</strong><br> <strong>Performance Note</strong> <p>By default, the window buffer in the current operating system is accessed via the CPU. If an application does not need to access the window buffer data using the CPU, it can proactively disable CPU access to enhance energy efficiency and reduce power consumption. </p> <p>For details about how to optimize power consumption for data read/write operations in data buffers, see [How do I proactively disable CPU access to window buffers to reduce power consumption?]{@link https://developer.huawei.com/consumer/en/doc/harmonyos-faqs/faqs-arkgraphics-2d-14}.</p> </p> |
| [BufferHandle *OH_NativeWindow_GetBufferHandleFromNative(OHNativeWindowBuffer *buffer)](#oh_nativewindow_getbufferhandlefromnative) | Obtains the pointer to a <b>BufferHandle</b> of a <b>OHNativeWindowBuffer</b> instance. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_NativeObjectReference(void *obj)](#oh_nativewindow_nativeobjectreference) | Adds the reference count of a native object. This interface needs to be used in conjunction with <b>OH_NativeWindow_NativeObjectUnreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_NativeObjectUnreference(void *obj)](#oh_nativewindow_nativeobjectunreference) | Decreases the reference count of a native object and, when the reference count reaches 0, destroys this object. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_GetNativeObjectMagic(void *obj)](#oh_nativewindow_getnativeobjectmagic) | Obtains the magic ID of a native object. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_NativeWindowSetScalingMode(OHNativeWindow *window, uint32_t sequence, OHScalingMode scalingMode)](#oh_nativewindow_nativewindowsetscalingmode) | Sets scalingMode of a native window.(Deprecated in API10) |
| [int32_t OH_NativeWindow_NativeWindowSetMetaData(OHNativeWindow *window, uint32_t sequence, int32_t size, const OHHDRMetaData *metaData)](#oh_nativewindow_nativewindowsetmetadata) | Sets metaData of a native window.(Deprecated in API10) |
| [int32_t OH_NativeWindow_NativeWindowSetMetaDataSet(OHNativeWindow *window, uint32_t sequence, OHHDRMetadataKey key, int32_t size, const uint8_t *metaData)](#oh_nativewindow_nativewindowsetmetadataset) | Sets metaDataSet of a native window.(Deprecated in API10) |
| [int32_t OH_NativeWindow_NativeWindowSetTunnelHandle(OHNativeWindow *window, const OHExtDataHandle *handle)](#oh_nativewindow_nativewindowsettunnelhandle) | Sets tunnel handle of a native window.(Deprecated in API10) |
| [int32_t OH_NativeWindow_NativeWindowAttachBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)](#oh_nativewindow_nativewindowattachbuffer) | Attach a buffer to an <b>OHNativeWindow</b> instance. This interface needs to be used in conjunction with <b>OH_NativeWindow_NativeWindowDetachBuffer</b>, otherwise buffer management will be chaotic. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_NativeWindowDetachBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)](#oh_nativewindow_nativewindowdetachbuffer) | Detach a buffer from an <b>OHNativeWindow</b> instance. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_GetSurfaceId(OHNativeWindow *window, uint64_t *surfaceId)](#oh_nativewindow_getsurfaceid) | Get surfaceId from native window. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_CreateNativeWindowFromSurfaceId(uint64_t surfaceId, OHNativeWindow **window)](#oh_nativewindow_createnativewindowfromsurfaceid) | Creates an <b>OHNativeWindow</b> instance. This interface needs to be used in conjunction with <b>OH_NativeWindow_DestroyNativeWindow</b>, otherwise memory leaks will occur. If there is a concurrent destroy OHNativeWindow, you need to add once and decrement once to the OHNativeWindow reference count through <b>OH_NativeWindow_NativeObjectReference</b> and <b>OH_NativeWindow_NativeObjectUnreference</b>. If the surface obtained through surfaceId is created in this process, the surface cannot be obtained across processes. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_NativeWindowSetScalingModeV2(OHNativeWindow *window, OHScalingModeV2 scalingMode)](#oh_nativewindow_nativewindowsetscalingmodev2) | Sets scalingMode of a native window. This interface is a non-thread-safe type interface. |
| [void OH_NativeWindow_SetBufferHold(OHNativeWindow *window)](#oh_nativewindow_setbufferhold) | Set native window buffer hold. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_WriteToParcel(OHNativeWindow *window, OHIPCParcel *parcel)](#oh_nativewindow_writetoparcel) | Write an OHNativeWindow to an OHIPCParcel. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_ReadFromParcel(OHIPCParcel *parcel, OHNativeWindow **window)](#oh_nativewindow_readfromparcel) | Read an OHNativeWindow from an OHIPCParcel. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_GetLastFlushedBufferV2(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd, float matrix[16])](#oh_nativewindow_getlastflushedbufferv2) | Get the last flushed <b>OHNativeWindowBuffer</b> from an <b>OHNativeWindow</b> instance. When the fenceFd is used up, you need to close it. This interface needs to be used in conjunction with <b>OH_NativeWindow_NativeObjectUnreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_SetColorSpace(OHNativeWindow *window, OH_NativeBuffer_ColorSpace colorSpace)](#oh_nativewindow_setcolorspace) | Set the color space of the native window. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_GetColorSpace(OHNativeWindow *window, OH_NativeBuffer_ColorSpace *colorSpace)](#oh_nativewindow_getcolorspace) | Get the color space of the native window. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_SetMetadataValue(OHNativeWindow *window, OH_NativeBuffer_MetadataKey metadataKey, int32_t size, uint8_t *metadata)](#oh_nativewindow_setmetadatavalue) | Set the metadata type of the native window. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_GetMetadataValue(OHNativeWindow *window, OH_NativeBuffer_MetadataKey metadataKey, int32_t *size, uint8_t **metadata)](#oh_nativewindow_getmetadatavalue) | Set the metadata type of the native window. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_CleanCache(OHNativeWindow *window)](#oh_nativewindow_cleancache) | Clean all <b>OHNativeWindowBuffer</b> caches of this <b>OHNativeWindow</b> This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_PreAllocBuffers(OHNativeWindow *window, uint32_t allocBufferCnt)](#oh_nativewindow_preallocbuffers) | PreAlloc <b>OHNativeWindowBuffer</b> of this <b>OHNativeWindow</b> This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_LockBuffer(OHNativeWindow* window, Region region, OHNativeWindowBuffer** buffer)](#oh_nativewindow_lockbuffer) | Requests an <b>OHNativeWindowBuffer</b> through an <b>OHNativeWindow</b> instance for content production, and lock the <b>OHNativeWindowBuffer</b>, the interface needs to be paired with <b>OH_NativeWindow_UnlockAndFlushBuffer</b> for use, after lock, it must be unlocked in order to relock, repeatedly lock or unlock will return an illegal operation error code, the interface supports rendering images directly through memory read and write on the CPU. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_UnlockAndFlushBuffer(OHNativeWindow* window)](#oh_nativewindow_unlockandflushbuffer) | Flushes the <b>OHNativeWindowBuffer</b> filled with the content to the buffer queue through an <b>OHNativeWindow</b> instance for content consumption, and unlock the <b>OHNativeWindowBuffer</b>. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_Set3DMetadataValue(OHNativeWindow *window, OH_NativeBuffer_3D_MetadataKey metadataKey, int32_t size, uint8_t *metadata)](#oh_nativewindow_set3dmetadatavalue) | Set the 3D metadata of the native window. This interface is a non-thread-safe type interface. |
| [int32_t OH_NativeWindow_Get3DMetadataValue(OHNativeWindow *window, OH_NativeBuffer_3D_MetadataKey metadataKey, int32_t *size, uint8_t **metadata)](#oh_nativewindow_get3dmetadatavalue) | Get the 3D metadata of the native window. This interface is a non-thread-safe type interface. |

## Enum type description

### NativeWindowOperation

```c
enum NativeWindowOperation
```

**Description**

Indicates the operation code in the function OH_NativeWindow_NativeWindowHandleOpt.

**Since**: 8

| Enum item | Description |
| -- | -- |
| SET_BUFFER_GEOMETRY | set native window buffer geometry, variable parameter in function is [in] int32_t width, [in] int32_t height |
| GET_BUFFER_GEOMETRY | get native window buffer geometry, variable parameter in function is [out] int32_t *height, [out] int32_t *width |
| GET_FORMAT | get native window buffer format, variable parameter in function is [out] int32_t *format, the enumeration value refers to {@link OH_NativeBuffer_Format}. |
| SET_FORMAT | set native window buffer format, variable parameter in function is [in] int32_t format, the enumeration value refers to {@link OH_NativeBuffer_Format}. |
| GET_USAGE | get native window buffer usage, variable parameter in function is [out] uint64_t *usage, the enumeration value refers to {@link OH_NativeBuffer_Usage}. |
| SET_USAGE | set native window buffer usage, variable parameter in function is [in] uint64_t usage, the enumeration value refers to {@link OH_NativeBuffer_Usage}. |
| SET_STRIDE |  |
| GET_STRIDE |  |
| SET_SWAP_INTERVAL | set native window buffer swap interval, variable parameter in function is [in] int32_t interval. |
| GET_SWAP_INTERVAL | get native window buffer swap interval, variable parameter in function is [out] int32_t *interval. |
| SET_TIMEOUT | set the timeout in milliseconds when the native window requests a buffer, the default value is 3000 milliseconds when not set, variable parameter in function is [in] int32_t timeout, in milliseconds. |
| GET_TIMEOUT | get the timeout in milliseconds when the native window requests a buffer, the default value is 3000 milliseconds when not set, variable parameter in function is [out] int32_t *timeout, in milliseconds. |
| SET_COLOR_GAMUT | set native window buffer colorGamut, variable parameter in function is [in] int32_t colorGamut, the enumeration value refers to {@link OH_NativeBuffer_ColorGamut}. |
| GET_COLOR_GAMUT | get native window buffer colorGamut, variable parameter in function is [out] int32_t *colorGamut, the enumeration value refers to {@link OH_NativeBuffer_ColorGamut}. |
| SET_TRANSFORM | set native window buffer transform, variable parameter in function is [in] int32_t transform, the enumeration value refers to {@link OH_NativeBuffer_TransformType}. |
| GET_TRANSFORM | get native window buffer transform, variable parameter in function is [out] int32_t *transform, the enumeration value refers to {@link OH_NativeBuffer_TransformType}. |
| SET_UI_TIMESTAMP | set native window buffer uiTimestamp, variable parameter in function is [in] uint64_t uiTimestamp. |
| GET_BUFFERQUEUE_SIZE |  |
| SET_SOURCE_TYPE |  |
| GET_SOURCE_TYPE |  |
| SET_APP_FRAMEWORK_TYPE |  |
| GET_APP_FRAMEWORK_TYPE |  |
| SET_HDR_WHITE_POINT_BRIGHTNESS |  |
| SET_SDR_WHITE_POINT_BRIGHTNESS |  |
| SET_DESIRED_PRESENT_TIMESTAMP = 24 |  |
| OH_NATIVEWINDOW_SET_DMABUFFER_NAME = 25 |  |

### OHScalingMode

```c
enum OHScalingMode
```

**Description**

Indicates Scaling Mode.

**Since**: 9

**Deprecated**: 10

**Replaced by**: OHScalingModeV2

| Enum item | Description |
| -- | -- |
| OH_SCALING_MODE_FREEZE = 0 | the window content is not updated until a buffer of the window size is received |
| OH_SCALING_MODE_SCALE_TO_WINDOW | the buffer is scaled in two dimensions to match the window size |
| OH_SCALING_MODE_SCALE_CROP | the buffer is uniformly scaled so that the smaller size of the buffer matches the window size |
| OH_SCALING_MODE_NO_SCALE_CROP | the window is clipped to the size of the buffer's clipping rectangle pixels outside the clipping rectangle are considered fully transparent. |

### OHScalingModeV2

```c
enum OHScalingModeV2
```

**Description**

Indicates Scaling Mode.

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_SCALING_MODE_FREEZE_V2 = 0 | the window content is not updated until a buffer of the window size is received |
| OH_SCALING_MODE_SCALE_TO_WINDOW_V2 | the buffer is scaled in two dimensions to match the window size |
| OH_SCALING_MODE_SCALE_CROP_V2 | the buffer is uniformly scaled so that the smaller size of the buffer matches the window size |
| OH_SCALING_MODE_NO_SCALE_CROP_V2 | the window is clipped to the size of the buffer's clipping rectangle pixels outside the clipping rectangle are considered fully transparent. |
| OH_SCALING_MODE_SCALE_FIT_V2 | Adapt to the buffer and scale proportionally to the buffer size. Prioritize displaying all buffer content. If the size is not the same as the window size, fill the unfilled area of the window with a background color. |

### OHHDRMetadataKey

```c
enum OHHDRMetadataKey
```

**Description**

Enumerates the HDR metadata keys.

**Since**: 9

**Deprecated**: 10

| Enum item | Description |
| -- | -- |

### OHSurfaceSource

```c
enum OHSurfaceSource
```

**Description**

Indicates the source type of surface.

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_SURFACE_SOURCE_DEFAULT = 0 | the default source type of surface. |
| OH_SURFACE_SOURCE_UI | the surface is created by ui. |
| OH_SURFACE_SOURCE_GAME | the surface is created by game. |
| OH_SURFACE_SOURCE_CAMERA | the surface is created by camera. |
| OH_SURFACE_SOURCE_VIDEO | the surface is created by video. |


## Function description

### OH_NativeWindow_CreateNativeWindow()

```c
OHNativeWindow* OH_NativeWindow_CreateNativeWindow(void* pSurface)
```

**Description**

Creates a <b>OHNativeWindow</b> instance. A new <b>OHNativeWindow</b> instance is created each time this function is called.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Deprecated**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| void* pSurface | Indicates the pointer to a <b>ProduceSurface</b>. The type is a pointer to <b>sptr<OHOS::Surface></b>. |

**Returns**:

| Type | Description |
| -- | -- |
| [OHNativeWindow*](capi-nativewindow-nativewindow.md) | Returns the pointer to the <b>OHNativeWindow</b> instance created. |

### OH_NativeWindow_DestroyNativeWindow()

```c
void OH_NativeWindow_DestroyNativeWindow(OHNativeWindow* window)
```

**Description**

Decreases the reference count of a <b>OHNativeWindow</b> instance by 1, and when the reference count reaches 0, destroys the instance. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md)* window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |

### OH_NativeWindow_CreateNativeWindowBufferFromSurfaceBuffer()

```c
OHNativeWindowBuffer* OH_NativeWindow_CreateNativeWindowBufferFromSurfaceBuffer(void* pSurfaceBuffer)
```

**Description**

Creates a <b>OHNativeWindowBuffer</b> instance. A new <b>OHNativeWindowBuffer</b> instance is created each time this function is called.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Deprecated**: 12

**Replaced by**: OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer

**Parameters**:

| Parameter | Description |
| -- | -- |
| void* pSurfaceBuffer | Indicates the pointer to a produce buffer. The type is <b>sptr<OHOS::SurfaceBuffer></b>. |

**Returns**:

| Type | Description |
| -- | -- |
| [OHNativeWindowBuffer*](capi-nativewindow-nativewindowbuffer.md) | Returns the pointer to the <b>OHNativeWindowBuffer</b> instance created. |

### OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer()

```c
OHNativeWindowBuffer* OH_NativeWindow_CreateNativeWindowBufferFromNativeBuffer(OH_NativeBuffer* nativeBuffer)
```

**Description**

Creates a <b>OHNativeWindowBuffer</b> instance. A new <b>OHNativeWindowBuffer</b> instance is created each time this function is called. This interface needs to be used in conjunction with <b>OH_NativeWindow_DestroyNativeWindowBuffer</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeBuffer](capi-nativewindow-oh-nativebuffer.md)* nativeBuffer | Indicates the pointer to a native buffer. The type is <b>OH_NativeBuffer*</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| [OHNativeWindowBuffer*](capi-nativewindow-nativewindowbuffer.md) | Returns the pointer to the <b>OHNativeWindowBuffer</b> instance created. |

### OH_NativeWindow_DestroyNativeWindowBuffer()

```c
void OH_NativeWindow_DestroyNativeWindowBuffer(OHNativeWindowBuffer* buffer)
```

**Description**

Decreases the reference count of a <b>OHNativeWindowBuffer</b> instance by 1 and, when the reference count reaches 0, destroys the instance. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md)* buffer | Indicates the pointer to a <b>OHNativeWindowBuffer</b> instance. |

### OH_NativeWindow_NativeWindowRequestBuffer()

```c
int32_t OH_NativeWindow_NativeWindowRequestBuffer(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd)
```

**Description**

Requests a <b>OHNativeWindowBuffer</b> through a <b>OHNativeWindow</b> instance for content production. Before calling this interface, you need to set the width and height of <b>OHNativeWindow</b> through <b>SET_BUFFER_GEOMETRY</b>. This interface needs to be used in conjunction with <b>OH_NativeWindow_NativeWindowFlushBuffer</b>, otherwise buffer will be exhausted. When the fenceFd is used up, you need to close it. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) **buffer | Indicates the double pointer to a <b>OHNativeWindowBuffer</b> instance. |
| int *fenceFd | Indicates the pointer to a file descriptor handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_NativeWindowFlushBuffer()

```c
int32_t OH_NativeWindow_NativeWindowFlushBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer, int fenceFd, Region region)
```

**Description**

Flushes the <b>OHNativeWindowBuffer</b> filled with the content to the buffer queue through a <b>OHNativeWindow</b> instance for content consumption. The fenceFd will be close by system. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | Indicates the pointer to a <b>OHNativeWindowBuffer</b> instance. |
| int fenceFd | Indicates a file descriptor handle, which is used for timing synchronization. |
| [Region](capi-nativewindow-region.md) region | Indicates a dirty region where content is updated. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_GetLastFlushedBuffer()

```c
int32_t OH_NativeWindow_GetLastFlushedBuffer(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd, float matrix[16])
```

**Description**

Get the last flushed <b>OHNativeWindowBuffer</b> from a <b>OHNativeWindow</b> instance.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 11

**Deprecated**: 12

**Replaced by**: OH_NativeWindow_GetLastFlushedBufferV2

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) **buffer | Indicates the pointer to a <b>OHNativeWindowBuffer</b> pointer. |
| int *fenceFd | Indicates the pointer to a file descriptor handle. |
| float matrix[16] | Indicates the retrieved 4*4 transform matrix. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_NativeWindowAbortBuffer()

```c
int32_t OH_NativeWindow_NativeWindowAbortBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)
```

**Description**

Returns the <b>OHNativeWindowBuffer</b> to the buffer queue through a <b>OHNativeWindow</b> instance, without filling in any content. The <b>OHNativeWindowBuffer</b> can be used for another request. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | Indicates the pointer to a <b>OHNativeWindowBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_NativeWindowHandleOpt()

```c
int32_t OH_NativeWindow_NativeWindowHandleOpt(OHNativeWindow *window, int code, ...)
```

**Description**

Sets or obtains the attributes of a native window, including the width, height, and content format. This interface is a non-thread-safe type interface.<br> <p><strong>API Note</strong><br> <strong>Performance Note</strong> <p>By default, the window buffer in the current operating system is accessed via the CPU. If an application does not need to access the window buffer data using the CPU, it can proactively disable CPU access to enhance energy efficiency and reduce power consumption. </p> <p>For details about how to optimize power consumption for data read/write operations in data buffers, see [How do I proactively disable CPU access to window buffers to reduce power consumption?]{@link https://developer.huawei.com/consumer/en/doc/harmonyos-faqs/faqs-arkgraphics-2d-14}.</p> </p>

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| int code | Indicates the operation code, pointer to <b>NativeWindowOperation</b>. |
| [](capi-nativewindow-nativewindow.md).[](capi-nativewindow-nativewindow.md).[](capi-nativewindow-nativewindow.md).[](capi-nativewindow-nativewindow.md) | variable parameter, must correspond to code one-to-one. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_GetBufferHandleFromNative()

```c
BufferHandle *OH_NativeWindow_GetBufferHandleFromNative(OHNativeWindowBuffer *buffer)
```

**Description**

Obtains the pointer to a <b>BufferHandle</b> of a <b>OHNativeWindowBuffer</b> instance. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | Indicates the pointer to a <b>OHNativeWindowBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| BufferHandle * | Returns the pointer to the <b>BufferHandle</b> instance obtained. |

### OH_NativeWindow_NativeObjectReference()

```c
int32_t OH_NativeWindow_NativeObjectReference(void *obj)
```

**Description**

Adds the reference count of a native object. This interface needs to be used in conjunction with <b>OH_NativeWindow_NativeObjectUnreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *obj | Indicates the pointer to a <b>OHNativeWindow</b> or <b>OHNativeWindowBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_NativeObjectUnreference()

```c
int32_t OH_NativeWindow_NativeObjectUnreference(void *obj)
```

**Description**

Decreases the reference count of a native object and, when the reference count reaches 0, destroys this object. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *obj | Indicates the pointer to a <b>OHNativeWindow</b> or <b>OHNativeWindowBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_GetNativeObjectMagic()

```c
int32_t OH_NativeWindow_GetNativeObjectMagic(void *obj)
```

**Description**

Obtains the magic ID of a native object. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *obj | Indicates the pointer to a <b>OHNativeWindow</b> or <b>OHNativeWindowBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the magic ID, which is unique for each native object. |

### OH_NativeWindow_NativeWindowSetScalingMode()

```c
int32_t OH_NativeWindow_NativeWindowSetScalingMode(OHNativeWindow *window, uint32_t sequence, OHScalingMode scalingMode)
```

**Description**

Sets scalingMode of a native window.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 9

**Deprecated**: 10

**Replaced by**: OH_NativeWindow_NativeWindowSetScalingModeV2

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| uint32_t sequence | Indicates the sequence to a produce buffer. |
| [OHScalingMode](capi-external-window-h.md#ohscalingmode) scalingMode | Indicates the enum value to <b>OHScalingMode</b> |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_NativeWindowSetMetaData()

```c
int32_t OH_NativeWindow_NativeWindowSetMetaData(OHNativeWindow *window, uint32_t sequence, int32_t size, const OHHDRMetaData *metaData)
```

**Description**

Sets metaData of a native window.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 9

**Deprecated**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| uint32_t sequence | Indicates the sequence to a produce buffer. |
| int32_t size | Indicates the size of a <b>OHHDRMetaData</b> vector. |
| [const OHHDRMetaData](capi-nativewindow-ohhdrmetadata.md) *metaData | Indicates the pointer to a <b>OHHDRMetaData</b> vector. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_NativeWindowSetMetaDataSet()

```c
int32_t OH_NativeWindow_NativeWindowSetMetaDataSet(OHNativeWindow *window, uint32_t sequence, OHHDRMetadataKey key, int32_t size, const uint8_t *metaData)
```

**Description**

Sets metaDataSet of a native window.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 9

**Deprecated**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| uint32_t sequence | Indicates the sequence to a produce buffer. |
| [OHHDRMetadataKey](capi-external-window-h.md#ohhdrmetadatakey) key | Indicates the enum value to <b>OHHDRMetadataKey</b> |
| int32_t size | Indicates the size of a uint8_t vector. |
| metaDate | Indicates the pointer to a uint8_t vector. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_NativeWindowSetTunnelHandle()

```c
int32_t OH_NativeWindow_NativeWindowSetTunnelHandle(OHNativeWindow *window, const OHExtDataHandle *handle)
```

**Description**

Sets tunnel handle of a native window.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 9

**Deprecated**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| [const OHExtDataHandle](capi-nativewindow-ohextdatahandle.md) *handle | Indicates the pointer to a <b>OHExtDataHandle</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_NativeWindowAttachBuffer()

```c
int32_t OH_NativeWindow_NativeWindowAttachBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)
```

**Description**

Attach a buffer to an <b>OHNativeWindow</b> instance. This interface needs to be used in conjunction with <b>OH_NativeWindow_NativeWindowDetachBuffer</b>, otherwise buffer management will be chaotic. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to an <b>OHNativeWindow</b> instance. |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | Indicates the pointer to a <b>OHNativeWindowBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_NativeWindowDetachBuffer()

```c
int32_t OH_NativeWindow_NativeWindowDetachBuffer(OHNativeWindow *window, OHNativeWindowBuffer *buffer)
```

**Description**

Detach a buffer from an <b>OHNativeWindow</b> instance. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to an <b>OHNativeWindow</b> instance. |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) *buffer | Indicates the pointer to a <b>OHNativeWindowBuffer</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_GetSurfaceId()

```c
int32_t OH_NativeWindow_GetSurfaceId(OHNativeWindow *window, uint64_t *surfaceId)
```

**Description**

Get surfaceId from native window. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to an <b>OHNativeWindow</b> instance. |
| uint64_t *surfaceId | Indicates the pointer to a surfaceId. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_CreateNativeWindowFromSurfaceId()

```c
int32_t OH_NativeWindow_CreateNativeWindowFromSurfaceId(uint64_t surfaceId, OHNativeWindow **window)
```

**Description**

Creates an <b>OHNativeWindow</b> instance. This interface needs to be used in conjunction with <b>OH_NativeWindow_DestroyNativeWindow</b>, otherwise memory leaks will occur. If there is a concurrent destroy OHNativeWindow, you need to add once and decrement once to the OHNativeWindow reference count through <b>OH_NativeWindow_NativeObjectReference</b> and <b>OH_NativeWindow_NativeObjectUnreference</b>. If the surface obtained through surfaceId is created in this process, the surface cannot be obtained across processes. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t surfaceId | Indicates the surfaceId to a surface. |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) **window | indicates the pointer to an <b>OHNativeWindow</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is Success, otherwise, failed. |

### OH_NativeWindow_NativeWindowSetScalingModeV2()

```c
int32_t OH_NativeWindow_NativeWindowSetScalingModeV2(OHNativeWindow *window, OHScalingModeV2 scalingMode)
```

**Description**

Sets scalingMode of a native window. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | indicates the pointer to an <b>OHNativeWindow</b> instance. |
| [OHScalingModeV2](capi-external-window-h.md#ohscalingmodev2) scalingMode | Indicates the enum value to <b>OHScalingModeV2</b> |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is Success, otherwise, failed. |

### OH_NativeWindow_SetBufferHold()

```c
void OH_NativeWindow_SetBufferHold(OHNativeWindow *window)
```

**Description**

Set native window buffer hold. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to an <b>OHNativeWindow</b> instance. |

### OH_NativeWindow_WriteToParcel()

```c
int32_t OH_NativeWindow_WriteToParcel(OHNativeWindow *window, OHIPCParcel *parcel)
```

**Description**

Write an OHNativeWindow to an OHIPCParcel. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to an <b>OHNativeWindow</b> instance. |
| [OHIPCParcel](capi-nativewindow-ohipcparcel.md) *parcel | Indicates the pointer to an <b>OHIPCParcel</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - parcel is NULL or window is NULL. |

### OH_NativeWindow_ReadFromParcel()

```c
int32_t OH_NativeWindow_ReadFromParcel(OHIPCParcel *parcel, OHNativeWindow **window)
```

**Description**

Read an OHNativeWindow from an OHIPCParcel. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHIPCParcel](capi-nativewindow-ohipcparcel.md) *parcel | Indicates the pointer to an <b>OHIPCParcel</b> instance. |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) **window | Indicates the pointer to an <b>OHNativeWindow</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - parcel is NULL or parcel does not contain the window. |

### OH_NativeWindow_GetLastFlushedBufferV2()

```c
int32_t OH_NativeWindow_GetLastFlushedBufferV2(OHNativeWindow *window, OHNativeWindowBuffer **buffer, int *fenceFd, float matrix[16])
```

**Description**

Get the last flushed <b>OHNativeWindowBuffer</b> from an <b>OHNativeWindow</b> instance. When the fenceFd is used up, you need to close it. This interface needs to be used in conjunction with <b>OH_NativeWindow_NativeObjectUnreference</b>, otherwise memory leaks will occur. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to an <b>OHNativeWindow</b> instance. |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md) **buffer | Indicates the pointer to an <b>OHNativeWindowBuffer</b> pointer. |
| int *fenceFd | Indicates the pointer to a file descriptor handle. |
| float matrix[16] | Indicates the retrieved 4*4 transform matrix. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window is NULL or buffer is NULL or fenceFd is NULL.<br>    {@link NATIVE_ERROR_BUFFER_STATE_INVALID} 41207000 - buffer state is wrong. |

### OH_NativeWindow_SetColorSpace()

```c
int32_t OH_NativeWindow_SetColorSpace(OHNativeWindow *window, OH_NativeBuffer_ColorSpace colorSpace)
```

**Description**

Set the color space of the native window. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| OH_NativeBuffer_ColorSpace colorSpace | Indicates the color space of native window, see <b>OH_NativeBuffer_ColorSpace</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window is NULL.<br>    {@link NATIVE_ERROR_BUFFER_STATE_INVALID} 41207000 - Incorrect colorSpace state. |

### OH_NativeWindow_GetColorSpace()

```c
int32_t OH_NativeWindow_GetColorSpace(OHNativeWindow *window, OH_NativeBuffer_ColorSpace *colorSpace)
```

**Description**

Get the color space of the native window. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| OH_NativeBuffer_ColorSpace *colorSpace | Indicates the color space of native window, see <b>OH_NativeBuffer_ColorSpace</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window is NULL.<br>    {@link NATIVE_ERROR_BUFFER_STATE_INVALID} 41207000 - Incorrect colorSpace state. |

### OH_NativeWindow_SetMetadataValue()

```c
int32_t OH_NativeWindow_SetMetadataValue(OHNativeWindow *window, OH_NativeBuffer_MetadataKey metadataKey, int32_t size, uint8_t *metadata)
```

**Description**

Set the metadata type of the native window. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| OH_NativeBuffer_MetadataKey metadataKey | Indicates the metadata type of native window, see <b>OH_NativeBuffer_MetadataKey</b>. |
| int32_t size | Indicates the size of a uint8_t vector. |
| uint8_t *metadata | Indicates the pointer to a uint8_t vector. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window or metadata is NULL.<br>    {@link NATIVE_ERROR_BUFFER_STATE_INVALID} 41207000 - Incorrect metadata state.<br>    {@link NATIVE_ERROR_UNSUPPORTED} 50102000 - Unsupported metadata key. |

### OH_NativeWindow_GetMetadataValue()

```c
int32_t OH_NativeWindow_GetMetadataValue(OHNativeWindow *window, OH_NativeBuffer_MetadataKey metadataKey, int32_t *size, uint8_t **metadata)
```

**Description**

Set the metadata type of the native window. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| OH_NativeBuffer_MetadataKey metadataKey | Indicates the metadata type of native window, see <b>OH_NativeBuffer_MetadataKey</b>. |
| int32_t *size | Indicates the size of a uint8_t vector. |
| uint8_t **metadata | Indicates the pointer to a uint8_t vector. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window, metadata, or size is NULL.<br>    {@link NATIVE_ERROR_BUFFER_STATE_INVALID} 41207000 - Incorrect metadata state.<br>    {@link NATIVE_ERROR_UNSUPPORTED} 50102000 - Unsupported metadata key. |

### OH_NativeWindow_CleanCache()

```c
int32_t OH_NativeWindow_CleanCache(OHNativeWindow *window)
```

**Description**

Clean all <b>OHNativeWindowBuffer</b> caches of this <b>OHNativeWindow</b> This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window is NULL.<br>    {@link NATIVE_ERROR_CONSUMER_DISCONNECTED} 41211000 - the consumer is disconnected.<br>    {@link NATIVE_ERROR_BINDER_ERROR} 50401000 - ipc send failed. |

### OH_NativeWindow_PreAllocBuffers()

```c
int32_t OH_NativeWindow_PreAllocBuffers(OHNativeWindow *window, uint32_t allocBufferCnt)
```

**Description**

PreAlloc <b>OHNativeWindowBuffer</b> of this <b>OHNativeWindow</b> This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| uint32_t allocBufferCnt | Indicates the count of <b>OHNativeWindowBuffers</b>. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns an error code, 0 is success, otherwise, failed. |

### OH_NativeWindow_LockBuffer()

```c
int32_t OH_NativeWindow_LockBuffer(OHNativeWindow* window, Region region, OHNativeWindowBuffer** buffer)
```

**Description**

Requests an <b>OHNativeWindowBuffer</b> through an <b>OHNativeWindow</b> instance for content production, and lock the <b>OHNativeWindowBuffer</b>, the interface needs to be paired with <b>OH_NativeWindow_UnlockAndFlushBuffer</b> for use, after lock, it must be unlocked in order to relock, repeatedly lock or unlock will return an illegal operation error code, the interface supports rendering images directly through memory read and write on the CPU. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md)* window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| [Region](capi-nativewindow-region.md) region | Indicates the info of the dirty region. |
| [OHNativeWindowBuffer](capi-nativewindow-nativewindowbuffer.md)** buffer | Indicates the pointer to an <b>OHNativeWindowBuffer</b> pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window or buffer is NULL.<br>    {@link NATIVE_ERROR_UNKNOWN} 50002000 - surface of window is NULL. |

### OH_NativeWindow_UnlockAndFlushBuffer()

```c
int32_t OH_NativeWindow_UnlockAndFlushBuffer(OHNativeWindow* window)
```

**Description**

Flushes the <b>OHNativeWindowBuffer</b> filled with the content to the buffer queue through an <b>OHNativeWindow</b> instance for content consumption, and unlock the <b>OHNativeWindowBuffer</b>. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md)* window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window is NULL.<br>    {@link NATIVE_ERROR_UNKNOWN} 50002000 - surface of window is NULL. |

### OH_NativeWindow_Set3DMetadataValue()

```c
int32_t OH_NativeWindow_Set3DMetadataValue(OHNativeWindow *window, OH_NativeBuffer_3D_MetadataKey metadataKey, int32_t size, uint8_t *metadata)
```

**Description**

Set the 3D metadata of the native window. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| OH_NativeBuffer_3D_MetadataKey metadataKey | Indicates the 3D metadata type of native window, see <b>OH_NativeBuffer_3D_MetadataKey</b>. |
| int32_t size | Indicates the size of a uint8_t vector. |
| uint8_t *metadata | Indicates the pointer to a uint8_t vector. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window or metadata is NULL.<br>    {@link NATIVE_ERROR_UNKNOWN} 50002000 - set 3D metadata failed.<br>    {@link NATIVE_ERROR_UNSUPPORTED} 50102000 - unsupported metadata key. |

### OH_NativeWindow_Get3DMetadataValue()

```c
int32_t OH_NativeWindow_Get3DMetadataValue(OHNativeWindow *window, OH_NativeBuffer_3D_MetadataKey metadataKey, int32_t *size, uint8_t **metadata)
```

**Description**

Get the 3D metadata of the native window. This interface is a non-thread-safe type interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OHNativeWindow](capi-nativewindow-nativewindow.md) *window | Indicates the pointer to a <b>OHNativeWindow</b> instance. |
| OH_NativeBuffer_3D_MetadataKey metadataKey | Indicates the 3D metadata type of native window, see <b>OH_NativeBuffer_3D_MetadataKey</b>. |
| int32_t *size | Indicates the size of a uint8_t vector. |
| uint8_t **metadata | Indicates the pointer to a uint8_t vector. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - window, metadata, or size is NULL.<br>    {@link NATIVE_ERROR_UNKNOWN} 50002000 - copy or allocate memory failed, otherwise get 3D metadata failed.<br>    {@link NATIVE_ERROR_UNSUPPORTED} 50102000 - unsupported metadata key. |


