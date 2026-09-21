# ChipGroupV2Item

```TypeScript
export declare class ChipGroupV2Item
```

Defines a single chip item in the **ChipGroupV2** component.

> **NOTE:** 
> 
> 1. If you need to support the close function while displaying a suffix icon (**suffixIcon** or
> **suffixSymbolIcon**), it is recommended to implement the deletion logic in the click event of **suffixIcon** or
> **suffixSymbolIcon**, or use other interaction methods as alternatives.

**Since:** 26.0.0

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipGroupV2ItemConfig)
```

A constructor used to create a **ChipGroupV2Item** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ChipGroupV2ItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemconfig-i.md) | Yes | Configuration of the **ChipGroupV2** item. |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

Accessibility description. This attribute is used to explain the component to users in detail. You should provide a thorough text description for this attribute to help users understand the operation and its possible results, especially when these results cannot be directly inferred from the component's attributes and accessibility text alone. When a component has both a text attribute and an accessibility description attribute and it is selected, the system first reads out the component's text attribute, followed by the content of the accessibility description attribute.

Default value: empty string.

When the value is **undefined**, the default value is used.

Decorator: **@Trace**

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

Accessibility level. This attribute is used to control whether the component can be recognized by accessibility services.

Supported values:

**"auto"**: the attribute value of the component is converted to **"yes"**.

**"yes"**: the component can be recognized by accessibility services.

**"no"**: the component cannot be recognized by accessibility services.

**"no-hide-descendants"**: the component and all its child components cannot be recognized by accessibility services.

When a value outside the supported range is passed in, the default value is used.

Default value: **"auto"**

When the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** string

**Default:** auto

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
public allowClose?: boolean
```

Whether to display the close icon. The value **true** means the close icon is displayed, and **false** means the opposite. When **suffixIcon** or **suffixSymbolIcon** is passed in, **allowClose** does not take effect. When neither **suffixIcon** nor **suffixSymbolIcon** is passed in, **allowClose** determines whether the close icon is displayed.

Default value: **false**

When the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** boolean

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeIcon

```TypeScript
public closeIcon?: ChipV2CloseConfig
```

Configuration of the close icon, including accessibility attribute configuration. Set this attribute when you need to customize the size or accessibility attributes of the close icon.

Default value:

- **fontSize**: when **size** is **ChipV2Size.SMALL**, the default value is  
`$r('sys.float.chip_small_font_size')`; in other cases, the default value is `$r('sys.float.chip_normal_font_size')`.  
- Accessibility: no accessibility description.

When the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ChipV2CloseConfig](arkts-arkui-arkui-advanced-chipv2-chipv2closeconfig-i.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
public label: ChipV2Label
```

**ChipV2** text.

Decorator: **@Trace**

**Type:** [ChipV2Label](arkts-arkui-arkui-advanced-chipv2-chipv2label-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
public prefixIcon?: ChipV2PrefixImageIcon
```

Prefix icon, used to display an image icon before the **ChipV2** text. Set this attribute when an icon identifier needs to be displayed on the left side of the **ChipV2**.

Default value: no prefix image icon.

When the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ChipV2PrefixImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2prefiximageicon-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbolIcon

```TypeScript
public prefixSymbolIcon?: ChipV2PrefixSymbolIcon
```

Prefix symbol icon, used to display a symbol icon before the **ChipV2** text. Set this attribute when a symbol icon identifier needs to be displayed on the left side of the **ChipV2**.

Default value: no prefix symbol icon.

When the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ChipV2PrefixSymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2prefixsymbolicon-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
public suffixIcon?: ChipV2SuffixImageIcon
```

Suffix icon, used to display an image icon after the **ChipV2** text. When this attribute is set, the **allowClose** attribute does not take effect.

Default value: no suffix image icon displayed.

When the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ChipV2SuffixImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2suffiximageicon-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolIcon

```TypeScript
public suffixSymbolIcon?: ChipV2SuffixSymbolIcon
```

Suffix symbol icon, used to display a symbol icon after the **ChipV2** text. When this attribute is set, the **allowClose** attribute does not take effect.

Default value: no suffix symbol icon displayed.

When the value is **undefined**, the default value is used.

Decorator: **@Trace**

**Type:** [ChipV2SuffixSymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2suffixsymbolicon-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
