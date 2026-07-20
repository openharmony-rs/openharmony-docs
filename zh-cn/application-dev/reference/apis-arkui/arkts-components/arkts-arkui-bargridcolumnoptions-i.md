# BarGridColumnOptions

TabBar栅格化方式设置的对象，包括栅格模式下的column边距和间隔，以及小、中、大屏下，页签占用的columns数量。

**起始版本：** 10

<!--Device-unnamed-interface BarGridColumnOptions--><!--Device-unnamed-interface BarGridColumnOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gutter

```TypeScript
gutter?: Dimension
```

栅格模式下的column间隔（不支持百分比设置）。

默认值：24.0

单位：vp

**类型：** Dimension

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BarGridColumnOptions-gutter?: Dimension--><!--Device-BarGridColumnOptions-gutter?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lg

```TypeScript
lg?: number
```

大屏下，页签占用的columns数量，必须是非负偶数。大屏为大于等于840vp但小于1024vp。

默认值为-1，代表页签占用TabBar全部宽度。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BarGridColumnOptions-lg?: number--><!--Device-BarGridColumnOptions-lg?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Dimension
```

栅格模式下的column边距（不支持百分比设置）。

默认值：24.0

单位：vp

**类型：** Dimension

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BarGridColumnOptions-margin?: Dimension--><!--Device-BarGridColumnOptions-margin?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## md

```TypeScript
md?: number
```

中屏下，页签占用的columns数量，必须是非负偶数。中屏为大于等于600vp但小于800vp。

默认值为-1，代表页签占用TabBar全部宽度。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BarGridColumnOptions-md?: number--><!--Device-BarGridColumnOptions-md?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sm

```TypeScript
sm?: number
```

小屏下，页签占用的columns数量，必须是非负偶数。小屏为大于等于320vp但小于600vp。

默认值为-1，代表页签占用TabBar全部宽度。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BarGridColumnOptions-sm?: number--><!--Device-BarGridColumnOptions-sm?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

