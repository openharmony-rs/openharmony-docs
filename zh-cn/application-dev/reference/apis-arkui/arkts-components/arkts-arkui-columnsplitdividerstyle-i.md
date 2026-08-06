# ColumnSplitDividerStyle

设置子组件与上下分割线的距离。 > **说明：** > > 与[RowSplit]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_相同，ColumnSplit的分割线可调整上下两侧子组件的高度，子组件的高度调整范围受其最大最小高度限制。 > > 支持[clip]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、[margin]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_等通用属性，未设置clip属性时，其默认值为true。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-interface ColumnSplitDividerStyle--><!--Device-unnamed-interface ColumnSplitDividerStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: Dimension
```

子组件与其下方分割线的距离。可调整间距（如避免内容与分割线重叠、美化布局等场景）。 默认值：0vp 取值范围：不支持负值。 非法值：按默认值处理，此时 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 接口获取到的属性值为undefined。

**类型：** Dimension

**默认值：** 0

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ColumnSplitDividerStyle-endMargin?: Dimension--><!--Device-ColumnSplitDividerStyle-endMargin?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: Dimension
```

子组件与其上方分割线的距离。可调整间距（如避免内容与分割线重叠、美化布局等场景）。 默认值：0vp 取值范围：不支持负值。 非法值：按默认值处理，此时 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 接口获取到的属性值为undefined。

**类型：** Dimension

**默认值：** 0

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ColumnSplitDividerStyle-startMargin?: Dimension--><!--Device-ColumnSplitDividerStyle-startMargin?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

