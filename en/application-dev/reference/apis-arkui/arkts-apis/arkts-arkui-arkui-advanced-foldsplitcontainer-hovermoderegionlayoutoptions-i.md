# HoverModeRegionLayoutOptions

```TypeScript
export interface HoverModeRegionLayoutOptions
```

Defines layout information for the hover state.

> **NOTE:** 
> 
> 1. In the hover state, the device has an avoidance area (the area near the crease where content may be invisible or restricted), and the impact of this area must be considered during layout calculation.
> 
> 2. In hover mode, the upper half of the screen is the display area, and the lower half is the operation area.

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

Position information of the expanded area. The value can be **TOP** (upper area) or **BOTTOM** (lower area). This field takes effect when **extra** is valid and **showExtraRegion** is set to **true**. "extra is valid" means that the **extra** parameter is passed to the **FoldSplitContainer** component.

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

Ratio of the primary area width to the expanded area width. The value can be a preset value from **PresetSplitRatio** or a custom value, with a value range of (0, +∞). If a value less than or equal to 0 is passed, the default value is used. This field takes effect when **extra** is valid and **showExtraRegion** is set to **true**. "extra is valid" means that the **extra** parameter is passed to the **FoldSplitContainer** component.

Default value: [PresetSplitRatio](arkts-arkui-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md).LAYOUT_3V2

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showExtraRegion

```TypeScript
showExtraRegion?: boolean
```

Whether to display the expanded area when the foldable screen is in the hover state. The value **true** means to display the expanded area, and **false** means not to display it.

Default value: **false**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
