# ToolBarSymbolGlyphOptions

```TypeScript
export interface ToolBarSymbolGlyphOptions
```

Defines the icon symbol options.

**Since:** 13

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ItemState, ToolBar, ToolBarOption, ToolBarOptions, ToolBarModifier } from '@kit.ArkUI';
```

## activated

```TypeScript
activated?: SymbolGlyphModifier
```

Icon symbol of the toolbar item in activated state.

Default value: **fontColor: $r('sys.color.icon_emphasize'), fontSize: 24vp**

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## normal

```TypeScript
normal?: SymbolGlyphModifier
```

Icon symbol of the toolbar item in normal state.

Default value: **fontColor: $r('sys.color.icon_primary'), fontSize: 24vp**

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
