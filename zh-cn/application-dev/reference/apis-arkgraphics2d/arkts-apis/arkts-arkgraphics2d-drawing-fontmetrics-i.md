# FontMetrics

描述字形大小和布局的属性信息，同一种字体中的字符属性大致相同。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-drawing-interface FontMetrics--><!--Device-drawing-interface FontMetrics-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## ascent

```TypeScript
ascent: double
```

文字最高处到基线之间的距离，浮点数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-ascent: double--><!--Device-FontMetrics-ascent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## avgCharWidth

```TypeScript
avgCharWidth?: double
```

平均字符宽度，浮点数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-avgCharWidth?: double--><!--Device-FontMetrics-avgCharWidth?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## bottom

```TypeScript
bottom: double
```

字体中任意字形边界框超出基线下方的最大距离，浮点数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-bottom: double--><!--Device-FontMetrics-bottom: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## capHeight

```TypeScript
capHeight?: double
```

大写字母顶部相对于基线的垂直偏移量，浮点数，通常为负值。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-capHeight?: double--><!--Device-FontMetrics-capHeight?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## descent

```TypeScript
descent: double
```

基线到文字最低处之间的距离，浮点数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-descent: double--><!--Device-FontMetrics-descent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## flags

```TypeScript
flags?: int
```

Font measurement flags that are valid.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-FontMetrics-flags?: int--><!--Device-FontMetrics-flags?: int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## leading

```TypeScript
leading: double
```

行间距，从上一行文字descent到下一行文字ascent之间的距离，浮点数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-leading: double--><!--Device-FontMetrics-leading: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## maxCharWidth

```TypeScript
maxCharWidth?: double
```

最大字符宽度，浮点数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-maxCharWidth?: double--><!--Device-FontMetrics-maxCharWidth?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## strikethroughPosition

```TypeScript
strikethroughPosition?: double
```

文本基线到删除线的垂直距离，浮点数，通常为负值。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-strikethroughPosition?: double--><!--Device-FontMetrics-strikethroughPosition?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## strikethroughThickness

```TypeScript
strikethroughThickness?: double
```

文本删除线的厚度，即贯穿文本字符的水平线的宽度，浮点数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-strikethroughThickness?: double--><!--Device-FontMetrics-strikethroughThickness?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## top

```TypeScript
top: double
```

字体中任意字形边界框超出基线上方的最大距离，浮点数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-top: double--><!--Device-FontMetrics-top: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## underlinePosition

```TypeScript
underlinePosition?: double
```

文本基线到下划线顶部的垂直距离，浮点数，通常是正数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-underlinePosition?: double--><!--Device-FontMetrics-underlinePosition?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## underlineThickness

```TypeScript
underlineThickness?: double
```

下划线的厚度，浮点数。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-underlineThickness?: double--><!--Device-FontMetrics-underlineThickness?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## xHeight

```TypeScript
xHeight?: double
```

小写字母x顶部相对于基线的垂直偏移量，浮点数，通常为负值。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-xHeight?: double--><!--Device-FontMetrics-xHeight?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## xMax

```TypeScript
xMax?: double
```

字体中任意字形边界框最右边沿到原点的水平距离，浮点数，此值多为正数，指示了字形在水平方向上的最大延伸范围。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-xMax?: double--><!--Device-FontMetrics-xMax?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## xMin

```TypeScript
xMin?: double
```

字体中任意字形边界框最左边沿到原点的水平距离，这个值往往小于零，意味着字形在水平方向上的最小边界。单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-FontMetrics-xMin?: double--><!--Device-FontMetrics-xMin?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

