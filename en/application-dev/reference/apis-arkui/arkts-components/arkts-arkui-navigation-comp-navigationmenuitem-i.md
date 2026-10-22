# NavigationMenuItem

```TypeScript
declare interface NavigationMenuItem
```

Defines the navigation menu item, including the menu icon and menu information.

**Since:** 8

<!--Device-unnamed-declare interface NavigationMenuItem--><!--Device-unnamed-declare interface NavigationMenuItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: () => void
```

Callback invoked when the menu item is selected.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigationMenuItem-action?: () => void--><!--Device-NavigationMenuItem-action?: () => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string | Resource
```

Icon path of the menu item.

**NOTE:** 

If the icon is in SVG format, the system sets the fill color by default, which overrides the **fill** attribute defined in the SVG file. As a result, the icon may be displayed abnormally. You are advised to set the **fill** attribute in the SVG file using the **style** attribute to override the default value. The following is an example:

Original code (the **fill** attribute will be overwritten by the default value): `<rect fill="rgb(255,0,0)" .../>`. You are advised to change it to `<rect style="fill: rgb(255,0,0)" .../>`.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigationMenuItem-icon?: string | Resource--><!--Device-NavigationMenuItem-icon?: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

Whether to enable a menu item.

**true** to enable the menu item, **false** otherwise. Default value: **true**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavigationMenuItem-isEnabled?: boolean--><!--Device-NavigationMenuItem-isEnabled?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

Symbol icon for a single option on the menu bar. It has higher priority than **icon**.

**NOTE:** 

The SymbolGlyphModifier object's [fontSize](arkts-arkui-symbolglyph-comp-attribute.md#fontsize) attribute cannot be used to change the icon size, [effectStrategy](arkts-arkui-symbolglyph-comp-attribute.md#effectstrategy) attribute cannot be used to change the animation effect, and [symbolEffect](arkts-arkui-symbolglyph-comp-attribute.md#symboleffect-1) attribute cannot be used to change the animation effect type.

**Type:** [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-NavigationMenuItem-symbolIcon?: SymbolGlyphModifier--><!--Device-NavigationMenuItem-symbolIcon?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string | Resource
```

Text of the menu item. Its visibility varies by the API version.

API version 9: visible.

Since API version 10: invisible.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigationMenuItem-value: string | Resource--><!--Device-NavigationMenuItem-value: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
