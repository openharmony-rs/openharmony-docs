# SelectTitleBarMenuItem

```TypeScript
export declare class SelectTitleBarMenuItem
```

Declaration of the menu item on the right side.

**Since:** 10

<!--Device-unnamed-export declare class SelectTitleBarMenuItem--><!--Device-unnamed-export declare class SelectTitleBarMenuItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { SelectTitleBar, SelectTitleBarMenuItem } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Callback invoked when the custom button on the right is tapped. Developers can define custom operations to be executed after the button is tapped.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectTitleBarMenuItem-action?: () => void--><!--Device-SelectTitleBarMenuItem-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessible description. You can provide comprehensive text explanations to help users understand the operation they are about to perform and its potential consequences, especially when these cannot be inferred from the component's attributes and accessibility text alone. If a component contains both text information and the accessible description, the text is announced first and then the accessible description, when the component is selected.

Default value: **"Double-tap to activate"**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SelectTitleBarMenuItem-accessibilityDescription?: ResourceStr--><!--Device-SelectTitleBarMenuItem-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the custom button on the right side of the title bar. It controls whether the current item can be recognized by accessibility services.

Supported values:

**"auto"**: The component is automatically converted to **"yes"** or **"no"** based on the specific situation.

**"yes"**: The component can be recognized by accessibility services.

**"no"**: The component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**.

**Type:** string

**Default:** "auto"

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SelectTitleBarMenuItem-accessibilityLevel?: string--><!--Device-SelectTitleBarMenuItem-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text attribute of the custom button on the right side of the title bar. When a component does not contain a text attribute, the screen reader does not announce anything when this component is selected, and the user cannot clearly know which component is currently selected. To address this scenario, developers can set accessibility text for components that do not contain text information. When the screen reader selects this component, it announces the content of the accessibility text, helping screen reader users clearly know which component they have selected.

Default value: when **label** is set, the default value is the content of the **label** attribute of the current item; when **label** is not set, the default value is a space character.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SelectTitleBarMenuItem-accessibilityText?: ResourceStr--><!--Device-SelectTitleBarMenuItem-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

Whether to enable.

Default value: **false**. The value **true** enables the menu item, and **false** disables it (grayed out and not tappable).

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectTitleBarMenuItem-isEnabled?: boolean--><!--Device-SelectTitleBarMenuItem-isEnabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

Icon label description, which can serve as the default value of **accessibilityText**. When both **label** and **accessibilityText** are set, **accessibilityText** takes precedence. When not set, there is no label by default.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-SelectTitleBarMenuItem-label?: ResourceStr--><!--Device-SelectTitleBarMenuItem-label?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource, which has higher priority than **value**.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SelectTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier--><!--Device-SelectTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Icon resource used to set the icon of the menu item on the right side of the title bar. It can be referenced through $r. When **symbolStyle** is also set, **symbolStyle** takes precedence.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SelectTitleBarMenuItem-value: ResourceStr--><!--Device-SelectTitleBarMenuItem-value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
