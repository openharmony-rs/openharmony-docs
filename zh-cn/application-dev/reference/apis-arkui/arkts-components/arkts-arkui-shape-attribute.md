# Shape属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** ShapeAttribute extends [CommonMethod<ShapeAttribute>]
**起始版本：** 7

<!--Device-unnamed-declare class ShapeAttribute extends CommonMethod<ShapeAttribute>--><!--Device-unnamed-declare class ShapeAttribute extends CommonMethod<ShapeAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## antiAlias

```TypeScript
antiAlias(value: boolean)
```

设置是否开启抗锯齿效果，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-antiAlias(value: boolean): ShapeAttribute--><!--Device-ShapeAttribute-antiAlias(value: boolean): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启抗锯齿效果。<br/>true：开启抗锯齿；false：关闭抗锯齿。<br/>默认值：true <br/>异常值undefined和null按照false处理。 |

## fill

```TypeScript
fill(value: ResourceColor)
```

设置填充区域的颜色，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法，异常值按照默认值处理。与通用属性foregroundColor同时设置时，后设置的属性生效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-fill(value: ResourceColor): ShapeAttribute--><!--Device-ShapeAttribute-fill(value: ResourceColor): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 填充区域颜色。<br/>默认值：[Color](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md).Black <br/>异常值undefined、null、NaN和Infinity按照默认值处理。 |

## fillOpacity

```TypeScript
fillOpacity(value: number | string | Resource)
```

设置填充区域透明度，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-fillOpacity(value: number | string | Resource): ShapeAttribute--><!--Device-ShapeAttribute-fillOpacity(value: number | string | Resource): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 填充区域透明度。<br/>**说明：**<br/>number格式取值范围是[0.0, 1.0]，若给定值小于0.0，则取值为0.0；若给定值大于1.0，则取值为1.0，其余异常值按1.0处理。<br/>string格式支持number格式取值的字符串形式，取值范围与number格式相同。<br/>Resource格式支持系统资源或者应用资源中的字符串，取值范围和number格式相同。<br/>默认值：1.0 |

## mesh

```TypeScript
mesh(value: Array<any>, column: number, row: number)
```

设置网格效果。将图像分割为（row + 1）* (column + 1)的网格，每个网格交点坐标存储在数组中（每两个元素表示一个交点的x、y坐标）。通过数组value中的坐标值，重新定位网格顶点位置，实现图像局部扭曲。支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。
> **说明：**  
>  
> mesh只对shape传入pixelMap时生效，且效果作用于传入的pixelMap。与[绘制模块](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-drawing.md)的  
> [drawPixelMapMesh<sup>12+</sup>](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-canvas-c.md#drawpixelmapmesh)效果一致，建议使用  
> drawPixelMapMesh。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-mesh(value: Array<any>, column: number, row: number): ShapeAttribute--><!--Device-ShapeAttribute-mesh(value: Array<any>, column: number, row: number): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | 是 | 长度（row + 1）* （column + 1）* 2的数组，记录扭曲后的位图各个顶点位置。<br/>设置异常值undefined、null时value按照空数组处理，设置空数组时column和row按0处理，value按空数组处理。 |
| column | number | 是 | mesh矩阵列数。<br/>设置异常值undefined、null、NaN和Infinity时column和row按0处理，value按空数组处理。 |
| row | number | 是 | mesh矩阵行数。<br/>设置异常值undefined、null、NaN和Infinity时column和row按0处理，value按空数组处理。 |

## stroke

```TypeScript
stroke(value: ResourceColor)
```

设置边框颜色，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法，不设置时，默认边框透明度为0，即没有边框。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-stroke(value: ResourceColor): ShapeAttribute--><!--Device-ShapeAttribute-stroke(value: ResourceColor): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 边框颜色。<br/>默认值：[Color](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md).Transparent<br/>异常值undefined和null按照默认值处理，NaN和Infinity按照[Color](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md).Black处理。 |

## strokeDashArray

```TypeScript
strokeDashArray(value: Array<any>)
```

设置边框间隙，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。取值范围为≥0，异常值按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-strokeDashArray(value: Array<any>): ShapeAttribute--><!--Device-ShapeAttribute-strokeDashArray(value: Array<any>): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | 是 | 定义Shape轮廓的虚线模式的数组，数组元素交替表示线段长度和间隙长度。<br/>默认值：[]（空数组）<br/>默认单位：vp <br/>异常值undefined和null按照默认值处理。<br/>**说明：**<br/>空数组：实线<br/>偶数多元素数组：数组元素按顺序循环，如[a, b, c, d]表示线段长度a->间隙长度b->线段长度c->间隙长度d->线段长度a->...<br/>奇数多元素数组：重复一次该数组元素，按偶数多元素数组的规则顺序循环，如[a, b, c]等效于[a, b, c, a, b, c]，表示线段长度a->间隙长度b->线段长度c->间隙长度a->线段长度b->间隙长度c->线段长度a->... |

## strokeDashOffset

```TypeScript
strokeDashOffset(value: Length)
```

设置边框绘制起点的偏移量，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。异常值按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-strokeDashOffset(value: Length): ShapeAttribute--><!--Device-ShapeAttribute-strokeDashOffset(value: Length): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 边框绘制起点的偏移量。<br/>默认值：0<br/>默认单位：vp <br/>异常值undefined和null按照默认值处理，NaN和Infinity会导致strokeDashArray失效。<br>**起始版本：** 11 |

## strokeLineCap

```TypeScript
strokeLineCap(value: LineCapStyle)
```

设置边框端点绘制样式，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-strokeLineCap(value: LineCapStyle): ShapeAttribute--><!--Device-ShapeAttribute-strokeLineCap(value: LineCapStyle): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineCapStyle](../arkts-apis/arkts-arkui-linecapstyle-e.md) | 是 | 边框端点绘制样式。<br/>默认值：LineCapStyle.Butt <br/>异常值undefined、null、NaN和Infinity按照默认值处理。 |

## strokeLineJoin

```TypeScript
strokeLineJoin(value: LineJoinStyle)
```

设置边框拐角绘制样式，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-strokeLineJoin(value: LineJoinStyle): ShapeAttribute--><!--Device-ShapeAttribute-strokeLineJoin(value: LineJoinStyle): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineJoinStyle](../arkts-apis/arkts-arkui-linejoinstyle-e.md) | 是 | 边框拐角绘制样式。<br/>默认值：LineJoinStyle.Miter <br/>异常值undefined、null、NaN和Infinity按照默认值处理。 |

## strokeMiterLimit

```TypeScript
strokeMiterLimit(value: Length)
```

设置斜接长度与边框宽度比值的极限值，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。斜接长度表示外边框外边交点到内边交点的距离，边框宽度即strokeWidth属性的值。该属性取值需在strokeLineJoin属性取值LineJoinStyle.Miter时生效。

该属性的合法值范围应当大于等于1.0，当取值范围在[0,1)时按1.0处理，其余异常值按默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-strokeMiterLimit(value: Length): ShapeAttribute--><!--Device-ShapeAttribute-strokeMiterLimit(value: Length): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 斜接长度与边框宽度比值的极限值。<br/>默认值：4 <br/>异常值undefined、null和NaN按照默认值处理，Infinity会导致stroke失效。<br>**起始版本：** 20 |

## strokeOpacity

```TypeScript
strokeOpacity(value: number | string | Resource)
```

设置边框透明度，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。该属性的取值范围是[0.0, 1.0]，若给定值小于0.0，则取值为0.0；若给定值大于1.0，则取值为1.0。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-strokeOpacity(value: number | string | Resource): ShapeAttribute--><!--Device-ShapeAttribute-strokeOpacity(value: number | string | Resource): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 边框透明度。<br/>默认值：[stroke](ShapeAttribute#stroke)接口设置的透明度。<br/>异常值NaN按0.0处理，undefined、null和Infinity按1.0处理。 |

## strokeWidth

```TypeScript
strokeWidth(value: Length)
```

设置边框宽度，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)动态设置属性方法。该属性若为string类型，暂不支持百分比，百分比按照1px处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-strokeWidth(value: Length): ShapeAttribute--><!--Device-ShapeAttribute-strokeWidth(value: Length): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 边框宽度，取值范围≥0。<br/>默认值：1 <br/>默认单位：vp<br/>异常值undefined、null和NaN按照默认值处理，Infinity按0处理。<br>**起始版本：** 20 |

## viewPort

```TypeScript
viewPort(value: ViewportRect)
```

设置形状的视口。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ShapeAttribute-viewPort(value: ViewportRect): ShapeAttribute--><!--Device-ShapeAttribute-viewPort(value: ViewportRect): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ViewportRect](arkts-arkui-viewportrect-i.md) | 是 | Viewport绘制属性。<br/>默认值：{}<br/>异常值undefined和null按照默认值处理。<br>**起始版本：** 18 |

