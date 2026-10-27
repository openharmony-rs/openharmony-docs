# NativeChildProcess_Fd

```c
struct NativeChildProcess_Fd {...}
```

## Overview

The struct describes the information about the file descriptor passed to the child process.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* fdName | Pointer to the name of the file descriptor. It contains a maximum of 20 characters.<br>**Since**: 13 |
| int32_t fd | Value of the file descriptor.<br>**Since**: 13 |
| struct NativeChildProcess_Fd* next | Pointer to the next file descriptor.<br>**Since**: 13 |


