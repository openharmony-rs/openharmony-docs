# MenuElement

```TypeScript
declare interface MenuElement
```

Configures icon, text, and interaction information of a menu item.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: () => void
```

Action triggered when a menu item is clicked.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Whether to enable interactions with the menu item.

**true**: yes; **false**: no

Default value: **true**.

**Type:** boolean

**Default:** true

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Menu item icon.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

Icon of a menu item. You can configure the menu item icon using **Modifier**. If both **symbolIcon** and **icon** are configured, the icon is not displayed.

**Type:** [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Menu item text.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
