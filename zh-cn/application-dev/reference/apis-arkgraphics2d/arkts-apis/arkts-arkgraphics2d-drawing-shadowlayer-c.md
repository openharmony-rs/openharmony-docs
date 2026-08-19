# ShadowLayer

阴影层对象，通过设置模糊半径、偏移量和颜色，可为图形、文本等绘制内容添加阴影渲染效果。 > **说明：** > > - 本Class首批接口从API version 12开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

<!--Device-drawing-class ShadowLayer--><!--Device-drawing-class ShadowLayer-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## create

```TypeScript
static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer
```

创建阴影层对象。

**起始版本：** 12

<!--Device-ShadowLayer-static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer--><!--Device-ShadowLayer-static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | number | 是 | 阴影的半径，必须为大于0的浮点数。单位为物理像素px。 |
| x | number | 是 | x轴上的偏移量，该参数为浮点数。单位为物理像素px。 |
| y | number | 是 | y轴上的偏移量，该参数为浮点数。单位为物理像素px。 |
| color | common2D.Color | 是 | ARGB格式的颜色。每个颜色通道的值是[0, 255]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) | 返回创建的阴影层对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## create

```TypeScript
static create(blurRadius: double, x: double, y: double, color: common2D.Color): ShadowLayer | undefined
```

创建阴影层对象。

**起始版本：** 23

<!--Device-ShadowLayer-static create(blurRadius: double, x: double, y: double, color: common2D.Color): ShadowLayer | undefined--><!--Device-ShadowLayer-static create(blurRadius: double, x: double, y: double, color: common2D.Color): ShadowLayer | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | double | 是 | 阴影的半径，必须为大于0的浮点数。单位为物理像素px。 |
| x | double | 是 | x轴上的偏移量，该参数为浮点数。单位为物理像素px。 |
| y | double | 是 | y轴上的偏移量，该参数为浮点数。单位为物理像素px。 |
| color | common2D.Color | 是 | ARGB格式的颜色。每个颜色通道的值是[0, 255]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) | 返回创建的阴影层对象。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## create

```TypeScript
static create(blurRadius: number, x: number, y: number, color: common2D.Color | number): ShadowLayer
```

创建阴影层对象。

**起始版本：** 18

<!--Device-ShadowLayer-static create(blurRadius: number, x: number, y: number, color: common2D.Color | number): ShadowLayer--><!--Device-ShadowLayer-static create(blurRadius: number, x: number, y: number, color: common2D.Color | number): ShadowLayer-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | number | 是 | 阴影的半径，必须为大于0的浮点数。单位为物理像素px。 |
| x | number | 是 | x轴上的偏移量，该参数为浮点数。单位为物理像素px。 |
| y | number | 是 | y轴上的偏移量，该参数为浮点数。单位为物理像素px。 |
| color | common2D.Color \| number | 是 | 颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，必须是16进制ARGB格式的无符 号整数，取值范围为[0, 0xFFFFFFFF]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) | 返回创建的阴影层对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## create

```TypeScript
static create(blurRadius: double, x: double, y: double, color: common2D.Color | int): ShadowLayer | undefined
```

创建阴影层对象。

**起始版本：** 23

<!--Device-ShadowLayer-static create(blurRadius: double, x: double, y: double, color: common2D.Color | int): ShadowLayer | undefined--><!--Device-ShadowLayer-static create(blurRadius: double, x: double, y: double, color: common2D.Color | int): ShadowLayer | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blurRadius | double | 是 | 阴影的半径，必须为大于0的浮点数。单位为物理像素px。 |
| x | double | 是 | x轴上的偏移量，该参数为浮点数。单位为物理像素px。 |
| y | double | 是 | y轴上的偏移量，该参数为浮点数。单位为物理像素px。 |
| color | common2D.Color \| int | 是 | 颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，必须是16进制ARGB格式的无符 号整数，取值范围为[0, 0xFFFFFFFF]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) | 返回创建的阴影层对象。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

