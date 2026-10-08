# native_fence.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=138b9da99fa1494d3d8b18ca10cbbcd2abcda6ea translatedAt=2026-08-24T09:11:22.331Z pushedAt=2026-08-31T11:47:32.051Z -->

## Overview

Defines the functions for obtaining and using NativeFence. NativeFence is used for synchronization control in the graphics system. It supports operations such as checking fence validity, blocking and waiting for fence signals, and closing fences. It is applicable to scenarios where graphics resource access needs to be synchronized between multiple threads or processes.

**Header file**: <native_fence/native_fence.h>

**Library**: libnative_fence.so

**Since**: 20

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Related module**: [NativeFence](capi-nativefence.md)

## Summary

### Functions

| Name                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [bool OH_NativeFence_IsValid(int fenceFd)](#oh_nativefence_isvalid) | Checks whether **fenceFd** is valid.                                       |
| [bool OH_NativeFence_Wait(int fenceFd, uint32_t timeout)](#oh_nativefence_wait) | Blocks the fenceFd passed in. The maximum blocking time is determined by the timeout parameter, in ms. The fenceFd passed in must be closed by the user. |
| [bool OH_NativeFence_WaitForever(int fenceFd)](#oh_nativefence_waitforever) | Permanently blocks the input **fenceFd**. The input **fenceFd** needs to be closed by yourself.      |
| [void OH_NativeFence_Close(int fenceFd)](#oh_nativefence_close) | Closes **fenceFd**.                                               |

## Function Description

### OH_NativeFence_IsValid()

```c
bool OH_NativeFence_IsValid(int fenceFd)
```

**Description**

Checks whether **fenceFd** is valid.

**Since**: 20

**Parameters**

| Name     | Description                              |
| ----------- | ---------------------------------- |
| int fenceFd | File descriptor used for synchronization control. |

**Returns**

| Type| Description                                                    |
| ---- | -------------------------------------------------------- |
| bool | Returns **true** if **fenceFd** is valid; **false** otherwise.|

### OH_NativeFence_Wait()

```c
bool OH_NativeFence_Wait(int fenceFd, uint32_t timeout)
```

**Description**

Blocks the passed-in fenceFd. The maximum blocking time is determined by the timeout parameter, in ms. The passed-in fenceFd needs to be closed by the user.

**Since**: 20

**Parameters**

| Name          | Description                                                        |
| ---------------- | ------------------------------------------------------------ |
| int fenceFd      | File descriptor used for synchronization control. |
| uint32_t timeout | Waiting time, in ms. A value greater than 0 indicates the specific waiting duration (applicable to scenarios where the waiting time needs to be limited; it is recommended to set a reasonable timeout value based on actual service requirements); 0 indicates that the API returns immediately (applicable to scenarios where only the fenceFd status is checked without blocking); to wait indefinitely, use [OH_NativeFence_WaitForever](#oh_nativefence_waitforever). |

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| bool | Returns **true** if the corresponding **fenceFd** has a signal triggered.<br>Returns **false** in the following cases:<br>1. The input **fenceFd** is a negative integer.<br>2. No signal is triggered within the specified timeout period.<br>3. The underlying **poll** API fails to be called.<br>4. The timeout period is set to **0**.<br>5. The file descriptor fails to be copied in the API.|

### OH_NativeFence_WaitForever()

```c
bool OH_NativeFence_WaitForever(int fenceFd)
```

**Description**

Permanently blocks the input **fenceFd**. The input **fenceFd** needs to be closed by yourself.

**Since**: 20

**Parameters**

| Name     | Description                              |
| ----------- | ---------------------------------- |
| int fenceFd | File descriptor for periodic sync.|

**Returns**

| Type| Description                                                        |
| ---- | ------------------------------------------------------------ |
| bool | true indicates that the corresponding fenceFd is signaled;<br>false is returned in the following cases:<br>1. The passed-in fenceFd is a negative integer.<br>2. No signal is triggered, and the wait is permanent.<br>3. The API fails to copy the file descriptor. |

### OH_NativeFence_Close()

```c
void OH_NativeFence_Close(int fenceFd)
```

**Description**

Closes **fenceFd**.

**Since**: 20

**Parameters**

| Name     | Description                                                  |
| ----------- | ------------------------------------------------------ |
| int fenceFd | File descriptor for periodic sync. The value is a non-negative integer.|