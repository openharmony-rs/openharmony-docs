# native_fence.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Flix-fangyang; @BruceXu; @ding-panyun-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
## Overview

This file declares the functions for obtaining and using **NativeFence**.

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
| [bool OH_NativeFence_Wait(int fenceFd, uint32_t timeout)](#oh_nativefence_wait) | Blocks the input **fenceFd**. The maximum blocking time is determined by the timeout parameter. The input **fenceFd** needs to be closed by yourself.|
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
| int fenceFd | File descriptor for periodic sync.|

**Returns**

| Type| Description                                                    |
| ---- | -------------------------------------------------------- |
| bool | Returns **true** if **fenceFd** is valid; **false** otherwise.|

### OH_NativeFence_Wait()

```c
bool OH_NativeFence_Wait(int fenceFd, uint32_t timeout)
```

**Description**

Blocks the input **fenceFd**. The maximum blocking time is determined by the timeout parameter. The input **fenceFd** needs to be closed by yourself.


**Since**: 20


**Parameters**

| Name          | Description                                                        |
| ---------------- | ------------------------------------------------------------ |
| int fenceFd      | File descriptor for periodic sync.                          |
| uint32_t timeout | Wait time. The unit is millisecond. The value **-1** indicates that the API waits permanently, and the value **0** indicates that the API returns a response immediately.|

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
| bool | Returns **true** if the corresponding **fenceFd** has a signal triggered.<br>Returns **false** in the following cases:<br>1. The input **fenceFd** is a negative integer.<br>2. No signal is triggered within the specified timeout period, and the API waits permanently.<br>3. The file descriptor fails to be copied in the API.|

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
