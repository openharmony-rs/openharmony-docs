# ToolBarV2

Declare Component ToolBarV2

**Since:** 18

**Decorator:** @ComponentV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction } from '@kit.ArkUI';
```

## activatedIndex

```TypeScript
activatedIndex?: number
```

Define toolbarV2 activate item index, default is -1.

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dividerModifier

```TypeScript
dividerModifier?: DividerModifier
```

Define divider Modifier.

**Type:** [DividerModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## toolBarList

```TypeScript
toolBarList: ToolBarV2Item[]
```

Define toolbarV2 item list.

**Type:** [ToolBarV2Item](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2item-c.md)[]

**Since:** 18

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
