# ChipItemStyle

```TypeScript
export interface ChipItemStyle
```

Defines the common attributes of chips.

> **NOTE:** 
> 
> 1. The size settings for chips can be of two types: (1) **ChipSize**, which offers two size options, **NORMAL** and
> **SMALL**; (2) **SizeOptions**.
> 
> 2. When **backgroundColor** and **selectedBackgroundColor** are set to **undefined**, the default background color is displayed. When an invalid value is passed in, the background color is transparent.
> 
> 3. Starting from API version 26.0.0, when **backgroundSystemMaterial** is set to a system material with auto-invert, **fontColor** uses a system-predefined invertible color resource (such as `$r('sys.color.font_primary')`),and the color automatically adapts to the inverted color of the material background color.

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

Default value: **$r('sys.color.ohos_id_color_button_normal')**

**Note:** Since API version 26.0.0, when **backgroundSystemMaterial** is set, **backgroundColor** must be set to **Color.Transparent**; otherwise, it conflicts with the system material. When **backgroundSystemMaterial** is undefined, the **backgroundColor** attribute takes effect.

When the value is **undefined**, the default value of **backgroundColor** is used.

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

Default value: **$r('sys.color.ohos_id_color_text_primary')**

**Note:** Since API version 26.0.0, when **backgroundSystemMaterial** is set to a system material with auto-invert, **fontColor** uses a system-predefined invertible color resource, and the text color automatically adapts to the inverted color of the material background color.

When the value is **undefined**, the default value of **fontColor** is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor?: ResourceColor
```

Chip background color when selected.

Default value: **$r('sys.color.ohos_id_color_emphasize')**

**Note:** Since API version 26.0.0, when **selectedBackgroundSystemMaterial** is set, **selectedBackgroundColor** must be set to **Color.Transparent**; otherwise, it conflicts with the system material. When **selectedBackgroundSystemMaterial** is **undefined**, the **selectedBackgroundColor** attribute takes effect.

When the value is **undefined**, the default value of **selectedBackgroundColor** is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedFontColor

```TypeScript
selectedFontColor?: ResourceColor
```

Chip text color when selected.

Default value: **$r('sys.color.ohos_id_color_text_primary_contrary')**

**Note:** Since API version 26.0.0, when **selectedBackgroundSystemMaterial** is set to a system material with auto -invert, **selectedFontColor** uses a system-predefined invertible color resource (for example, `$r('sys.color.font_primary')`), and the color automatically adapts to the inverted color of the material background color.

When the value is **undefined**, the default value of **selectedFontColor** is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ChipSize | SizeOptions
```

Chip size. To use it, import the **ChipSize** type from the **Chip** component. **ChipSize.NORMAL** applies to most standard scenarios; **ChipSize.SMALL** applies to compact layouts or space-constrained scenarios; **SizeOptions** applies to special scenarios where a custom precise size is required.

Default value: **ChipSize.NORMAL** or **{ height: 0, width: 0 }**

When the value is **undefined**, the default value is used.

**Type:** [ChipSize](arkts-arkui-arkui-advanced-chip-chipsize-e.md) &#124; [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
