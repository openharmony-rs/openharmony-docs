# native_display_soloist.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @wh_qwe-->
<!--Designer: @wh_qwe-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=ccdbec13380fdf227c4a20f5bde9cc05c16badee translatedAt=2026-08-24T09:11:35.201Z pushedAt=2026-08-31T11:47:09.144Z -->

## Overview

This file declares the functions for obtaining and using native display soloist.

**File to include**: <native_display_soloist/native_display_soloist.h>

**Library**: libnative_display_soloist.so

**System capability**: SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**Since**: 12

**Related module**: [NativeDisplaySoloist](capi-nativedisplaysoloist.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [DisplaySoloist_ExpectedRateRange](capi-nativedisplaysoloist-displaysoloist-expectedraterange.md) | DisplaySoloist_ExpectedRateRange | Defines the expected frame rate range struct, which is used to set the expected frame rate range of DisplaySoloist (variable frame rate rendering on a dedicated thread). The set expected frame rate range serves as a reference for system scheduling, and the system adjusts the rendering frame rate within this range as much as possible. |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) | OH_DisplaySoloist | Declares the OH_DisplaySoloist struct, which is used for native-side services that need to implement frame rate control on a dedicated thread. |

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*OH_DisplaySoloist_FrameCallback)(long long timestamp, long long targetTimestamp, void* data)](#oh_displaysoloist_framecallback) | OH_DisplaySoloist_FrameCallback | Defines the callback function type of OH_DisplaySoloist. It is invoked by the system each time a VSync signal arrives, to execute the custom service of each frame. |
| [OH_DisplaySoloist* OH_DisplaySoloist_Create(bool useExclusiveThread)](#oh_displaysoloist_create) | - | Creates an [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. Each call creates a new instance. The useExclusiveThread parameter determines the thread mode: in dedicated thread mode, the instance has an independent thread, which delivers higher performance but consumes more resources; in shared thread mode, multiple instances share a thread, which consumes fewer resources but may incur scheduling latency. |
| [int32_t OH_DisplaySoloist_Destroy(OH_DisplaySoloist* displaySoloist)](#oh_displaysoloist_destroy) | - | Destroys the [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance and reclaims the memory occupied by the object. Before destruction, call [OH_DisplaySoloist_Stop](#oh_displaysoloist_stop) to stop the callback. After destruction, do not access the instance or rely on its callback again. |
| [int32_t OH_DisplaySoloist_Start(OH_DisplaySoloist* displaySoloist, OH_DisplaySoloist_FrameCallback callback, void* data)](#oh_displaysoloist_start) | - | Starts requesting VSync signals and invokes the callback function each time a VSync signal arrives. If an expected frame rate range has been set through [OH_DisplaySoloist_SetExpectedFrameRateRange](#oh_displaysoloist_setexpectedframeraterange), the expected frame rate range takes effect. |
| [int32_t OH_DisplaySoloist_Stop(OH_DisplaySoloist* displaySoloist)](#oh_displaysoloist_stop) | - | Stops requesting VSync signals and stops invoking the callback function. It also invalidates the expected frame rate range set through [OH_DisplaySoloist_SetExpectedFrameRateRange](#oh_displaysoloist_setexpectedframeraterange). After stopping, you can call [OH_DisplaySoloist_Start](#oh_displaysoloist_start) again to restart. This function is used in pair with [OH_DisplaySoloist_Start](#oh_displaysoloist_start) and must be called after [OH_DisplaySoloist_Start](#oh_displaysoloist_start). |
| [int32_t OH_DisplaySoloist_SetExpectedFrameRateRange(OH_DisplaySoloist* displaySoloist, DisplaySoloist_ExpectedRateRange* range)](#oh_displaysoloist_setexpectedframeraterange) | - | Sets the expected VSync frame rate range. The set expected frame rate range serves as a reference for system scheduling, and the system adjusts the rendering frame rate within this range as much as possible. If this method is not called, or if DisplaySoloist_ExpectedRateRange(0, 0, 0) is passed in, the frame rate follows the current running frame rate of the application. It is recommended to set the range before calling [OH_DisplaySoloist_Start](#oh_displaysoloist_start) so that it takes effect immediately. Setting it after calling [OH_DisplaySoloist_Start](#oh_displaysoloist_start) also takes effect, but may incur latency. |

## Function Description

### OH_DisplaySoloist_FrameCallback()

```
typedef void (*OH_DisplaySoloist_FrameCallback)(long long timestamp, long long targetTimestamp, void* data)
```

**Description**

Type of the OH_DisplaySoloist callback function. It is invoked by the system each time a VSync signal arrives, to execute the custom service of each frame.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| long long timestamp | VSync timestamp of the current frame, in nanoseconds. |
| long long targetTimestamp | Expected VSync timestamp of the next frame, in nanoseconds. |
| void* data | Pointer to the user-defined data. |

### OH_DisplaySoloist_Create()

```
OH_DisplaySoloist* OH_DisplaySoloist_Create(bool useExclusiveThread)
```

**Description**

Creates an [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. Each call creates a new instance. The useExclusiveThread parameter determines the thread mode: in dedicated thread mode, the instance has an independent thread, which delivers higher performance but consumes more resources; in shared thread mode, multiple instances share a thread, which consumes fewer resources but may incur scheduling latency.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| bool useExclusiveThread | Indicates whether this [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance uses a dedicated thread. true indicates a dedicated thread, and false indicates a shared thread (sharing a thread with other instances). |

**Returns**

| Type| Description|
| -- | -- |
| OH_DisplaySoloist* | Returns the pointer to the [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance created if the operation is successful; returns a null pointer otherwise. The failure cause may be out of memory.|

### OH_DisplaySoloist_Destroy()

```
int32_t OH_DisplaySoloist_Destroy(OH_DisplaySoloist* displaySoloist)
```

**Description**

Destroys the [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance and reclaims the memory occupied by the object. Before destruction, call [OH_DisplaySoloist_Stop](#oh_displaysoloist_stop) to stop the callback. After destruction, do not access the instance or rely on its callback.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | Pointer to an [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. Must not be null. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | 0 indicates success; -1 indicates failure, possibly because an incorrect displaySoloist is passed in. |

### OH_DisplaySoloist_Start()

```
int32_t OH_DisplaySoloist_Start(OH_DisplaySoloist* displaySoloist, OH_DisplaySoloist_FrameCallback callback, void* data)
```

**Description**

Starts requesting VSync signals and invokes the callback function each time a VSync signal arrives. If an expected frame rate range has been set through [OH_DisplaySoloist_SetExpectedFrameRateRange](#oh_displaysoloist_setexpectedframeraterange), the expected frame rate range takes effect.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | Pointer to an [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. Must not be null. |
| [OH_DisplaySoloist_FrameCallback](#oh_displaysoloist_framecallback) callback | Callback invoked when the next VSync signal arrives. |
| void* data | Pointer to the user-defined data, used to pass custom data to the callback function. Pass this parameter when custom data needs to be accessed in the callback function. It can be null. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | The return value 0 indicates success; -1 indicates failure, possibly because an invalid displaySoloist or callback is passed in. |

### OH_DisplaySoloist_Stop()

```
int32_t OH_DisplaySoloist_Stop(OH_DisplaySoloist* displaySoloist)
```

**Description**

Stops requesting VSync signals and stops invoking the callback function callback. It also invalidates the expected frame rate range set through [OH_DisplaySoloist_SetExpectedFrameRateRange](#oh_displaysoloist_setexpectedframeraterange). After stopping, you can call [OH_DisplaySoloist_Start](#oh_displaysoloist_start) again to restart. It is used in pair with [OH_DisplaySoloist_Start](#oh_displaysoloist_start) and must be called after [OH_DisplaySoloist_Start](#oh_displaysoloist_start).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | Pointer to an [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. Must not be null. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | The value 0 indicates success, and -1 indicates failure. The possible cause is that an incorrect displaySoloist is passed in. |

### OH_DisplaySoloist_SetExpectedFrameRateRange()

```
int32_t OH_DisplaySoloist_SetExpectedFrameRateRange(OH_DisplaySoloist* displaySoloist, DisplaySoloist_ExpectedRateRange* range)
```

**Description**

Sets the expected VSync frame rate range. The set expected frame rate range serves as a reference for system scheduling, and the system tries to adjust the rendering frame rate within this range. If this method is not called or DisplaySoloist_ExpectedRateRange(0, 0, 0) is passed in, the frame rate follows the current running frame rate of the application. It is recommended to set it before calling [OH_DisplaySoloist_Start](#oh_displaysoloist_start) so that it takes effect immediately. Setting it after calling [OH_DisplaySoloist_Start](#oh_displaysoloist_start) also takes effect but may incur latency.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | Pointer to an [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. Must not be null. |
| [DisplaySoloist_ExpectedRateRange](capi-nativedisplaysoloist-displaysoloist-expectedraterange.md)* range | Pointer to a [DisplaySoloist_ExpectedRateRange](capi-nativedisplaysoloist-displaysoloist-expectedraterange.md) instance of the expected frame rate range. Must not be null. Contains three fields: expected, min, and max, in frames per second (fps). The fields must be non-negative integers within the range [0, maximum device frame rate], and must satisfy min <= expected <= max. If the value is out of the valid range, parameter verification fails. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns 0 if the operation is successful; returns -1 if the operation fails. Possible failure causes: 1. A required parameter is not specified; 2. The parameter type is incorrect; 3. Parameter verification fails or DisplaySoloist_ExpectedRateRange is invalid. |