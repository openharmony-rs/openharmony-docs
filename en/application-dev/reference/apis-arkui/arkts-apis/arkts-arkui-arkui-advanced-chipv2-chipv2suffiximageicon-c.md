# ChipV2SuffixImageIcon

```TypeScript
export declare class ChipV2SuffixImageIcon extends ChipV2ImageIcon
```

Defines the suffix icon class.

This API inherits from [ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md).

**Inheritance/Implementation:** ChipV2SuffixImageIcon extends [ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md)

**Since:** 26.0.0

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## action

```TypeScript
public action?: VoidCallback
```

Callback for the suffix icon tap event. This callback is invoked when the suffix icon is tapped.

Default value: no suffix icon event is set.

When the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: ChipV2SuffixImageIconConfig)
```

A constructor used to create a **ChipV2SuffixImageIcon** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ChipV2SuffixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffiximageiconconfig-i.md) | Yes | Attribute configuration of the suffix icon, which is used to set the display attributes, accessibility functions, and tap events of the suffix Image icon. This parameter inherits from **ChipV2ImageIconConfig** and **ChipV2AccessibilityConfig** and includes configuration options such as **src**, **size**, **accessibilityLevel**, and **action**. |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

Accessibility description. This description is used to explain the current component to users in detail. You should provide comprehensive text descriptions to help users understand the actions to be performed and their consequences, especially when these consequences cannot be directly inferred from the component's attributes and accessibility text. When a component that is selected has both a text attribute and an accessibility description attribute, the system first reads the component's text attribute, followed by the accessibility description.

Default value: empty string.

When the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
```

Accessibility level. This attribute controls whether the suffix icon can be recognized by accessibility services.

Supported values:

**"auto"**: The attribute value of the current component is converted to **"yes"**.

**"yes"**: The current component can be recognized by accessibility services.

**"no"**: The current component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**

When the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** string

**Default:** auto

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
public accessibilityText?: ResourceStr
```

Accessibility text. When a component has no text attribute, the screen reader does not read it aloud when this component is selected, making it difficult for users to identify the currently selected component. You can set accessibility text for such components so that the screen reader reads the text aloud, helping users identify the selected component.

Default value: empty string.

When the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
