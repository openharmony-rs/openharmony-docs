# HoverModeRegionLayoutOptions

悬停态布局信息。

> **说明：**
> 
> 1. 在悬停状态下，设备存在避让区域（折痕附近的区域，该区域内容可能不可见或受限），布局计算时需考虑该区域的影响。
> 
> 2. 在悬停模式下，屏幕上半部分为显示区域，下半部分为操作区域。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions, PresetSplitRatio, FoldSplitContainer, HoverModeStatus, OnHoverStatusChangeHandler, } from '@kit.ArkUI';
```

## extraRegionPosition

```TypeScript
extraRegionPosition?: ExtraRegionPosition
```

扩展区域的位置信息，可选值为TOP（上半区域）或BOTTOM（下半区域）。此字段在extra有效且showExtraRegion设置为true时生效。extra有效是指FoldSplitContainer组件传入了extra参数。默认值：`ExtraRegionPosition.TOP`

**类型：** [ExtraRegionPosition](arkts-arkui-arkui-advanced-foldsplitcontainer-extraregionposition-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## horizontalSplitRatio

```TypeScript
horizontalSplitRatio?: number
```

主要区域宽度与扩展区域宽度的比值。取值可使用PresetSplitRatio预设值或自定义数值，取值范围为(0, +∞)，传入小于等于0的值时使用默认值。此字段在extra有效且showExtraRegion设置为true时生效。 extra有效是指FoldSplitContainer组件传入了extra参数。默认值：[PresetSplitRatio](arkts-arkui-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md).LAYOUT_3V2

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showExtraRegion

```TypeScript
showExtraRegion?: boolean
```

可折叠屏幕在半折叠状态下是否显示扩展区域。设置为true时表示显示扩展区域，设置为false时表示不显示扩展区域。默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
