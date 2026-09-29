# MenuItemOptions

```TypeScript
declare interface MenuItemOptions
```

Provides information about the menu item.

**Since:** 9

<!--Device-unnamed-declare interface MenuItemOptions--><!--Device-unnamed-declare interface MenuItemOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

Builder for a level-2 menu. By default, no secondary menu is displayed.

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemOptions-builder?: CustomBuilder--><!--Device-MenuItemOptions-builder?: CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

Content of the menu item. The default value is an empty string.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemOptions-content?: ResourceStr--><!--Device-MenuItemOptions-content?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endIcon

```TypeScript
endIcon?: ResourceStr
```

End icon of the menu item. Symbol icons are not supported. If the symbol icon is used, **symbolEndIcon** must be used. By default, no end icon is displayed.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemOptions-endIcon?: ResourceStr--><!--Device-MenuItemOptions-endIcon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## labelInfo

```TypeScript
labelInfo?: ResourceStr
```

Label information at the end of the menu item, such as shortcut keys like Ctrl+C. By default, no label information is displayed.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemOptions-labelInfo?: ResourceStr--><!--Device-MenuItemOptions-labelInfo?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startIcon

```TypeScript
startIcon?: ResourceStr
```

Start icon of the menu item. Symbol icons are not supported. If a symbol icon is used, **symbolStartIcon** must be used. By default, no start icon is displayed.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-MenuItemOptions-startIcon?: ResourceStr--><!--Device-MenuItemOptions-startIcon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolEndIcon

```TypeScript
symbolEndIcon?: SymbolGlyphModifier
```

Symbol icon at the end of the menu item. When this parameter is set, the icon set through **endIcon** is not displayed. By default, no symbol icon is displayed at the end of the menu item.

**Type:** [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MenuItemOptions-symbolEndIcon?: SymbolGlyphModifier--><!--Device-MenuItemOptions-symbolEndIcon?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolStartIcon

```TypeScript
symbolStartIcon?: SymbolGlyphModifier
```

Symbol icon at the start of the menu item. When this parameter is set, the icon set through **startIcon** is not displayed. By default, no symbol icon is displayed at the start of the menu item.

**Type:** [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MenuItemOptions-symbolStartIcon?: SymbolGlyphModifier--><!--Device-MenuItemOptions-symbolStartIcon?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
