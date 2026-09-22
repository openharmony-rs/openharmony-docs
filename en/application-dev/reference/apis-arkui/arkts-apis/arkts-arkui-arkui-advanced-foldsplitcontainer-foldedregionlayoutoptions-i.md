# FoldedRegionLayoutOptions

```TypeScript
export interface FoldedRegionLayoutOptions
```

Defines the layout information for the folded state.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions, PresetSplitRatio, FoldSplitContainer, HoverModeStatus, OnHoverStatusChangeHandler, } from '@kit.ArkUI';
```

## verticalSplitRatio

```TypeScript
verticalSplitRatio?: number
```

Ratio of the primary area height to the secondary area height. The value can be a **PresetSplitRatio** preset value or a custom value. The value range is (0, +∞). If a value less than or equal to 0 is passed, the default value is used. This field takes effect only in the folded state layout. For example, when the value is 1.5, it indicates that the primary area height is 1.5 times the secondary area height (i.e., a 3:2 ratio).

Default value: [PresetSplitRatio](arkts-arkui-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md).LAYOUT_1V1

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
