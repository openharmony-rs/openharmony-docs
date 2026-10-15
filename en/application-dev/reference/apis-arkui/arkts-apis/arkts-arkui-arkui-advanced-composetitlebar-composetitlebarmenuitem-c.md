# ComposeTitleBarMenuItem

```TypeScript
export declare class ComposeTitleBarMenuItem
```

Declaration of the menu item on the right side.

**Since:** 10

<!--Device-unnamed-export declare class ComposeTitleBarMenuItem--><!--Device-unnamed-export declare class ComposeTitleBarMenuItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeTitleBar, ComposeTitleBarMenuItem } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Callback invoked when a menu item is tapped. The **item** parameter does not support triggering the action event.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComposeTitleBarMenuItem-action?: () => void--><!--Device-ComposeTitleBarMenuItem-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the custom button on the right of the title bar, used to explain the component function and operation consequences to users in detail. When the component is selected, the system announces the text attribute first, and then the accessibility description. The item attribute does not support setting this attribute.

Default value: "Double-tap with one finger to execute".

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ComposeTitleBarMenuItem-accessibilityDescription?: ResourceStr--><!--Device-ComposeTitleBarMenuItem-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the custom button on the right of the title bar, which controls whether the current item can be recognized by accessibility services. This applies only to **items** in **menuItems**, not to the item parameter.

Supported values:

**"auto"**: equivalent to **"yes"**.

**"yes"**: can be recognized by accessibility services.

**"no"**: cannot be recognized by accessibility services.

**"no-hide-descendants"**: neither the current item nor its child components can be recognized.

Default value: **"auto"**. The item parameter does not support setting this attribute.

**Type:** string

**Default:** "auto".The options are as follows:<br>"auto":The value is converted to "yes" or "no" based on the component."yes": the current component is selectable for the accessibility service."no": The current component is not selectable for the accessibility service."no-hide-descendants":The current component and all its child components are not selectable<br> for the accessibility service.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ComposeTitleBarMenuItem-accessibilityLevel?: string--><!--Device-ComposeTitleBarMenuItem-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text of the custom button on the right of the title bar. When a component has no text attribute, the screen reader does not announce it. After this attribute is set, the screen reader can announce the content, helping users understand the selected component. The **item** attribute does not support setting this attribute.

Default value: when **label** is set, the default value is the content of the **label** attribute of the current item; when **label** is not set, the default value is an empty string.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ComposeTitleBarMenuItem-accessibilityText?: ResourceStr--><!--Device-ComposeTitleBarMenuItem-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

Whether to enable. Default value: **false**.

The value **true** indicates enabled, and **false** indicates disabled.

The **item** parameter does not support triggering the **isEnabled** attribute.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComposeTitleBarMenuItem-isEnabled?: boolean--><!--Device-ComposeTitleBarMenuItem-isEnabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

Icon label description, used to set auxiliary text information for the icon. When **accessibilityText** is not set, **label** can serve as the default value for the accessibility text.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ComposeTitleBarMenuItem-label?: ResourceStr--><!--Device-ComposeTitleBarMenuItem-label?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource, which takes precedence over **value**. This attribute is not supported for the avatar on the left of the item. If not set, the icon resource specified by the **value** attribute is used.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ComposeTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier--><!--Device-ComposeTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Icon resource. If the **symbolStyle** attribute is also set, **symbolStyle** takes precedence.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ComposeTitleBarMenuItem-value: ResourceStr--><!--Device-ComposeTitleBarMenuItem-value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
