# SuffixIconOptions

```TypeScript
export interface SuffixIconOptions extends IconCommonOptions
```

Defines the suffix icon options.

Inherits from [IconCommonOptions](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md).

**Inheritance/Implementation:** SuffixIconOptions extends [IconCommonOptions](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Callback for the suffix icon tap event, with no parameters and no return value. It is triggered when the user taps the suffix icon.

When the value is **undefined**, no suffix icon event is set.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description for the suffix icon. This description is used to explain the suffix icon to users in detail. Developers should provide a relatively detailed text description to help users understand the operation to be performed and its possible consequences, especially when these consequences cannot be directly learned from the suffix icon's attributes and accessibility text alone. If the suffix icon has both a text attribute and an accessibility description attribute, when the suffix icon is selected, the system first announces the text attribute of the suffix icon, and then announces the content of the accessibility description attribute.

Default value: **''**

When the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level for the suffix icon. Controls whether the suffix icon can be recognized by accessibility services.

Supported values:

**"auto"**: Converted to **"yes"** if the component has an action, and to **"no"** otherwise.

**"yes"**: The component can be recognized by accessibility services.

**"no"**: The component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**.

When the value is undefined, the default value is used.

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

Accessibility text attribute for the suffix icon. When the suffix icon does not contain a text attribute, the screen reader does not announce it upon selection, and the user cannot clearly know whether the suffix icon is currently selected. Developers can set accessibility text for such icons, which is announced by the screen reader upon selection.

Default value: **''**

When the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
