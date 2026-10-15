# TabTitleBarMenuItem

```TypeScript
export declare class TabTitleBarMenuItem
```

Declaration of the menu item on the right side.

**Since:** 10

<!--Device-unnamed-export declare class TabTitleBarMenuItem--><!--Device-unnamed-export declare class TabTitleBarMenuItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { TabTitleBar, TabTitleBarMenuItem, TabTitleBarTabItem } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Action closure triggered when the menu item is tapped. If not set, tapping the menu item has no response.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabTitleBarMenuItem-action?: () => void--><!--Device-TabTitleBarMenuItem-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the custom button on the right side of the title bar. This description is used to explain the current component to users in detail. You should provide a relatively detailed text description for this attribute to help users understand the action to be performed and its possible consequences, especially when such consequences cannot be directly inferred from the component's attributes and accessibility text. If a component that is selected has both a text attribute and an accessibility description attribute, the system first announces the text attribute and then the content of the accessibility description attribute.

Default value: **"Double-tap with one finger to execute."**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabTitleBarMenuItem-accessibilityDescription?: ResourceStr--><!--Device-TabTitleBarMenuItem-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the custom button on the right side of the title bar. It controls whether the current item can be recognized by accessibility services.

Supported values:

**"auto"**: Automatically determined based on whether the component is interactive. If the component is interactive, it is equivalent to **"yes"**; otherwise, it is equivalent to **"no"**.

**"yes"**: The current component can be recognized by accessibility services.

**"no"**: The current component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**

**Type:** string

**Default:** "auto"

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabTitleBarMenuItem-accessibilityLevel?: string--><!--Device-TabTitleBarMenuItem-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text attribute of the custom button on the right side of the title bar. It provides spoken text for components that do not contain text information.

Default value: If the **label** attribute is set, the default value is the content of the label attribute; otherwise, the default value is a space character.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabTitleBarMenuItem-accessibilityText?: ResourceStr--><!--Device-TabTitleBarMenuItem-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

Whether to enable. The value **true** means enabled, and **false** means disabled. When disabled, the menu item does not respond to tap events, and the action is not triggered.

Default value: **false**

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabTitleBarMenuItem-isEnabled?: boolean--><!--Device-TabTitleBarMenuItem-isEnabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

Icon label, which provides a text description for the menu item icon.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-TabTitleBarMenuItem-label?: ResourceStr--><!--Device-TabTitleBarMenuItem-label?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource, which takes precedence over **value**. Pass this parameter when a symbol icon is needed. If not passed, the icon set by value is used.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier--><!--Device-TabTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Icon resource. If **symbolStyle** is set, this attribute does not take effect.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabTitleBarMenuItem-value: ResourceStr--><!--Device-TabTitleBarMenuItem-value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
