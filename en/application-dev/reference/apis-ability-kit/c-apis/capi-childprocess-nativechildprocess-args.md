# NativeChildProcess_Args

```c
struct NativeChildProcess_Args {...}
```

## Overview

The struct describes the parameters passed to the child process.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* entryParams | Pointer to the entry parameters. The size cannot exceed 150 KB.<br>**Since**: 13 |
| struct NativeChildProcess_FdList fdList | List of file descriptors passed to the child process.<br>**Since**: 13 |


