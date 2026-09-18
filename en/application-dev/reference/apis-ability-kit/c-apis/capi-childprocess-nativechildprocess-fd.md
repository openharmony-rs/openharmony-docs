# NativeChildProcess_Fd

```c
typedef struct NativeChildProcess_Fd {...} NativeChildProcess_Fd
```

## Overview

The struct describes the information about the file descriptor passed to the child process.

**Since**: 13

**Related module**: [ChildProcess](capi-childprocess.md)

**Header file**: [native_child_process.h](capi-native-child-process-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* fdName |  |
| int32_t fd |  |
| struct [NativeChildProcess_Fd*](capi-childprocess-nativechildprocess-fd.md) next |  |


