# ChipGroupPaddingOptions

Defines the top and bottom padding of a **ChipGroup** component, which is used to control the overall height of the ChipGroup.

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

Bottom padding. Percentage values are not supported.

Default value: **14**

Unit: vp

If this parameter is set to **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top: Length
```

Top padding. Percentage values are not supported.

Default value: **14**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
