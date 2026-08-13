# ShapeAttribute

绘制组件的父组件，父组件中会描述所有绘制组件均支持的通用属性。 1、绘制组件使用Shape作为父组件，实现类似SVG的效果。 2、绘制组件单独使用，用于在页面上绘制指定的图形。

**继承/实现关系：** ShapeAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ShapeAttribute--><!--Device-unnamed-export declare interface ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## antiAlias

```TypeScript
antiAlias(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-antiAlias(value: boolean | undefined): this--><!--Device-ShapeAttribute-antiAlias(value: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<ShapeAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-attributeModifier(modifier: AttributeModifier<ShapeAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-ShapeAttribute-attributeModifier(modifier: AttributeModifier<ShapeAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[ShapeAttribute](arkts-arkui-shape-shapeattribute-i.md)&gt; \| [AttributeModifier](../arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## fill

```TypeScript
fill(value: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-fill(value: ResourceColor | undefined): this--><!--Device-ShapeAttribute-fill(value: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## fillOpacity

```TypeScript
fillOpacity(value: double | string | Resource | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-fillOpacity(value: double | string | Resource | undefined): this--><!--Device-ShapeAttribute-fillOpacity(value: double | string | Resource | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## mesh

```TypeScript
mesh(value: Array<double> | undefined, column: int | undefined, row: int | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-mesh(value: Array<double> | undefined, column: int | undefined, row: int | undefined): this--><!--Device-ShapeAttribute-mesh(value: Array<double> | undefined, column: int | undefined, row: int | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;double&gt; \| undefined | 是 |  |
| column | int \| undefined | 是 |  |
| row | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setShapeOptions

```TypeScript
setShapeOptions(value?: PixelMap): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-setShapeOptions(value?: PixelMap): this--><!--Device-ShapeAttribute-setShapeOptions(value?: PixelMap): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PixelMap](../arkts-components/arkts-arkui-pixelmap-t.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## stroke

```TypeScript
stroke(value: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-stroke(value: ResourceColor | undefined): this--><!--Device-ShapeAttribute-stroke(value: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeDashArray

```TypeScript
strokeDashArray(value: Array<Length> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-strokeDashArray(value: Array<Length> | undefined): this--><!--Device-ShapeAttribute-strokeDashArray(value: Array<Length> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[Length](arkts-arkui-length-t.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeDashOffset

```TypeScript
strokeDashOffset(value: Length | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-strokeDashOffset(value: Length | undefined): this--><!--Device-ShapeAttribute-strokeDashOffset(value: Length | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeLineCap

```TypeScript
strokeLineCap(value: LineCapStyle | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-strokeLineCap(value: LineCapStyle | undefined): this--><!--Device-ShapeAttribute-strokeLineCap(value: LineCapStyle | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineCapStyle](arkts-arkui-linecapstyle-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeLineJoin

```TypeScript
strokeLineJoin(value: LineJoinStyle | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-strokeLineJoin(value: LineJoinStyle | undefined): this--><!--Device-ShapeAttribute-strokeLineJoin(value: LineJoinStyle | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineJoinStyle](arkts-arkui-linejoinstyle-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeMiterLimit

```TypeScript
strokeMiterLimit(value: Length | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-strokeMiterLimit(value: Length | undefined): this--><!--Device-ShapeAttribute-strokeMiterLimit(value: Length | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeOpacity

```TypeScript
strokeOpacity(value: double | string | Resource | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-strokeOpacity(value: double | string | Resource | undefined): this--><!--Device-ShapeAttribute-strokeOpacity(value: double | string | Resource | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeWidth

```TypeScript
strokeWidth(value: Length | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-strokeWidth(value: Length | undefined): this--><!--Device-ShapeAttribute-strokeWidth(value: Length | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## viewPort

```TypeScript
viewPort(value: ViewportRect | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-ShapeAttribute-viewPort(value: ViewportRect | undefined): this--><!--Device-ShapeAttribute-viewPort(value: ViewportRect | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ViewportRect](arkts-arkui-shape-viewportrect-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

Call attributeModifier.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default--><!--Device-ShapeAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

