# ExpandedRegionLayoutOptions

```TypeScript
export interface ExpandedRegionLayoutOptions
```

Defines layout information for the expanded state.

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

Position of the expanded area. The options are **TOP** (upper half) and **BOTTOM** (lower half). This field takes effect when **isExtraRegionPerpendicular** is set to **false** and **extra** is valid.

Default value: `ExtraRegionPosition.TOP`

**Type:** [ExtraRegionPosition](arkts-arkui-arkui-advanced-foldsplitcontainer-extraregionposition-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## horizontalSplitRatio

```TypeScript
horizontalSplitRatio?: number
```

Ratio of the primary area width to the expanded area width. The value can be a preset value of **PresetSplitRatio** or a custom value. The value range is (0, +∞). If a value less than or equal to 0 is passed, the default value is used. This field takes effect only when **extra** is valid.

Default value: [PresetSplitRatio](arkts-arkui-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md).LAYOUT_3V2

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isExtraRegionPerpendicular

```TypeScript
isExtraRegionPerpendicular?: boolean
```

Whether the expanded area runs through the entire component from top to bottom. The value **true** means the expanded area runs through the entire component, and **false** means the opposite. This field takes effect only when **extra** is valid.

Default value: **true**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## verticalSplitRatio

```TypeScript
verticalSplitRatio?: number
```

Ratio of the primary area height to the secondary area height. The value can be a preset value of **PresetSplitRatio** or a custom value. The value range is (0, +∞). If a value less than or equal to 0 is passed, the default value is used. For example, when the value is 1.5, the primary area height is 1.5 times the secondary area height (that is, a 3:2 ratio).

Default value: [PresetSplitRatio](arkts-arkui-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md).LAYOUT_1V1

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
