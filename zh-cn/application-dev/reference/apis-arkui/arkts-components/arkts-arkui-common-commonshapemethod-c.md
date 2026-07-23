# CommonShapeMethod

CommonShapeMethod

**继承/实现关系：** CommonShapeMethod extends [CommonMethod<T>]

**起始版本：** 11

<!--Device-unnamed-declare class CommonShapeMethod<T> extends CommonMethod<T>--><!--Device-unnamed-declare class CommonShapeMethod<T> extends CommonMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## antiAlias

```TypeScript
antiAlias(value: boolean): T
```

Indicates whether to enable anti-aliasing

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-antiAlias(value: boolean): T--><!--Device-CommonShapeMethod-antiAlias(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## fill

```TypeScript
fill(value: ResourceColor): T
```

Fill color.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-fill(value: ResourceColor): T--><!--Device-CommonShapeMethod-fill(value: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## fillOpacity

```TypeScript
fillOpacity(value: number | string | Resource): T
```

fill Opacity

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-fillOpacity(value: number | string | Resource): T--><!--Device-CommonShapeMethod-fillOpacity(value: number | string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## stroke

```TypeScript
stroke(value: ResourceColor): T
```

border Color

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-stroke(value: ResourceColor): T--><!--Device-CommonShapeMethod-stroke(value: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## strokeDashArray

```TypeScript
strokeDashArray(value: Array<any>): T
```

Sets the gap for the border.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeDashArray(value: Array<any>): T--><!--Device-CommonShapeMethod-strokeDashArray(value: Array<any>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<any> | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## strokeDashOffset

```TypeScript
strokeDashOffset(value: number | string): T
```

Offset from the start point of the border drawing.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeDashOffset(value: number | string): T--><!--Device-CommonShapeMethod-strokeDashOffset(value: number | string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## strokeLineCap

```TypeScript
strokeLineCap(value: LineCapStyle): T
```

Path endpoint drawing style.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeLineCap(value: LineCapStyle): T--><!--Device-CommonShapeMethod-strokeLineCap(value: LineCapStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineCapStyle](../arkts-apis/arkts-arkui-enums-linecapstyle-e.md) | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## strokeLineJoin

```TypeScript
strokeLineJoin(value: LineJoinStyle): T
```

Border corner drawing style.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeLineJoin(value: LineJoinStyle): T--><!--Device-CommonShapeMethod-strokeLineJoin(value: LineJoinStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineJoinStyle](../arkts-apis/arkts-arkui-enums-linejoinstyle-e.md) | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## strokeMiterLimit

```TypeScript
strokeMiterLimit(value: number | string): T
```

Limits for drawing acute angles as bevels

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeMiterLimit(value: number | string): T--><!--Device-CommonShapeMethod-strokeMiterLimit(value: number | string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## strokeOpacity

```TypeScript
strokeOpacity(value: number | string | Resource): T
```

Sets the opacity of the border.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeOpacity(value: number | string | Resource): T--><!--Device-CommonShapeMethod-strokeOpacity(value: number | string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

## strokeWidth

```TypeScript
strokeWidth(value: Length): T
```

Sets the width of the dividing line.

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-strokeWidth(value: Length): T--><!--Device-CommonShapeMethod-strokeWidth(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | @returns { T } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@form@atomicservice |

