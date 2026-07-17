# FontMetrics

描述字形大小和布局的属性信息，同一种字体中的字符属性大致相同。

**起始版本：** 11

<!--Device-drawing-interface FontMetrics--><!--Device-drawing-interface FontMetrics-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## ascent

```TypeScript
ascent: number
```

文字最高处到基线之间的距离，浮点数。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-ascent: double--><!--Device-FontMetrics-ascent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## avgCharWidth

```TypeScript
avgCharWidth?: number
```

平均字符宽度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-avgCharWidth?: double--><!--Device-FontMetrics-avgCharWidth?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## bottom

```TypeScript
bottom: number
```

基线到文字最低处之间的最大距离，浮点数。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-bottom: double--><!--Device-FontMetrics-bottom: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## capHeight

```TypeScript
capHeight?: number
```

大写字母的高度，通常为负值。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-capHeight?: double--><!--Device-FontMetrics-capHeight?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## descent

```TypeScript
descent: number
```

基线到文字最低处之间的距离，浮点数。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-descent: double--><!--Device-FontMetrics-descent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## flags

```TypeScript
flags?: FontMetricsFlags
```

表明哪些字体度量标志有效。

**类型：** FontMetricsFlags

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-flags?: FontMetricsFlags--><!--Device-FontMetrics-flags?: FontMetricsFlags-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## leading

```TypeScript
leading: number
```

行间距，从上一行文字descent到下一行文字ascent之间的距离，浮点数。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-leading: double--><!--Device-FontMetrics-leading: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## maxCharWidth

```TypeScript
maxCharWidth?: number
```

最大字符宽度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-maxCharWidth?: double--><!--Device-FontMetrics-maxCharWidth?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## strikethroughPosition

```TypeScript
strikethroughPosition?: number
```

文本基线到底部删除线的垂直距离，通常为负值。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-strikethroughPosition?: double--><!--Device-FontMetrics-strikethroughPosition?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## strikethroughThickness

```TypeScript
strikethroughThickness?: number
```

文本删除线的厚度，即贯穿文本字符的水平线的宽度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-strikethroughThickness?: double--><!--Device-FontMetrics-strikethroughThickness?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## top

```TypeScript
top: number
```

文字最高处到基线之间的最大距离，浮点数。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-top: double--><!--Device-FontMetrics-top: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## underlinePosition

```TypeScript
underlinePosition?: number
```

文本基线到下划线顶部的垂直距离，通常是正数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-underlinePosition?: double--><!--Device-FontMetrics-underlinePosition?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## underlineThickness

```TypeScript
underlineThickness?: number
```

下划线的厚度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-underlineThickness?: double--><!--Device-FontMetrics-underlineThickness?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## xHeight

```TypeScript
xHeight?: number
```

小写字母x的高度，通常为负值。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-xHeight?: double--><!--Device-FontMetrics-xHeight?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## xMax

```TypeScript
xMax?: number
```

字体中任意字形边界框最右边沿到原点的水平距离，此值多为正数，指示了字形在水平方向上的最大延伸范围。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-xMax?: double--><!--Device-FontMetrics-xMax?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## xMin

```TypeScript
xMin?: number
```

字体中任意字形边界框最左边沿到原点的水平距离，这个值往往小于零，意味着字形在水平方向上的最小边界。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-xMin?: double--><!--Device-FontMetrics-xMin?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

