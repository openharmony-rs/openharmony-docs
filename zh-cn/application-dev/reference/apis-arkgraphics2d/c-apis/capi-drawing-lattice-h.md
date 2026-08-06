# drawing_lattice.h

## 概述

This file declares the functions related to the rectangular lattice object.

**库：** libnative_drawing.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 23

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Drawing_LatticeRectType](#oh_drawing_latticerecttype) | OH_Drawing_LatticeRectType | 定义填充网格的矩形类型的枚举。仅在矩形网格对象中使用。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_ErrorCode OH_Drawing_LatticeDestroy(OH_Drawing_Lattice* lattice)](#oh_drawing_latticedestroy) | 用于销毁矩形网格对象并回收该对象占有的内存。 |
| [OH_Drawing_ErrorCode OH_Drawing_LatticeCreate(const int* xDivs, const int* yDivs, uint32_t xCount, uint32_t yCount, const OH_Drawing_Rect* bounds, const OH_Drawing_LatticeRectType* rectTypes, uint32_t rectTypeCount, const uint32_t* colors, uint32_t colorCount, OH_Drawing_Lattice** lattice)](#oh_drawing_latticecreate) | Divides the image into lattices. The lattices on both even columns and even rows are fixed, and they aredrawn at their original size if the target is large enough. If the target is too small to hold the fixed lattices,all the fixed lattices are scaled down to fit the target, and the lattices that are not on even columns and evenrows are scaled to accommodate the remaining space. |

## 枚举类型说明

### OH_Drawing_LatticeRectType

```c
enum OH_Drawing_LatticeRectType
```

**描述**

定义填充网格的矩形类型的枚举。仅在矩形网格对象中使用。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| DEFAULT |  |
| TRANSPARENT |  |
| FIXED_COLOR |  |


## 函数说明

### OH_Drawing_LatticeDestroy()

```c
OH_Drawing_ErrorCode OH_Drawing_LatticeDestroy(OH_Drawing_Lattice* lattice)
```

**描述**

用于销毁矩形网格对象并回收该对象占有的内存。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md)* lattice | 指向矩形网格对象[OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md)的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行结果。<br> OH_DRAWING_SUCCESS，表示执行成功。<br> OH_DRAWING_ERROR_INCORRECT_PARAMETER，表示lattice是空指针。 |

### OH_Drawing_LatticeCreate()

```c
OH_Drawing_ErrorCode OH_Drawing_LatticeCreate(const int* xDivs, const int* yDivs, uint32_t xCount, uint32_t yCount, const OH_Drawing_Rect* bounds, const OH_Drawing_LatticeRectType* rectTypes, uint32_t rectTypeCount, const uint32_t* colors, uint32_t colorCount, OH_Drawing_Lattice** lattice)
```

**描述**

Divides the image into lattices. The lattices on both even columns and even rows are fixed, and they aredrawn at their original size if the target is large enough. If the target is too small to hold the fixed lattices,all the fixed lattices are scaled down to fit the target, and the lattices that are not on even columns and evenrows are scaled to accommodate the remaining space.

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const int* xDivs | 用于划分图像的X坐标值数组。该参数为整数。 |
| const int* yDivs | 用于划分图像的Y坐标值数组。该参数为整数。 |
| uint32_t xCount | X坐标值数组的大小。取值范围为[0, 5]。 |
| uint32_t yCount | Y坐标值数组的大小。取值范围为[0, 5]。 |
| [const OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* bounds | 要绘制的原始边界矩形，默认为原始图像矩形大小。参数应为整数，向下取整。 |
| [const OH_Drawing_LatticeRectType](capi-drawing-lattice-h.md#oh_drawing_latticerecttype)* rectTypes | 填充网格的类型数组。 |
| uint32_t rectTypeCount | rectTypes数组的大小。如果rectTypes不是空指针，数组大小必须等于`(xCount + 1)*(yCount + 1)`。如果rectTypes是空指针，数组大小必须等于0。 |
| const uint32_t* colors | 填充网格的颜色数组。 |
| uint32_t colorCount | colors数组的大小。 如果colors不是空指针，数组大小必须等于`(xCount + 1)*(yCount + 1)`。如果colors是空指针，数组大小必须等于0。 |
| [OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md)** lattice | 指向矩形网格对象[OH_Drawing_Lattice](capi-drawing-oh-drawing-lattice.md)的二级指针，作为出参，返回给调用者。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行结果。<br> 返回OH_DRAWING_SUCCESS，表示执行成功。<br> 返回OH_DRAWING_ERROR_INCORRECT_PARAMETER，有以下可能原因：<br> - xDivs或yDivs是空指针nullptr；<br> - rectTypes不是空指针，且rectTypeCount不等于`(xCount + 1)(yCount + 1)`。<br> - colors不是空指针，且colorCount不等于`(xCount + 1)(yCount + 1)`。<br> - rectTypes是空指针，且rectTypeCount不等于0。<br> - colors是空指针，且colorCount不等于0。<br> 返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE，表示rectTypes中的枚举值超过枚举范围。 |


