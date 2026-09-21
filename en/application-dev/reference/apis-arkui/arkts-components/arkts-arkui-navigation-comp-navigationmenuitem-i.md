# NavigationMenuItem

```TypeScript
declare interface NavigationMenuItem
```

Defines the navigation menu item, including the menu icon and menu information.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: () => void
```

Callback invoked when the menu item is selected.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string | Resource
```

Icon path of the menu item.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

Enabled status. **true** (default): enabled. **false**: disabled.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

Symbol icon for a single option on the menu bar. It has higher priority than **icon**.

**Type:** [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
