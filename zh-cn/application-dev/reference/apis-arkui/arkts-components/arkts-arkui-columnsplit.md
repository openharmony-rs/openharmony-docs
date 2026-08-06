# ColumnSplit

将子组件纵向布局，并在每个子组件之间插入横向分割线。适用于需要垂直方向上多区域布局且支持动态调整区域大小的场景，如仪表盘界面、可调节高度的上下分区布局等。通过可拖拽的分割线，用户可以灵活调整各区域高度，提升界面交互性和用户体验。 > **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件 可以包含子组件。 ColumnSplit通过分割线限制子组件的高度。初始化时，分割线位置根据子组件的高度来计算。初始化后，动态修改子组件的高度不生效，分割线位置保持不变。设置resizeable(true)后，可通过拖动相邻分割线改变子组件高度。 初始化后，当动态修改[margin]{@link CommonMethod#margin}、[border]{@link CommonMethod#border}、 [padding]{@link CommonMethod#padding}通用属性导致子组件尺寸大于相邻分割线间距时，不支持拖动分割线改变子组件的高度。

## ColumnSplit

```TypeScript
ColumnSplit()
```

带分割线的子组件纵向布局。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ColumnSplitInterface-(): ColumnSplitAttribute--><!--Device-ColumnSplitInterface-(): ColumnSplitAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

