# native_fence.h

## Overview

Defines the functions for using native fence.

**Library**: libnative_fence.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 20

**Related module**: [NativeFence](capi-nativefence.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [bool OH_NativeFence_IsValid(int fenceFd)](#oh_nativefence_isvalid) | Checks if the fenceFd is valid. |
| [bool OH_NativeFence_Wait(int fenceFd, uint32_t timeout)](#oh_nativefence_wait) | Waits for a fence signal. The maximum waiting time is determined by the timeout parameter. The incoming fenceFd needs to be closed by the user themselves. |
| [bool OH_NativeFence_WaitForever(int fenceFd)](#oh_nativefence_waitforever) | Waits forever for a fence signal. The incoming fenceFd needs to be closed by the user themselves. |
| [void OH_NativeFence_Close(int fenceFd)](#oh_nativefence_close) | Close the fenceFd. |

## Function description

### OH_NativeFence_IsValid()

```c
bool OH_NativeFence_IsValid(int fenceFd)
```

**Description**

Checks if the fenceFd is valid.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int fenceFd | Indicates a file descriptor handle, which is used for timing synchronization. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the fenceFd is valid.          Returns false if the fenceFd is a negative integer. |

### OH_NativeFence_Wait()

```c
bool OH_NativeFence_Wait(int fenceFd, uint32_t timeout)
```

**Description**

Waits for a fence signal. The maximum waiting time is determined by the timeout parameter. The incoming fenceFd needs to be closed by the user themselves.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int fenceFd | Indicates a file descriptor handle, which is used for timing synchronization. |
| uint32_t timeout | Indicates the timeout duration. The unit is milliseconds, 0 represents immediate return. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the fence signaled.          Returns false in the following cases:          1.if the fenceFd is a negative integer.          2.no event occurred within the specified timeout period.          3.the underlying poll interface call failed.          4.the timeout value is 0.          5.failed to duplicate the file descriptor. |

### OH_NativeFence_WaitForever()

```c
bool OH_NativeFence_WaitForever(int fenceFd)
```

**Description**

Waits forever for a fence signal. The incoming fenceFd needs to be closed by the user themselves.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int fenceFd | Indicates a file descriptor handle, which is used for timing synchronization. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the fence signaled.          Returns false in the following cases:          1.if the fenceFd is a negative integer.          2.no incidents have occurred, permanent waiting.          3.failed to duplicate the file descriptor. |

### OH_NativeFence_Close()

```c
void OH_NativeFence_Close(int fenceFd)
```

**Description**

Close the fenceFd.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int fenceFd | Indicates a file descriptor handle, which is used for timing synchronization. This value is a non negative integer. |


