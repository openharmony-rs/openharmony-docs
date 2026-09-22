# ChipGroupV2ItemConfig

```TypeScript
export interface ChipGroupV2ItemConfig
```

Defines the non-common attribute configuration of a **ChipV2**.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the **ChipV2** item in **ChipGroupV2**. This description is used to explain the **ChipV2** item in **ChipGroupV2** to users in detail. You should provide a relatively detailed text description for the attributes of the **ChipV2** item in **ChipGroupV2** to help users understand the operation to be performed and its possible results, especially when these results cannot be directly learned from the attributes and accessibility text of the **ChipV2** item in **ChipGroupV2** alone. If the **ChipV2** item in **ChipGroupV2** has both a text attribute and an accessibility description attribute and the item is selected, the system first announces the item's text attribute, and then announces the content of the accessibility description attribute.

Default value: empty string.

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the **ChipV2** item in **ChipGroupV2**. This attribute is used to control whether the **ChipV2** item in **ChipGroupV2** can be recognized by accessibility services.

Supported values:

**"auto"**: The attribute value of the **ChipV2** item in **ChipGroupV2** is converted to **"yes"**.

**"yes"**: The **ChipV2** item in **ChipGroupV2** can be recognized by accessibility services.

"no": The **ChipV2** item in **ChipGroupV2** cannot be recognized by accessibility services.

**"no-hide-descendants"**: The **ChipV2** item in **ChipGroupV2** and all its child components cannot be recognized by accessibility services.

If a value outside the supported range is passed in, the default value is used.

Default value: **"auto"**

If the value is **undefined**, the default value is used.

**Type:** string

**Default:** auto

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

Whether to display the close icon. Value rules: **true** means to display the close icon, and **false** means the opposite.

When **suffixIcon** or **suffixSymbolIcon** is passed in, **allowClose** does not take effect. When neither **suffixIcon** nor **suffixSymbolIcon** is passed in, **allowClose** determines whether the close icon is displayed.

Default value: **false**

If the value is **undefined**, the default value is used.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeIcon

```TypeScript
closeIcon?: ChipV2CloseConfig
```

Configuration of the close icon, including accessibility attribute configuration. Set this attribute when you need to customize the size or accessibility attributes of the close icon.

Default value:

- **fontSize**: when **size** is **ChipV2Size.SMALL**, the default value is  
`$r('sys.float.chip_small_font_size')`; in other cases, the default value is `$r('sys.float.chip_normal_font_size')`.  
- Accessibility: no accessibility description.

If the value is **undefined**, the default value is used.

**Type:** [ChipV2CloseConfig](arkts-arkui-arkui-advanced-chipv2-chipv2closeconfig-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: ChipV2LabelConfig
```

Text attribute.

**Type:** [ChipV2LabelConfig](arkts-arkui-arkui-advanced-chipv2-chipv2labelconfig-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: ChipV2PrefixImageIconConfig
```

Prefix image icon, which is used to display an image icon before the **ChipV2** text. Set this attribute when an icon identifier needs to be displayed on the left side of **ChipV2**.

Default value: no prefix image icon.

If the value is **undefined**, the default value is used.

**Type:** [ChipV2PrefixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2prefiximageiconconfig-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbolIcon

```TypeScript
prefixSymbolIcon?: ChipV2PrefixSymbolIconConfig
```

Prefix symbol icon, which is used to display a symbol icon before the **ChipV2** text. Set this attribute when a symbol icon identifier needs to be displayed on the left side of **ChipV2**.

Default value: no prefix symbol icon.

If the value is **undefined**, the default value is used.

**Type:** [ChipV2PrefixSymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2prefixsymboliconconfig-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: ChipV2SuffixImageIconConfig
```

Suffix image icon, which is used to display an image icon after the **ChipV2** text. When this attribute is set, the **allowClose** attribute does not take effect.

Default value: no suffix image icon is displayed.

If the value is **undefined**, the default value is used.

**Type:** [ChipV2SuffixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffiximageiconconfig-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolIcon

```TypeScript
suffixSymbolIcon?: ChipV2SuffixSymbolIconConfig
```

Suffix symbol icon, which is used to display a symbol icon after the **ChipV2** text. When this attribute is set, the **allowClose** attribute does not take effect.

Default value: no suffix symbol icon is displayed.

If the value is **undefined**, the default value is used.

**Type:** [ChipV2SuffixSymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffixsymboliconconfig-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
