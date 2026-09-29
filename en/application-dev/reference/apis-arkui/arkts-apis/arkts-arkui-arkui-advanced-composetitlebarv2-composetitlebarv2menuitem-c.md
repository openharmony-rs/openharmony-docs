# ComposeTitleBarV2MenuItem

```TypeScript
export declare class ComposeTitleBarV2MenuItem
```

Declaration of the menu item on the right side.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ComposeTitleBarV2MenuItem--><!--Device-unnamed-export declare class ComposeTitleBarV2MenuItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ComposeTitleBarV2, ComposeTitleBarV2MenuItem, ComposeTitleBarV2MenuItemParams } from '@kit.ArkUI';
```

## action

```TypeScript
action?: OnActionCallback
```

Callback function when click on this menu item.

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeTitleBarV2MenuItem-action?: OnActionCallback--><!--Device-ComposeTitleBarV2MenuItem-action?: OnActionCallback-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(params?: ComposeTitleBarV2MenuItemParams)
```

Constructor of ComposeTitleBarV2MenuItem.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeTitleBarV2MenuItem-constructor(params?: ComposeTitleBarV2MenuItemParams)--><!--Device-ComposeTitleBarV2MenuItem-constructor(params?: ComposeTitleBarV2MenuItemParams)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [ComposeTitleBarV2MenuItemParams](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitemparams-i.md) | No | Parameters for creating a menu item instance |

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

The accessibilityDescription of this menu item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeTitleBarV2MenuItem-accessibilityDescription?: ResourceStr--><!--Device-ComposeTitleBarV2MenuItem-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

The accessibilityLevel of this menu item.

**Type:** string

**Default:** auto .The options are as follows:<br>"auto":The value is converted to "yes" or "no" based on the component."yes": the current component is selectable for the accessibility service."no": The current component is not selectable for the accessibility service."no-hide-descendants":The current component and all its child components are not selectable<br> for the accessibility service.

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeTitleBarV2MenuItem-accessibilityLevel?: string--><!--Device-ComposeTitleBarV2MenuItem-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

The accessibilityText of this menu item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeTitleBarV2MenuItem-accessibilityText?: ResourceStr--><!--Device-ComposeTitleBarV2MenuItem-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

Whether to enable this menu item.

**Type:** boolean

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeTitleBarV2MenuItem-isEnabled?: boolean--><!--Device-ComposeTitleBarV2MenuItem-isEnabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

Icon label for this menu item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeTitleBarV2MenuItem-label?: ResourceStr--><!--Device-ComposeTitleBarV2MenuItem-label?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource for this menu item, which has higher priority than value.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeTitleBarV2MenuItem-symbolStyle?: SymbolGlyphModifier--><!--Device-ComposeTitleBarV2MenuItem-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Icon resource for this menu item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ComposeTitleBarV2MenuItem-value: ResourceStr--><!--Device-ComposeTitleBarV2MenuItem-value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
