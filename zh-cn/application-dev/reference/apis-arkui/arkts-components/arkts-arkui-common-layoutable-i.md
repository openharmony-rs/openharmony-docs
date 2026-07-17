# Layoutable

子组件布局信息。

**起始版本：** 10

<!--Device-unnamed-declare interface Layoutable--><!--Device-unnamed-declare interface Layoutable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getBorderWidth

```TypeScript
getBorderWidth() : DirectionalEdgesT<number>
```

调用此方法获取子组件的borderWidth信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Layoutable-getBorderWidth() : DirectionalEdgesT<number>--><!--Device-Layoutable-getBorderWidth() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-units-directionaledgest-i.md)<number> | 子组件的borderWidth信息。 |

## getMargin

```TypeScript
getMargin() : DirectionalEdgesT<number>
```

调用此方法获取子组件的margin信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Layoutable-getMargin() : DirectionalEdgesT<number>--><!--Device-Layoutable-getMargin() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-units-directionaledgest-i.md)<number> | 子组件的margin信息。 |

## getPadding

```TypeScript
getPadding() : DirectionalEdgesT<number>
```

调用此方法获取子组件的padding信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Layoutable-getPadding() : DirectionalEdgesT<number>--><!--Device-Layoutable-getPadding() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-units-directionaledgest-i.md)<number> | 子组件的padding信息。 |

## layout

```TypeScript
layout(position: Position): void
```

调用此方法对子组件的位置信息进行限制。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Layoutable-layout(position: Position): void--><!--Device-Layoutable-layout(position: Position): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](../arkts-apis/arkts-arkui-display-position-i.md) | 是 | 绝对位置。 |

## measureResult

```TypeScript
measureResult: MeasureResult
```

子组件测量后的尺寸信息。单位为： vp。

**类型：** MeasureResult

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Layoutable-measureResult: MeasureResult--><!--Device-Layoutable-measureResult: MeasureResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId?: number
```

系统为子组件分配的唯一标识UniqueID。取值应为≥0的整数。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Layoutable-uniqueId?: number--><!--Device-Layoutable-uniqueId?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

