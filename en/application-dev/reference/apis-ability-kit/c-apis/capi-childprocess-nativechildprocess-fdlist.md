# NativeChildProcess_FdList

```c
struct NativeChildProcess_FdList {...}
```

## Overview

Defines the list of file descriptor information passed to the child process. The number of file descriptor records must not exceed 16; exceeding the limit will cause the child process creation to fail.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct NativeChildProcess_Fd* head | Pointer to the first file descriptor in the linked list passed to the child process.<br>**Since**: 13 |


