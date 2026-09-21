# SelectOption

```TypeScript
declare interface SelectOption
```

Provides information about the drop-down menu options.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon of the drop-down menu option.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

Symbol icon of drop-down menu option.

**symbolIcon** takes precedence over **icon**.

**Type:** [SymbolGlyphModifier](arkts-arkui-common-comp-symbolglyphmodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Value of the drop-down menu option.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
