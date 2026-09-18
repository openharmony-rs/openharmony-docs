# ChipGroupSpaceOptions

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

Right padding. Percentage values are not supported.

Default value: **16**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemSpace

```TypeScript
itemSpace?: string | number
```

Spacing between chips. Percentage values are not supported.

Value range:

Number type: a value greater than or equal to 0 (for example, **0**, **8**, **16**, or **24.5**)

String type: a value greater than or equal to 0, with a unit of fp, vp, px, or lpx (for example, **"8vp"**, **"16fp"**, **"12px"**, or **"10lpx"**)

Not supported: negative values, percentage units, and invalid string formats.

Default value: **8**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** string &#124; number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startSpace

```TypeScript
startSpace?: Length
```

Left padding. Percentage values are not supported.

Default value: **16**

Unit: vp

If this parameter is set to **undefined**, the default value is used.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
