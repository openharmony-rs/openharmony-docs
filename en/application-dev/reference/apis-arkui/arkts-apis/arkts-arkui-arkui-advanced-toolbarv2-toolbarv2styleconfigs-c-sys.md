# ToolBarV2StyleConfigs (System API)

```TypeScript
export declare class ToolBarV2StyleConfigs
```

定义工具栏的样式配置。

**Since:** 26.1.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class ToolBarV2StyleConfigs--><!--Device-unnamed-export declare class ToolBarV2StyleConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ToolBarV2ItemState, ToolBarV2SymbolGlyph, ToolBarV2SymbolGlyphOptions, ToolBarV2ItemText, ToolBarV2ItemTextOptions, ToolBarV2ItemIconType, ToolBarV2ItemImage, ToolBarV2ItemImageOptions, ToolBarV2, ToolBarV2Item, ToolBarV2ItemOptions, ToolBarV2Modifier, ToolBarV2ItemAction, AdvancedToolBarV2Item, AdvancedToolBarV2ItemOptions, AdvancedToolBarV2Modifier, BarBackgroundVisibility, ToolBarV2ItemGroupStyle, ToolBarV2ItemGroupStyleOptions, ToolBarV2ItemPlacement, ToolBarV2OverflowMenuStyle, ToolBarV2PaddingOptions, ToolBarV2StyleConfigs, ToolBarV2StyleOptions, ToolBarV2TitleConfigs, ToolBarV2TitleOptions, ToolBarV2TitleStyle, ToolBarV2TitleStyleOptions, ToolBarV2MaterialStyle } from '@kit.ArkUI';
```

## systemBackgroundMaterial

```TypeScript
systemBackgroundMaterial?: uiMaterial.Material
```

工具栏的系统材质效果。默认值：undefined。不设置时，不系统材质。

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

<!--Device-ToolBarV2StyleConfigs-systemBackgroundMaterial?: uiMaterial.Material--><!--Device-ToolBarV2StyleConfigs-systemBackgroundMaterial?: uiMaterial.Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## systemMaterialStyle

```TypeScript
systemMaterialStyle?: ToolBarV2MaterialStyle
```

工具栏的简化材质样式。如果两者systemBackgroundMaterial和systemMaterialStyle都设置了，systemBackgroundMaterial优先生效。默认值：undefined。不设置时，默认为ToolBarV2MaterialStyle.NONE效果。

**Type:** [ToolBarV2MaterialStyle](arkts-arkui-arkui-advanced-toolbarv2-toolbarv2materialstyle-e-sys.md)

**Since:** 26.1.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

<!--Device-ToolBarV2StyleConfigs-systemMaterialStyle?: ToolBarV2MaterialStyle--><!--Device-ToolBarV2StyleConfigs-systemMaterialStyle?: ToolBarV2MaterialStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
