# OutlineOptions

外描边选项设置。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: EdgeColors | ResourceColor | LocalizedEdgeColors
```

设置外描边颜色。

默认值：Color.Black

**类型：** EdgeColors &#124; [ResourceColor](arkts-arkui-resourcecolor-t.md) &#124; [LocalizedEdgeColors](arkts-arkui-localizededgecolors-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: OutlineRadiuses | Dimension
```

设置外描边圆角半径，不支持百分比。

默认值：0

最大生效值：组件width/2 + outlineWidth或组件height/2 + outlineWidth。

**类型：** OutlineRadiuses &#124; [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: EdgeOutlineStyles | OutlineStyle
```

设置外描边样式。

默认值：OutlineStyle.SOLID

**类型：** EdgeOutlineStyles &#124; [OutlineStyle](../arkts-components/arkts-arkui-outlinestyle-e.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: EdgeOutlineWidths | Dimension
```

设置外描边宽度，不支持百分比。

默认值：0，外描边效果中width为必设项，否则不显示外描边。

**类型：** EdgeOutlineWidths &#124; [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
