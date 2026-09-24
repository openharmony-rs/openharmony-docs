# SegmentButtonIconTextItem

```TypeScript
interface SegmentButtonIconTextItem
```

Icon and text button information.

> **NOTE:** 
> 
> Both the **icon** and **selectedIcon** attributes must be set. Setting only one of them is invalid.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SegmentButton, SegmentButtonOptions, SegmentButtonItemOptionsArray, TabSegmentButtonOptions, TabSegmentButtonConstructionOptions, CapsuleSegmentButtonOptions, CapsuleSegmentButtonConstructionOptions, SegmentButtonTextItem, SegmentButtonIconItem, SegmentButtonIconTextItem, DimensionNoPercentage, CommonSegmentButtonOptions, ItemRestriction, SegmentButtonItemTuple, SegmentButtonItemArray, SegmentButtonItemOptionsConstructorOptions, SegmentButtonItemOptions, BorderRadiusMode } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description, which provides additional explanation about the current component for users. Developers can set a relatively detailed explanatory text for this attribute to help users understand the operation to be performed, such as the possible consequences of the operation, especially when such consequences cannot be learned from the component's own attributes and accessibility text. If a component has both a text attribute and an accessibility description attribute, the text attribute is announced first when the component is selected, followed by the accessibility description.

Default value: empty string.

When the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Default:** ""

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level, which determines whether the current component can be recognized by accessibility services.

Supported values:

**"auto"**: The current component can be recognized by accessibility services.

**"yes"**: The current component can be recognized by accessibility services.

**"no"**: The current component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**

When the value is **undefined**, the default value is used.

**Type:** string

**Default:** "auto"

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: ResourceStr
```

Icon of the button in unselected state.

When the value is **undefined**, no icon is displayed.

**Note:** **icon** and **selectedIcon** must be set together. Setting either alone is ineffective.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconAccessibilityText

```TypeScript
iconAccessibilityText?: ResourceStr
```

Accessibility text of the button icon in unselected state.

Default value: empty string.

When the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Default:** ""

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIcon

```TypeScript
selectedIcon: ResourceStr
```

Icon of the button in selected state.

When the value is **undefined**, no icon is displayed.

**Note:** **icon** and **selectedIcon** must be set together. Setting either alone is ineffective.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIconAccessibilityText

```TypeScript
selectedIconAccessibilityText?: ResourceStr
```

Accessibility text of the button icon in selected state.

Default value: empty string.

When the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Default:** ""

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

Button text.

When the value is **undefined**, no text content is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
