# FoldedRegionLayoutOptions

折叠态布局信息。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-export interface FoldedRegionLayoutOptions--><!--Device-unnamed-export interface FoldedRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalSplitRatio

```TypeScript
verticalSplitRatio?: number
```

主要区域高度与次要区域高度的比值。取值可使用PresetSplitRatio预设值或自定义数值，取值范围为(0, +∞)，传入小于等于0的值时使用默认值。此字段仅在折叠态布局下生效。例如：取值为1.5时，表示主要区域高度是次要区域 高度的1.5倍（即3:2比例）。 默认值：[PresetSplitRatio](arkts-arkui-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md#PresetSplitRatio).LAYOUT_1V1

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FoldedRegionLayoutOptions-verticalSplitRatio?: number--><!--Device-FoldedRegionLayoutOptions-verticalSplitRatio?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

