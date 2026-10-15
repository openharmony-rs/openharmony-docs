# ToolBarOption

```TypeScript
export declare class ToolBarOption
```

Defines the content and attributes of a toolbar.

**Since:** 10

**Decorator:** @Observed

<!--Device-unnamed-export declare class ToolBarOption--><!--Device-unnamed-export declare class ToolBarOption-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ItemState, ToolBar, ToolBarOption, ToolBarOptions, ToolBarModifier } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Tap event of the toolbar item. If not passed in, tapping the item does not trigger any action.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolBarOption-action?: () => void--><!--Device-ToolBarOption-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessibility description of the toolbar item. Used to explain the function and operation consequences of the current component to users in detail, especially when such information cannot be directly obtained from the component text alone. When the component is selected, the content of the text attribute and the accessibility description attribute are announced in sequence.

Default value: "Double-tap with one finger to execute".

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarOption-accessibilityDescription?: ResourceStr--><!--Device-ToolBarOption-accessibilityDescription?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the toolbar item. Used to control whether the current item can be recognized by accessibility services.

Supported values:

**"auto"**: The current component is converted to **"yes"**.

**"yes"**: The current component can be recognized by accessibility services.

**"no"**: The current component cannot be recognized by accessibility services.

**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.

Default value: **"auto"**

**Type:** string

**Default:** "auto"

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarOption-accessibilityLevel?: string--><!--Device-ToolBarOption-accessibilityLevel?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

Accessibility text attribute of the toolbar item. When the component does not contain a text attribute, the screen reader does not announce it when this component is selected. Developers can set accessibility text for components that do not contain text information, so that the screen reader announces the text content when this component is selected.

Default value: the content of the current item's content attribute.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarOption-accessibilityText?: ResourceStr--><!--Device-ToolBarOption-accessibilityText?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activatedIconColor

```TypeScript
activatedIconColor?: ResourceColor
```

Fill color of the toolbar item icon in the activated state.

Default value: **$r('sys.color.icon_emphasize')**.

When the **toolBarSymbolOptions** attribute is set, this parameter does not take effect.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBarOption-activatedIconColor?: ResourceColor--><!--Device-ToolBarOption-activatedIconColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activatedTextColor

```TypeScript
activatedTextColor?: ResourceColor
```

Font color of the toolbar item in the activated state.

Default value: **$r('sys.color.font_emphasize')**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBarOption-activatedTextColor?: ResourceColor--><!--Device-ToolBarOption-activatedTextColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ResourceStr
```

Text of the toolbar item.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolBarOption-content: ResourceStr--><!--Device-ToolBarOption-content: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: Resource
```

Icon of the toolbar item.

By default, if not set or set to **undefined**, the icon is not displayed.

When the **toolBarSymbolOptions** attribute is set, the icon attribute does not take effect.

**Type:** [Resource](arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolBarOption-icon?: Resource--><!--Device-ToolBarOption-icon?: Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconColor

```TypeScript
iconColor?: ResourceColor
```

Fill color of the toolbar item icon.

Default value: $r('sys.color.icon_primary').

When the toolBarSymbolOptions attribute is set, this parameter does not take effect.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBarOption-iconColor?: ResourceColor--><!--Device-ToolBarOption-iconColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: ItemState
```

State of the toolbar item.

Default value: **ItemState.ENABLE**

**Type:** [ItemState](arkts-arkui-arkui-advanced-toolbar-itemstate-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolBarOption-state?: ItemState--><!--Device-ToolBarOption-state?: ItemState-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textColor

```TypeScript
textColor?: ResourceColor
```

Font color of the toolbar item.

Default value: **$r('sys.color.font_primary')**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBarOption-textColor?: ResourceColor--><!--Device-ToolBarOption-textColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolBarSymbolOptions

```TypeScript
toolBarSymbolOptions?: ToolBarSymbolGlyphOptions
```

Icon attribute of the toolbar item, of the symbol type. After this parameter is set, the **icon** attribute does not take effect.

**Type:** [ToolBarSymbolGlyphOptions](arkts-arkui-arkui-advanced-toolbar-toolbarsymbolglyphoptions-i.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-ToolBarOption-toolBarSymbolOptions?: ToolBarSymbolGlyphOptions--><!--Device-ToolBarOption-toolBarSymbolOptions?: ToolBarSymbolGlyphOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
