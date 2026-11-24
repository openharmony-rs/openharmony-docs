# BufferHandle

```c
typedef struct BufferHandle {...} BufferHandle
```

## Overview

Buffer handle used to transfer and obtain information about the buffer.

<!--Device-typedef struct BufferHandle {...} BufferHandle--><!--Device-typedef struct BufferHandle {...} BufferHandle-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Related module**: [NativeWindow](capi-arkgraphics2d-nativewindow.md)

**Header file**: [buffer_handle.h](capi-buffer-handle-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t fd | buffer fd, -1 if not supported<br><!--Device-int32_t fd--><!--Device-int32_t fd-End--> |
| int32_t width | the width of memory<br><!--Device-int32_t width--><!--Device-int32_t width-End--> |
| int32_t stride | the stride of memory<br><!--Device-int32_t stride--><!--Device-int32_t stride-End--> |
| int32_t height | the height of memory<br><!--Device-int32_t height--><!--Device-int32_t height-End--> |
| int32_t size | size of memory<br><!--Device-int32_t size--><!--Device-int32_t size-End--> |
| int32_t format | the format of memory<br><!--Device-int32_t format--><!--Device-int32_t format-End--> |
| uint64_t usage | the usage of memory<br><!--Device-uint64_t usage--><!--Device-uint64_t usage-End--> |
| void *virAddr | Virtual address of memory<br><!--Device-void *virAddr--><!--Device-void *virAddr-End--> |
| int32_t key | Shared memory key<br><!--Device-int32_t key--><!--Device-int32_t key-End--> |
| uint64_t phyAddr | Physical address<br><!--Device-uint64_t phyAddr--><!--Device-uint64_t phyAddr-End--> |
| uint32_t reserveFds | the number of reserved fd value<br><!--Device-uint32_t reserveFds--><!--Device-uint32_t reserveFds-End--> |
| uint32_t reserveInts | the number of reserved integer value<br><!--Device-uint32_t reserveInts--><!--Device-uint32_t reserveInts-End--> |
| int32_t reserve[0] | the data<br><!--Device-int32_t reserve[0]--><!--Device-int32_t reserve[0]-End--> |


