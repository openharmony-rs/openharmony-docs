# ChipGroupSpaceOptions

```TypeScript
export interface ChipGroupSpaceOptions
```

Defines the left and right padding of the chip group, and the spacing between chips.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## endSpace

```TypeScript
endSpace?: Length
```

Right padding (percentages are not supported).

When a negative number, percentage, or invalid string format is passed, the default value is used.

Default value: **16**

Unit: vp

When the value is **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
itemSpace?: string | number
```

Spacing between chips (percentages are not supported).

Value range:

number type: a value greater than or equal to 0 (for example, 0, 8, 16, 24.5).

string type: a string in fp | vp | px | lpx with the numeric part greater than or equal to 0 (for example, "8vp", "16fp", "12px", "10lpx").

**Note:** When a negative number, percentage, or invalid string format is passed, the default value is used.

Default value: **8**

Unit: vp

When the value is **undefined**, the default value is used.

**Type:** string &#124; number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startSpace

```TypeScript
startSpace?: Length
```

Left padding (percentages are not supported).

When a negative number, percentage, or invalid string format is passed, the default value is used.

Default value: **16**

Unit: vp

When the value is **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
