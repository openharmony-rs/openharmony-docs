# HoverModeRegionLayoutOptions

Layout information for the semi-folded state.

> **NOTE:** 
> 
> 1. In semi-folded state, the device contains an avoidance area, and layout calculations must account for the impact of this avoidance area on the overall layout.
> 2. In semi-folded mode, the upper screen is dedicated to content display, and the lower screen is reserved for interaction.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions, PresetSplitRatio, FoldSplitContainer, HoverModeStatus, OnHoverStatusChangeHandler, } from '@kit.ArkUI';
```

## extraRegionPosition

```TypeScript
extraRegionPosition?: ExtraRegionPosition
```

Position information of the extra region. This setting takes effect only when **showExtraRegion** is set to **true**.

Default value: **ExtraRegionPosition.top**.

**Type:** [ExtraRegionPosition](arkts-arkui-arkui-advanced-foldsplitcontainer-extraregionposition-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## horizontalSplitRatio

```TypeScript
horizontalSplitRatio?: number
```

Width ratio between the primary and extra regions. This setting takes effect only when **extra** is effective. The value range is all integers. Default value: {@link.PresetSplitRatio}.LAYOUT_3V2.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showExtraRegion

```TypeScript
showExtraRegion?: boolean
```

Whether to display the extra region in the half-folded state. The value **true** means to display the extra region in the half-folded state, and **false** means the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
