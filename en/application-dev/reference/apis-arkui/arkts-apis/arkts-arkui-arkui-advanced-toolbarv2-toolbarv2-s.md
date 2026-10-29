# ToolBarV2

```TypeScript
export declare struct ToolBarV2
```

The toolbar is used to display action options for the current screen content. It is displayed at the bottom of the screen and is suitable for scenarios where quick action entries need to be provided to users. A maximum of five entries can be displayed at the bottom. Any excess entries are collapsed into a "More" item, which is displayed on the far right. It is suitable for scenarios where quick operations on the current page content are needed, helping users quickly access common functions and improving operation efficiency.<br> ToolbarV2 supports configuring advanced toolbar items via `AdvancedToolbarV2Item` (which extends `ToolBarV2Item`). A toolbar with configured advanced items is more flexible, allowing you to customize titles, overflow menus, item grouping, and more. This component is implemented based on [state management (V2)](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management (V1)](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management (V2) enhances the deep observation and management capabilities of data objects, no longer limited to the component level. With state management (V2), developers can more flexibly control the data and state of the toolbar through this component, achieving more efficient UI refresh. <br>

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If [universal attributes](../arkts-components/arkts-arkui-common-comp.md) and [universal events](../arkts-components/arkts-arkui-common-comp.md) are set for **ToolBarV2**, the compilation toolchain will generate an additional node \_\_Common\_\_ and attach the universal attributes or universal events to \_\_Common\_\_, rather than directly applying them to **ToolBarV2** itself. This may cause the universal attributes or universal events set by the developer to not take effect or behave unexpectedly. Therefore, setting universal attributes and universal events for **ToolBarV2** is not recommended.
> 
> - When the system switches between light and dark modes, the toolbar background color does not automatically follow the switch.

**Since:** 18

**Decorator:** @ComponentV2

<!--Device-unnamed-export declare struct ToolBarV2--><!--Device-unnamed-export declare struct ToolBarV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolbarV2Item, AdvancedToolbarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolbarV2ItemGroupStyle, ToolbarV2ItemGroupStyleOptions, ToolbarV2ItemPlacement, ToolbarV2OverflowMenuStyle, ToolbarV2PaddingOptions, ToolbarV2StyleConfigs, ToolbarV2StyleOptions, ToolbarV2TitleConfigs, ToolbarV2TitleOptions, ToolbarV2TitleStyle, ToolbarV2TitleStyleOptions } from '@kit.ArkUI';
```

## activatedIndex

```TypeScript
activatedIndex?: number
```

Define toolbarV2 activate item index, default is -1. Which is only used for ToolBarV2Item.

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2-activatedIndex?: number--><!--Device-ToolBarV2-activatedIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## advancedToolBarModifier

```TypeScript
advancedToolBarModifier?: AdvancedToolBarV2Modifier
```

Define advanced toolbarV2 modifier. Merges layout attributes, style configs, and overflow menu style into a single modifier.

**Type:** [AdvancedToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-advancedtoolbarv2modifier-c.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ToolBarV2-advancedToolBarModifier?: AdvancedToolBarV2Modifier--><!--Device-ToolBarV2-advancedToolBarModifier?: AdvancedToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dividerModifier

```TypeScript
dividerModifier?: DividerModifier
```

Define toolbarV2 divider Modifier.

**Type:** [DividerModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2-dividerModifier?: DividerModifier--><!--Device-ToolBarV2-dividerModifier?: DividerModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolBarList

```TypeScript
toolBarList: ToolBarV2Item[]
```

Define toolbarV2 item list. Using ToolBarV2Item[] constitutes a simple toolbar. `AdvancedToolbarV2Item` (which extends `ToolBarV2Item`) can be used for advanced layout scenarios such as titles, overflow menus, and item grouping.

**Type:** [ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md)[]

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2-toolBarList: ToolBarV2Item[]--><!--Device-ToolBarV2-toolBarList: ToolBarV2Item[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolBarModifier

```TypeScript
toolBarModifier?: ToolBarV2Modifier
```

Define toolbarV2 modifier.

**Type:** [ToolBarV2Modifier](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2modifier-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2-toolBarModifier?: ToolBarV2Modifier--><!--Device-ToolBarV2-toolBarModifier?: ToolBarV2Modifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
