# ToolBarV2SymbolGlyph

```TypeScript
export class ToolBarV2SymbolGlyph
```

ToolBarV2SymbolGlyph定义Symbol图标的属性。

**Since:** 18

**Decorator:** @ObservedV2

<!--Device-unnamed-export class ToolBarV2SymbolGlyph--><!--Device-unnamed-export class ToolBarV2SymbolGlyph-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options: ToolBarV2SymbolGlyphOptions)
```

ToolBarV2SymbolGlyph的构造函数。

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2SymbolGlyph-constructor(options: ToolBarV2SymbolGlyphOptions)--><!--Device-ToolBarV2SymbolGlyph-constructor(options: ToolBarV2SymbolGlyphOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ToolBarV2SymbolGlyphOptions](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2symbolglyphoptions-i.md) | Yes | symbol info. |

## activated

```TypeScript
activated?: SymbolGlyphModifier
```

工具栏symbol图标激活态样式。

默认值：fontColor：$r('sys.color.icon_emphasize')，fontSize：24vp。

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2SymbolGlyph-activated?: SymbolGlyphModifier--><!--Device-ToolBarV2SymbolGlyph-activated?: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## normal

```TypeScript
normal: SymbolGlyphModifier
```

工具栏symbol图标普通态样式。

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 18

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ToolBarV2SymbolGlyph-normal: SymbolGlyphModifier--><!--Device-ToolBarV2SymbolGlyph-normal: SymbolGlyphModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
