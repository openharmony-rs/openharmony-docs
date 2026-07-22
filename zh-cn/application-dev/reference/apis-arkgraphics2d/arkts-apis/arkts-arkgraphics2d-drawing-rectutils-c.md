# RectUtils

提供了处理矩形的工具。主要的使用场景：

1. 矩形快速构建与获取基本属性，如构造新矩形、拷贝矩形、获取矩形的宽高以及中心点等。2. 边界计算与调整，如获取包含关系、计算与更新矩形之间交集和并集，更新边界值等。
> **说明：**  
>  
> - 本Class首批接口从API version 20开始支持。  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 20

<!--Device-drawing-class RectUtils--><!--Device-drawing-class RectUtils-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## centerX

```TypeScript
static centerX(rect: common2D.Rect): number
```

获取矩形中心的横坐标。

**起始版本：** 20

<!--Device-RectUtils-static centerX(rect: common2D.Rect): double--><!--Device-RectUtils-static centerX(rect: common2D.Rect): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回矩形中心的横坐标。 |

## centerY

```TypeScript
static centerY(rect: common2D.Rect): number
```

获取矩形中心的纵坐标。

**起始版本：** 20

<!--Device-RectUtils-static centerY(rect: common2D.Rect): double--><!--Device-RectUtils-static centerY(rect: common2D.Rect): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回矩形中心的纵坐标。 |

## contains

```TypeScript
static contains(rect: common2D.Rect, other: common2D.Rect): boolean
```

判断一个矩形是否完全包含另外一个矩形。

**起始版本：** 20

<!--Device-RectUtils-static contains(rect: common2D.Rect, other: common2D.Rect): boolean--><!--Device-RectUtils-static contains(rect: common2D.Rect, other: common2D.Rect): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形对象。 |
| other | common2D.Rect | 是 | 判断是否被包含的矩形对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回矩形是否完全包含另一个矩形的结果。true表示指定矩形在另一个矩形内部或者相等，false表示指定矩形在另一个矩形外部。空的矩形不包含任何矩形。 |

## contains

```TypeScript
static contains(rect: common2D.Rect, left: number, top: number, right: number, bottom: number): boolean
```

判断一个矩形是否完全包含另外一个矩形（另一个矩形分别用左上右下坐标表示）。

**起始版本：** 20

<!--Device-RectUtils-static contains(rect: common2D.Rect, left: double, top: double, right: double, bottom: double): boolean--><!--Device-RectUtils-static contains(rect: common2D.Rect, left: double, top: double, right: double, bottom: double): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形对象。 |
| left | number | 是 | 矩形的左上角x轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| top | number | 是 | 矩形的左上角y轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |
| right | number | 是 | 矩形的右下角x轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| bottom | number | 是 | 矩形的右下角y轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回矩形是否完全包含由左上右下坐标组成的矩形的结果。true表示指定左上右下坐标组成的矩形在矩形的内部或者相等，false表示指定左上右下坐标组成的矩形在矩形的外部。空的矩形不包含任何矩形。 |

## contains

```TypeScript
static contains(rect: common2D.Rect, x: number, y: number): boolean
```

判断一个矩形是否完全包含一个点。

**起始版本：** 20

<!--Device-RectUtils-static contains(rect: common2D.Rect, x: double, y: double): boolean--><!--Device-RectUtils-static contains(rect: common2D.Rect, x: double, y: double): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形对象。 |
| x | number | 是 | 要判断点的x轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| y | number | 是 | 要判断点的y轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回矩形是否完全包含x、y组成的点的结果。true表示矩形完全包含x、y组成的点，false表示矩形不完全包含x、y组成的点。左边界和上边界属于矩形内部，右边界和下边界不属于矩形内部。空的矩形不包含任何点。 |

## getHeight

```TypeScript
static getHeight(rect: common2D.Rect): number
```

获取矩形的高度。

**起始版本：** 20

<!--Device-RectUtils-static getHeight(rect: common2D.Rect): double--><!--Device-RectUtils-static getHeight(rect: common2D.Rect): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回矩形的高。如果矩形的上边界大于下边界，获取的高度为负值，上边界小于下边界则为正值。 |

## getWidth

```TypeScript
static getWidth(rect: common2D.Rect): number
```

获取矩形的宽度。

**起始版本：** 20

<!--Device-RectUtils-static getWidth(rect: common2D.Rect): double--><!--Device-RectUtils-static getWidth(rect: common2D.Rect): double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回矩形的宽。如果矩形的左边界大于右边界，获取的宽度为负值，左边界小于右边界则为正值。 |

## inset

```TypeScript
static inset(rect: common2D.Rect, left: number, top: number, right: number, bottom: number): void
```

将指定矩形的左边界、上边界、右边界和下边界分别和传入的"左上右下"的值相加。

**起始版本：** 20

<!--Device-RectUtils-static inset(rect: common2D.Rect, left: double, top: double, right: double, bottom: double): void--><!--Device-RectUtils-static inset(rect: common2D.Rect, left: double, top: double, right: double, bottom: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形对象。 |
| left | number | 是 | 添加到矩形左边界的值（矩形左上角横坐标），该参数为浮点数。0表示不进行任何运算，正数表示进行相加运算，负数表示相减运算。 |
| top | number | 是 | 添加到矩形上边界的值（矩形左上角纵坐标），该参数为浮点数。0表示不进行任何运算，正数表示进行相加运算，负数表示相减运算。 |
| right | number | 是 | 添加到矩形右边界的值（矩形右下角横坐标），该参数为浮点数。0表示不进行任何运算，正数表示进行相加运算，负数表示相减运算。 |
| bottom | number | 是 | 添加到矩形下边界的值（矩形右下角纵坐标），该参数为浮点数。0表示不进行任何运算，正数表示进行相加运算，负数表示相减运算。 |

## intersect

```TypeScript
static intersect(rect: common2D.Rect, other: common2D.Rect): boolean
```

计算两个矩形的交集区域，并将交集结果更新到第一个入参代表的矩形区域。

**起始版本：** 20

<!--Device-RectUtils-static intersect(rect: common2D.Rect, other: common2D.Rect): boolean--><!--Device-RectUtils-static intersect(rect: common2D.Rect, other: common2D.Rect): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 用于计算交集的原矩形。 |
| other | common2D.Rect | 是 | 用于计算交集的另一个矩形。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回两个矩形是否有交集的结果。true表示两个矩形有交集，false表示两个矩形没有交集。 |

## isEmpty

```TypeScript
static isEmpty(rect: common2D.Rect): boolean
```

判断矩形是否为空（左边界大于等于右边界或者上边界大于等于下边界）。

**起始版本：** 20

<!--Device-RectUtils-static isEmpty(rect: common2D.Rect): boolean--><!--Device-RectUtils-static isEmpty(rect: common2D.Rect): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 用于判断的矩形对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回矩形是否为空的结果。true表示矩形是空，false表示矩形不为空。 |

## isEqual

```TypeScript
static isEqual(rect: common2D.Rect, other: common2D.Rect): boolean
```

判断两个矩形是否相等。

**起始版本：** 20

<!--Device-RectUtils-static isEqual(rect: common2D.Rect, other: common2D.Rect): boolean--><!--Device-RectUtils-static isEqual(rect: common2D.Rect, other: common2D.Rect): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 需要判断的原矩形。 |
| other | common2D.Rect | 是 | 需要判断的另一矩形。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回两个矩形是否相等的结果。true表示两个矩形相等，false表示两个矩形不相等。 |

## isIntersect

```TypeScript
static isIntersect(rect: common2D.Rect, other: common2D.Rect): boolean
```

判断两个矩形是否相交。

**起始版本：** 20

<!--Device-RectUtils-static isIntersect(rect: common2D.Rect, other: common2D.Rect): boolean--><!--Device-RectUtils-static isIntersect(rect: common2D.Rect, other: common2D.Rect): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 用于计算交集的原矩形。 |
| other | common2D.Rect | 是 | 用于计算交集的另一个矩形。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回两个矩形是否有交集的结果。true表示指定矩形与原矩形相交，false表示指定矩形和原矩形没有交集。两矩形仅边重叠或点相交返回false。 |

## makeCopy

```TypeScript
static makeCopy(src: common2D.Rect): common2D.Rect
```

拷贝一个矩形。

**起始版本：** 20

<!--Device-RectUtils-static makeCopy(src: common2D.Rect): common2D.Rect--><!--Device-RectUtils-static makeCopy(src: common2D.Rect): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | common2D.Rect | 是 | 用于拷贝的矩形。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Created rectangle. |

## makeEmpty

```TypeScript
static makeEmpty(): common2D.Rect
```

创建一个上下左右边界坐标都是0的矩形。

**起始版本：** 20

<!--Device-RectUtils-static makeEmpty(): common2D.Rect--><!--Device-RectUtils-static makeEmpty(): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Created rectangle object. |

## makeLtrb

```TypeScript
static makeLtrb(left: number, top: number, right: number, bottom: number): common2D.Rect
```

创建指定上下左右边界的矩形。

**起始版本：** 20

<!--Device-RectUtils-static makeLtrb(left: number, top: number, right: number, bottom: number): common2D.Rect--><!--Device-RectUtils-static makeLtrb(left: number, top: number, right: number, bottom: number): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| left | number | 是 | 矩形的左上角x轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| top | number | 是 | 矩形的左上角y轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |
| right | number | 是 | 矩形的右下角x轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| bottom | number | 是 | 矩形的右下角y轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Created rectangle. |

## offset

```TypeScript
static offset(rect: common2D.Rect, dx: number, dy: number): void
```

对矩形进行平移。

**起始版本：** 20

<!--Device-RectUtils-static offset(rect: common2D.Rect, dx: double, dy: double): void--><!--Device-RectUtils-static offset(rect: common2D.Rect, dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 发生偏移的矩形区域。 |
| dx | number | 是 | 水平方向平移的距离，该参数为浮点数。0表示不平移，负数表示向左平移，正数表示向右平移。 |
| dy | number | 是 | 竖直方向平移的距离，该参数为浮点数。0表示不平移，负数表示向上平移，正数表示向下平移。 |

## offsetTo

```TypeScript
static offsetTo(rect: common2D.Rect, newLeft: number, newTop: number): void
```

将矩形平移到指定位置。

**起始版本：** 20

<!--Device-RectUtils-static offsetTo(rect: common2D.Rect, newLeft: double, newTop: double): void--><!--Device-RectUtils-static offsetTo(rect: common2D.Rect, newLeft: double, newTop: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 发生偏移的矩形区域。 |
| newLeft | number | 是 | 要平移到的对应位置的x轴坐标，浮点数。0表示坐标原点，负数位于坐标原点左侧，正数位于坐标原点右侧。 |
| newTop | number | 是 | 要平移到的对应位置的y轴坐标，浮点数。0表示坐标原点，负数位于坐标原点上侧，正数位于坐标原点下侧。 |

## setEmpty

```TypeScript
static setEmpty(rect: common2D.Rect): void
```

将矩形的上下左右边界都设为0。

**起始版本：** 20

<!--Device-RectUtils-static setEmpty(rect: common2D.Rect): void--><!--Device-RectUtils-static setEmpty(rect: common2D.Rect): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 用于设置为空的矩形对象。 |

## setLtrb

```TypeScript
static setLtrb(rect: common2D.Rect, left: number, top: number, right: number, bottom: number): void
```

使用传入的"上下左右"的值更新当前矩形的上下左右边界值。

**起始版本：** 20

<!--Device-RectUtils-static setLtrb(rect: common2D.Rect, left: double, top: double, right: double, bottom: double): void--><!--Device-RectUtils-static setLtrb(rect: common2D.Rect, left: double, top: double, right: double, bottom: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形对象。 |
| left | number | 是 | 矩形的左上角x轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| top | number | 是 | 矩形的左上角y轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |
| right | number | 是 | 矩形的右下角x轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点左侧，正数表示位于坐标原点右侧。 |
| bottom | number | 是 | 矩形的右下角y轴坐标，该参数为浮点数。0表示坐标原点，负数表示位于坐标原点上侧，正数表示位于坐标原点下侧。 |

## setRect

```TypeScript
static setRect(rect: common2D.Rect, other: common2D.Rect): void
```

使用另一个矩形对当前矩形进行赋值。

**起始版本：** 20

<!--Device-RectUtils-static setRect(rect: common2D.Rect, other: common2D.Rect): void--><!--Device-RectUtils-static setRect(rect: common2D.Rect, other: common2D.Rect): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 原矩形。 |
| other | common2D.Rect | 是 | 用于赋值的矩形。 |

## sort

```TypeScript
static sort(rect: common2D.Rect): void
```

如果矩形存在反转的情况（即左边界大于右边界或上边界大于下边界），则对矩形的上下（左右）边界值进行交换，使得上边界小于下边界（左边界小于右边界）。如果矩形不存在反转的情况（即左边界小于等于右边界或上边界小于等于下边界)，不做任何操作。

**起始版本：** 20

<!--Device-RectUtils-static sort(rect: common2D.Rect): void--><!--Device-RectUtils-static sort(rect: common2D.Rect): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 用于设置的矩形对象。 |

## union

```TypeScript
static union(rect: common2D.Rect, other: common2D.Rect): void
```

计算矩形的并集区域，并将并集结果更新到第一个入参表示的矩形区域。如果第一个入参矩形为空，则将并集结果更新到第二个入参代表的矩形区域；如果第二个入参的矩形为空，则不进行任何操作。

**起始版本：** 20

<!--Device-RectUtils-static union(rect: common2D.Rect, other: common2D.Rect): void--><!--Device-RectUtils-static union(rect: common2D.Rect, other: common2D.Rect): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 用于计算并集的原矩形。 |
| other | common2D.Rect | 是 | 用于计算并集的另一个矩形。 |

