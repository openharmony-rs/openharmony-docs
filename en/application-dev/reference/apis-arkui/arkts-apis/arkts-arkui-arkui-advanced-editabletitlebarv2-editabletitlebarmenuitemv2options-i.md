# EditableTitleBarMenuItemV2Options

```TypeScript
export declare interface EditableTitleBarMenuItemV2Options
```

Defines the menu item configuration options.

**Since:** 26.0.0

<!--Device-unnamed-export declare interface EditableTitleBarMenuItemV2Options--><!--Device-unnamed-export declare interface EditableTitleBarMenuItemV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## action

```TypeScript
action?: OnActionCallback
```

Callback invoked when the menu item is tapped.

Default value: **undefined**, which means no response when tapped.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2Options-action?: OnActionCallback--><!--Device-EditableTitleBarMenuItemV2Options-action?: OnActionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description, which explains in detail the operation of the current component and its possible consequences to the user. If the component has both a text attribute and an accessibility description attribute, the system announces the text attribute first and then the accessibility description attribute when the component is selected.

Default value: **"Single-tap with one finger to execute."**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2Options-accessibilityDescription?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2Options-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level, which controls whether the current item can be recognized by the accessibility service.

Supported values:

**"auto"**: The current component is converted to **"yes"** or **"no"** depending on the situation.

**"yes"**: The current component can be recognized by the accessibility service.

**"no"**: The current component cannot be recognized by the accessibility service.

**"no-hide-descendants"**: The current component and all its child components cannot be recognized by the accessibility service.

If a value outside the preceding range is passed in, it is processed as **"auto"**.

Default value: **"auto"**

**Type:** string

**Default:** 'auto'

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2Options-accessibilityLevel?: string--><!--Device-EditableTitleBarMenuItemV2Options-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text for the screen reader. When the component does not contain a text attribute, setting this attribute enables the screen reader to announce the accessibility text when the component is selected.

Default value: If **label** is set, the default value is the content of the label attribute of the current item; otherwise, the default value is **" "**.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2Options-accessibilityText?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2Options-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultFocus

```TypeScript
defaultFocus?: boolean
```

Whether to obtain focus by default.

**true**: The component obtains focus.

**false**: The component does not obtain focus.

Default value: **false**.

When using the **defaultFocus** attribute, set the **isEnabled** attribute to **true** in advance; otherwise, the **defaultFocus** value is recognized as **false**. If multiple operable areas in the title bar are set as the default focus, the first one in display order among the operable areas set as the default focus is the default focus.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2Options-defaultFocus?: boolean--><!--Device-EditableTitleBarMenuItemV2Options-defaultFocus?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

Whether to enable an item.

Default value: **true**, meaning to enable.

When **isEnabled** is **false**, the item is disabled.

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2Options-isEnabled?: boolean--><!--Device-EditableTitleBarMenuItemV2Options-isEnabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

Label text of the long-press dialog box.

Default value: **undefined**, which means no label is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2Options-label?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2Options-label?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Modifier for the Symbol icon style. Pass this parameter when a Symbol icon is used and its style needs to be customized. It takes precedence over value.

Default value: **undefined**, which means no Symbol icon style modifier is set.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2Options-symbolStyle?: SymbolGlyphModifier--><!--Device-EditableTitleBarMenuItemV2Options-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

Icon resource, which supports Symbol or Image. When both value and **symbolStyle** are set, **symbolStyle** takes effect and value does not.

Default value: **''**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarMenuItemV2Options-value?: ResourceStr--><!--Device-EditableTitleBarMenuItemV2Options-value?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
