# BufferHandle

```c
typedef struct BufferHandle {...} BufferHandle
```

## Overview

Buffer handle used to transfer and obtain information about the buffer.

**Since**: 8

**Related module**: [NativeWindow](capi-nativewindow.md)

**Header file**: [buffer_handle.h](capi-buffer-handle-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t fd | buffer fd, -1 if not supported |
| int32_t width | the width of memory |
| int32_t stride | the stride of memory |
| int32_t height | the height of memory |
| int32_t size | size of memory |
| int32_t format | the format of memory |
| uint64_t usage | the usage of memory |
| void *virAddr | Virtual address of memory |
| int32_t key | Shared memory key |
| uint64_t phyAddr | Physical address |
| uint32_t reserveFds | the number of reserved fd value |
| uint32_t reserveInts | the number of reserved integer value |
| int32_t reserve[0] | the data |


