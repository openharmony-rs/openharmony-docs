# Layoutable

```TypeScript
declare interface Layoutable
```

子组件布局信息。Layoutable对象由ArkUI框架在onPlaceChildren调用时创建并传入，包含子组件的测量结果和唯一标识。开发者通过Layoutable的layout方法设置子组件位置，通过getMargin、getPadding、getBorderWidth方法获取子组件的边距信息用于精确布局计算。

**起始版本：** 10

<!--Device-unnamed-declare interface Layoutable--><!--Device-unnamed-declare interface Layoutable-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getBorderWidth

```TypeScript
getBorderWidth() : DirectionalEdgesT<number>
```

调用此方法获取子组件的borderWidth信息，返回其边框宽度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Layoutable-getBorderWidth() : DirectionalEdgesT<number>--><!--Device-Layoutable-getBorderWidth() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | 子组件的边框宽度对象，包含四个方向的边框宽度值。单位：vp。 |

## getMargin

```TypeScript
getMargin() : DirectionalEdgesT<number>
```

调用此方法获取子组件的margin信息，返回其外边距。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Layoutable-getMargin() : DirectionalEdgesT<number>--><!--Device-Layoutable-getMargin() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | 子组件的外边距对象，包含四个方向的边距值。单位：vp。 |

## getPadding

```TypeScript
getPadding() : DirectionalEdgesT<number>
```

调用此方法获取子组件的padding信息，返回其内边距。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Layoutable-getPadding() : DirectionalEdgesT<number>--><!--Device-Layoutable-getPadding() : DirectionalEdgesT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DirectionalEdgesT](../arkts-apis/arkts-arkui-directionaledgest-i.md)&lt;number&gt; | 子组件的内边距对象，包含四个方向的内边距值。单位：vp。 |

## layout

```TypeScript
layout(position: Position): void
```

调用此方法设置子组件的位置信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Layoutable-layout(position: Position): void--><!--Device-Layoutable-layout(position: Position): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | Position | 是 | 绝对位置，包含x和y坐标（原点为父组件左上角，x轴向右为正，y轴向下为正）。单位：vp。 |

## measureResult

```TypeScript
measureResult: MeasureResult
```

子组件测量后的尺寸信息。单位为： vp。

**类型：** [MeasureResult](arkts-arkui-common-comp-measureresult-i.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-Layoutable-measureResult: MeasureResult--><!--Device-Layoutable-measureResult: MeasureResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uniqueId

```TypeScript
uniqueId?: number
```

系统为子组件分配的唯一标识UniqueID。用于唯一标识子组件以进行后续操作（如通过getFrameNodeByUniqueId获取FrameNode）。取值范围[0, +∞)。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

<!--Device-Layoutable-uniqueId?: number--><!--Device-Layoutable-uniqueId?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
