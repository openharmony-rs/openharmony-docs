# ChipV2CloseConfig

ChipV2CloseConfig用于定义ChipV2组件关闭图标的功能属性配置，包括无障碍功能属性。 继承自[ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md#ChipV2AccessibilityConfig)。

**继承/实现关系：** ChipV2CloseConfig extends [ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md#ChipV2AccessibilityConfig)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export interface ChipV2CloseConfig--><!--Device-unnamed-export interface ChipV2CloseConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

设置ChipV2组件默认关闭图标的大小，不支持百分比。传入百分比时按默认值处理。 默认值： size为ChipV2Size.SMALL时，默认值：`\$r('sys.float.chip_small_font_size')`。 size不为ChipV2Size.SMALL时，默认值：`\$r('sys.float.chip_normal_font_size')` 单位：fp 值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2CloseConfig-fontSize?: LengthMetrics--><!--Device-ChipV2CloseConfig-fontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

