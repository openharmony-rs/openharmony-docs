# SegmentButtonTextItem

```TypeScript
interface SegmentButtonTextItem
```

Text button information.

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

Accessibility description, which provides further explanation of the current component for users. Developers can set a relatively detailed explanatory text for this attribute to help users understand the operation to be performed, such as the possible consequences of the operation, especially when these consequences cannot be learned from the component's own attributes and accessibility text. If a component has both a text attribute and an accessibility description attribute, when the component is selected, the text attribute is announced first, followed by the content of the accessibility description attribute.

Default value: empty string.

If the value is **undefined**, the default value is used.

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

Accessibility level, which controls whether the current component can be recognized by accessibility services.

Supported values:

**"auto"**: The current component can be recognized by accessibility services.

**"yes"**: The current component can be recognized by accessibility services.

**"no"**: The current component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**

If the value is **undefined**, the default value is used.

**Type:** string

**Default:** "auto"

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

Button text.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
