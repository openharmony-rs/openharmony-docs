# OperateIconV2

```TypeScript
export declare class OperateIconV2
```

Defines the type of the right icon element of the list item.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class OperateIconV2--><!--Device-unnamed-export declare class OperateIconV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeListItemV2, ContentItemV2, ContentItemV2Options, IconTypeV2, OperateButtonV2, OperateButtonV2Options, OperateCheckV2, OperateCheckV2Options, OperateIconV2, OperateIconV2Options, OperateItemV2, OperateItemV2Options } from '@kit.ArkUI';
```

## action

```TypeScript
public action?: OnActionCallback
```

Callback invoked when the icon or arrow of the right element of the list item is tapped.

If this parameter is not set or is set to **undefined**, tapping the icon or arrow does not trigger the callback.

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2-public action?: OnActionCallback--><!--Device-OperateIconV2-public action?: OnActionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: OperateIconV2Options)
```

A constructor used to create an **OperateIconV2** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2-constructor(options?: OperateIconV2Options)--><!--Device-OperateIconV2-constructor(options?: OperateIconV2Options)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [OperateIconV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateiconv2options-i.md) | No | Configuration of the right icon of the list item.<br>If this parameter is not set or is set to **undefined**, an object is created based on the default effect of each attribute. |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

Accessibility description of the icon or arrow. This description is used to explain the current component to users in detail. You should provide a relatively detailed text description for this attribute to help users understand the action to be performed and its possible consequences, especially when such consequences cannot be directly inferred from the component's attributes and accessibility text. If a component that is selected has both a text attribute and an accessibility description attribute, the system first announces the text attribute and then the content of the accessibility description attribute.

Default value: **"Double-tap with one finger to execute."**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2-public accessibilityDescription?: ResourceStr--><!--Device-OperateIconV2-public accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
```

Accessibility level of the icon or arrow of the right element of the list item. This attribute controls whether the current item can be recognized by accessibility services.

Supported values:

**"auto"**: Whether the current component can be recognized by accessibility services is determined by the accessibility service and ArkUI together.

**"yes"**: The current component can be recognized by accessibility services.

**"no"**: The current component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**

**Type:** string

**Default:** auto

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2-public accessibilityLevel?: string--><!--Device-OperateIconV2-public accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
public accessibilityText?: ResourceStr
```

Accessibility text of the icon or arrow. When a component does not contain a text attribute, the screen reader does not announce it upon selection, leaving users unaware of which component is currently selected. To address this issue, you can set accessibility text for components that do not contain text information. When the screen reader selects such a component, it announces the content of the accessibility text, helping users clearly identify the selected component.

Default value: **""**

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2-public accessibilityText?: ResourceStr--><!--Device-OperateIconV2-public accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
public symbolStyle?: SymbolGlyphModifier
```

Symbol icon or arrow resource, which takes precedence over **value**.

By default, this attribute is not set or is set to **undefined**, and the symbol icon is not displayed.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2-public symbolStyle?: SymbolGlyphModifier--><!--Device-OperateIconV2-public symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
public value: ResourceStr
```

Icon or arrow resource of the right element of the list item.

If **symbolStyle** is also set, only the Symbol icon is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-OperateIconV2-public value: ResourceStr--><!--Device-OperateIconV2-public value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
