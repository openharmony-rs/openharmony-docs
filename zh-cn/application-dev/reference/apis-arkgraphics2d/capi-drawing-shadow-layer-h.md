# drawing_shadow_layer.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 概述

声明与绘图模块中的阴影层对象相关的函数，用于创建和销毁阴影层对象。阴影层用于为绘图内容添加阴影效果，支持通过设置模糊半径、偏移量和颜色来创建阴影层，适用于需要为图形或文本添加阴影渲染的场景。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**引用文件：** \<native_drawing/drawing_shadow_layer.h\>

**库：** libnative_drawing.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_ShadowLayer* OH_Drawing_ShadowLayerCreate(float blurRadius, float x, float y, uint32_t color)](#oh_drawing_shadowlayercreate) | 创建一个阴影层对象，适用于为图形或文本添加阴影效果。创建的阴影层对象在使用完毕后，必须调用[OH_Drawing_ShadowLayerDestroy](#oh_drawing_shadowlayerdestroy)进行销毁并释放内存，否则会导致内存泄漏。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>blurRadius小于等于0时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE，请将blurRadius设置为大于0的值。 |
| [void OH_Drawing_ShadowLayerDestroy(OH_Drawing_ShadowLayer* shadowLayer)](#oh_drawing_shadowlayerdestroy) | 销毁阴影层对象，并回收该对象占用的内存。 |

## 函数说明

### OH_Drawing_ShadowLayerCreate()

```c
OH_Drawing_ShadowLayer* OH_Drawing_ShadowLayerCreate(float blurRadius, float x, float y, uint32_t color)
```

**描述**

创建一个阴影层对象，适用于为图形或文本添加阴影效果。创建的阴影层对象在使用完毕后，必须调用[OH_Drawing_ShadowLayerDestroy](#oh_drawing_shadowlayerdestroy)进行销毁并释放内存，否则会导致内存泄漏。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>blurRadius小于等于0时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE，请将blurRadius设置为大于0的值。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| float blurRadius | 表示阴影的模糊半径，必须大于0。单位为px。 |
| float x | 表示x轴上的偏移量。单位为px。 |
| float y | 表示y轴上的偏移量。单位为px。 |
| uint32_t color | 表示阴影的颜色，颜色格式为ARGB（0xAARRGGBB）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShadowLayer](capi-drawing-oh-drawing-shadowlayer.md)* | 返回创建的阴影层对象的指针。 |

### OH_Drawing_ShadowLayerDestroy()

```c
void OH_Drawing_ShadowLayerDestroy(OH_Drawing_ShadowLayer* shadowLayer)
```

**描述**

销毁阴影层对象，并回收该对象占用的内存。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_ShadowLayer](capi-drawing-oh-drawing-shadowlayer.md)* shadowLayer | 表示指向阴影层对象的指针。 |

