# EditorMenuOptions

```TypeScript
export interface EditorMenuOptions
```

Describes the edit menu options.

**Since:** 11

<!--Device-unnamed-export interface EditorMenuOptions--><!--Device-unnamed-export interface EditorMenuOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

Event callback for tapping a menu item. When both builder and action are configured, tapping the icon triggers both. When not set, no response occurs on tap.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EditorMenuOptions-action?: () => void--><!--Device-EditorMenuOptions-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: () => void
```

Displays a user-defined component when tapped. The custom component is used with @Builder during construction. When not set, no custom component is displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EditorMenuOptions-builder?: () => void--><!--Device-EditorMenuOptions-builder?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: ResourceStr
```

Icon resource of the edit menu item. If symbolStyle is also set, this attribute does not take effect.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EditorMenuOptions-icon: ResourceStr--><!--Device-EditorMenuOptions-icon: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol icon resource. Pass this parameter when a system Symbol icon (supporting advanced features such as dynamic color and multi-color) is needed. When not passed, the icon resource specified by the icon attribute is used. Has higher priority than icon. When both are set, symbolStyle is used preferentially.

**Type:** [SymbolGlyphModifier](../arkts-components/arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-EditorMenuOptions-symbolStyle?: SymbolGlyphModifier--><!--Device-EditorMenuOptions-symbolStyle?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
