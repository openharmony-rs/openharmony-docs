# ScrollableBarModeOptions

Scrollable模式下的TabBar的布局样式对象。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## margin

```TypeScript
margin?: Dimension
```

Scrollable模式下的TabBar的左右边距（不支持百分比设置）。默认值：0.0单位：vp取值范围：[0, +∞)。设置为小于0的值时，按默认值显示。

**类型：** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## nonScrollableLayoutStyle

```TypeScript
nonScrollableLayoutStyle?: LayoutStyle
```

Scrollable模式下不滚动时的页签排布方式，仅水平模式下有效。默认值：LayoutStyle.ALWAYS_CENTER

**类型：** [LayoutStyle](arkts-arkui-layoutstyle-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
