# SuffixImageIconOptions

```TypeScript
export interface SuffixImageIconOptions extends IconOptions
```

Defines the configuration options for suffix icons.

Inherits from [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md).

**Inheritance/Implementation:** SuffixImageIconOptions extends [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md)

**Since:** 14

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: VoidCallback
```

Response event of the suffix icon. The callback is triggered when the user taps the suffix icon. Set this parameter when you need to add custom interaction to the suffix icon, such as performing a search, opening a menu, or deleting an item.

If the value is **undefined**, there is no suffix icon response event.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the suffix icon. This description is used to explain the suffix icon to users in detail. You should provide a thorough text description for this attribute of the suffix icon to help users understand the operation to be performed and its possible consequences, especially when such consequences cannot be directly inferred from the suffix icon's attributes and accessibility text. When the suffix icon has both a text attribute and an accessibility description attribute, the system first reads the text attribute of the suffix icon, followed by the content of the accessibility description attribute.

Default value: empty string.

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the suffix icon. This attribute controls whether the suffix icon can be recognized by accessibility services. Set this parameter when you need to provide access support for users of accessibility services, or when you need to exclude decorative icons from the accessibility tree.

Supported values:

**"auto"**: The suffix icon is converted to **"yes"** if an action exists, and to **"no"** if no action exists. This applies to most scenarios.

**"yes"**: The suffix icon can be recognized by accessibility services. This applies to functional icons.

**"no"**: The suffix icon cannot be recognized by accessibility services. This applies to purely decorative icons.

**"no-hide-descendants"**: The suffix icon and all its child components cannot be recognized by accessibility services. This applies to scenarios where an entire area needs to be hidden.

Default value: **"auto"**

If the value is **undefined**, the default value is used.

**Type:** string

**Default:** "auto"

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text attribute of the suffix icon. This attribute is used to further explain the suffix icon to users. You can set a relatively detailed description for this attribute of the suffix icon to help users understand the operation to be performed, especially the possible consequences that cannot be inferred from the suffix icon's own attributes and accessibility text. When the suffix icon has both a text attribute and an accessibility description attribute, the system first reads the text attribute of the suffix icon, followed by the content of the accessibility description attribute.

Default value: empty string.

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
