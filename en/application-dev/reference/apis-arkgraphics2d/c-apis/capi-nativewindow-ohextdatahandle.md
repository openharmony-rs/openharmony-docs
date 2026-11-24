# OHExtDataHandle

```c
typedef struct OHExtDataHandle {...} OHExtDataHandle
```

## Overview

Defines the ExtData Handle

<!--Device-struct OHExtDataHandle {...}--><!--Device-struct OHExtDataHandle {...}-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 9

**Deprecated**: 10

**Related module**: [NativeWindow](capi-arkgraphics2d-nativewindow.md)

**Header file**: [external_window.h](capi-external-window-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t fd | < Handle fd, -1 if not supported<br><!--Device-int32_t fd--><!--Device-int32_t fd-End--> |
| uint32_t reserveInts | < the number of reserved integer value<br><!--Device-uint32_t reserveInts--><!--Device-uint32_t reserveInts-End--> |
| int32_t reserve[0] | < the reserved data<br><!--Device-int32_t reserve[0]--><!--Device-int32_t reserve[0]-End--> |


