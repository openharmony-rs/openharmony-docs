# native_vsync.h

## Overview

Defines the functions for obtaining and using a native vsync.

**Library**: libnative_vsync.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 9

**Related module**: [NativeVsync](capi-nativevsync.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NativeVSync_ExpectedRateRange](capi-nativevsync-oh-nativevsync-expectedraterange.md) | OH_NativeVSync_ExpectedRateRange | Defines the expected frame rate range struct. |

### Function

| Name | Description |
| -- | -- |
| [OH_NativeVSync* OH_NativeVSync_Create(const char* name, unsigned int length)](#oh_nativevsync_create) | Creates a <b>NativeVsync</b> instance. A new <b>NativeVsync</b> instance is created each time this function is called. |
| [void OH_NativeVSync_Destroy(OH_NativeVSync* nativeVsync)](#oh_nativevsync_destroy) | Destroys an <b>OH_NativeVSync</b> instance. Once the <b>OH_NativeVSync</b> pointer is destroyed, it must not be used to prevent dangling pointer problems. Pay special attention to the management of the <b>OH_NativeVSync</b> pointer in concurrent multithreaded scenarios. |
| [OH_NativeVSync* OH_NativeVSync_Create_ForAssociatedWindow(uint64_t windowID, const char* name, unsigned int length)](#oh_nativevsync_create_forassociatedwindow) | Creates a <b>NativeVsync</b> instance. A new <b>NativeVsync</b> instance is created each time this function is called. |
| [int OH_NativeVSync_RequestFrame(OH_NativeVSync* nativeVsync, OH_NativeVSync_FrameCallback callback, void* data)](#oh_nativevsync_requestframe) | Request next vsync with callback. If you call this interface multiple times in one frame, it will only call the last callback. |
| [int OH_NativeVSync_RequestFrameWithMultiCallback(OH_NativeVSync* nativeVsync, OH_NativeVSync_FrameCallback callback, void* data)](#oh_nativevsync_requestframewithmulticallback) | Request next vsync with callback. If this function is called multiple times in one vsync period, all these callbacks and dataset will be called. |
| [int OH_NativeVSync_GetPeriod(OH_NativeVSync* nativeVsync, long long* period)](#oh_nativevsync_getperiod) | Obtains the VSync period. The VSync period is refreshed only when the <b>OH_NativeVSync_FrameCallback</b> callback is received following a request for a VSync signal via <b>OH_NativeVSync_RequestFrame</b>. To obtain the VSync period for the first time using this function, you need to call <b>OH_NativeVSync_RequestFrame</b> to request a VSync signal. Once the <b>OH_NativeVSync_FrameCallback</b> callback is received, the vsync period can be obtained. |
| [int OH_NativeVSync_DVSyncSwitch(OH_NativeVSync* nativeVsync, bool enable)](#oh_nativevsync_dvsyncswitch) | Enables DVSync to improve the smoothness of self-drawing animations. DVSync, short for Decoupled VSync, is a frame timing management policy that is decoupled from the hardware's VSync. DVSync drives the early rendering of upcoming animation frames by sending VSync signals with future timestamps. These frames are stored in a frame buffer queue. This helps DVSync reduce potential frame drop and therefore enhances the smoothness of animations. DVSync requires free self-drawing frame buffers to store these pre-rendered animation frames. Therefore, you must ensure that at least one free frame buffer is available. Otherwise, do not enable DVSync. After DVSync is enabled, you must correctly respond to the early VSync signals and request the subsequent VSync after the animation frame associated with the previous VSync is complete. In addition, the self-drawing frames must carry timestamps that align with VSync. After the animation ends, disable DVSync. Only phones and tablets support DVSync. On a platform that does not support DVSync or if another application has enabled DVSync, the attempt to enable it will not take effect, and the application still receives normal VSync signals. |
| [int OH_NativeVSync_SetExpectedFrameRateRange(OH_NativeVSync* nativeVsync, OH_NativeVSync_ExpectedRateRange* range)](#oh_nativevsync_setexpectedframeraterange) | Set vsync expected frame rate range. |

## Function description

### OH_NativeVSync_Create()

```c
OH_NativeVSync* OH_NativeVSync_Create(const char* name, unsigned int length)
```

**Description**

Creates a <b>NativeVsync</b> instance. A new <b>NativeVsync</b> instance is created each time this function is called.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* name | Indicates the vsync connection name. |
| unsigned int length | Indicates the name's length. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NativeVSync* | Returns the pointer to the <b>NativeVsync</b> instance created. |

### OH_NativeVSync_Destroy()

```c
void OH_NativeVSync_Destroy(OH_NativeVSync* nativeVsync)
```

**Description**

Destroys an <b>OH_NativeVSync</b> instance. Once the <b>OH_NativeVSync</b> pointer is destroyed, it must not be used to prevent dangling pointer problems. Pay special attention to the management of the <b>OH_NativeVSync</b> pointer in concurrent multithreaded scenarios.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeVSync* nativeVsync | Pointer to an <b>OH_NativeVSync</b> instance. |

### OH_NativeVSync_Create_ForAssociatedWindow()

```c
OH_NativeVSync* OH_NativeVSync_Create_ForAssociatedWindow(uint64_t windowID, const char* name, unsigned int length)
```

**Description**

Creates a <b>NativeVsync</b> instance. A new <b>NativeVsync</b> instance is created each time this function is called.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t windowID | Indicates the id of the associated window. |
| const char* name | Indicates the vsync connection name. |
| unsigned int length | Indicates the name's length. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_NativeVSync* | Returns the pointer to the <b>NativeVsync</b> instance created. |

### OH_NativeVSync_RequestFrame()

```c
int OH_NativeVSync_RequestFrame(OH_NativeVSync* nativeVsync, OH_NativeVSync_FrameCallback callback, void* data)
```

**Description**

Request next vsync with callback. If you call this interface multiple times in one frame, it will only call the last callback.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeVSync* nativeVsync | Indicates the pointer to a NativeVsync. |
| OH_NativeVSync_FrameCallback callback | Indicates the OH_NativeVSync_FrameCallback which will be called when next vsync coming. |
| void* data | Indicates data which will be used in callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - the parameter nativeVsync is NULL or callback is NULL.<br>    {@link NATIVE_ERROR_BINDER_ERROR} 50401000 - ipc send failed. |

### OH_NativeVSync_RequestFrameWithMultiCallback()

```c
int OH_NativeVSync_RequestFrameWithMultiCallback(OH_NativeVSync* nativeVsync, OH_NativeVSync_FrameCallback callback, void* data)
```

**Description**

Request next vsync with callback. If this function is called multiple times in one vsync period, all these callbacks and dataset will be called.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeVSync* nativeVsync | Indicates the pointer to a NativeVsync. |
| OH_NativeVSync_FrameCallback callback | Indicates the OH_NativeVSync_FrameCallback which will be called when next vsync coming. |
| void* data | Indicates data which will be used in callback. |

**Returns**:

| Type | Description |
| -- | -- |
| int | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - the parameter nativeVsync is NULL or callback is NULL.<br>    {@link NATIVE_ERROR_BINDER_ERROR} 50401000 - ipc send failed. |

### OH_NativeVSync_GetPeriod()

```c
int OH_NativeVSync_GetPeriod(OH_NativeVSync* nativeVsync, long long* period)
```

**Description**

Obtains the VSync period. The VSync period is refreshed only when the <b>OH_NativeVSync_FrameCallback</b> callback is received following a request for a VSync signal via <b>OH_NativeVSync_RequestFrame</b>. To obtain the VSync period for the first time using this function, you need to call <b>OH_NativeVSync_RequestFrame</b> to request a VSync signal. Once the <b>OH_NativeVSync_FrameCallback</b> callback is received, the vsync period can be obtained.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeVSync* nativeVsync | Indicates the pointer to a NativeVsync. |
| long long* period | Indicates the vsync period. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns int32_t, return value == 0, success, otherwise, failed. |

### OH_NativeVSync_DVSyncSwitch()

```c
int OH_NativeVSync_DVSyncSwitch(OH_NativeVSync* nativeVsync, bool enable)
```

**Description**

Enables DVSync to improve the smoothness of self-drawing animations. DVSync, short for Decoupled VSync, is a frame timing management policy that is decoupled from the hardware's VSync. DVSync drives the early rendering of upcoming animation frames by sending VSync signals with future timestamps. These frames are stored in a frame buffer queue. This helps DVSync reduce potential frame drop and therefore enhances the smoothness of animations. DVSync requires free self-drawing frame buffers to store these pre-rendered animation frames. Therefore, you must ensure that at least one free frame buffer is available. Otherwise, do not enable DVSync. After DVSync is enabled, you must correctly respond to the early VSync signals and request the subsequent VSync after the animation frame associated with the previous VSync is complete. In addition, the self-drawing frames must carry timestamps that align with VSync. After the animation ends, disable DVSync. Only phones and tablets support DVSync. On a platform that does not support DVSync or if another application has enabled DVSync, the attempt to enable it will not take effect, and the application still receives normal VSync signals.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeVSync* nativeVsync | Indicates the pointer to a NativeVsync. |
| bool enable | Whether to enable DVSync.The value true means to enable DVSync, and false means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - the parameter nativeVsync is NULL.<br>    {@link NATIVE_ERROR_BINDER_ERROR} 50401000 - ipc send failed. |

### OH_NativeVSync_SetExpectedFrameRateRange()

```c
int OH_NativeVSync_SetExpectedFrameRateRange(OH_NativeVSync* nativeVsync, OH_NativeVSync_ExpectedRateRange* range)
```

**Description**

Set vsync expected frame rate range.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_NativeVSync* nativeVsync | Indicates the pointer to a NativeVsync. |
| [OH_NativeVSync_ExpectedRateRange](capi-nativevsync-oh-nativevsync-expectedraterange.md)* range | Indicates the pointer to an expected rate range. |

**Returns**:

| Type | Description |
| -- | -- |
| int | {@link NATIVE_ERROR_OK} 0 - Success.<br>    {@link NATIVE_ERROR_INVALID_ARGUMENTS} 40001000 - the parameter nativeVsync is NULL or range is NULL or Invalid. |


