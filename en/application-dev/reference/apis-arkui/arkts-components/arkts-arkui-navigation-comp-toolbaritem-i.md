# ToolbarItem

```TypeScript
declare interface ToolbarItem
```

Provides customizable parameters of the toolbar.

**Since:** 10

<!--Device-unnamed-declare interface ToolbarItem--><!--Device-unnamed-declare interface ToolbarItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: () => void
```

Callback invoked when the menu item is selected.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolbarItem-action?: () => void--><!--Device-ToolbarItem-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activeIcon

```TypeScript
activeIcon?: ResourceStr
```

Icon path of the toolbar item in the active state.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolbarItem-activeIcon?: ResourceStr--><!--Device-ToolbarItem-activeIcon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activeSymbolIcon

```TypeScript
activeSymbolIcon?: SymbolGlyphModifier
```

Symbol icon for a single option on the menu bar when it is in active state. It has higher priority than **activeIcon**.

**NOTE:** 

The SymbolGlyphModifier object's [fontSize](arkts-arkui-symbolglyph-comp-attribute.md#fontsize) attribute cannot be used to change the icon size, [effectStrategy](arkts-arkui-symbolglyph-comp-attribute.md#effectstrategy) attribute cannot be used to change the animation effect, and [symbolEffect](arkts-arkui-symbolglyph-comp-attribute.md#symboleffect1) attribute cannot be used to change the animation effect type.

**Type:** [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ToolbarItem-activeSymbolIcon?: SymbolGlyphModifier--><!--Device-ToolbarItem-activeSymbolIcon?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon path of the toolbar item.

**NOTE:** 

If the icon is in SVG format, the system sets the fill color by default, which overrides the **fill** attribute defined in the SVG file. As a result, the icon may be displayed abnormally. You are advised to set the **fill** attribute in the SVG file using the **style** attribute to override the default value. The following is an example:

Original code (the **fill** attribute will be overwritten by the default value): `<rect fill="rgb(255,0,0)" .../>`. You are advised to change it to `<rect style="fill: rgb(255,0,0)" .../>`.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolbarItem-icon?: ResourceStr--><!--Device-ToolbarItem-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status?: ToolbarItemStatus
```

Status of a toolbar item.

Default value: **ToolbarItemStatus.NORMAL**

**Type:** [ToolbarItemStatus](arkts-arkui-navigation-comp-toolbaritemstatus-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolbarItem-status?: ToolbarItemStatus--><!--Device-ToolbarItem-status?: ToolbarItemStatus-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

Symbol icon for a single option on the toolbar. It has higher priority than **icon**.

**NOTE:** 

The SymbolGlyphModifier object's [fontSize](arkts-arkui-symbolglyph-comp-attribute.md#fontsize) attribute cannot be used to change the icon size, [effectStrategy](arkts-arkui-symbolglyph-comp-attribute.md#effectstrategy) attribute cannot be used to change the animation effect, and [symbolEffect](arkts-arkui-symbolglyph-comp-attribute.md#symboleffect1) attribute cannot be used to change the animation effect type.

**Type:** [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ToolbarItem-symbolIcon?: SymbolGlyphModifier--><!--Device-ToolbarItem-symbolIcon?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Text of the toolbar item.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ToolbarItem-value: ResourceStr--><!--Device-ToolbarItem-value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
