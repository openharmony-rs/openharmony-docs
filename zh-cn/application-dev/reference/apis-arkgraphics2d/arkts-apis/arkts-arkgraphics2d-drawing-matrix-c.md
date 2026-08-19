# Matrix

矩阵对象，用于图形的坐标变换，支持平移、旋转、缩放和倾斜等变换操作。通过矩阵变换可实现不同坐标系之间的映射。 表示为3×3的矩阵，如下图所示：  矩阵中的元素从左到右，从上到下分别表示水平缩放因子、水平倾斜系数、水平位移系数、垂直倾斜系数、垂直缩放因子、垂直位移系数、x轴透视系数、y轴透视系数、透视缩放因子。 设(x&lt;sub&gt;1&lt;/sub&gt;, y&lt;sub&gt;1&lt;/sub&gt;)为源坐标点，(x&lt;sub&gt;2&lt;/sub&gt;, y&lt;sub&gt;2&lt;/sub&gt;)为源坐标点通过矩阵变换后的坐标点，则两个坐标点的关系如下：  > **说明：** > > - 本Class首批接口从API version 12开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

<!--Device-drawing-class Matrix--><!--Device-drawing-class Matrix-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor

```TypeScript
constructor()
```

构造一个矩阵对象。

**起始版本：** 23

<!--Device-Matrix-constructor()--><!--Device-Matrix-constructor()-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## constructor

```TypeScript
constructor(matrix: Matrix)
```

拷贝一个矩阵。

**起始版本：** 23

<!--Device-Matrix-constructor(matrix: Matrix)--><!--Device-Matrix-constructor(matrix: Matrix)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 被拷贝的矩阵。 |

## getAll

```TypeScript
getAll(): Array<number>
```

获取矩阵的所有元素值。

**起始版本：** 12

<!--Device-Matrix-getAll(): Array<number>--><!--Device-Matrix-getAll(): Array<number>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 存储矩阵元素值的浮点数组，长度为9。 |

## getAll

```TypeScript
getAll(): Array<double> | undefined
```

获取矩阵的所有元素值。

**起始版本：** 23

<!--Device-Matrix-getAll(): Array<double> | undefined--><!--Device-Matrix-getAll(): Array<double> | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;double&gt; | 存储矩阵元素值的浮点数组，长度为9。获取失败时返回undefined。 |

## getValue

```TypeScript
getValue(index: int): double
```

获取矩阵给定索引位的值。索引范围0-8。

**起始版本：** 23

<!--Device-Matrix-getValue(index: int): double--><!--Device-Matrix-getValue(index: int): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 索引位置，范围0-8，该参数为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 函数返回矩阵给定索引位对应的值，该返回值为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## invert

```TypeScript
invert(matrix: Matrix): boolean
```

将矩阵matrix设置为当前矩阵的逆矩阵，并返回是否设置成功的结果。

**起始版本：** 23

<!--Device-Matrix-invert(matrix: Matrix): boolean--><!--Device-Matrix-invert(matrix: Matrix): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 矩阵对象，用于存储获取到的逆矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回matrix是否被设置为逆矩阵的结果。true表示当前矩阵可逆，matrix被设置为逆矩阵，false表示当前矩阵不可逆，matrix不被设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## isAffine

```TypeScript
isAffine(): boolean
```

判断当前矩阵是否为仿射矩阵。仿射矩阵是一种包括平移、旋转、缩放等变换的矩阵。

**起始版本：** 24

<!--Device-Matrix-isAffine(): boolean--><!--Device-Matrix-isAffine(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前矩阵是否为仿射矩阵。true表示是仿射矩阵，false表示不是仿射矩阵。 |

## isEqual

```TypeScript
isEqual(matrix: Matrix): boolean
```

判断两个矩阵是否相等。

**起始版本：** 23

<!--Device-Matrix-isEqual(matrix: Matrix): boolean--><!--Device-Matrix-isEqual(matrix: Matrix): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 另一个矩阵，用来与当前矩阵比较是否相等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回两个矩阵的比较结果。true表示两个矩阵相等，false表示两个矩阵不相等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## isIdentity

```TypeScript
isIdentity(): boolean
```

判断矩阵是否是单位矩阵。

**起始版本：** 23

<!--Device-Matrix-isIdentity(): boolean--><!--Device-Matrix-isIdentity(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回矩阵是否是单位矩阵。true表示矩阵是单位矩阵，false表示矩阵不是单位矩阵。 |

## mapPoints

```TypeScript
mapPoints(src: Array<common2D.Point>): Array<common2D.Point>
```

通过矩阵变换将源点数组映射到目标点数组。

**起始版本：** 12

<!--Device-Matrix-mapPoints(src: Array<common2D.Point>): Array<common2D.Point>--><!--Device-Matrix-mapPoints(src: Array<common2D.Point>): Array<common2D.Point>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Array&lt;common2D.Point&gt; | 是 | 源点数组，作为矩阵变换的输入点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Point&gt; | 源点数组经矩阵变换后的点数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## mapPoints

```TypeScript
mapPoints(src: Array<common2D.Point>): Array<common2D.Point> | undefined
```

通过矩阵变换将源点数组映射到目标点数组。

**起始版本：** 23

<!--Device-Matrix-mapPoints(src: Array<common2D.Point>): Array<common2D.Point> | undefined--><!--Device-Matrix-mapPoints(src: Array<common2D.Point>): Array<common2D.Point> | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Array&lt;common2D.Point&gt; | 是 | 源点数组，作为矩阵变换的输入点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;common2D.Point&gt; | 源点数组经矩阵变换后的点数组。创建对象失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## mapRadius

```TypeScript
mapRadius(radius: double): double
```

返回半径为radius的圆经过当前矩阵映射形成的椭圆的平均半径。平均半径的平方为椭圆长轴长度和短轴长度的乘积。若当前矩阵包含透视变换，则该结果无意义。

**起始版本：** 24

<!--Device-Matrix-mapRadius(radius: double): double--><!--Device-Matrix-mapRadius(radius: double): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | double | 是 | 用于计算的圆的半径，浮点数。如果是负数，则按照绝对值进行计算。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 返回经过变换之后的平均半径。单位为物理像素px。 |

## mapRect

```TypeScript
mapRect(dst: common2D.Rect, src: common2D.Rect): boolean
```

将目标矩形设置为源矩形通过矩阵变换后的图形的外接矩形。如下图所示，蓝色矩形为源矩形，假设黄色矩形为源矩形通过矩阵变换形成的图形，此时黄色矩形的边不与坐标轴平行，无法使用矩形对象表示，因此，将目标矩形设置为黄色矩形的外接矩形，即 黑色矩形。 

**起始版本：** 23

<!--Device-Matrix-mapRect(dst: common2D.Rect, src: common2D.Rect): boolean--><!--Device-Matrix-mapRect(dst: common2D.Rect, src: common2D.Rect): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dst | common2D.Rect | 是 | 目标矩形对象，用于存储源矩形经矩阵变换后的图形的外接矩形。 |
| src | common2D.Rect | 是 | 源矩形对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回源矩形经过矩阵变换后的图形是否仍然是矩形，true表示是矩形，false表示不是矩形。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## postConcat

```TypeScript
postConcat(matrix: Matrix): void
```

将一个矩阵乘在当前矩阵的左侧，即新的变换在当前矩阵的变换之后应用。如果需要在当前矩阵的变换之前应用新变换，使用preConcat方法。

**起始版本：** 24

<!--Device-Matrix-postConcat(matrix: Matrix): void--><!--Device-Matrix-postConcat(matrix: Matrix): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 表示用于运算的矩阵，位于乘法表达式左侧。 |

## postRotate

```TypeScript
postRotate(degree: double, px: double, py: double): void
```

将矩阵设置为矩阵右乘围绕旋转中心点旋转degree角度的单位矩阵后得到的矩阵，即新的旋转变换在当前矩阵的变换之后应用。如果需要在当前矩阵的变换之前应用旋转变换，使用preRotate方法。

**起始版本：** 23

<!--Device-Matrix-postRotate(degree: double, px: double, py: double): void--><!--Device-Matrix-postRotate(degree: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| degree | double | 是 | 旋转角度，单位为度。正数表示顺时针旋转，负数表示逆时针旋转，该参数为浮点数。 |
| px | double | 是 | 旋转中心点的x轴坐标，该参数为浮点数。单位为物理像素px。 |
| py | double | 是 | 旋转中心点的y轴坐标，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## postScale

```TypeScript
postScale(sx: double, sy: double, px: double, py: double): void
```

将矩阵设置为矩阵右乘围绕缩放中心点按sx和sy缩放系数缩放后的单位矩阵后得到的矩阵，即新的缩放变换在当前矩阵的变换之后应用。如果需要在当前矩阵的变换之前应用缩放变换，使用preScale方法。

**起始版本：** 23

<!--Device-Matrix-postScale(sx: double, sy: double, px: double, py: double): void--><!--Device-Matrix-postScale(sx: double, sy: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | double | 是 | x轴方向缩放因子，负数表示先关于x = px作镜像翻转后再进行缩放，该参数为浮点数。 |
| sy | double | 是 | y轴方向缩放因子，负数表示先关于y = py作镜像翻转后再进行缩放，该参数为浮点数。 |
| px | double | 是 | 缩放中心点的x轴坐标，该参数为浮点数。单位为物理像素px。 |
| py | double | 是 | 缩放中心点的y轴坐标，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## postSkew

```TypeScript
postSkew(kx: double, ky: double, px: double, py: double): void
```

当前矩阵右乘一个倾斜变换矩阵。

**起始版本：** 24

<!--Device-Matrix-postSkew(kx: double, ky: double, px: double, py: double): void--><!--Device-Matrix-postSkew(kx: double, ky: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| kx | double | 是 | x轴上的倾斜量，该参数为浮点数。正值会使绘制沿y轴增量方向向右倾斜；负值会使绘制沿y轴增量方向向左倾斜。 |
| ky | double | 是 | y轴上的倾斜量，该参数为浮点数。正值会使绘制沿x轴增量方向向下倾斜；负值会使绘制沿x轴增量方向向上倾斜。 |
| px | double | 是 | 倾斜中心点的x轴坐标，该参数为浮点数。0表示坐标原点，正数表示位于坐标原点右侧，负数表示位于坐标原点左侧。单位为物理像素px。 |
| py | double | 是 | 倾斜中心点的y轴坐标，该参数为浮点数。0表示坐标原点，正数表示位于坐标原点下侧，负数表示位于坐标原点上侧。单位为物理像素px。 |

## postTranslate

```TypeScript
postTranslate(dx: double, dy: double): void
```

将矩阵设置为矩阵右乘平移dx和dy距离后的单位矩阵后得到的矩阵，即新的平移变换在当前矩阵的变换之后应用。如果需要在当前矩阵的变换之前应用平移变换，使用preTranslate方法。

**起始版本：** 23

<!--Device-Matrix-postTranslate(dx: double, dy: double): void--><!--Device-Matrix-postTranslate(dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | double | 是 | x轴方向平移距离，正数表示往x轴正方向平移，负数表示往x轴负方向平移，该参数为浮点数。单位为物理像素px。 |
| dy | double | 是 | y轴方向平移距离，正数表示往y轴正方向平移，负数表示往y轴负方向平移，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## preConcat

```TypeScript
preConcat(matrix: Matrix): void
```

将一个矩阵乘在当前矩阵的右侧，即新的变换在当前矩阵的变换之前应用。如果需要在当前矩阵的变换之后应用新变换，使用postConcat方法。

**起始版本：** 23

<!--Device-Matrix-preConcat(matrix: Matrix): void--><!--Device-Matrix-preConcat(matrix: Matrix): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 表示用于运算的矩阵，位于乘法表达式右侧。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## preRotate

```TypeScript
preRotate(degree: double, px: double, py: double): void
```

将矩阵设置为矩阵左乘围绕旋转中心点旋转degree角度的单位矩阵后得到的矩阵，即新的旋转变换在当前矩阵的变换之前应用。如果需要在当前矩阵的变换之后应用旋转变换，使用postRotate方法。

**起始版本：** 23

<!--Device-Matrix-preRotate(degree: double, px: double, py: double): void--><!--Device-Matrix-preRotate(degree: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| degree | double | 是 | 旋转角度，单位为度。正数表示顺时针旋转，负数表示逆时针旋转，该参数为浮点数。 |
| px | double | 是 | 旋转中心点的x轴坐标，该参数为浮点数。单位为物理像素px。 |
| py | double | 是 | 旋转中心点的y轴坐标，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## preScale

```TypeScript
preScale(sx: double, sy: double, px: double, py: double): void
```

将矩阵设置为矩阵左乘围绕缩放中心点按sx和sy缩放系数缩放后的单位矩阵后得到的矩阵，即新的缩放变换在当前矩阵的变换之前应用。如果需要在当前矩阵的变换之后应用缩放变换，使用postScale方法。

**起始版本：** 23

<!--Device-Matrix-preScale(sx: double, sy: double, px: double, py: double): void--><!--Device-Matrix-preScale(sx: double, sy: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | double | 是 | x轴方向缩放因子，为负数时可看作是先关于x = px作镜像翻转后再进行缩放，该参数为浮点数。 |
| sy | double | 是 | y轴方向缩放因子，为负数时可看作是先关于y = py作镜像翻转后再进行缩放，该参数为浮点数。 |
| px | double | 是 | 缩放中心点的x轴坐标，该参数为浮点数。单位为物理像素px。 |
| py | double | 是 | 缩放中心点的y轴坐标，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## preSkew

```TypeScript
preSkew(kx: double, ky: double, px: double, py: double): void
```

当前矩阵左乘一个倾斜变换矩阵。

**起始版本：** 24

<!--Device-Matrix-preSkew(kx: double, ky: double, px: double, py: double): void--><!--Device-Matrix-preSkew(kx: double, ky: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| kx | double | 是 | x轴上的倾斜量，该参数为浮点数。正值会使绘制沿y轴增量方向向右倾斜；负值会使绘制沿y轴增量方向向左倾斜。 |
| ky | double | 是 | y轴上的倾斜量，该参数为浮点数。正值会使绘制沿x轴增量方向向下倾斜；负值会使绘制沿x轴增量方向向上倾斜。 |
| px | double | 是 | 倾斜中心点的x轴坐标，该参数为浮点数。0表示坐标原点，正数表示位于坐标原点右侧，负数表示位于坐标原点左侧。单位为物理像素px。 |
| py | double | 是 | 倾斜中心点的y轴坐标，该参数为浮点数。0表示坐标原点，正数表示位于坐标原点下侧，负数表示位于坐标原点上侧。单位为物理像素px。 |

## preTranslate

```TypeScript
preTranslate(dx: double, dy: double): void
```

将矩阵设置为矩阵左乘平移dx和dy距离后的单位矩阵后得到的矩阵，即新的平移变换在当前矩阵的变换之前应用。如果需要在当前矩阵的变换之后应用平移变换，使用postTranslate方法。

**起始版本：** 23

<!--Device-Matrix-preTranslate(dx: double, dy: double): void--><!--Device-Matrix-preTranslate(dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | double | 是 | x轴方向平移距离，正数表示往x轴正方向平移，负数表示往x轴负方向平移，该参数为浮点数。单位为物理像素px。 |
| dy | double | 是 | y轴方向平移距离，正数表示往y轴正方向平移，负数表示往y轴负方向平移，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## rectStaysRect

```TypeScript
rectStaysRect(): boolean
```

判断经过该矩阵映射后的矩形的形状是否仍为矩形。

**起始版本：** 24

<!--Device-Matrix-rectStaysRect(): boolean--><!--Device-Matrix-rectStaysRect(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回经过该矩阵映射后的矩形的形状是否仍为矩形。true表示仍是矩形，false表示不是矩形。 |

## reset

```TypeScript
reset(): void
```

重置当前矩阵为单位矩阵。

**起始版本：** 23

<!--Device-Matrix-reset(): void--><!--Device-Matrix-reset(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## setConcat

```TypeScript
setConcat(matrixA: Matrix, matrixB: Matrix): void
```

用两个矩阵的乘积更新当前矩阵，即当前矩阵 = matrixA × matrixB。

**起始版本：** 24

<!--Device-Matrix-setConcat(matrixA: Matrix, matrixB: Matrix): void--><!--Device-Matrix-setConcat(matrixA: Matrix, matrixB: Matrix): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrixA | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 用于运算的矩阵A，位于乘法表达式左侧。 |
| matrixB | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 用于运算的矩阵B，位于乘法表达式右侧。 |

## setMatrix

```TypeScript
setMatrix(values: Array<double>): void
```

设置矩阵对象的各项参数。

**起始版本：** 23

<!--Device-Matrix-setMatrix(values: Array<double>): void--><!--Device-Matrix-setMatrix(values: Array<double>): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | Array&lt;double&gt; | 是 | 长度为9的浮点数组，表示矩阵对象的各项参数。数组中的值按下标从小到大分别表示水平缩放因子、水平倾斜系数、水平位移系数（单位为物理像素px）、垂直倾斜系数、垂直 缩放因子、垂直位移系数（单位为物理像素px）、x轴透视系数、y轴透视系数和透视缩放因子。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setMatrix

```TypeScript
setMatrix(matrix: Array<double> | Matrix): void
```

用一个矩阵对当前矩阵进行更新。

**起始版本：** 24

<!--Device-Matrix-setMatrix(matrix: Array<double> | Matrix): void--><!--Device-Matrix-setMatrix(matrix: Array<double> | Matrix): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | Array&lt;double&gt; \| [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | 是 | 用于更新的数组或矩阵。当类型为数组时，长度固定为9。 |

## setPolyToPoly

```TypeScript
setPolyToPoly(src: Array<common2D.Point>, dst: Array<common2D.Point>, count: int): boolean
```

将当前矩阵设置为能够将源点数组映射到目标点数组的变换矩阵。源点和目标点的个数必须大于等于0，小于等于4。

**起始版本：** 23

<!--Device-Matrix-setPolyToPoly(src: Array<common2D.Point>, dst: Array<common2D.Point>, count: int): boolean--><!--Device-Matrix-setPolyToPoly(src: Array<common2D.Point>, dst: Array<common2D.Point>, count: int): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Array&lt;common2D.Point&gt; | 是 | 源点数组，长度必须为count。 |
| dst | Array&lt;common2D.Point&gt; | 是 | 目标点数组，长度必须为count。 |
| count | int | 是 | src和dst中点的数量，取值范围为[0, 4]，该参数为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置矩阵是否成功的结果，true表示设置成功，false表示设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setRectToRect

```TypeScript
setRectToRect(src: common2D.Rect, dst: common2D.Rect, scaleToFit: ScaleToFit): boolean
```

将当前矩阵设置为能使源矩形映射到目标矩形的变换矩阵。

**起始版本：** 23

<!--Device-Matrix-setRectToRect(src: common2D.Rect, dst: common2D.Rect, scaleToFit: ScaleToFit): boolean--><!--Device-Matrix-setRectToRect(src: common2D.Rect, dst: common2D.Rect, scaleToFit: ScaleToFit): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | common2D.Rect | 是 | 源矩形，用于指定映射的源区域。 |
| dst | common2D.Rect | 是 | 目标矩形，用于指定映射的目标区域。 |
| scaleToFit | [ScaleToFit](arkts-arkgraphics2d-drawing-scaletofit-e.md) | 是 | 源矩形到目标矩形的映射方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回矩阵是否可以表示矩形之间的映射，true表示可以，false表示不可以。如果源矩形的宽高任意一个小于等于0，则返回false，并将矩阵设置为单位矩阵；如果目标矩形的宽高任意一个小于 等于0，则返回true，并将矩阵设置为除透视缩放因子为1外其余值皆为0的矩阵。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setRotation

```TypeScript
setRotation(degree: double, px: double, py: double): void
```

设置矩阵为单位矩阵，并围绕旋转中心点(px, py)进行旋转。

**起始版本：** 23

<!--Device-Matrix-setRotation(degree: double, px: double, py: double): void--><!--Device-Matrix-setRotation(degree: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| degree | double | 是 | 角度，单位为度。正数表示顺时针旋转，负数表示逆时针旋转，该参数为浮点数。 |
| px | double | 是 | 旋转中心点的x轴坐标，该参数为浮点数。单位为物理像素px。 |
| py | double | 是 | 旋转中心点的y轴坐标，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setScale

```TypeScript
setScale(sx: double, sy: double, px: double, py: double): void
```

设置矩阵为单位矩阵，并围绕缩放中心点(px, py)按sx和sy进行缩放。

**起始版本：** 23

<!--Device-Matrix-setScale(sx: double, sy: double, px: double, py: double): void--><!--Device-Matrix-setScale(sx: double, sy: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | double | 是 | x轴方向缩放因子，为负数时可看作是先关于x = px作镜像翻转后再进行缩放，该参数为浮点数。 |
| sy | double | 是 | y轴方向缩放因子，为负数时可看作是先关于y = py作镜像翻转后再进行缩放，该参数为浮点数。 |
| px | double | 是 | 缩放中心点的x轴坐标，该参数为浮点数。单位为物理像素px。 |
| py | double | 是 | 缩放中心点的y轴坐标，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

## setSinCos

```TypeScript
setSinCos(sinValue: double, cosValue: double, px: double, py: double): void
```

设置矩阵为单位矩阵，使其围绕旋转中心点(px, py)以指定的正弦值和余弦值旋转。与[setRotation](#setrotation)功能类似，但setRotation直接传入角度 值，而本方法传入正弦值和余弦值。

**起始版本：** 24

<!--Device-Matrix-setSinCos(sinValue: double, cosValue: double, px: double, py: double): void--><!--Device-Matrix-setSinCos(sinValue: double, cosValue: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sinValue | double | 是 | 旋转角度的正弦值。仅当正弦值和余弦值的平方和为1时，为旋转变换，否则矩阵可能包含平移缩放等其他变换。 |
| cosValue | double | 是 | 旋转角度的余弦值。仅当正弦值和余弦值的平方和为1时，为旋转变换，否则矩阵可能包含平移缩放等其他变换。 |
| px | double | 是 | 旋转中心的x轴坐标，该参数为浮点数。0表示坐标原点，正数表示位于坐标原点右侧，负数表示位于坐标原点左侧。单位为物理像素px。 |
| py | double | 是 | 旋转中心的y轴坐标，该参数为浮点数。0表示坐标原点，正数表示位于坐标原点下侧，负数表示位于坐标原点上侧。单位为物理像素px。 |

## setSkew

```TypeScript
setSkew(kx: double, ky: double, px: double, py: double): void
```

设置矩阵为单位矩阵，并围绕倾斜中心点(px, py)按(kx, ky)进行倾斜变换。与[setRotation](#setrotation)、 [setScale](#setscale)、[setTranslation](#settranslation)类似，均为重置矩阵后施加单一变换。

**起始版本：** 24

<!--Device-Matrix-setSkew(kx: double, ky: double, px: double, py: double): void--><!--Device-Matrix-setSkew(kx: double, ky: double, px: double, py: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| kx | double | 是 | x轴上的倾斜量，该参数为浮点数。正值会使绘制沿y轴增量方向向右倾斜；负值会使绘制沿y轴增量方向向左倾斜。 |
| ky | double | 是 | y轴上的倾斜量，该参数为浮点数。正值会使绘制沿x轴增量方向向下倾斜；负值会使绘制沿x轴增量方向向上倾斜。 |
| px | double | 是 | 倾斜中心点的x轴坐标，该参数为浮点数。0表示坐标原点，正数表示位于坐标原点右侧，负数表示位于坐标原点左侧。单位为物理像素px。 |
| py | double | 是 | 倾斜中心点的y轴坐标，该参数为浮点数。0表示坐标原点，正数表示位于坐标原点下侧，负数表示位于坐标原点上侧。单位为物理像素px。 |

## setTranslation

```TypeScript
setTranslation(dx: double, dy: double): void
```

设置矩阵为单位矩阵，并平移(dx, dy)。

**起始版本：** 23

<!--Device-Matrix-setTranslation(dx: double, dy: double): void--><!--Device-Matrix-setTranslation(dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | double | 是 | x轴方向平移距离，正数表示往x轴正方向平移，负数表示往x轴负方向平移，该参数为浮点数。单位为物理像素px。 |
| dy | double | 是 | y轴方向平移距离，正数表示往y轴正方向平移，负数表示往y轴负方向平移，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |

