# Lattice

矩形网格对象。该对象用于将图像按照矩形网格进行划分，支持固定指定网格区域、缩放其余网格实现局部拉伸、自定义网格绘制类型、网格颜色填充以及指定绘制边界矩形等能力。创建Lattice对象后，需配合 [Canvas.drawImageLattice](arkts-arkgraphics2d-drawing-canvas-c.md#drawimagelattice)方法使用以实现图像的局部拉伸绘制。 > **说明：** > > - 本Class首批接口从API version 12开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

<!--Device-drawing-class Lattice--><!--Device-drawing-class Lattice-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## createImageLattice

```TypeScript
static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,
        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<common2D.Color> | null): Lattice
```

创建矩形网格对象。将图像划分为矩形网格，同时处于偶数列和偶数行上的网格是固定的，如果目标网格足够大，则这些固定网格以其原始大小进行绘制，其余网格将进行缩放，来适应剩余的空间。如果目标网格太小，无法容纳这些固定网格，则所有固定网 格都会按比例缩小以适应目标网格。

**起始版本：** 12

<!--Device-Lattice-static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<common2D.Color> | null): Lattice--><!--Device-Lattice-static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<common2D.Color> | null): Lattice-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xDivs | Array&lt;number&gt; | 是 | 用于划分图像的X坐标值数组，单位为物理像素px。数组元素需为整数。若传入小数，会直接舍弃小数部分，转为整数。 |
| yDivs | Array&lt;number&gt; | 是 | 用于划分图像的Y坐标值数组，单位为物理像素px。数组元素需为整数。若传入小数，会直接舍弃小数部分，转为整数。 |
| fXCount | number | 是 | X坐标值数组的元素个数，需与xDivs数组的长度一致。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fYCount | number | 是 | Y坐标值数组的元素个数，需与yDivs数组的长度一致。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fBounds | common2D.Rect \| null | 否 | 要绘制的原始边界矩形。当仅需绘制图像的局部区域时传入此参数，不传入时默认为原始图像矩形大小。矩形参数需为整数，单位为物理像素px（若矩形参 数为小数，会直接舍弃小数部分，转为整数）。 |
| fRectTypes | Array&lt;RectType&gt; \| null | 否 | 填充矩形网格类型的数组，用于指定每个矩形网格的绘制类型，默认为空。如果设置，大小必须为(fXCount + 1) ( fYCount + 1)。 |
| fColors | Array&lt;common2D.Color&gt; \| null | 否 | 填充网格的颜色数组，用于为每个网格单元格指定填充颜色，设置后对应网格区域将以指定颜色进行纯色填充，替换原有图像内容。不传入 时默认为空（网格不使用自定义颜色填充，保留原始图像内容）。如果设置，大小必须为(fXCount + 1) (fYCount + 1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Lattice](arkts-arkgraphics2d-drawing-lattice-c.md) | 返回创建的矩形网格对象，该对象可传入绘制接口以实现图像局部拉伸——固定网格保持原始大小、其余网格自适应缩放填充剩余空间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createImageLattice

```TypeScript
static createImageLattice(xDivs: Array<int>, yDivs: Array<int>, fXCount: int, fYCount: int,
        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<common2D.Color> | null): Lattice | undefined
```

创建矩形网格对象。将图像划分为矩形网格，同时处于偶数列和偶数行上的网格是固定的，如果目标网格足够大，则这些固定网格以其原始大小进行绘制，其余网格将进行缩放，来适应剩余的空间。如果目标网格太小，无法容纳这些固定网格，则所有固定网 格都会按比例缩小以适应目标网格。

**起始版本：** 23

<!--Device-Lattice-static createImageLattice(xDivs: Array<int>, yDivs: Array<int>, fXCount: int, fYCount: int,        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<common2D.Color> | null): Lattice | undefined--><!--Device-Lattice-static createImageLattice(xDivs: Array<int>, yDivs: Array<int>, fXCount: int, fYCount: int,        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<common2D.Color> | null): Lattice | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xDivs | Array&lt;int&gt; | 是 | 用于划分图像的X坐标值数组，单位为物理像素px。数组元素需为整数。若传入小数，会直接舍弃小数部分，转为整数。 |
| yDivs | Array&lt;int&gt; | 是 | 用于划分图像的Y坐标值数组，单位为物理像素px。数组元素需为整数。若传入小数，会直接舍弃小数部分，转为整数。 |
| fXCount | int | 是 | X坐标值数组的元素个数，需与xDivs数组的长度一致。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fYCount | int | 是 | Y坐标值数组的元素个数，需与yDivs数组的长度一致。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fBounds | common2D.Rect \| null | 否 | 要绘制的原始边界矩形。当仅需绘制图像的局部区域时传入此参数，不传入时默认为原始图像矩形大小。矩形参数需为整数，单位为物理像素px（若矩形参 数为小数，会直接舍弃小数部分，转为整数）。 |
| fRectTypes | Array&lt;RectType&gt; \| null | 否 | 填充矩形网格类型的数组，用于指定每个矩形网格的绘制类型，默认为空。如果设置，大小必须为(fXCount + 1) ( fYCount + 1)。 |
| fColors | Array&lt;common2D.Color&gt; \| null | 否 | 填充网格的颜色数组，用于为每个网格单元格指定填充颜色，设置后对应网格区域将以指定颜色进行纯色填充，替换原有图像内容。不传入 时默认为空（网格不使用自定义颜色填充，保留原始图像内容）。如果设置，大小必须为(fXCount + 1) (fYCount + 1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Lattice](arkts-arkgraphics2d-drawing-lattice-c.md) | 返回创建的矩形网格对象，该对象可传入绘制接口以实现图像局部拉伸——固定网格保持原始大小、其余网格自适应缩放填充剩余空间。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createImageLattice

```TypeScript
static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,
        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<number> | null): Lattice
```

创建矩形网格对象。将图像划分为矩形网格，同时处于偶数列和偶数行上的网格是固定的，如果目标网格足够大，则这些固定网格以其原始大小进行绘制，其余网格将进行缩放，以适应剩余的空间。如果目标网格太小，无法容纳这些固定网格，则所有固定网 格都会按比例缩小以适应目标网格。

**起始版本：** 18

<!--Device-Lattice-static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<number> | null): Lattice--><!--Device-Lattice-static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<number> | null): Lattice-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xDivs | Array&lt;number&gt; | 是 | 用于划分图像的X坐标值数组，单位为物理像素px。数组元素需为整数。若传入小数，会直接舍弃小数部分，转为整数。 |
| yDivs | Array&lt;number&gt; | 是 | 用于划分图像的Y坐标值数组，单位为物理像素px。数组元素需为整数。若传入小数，会直接舍弃小数部分，转为整数。 |
| fXCount | number | 是 | X坐标值数组的元素个数，需与xDivs数组的长度一致。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fYCount | number | 是 | Y坐标值数组的元素个数，需与yDivs数组的长度一致。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fBounds | common2D.Rect \| null | 否 | 要绘制的原始边界矩形。当仅需绘制图像的局部区域时传入此参数，不传入时默认为原始图像矩形大小。矩形参数需为整数，单位为物理像素px（若矩形参 数为小数，会直接舍弃小数部分，转为整数）。 |
| fRectTypes | Array&lt;RectType&gt; \| null | 否 | 填充矩形网格类型的数组，用于指定每个矩形网格的绘制类型，默认为空。如果设置，大小必须为(fXCount + 1) ( fYCount + 1)。 |
| fColors | Array&lt;number&gt; \| null | 否 | 填充网格的颜色数组，用于为每个网格单元格指定填充颜色，设置后对应网格区域将以指定颜色进行纯色填充，替换原有图像内容。颜色用16进制ARGB 格式的32位无符号整数表示，取值范围[0, 4294967295]。不传入时默认为空（网格不使用自定义颜色填充，保留原始图像内容）。如果设置，大小必须为(fXCount + 1) (fYCount + 1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Lattice](arkts-arkgraphics2d-drawing-lattice-c.md) | 返回创建的矩形网格对象，该对象可传入绘制接口以实现图像局部拉伸——固定网格保持原始大小、其余网格自适应缩放填充剩余空间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createImageLatticeWithArrayInt

```TypeScript
static createImageLatticeWithArrayInt(xDivs: Array<int>, yDivs: Array<int>, fXCount: int, fYCount: int,
        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<int> | null): Lattice | undefined
```

创建矩形网格对象。将图像划分为矩形网格，同时处于偶数列和偶数行上的网格是固定的，如果目标网格足够大，则这些固定网格以其原始大小进行绘制，其余网格将进行缩放，以适应剩余的空间。如果目标网格太小，无法容纳这些固定网格，则所有固定网 格都会按比例缩小以适应目标网格。

**起始版本：** 23

<!--Device-Lattice-static createImageLatticeWithArrayInt(xDivs: Array<int>, yDivs: Array<int>, fXCount: int, fYCount: int,        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<int> | null): Lattice | undefined--><!--Device-Lattice-static createImageLatticeWithArrayInt(xDivs: Array<int>, yDivs: Array<int>, fXCount: int, fYCount: int,        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<int> | null): Lattice | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xDivs | Array&lt;int&gt; | 是 | 用于划分图像的X坐标值数组，单位为物理像素px。数组元素需为整数。若传入小数，会直接舍弃小数部分，转为整数。 |
| yDivs | Array&lt;int&gt; | 是 | 用于划分图像的Y坐标值数组，单位为物理像素px。数组元素需为整数。若传入小数，会直接舍弃小数部分，转为整数。 |
| fXCount | int | 是 | X坐标值数组的元素个数，需与xDivs数组的长度一致。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fYCount | int | 是 | Y坐标值数组的元素个数，需与yDivs数组的长度一致。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fBounds | common2D.Rect \| null | 否 | 要绘制的原始边界矩形。当仅需绘制图像的局部区域时传入此参数，不传入时默认为原始图像矩形大小。矩形参数需为整数，单位为物理像素px（若矩形参 数为小数，会直接舍弃小数部分，转为整数）。 |
| fRectTypes | Array&lt;RectType&gt; \| null | 否 | 填充矩形网格类型的数组，用于指定每个矩形网格的绘制类型，默认为空。如果设置，大小必须为(fXCount + 1) ( fYCount + 1)。 |
| fColors | Array&lt;int&gt; \| null | 否 | 填充网格的颜色数组，用于为每个网格单元格指定填充颜色，设置后对应网格区域将以指定颜色进行纯色填充，替换原有图像内容。颜色用16进制ARGB 格式的32位无符号整数表示，取值范围[0, 4294967295]。不传入时默认为空（网格不使用自定义颜色填充，保留原始图像内容）。如果设置，大小必须为(fXCount + 1) (fYCount + 1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Lattice](arkts-arkgraphics2d-drawing-lattice-c.md) | 返回创建的矩形网格对象，该对象可传入绘制接口以实现图像局部拉伸——固定网格保持原始大小、其余网格自适应缩放填充剩余空间。创建失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

