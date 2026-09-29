# OperateIconV2Options

```TypeScript
export interface OperateIconV2Options
```

Defines options for the **OperateIconV2** constructor.

**Since:** 26.0.0

<!--Device-unnamed-export interface OperateIconV2Options--><!--Device-unnamed-export interface OperateIconV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## action

```TypeScript
action?: OnActionCallback
```

Callback invoked when the icon or arrow of the right element of the list item is tapped.

By default, or when it is set to **undefined**, tapping the icon or arrow does not trigger the callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2Options-action?: OnActionCallback--><!--Device-OperateIconV2Options-action?: OnActionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the icon or arrow. This description is used to explain the current component to users in detail. You should provide a relatively detailed text description for this attribute to help users understand the action to be performed and its possible consequences, especially when such consequences cannot be directly inferred from the component's attributes and accessibility text. If a component that is selected has both a text attribute and an accessibility description attribute, the system first announces the text attribute and then the content of the accessibility description attribute. Default value: **"Double-tap with one finger to execute."**.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2Options-accessibilityDescription?: ResourceStr--><!--Device-OperateIconV2Options-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the icon or arrow of the right element of the list item. This attribute controls whether the current item can be recognized by accessibility services. Supported values: **"auto"**: Whether the current component can be recognized by accessibility services is determined by the accessibility service and ArkUI. **"yes"**: The current component can be recognized by accessibility services. **"no"**: The current component cannot be recognized by accessibility services. **"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services. Default value: **"auto"**.

**Type:** string

**Default:** auto

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2Options-accessibilityLevel?: string--><!--Device-OperateIconV2Options-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text of the icon or arrow. When a component does not contain a text attribute, the screen reader does not announce it upon selection, leaving users unaware of which component is currently selected. To address this scenario, developers can set accessibility text for components that do not contain text information. When the screen reader selects such a component, it announces the content of the accessibility text, helping screen reader users clearly identify the selected component. Default value: **""**.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2Options-accessibilityText?: ResourceStr--><!--Device-OperateIconV2Options-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon or arrow resource of the right element of the list item. It has a higher priority than **value**. When both are set, only the Symbol icon is displayed.

By default, or when it is set to **undefined**, no Symbol icon is displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2Options-symbolStyle?: SymbolGlyphModifier--><!--Device-OperateIconV2Options-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

Icon or arrow resource of the right element of the list item.

Default value: **""**, which means no icon or arrow resource is displayed.

When **symbolStyle** is also set, only the Symbol icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2Options-value?: ResourceStr--><!--Device-OperateIconV2Options-value?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
