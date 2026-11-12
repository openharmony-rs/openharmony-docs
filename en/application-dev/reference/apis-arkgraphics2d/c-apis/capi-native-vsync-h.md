# native_vsync.h

## Overview

This file declares the functions for obtaining and using native vertical synchronization (VSync).

**File to Include**: <native_vsync/native_vsync.h>

**Library**: libnative_vsync.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 9

**Related module**: [NativeVsync](capi-arkgraphics2d-nativevsync.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_NativeVSync_ExpectedRateRange](capi-nativevsync-oh-nativevsync-expectedraterange.md) | OH_NativeVSync_ExpectedRateRange | Provides the expected frame rate range. |
| [OH_NativeVSync](capi-nativevsync-oh-nativevsync.md) | OH_NativeVSync | Provides the declaration of an **OH_NativeVSync** struct. |

### Functions

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_NativeVSync_FrameCallback)(long long timestamp, void *data)](#oh_nativevsync_framecallback) | OH_NativeVSync_FrameCallback | Defines the pointer to a VSync callback function. |
| [OH_NativeVSync *OH_NativeVSync_Create(const char *name, unsigned int length)](#oh_nativevsync_create) | - | Creates an OH_NativeVSync instance. Each call creates a new instance. The number of OH_NativeVSync instances is limited, and a null pointer is returned when the limit is exceeded. <br>This API must be used together with [OH_NativeVSync_Destroy](capi-native-vsync-h.md#oh_nativevsync_destroy); otherwise, a memory leak occurs. |
| [void OH_NativeVSync_Destroy(OH_NativeVSync *nativeVsync)](#oh_nativevsync_destroy) | - | Destroys an **OH_NativeVSync** instance. <br>Once the **OH_NativeVSync** pointer is destroyed, it should not be used, as this can result in dangling pointer problems. Pay special attention to the management of the **OH_NativeVSync** pointer in multithreaded scenarios. |
| [OH_NativeVSync *OH_NativeVSync_Create_ForAssociatedWindow(uint64_t windowID, const char *name, unsigned int length)](#oh_nativevsync_create_forassociatedwindow) | - | Creates an **OH_NativeVSync** instance to bind with a window. A new **OH_NativeVSync** instance is created each time this API is called. <br>The actual VSync period of the **OH_NativeVSync** instance created by calling this function may be different from the system's VSync period. The system adjusts the actual VSync period based on the window status. |
| [int OH_NativeVSync_RequestFrame(OH_NativeVSync *nativeVsync, OH_NativeVSync_FrameCallback callback, void *data)](#oh_nativevsync_requestframe) | - | Requests the next VSync signal. When the signal arrives, the callback function callback is invoked. <br>If this API is called multiple times within the same frame, only the last callback is triggered. <br>If this API and [OH_NativeVSync_RequestFrameWithMultiCallback](capi-native-vsync-h.md#oh_nativevsync_requestframewithmulticallback) are called within the same frame, this API does not take effect. |
| [int OH_NativeVSync_RequestFrameWithMultiCallback(OH_NativeVSync *nativeVsync, OH_NativeVSync_FrameCallback callback, void *data)](#oh_nativevsync_requestframewithmulticallback) | - | Requests the next VSync signal. When the signal arrives, the callback function callback is invoked. <br>If this API is called multiple times within the same frame, every callback passed in is executed. |
| [int OH_NativeVSync_GetPeriod(OH_NativeVSync *nativeVsync, long long *period)](#oh_nativevsync_getperiod) | - | Obtains the VSync period. <br>The VSync period is refreshed only when the **OH_NativeVSync_FrameCallback** callback is received following a request for a VSync signal via **OH_NativeVSync_RequestFrame** or **OH_NativeVSync_RequestFrameWithMultiCallback**. <br>To obtain the VSync period for the first time using this function, you need to call **OH_NativeVSync_RequestFrame** or **OH_NativeVSync_RequestFrameWithMultiCallback** to request a VSync signal. Once the **OH_NativeVSync_FrameCallback** callback is received, the vsync period can be obtained. |
| [int OH_NativeVSync_DVSyncSwitch(OH_NativeVSync *nativeVsync, bool enable)](#oh_nativevsync_dvsyncswitch) | - | Enables DVSync to improve the smoothness of self-drawing animations. <br>DVSync, short for Decoupled VSync, is a frame timing management policy that is decoupled from the hardware's VSync. <br>DVSync drives the early rendering of upcoming animation frames by sending VSync signals with future timestamps. These frames are stored in a frame buffer queue. This helps DVSync reduce potential frame drops and therefore enhances the smoothness of animations. <br>DVSync requires free self-drawing frame buffers to store these pre-rendered animation frames. Therefore, you must ensure that at least one free frame buffer is available. Otherwise, do not enable DVSync. <br>After DVSync is enabled, you must correctly respond to the early VSync signals and request the subsequent VSync after the animation frame associated with the previous VSync is complete. In addition, the self-drawing frames must carry timestamps that align with VSync. <br>After the animation ends, disable DVSync. <br>On a platform that does not support DVSync or if another application has enabled DVSync, the attempt to enable it will not take effect, and the application still receives normal VSync signals. |
| [int OH_NativeVSync_SetExpectedFrameRateRange(OH_NativeVSync *nativeVsync, OH_NativeVSync_ExpectedRateRange *range)](#oh_nativevsync_setexpectedframeraterange) | - | Sets the expected frame rate and its range. The actual frame rate may be different from the expected frame rate due to system power consumption, performance, and hardware specifications. |

## Function description

### OH_NativeVSync_FrameCallback()

```c
typedef void (*OH_NativeVSync_FrameCallback)(long long timestamp, void *data)
```

**Description**

Defines the pointer to a VSync callback function.

<!--Device-typedef void (*OH_NativeVSync_FrameCallback)(long long timestamp, void *data)--><!--Device-typedef void (*OH_NativeVSync_FrameCallback)(long long timestamp, void *data)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| long long timestamp | [in] System timestamp obtained by VSync using CLOCK_MONOTONIC, in nanoseconds. |
| void *data | [in] Pointer to user-defined data. |

### OH_NativeVSync_Create()

```c
OH_NativeVSync *OH_NativeVSync_Create(const char *name, unsigned int length)
```

**Description**

Creates an OH_NativeVSync instance. Each call creates a new instance. The number of OH_NativeVSync instances is limited, and a null pointer is returned when the limit is exceeded. <br>This API must be used together with [OH_NativeVSync_Destroy](capi-native-vsync-h.md#oh_nativevsync_destroy); otherwise, a memory leak occurs.

<!--Device-OH_NativeVSync *OH_NativeVSync_Create(const char *name, unsigned int length)--><!--Device-OH_NativeVSync *OH_NativeVSync_Create(const char *name, unsigned int length)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 9

**Resource release**: [OH_NativeVSync_Destroy](#oh_nativevsync_destroy)

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | [in] Pointer to the name that associates with the **OH_NativeVSync** instance. |
| unsigned int length | [in] Length of the name (number of characters). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_NativeVSync *](capi-nativevsync-oh-nativevsync.md) | Returns the pointer to an **OH_NativeVSync** instance. |

### OH_NativeVSync_Destroy()

```c
void OH_NativeVSync_Destroy(OH_NativeVSync *nativeVsync)
```

**Description**

Destroys an **OH_NativeVSync** instance. <br>Once the **OH_NativeVSync** pointer is destroyed, it should not be used, as this can result in dangling pointer problems. Pay special attention to the management of the **OH_NativeVSync** pointer in multithreaded scenarios.

<!--Device-void OH_NativeVSync_Destroy(OH_NativeVSync *nativeVsync)--><!--Device-void OH_NativeVSync_Destroy(OH_NativeVSync *nativeVsync)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeVSync](capi-nativevsync-oh-nativevsync.md) *nativeVsync | [in] Pointer to an **OH_NativeVSync** instance. |

### OH_NativeVSync_Create_ForAssociatedWindow()

```c
OH_NativeVSync *OH_NativeVSync_Create_ForAssociatedWindow(uint64_t windowID, const char *name, unsigned int length)
```

**Description**

Creates an **OH_NativeVSync** instance to bind with a window. A new **OH_NativeVSync** instance is created each time this API is called. <br>The actual VSync period of the **OH_NativeVSync** instance created by calling this function may be different from the system's VSync period. The system adjusts the actual VSync period based on the window status.

<!--Device-OH_NativeVSync *OH_NativeVSync_Create_ForAssociatedWindow(uint64_t windowID, const char *name, unsigned int length)--><!--Device-OH_NativeVSync *OH_NativeVSync_Create_ForAssociatedWindow(uint64_t windowID, const char *name, unsigned int length)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 14

**Resource release**: [OH_NativeVSync_Destroy](#oh_nativevsync_destroy)

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t windowID | [in] Window ID, which is the index identifier of the window child process and can be obtained through [OH_NativeWindow_GetSurfaceId](capi-external-window-h.md#oh_nativewindow_getsurfaceid). |
| const char *name | [in] Pointer to the name that associates with the **OH_NativeVSync** instance. |
| unsigned int length | [in] Length of the name (number of characters). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_NativeVSync *](capi-nativevsync-oh-nativevsync.md) | Returns the pointer to an **OH_NativeVSync** instance. |

### OH_NativeVSync_RequestFrame()

```c
int OH_NativeVSync_RequestFrame(OH_NativeVSync *nativeVsync, OH_NativeVSync_FrameCallback callback, void *data)
```

**Description**

Requests the next VSync signal. When the signal arrives, the callback function callback is invoked. <br>If this API is called multiple times within the same frame, only the last callback is triggered. <br>If this API and [OH_NativeVSync_RequestFrameWithMultiCallback](capi-native-vsync-h.md#oh_nativevsync_requestframewithmulticallback) are called within the same frame, this API does not take effect.

<!--Device-int OH_NativeVSync_RequestFrame(OH_NativeVSync *nativeVsync, OH_NativeVSync_FrameCallback callback, void *data)--><!--Device-int OH_NativeVSync_RequestFrame(OH_NativeVSync *nativeVsync, OH_NativeVSync_FrameCallback callback, void *data)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeVSync](capi-nativevsync-oh-nativevsync.md) *nativeVsync | [in] Pointer to an **OH_NativeVSync** instance. |
| [OH_NativeVSync_FrameCallback](capi-native-vsync-h.md#oh_nativevsync_framecallback) callback | [in] Function pointer of the **OH_NativeVSync_FrameCallback** type. This function pointer will be called when the next VSync signal arrives. |
| void *data | [in] Pointer to the user-defined data struct. The type is void. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise. |

### OH_NativeVSync_RequestFrameWithMultiCallback()

```c
int OH_NativeVSync_RequestFrameWithMultiCallback(OH_NativeVSync *nativeVsync, OH_NativeVSync_FrameCallback callback, void *data)
```

**Description**

Requests the next VSync signal. When the signal arrives, the callback function callback is invoked. <br>If this API is called multiple times within the same frame, every callback passed in is executed.

<!--Device-int OH_NativeVSync_RequestFrameWithMultiCallback(OH_NativeVSync *nativeVsync, OH_NativeVSync_FrameCallback callback, void *data)--><!--Device-int OH_NativeVSync_RequestFrameWithMultiCallback(OH_NativeVSync *nativeVsync, OH_NativeVSync_FrameCallback callback, void *data)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeVSync](capi-nativevsync-oh-nativevsync.md) *nativeVsync | [in] Pointer to an **OH_NativeVSync** instance. |
| [OH_NativeVSync_FrameCallback](capi-native-vsync-h.md#oh_nativevsync_framecallback) callback | [in] Function pointer of the **OH_NativeVSync_FrameCallback** type. This function pointer will be called when the next VSync signal arrives. |
| void *data | [in] Pointer to the user-defined data struct. The type is void. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise. |

### OH_NativeVSync_GetPeriod()

```c
int OH_NativeVSync_GetPeriod(OH_NativeVSync *nativeVsync, long long *period)
```

**Description**

Obtains the VSync period. <br>The VSync period is refreshed only when the **OH_NativeVSync_FrameCallback** callback is received following a request for a VSync signal via **OH_NativeVSync_RequestFrame** or **OH_NativeVSync_RequestFrameWithMultiCallback**. <br>To obtain the VSync period for the first time using this function, you need to call **OH_NativeVSync_RequestFrame** or **OH_NativeVSync_RequestFrameWithMultiCallback** to request a VSync signal. Once the **OH_NativeVSync_FrameCallback** callback is received, the vsync period can be obtained.

<!--Device-int OH_NativeVSync_GetPeriod(OH_NativeVSync *nativeVsync, long long *period)--><!--Device-int OH_NativeVSync_GetPeriod(OH_NativeVSync *nativeVsync, long long *period)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeVSync](capi-nativevsync-oh-nativevsync.md) *nativeVsync | [in] Pointer to an **OH_NativeVSync** instance. |
| long long *period | [out] Pointer to the VSync period. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise. |

### OH_NativeVSync_DVSyncSwitch()

```c
int OH_NativeVSync_DVSyncSwitch(OH_NativeVSync *nativeVsync, bool enable)
```

**Description**

Enables DVSync to improve the smoothness of self-drawing animations. <br>DVSync, short for Decoupled VSync, is a frame timing management policy that is decoupled from the hardware's VSync. <br>DVSync drives the early rendering of upcoming animation frames by sending VSync signals with future timestamps. These frames are stored in a frame buffer queue. This helps DVSync reduce potential frame drops and therefore enhances the smoothness of animations. <br>DVSync requires free self-drawing frame buffers to store these pre-rendered animation frames. Therefore, you must ensure that at least one free frame buffer is available. Otherwise, do not enable DVSync. <br>After DVSync is enabled, you must correctly respond to the early VSync signals and request the subsequent VSync after the animation frame associated with the previous VSync is complete. In addition, the self-drawing frames must carry timestamps that align with VSync. <br>After the animation ends, disable DVSync. <br>On a platform that does not support DVSync or if another application has enabled DVSync, the attempt to enable it will not take effect, and the application still receives normal VSync signals.

<!--Device-int OH_NativeVSync_DVSyncSwitch(OH_NativeVSync *nativeVsync, bool enable)--><!--Device-int OH_NativeVSync_DVSyncSwitch(OH_NativeVSync *nativeVsync, bool enable)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeVSync](capi-nativevsync-oh-nativevsync.md) *nativeVsync | [in] Pointer to an **OH_NativeVSync** instance. |
| bool enable | [in] Whether to enable DVSync. The value **true** means to enable DVSync, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns **0** if the operation is successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise. |

### OH_NativeVSync_SetExpectedFrameRateRange()

```c
int OH_NativeVSync_SetExpectedFrameRateRange(OH_NativeVSync *nativeVsync, OH_NativeVSync_ExpectedRateRange *range)
```

**Description**

Sets the expected frame rate and its range. The actual frame rate may be different from the expected frame rate due to system power consumption, performance, and hardware specifications.

<!--Device-int OH_NativeVSync_SetExpectedFrameRateRange(OH_NativeVSync *nativeVsync, OH_NativeVSync_ExpectedRateRange *range)--><!--Device-int OH_NativeVSync_SetExpectedFrameRateRange(OH_NativeVSync *nativeVsync, OH_NativeVSync_ExpectedRateRange *range)-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeVsync

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_NativeVSync](capi-nativevsync-oh-nativevsync.md) *nativeVsync | [in] Pointer to an [OH_NativeVSync](capi-nativevsync-oh-nativevsync.md) instance. |
| [OH_NativeVSync_ExpectedRateRange](capi-nativevsync-oh-nativevsync-expectedraterange.md) *range | [in] Pointer to an [OH_NativeVSync_ExpectedRateRange](capi-nativevsync-oh-nativevsync-expectedraterange.md) instance. <br>Valid expected frame rate range: 0 <= Minimum value <= Expected frame rate <= Maximum value <= 144. <br>The value **0** means that the expected frame rate is canceled. <br>You need to manage the lifecycle of this pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns **0** if successful; returns an error code defined in [OHNativeErrorCode](capi-graphic-error-code-h.md#ohnativeerrorcode) otherwise. |


