# OutlineOptions

外描边选项设置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface OutlineOptions--><!--Device-unnamed-export declare interface OutlineOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: EdgeColors | ResourceColor | LocalizedEdgeColors
```

设置外描边颜色。 默认值：Color.Black

**类型：** [EdgeColors](arkts-na-units-edgecolors-i.md) \| [ResourceColor](arkts-na-resourcecolor-t.md) \| [LocalizedEdgeColors](arkts-na-units-localizededgecolors-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OutlineOptions-color?: EdgeColors | ResourceColor | LocalizedEdgeColors--><!--Device-OutlineOptions-color?: EdgeColors | ResourceColor | LocalizedEdgeColors-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: OutlineRadiuses | Dimension
```

设置外描边圆角半径，不支持百分比。 默认值：0 最大生效值：组件width/2 + outlineWidth或组件height/2 + outlineWidth。

**类型：** [OutlineRadiuses](arkts-na-units-outlineradiuses-i.md) \| [Dimension](arkts-na-dimension-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OutlineOptions-radius?: OutlineRadiuses | Dimension--><!--Device-OutlineOptions-radius?: OutlineRadiuses | Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: EdgeOutlineStyles | OutlineStyle
```

设置外描边样式。 默认值：OutlineStyle.SOLID

**类型：** [EdgeOutlineStyles](arkts-na-units-edgeoutlinestyles-i.md) \| [OutlineStyle](../../apis-arkui/arkts-components/arkts-arkui-outlinestyle-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OutlineOptions-style?: EdgeOutlineStyles | OutlineStyle--><!--Device-OutlineOptions-style?: EdgeOutlineStyles | OutlineStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: EdgeOutlineWidths | Dimension
```

设置外描边宽度，不支持百分比。 默认值：0，外描边效果中width为必设项，否则不显示外描边。

**类型：** [EdgeOutlineWidths](arkts-na-units-edgeoutlinewidths-i.md) \| [Dimension](arkts-na-dimension-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OutlineOptions-width?: EdgeOutlineWidths | Dimension--><!--Device-OutlineOptions-width?: EdgeOutlineWidths | Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

