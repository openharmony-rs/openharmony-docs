# Brush

画刷对象，描述所绘制图形的填充信息。

> **说明：**  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 11

<!--Device-drawing-class Brush--><!--Device-drawing-class Brush-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor

```TypeScript
constructor()
```

构造一个新的画刷对象。

**起始版本：** 12

<!--Device-Brush-constructor()--><!--Device-Brush-constructor()-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## constructor

```TypeScript
constructor(brush: Brush)
```

复制构造一个新的画刷对象。

**起始版本：** 12

<!--Device-Brush-constructor(brush: Brush)--><!--Device-Brush-constructor(brush: Brush)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brush | [Brush](arkts-arkgraphics2d-drawing-brush-c.md) | 是 | 待复制的画刷对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## getAlpha

```TypeScript
getAlpha(): number
```

获取画刷的透明度。

**起始版本：** 12

<!--Device-Brush-getAlpha(): int--><!--Device-Brush-getAlpha(): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回画刷的透明度，该返回值为0到255之间的整数。 |

## getColor

```TypeScript
getColor(): common2D.Color
```

获取画刷的颜色。

**起始版本：** 12

<!--Device-Brush-getColor(): common2D.Color--><!--Device-Brush-getColor(): common2D.Color-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Color | Color of the brush. |

## getColor4f

```TypeScript
getColor4f(): common2D.Color4f
```

获取画刷的颜色，与[getColor](arkts-arkgraphics2d-drawing-brush-c.md#getcolor-1)的区别是返回值类型为浮点数，适用于需要浮点数类型的场景。

**起始版本：** 20

<!--Device-Brush-getColor4f(): common2D.Color4f--><!--Device-Brush-getColor4f(): common2D.Color4f-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Color4f | Color of the brush. |

## getColorFilter

```TypeScript
getColorFilter(): ColorFilter
```

获取画刷的颜色滤波器。

**起始版本：** 12

<!--Device-Brush-getColorFilter(): ColorFilter--><!--Device-Brush-getColorFilter(): ColorFilter-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorFilter](../../apis-arkui/arkts-apis/arkts-arkui-units-colorfilter-c.md) | 返回颜色滤波器。 |

## getHexColor

```TypeScript
getHexColor(): number
```

获取画刷的颜色。

**起始版本：** 18

<!--Device-Brush-getHexColor(): int--><!--Device-Brush-getHexColor(): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回画刷的颜色，以16进制ARGB格式的32位无符号整数表示。 |

## isAntiAlias

```TypeScript
isAntiAlias(): boolean
```

获取画刷是否开启抗锯齿属性。

**起始版本：** 12

<!--Device-Brush-isAntiAlias(): boolean--><!--Device-Brush-isAntiAlias(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回画刷是否开启抗锯齿属性，true表示开启，false表示关闭。 |

## reset

```TypeScript
reset(): void
```

重置当前画刷为初始状态。

**起始版本：** 12

<!--Device-Brush-reset(): void--><!--Device-Brush-reset(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## setAlpha

```TypeScript
setAlpha(alpha: number): void
```

设置画刷的透明度。

**起始版本：** 11

<!--Device-Brush-setAlpha(alpha: int): void--><!--Device-Brush-setAlpha(alpha: int): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alpha | number | 是 | 用于表示透明度的[0, 255]区间内的整数值，传入浮点类型时向下取整。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setAntiAlias

```TypeScript
setAntiAlias(aa: boolean): void
```

设置画刷是否开启抗锯齿。开启后，可以使得图形的边缘在显示时更平滑。未调用此接口设置时，系统默认关闭抗锯齿。

**起始版本：** 11

<!--Device-Brush-setAntiAlias(aa: boolean): void--><!--Device-Brush-setAntiAlias(aa: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aa | boolean | 是 | 表示是否开启抗锯齿，true表示开启，false表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setBlendMode

```TypeScript
setBlendMode(mode: BlendMode): void
```

设置画刷的混合模式。未调用此接口设置时，系统默认的混合模式为SRC_OVER。

**起始版本：** 11

<!--Device-Brush-setBlendMode(mode: BlendMode): void--><!--Device-Brush-setBlendMode(mode: BlendMode): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [BlendMode](../../apis-arkui/arkts-components/arkts-arkui-common-blendmode-e.md) | 是 | 颜色的混合模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setColor

```TypeScript
setColor(color: common2D.Color): void
```

设置画刷的颜色。

**起始版本：** 11

<!--Device-Brush-setColor(color: common2D.Color): void--><!--Device-Brush-setColor(color: common2D.Color): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color | 是 | ARGB格式的颜色，每个颜色通道的值是0到255之间的整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setColor

```TypeScript
setColor(alpha: number, red: number, green: number, blue: number): void
```

设置画刷的颜色。性能优于[setColor](arkts-arkgraphics2d-drawing-brush-c.md#setcolor-1)接口，推荐使用本接口。

**起始版本：** 12

<!--Device-Brush-setColor(alpha: int, red: int, green: int, blue: int): void--><!--Device-Brush-setColor(alpha: int, red: int, green: int, blue: int): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alpha | number | 是 | ARGB格式颜色的透明度通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。 |
| red | number | 是 | ARGB格式颜色的红色通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。 |
| green | number | 是 | ARGB格式颜色的绿色通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。 |
| blue | number | 是 | ARGB格式颜色的蓝色通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setColor

```TypeScript
setColor(color: number): void
```

设置画刷的颜色。

**起始版本：** 18

<!--Device-Brush-setColor(color: int): void--><!--Device-Brush-setColor(color: int): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | number | 是 | 16进制ARGB格式的颜色。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setColor4f

```TypeScript
setColor4f(color4f: common2D.Color4f, colorSpace: colorSpaceManager.ColorSpaceManager | null): void
```

设置画刷的颜色以及标准色域，与[setColor](arkts-arkgraphics2d-drawing-brush-c.md#setcolor-1)区别在于可以单独设置色域，适用于需要单独设置色域的场景。

**起始版本：** 20

<!--Device-Brush-setColor4f(color4f: common2D.Color4f, colorSpace: colorSpaceManager.ColorSpaceManager | null): void--><!--Device-Brush-setColor4f(color4f: common2D.Color4f, colorSpace: colorSpaceManager.ColorSpaceManager | null): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color4f | common2D.Color4f | 是 | ARGB格式的颜色，每个颜色通道的值是0.0-1.0之间的浮点数，大于1.0时，取1.0，小于0.0时，取0.0。 |
| colorSpace | colorSpaceManager.ColorSpaceManager \| null | 是 | 标准色域对象，null表示使用SRGB色域。 |

## setColorFilter

```TypeScript
setColorFilter(filter: ColorFilter | null): void
```

给画刷添加额外的颜色滤波器。

**起始版本：** 11

<!--Device-Brush-setColorFilter(filter: ColorFilter | null): void--><!--Device-Brush-setColorFilter(filter: ColorFilter | null): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | ColorFilter \| null | 是 | 颜色滤波器。null表示清空颜色滤波器。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setImageFilter

```TypeScript
setImageFilter(filter: ImageFilter | null): void
```

为画刷设置图像滤波器。

**起始版本：** 12

<!--Device-Brush-setImageFilter(filter: ImageFilter | null): void--><!--Device-Brush-setImageFilter(filter: ImageFilter | null): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | ImageFilter \| null | 是 | 图像滤波器，null表示清空图像滤波器效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setMaskFilter

```TypeScript
setMaskFilter(filter: MaskFilter | null): void
```

给画刷添加额外的蒙版滤镜。

**起始版本：** 12

<!--Device-Brush-setMaskFilter(filter: MaskFilter | null): void--><!--Device-Brush-setMaskFilter(filter: MaskFilter | null): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | MaskFilter \| null | 是 | 蒙版滤镜。null表示清空蒙版滤镜。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setShaderEffect

```TypeScript
setShaderEffect(shaderEffect: ShaderEffect | null): void
```

设置画刷着色器效果。

**起始版本：** 12

<!--Device-Brush-setShaderEffect(shaderEffect: ShaderEffect | null): void--><!--Device-Brush-setShaderEffect(shaderEffect: ShaderEffect | null): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shaderEffect | ShaderEffect \| null | 是 | 着色器对象。null表示清空着色器效果。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setShadowLayer

```TypeScript
setShadowLayer(shadowLayer: ShadowLayer | null): void
```

设置画刷阴影层效果。当前仅在绘制文字时生效。

**起始版本：** 12

<!--Device-Brush-setShadowLayer(shadowLayer: ShadowLayer | null): void--><!--Device-Brush-setShadowLayer(shadowLayer: ShadowLayer | null): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shadowLayer | ShadowLayer \| null | 是 | 阴影层对象。null表示清空阴影层效果。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

