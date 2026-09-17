# OH_NativeVSync_ExpectedRateRange

```c
typedef struct OH_NativeVSync_ExpectedRateRange {...} OH_NativeVSync_ExpectedRateRange
```

## Overview

Defines the expected frame rate range struct.

**Since**: 20

**Related module**: [NativeVsync](capi-nativevsync.md)

**Header file**: [native_vsync.h](capi-native-vsync-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t min | The minimum frame rate of dynamical callback rate range. |
| int32_t max | The maximum frame rate of dynamical callback rate range. |
| int32_t expected | The expected frame rate of dynamical callback rate range. |


