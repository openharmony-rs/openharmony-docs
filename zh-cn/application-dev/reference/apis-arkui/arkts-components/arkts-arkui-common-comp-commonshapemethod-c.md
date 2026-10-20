# CommonShapeMethod

```TypeScript
declare class CommonShapeMethod<T> extends CommonMethod<T>
```

CommonShapeMethod

**继承/实现关系：** CommonShapeMethod extends CommonMethod&lt;T&gt;

**起始版本：** 11

<!--Device-unnamed-declare class CommonShapeMethod<T> extends CommonMethod<T>--><!--Device-unnamed-declare class CommonShapeMethod<T> extends CommonMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## antiAlias

```TypeScript
antiAlias(value: boolean): T
```

设置是否开启抗锯齿效果，支持attributeModifier动态设置属性方法。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-antiAlias(value: boolean): T--><!--Device-CommonShapeMethod-antiAlias(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启抗锯齿效果。<br>true：开启抗锯齿；false：关闭抗锯齿。<br>默认值：true <br>异常值undefined和null按照false处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## fill

```TypeScript
fill(value: ResourceColor): T
```

设置填充区域的颜色，支持attributeModifier动态设置属性方法，异常值按照默认值处理。与通用属性foregroundColor同时设置时，后设置的属性生效。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-fill(value: ResourceColor): T--><!--Device-CommonShapeMethod-fill(value: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 填充区域颜色。<br>默认值：Color.Black <br>异常值undefined、null、NaN和Infinity按照默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## fillOpacity

```TypeScript
fillOpacity(value: number | string | Resource): T
```

设置填充区域透明度，支持attributeModifier动态设置属性方法。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-fillOpacity(value: number | string | Resource): T--><!--Device-CommonShapeMethod-fillOpacity(value: number | string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | 是 | 填充区域透明度。<br>默认值：1.0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## stroke

```TypeScript
stroke(value: ResourceColor): T
```

设置边框颜色，支持attributeModifier动态设置属性方法，不设置时，默认边框透明度为0，即无边框。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-stroke(value: ResourceColor): T--><!--Device-CommonShapeMethod-stroke(value: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 边框颜色。<br>默认值：Color.Transparent<br>异常值undefined和null按照默认值处理，NaN和Infinity按照Color.Black处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## strokeDashArray

```TypeScript
strokeDashArray(value: Array<any>): T
```

设置边框的虚线长度和虚线间隙长度，支持attributeModifier动态设置属性方法。取值范围≥0。异常值将按默认值处理。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeDashArray(value: Array<any>): T--><!--Device-CommonShapeMethod-strokeDashArray(value: Array<any>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;any&gt; | 是 | 定义Rect边框的虚线模式的数组，数组元素交替表示线段长度和间隙长度。<br>默认值：[]（空数组）<br>默认单位：vp <br>异常值undefined和null按照默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## strokeDashOffset

```TypeScript
strokeDashOffset(value: number | string): T
```

设置边框绘制起点的偏移量，支持attributeModifier动态设置属性方法。异常值按照默认值处理。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeDashOffset(value: number | string): T--><!--Device-CommonShapeMethod-strokeDashOffset(value: number | string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number &#124; string | 是 | 边框绘制起点的偏移量。<br>默认值：0<br>默认单位：vp <br>异常值undefined和null按照默认值处理，NaN和Infinity会导致strokeDashArray失效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## strokeLineCap

```TypeScript
strokeLineCap(value: LineCapStyle): T
```

设置边框端点绘制样式，支持attributeModifier动态设置属性方法。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeLineCap(value: LineCapStyle): T--><!--Device-CommonShapeMethod-strokeLineCap(value: LineCapStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineCapStyle](../arkts-apis/arkts-arkui-linecapstyle-e.md) | 是 | 边框端点绘制样式。<br>默认值：LineCapStyle.Butt <br>异常值undefined、null、NaN和Infinity按照默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## strokeLineJoin

```TypeScript
strokeLineJoin(value: LineJoinStyle): T
```

设置边框拐角绘制样式，支持attributeModifier动态设置属性方法。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeLineJoin(value: LineJoinStyle): T--><!--Device-CommonShapeMethod-strokeLineJoin(value: LineJoinStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineJoinStyle](../arkts-apis/arkts-arkui-linejoinstyle-e.md) | 是 | 边框拐角绘制样式。<br>默认值：LineJoinStyle.Miter <br>异常值undefined、null、NaN和Infinity按照默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## strokeMiterLimit

```TypeScript
strokeMiterLimit(value: number | string): T
```

设置斜接长度与边框宽度比值的极限值，支持attributeModifier动态设置属性方法。斜接长度表示外边框外边交点到内边交点的距离，边框宽度即strokeWidth属性的值。该属性取值需在strokeLineJoin属性取值LineJoinStyle.Miter时生效。该属性的合法值范围应当大于等于1.0，当取值范围在[0,1)时按1.0处理，其余异常值按默认值处理。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeMiterLimit(value: number | string): T--><!--Device-CommonShapeMethod-strokeMiterLimit(value: number | string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number &#124; string | 是 | 斜接长度与边框宽度比值的极限值。<br>默认值：4 <br>异常值undefined、null和NaN按照默认值处理，Infinity会导致stroke失效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## strokeOpacity

```TypeScript
strokeOpacity(value: number | string | Resource): T
```

设置边框透明度，支持attributeModifier动态设置属性方法。该属性的取值范围是[0.0, 1.0]，若给定值小于0.0，则取值为0.0；若给定值大于1.0，则取值为1.0。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeOpacity(value: number | string | Resource): T--><!--Device-CommonShapeMethod-strokeOpacity(value: number | string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | 是 | 边框透明度。<br>默认值：stroke接口设置的透明度<br>异常值NaN按0.0处理，undefined、null和Infinity按1.0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## strokeWidth

```TypeScript
strokeWidth(value: Length): T
```

设置边框宽度，支持attributeModifier动态设置属性方法。该属性若为string类型，暂不支持百分比，百分比按照1px处理。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeWidth(value: Length): T--><!--Device-CommonShapeMethod-strokeWidth(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 边框宽度，取值范围≥0。<br>默认值：1 <br>默认单位：vp<br>异常值undefined、null和NaN按照默认值处理，Infinity按0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |
