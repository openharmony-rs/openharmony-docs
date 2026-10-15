# EditableTitleBarMenuItem

```TypeScript
export declare class EditableTitleBarMenuItem
```

Declaration of the menu item on the right side.

**Since:** 10

<!--Device-unnamed-export declare class EditableTitleBarMenuItem--><!--Device-unnamed-export declare class EditableTitleBarMenuItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconType, EditableTitleBar, EditableTitleBarMenuItem, EditableTitleBarItem, EditableTitleBarOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Tap event for the custom button on the right side of the title bar. When this parameter is not set, tapping the button has no response.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EditableTitleBarMenuItem-action?: () => void--><!--Device-EditableTitleBarMenuItem-action?: () => void-End-->

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

<!--Device-EditableTitleBarMenuItem-accessibilityDescription?: ResourceStr--><!--Device-EditableTitleBarMenuItem-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level. It determines whether the component can be recognized by accessibility services.

The options are as follows:

**"auto"**: This option is treated as "yes" by the system for this component.

**"yes"**: The component can be recognized by accessibility services.

**"no"**: The component cannot be recognized by accessibility services.

**"no-hide-descendants"**: Neither the component nor its child components can be recognized by accessibility services.

Default value: **"auto"**

**Type:** string

**Default:** "auto"

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-EditableTitleBarMenuItem-accessibilityLevel?: string--><!--Device-EditableTitleBarMenuItem-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text attribute for the custom button on the right side of the title bar. When a component does not contain a text attribute, the screen reader does not announce anything when this component is selected, and the user cannot clearly know which component is currently selected. To address this scenario, developers can set accessibility text for components that do not contain text information. When the screen reader selects this component, it announces the accessibility text, helping screen reader users clearly know which component they have selected.

Default value: **" "** when the label attribute is not set; the content of the label attribute when the label attribute is set.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-EditableTitleBarMenuItem-accessibilityText?: ResourceStr--><!--Device-EditableTitleBarMenuItem-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether to set as the default focus.

**true**: The item gains focus.

**false**: The item does not gain focus.

Default value: **false**

When using the **defaultFocus** attribute, set the **isEnabled** attribute to **true** beforehand; otherwise, the **defaultFocus** setting does not take effect.

**Note:** If multiple operable areas are set as the default focus at the same time, the first operable area in the display order among those set as the default focus becomes the default focus.

**Type:** boolean

**Default:** { false }

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-EditableTitleBarMenuItem-defaultFocus?: boolean--><!--Device-EditableTitleBarMenuItem-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

Whether to enable.

Default value: **true**, meaning enabled by default.

When **isEnabled** is **true**, the item is enabled.

When **isEnabled** is **false**, the item is disabled.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EditableTitleBarMenuItem-isEnabled?: boolean--><!--Device-EditableTitleBarMenuItem-isEnabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

Icon label description. When this parameter is not set, no icon label is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EditableTitleBarMenuItem-label?: ResourceStr--><!--Device-EditableTitleBarMenuItem-label?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource, which takes precedence over value. When this parameter is not set, the value parameter is used to display the icon.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-EditableTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier--><!--Device-EditableTitleBarMenuItem-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Icon resource.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EditableTitleBarMenuItem-value: ResourceStr--><!--Device-EditableTitleBarMenuItem-value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
