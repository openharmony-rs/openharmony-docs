# ExpandedRegionLayoutOptions

展开态布局信息。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraRegionPosition

```TypeScript
extraRegionPosition?: ExtraRegionPosition
```

扩展区域的位置信息。当isExtraRegionPerpendicular设置为false时，此字段生效。

默认值：ExtraRegionPosition.top

**类型：** ExtraRegionPosition

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## horizontalSplitRatio

```TypeScript
horizontalSplitRatio?: number
```

主要区域与扩展区域之间的宽度比例。此字段在extra有效时生效。

默认值：[PresetSplitRatio](arkts-na-presetsplitratio-e.md).LAYOUT_3V2

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isExtraRegionPerpendicular

```TypeScript
isExtraRegionPerpendicular?: boolean
```

设置为true时，扩展区域从上到下贯穿整个组件；设置为false时，扩展区域不贯穿整个组件。此字段仅在extra有效时生效。

默认值：true

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## verticalSplitRatio

```TypeScript
verticalSplitRatio?: number
```

主要区域与次要区域之间的高度比例。

默认值：[PresetSplitRatio](arkts-na-presetsplitratio-e.md).LAYOUT_1V1

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

