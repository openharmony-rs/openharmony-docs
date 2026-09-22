# SymbolItemOptions

```TypeScript
export interface SymbolItemOptions
```

Defines the suffix icon option type for **ChipGroup**.

**Since:** 14

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action: VoidCallback
```

Response event of the trailing icon. The callback is triggered when the user taps the tail icon. Set this parameter when you need to add custom interaction to the tail icon, such as performing a specific operation or opening an interface.

If the value is **undefined**, there is no tail icon response event.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the trailing icon. This description is used to explain the trailing icon to users in detail. You should provide a thorough text description for this attribute to help users understand the operation to be performed and its possible results, especially when such results cannot be directly inferred from the trailing icon's attributes and accessibility text. When a trailing icon that is selected has both a text attribute and an accessibility description attribute, the system first reads the text attribute, followed by the content of the accessibility description attribute.

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

Accessibility level of the trailing icon. Used to control whether the trailing icon can be recognized by accessibility services. Set this parameter when you need to provide access support for users of accessibility services, or when you need to exclude decorative icons from the accessibility tree.

Supported values:

**"auto"**: The trailing icon is converted to **"yes"**, applicable to most scenarios.

**"yes"**: The trailing icon can be recognized by accessibility services, applicable to scenarios where accessibility access needs to be explicitly enabled.

**"no"**: The trailing icon cannot be recognized by accessibility services, applicable to purely decorative icon scenarios.

**"no-hide-descendants"**: The trailing icon and all its child components cannot be recognized by accessibility services, applicable to scenarios where the entire area needs to be hidden.

Default value: **"auto"**.

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

Accessibility text attribute of the trailing icon. This attribute is used to further explain the trailing icon to users. You can set a relatively detailed description for this attribute of the trailing icon to help users understand the operation to be performed, especially the possible consequences that cannot be inferred from the trailing icon's own attributes and accessibility text. When the trailing icon has both a text attribute and an accessibility description attribute, the system first reads the text attribute of the trailing icon, followed by the content of the accessibility description attribute.

The default value is an empty string.

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbol

```TypeScript
symbol: SymbolGlyphModifier
```

**SymbolGlyphModifier** configuration object for the trailing icon, used to set the icon's display style, rendering mode, etc.

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
