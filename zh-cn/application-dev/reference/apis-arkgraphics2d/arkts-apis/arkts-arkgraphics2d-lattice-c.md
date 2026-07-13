# Lattice

矩形网格对象。该对象用于将图片按照矩形网格进行划分。

> **说明：**
>
> - 本Class首批接口从API version 12开始支持。
>
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## createImageLattice

```TypeScript
static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,
        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<common2D.Color> | null): Lattice
```

创建矩形网格对象。将图像划分为矩形网格，同时处于偶数列和偶数行上的网格是固定的，如果目标网格足够大，则这些固定网格以其原始大小进行绘制。如果目标网格太小，无法容纳这些固定网格，则所有固定网格都会按比例缩小以适应目标网格。其余网
格将进行缩放，来适应剩余的空间。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xDivs | Array&lt;number&gt; | 是 | 用于划分图像的X坐标值数组。该参数为整数。 |
| yDivs | Array&lt;number&gt; | 是 | 用于划分图像的Y坐标值数组。该参数为整数。 |
| fXCount | number | 是 | X坐标值数组的大小。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fYCount | number | 是 | Y坐标值数组的大小。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fBounds | common2D.Rect \| null | 否 | 可选，要绘制的原始边界矩形，矩形参数须为整数，默认为原始图像矩形大小（若矩形参数为小数，会直接舍弃小数部分，转为整数）。 |
| fRectTypes | Array&lt;RectType&gt; \| null | 否 | 可选，填充网格类型的数组，默认为空。如果设置，大小必须为(fXCount + 1) * (fYCount + 1)。 |
| fColors | Array&lt;common2D.Color&gt; \| null | 否 | 可选，填充网格的颜色数组，默认为空。如果设置，大小必须为(fXCount + 1) * (fYCount + 1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Lattice | 返回创建的矩形网格对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createImageLattice

```TypeScript
static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,
        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<number> | null): Lattice
```

创建矩形网格对象。将图像划分为矩形网格，同时处于偶数列和偶数行上的网格是固定的，如果目标网格足够大，则这些固定网格以其原始大小进行绘制。如果目标网格太小，无法容纳这些固定网格，则所有固定网格都会按比例缩小以适应目标网格。其余网
格将进行缩放，来适应剩余的空间。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xDivs | Array&lt;number&gt; | 是 | 用于划分图像的X坐标值数组。该参数为整数。 |
| yDivs | Array&lt;number&gt; | 是 | 用于划分图像的Y坐标值数组。该参数为整数。 |
| fXCount | number | 是 | X坐标值数组的大小。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fYCount | number | 是 | Y坐标值数组的大小。基于功能和性能的考虑，取值范围为[0, 5]。 |
| fBounds | common2D.Rect \| null | 否 | 可选，要绘制的原始边界矩形，矩形参数须为整数，默认为原始图像矩形大小（若矩形参数为小数，会直接舍弃小数部分，转为整数）。 |
| fRectTypes | Array&lt;RectType&gt; \| null | 否 | 可选，填充网格类型的数组，默认为空。如果设置，大小必须为(fXCount + 1) * (fYCount + 1)。 |
| fColors | Array&lt;number&gt; \| null | 否 | 可选，填充网格的颜色数组，颜色用16进制ARGB格式的32位无符号整数表示，参数默认为空。如果设置，大小必须为(fXCount + 1)* (fYCount + 1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Lattice | 返回创建的矩形网格对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

