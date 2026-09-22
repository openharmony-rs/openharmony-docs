# BorderOptions

```TypeScript
declare interface BorderOptions
```

边框属性集合，用于描述边框相关信息。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: EdgeColors | ResourceColor | LocalizedEdgeColors
```

设置边框颜色。

**类型：** EdgeColors &#124; [ResourceColor](arkts-arkui-resourcecolor-t.md) &#124; [LocalizedEdgeColors](arkts-arkui-localizededgecolors-i.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dashGap

```TypeScript
dashGap?: EdgeWidths | LengthMetrics | LocalizedEdgeWidths
```

设置虚线的线段间距，仅在边框样式为虚线时生效。

不支持设置百分比。

**卡片能力：** 该接口不支持在ArkTS卡片中使用。

**类型：** EdgeWidths &#124; [LengthMetrics](arkts-arkui-lengthmetrics-t.md) &#124; [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dashWidth

```TypeScript
dashWidth?: EdgeWidths | LengthMetrics | LocalizedEdgeWidths
```

设置虚线的线段长度，仅在边框样式为虚线时生效。

不支持设置百分比。

**卡片能力：** 该接口不支持在ArkTS卡片中使用。

**类型：** EdgeWidths &#124; [LengthMetrics](arkts-arkui-lengthmetrics-t.md) &#124; [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: BorderRadiuses | Length | LocalizedBorderRadiuses
```

设置边框圆角半径。

**类型：** [BorderRadiuses](arkts-arkui-borderradiuses-t.md) &#124; [Length](arkts-arkui-length-t.md) &#124; [LocalizedBorderRadiuses](arkts-arkui-localizedborderradiuses-i.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: EdgeStyles | BorderStyle
```

设置边框样式。

**类型：** EdgeStyles &#124; [BorderStyle](arkts-arkui-borderstyle-e.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: EdgeWidths | Length | LocalizedEdgeWidths
```

设置边框宽度。

**类型：** EdgeWidths &#124; [Length](arkts-arkui-length-t.md) &#124; [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
