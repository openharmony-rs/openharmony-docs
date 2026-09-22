# native_display_soloist.h

## Overview

Defines the functions for obtaining and using a native displaySoloist.

**Library**: libnative_display_soloist.so

**System capability**: SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**Since**: 12

**Related module**: [NativeDisplaySoloist](capi-nativedisplaysoloist.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [DisplaySoloist_ExpectedRateRange](capi-nativedisplaysoloist-displaysoloist-expectedraterange.md) | DisplaySoloist_ExpectedRateRange | This struct describes the expected frame rate range. |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) | OH_DisplaySoloist | Provides the declaration of an **OH_DisplaySoloist** struct. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_DisplaySoloist_FrameCallback)(long long timestamp, long long targetTimestamp, void* data)](#oh_displaysoloist_framecallback) | OH_DisplaySoloist_FrameCallback | Defines the pointer to an OH_DisplaySoloist callback function. |
| [OH_DisplaySoloist* OH_DisplaySoloist_Create(bool useExclusiveThread)](#oh_displaysoloist_create) | - | Creates an **OH_DisplaySoloist** instance. A new **OH_DisplaySoloist** instance is created each time this API is called. |
| [int32_t OH_DisplaySoloist_Destroy(OH_DisplaySoloist* displaySoloist)](#oh_displaysoloist_destroy) | - | Destroys an **OH_DisplaySoloist** object and reclaims the memory occupied. |
| [int32_t OH_DisplaySoloist_Start(OH_DisplaySoloist* displaySoloist, OH_DisplaySoloist_FrameCallback callback, void* data)](#oh_displaysoloist_start) | - | Sets a callback function for each frame. The callback function is triggered each time a VSync signal arrives. |
| [int32_t OH_DisplaySoloist_Stop(OH_DisplaySoloist* displaySoloist)](#oh_displaysoloist_stop) | - | Stops requesting the next VSync signal and triggering the callback function. |
| [int32_t OH_DisplaySoloist_SetExpectedFrameRateRange(OH_DisplaySoloist* displaySoloist, DisplaySoloist_ExpectedRateRange* range)](#oh_displaysoloist_setexpectedframeraterange) | - | Sets the expected frame rate range. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_DisplaySoloist_FrameCallback)(long long timestamp, long long targetTimestamp, void* data) | Defines the pointer to an OH_DisplaySoloist callback function.<br>**Since**: 12 |

## Function description

### OH_DisplaySoloist_FrameCallback()

```c
typedef void (*OH_DisplaySoloist_FrameCallback)(long long timestamp, long long targetTimestamp, void* data)
```

**Description**

Defines the pointer to an OH_DisplaySoloist callback function.

**System capability**: SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| long long timestamp | Current frame VSync timestamp. |
| long long targetTimestamp | Expected VSync timestamp of the next frame. |
| void\* data | Pointer to user-defined data. |

### OH_DisplaySoloist_Create()

```c
OH_DisplaySoloist* OH_DisplaySoloist_Create(bool useExclusiveThread)
```

**Description**

Creates an **OH_DisplaySoloist** instance. A new **OH_DisplaySoloist** instance is created each time this API is called.

**System capability**: SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool useExclusiveThread | Whether the **OH_DisplaySoloist** instance is an exclusive thread. **true** means yes; **<br>false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_DisplaySoloist*](capi-nativedisplaysoloist-oh-displaysoloist.md) | Returns the pointer to the [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance created if the operation is successful;  returns a null pointer otherwise. The failure cause may be out of memory. |

### OH_DisplaySoloist_Destroy()

```c
int32_t OH_DisplaySoloist_Destroy(OH_DisplaySoloist* displaySoloist)
```

**Description**

Destroys an **OH_DisplaySoloist** object and reclaims the memory occupied.

**System capability**: SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | Pointer to the [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns 0 if the operation is successful; returns -1 otherwise. |

### OH_DisplaySoloist_Start()

```c
int32_t OH_DisplaySoloist_Start(OH_DisplaySoloist* displaySoloist, OH_DisplaySoloist_FrameCallback callback, void* data)
```

**Description**

Sets a callback function for each frame. The callback function is triggered each time a VSync signal arrives.

**System capability**: SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | Pointer to the [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. |
| [OH_DisplaySoloist_FrameCallback](capi-native-display-soloist-h.md#oh_displaysoloist_framecallback) callback | Callback function to be triggered when the next VSync signal arrives. |
| void* data | Pointer to the user-defined data struct. The type is void. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns 0 if the operation is successful; returns -1 otherwise. |

### OH_DisplaySoloist_Stop()

```c
int32_t OH_DisplaySoloist_Stop(OH_DisplaySoloist* displaySoloist)
```

**Description**

Stops requesting the next VSync signal and triggering the callback function.

**System capability**: SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | Pointer to the [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns 0 if the operation is successful; returns -1 otherwise. |

### OH_DisplaySoloist_SetExpectedFrameRateRange()

```c
int32_t OH_DisplaySoloist_SetExpectedFrameRateRange(OH_DisplaySoloist* displaySoloist, DisplaySoloist_ExpectedRateRange* range)
```

**Description**

Sets the expected frame rate range.

**System capability**: SystemCapability.Graphic.Graphic2D.HyperGraphicManager

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md)* displaySoloist | Pointer to the [OH_DisplaySoloist](capi-nativedisplaysoloist-oh-displaysoloist.md) instance. |
| [DisplaySoloist_ExpectedRateRange](capi-nativedisplaysoloist-displaysoloist-expectedraterange.md)* range | Pointer to the [DisplaySoloist_ExpectedRateRange](capi-nativedisplaysoloist-displaysoloist-expectedraterange.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns 0 if the operation is successful; returns -1 otherwise. |


