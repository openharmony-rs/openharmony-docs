# ChipGroupV2SymbolItemConfig

```TypeScript
export interface ChipGroupV2SymbolItemConfig
```

Defines the configuration type of the suffix symbol icon.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## action

```TypeScript
action: VoidCallback
```

Response event for the suffix icon.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the suffix icon. This description is used to explain the suffix icon in detail to users. You should provide a relatively detailed text description for this attribute of the suffix icon to help users understand the operation to be performed and its possible consequences, especially when these consequences cannot be directly learned from the trailing icon's attributes and accessibility text. When the suffix icon has both a text attribute and an accessibility description attribute and the icon is selected, the system announces the text attribute of the icon first, followed by the content of the accessibility description attribute.

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

Accessibility level of the suffix icon. It is used to control whether the trailing icon can be recognized by accessibility services.

Supported values:

**"auto"**: The attribute value of the suffix icon is converted to **"yes"**.

**"yes"**: The suffix icon can be recognized by accessibility services.

**"no"**: The suffix icon cannot be recognized by accessibility services.

**"no-hide-descendants"**: The suffix icon and all its child components cannot be recognized by accessibility services.

If a value outside the supported range is passed in, the default value is used.

Default value: **"auto"**

If the value is **undefined**, the default value is used.

**Type:** string

**Default:** auto

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text attribute of the suffix icon. It is used to provide further explanation of the trailing icon for users. You can set a relatively detailed description text for this attribute of the suffix icon to help users understand the operation to be performed. For example, it helps users understand the possible consequences of the operation to be performed, especially when these consequences cannot be learned from the suffix icon's attributes and accessibility text. When the suffix icon has both a text attribute and an accessibility description attribute and the icon is selected, the text attribute of the icon is announced first, followed by the content of the accessibility description attribute.

Default value: empty string.

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbol

```TypeScript
symbol: SymbolGlyphModifier
```

**SymbolGlyphModifier** configuration object for the suffix icon. After being set, the specified symbol icon is displayed in the suffix area of the **ChipGroupV2**, with support for configuring display style, rendering mode, color, and other attributes.

**Note:** When **SymbolGlyphModifier** is passed in, using **symbolEffect** to modify the animation type and [effectStrategy](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#effectstrategy) to set the animation is not supported.

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
