# ScrollableBarModeOptions

Scrollable模式下的TabBar的布局样式对象。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Dimension
```

Scrollable模式下的TabBar的左右边距（不支持百分比设置）。

默认值：0.0

单位：vp

取值范围：[0, +∞)。

**类型：** Dimension

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nonScrollableLayoutStyle

```TypeScript
nonScrollableLayoutStyle?: LayoutStyle
```

Scrollable模式下不滚动时的页签排布方式。

默认值：LayoutStyle.ALWAYS_CENTER

**类型：** LayoutStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

