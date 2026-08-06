# drawing_point.h

## 概述

This file declares the functions related to the coordinate point in the drawing module.

**库：** libnative_drawing.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_Point* OH_Drawing_PointCreate(float x, float y)](#oh_drawing_pointcreate) | 用于创建一个坐标点对象。 |
| [OH_Drawing_ErrorCode OH_Drawing_PointGetX(const OH_Drawing_Point* point, float* x)](#oh_drawing_pointgetx) | 用于获取点的x轴坐标。 |
| [OH_Drawing_ErrorCode OH_Drawing_PointGetY(const OH_Drawing_Point* point, float* y)](#oh_drawing_pointgety) | 用于获取点的y轴坐标。 |
| [OH_Drawing_ErrorCode OH_Drawing_PointSet(OH_Drawing_Point* point, float x, float y)](#oh_drawing_pointset) | 用于设置点的x轴和y轴坐标。 |
| [OH_Drawing_ErrorCode OH_Drawing_PointNegate(OH_Drawing_Point* point)](#oh_drawing_pointnegate) | 对point对象的坐标取反。 |
| [OH_Drawing_ErrorCode OH_Drawing_PointOffset(OH_Drawing_Point* point, float dx, float dy)](#oh_drawing_pointoffset) | 对point对象的坐标分别偏移dx、dy。 |
| [void OH_Drawing_PointDestroy(OH_Drawing_Point* point)](#oh_drawing_pointdestroy) | 用于销毁坐标点对象并回收该对象占有的内存。 |

## 函数说明

### OH_Drawing_PointCreate()

```c
OH_Drawing_Point* OH_Drawing_PointCreate(float x, float y)
```

**描述**

用于创建一个坐标点对象。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| float x | X轴坐标。 |
| float y | Y轴坐标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_Point*](capi-drawing-oh-drawing-point.md) | 函数会返回一个指针，指针指向创建的坐标点对象。 |

### OH_Drawing_PointGetX()

```c
OH_Drawing_ErrorCode OH_Drawing_PointGetX(const OH_Drawing_Point* point, float* x)
```

**描述**

用于获取点的x轴坐标。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | 指向坐标点对象[OH_Drawing_Point](capi-drawing-oh-drawing-point.md)的指针。 |
| float* x | 表示点的x轴坐标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行错误码。<br> 返回OH_DRAWING_SUCCESS，表示执行成功。<br> 返回OH_DRAWING_ERROR_INVALID_PARAMETER，表示参数point或者x为空。 |

### OH_Drawing_PointGetY()

```c
OH_Drawing_ErrorCode OH_Drawing_PointGetY(const OH_Drawing_Point* point, float* y)
```

**描述**

用于获取点的y轴坐标。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | 指向坐标点对象[OH_Drawing_Point](capi-drawing-oh-drawing-point.md)的指针。 |
| float* y | 表示点的y轴坐标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行错误码。<br> 返回OH_DRAWING_SUCCESS，表示执行成功。<br> 返回OH_DRAWING_ERROR_INVALID_PARAMETER，表示参数point或者y为空。 |

### OH_Drawing_PointSet()

```c
OH_Drawing_ErrorCode OH_Drawing_PointSet(OH_Drawing_Point* point, float x, float y)
```

**描述**

用于设置点的x轴和y轴坐标。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | 指向坐标点对象[OH_Drawing_Point](capi-drawing-oh-drawing-point.md)的指针。 |
| float x | 表示点的x轴坐标。 |
| float y | 表示点的y轴坐标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行错误码。<br> 返回OH_DRAWING_SUCCESS，表示执行成功。<br> 返回OH_DRAWING_ERROR_INVALID_PARAMETER，表示参数point为空。 |

### OH_Drawing_PointNegate()

```c
OH_Drawing_ErrorCode OH_Drawing_PointNegate(OH_Drawing_Point* point)
```

**描述**

对point对象的坐标取反。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | 需要被操作的point对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 返回错误码。<br>  操作成功时，返回 [OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode).<br>  Point对象指针为空时，返回 [OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) |

### OH_Drawing_PointOffset()

```c
OH_Drawing_ErrorCode OH_Drawing_PointOffset(OH_Drawing_Point* point, float dx, float dy)
```

**描述**

对point对象的坐标分别偏移dx、dy。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | 表示被操作的point对象指针。 |
| float dx | 表示x轴方向的偏移量，单位为像素。 |
| float dy | 表示y轴方向的偏移量，单位为像素。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 返回错误码。<br>  操作成功时，返回[OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode).<br>  Point对象指针为空时，返回 [OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) |

### OH_Drawing_PointDestroy()

```c
void OH_Drawing_PointDestroy(OH_Drawing_Point* point)
```

**描述**

用于销毁坐标点对象并回收该对象占有的内存。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | 指向坐标点对象的指针。 |


