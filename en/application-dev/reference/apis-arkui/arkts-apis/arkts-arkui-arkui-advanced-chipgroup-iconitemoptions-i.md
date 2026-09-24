# IconItemOptions

```TypeScript
export interface IconItemOptions
```

Defines the trailing builder API, which is used to configure the display properties of the trailing icon and its background area.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the trailing icon. This description is used to explain the trailing icon to users in detail. Developers should provide a relatively detailed text description for this attribute of the trailing icon to help users understand the operation to be performed and its possible consequences, especially when these consequences cannot be directly learned from the trailing icon's attributes and accessibility text alone. If the trailing icon has both a text attribute and an accessibility description attribute, when the trailing icon is selected, the system will first announce the text attribute of the trailing icon, and then announce the content of the accessibility description attribute.

Default value: empty string

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

Accessibility level of the trailing icon. Used to control whether the trailing icon can be recognized by accessibility services. Set this parameter when you need to provide access support for accessibility service users, or when you need to exclude decorative icons from the accessibility tree.

Supported values:

**"auto"**: The trailing icon is converted to **"yes"**, applicable to most scenarios.

**"yes"**: The trailing icon can be recognized by accessibility services, applicable to functional icons.

**"no"**: The trailing icon cannot be recognized by accessibility services, applicable to purely decorative icons.

**"no-hide-descendants"**: The trailing icon and all its child components cannot be recognized by accessibility services, applicable to scenarios where the entire area needs to be hidden.

Default value: **"auto"**

When the value is **undefined**, the default value is used.

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

Accessibility text attribute of the trailing icon. It is used to further explain the trailing icon to users. Developers can set a relatively detailed explanatory text for this attribute of the trailing icon to help users understand the operation to be performed. For example, help users understand the possible consequences of the operation to be performed, especially when these consequences cannot be learned from the trailing icon's own attributes and accessibility text. If the trailing icon has both a text attribute and an accessibility description attribute, when the trailing icon is selected, the text attribute of the trailing icon is announced first, followed by the content of the accessibility description attribute.

Default value: empty string.

When the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: Callback<void>
```

Callback for the tap event on the trailing icon. It is triggered when the user taps the trailing icon. Set this parameter to add custom interaction to the trailing icon, such as performing a specific operation or opening a page.

When it is **undefined**, this callback is not triggered.

**Type:** Callback&lt;void&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: IconOptions
```

Custom Builder icon.

When the chip size is **ChipSize.SMALL**, the default icon size is **{width: '16vp', height: '16vp'}**.

When the chip size is **ChipSize.NORMAL**, the default icon size is **{width: '24vp', height: '24vp'}**.

To dynamically change the size, the SymbolGlyphModifier type must be used when [IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md) is introduced.

When the value is **undefined**, the default value is used.

**Type:** [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
