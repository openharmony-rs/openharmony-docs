# DDK_Ashmem

```c
typedef struct DDK_Ashmem {...} DDK_Ashmem
```

## 概述

定义通过接口{@link OH_DDK_CreateAshmem}创建的共享内存。共享内存的缓冲区提供更好的性能，适用于多个模块之间高效共享大数据量、驱动程序与应用程序之间快速数据交换等需要高性能数据共享的场景。

**起始版本：** 12

**相关模块：** [Ddk](capi-ddk.md)

**所在头文件：** [ddk_types.h](capi-ddk-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t ashmemFd | 共享内存的文件描述符。 |
| const uint8_t* address | 缓冲区地址。 |
| const uint32_t size | 缓冲区大小。 |
| uint32_t offset | 已使用缓冲区的偏移量。默认值为0，表示没有偏移，缓冲区从address指定地址开始。offset与bufferLength之和不超过size，否则会导致越界访问。 |
| uint32_t bufferLength | 使用的缓冲区长度。该值在默认情况下等于size（表示使用整个缓冲区），且offset与bufferLength之和不能大于size，否则会导致越界访问。 |
| uint32_t transferredLength | 已传输数据的长度。单位：Byte。在数据传输完成后由接口更新。 |


