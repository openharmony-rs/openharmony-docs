# SymbolItemOptions

Suffix icon option type of ChipGroup.

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

Action of the trailing symbol item.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessible description of the trailing symbol item. You can provide comprehensive text explanations to help users understand the operation they are about to perform and its potential consequences, especially when these cannot be inferred from the component's attributes and accessibility text alone. If a trailing symbol item contains both text information and the accessible description, the text is announced first and then the accessible description, when the trailing symbol item is selected.

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

Accessibility level of the trailing symbol item. It determines whether the trailing symbol item can be recognized by accessibility services.

The options are as follows:

**"auto"**: It is treated as "yes" by the system.

**"yes"**: The trailing symbol item can be recognized by accessibility services.

**"no"**: The trailing symbol item cannot be recognized by accessibility services.

**"no-hide-descendants"**: Neither the trailing symbol item nor its child components can be recognized by accessibility services.

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

Accessibility text of the trailing symbol item. If a trailing symbol item does not contain text information, it will not be announced by the screen reader when selected. In this case, the screen reader user cannot know which item is selected. To solve this problem, you can set accessibility text for trailing symbol items without text information. When such a trailing symbol item is selected, the screen reader announces the specified accessibility text, informing the user which item is selected.

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

Settings of the trailing symbol item.

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
