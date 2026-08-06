# ShapeAttribute

绘制组件的父组件，父组件中会描述所有绘制组件均支持的通用属性。 1、绘制组件使用Shape作为父组件，实现类似SVG的效果。 2、绘制组件单独使用，用于在页面上绘制指定的图形。

**继承/实现关系：** ShapeAttribute extends [CommonMethod](../../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ShapeAttribute extends CommonMethod--><!--Device-unnamed-export declare interface ShapeAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## antiAlias

```TypeScript
default antiAlias(value: boolean | undefined): this
```

设置是否开启抗锯齿效果，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default antiAlias(value: boolean | undefined): this--><!--Device-ShapeAttribute-default antiAlias(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 是否开启抗锯齿效果。true：开启抗锯齿；false：关闭抗锯齿。默认值：true异常值undefined和null按照false处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## attributeModifier

```TypeScript
default attributeModifier(modifier: AttributeModifier<ShapeAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

Call attributeModifier.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default attributeModifier(modifier: AttributeModifier<ShapeAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-ShapeAttribute-default attributeModifier(modifier: AttributeModifier<ShapeAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| AttributeModifier&lt;CommonMethod&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## fill

```TypeScript
default fill(value: ResourceColor | undefined): this
```

设置填充区域的颜色，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法，异常值按照默认值处理。 与通用属性foregroundColor同时设置时，后设置的属性生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default fill(value: ResourceColor | undefined): this--><!--Device-ShapeAttribute-default fill(value: ResourceColor | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 填充区域颜色。默认值：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_.Black异常值undefined、null、NaN和Infinity按照默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## fillOpacity

```TypeScript
default fillOpacity(value: double | string | Resource | undefined): this
```

设置填充区域透明度，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default fillOpacity(value: double | string | Resource | undefined): this--><!--Device-ShapeAttribute-default fillOpacity(value: double | string | Resource | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| string \| Resource \| undefined | 是 | 填充区域透明度。说明：number格式取值范围是[0.0, 1.0]，若给定值小于0.0，则取值为0.0；若给定值大于1.0，则取值为1.0，其余异常值按1.0处理。string格式支持number格式取值的字符串形式，取值范围与number格式相同。Resource格式支持系统资源或者应用资源中的字符串，取值范围和number格式相同。异常值NaN按0.0处理，undefined、null和Infinity按1.0处理。默认值：1.0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## mesh

```TypeScript
default mesh(value: Array<double> | undefined, column: int | undefined, row: int | undefined): this
```

设置网格效果。将图像分割为（row + 1）* (column + 1)的网格， 每个网格交点坐标存储在数组中（每两个元素表示一个交点的x、y坐标）。 通过数组value中的坐标值，重新定位网格顶点位置，实现图像局部扭曲。 支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。 > 说明： > > mesh只对shape传入pixelMap时生效，且效果作用于传入的pixelMap。 > 与\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_的 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ > 效果一致，建议使用drawPixelMapMesh。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default mesh(value: Array<double> | undefined, column: int | undefined, row: int | undefined): this--><!--Device-ShapeAttribute-default mesh(value: Array<double> | undefined, column: int | undefined, row: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;double&gt; \| undefined | 是 | 长度（row + 1）* （column + 1）* 2的数组，记录扭曲后的位图各个顶点位置。设置异常值undefined时value按照空数组处理，设置空数组时column和row按0处理，value按空数组处理。 |
| column | int \| undefined | 是 | mesh矩阵列数。设置异常值undefined时column和row按0处理，value按空数组处理。 |
| row | int \| undefined | 是 | mesh矩阵行数。设置异常值undefined时column和row按0处理，value按空数组处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setShapeOptions

```TypeScript
default setShapeOptions(value?: PixelMap): this
```

Set Shape options.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default setShapeOptions(value?: PixelMap): this--><!--Device-ShapeAttribute-default setShapeOptions(value?: PixelMap): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Shape constructor options |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | Returns the instance of the ShapeAttribute. |

## stroke

```TypeScript
default stroke(value: ResourceColor | undefined): this
```

设置边框颜色，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法，不设置时，默认边框透明度为0，即没有边框。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default stroke(value: ResourceColor | undefined): this--><!--Device-ShapeAttribute-default stroke(value: ResourceColor | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 边框颜色。默认值：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_.Transparent异常值undefined和null按照默认值处理，NaN和Infinity按照\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_.Black处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeDashArray

```TypeScript
default strokeDashArray(value: Array<Length> | undefined): this
```

设置边框间隙，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。取值范围为≥0，异常值按照默认值处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default strokeDashArray(value: Array<Length> | undefined): this--><!--Device-ShapeAttribute-default strokeDashArray(value: Array<Length> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| undefined | 是 | 定义Shape轮廓的虚线模式的数组，数组元素交替表示线段长度和间隙长度。默认值：[]（空数组）默认单位：vp异常值undefined和null按照默认值处理。说明：空数组：实线偶数多元素数组：数组元素按顺序循环，如[a, b, c, d]表示线段长度a->间隙长度b->线段长度c->间隙长度d->线段长度a->...奇数多元素数组：重复一次该数组元素，按偶数多元素数组的规则顺序循环，如[a, b, c]等效于[a, b, c, a, b, c]，表示线段长度a->间隙长度b->线段长度c->间隙长度a->线段长度b->间隙长度c->线段长度a->... |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeDashOffset

```TypeScript
default strokeDashOffset(value: Length | undefined): this
```

设置边框绘制起点的偏移量，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。异常值按照默认值处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default strokeDashOffset(value: Length | undefined): this--><!--Device-ShapeAttribute-default strokeDashOffset(value: Length | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 边框绘制起点的偏移量。默认值：0默认单位：vp异常值undefined和null按照默认值处理，NaN和Infinity会导致strokeDashArray失效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeLineCap

```TypeScript
default strokeLineCap(value: LineCapStyle | undefined): this
```

设置边框端点绘制样式，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default strokeLineCap(value: LineCapStyle | undefined): this--><!--Device-ShapeAttribute-default strokeLineCap(value: LineCapStyle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 边框端点绘制样式。默认值：LineCapStyle.Butt异常值undefined、null、NaN和Infinity按照默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeLineJoin

```TypeScript
default strokeLineJoin(value: LineJoinStyle | undefined): this
```

设置边框拐角绘制样式，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default strokeLineJoin(value: LineJoinStyle | undefined): this--><!--Device-ShapeAttribute-default strokeLineJoin(value: LineJoinStyle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 边框拐角绘制样式。默认值：LineJoinStyle.Miter异常值undefined、null、NaN和Infinity按照默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeMiterLimit

```TypeScript
default strokeMiterLimit(value: Length | undefined): this
```

设置斜接长度与边框宽度比值的极限值，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。 斜接长度表示外边框外边交点到内边交点的距离，边框宽度即strokeWidth属性的值。 该属性取值需在strokeLineJoin属性取值LineJoinStyle.Miter时生效。 该属性的合法值范围应当大于等于1.0，当取值范围在[0,1)时按1.0处理，其余异常值按默认值处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default strokeMiterLimit(value: Length | undefined): this--><!--Device-ShapeAttribute-default strokeMiterLimit(value: Length | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 斜接长度与边框宽度比值的极限值。默认值：4异常值undefined、null和NaN按照默认值处理，Infinity会导致stroke失效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeOpacity

```TypeScript
default strokeOpacity(value: double | string | Resource | undefined): this
```

设置边框透明度，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。 该属性的取值范围是[0.0, 1.0]，若给定值小于0.0，则取值为0.0；若给定值大于1.0，则取值为1.0。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default strokeOpacity(value: double | string | Resource | undefined): this--><!--Device-ShapeAttribute-default strokeOpacity(value: double | string | Resource | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| string \| Resource \| undefined | 是 | 边框透明度。默认值：stroke接口设置的透明度。异常值NaN按0.0处理，undefined、null和Infinity按1.0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## strokeWidth

```TypeScript
default strokeWidth(value: Length | undefined): this
```

设置边框宽度，支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 动态设置属性方法。该属性若为string类型，暂不支持百分比，百分比按照1px处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default strokeWidth(value: Length | undefined): this--><!--Device-ShapeAttribute-default strokeWidth(value: Length | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 边框宽度，取值范围≥0。默认值：1默认单位：vp异常值undefined、null和NaN按照默认值处理，Infinity按0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## viewPort

```TypeScript
default viewPort(value: ViewportRect | undefined): this
```

设置形状的视口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeAttribute-default viewPort(value: ViewportRect | undefined): this--><!--Device-ShapeAttribute-default viewPort(value: ViewportRect | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Viewport绘制属性。默认值：{}异常值undefined和null按照默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

