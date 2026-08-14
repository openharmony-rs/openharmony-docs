# ChipV2LocalizedLabelMarginConfig

ChipV2LocalizedLabelMarginConfig用于定义本地化文本与左右侧图标之间间距配置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export interface ChipV2LocalizedLabelMarginConfig--><!--Device-unnamed-export interface ChipV2LocalizedLabelMarginConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: LengthMetrics
```

文本与结束侧图标之间间距，不支持百分比。传入百分比时按默认值处理。 默认值： size为ChipV2Size.SMALL时，end默认值： `LengthMetrics.resource(\$r('sys.float.chip_small_text_margin'))`。 size为ChipV2Size.NORMAL时，end默认值： `LengthMetrics.resource(\$r('sys.float.chip_normal_text_margin'))`。 单位：vp 取值范围：[0, +∞) 超出取值范围按默认值处理。 值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LocalizedLabelMarginConfig-end?: LengthMetrics--><!--Device-ChipV2LocalizedLabelMarginConfig-end?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: LengthMetrics
```

文本与起始侧图标之间间距，不支持百分比。传入百分比时按默认值处理。 默认值： size为ChipV2Size.SMALL时，start默认值： `LengthMetrics.resource(\$r('sys.float.chip_small_text_margin'))`。 size为ChipV2Size.NORMAL时，start默认值： `LengthMetrics.resource(\$r('sys.float.chip_normal_text_margin'))`。 单位：vp 取值范围：[0, +∞) 超出取值范围按默认值处理。 值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LocalizedLabelMarginConfig-start?: LengthMetrics--><!--Device-ChipV2LocalizedLabelMarginConfig-start?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

