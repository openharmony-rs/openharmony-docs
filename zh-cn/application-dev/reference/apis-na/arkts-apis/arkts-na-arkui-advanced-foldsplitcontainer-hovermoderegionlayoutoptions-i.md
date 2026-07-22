# HoverModeRegionLayoutOptions

悬停态布局信息。
> **说明：**  
>  
> 1.在悬停状态下，设备存在避让区域，布局计算时需考虑该区域的影响。  
> > 2.在悬停模式下，屏幕上半部分为显示区域，下半部分为操作区域。

**起始版本：** 12

<!--Device-unnamed-export interface HoverModeRegionLayoutOptions--><!--Device-unnamed-export interface HoverModeRegionLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraRegionPosition

```TypeScript
extraRegionPosition?: ExtraRegionPosition
```

扩展区域的位置信息，当且仅当showExtraRegion设置为true时此字段才生效。

默认值：ExtraRegionPosition.top

**类型：** ExtraRegionPosition

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HoverModeRegionLayoutOptions-extraRegionPosition?: ExtraRegionPosition--><!--Device-HoverModeRegionLayoutOptions-extraRegionPosition?: ExtraRegionPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## horizontalSplitRatio

```TypeScript
horizontalSplitRatio?: number
```

主要区域与扩展区域之间的宽度比例。此字段在extra有效时生效。

默认值：[PresetSplitRatio](arkts-na-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md).LAYOUT_3V2

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HoverModeRegionLayoutOptions-horizontalSplitRatio?: number--><!--Device-HoverModeRegionLayoutOptions-horizontalSplitRatio?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showExtraRegion

```TypeScript
showExtraRegion?: boolean
```

可折叠屏幕在半折叠状态下是否显示扩展区域。设置为true时表示显示扩展区域，设置为false时表示不显示扩展区域。

默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HoverModeRegionLayoutOptions-showExtraRegion?: boolean--><!--Device-HoverModeRegionLayoutOptions-showExtraRegion?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

