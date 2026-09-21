# ChipGroupPaddingOptions

```TypeScript
export interface ChipGroupPaddingOptions
```

Defines the top and bottom padding of a **ChipGroup** component, which is used to control the overall height of the **ChipGroup**.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom: Length
```

Bottom padding of the **ChipGroup** (percentage not supported).

If a negative number, percentage, or invalid string format is passed, the default value is used.

Default value: **14**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top: Length
```

Top padding of the **ChipGroup** (percentage not supported).

If a negative number, percentage, or invalid string format is passed, the default value is used.

Default value: **14**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
