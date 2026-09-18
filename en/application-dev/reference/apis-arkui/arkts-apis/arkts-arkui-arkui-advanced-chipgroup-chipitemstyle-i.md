# ChipItemStyle

Defines the common attributes shared by all chips.

> **NOTE:** 
> 
> 1. The size settings for chips can be of two types: (1) **ChipSize**, which conveniently offers two size options,
> **NORMAL** and **SMALL**; (2) **SizeOptions**.
> 
> 2. If **backgroundColor** or **selectedBackgroundColor** is set to **undefined**, the default background color is used. If an invalid value is provided, the background color is transparent.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Chip background color.

Default value: **&#36;r('sys.color.ohos_id_color_button_normal')**

If this parameter is set to **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Chip text color.

Default value: **&#36;r('sys.color.ohos_id_color_text_primary')**

If this parameter is set to **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor?: ResourceColor
```

Background color of the chip when it is activated.

Default value: **&#36;r('sys.color.ohos_id_color_emphasize')**

If this parameter is set to **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor?: ResourceColor
```

Text color of the chip when it is activated.

Default value: **&#36;r('sys.color.ohos_id_color_text_primary_contrary')**

If this parameter is set to **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ChipSize | SizeOptions
```

Chip size. The ChipSize type needs to be imported from the Chip component.

Default value: **ChipSize.NORMAL** or **{ height: 0, width: 0 }**

If the value is **undefined**, the default value is used.

**Type:** [ChipSize](arkts-arkui-arkui-advanced-chip-chipsize-e.md) &#124; [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
