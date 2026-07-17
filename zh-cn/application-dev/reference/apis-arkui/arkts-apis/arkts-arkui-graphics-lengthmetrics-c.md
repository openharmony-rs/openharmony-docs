# LengthMetrics

用于设置长度属性，当长度单位为PERCENT时，值为1表示100%。

**起始版本：** 12

<!--Device-unnamed-declare class LengthMetrics--><!--Device-unnamed-declare class LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoRefresh

```TypeScript
autoRefresh?(value: boolean): LengthMetrics
```

为LengthMetrics对象设置自动刷新。启用时，由LengthMetrics.resource()创建的对象的长度值将自动更新当系统配置发生变化时。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-autoRefresh?(value: boolean): LengthMetrics--><!--Device-LengthMetrics-autoRefresh?(value: boolean): LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当系统配置发生变化时，是否自动更新长度值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | 返回用于链接的LengthMetrics对象。 |

## constructor

```TypeScript
constructor(value: number, unit?:LengthUnit)
```

LengthMetrics的构造函数。若参数unit不传入值或传入undefined，返回值使用默认单位VP；若unit传入非LengthUnit类型的值，返回默认值0VP。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-constructor(value: number, unit?:LengthUnit)--><!--Device-LengthMetrics-constructor(value: number, unit?:LengthUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。<br/>取值范围：[0, +∞) |
| unit | [LengthUnit](arkts-arkui-graphics-lengthunit-e.md) | 否 | 长度属性的单位。 |

## fp

```TypeScript
static fp(value: number): LengthMetrics
```

用于生成单位为FP的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-static fp(value: number): LengthMetrics--><!--Device-LengthMetrics-static fp(value: number): LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | LengthMetrics 类的实例。 |

## lpx

```TypeScript
static lpx(value: number): LengthMetrics
```

用于生成单位为LPX的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-static lpx(value: number): LengthMetrics--><!--Device-LengthMetrics-static lpx(value: number): LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | LengthMetrics 类的实例。 |

## percent

```TypeScript
static percent(value: number): LengthMetrics
```

用于生成单位为PERCENT的长度属性，值为1表示100%。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-static percent(value: number): LengthMetrics--><!--Device-LengthMetrics-static percent(value: number): LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。<br/>取值范围：[0, 1] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | LengthMetrics 类的实例。 |

## px

```TypeScript
static px(value: number): LengthMetrics
```

用于生成单位为PX的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-static px(value: number): LengthMetrics--><!--Device-LengthMetrics-static px(value: number): LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | LengthMetrics 类的实例。 |

## resource

```TypeScript
static resource(value: Resource): LengthMetrics
```

用于生成Resource类型资源的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-static resource(value: Resource): LengthMetrics--><!--Device-LengthMetrics-static resource(value: Resource): LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Resource](arkts-arkui-resource-t.md) | 是 | 长度属性的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | LengthMetrics 类的实例。 |

## vp

```TypeScript
static vp(value: number): LengthMetrics
```

用于生成单位为VP的长度属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-static vp(value: number): LengthMetrics--><!--Device-LengthMetrics-static vp(value: number): LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 长度属性的值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | LengthMetrics 类的实例。 |

## unit

```TypeScript
public unit: LengthUnit
```

长度属性的单位，默认为VP。

**类型：** LengthUnit

**默认值：** VP

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-public unit: LengthUnit--><!--Device-LengthMetrics-public unit: LengthUnit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
public value: number
```

长度属性的值。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LengthMetrics-public value: number--><!--Device-LengthMetrics-public value: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

