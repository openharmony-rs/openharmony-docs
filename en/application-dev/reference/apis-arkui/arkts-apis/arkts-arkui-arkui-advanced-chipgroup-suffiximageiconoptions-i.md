# SuffixImageIconOptions

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

Action of the suffix icon.

If the value is **undefined**, no suffix icon interaction event is triggered.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessible description of the suffix icon. You can provide comprehensive text explanations to help users understand the operation they are about to perform and its potential consequences, especially when these cannot be inferred from the component's attributes and accessibility text alone. If an icon contains both text information and the accessible description, the text is announced first and then the accessible description, when the icon is selected.

The default value is an empty string.

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

Accessibility level of the suffix icon. It determines whether the icon can be recognized by accessibility services.

The options are as follows:

**"auto"**: It is treated as "yes" when **action** is set for the icon and as "no" otherwise.

**"yes"**: The icon can be recognized by accessibility services.

**"no"**: The icon cannot be recognized by accessibility services.

**"no-hide-descendants"**: Neither the icon nor its child components can be recognized by accessibility services.

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

Accessibility text, that is, accessibility label name, of the suffix icon. If an icon does not contain text information, it will not be announced by the screen reader when selected. In this case, the screen reader user cannot know which icon is selected. To solve this problem, you can set accessibility text for icons without text information. When such an icon is selected, the screen reader announces the specified accessibility text, informing the user which icon is selected.

The default value is an empty string.

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
