# drawing_color_space.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 概述

声明与绘图模块中的颜色空间对象相关的函数。颜色空间用于定义颜色的解释和映射方式，确保图像在不同显示设备上的一致性呈现。本文件提供创建标准颜色空间（sRGB）和线性颜色空间（sRGB Linear）的函数，以及销毁颜色空间对象并回收内存的函数，用于图像渲染和色彩管理等场景。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**引用文件：** <native_drawing/drawing_color_space.h>

**库：** libnative_drawing.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)](#oh_drawing_colorspacecreatesrgb) | 创建一个标准sRGB颜色空间。适用于需要将颜色值按照sRGB标准进行解释和渲染的场景。创建的颜色空间对象使用完毕后必须调用[OH_Drawing_ColorSpaceDestroy](#oh_drawing_colorspacedestroy)销毁并释放内存，否则会导致内存泄漏。 |
| [OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)](#oh_drawing_colorspacecreatesrgblinear) | 创建一个Gamma值为1.0的线性颜色空间。与OH_Drawing_ColorSpaceCreateSrgb创建的标准sRGB颜色空间不同，线性颜色空间适用于需要进行线性颜色计算（如混合、光照等）的场景。创建的颜色空间对象使用完毕后必须调用[OH_Drawing_ColorSpaceDestroy](#oh_drawing_colorspacedestroy)销毁并释放内存，否则会导致内存泄漏。 |
| [void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)](#oh_drawing_colorspacedestroy) | 销毁颜色空间对象，并回收该对象占用的内存。 |

## 函数说明

### OH_Drawing_ColorSpaceCreateSrgb()

```c
OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgb(void)
```

**描述**

创建一个标准sRGB颜色空间。适用于需要将颜色值按照sRGB标准进行解释和渲染的场景。创建的颜色空间对象使用完毕后必须调用[OH_Drawing_ColorSpaceDestroy](#oh_drawing_colorspacedestroy)销毁并释放内存，否则会导致内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* | 返回一个指向创建的颜色空间对象[OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)的指针。 |

### OH_Drawing_ColorSpaceCreateSrgbLinear()

```c
OH_Drawing_ColorSpace* OH_Drawing_ColorSpaceCreateSrgbLinear(void)
```

**描述**

创建一个Gamma值为1.0的线性颜色空间。与OH_Drawing_ColorSpaceCreateSrgb创建的标准sRGB颜色空间不同，线性颜色空间适用于需要进行线性颜色计算（如混合、光照等）的场景。创建的颜色空间对象使用完毕后必须调用[OH_Drawing_ColorSpaceDestroy](#oh_drawing_colorspacedestroy)销毁并释放内存，否则会导致内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* | 返回一个指向创建的颜色空间对象[OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)的指针。 |

### OH_Drawing_ColorSpaceDestroy()

```c
void OH_Drawing_ColorSpaceDestroy(OH_Drawing_ColorSpace* colorSpace)
```

**描述**

销毁颜色空间对象，并回收该对象占用的内存。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)* colorSpace | 指向待销毁的颜色空间对象[OH_Drawing_ColorSpace](capi-drawing-oh-drawing-colorspace.md)的指针。 |

