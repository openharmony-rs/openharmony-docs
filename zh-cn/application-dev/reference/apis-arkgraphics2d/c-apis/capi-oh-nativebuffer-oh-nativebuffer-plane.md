# OH_NativeBuffer_Plane

```c
typedef struct OH_NativeBuffer_Plane {...} OH_NativeBuffer_Plane
```

## 概述

单个图像平面格式信息。

**起始版本：** 12

**相关模块：** [OH_NativeBuffer](capi-oh-nativebuffer.md)

**所在头文件：** [native_buffer.h](capi-native-buffer-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t offset | 平面字节偏移 |
| uint32_t rowStride | 图像一行第一个值到下一行第一个值的字节距离 |
| uint32_t columnStride | 图像一列第一个值到下一列第一个值的字节距离 |


