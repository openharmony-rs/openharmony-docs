# OHExtDataHandle

```c
typedef struct OHExtDataHandle {...} OHExtDataHandle
```

## Overview

Defines the ExtData Handle

**Since**: 9

**Deprecated**: 10

**Related module**: [NativeWindow](capi-nativewindow.md)

**Header file**: [external_window.h](capi-external-window-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t fd | < Handle fd, -1 if not supported |
| uint32_t reserveInts | < the number of reserved integer value |
| int32_t reserve[0] | < the reserved data |


