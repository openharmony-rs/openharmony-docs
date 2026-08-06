# OH_ImageBufferData

```c
typedef struct OH_ImageBufferData {...} OH_ImageBufferData
```

## 概述

OH_ImageBufferData是native层封装的图像数据结构体。获取OH_ImageNative_GetBufferData对象使用[OH_ImageNative_GetBufferData](capi-image-native-h.md#oh_imagenative_getbufferdata)函数。<br> 结构体中保存的是对原图像数据的浅拷贝，当原数据被释放后，不应再对该结构体中的指针进行任何读写操作，否则会出现未定义行为。

**起始版本：** 23

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_native.h](capi-image-native-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t *rowStride | 图像颜色分量行间距的数组，单位为像素（px）。 |
| int32_t *pixelStride | 图像颜色分量像素间距的数组，单位为像素（px）。 |
| [](capi-image-nativemodule-oh-imagenative.md)i[](capi-image-nativemodule-oh-imagenative.md)n[](capi-image-nativemodule-oh-imagenative.md)t[](capi-image-nativemodule-oh-imagenative.md)3[](capi-image-nativemodule-oh-imagenative.md)2[](capi-image-nativemodule-oh-imagenative.md)_[](capi-image-nativemodule-oh-imagenative.md)t[](capi-image-nativemodule-oh-imagenative.md) [](capi-image-nativemodule-oh-imagenative.md) [](capi-image-nativemodule-oh-imagenative.md)n[](capi-image-nativemodule-oh-imagenative.md)u[](capi-image-nativemodule-oh-imagenative.md)m[](capi-image-nativemodule-oh-imagenative.md)S[](capi-image-nativemodule-oh-imagenative.md)t[](capi-image-nativemodule-oh-imagenative.md)r[](capi-image-nativemodule-oh-imagenative.md)i[](capi-image-nativemodule-oh-imagenative.md)d[](capi-image-nativemodule-oh-imagenative.md)e[](capi-image-nativemodule-oh-imagenative.md) | 数组长度。 |
| [](capi-image-nativemodule-oh-imagenative.md)s[](capi-image-nativemodule-oh-imagenative.md)i[](capi-image-nativemodule-oh-imagenative.md)z[](capi-image-nativemodule-oh-imagenative.md)e[](capi-image-nativemodule-oh-imagenative.md)_[](capi-image-nativemodule-oh-imagenative.md)t[](capi-image-nativemodule-oh-imagenative.md) [](capi-image-nativemodule-oh-imagenative.md) [](capi-image-nativemodule-oh-imagenative.md)b[](capi-image-nativemodule-oh-imagenative.md)u[](capi-image-nativemodule-oh-imagenative.md)f[](capi-image-nativemodule-oh-imagenative.md)f[](capi-image-nativemodule-oh-imagenative.md)e[](capi-image-nativemodule-oh-imagenative.md)r[](capi-image-nativemodule-oh-imagenative.md)S[](capi-image-nativemodule-oh-imagenative.md)i[](capi-image-nativemodule-oh-imagenative.md)z[](capi-image-nativemodule-oh-imagenative.md)e[](capi-image-nativemodule-oh-imagenative.md) | 缓冲区的大小，单位为字节（Byte）。 |
| [](capi-image-nativemodule-oh-imagenative.md)O[](capi-image-nativemodule-oh-imagenative.md)H[](capi-image-nativemodule-oh-imagenative.md)_[](capi-image-nativemodule-oh-imagenative.md)N[](capi-image-nativemodule-oh-imagenative.md)a[](capi-image-nativemodule-oh-imagenative.md)t[](capi-image-nativemodule-oh-imagenative.md)i[](capi-image-nativemodule-oh-imagenative.md)v[](capi-image-nativemodule-oh-imagenative.md)e[](capi-image-nativemodule-oh-imagenative.md)B[](capi-image-nativemodule-oh-imagenative.md)u[](capi-image-nativemodule-oh-imagenative.md)f[](capi-image-nativemodule-oh-imagenative.md)f[](capi-image-nativemodule-oh-imagenative.md)e[](capi-image-nativemodule-oh-imagenative.md)r[](capi-image-nativemodule-oh-imagenative.md) [](capi-image-nativemodule-oh-imagenative.md) [](capi-image-nativemodule-oh-imagenative.md)*[](capi-image-nativemodule-oh-imagenative.md)n[](capi-image-nativemodule-oh-imagenative.md)a[](capi-image-nativemodule-oh-imagenative.md)t[](capi-image-nativemodule-oh-imagenative.md)i[](capi-image-nativemodule-oh-imagenative.md)v[](capi-image-nativemodule-oh-imagenative.md)e[](capi-image-nativemodule-oh-imagenative.md)B[](capi-image-nativemodule-oh-imagenative.md)u[](capi-image-nativemodule-oh-imagenative.md)f[](capi-image-nativemodule-oh-imagenative.md)f[](capi-image-nativemodule-oh-imagenative.md)e[](capi-image-nativemodule-oh-imagenative.md)r[](capi-image-nativemodule-oh-imagenative.md) | 图像的OH_NativeBuffer缓冲区对象的指针。 |


