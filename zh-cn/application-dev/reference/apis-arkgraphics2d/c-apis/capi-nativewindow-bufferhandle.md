# BufferHandle

```c
typedef struct BufferHandle {...} BufferHandle
```

## 概述

用于传输和获取缓冲区信息的BufferHandle。

<!--Device-typedef struct BufferHandle {...} BufferHandle--><!--Device-typedef struct BufferHandle {...} BufferHandle-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**相关模块：** [NativeWindow](capi-arkgraphics2d-nativewindow.md)

**所在头文件：** [buffer_handle.h](capi-buffer-handle-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t fd | 缓冲区文件描述符，若不支持则为-1<br><!--Device-int32_t fd--><!--Device-int32_t fd-End--> |
| int32_t width | 缓冲区内存的宽度，单位为像素<br><!--Device-int32_t width--><!--Device-int32_t width-End--> |
| int32_t stride | 缓冲区内存的步幅，单位为字节<br><!--Device-int32_t stride--><!--Device-int32_t stride-End--> |
| int32_t height | 缓冲区内存的高度，单位为像素<br><!--Device-int32_t height--><!--Device-int32_t height-End--> |
| int32_t size | 缓冲区内存的大小，单位为字节<br><!--Device-int32_t size--><!--Device-int32_t size-End--> |
| int32_t format | 缓冲区内存的格式，取值具体可见OH_NativeBuffer_Format枚举值<br><!--Device-int32_t format--><!--Device-int32_t format-End--> |
| uint64_t usage | 缓冲区内存的用途，按位标志位，取值具体可见OH_NativeBuffer_Usage枚举值<br><!--Device-uint64_t usage--><!--Device-uint64_t usage-End--> |
| void *virAddr | 缓冲区内存的虚拟地址<br><!--Device-void *virAddr--><!--Device-void *virAddr-End--> |
| int32_t key | 缓冲区共享内存键值<br><!--Device-int32_t key--><!--Device-int32_t key-End--> |
| uint64_t phyAddr | 缓冲区内存的物理地址<br><!--Device-uint64_t phyAddr--><!--Device-uint64_t phyAddr-End--> |
| uint32_t reserveFds | 额外数据的文件描述符数量<br><!--Device-uint32_t reserveFds--><!--Device-uint32_t reserveFds-End--> |
| uint32_t reserveInts | 额外数据的整型值数量<br><!--Device-uint32_t reserveInts--><!--Device-uint32_t reserveInts-End--> |
| int32_t reserve[0] | 额外数据<br><!--Device-int32_t reserve[0]--><!--Device-int32_t reserve[0]-End--> |


