| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API卡片权限变更|类名：RichEditorAttribute；<br>API声明：copyOptions(value: CopyOptions): RichEditorAttribute;<br>差异内容：form|类名：RichEditorAttribute；<br>API声明：copyOptions(value: CopyOptions): RichEditorAttribute;<br>差异内容：NA|component/rich_editor.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface DragItemInfo<br>差异内容：NA|类名：global；<br>API声明：declare interface DragItemInfo<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragItemInfo；<br>API声明：pixelMap?: PixelMap;<br>差异内容：NA|类名：DragItemInfo；<br>API声明：pixelMap?: PixelMap;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragItemInfo；<br>API声明：builder?: CustomBuilder;<br>差异内容：NA|类名：DragItemInfo；<br>API声明：builder?: CustomBuilder;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragItemInfo；<br>API声明：extraInfo?: string;<br>差异内容：NA|类名：DragItemInfo；<br>API声明：extraInfo?: string;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum DragResult<br>差异内容：NA|类名：global；<br>API声明：declare enum DragResult<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragResult；<br>API声明：DRAG_SUCCESSFUL = 0<br>差异内容：NA|类名：DragResult；<br>API声明：DRAG_SUCCESSFUL = 0<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragResult；<br>API声明：DRAG_FAILED = 1<br>差异内容：NA|类名：DragResult；<br>API声明：DRAG_FAILED = 1<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface DragEvent<br>差异内容：NA|类名：global；<br>API声明：declare interface DragEvent<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragEvent；<br>API声明：getDisplayX(): number;<br>差异内容：NA|类名：DragEvent；<br>API声明：getDisplayX(): number;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragEvent；<br>API声明：getDisplayY(): number;<br>差异内容：NA|类名：DragEvent；<br>API声明：getDisplayY(): number;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragEvent；<br>API声明：getWindowX(): number;<br>差异内容：NA|类名：DragEvent；<br>API声明：getWindowX(): number;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragEvent；<br>API声明：getWindowY(): number;<br>差异内容：NA|类名：DragEvent；<br>API声明：getWindowY(): number;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragEvent；<br>API声明：setResult(dragResult: DragResult): void;<br>差异内容：NA|类名：DragEvent；<br>API声明：setResult(dragResult: DragResult): void;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragEvent；<br>API声明：getResult(): DragResult;<br>差异内容：NA|类名：DragEvent；<br>API声明：getResult(): DragResult;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：DragEvent；<br>API声明：getPreviewRect(): Rectangle;<br>差异内容：NA|类名：DragEvent；<br>API声明：getPreviewRect(): Rectangle;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：CommonMethod；<br>API声明：onDragStart(event: (event: DragEvent, extraParams?: string) => CustomBuilder \| DragItemInfo): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：onDragStart(event: (event: DragEvent, extraParams?: string) => CustomBuilder \| DragItemInfo): T;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：CommonMethod；<br>API声明：onDragEnter(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：onDragEnter(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：CommonMethod；<br>API声明：onDragMove(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：onDragMove(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：CommonMethod；<br>API声明：onDragLeave(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：onDragLeave(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：CommonMethod；<br>API声明：onDrop(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：onDrop(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：CommonMethod；<br>API声明：onDragEnd(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：onDragEnd(event: (event: DragEvent, extraParams?: string) => void): T;<br>差异内容：crossplatform|component/common.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export interface ChipSymbolGlyphOptions<br>差异内容：crossplatform|类名：global；<br>API声明：export interface ChipSymbolGlyphOptions<br>差异内容：NA|api/@ohos.arkui.advanced.Chip.d.ets|
|API跨平台权限变更|类名：ChipSymbolGlyphOptions；<br>API声明：normal?: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：ChipSymbolGlyphOptions；<br>API声明：normal?: SymbolGlyphModifier;<br>差异内容：NA|api/@ohos.arkui.advanced.Chip.d.ets|
|API跨平台权限变更|类名：ChipSymbolGlyphOptions；<br>API声明：activated?: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：ChipSymbolGlyphOptions；<br>API声明：activated?: SymbolGlyphModifier;<br>差异内容：NA|api/@ohos.arkui.advanced.Chip.d.ets|
|API跨平台权限变更|类名：ChipOptions；<br>API声明：prefixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：crossplatform|类名：ChipOptions；<br>API声明：prefixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：NA|api/@ohos.arkui.advanced.Chip.d.ets|
|API跨平台权限变更|类名：ChipOptions；<br>API声明：suffixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：crossplatform|类名：ChipOptions；<br>API声明：suffixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：NA|api/@ohos.arkui.advanced.Chip.d.ets|
|API跨平台权限变更|类名：ChipGroupItemOptions；<br>API声明：prefixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：crossplatform|类名：ChipGroupItemOptions；<br>API声明：prefixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：NA|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|API跨平台权限变更|类名：ChipGroupItemOptions；<br>API声明：suffixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：crossplatform|类名：ChipGroupItemOptions；<br>API声明：suffixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：NA|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|API跨平台权限变更|类名：SymbolGlyphModifier；<br>API声明：applyNormalAttribute?(instance: SymbolGlyphAttribute): void;<br>差异内容：crossplatform|类名：SymbolGlyphModifier；<br>API声明：applyNormalAttribute?(instance: SymbolGlyphAttribute): void;<br>差异内容：NA|api/arkui/SymbolGlyphModifier.d.ts|
|API跨平台权限变更|类名：SymbolSpanModifier；<br>API声明：applyNormalAttribute?(attribute: SymbolSpanAttribute): void;<br>差异内容：crossplatform|类名：SymbolSpanModifier；<br>API声明：applyNormalAttribute?(attribute: SymbolSpanAttribute): void;<br>差异内容：NA|api/arkui/SymbolSpanModifier.d.ts|
|API跨平台权限变更|类名：MenuElement；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：MenuElement；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：NA|component/common.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare type SymbolGlyphModifier = import('../api/arkui/SymbolGlyphModifier').SymbolGlyphModifier;<br>差异内容：crossplatform|类名：global；<br>API声明：declare type SymbolGlyphModifier = import('../api/arkui/SymbolGlyphModifier').SymbolGlyphModifier;<br>差异内容：NA|component/common.d.ts|
|API跨平台权限变更|类名：MenuItemOptions；<br>API声明：symbolStartIcon?: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：MenuItemOptions；<br>API声明：symbolStartIcon?: SymbolGlyphModifier;<br>差异内容：NA|component/menu_item.d.ts|
|API跨平台权限变更|类名：MenuItemOptions；<br>API声明：symbolEndIcon?: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：MenuItemOptions；<br>API声明：symbolEndIcon?: SymbolGlyphModifier;<br>差异内容：NA|component/menu_item.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：interface CancelButtonSymbolOptions<br>差异内容：crossplatform|类名：global；<br>API声明：interface CancelButtonSymbolOptions<br>差异内容：NA|component/search.d.ts|
|API跨平台权限变更|类名：CancelButtonSymbolOptions；<br>API声明：style?: CancelButtonStyle;<br>差异内容：crossplatform|类名：CancelButtonSymbolOptions；<br>API声明：style?: CancelButtonStyle;<br>差异内容：NA|component/search.d.ts|
|API跨平台权限变更|类名：CancelButtonSymbolOptions；<br>API声明：icon?: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：CancelButtonSymbolOptions；<br>API声明：icon?: SymbolGlyphModifier;<br>差异内容：NA|component/search.d.ts|
|API跨平台权限变更|类名：SelectOption；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：SelectOption；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：NA|component/select.d.ts|
|API跨平台权限变更|类名：MenuItemConfiguration；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：MenuItemConfiguration；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：NA|component/select.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：interface SymbolGlyphInterface<br>差异内容：crossplatform|类名：global；<br>API声明：interface SymbolGlyphInterface<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum SymbolRenderingStrategy<br>差异内容：crossplatform|类名：global；<br>API声明：declare enum SymbolRenderingStrategy<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolRenderingStrategy；<br>API声明：SINGLE = 0<br>差异内容：crossplatform|类名：SymbolRenderingStrategy；<br>API声明：SINGLE = 0<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_COLOR = 1<br>差异内容：crossplatform|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_COLOR = 1<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_OPACITY = 2<br>差异内容：crossplatform|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_OPACITY = 2<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum SymbolEffectStrategy<br>差异内容：crossplatform|类名：global；<br>API声明：declare enum SymbolEffectStrategy<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolEffectStrategy；<br>API声明：NONE = 0<br>差异内容：crossplatform|类名：SymbolEffectStrategy；<br>API声明：NONE = 0<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolEffectStrategy；<br>API声明：SCALE = 1<br>差异内容：crossplatform|类名：SymbolEffectStrategy；<br>API声明：SCALE = 1<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolEffectStrategy；<br>API声明：HIERARCHICAL = 2<br>差异内容：crossplatform|类名：SymbolEffectStrategy；<br>API声明：HIERARCHICAL = 2<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum EffectDirection<br>差异内容：crossplatform|类名：global；<br>API声明：declare enum EffectDirection<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：EffectDirection；<br>API声明：DOWN = 0<br>差异内容：crossplatform|类名：EffectDirection；<br>API声明：DOWN = 0<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：EffectDirection；<br>API声明：UP = 1<br>差异内容：crossplatform|类名：EffectDirection；<br>API声明：UP = 1<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum EffectScope<br>差异内容：crossplatform|类名：global；<br>API声明：declare enum EffectScope<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：EffectScope；<br>API声明：LAYER = 0<br>差异内容：crossplatform|类名：EffectScope；<br>API声明：LAYER = 0<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：EffectScope；<br>API声明：WHOLE = 1<br>差异内容：crossplatform|类名：EffectScope；<br>API声明：WHOLE = 1<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum EffectFillStyle<br>差异内容：crossplatform|类名：global；<br>API声明：declare enum EffectFillStyle<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：EffectFillStyle；<br>API声明：CUMULATIVE = 0<br>差异内容：crossplatform|类名：EffectFillStyle；<br>API声明：CUMULATIVE = 0<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：EffectFillStyle；<br>API声明：ITERATIVE = 1<br>差异内容：crossplatform|类名：EffectFillStyle；<br>API声明：ITERATIVE = 1<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class SymbolEffect<br>差异内容：crossplatform|类名：global；<br>API声明：declare class SymbolEffect<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class ScaleSymbolEffect<br>差异内容：crossplatform|类名：global；<br>API声明：declare class ScaleSymbolEffect<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：ScaleSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：crossplatform|类名：ScaleSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：ScaleSymbolEffect；<br>API声明：direction?: EffectDirection;<br>差异内容：crossplatform|类名：ScaleSymbolEffect；<br>API声明：direction?: EffectDirection;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class HierarchicalSymbolEffect<br>差异内容：crossplatform|类名：global；<br>API声明：declare class HierarchicalSymbolEffect<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：HierarchicalSymbolEffect；<br>API声明：fillStyle?: EffectFillStyle;<br>差异内容：crossplatform|类名：HierarchicalSymbolEffect；<br>API声明：fillStyle?: EffectFillStyle;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class AppearSymbolEffect<br>差异内容：crossplatform|类名：global；<br>API声明：declare class AppearSymbolEffect<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：AppearSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：crossplatform|类名：AppearSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class DisappearSymbolEffect<br>差异内容：crossplatform|类名：global；<br>API声明：declare class DisappearSymbolEffect<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：DisappearSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：crossplatform|类名：DisappearSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class BounceSymbolEffect<br>差异内容：crossplatform|类名：global；<br>API声明：declare class BounceSymbolEffect<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：BounceSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：crossplatform|类名：BounceSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：BounceSymbolEffect；<br>API声明：direction?: EffectDirection;<br>差异内容：crossplatform|类名：BounceSymbolEffect；<br>API声明：direction?: EffectDirection;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class ReplaceSymbolEffect<br>差异内容：crossplatform|类名：global；<br>API声明：declare class ReplaceSymbolEffect<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：ReplaceSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：crossplatform|类名：ReplaceSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class PulseSymbolEffect<br>差异内容：crossplatform|类名：global；<br>API声明：declare class PulseSymbolEffect<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class SymbolGlyphAttribute<br>差异内容：crossplatform|类名：global；<br>API声明：declare class SymbolGlyphAttribute<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolGlyphAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolGlyphAttribute;<br>差异内容：crossplatform|类名：SymbolGlyphAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolGlyphAttribute;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolGlyphAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolGlyphAttribute;<br>差异内容：crossplatform|类名：SymbolGlyphAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolGlyphAttribute;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolGlyphAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolGlyphAttribute;<br>差异内容：crossplatform|类名：SymbolGlyphAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolGlyphAttribute;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolGlyphAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolGlyphAttribute;<br>差异内容：crossplatform|类名：SymbolGlyphAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolGlyphAttribute;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolGlyphAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolGlyphAttribute;<br>差异内容：crossplatform|类名：SymbolGlyphAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolGlyphAttribute;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolGlyphAttribute；<br>API声明：symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean): SymbolGlyphAttribute;<br>差异内容：crossplatform|类名：SymbolGlyphAttribute；<br>API声明：symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean): SymbolGlyphAttribute;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：SymbolGlyphAttribute；<br>API声明：symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number): SymbolGlyphAttribute;<br>差异内容：crossplatform|类名：SymbolGlyphAttribute；<br>API声明：symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number): SymbolGlyphAttribute;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare const SymbolGlyph: SymbolGlyphInterface;<br>差异内容：crossplatform|类名：global；<br>API声明：declare const SymbolGlyph: SymbolGlyphInterface;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare const SymbolGlyphInstance: SymbolGlyphAttribute;<br>差异内容：crossplatform|类名：global；<br>API声明：declare const SymbolGlyphInstance: SymbolGlyphAttribute;<br>差异内容：NA|component/symbolglyph.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：interface SymbolSpanInterface<br>差异内容：crossplatform|类名：global；<br>API声明：interface SymbolSpanInterface<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class SymbolSpanAttribute<br>差异内容：crossplatform|类名：global；<br>API声明：declare class SymbolSpanAttribute<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：SymbolSpanAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolSpanAttribute;<br>差异内容：crossplatform|类名：SymbolSpanAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolSpanAttribute;<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：SymbolSpanAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolSpanAttribute;<br>差异内容：crossplatform|类名：SymbolSpanAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolSpanAttribute;<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：SymbolSpanAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolSpanAttribute;<br>差异内容：crossplatform|类名：SymbolSpanAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolSpanAttribute;<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：SymbolSpanAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolSpanAttribute;<br>差异内容：crossplatform|类名：SymbolSpanAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolSpanAttribute;<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：SymbolSpanAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolSpanAttribute;<br>差异内容：crossplatform|类名：SymbolSpanAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolSpanAttribute;<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：SymbolSpanAttribute；<br>API声明：attributeModifier(modifier: AttributeModifier\<SymbolSpanAttribute>): SymbolSpanAttribute;<br>差异内容：crossplatform|类名：SymbolSpanAttribute；<br>API声明：attributeModifier(modifier: AttributeModifier\<SymbolSpanAttribute>): SymbolSpanAttribute;<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare const SymbolSpan: SymbolSpanInterface;<br>差异内容：crossplatform|类名：global；<br>API声明：declare const SymbolSpan: SymbolSpanInterface;<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare const SymbolSpanInstance: SymbolSpanAttribute;<br>差异内容：crossplatform|类名：global；<br>API声明：declare const SymbolSpanInstance: SymbolSpanAttribute;<br>差异内容：NA|component/symbol_span.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class TabBarSymbol<br>差异内容：crossplatform|类名：global；<br>API声明：declare class TabBarSymbol<br>差异内容：NA|component/tab_content.d.ts|
|API跨平台权限变更|类名：TabBarSymbol；<br>API声明：normal: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：TabBarSymbol；<br>API声明：normal: SymbolGlyphModifier;<br>差异内容：NA|component/tab_content.d.ts|
|API跨平台权限变更|类名：TabBarSymbol；<br>API声明：selected?: SymbolGlyphModifier;<br>差异内容：crossplatform|类名：TabBarSymbol；<br>API声明：selected?: SymbolGlyphModifier;<br>差异内容：NA|component/tab_content.d.ts|
|API废弃版本变更|类名：ChipGroupItemOptions；<br>API声明：suffixIcon?: IconOptions;<br>差异内容：NA|类名：ChipGroupItemOptions；<br>API声明：suffixIcon?: IconOptions;<br>差异内容：14|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|API废弃版本变更|类名：CommonMethod；<br>API声明：gridSpan(value: number): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：gridSpan(value: number): T;<br>差异内容：14|component/common.d.ts|
|API废弃版本变更|类名：CommonMethod；<br>API声明：gridOffset(value: number): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：gridOffset(value: number): T;<br>差异内容：14|component/common.d.ts|
|函数变更|类名：NavDestinationAttribute；<br>API声明：title(value: string \| CustomBuilder \| NavDestinationCommonTitle \| NavDestinationCustomTitle, options?: NavigationTitleOptions): NavDestinationAttribute;<br>差异内容：value: string \| CustomBuilder \| NavDestinationCommonTitle \| NavDestinationCustomTitle|类名：NavDestinationAttribute；<br>API声明：title(value: string \| CustomBuilder \| NavDestinationCommonTitle \| NavDestinationCustomTitle \| Resource, options?: NavigationTitleOptions): NavDestinationAttribute;<br>差异内容：value: string \| CustomBuilder \| NavDestinationCommonTitle \| NavDestinationCustomTitle \| Resource|component/nav_destination.d.ts|
|属性变更|类名：NavigationCommonTitle；<br>API声明：main: string;<br>差异内容：string|类名：NavigationCommonTitle；<br>API声明：main: string \| Resource;<br>差异内容：string,Resource|component/navigation.d.ts|
|属性变更|类名：NavigationCommonTitle；<br>API声明：sub: string;<br>差异内容：string|类名：NavigationCommonTitle；<br>API声明：sub: string \| Resource;<br>差异内容：string,Resource|component/navigation.d.ts|
|属性变更|类名：NavigationMenuItem；<br>API声明：value: string;<br>差异内容：string|类名：NavigationMenuItem；<br>API声明：value: string \| Resource;<br>差异内容：string,Resource|component/navigation.d.ts|
|属性变更|类名：NavigationMenuItem；<br>API声明：icon?: string;<br>差异内容：string|类名：NavigationMenuItem；<br>API声明：icon?: string \| Resource;<br>差异内容：string,Resource|component/navigation.d.ts|
|属性变更|类名：NavDestinationCommonTitle；<br>API声明：main: string;<br>差异内容：string|类名：NavDestinationCommonTitle；<br>API声明：main: string \| Resource;<br>差异内容：string,Resource|component/nav_destination.d.ts|
|属性变更|类名：NavDestinationCommonTitle；<br>API声明：sub: string;<br>差异内容：string|类名：NavDestinationCommonTitle；<br>API声明：sub: string \| Resource;<br>差异内容：string,Resource|component/nav_destination.d.ts|
|自定义类型变更|类名：global；<br>API声明：declare type StyledStringValue = TextStyle \| DecorationStyle \| BaselineOffsetStyle \| LetterSpacingStyle \| TextShadowStyle \| GestureStyle \| ImageAttachment \| ParagraphStyle \| LineHeightStyle \| CustomSpan \| UserDataSpan;<br>差异内容：TextStyle \| DecorationStyle \| BaselineOffsetStyle \| LetterSpacingStyle \| TextShadowStyle \| GestureStyle \| ImageAttachment \| ParagraphStyle \| LineHeightStyle \| CustomSpan \| UserDataSpan|类名：global；<br>API声明：declare type StyledStringValue = TextStyle \| DecorationStyle \| BaselineOffsetStyle \| LetterSpacingStyle \| TextShadowStyle \| GestureStyle \| ImageAttachment \| ParagraphStyle \| LineHeightStyle \| UrlStyle \| CustomSpan \| UserDataSpan \| BackgroundColorStyle;<br>差异内容：TextStyle \| DecorationStyle \| BaselineOffsetStyle \| LetterSpacingStyle \| TextShadowStyle \| GestureStyle \| ImageAttachment \| ParagraphStyle \| LineHeightStyle \| UrlStyle \| CustomSpan \| UserDataSpan \| BackgroundColorStyle|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare enum SplitPolicy<br>差异内容：export declare enum SplitPolicy|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：SplitPolicy；<br>API声明：HOME_PAGE = 0<br>差异内容：HOME_PAGE = 0|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：SplitPolicy；<br>API声明：DETAIL_PAGE = 1<br>差异内容：DETAIL_PAGE = 1|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：SplitPolicy；<br>API声明：FULL_PAGE = 2<br>差异内容：FULL_PAGE = 2|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct MultiNavigation<br>差异内容：export declare struct MultiNavigation|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavigation；<br>API声明：@State<br>    multiStack: MultiNavPathStack;<br>差异内容：@State<br>    multiStack: MultiNavPathStack;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavigation；<br>API声明：@BuilderParam<br>    navDestination: NavDestinationBuildFunction;<br>差异内容：@BuilderParam<br>    navDestination: NavDestinationBuildFunction;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavigation；<br>API声明：onNavigationModeChange?: OnNavigationModeChangeCallback;<br>差异内容：onNavigationModeChange?: OnNavigationModeChangeCallback;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavigation；<br>API声明：onHomeShowOnTop?: OnHomeShowOnTopCallback;<br>差异内容：onHomeShowOnTop?: OnHomeShowOnTopCallback;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class MultiNavPathStack<br>差异内容：export declare class MultiNavPathStack|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void;<br>差异内容：pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void;<br>差异内容：pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void;<br>差异内容：pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：pushPathByName(name: string, param: Object, onPop?: base.Callback\<PopInfo>, animated?: boolean, policy?: SplitPolicy): void;<br>差异内容：pushPathByName(name: string, param: Object, onPop?: base.Callback\<PopInfo>, animated?: boolean, policy?: SplitPolicy): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：replacePath(info: NavPathInfo, animated?: boolean): void;<br>差异内容：replacePath(info: NavPathInfo, animated?: boolean): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：replacePath(info: NavPathInfo, options?: NavigationOptions): void;<br>差异内容：replacePath(info: NavPathInfo, options?: NavigationOptions): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：replacePathByName(name: string, param: Object, animated?: boolean): void;<br>差异内容：replacePathByName(name: string, param: Object, animated?: boolean): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：removeByIndexes(indexes: Array\<number>): number;<br>差异内容：removeByIndexes(indexes: Array\<number>): number;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：removeByName(name: string): number;<br>差异内容：removeByName(name: string): number;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：pop(animated?: boolean): NavPathInfo \| undefined;<br>差异内容：pop(animated?: boolean): NavPathInfo \| undefined;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：pop(result?: Object, animated?: boolean): NavPathInfo \| undefined;<br>差异内容：pop(result?: Object, animated?: boolean): NavPathInfo \| undefined;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：popToName(name: string, animated?: boolean): number;<br>差异内容：popToName(name: string, animated?: boolean): number;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：popToName(name: string, result: Object, animated?: boolean): number;<br>差异内容：popToName(name: string, result: Object, animated?: boolean): number;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：popToIndex(index: number, animated?: boolean): void;<br>差异内容：popToIndex(index: number, animated?: boolean): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：popToIndex(index: number, result: Object, animated?: boolean): void;<br>差异内容：popToIndex(index: number, result: Object, animated?: boolean): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：moveToTop(name: string, animated?: boolean): number;<br>差异内容：moveToTop(name: string, animated?: boolean): number;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：moveIndexToTop(index: number, animated?: boolean): void;<br>差异内容：moveIndexToTop(index: number, animated?: boolean): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：clear(animated?: boolean): void;<br>差异内容：clear(animated?: boolean): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：getAllPathName(): Array\<string>;<br>差异内容：getAllPathName(): Array\<string>;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：getParamByIndex(index: number): Object \| undefined;<br>差异内容：getParamByIndex(index: number): Object \| undefined;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：getParamByName(name: string): Array\<Object>;<br>差异内容：getParamByName(name: string): Array\<Object>;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：getIndexByName(name: string): Array\<number>;<br>差异内容：getIndexByName(name: string): Array\<number>;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：size(): number;<br>差异内容：size(): number;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：disableAnimation(disable: boolean): void;<br>差异内容：disableAnimation(disable: boolean): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：switchFullScreenState(isFullScreen?: boolean): boolean;<br>差异内容：switchFullScreenState(isFullScreen?: boolean): boolean;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：setHomeWidthRange(minPercent: number, maxPercent: number): void;<br>差异内容：setHomeWidthRange(minPercent: number, maxPercent: number): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：keepBottomPage(keepBottom: boolean): void;<br>差异内容：keepBottomPage(keepBottom: boolean): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：MultiNavPathStack；<br>API声明：setPlaceholderPage(info: NavPathInfo): void;<br>差异内容：setPlaceholderPage(info: NavPathInfo): void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：global；<br>API声明：declare type NavDestinationBuildFunction = (name: string, param?: object) => void;<br>差异内容：declare type NavDestinationBuildFunction = (name: string, param?: object) => void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：global；<br>API声明：declare type OnNavigationModeChangeCallback = (mode: NavigationMode) => void;<br>差异内容：declare type OnNavigationModeChangeCallback = (mode: NavigationMode) => void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：global；<br>API声明：declare type OnHomeShowOnTopCallback = (name: string) => void;<br>差异内容：declare type OnHomeShowOnTopCallback = (name: string) => void;|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|新增API|NA|类名：global；<br>API声明：export class MarqueeDynamicSyncScene<br>差异内容：export class MarqueeDynamicSyncScene|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：MarqueeDynamicSyncScene；<br>API声明：readonly type: MarqueeDynamicSyncSceneType;<br>差异内容：readonly type: MarqueeDynamicSyncSceneType;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：FocusController；<br>API声明：activate(isActive: boolean, autoInactive?: boolean): void;<br>差异内容：activate(isActive: boolean, autoInactive?: boolean): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：FocusController；<br>API声明：setAutoFocusTransfer(isAutoFocusTransfer: boolean): void;<br>差异内容：setAutoFocusTransfer(isAutoFocusTransfer: boolean): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：KeyboardAvoidMode；<br>API声明：OFFSET_WITH_CARET = 2<br>差异内容：OFFSET_WITH_CARET = 2|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：KeyboardAvoidMode；<br>API声明：RESIZE_WITH_CARET = 3<br>差异内容：RESIZE_WITH_CARET = 3|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：KeyboardAvoidMode；<br>API声明：NONE = 4<br>差异内容：NONE = 4|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export const enum MarqueeDynamicSyncSceneType<br>差异内容：export const enum MarqueeDynamicSyncSceneType|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：MarqueeDynamicSyncSceneType；<br>API声明：ANIMATION = 1<br>差异内容：ANIMATION = 1|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare enum AccessibilitySelectedType<br>差异内容：export declare enum AccessibilitySelectedType|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：AccessibilitySelectedType；<br>API声明：CLICKED = 0<br>差异内容：CLICKED = 0|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：AccessibilitySelectedType；<br>API声明：CHECKED = 1<br>差异内容：CHECKED = 1|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：AccessibilitySelectedType；<br>API声明：SELECTED = 2<br>差异内容：SELECTED = 2|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：SuffixIconOptions；<br>API声明：accessibilityText?: ResourceStr;<br>差异内容：accessibilityText?: ResourceStr;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：SuffixIconOptions；<br>API声明：accessibilityDescription?: ResourceStr;<br>差异内容：accessibilityDescription?: ResourceStr;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：SuffixIconOptions；<br>API声明：accessibilityLevel?: string;<br>差异内容：accessibilityLevel?: string;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface AccessibilityOptions<br>差异内容：export interface AccessibilityOptions|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：AccessibilityOptions；<br>API声明：accessibilityLevel?: string;<br>差异内容：accessibilityLevel?: string;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：AccessibilityOptions；<br>API声明：accessibilityText?: ResourceStr;<br>差异内容：accessibilityText?: ResourceStr;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：AccessibilityOptions；<br>API声明：accessibilityDescription?: ResourceStr;<br>差异内容：accessibilityDescription?: ResourceStr;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface CloseOptions<br>差异内容：export interface CloseOptions|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface ChipSuffixSymbolGlyphOptions<br>差异内容：export interface ChipSuffixSymbolGlyphOptions|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipSuffixSymbolGlyphOptions；<br>API声明：normalAccessibility?: AccessibilityOptions;<br>差异内容：normalAccessibility?: AccessibilityOptions;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipSuffixSymbolGlyphOptions；<br>API声明：activatedAccessibility?: AccessibilityOptions;<br>差异内容：activatedAccessibility?: AccessibilityOptions;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipSuffixSymbolGlyphOptions；<br>API声明：action?: VoidCallback;<br>差异内容：action?: VoidCallback;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions;<br>差异内容：suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：closeOptions?: CloseOptions;<br>差异内容：closeOptions?: CloseOptions;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：accessibilityDescription?: ResourceStr;<br>差异内容：accessibilityDescription?: ResourceStr;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：accessibilityLevel?: string;<br>差异内容：accessibilityLevel?: string;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：accessibilitySelectedType?: AccessibilitySelectedType;<br>差异内容：accessibilitySelectedType?: AccessibilitySelectedType;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface SuffixImageIconOptions<br>差异内容：export interface SuffixImageIconOptions|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：SuffixImageIconOptions；<br>API声明：action?: VoidCallback;<br>差异内容：action?: VoidCallback;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：SuffixImageIconOptions；<br>API声明：accessibilityText?: ResourceStr;<br>差异内容：accessibilityText?: ResourceStr;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：SuffixImageIconOptions；<br>API声明：accessibilityDescription?: ResourceStr;<br>差异内容：accessibilityDescription?: ResourceStr;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：SuffixImageIconOptions；<br>API声明：accessibilityLevel?: string;<br>差异内容：accessibilityLevel?: string;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：suffixImageIcon?: SuffixImageIconOptions;<br>差异内容：suffixImageIcon?: SuffixImageIconOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions;<br>差异内容：suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：closeOptions?: CloseOptions;<br>差异内容：closeOptions?: CloseOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：accessibilityDescription?: ResourceStr;<br>差异内容：accessibilityDescription?: ResourceStr;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：accessibilityLevel?: string;<br>差异内容：accessibilityLevel?: string;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：IconItemOptions；<br>API声明：accessibilityText?: ResourceStr;<br>差异内容：accessibilityText?: ResourceStr;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：IconItemOptions；<br>API声明：accessibilityDescription?: ResourceStr;<br>差异内容：accessibilityDescription?: ResourceStr;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：IconItemOptions；<br>API声明：accessibilityLevel?: string;<br>差异内容：accessibilityLevel?: string;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface SymbolItemOptions<br>差异内容：export interface SymbolItemOptions|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：SymbolItemOptions；<br>API声明：symbol: SymbolGlyphModifier;<br>差异内容：symbol: SymbolGlyphModifier;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：SymbolItemOptions；<br>API声明：action: VoidCallback;<br>差异内容：action: VoidCallback;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：SymbolItemOptions；<br>API声明：accessibilityText?: ResourceStr;<br>差异内容：accessibilityText?: ResourceStr;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：SymbolItemOptions；<br>API声明：accessibilityDescription?: ResourceStr;<br>差异内容：accessibilityDescription?: ResourceStr;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：SymbolItemOptions；<br>API声明：accessibilityLevel?: string;<br>差异内容：accessibilityLevel?: string;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：Window；<br>API声明：setSubWindowModal(isModal: boolean, modalityType: ModalityType): Promise\<void>;<br>差异内容：setSubWindowModal(isModal: boolean, modalityType: ModalityType): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：window；<br>API声明：interface DecorButtonStyle<br>差异内容：interface DecorButtonStyle|api/@ohos.window.d.ts|
|新增API|NA|类名：DecorButtonStyle；<br>API声明：colorMode?: ConfigurationConstant.ColorMode;<br>差异内容：colorMode?: ConfigurationConstant.ColorMode;|api/@ohos.window.d.ts|
|新增API|NA|类名：DecorButtonStyle；<br>API声明：buttonBackgroundSize?: number;<br>差异内容：buttonBackgroundSize?: number;|api/@ohos.window.d.ts|
|新增API|NA|类名：DecorButtonStyle；<br>API声明：spacingBetweenButtons?: number;<br>差异内容：spacingBetweenButtons?: number;|api/@ohos.window.d.ts|
|新增API|NA|类名：DecorButtonStyle；<br>API声明：closeButtonRightMargin?: number;<br>差异内容：closeButtonRightMargin?: number;|api/@ohos.window.d.ts|
|新增API|NA|类名：window；<br>API声明：function getWindowsByCoordinate(displayId: number, windowNumber?: number, x?: number, y?: number): Promise\<Array\<Window>>;<br>差异内容：function getWindowsByCoordinate(displayId: number, windowNumber?: number, x?: number, y?: number): Promise\<Array\<Window>>;|api/@ohos.window.d.ts|
|新增API|NA|类名：MaximizePresentation；<br>API声明：ENTER_IMMERSIVE_DISABLE_TITLE_AND_DOCK_HOVER = 3<br>差异内容：ENTER_IMMERSIVE_DISABLE_TITLE_AND_DOCK_HOVER = 3|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：on(type: 'displayIdChange', callback: Callback\<number>): void;<br>差异内容：on(type: 'displayIdChange', callback: Callback\<number>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：off(type: 'displayIdChange', callback?: Callback\<number>): void;<br>差异内容：off(type: 'displayIdChange', callback?: Callback\<number>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setWindowTopmost(isWindowTopmost: boolean): Promise\<void>;<br>差异内容：setWindowTopmost(isWindowTopmost: boolean): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：raiseToAppTop(): Promise\<void>;<br>差异内容：raiseToAppTop(): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setRaiseByClickEnabled(enable: boolean): Promise\<void>;<br>差异内容：setRaiseByClickEnabled(enable: boolean): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setResizeByDragEnabled(enable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：setResizeByDragEnabled(enable: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setResizeByDragEnabled(enable: boolean): Promise\<void>;<br>差异内容：setResizeByDragEnabled(enable: boolean): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：restore(): Promise\<void>;<br>差异内容：restore(): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setWindowTitleMoveEnabled(enabled: boolean): void;<br>差异内容：setWindowTitleMoveEnabled(enabled: boolean): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setDecorButtonStyle(dectorStyle: DecorButtonStyle): void;<br>差异内容：setDecorButtonStyle(dectorStyle: DecorButtonStyle): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：getDecorButtonStyle(): DecorButtonStyle;<br>差异内容：getDecorButtonStyle(): DecorButtonStyle;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setWindowTitleButtonVisible(isMaximizeButtonVisible: boolean, isMinimizeButtonVisible: boolean, isCloseButtonVisible?: boolean): void;<br>差异内容：setWindowTitleButtonVisible(isMaximizeButtonVisible: boolean, isMinimizeButtonVisible: boolean, isCloseButtonVisible?: boolean): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：startMoving(): Promise\<void>;<br>差异内容：startMoving(): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setTitleAndDockHoverShown(isTitleHoverShown?: boolean, isDockHoverShown?: boolean): Promise\<void>;<br>差异内容：setTitleAndDockHoverShown(isTitleHoverShown?: boolean, isDockHoverShown?: boolean): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：window；<br>API声明：enum ModalityType<br>差异内容：enum ModalityType|api/@ohos.window.d.ts|
|新增API|NA|类名：ModalityType；<br>API声明：WINDOW_MODALITY = 0<br>差异内容：WINDOW_MODALITY = 0|api/@ohos.window.d.ts|
|新增API|NA|类名：ModalityType；<br>API声明：APPLICATION_MODALITY = 1<br>差异内容：APPLICATION_MODALITY = 1|api/@ohos.window.d.ts|
|新增API|NA|类名：SubWindowOptions；<br>API声明：modalityType?: ModalityType;<br>差异内容：modalityType?: ModalityType;|api/@ohos.window.d.ts|
|新增API|NA|类名：WindowStage；<br>API声明：on(eventType: 'windowStageClose', callback: Callback\<void>): void;<br>差异内容：on(eventType: 'windowStageClose', callback: Callback\<void>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：WindowStage；<br>API声明：off(eventType: 'windowStageClose', callback?: Callback\<void>): void;<br>差异内容：off(eventType: 'windowStageClose', callback?: Callback\<void>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：WindowStage；<br>API声明：removeStartingWindow(): Promise\<void>;<br>差异内容：removeStartingWindow(): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：WindowStage；<br>API声明：setWindowModal(isModal: boolean): Promise\<void>;<br>差异内容：setWindowModal(isModal: boolean): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：WindowStage；<br>API声明：setWindowRectAutoSave(enabled: boolean): Promise\<void>;<br>差异内容：setWindowRectAutoSave(enabled: boolean): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：WindowStage；<br>API声明：isWindowRectAutoSave(): Promise\<boolean>;<br>差异内容：isWindowRectAutoSave(): Promise\<boolean>;|api/@ohos.window.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Marquee'): Marquee;<br>差异内容：function createNode(context: UIContext, nodeType: 'Marquee'): Marquee;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'TextArea'): TextArea;<br>差异内容：function createNode(context: UIContext, nodeType: 'TextArea'): TextArea;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'SymbolGlyph'): SymbolGlyph;<br>差异内容：function createNode(context: UIContext, nodeType: 'SymbolGlyph'): SymbolGlyph;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'QRCode'): QRCode;<br>差异内容：function createNode(context: UIContext, nodeType: 'QRCode'): QRCode;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Badge'): Badge;<br>差异内容：function createNode(context: UIContext, nodeType: 'Badge'): Badge;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'TextClock'): TextClock;<br>差异内容：function createNode(context: UIContext, nodeType: 'TextClock'): TextClock;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'TextTimer'): TextTimer;<br>差异内容：function createNode(context: UIContext, nodeType: 'TextTimer'): TextTimer;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Grid'): Grid;<br>差异内容：function createNode(context: UIContext, nodeType: 'Grid'): Grid;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'GridItem'): GridItem;<br>差异内容：function createNode(context: UIContext, nodeType: 'GridItem'): GridItem;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：get gestureEvent(): UIGestureEvent;<br>差异内容：get gestureEvent(): UIGestureEvent;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Marquee = TypedFrameNode\<MarqueeInterface, MarqueeAttribute>;<br>差异内容：type Marquee = TypedFrameNode\<MarqueeInterface, MarqueeAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type TextArea = TypedFrameNode\<TextAreaInterface, TextAreaAttribute>;<br>差异内容：type TextArea = TypedFrameNode\<TextAreaInterface, TextAreaAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type SymbolGlyph = TypedFrameNode\<SymbolGlyphInterface, SymbolGlyphAttribute>;<br>差异内容：type SymbolGlyph = TypedFrameNode\<SymbolGlyphInterface, SymbolGlyphAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type QRCode = TypedFrameNode\<QRCodeInterface, QRCodeAttribute>;<br>差异内容：type QRCode = TypedFrameNode\<QRCodeInterface, QRCodeAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Badge = TypedFrameNode\<BadgeInterface, BadgeAttribute>;<br>差异内容：type Badge = TypedFrameNode\<BadgeInterface, BadgeAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type TextClock = TypedFrameNode\<TextClockInterface, TextClockAttribute>;<br>差异内容：type TextClock = TypedFrameNode\<TextClockInterface, TextClockAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type TextTimer = TypedFrameNode\<TextTimerInterface, TextTimerAttribute>;<br>差异内容：type TextTimer = TypedFrameNode\<TextTimerInterface, TextTimerAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Grid = TypedFrameNode\<GridInterface, GridAttribute>;<br>差异内容：type Grid = TypedFrameNode\<GridInterface, GridAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type GridItem = TypedFrameNode\<GridItemInterface, GridItemAttribute>;<br>差异内容：type GridItem = TypedFrameNode\<GridItemInterface, GridItemAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：focusScopeId(id: string, isGroup?: boolean, arrowStepOut?: boolean): T;<br>差异内容：focusScopeId(id: string, isGroup?: boolean, arrowStepOut?: boolean): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：useEffect(useEffect: boolean, effectType: EffectType): T;<br>差异内容：useEffect(useEffect: boolean, effectType: EffectType): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：accessibilityGroup(isGroup: boolean, accessibilityOptions: AccessibilityOptions): T;<br>差异内容：accessibilityGroup(isGroup: boolean, accessibilityOptions: AccessibilityOptions): T;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum EffectType<br>差异内容：declare enum EffectType|component/common.d.ts|
|新增API|NA|类名：EffectType；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|component/common.d.ts|
|新增API|NA|类名：EffectType；<br>API声明：WINDOW_EFFECT = 1<br>差异内容：WINDOW_EFFECT = 1|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum BlurStyleActivePolicy<br>差异内容：declare enum BlurStyleActivePolicy|component/common.d.ts|
|新增API|NA|类名：BlurStyleActivePolicy；<br>API声明：FOLLOWS_WINDOW_ACTIVE_STATE = 0<br>差异内容：FOLLOWS_WINDOW_ACTIVE_STATE = 0|component/common.d.ts|
|新增API|NA|类名：BlurStyleActivePolicy；<br>API声明：ALWAYS_ACTIVE = 1<br>差异内容：ALWAYS_ACTIVE = 1|component/common.d.ts|
|新增API|NA|类名：BlurStyleActivePolicy；<br>API声明：ALWAYS_INACTIVE = 2<br>差异内容：ALWAYS_INACTIVE = 2|component/common.d.ts|
|新增API|NA|类名：BackgroundBlurStyleOptions；<br>API声明：policy?: BlurStyleActivePolicy;<br>差异内容：policy?: BlurStyleActivePolicy;|component/common.d.ts|
|新增API|NA|类名：BackgroundBlurStyleOptions；<br>API声明：inactiveColor?: ResourceColor;<br>差异内容：inactiveColor?: ResourceColor;|component/common.d.ts|
|新增API|NA|类名：BackgroundEffectOptions；<br>API声明：policy?: BlurStyleActivePolicy;<br>差异内容：policy?: BlurStyleActivePolicy;|component/common.d.ts|
|新增API|NA|类名：BackgroundEffectOptions；<br>API声明：inactiveColor?: ResourceColor;<br>差异内容：inactiveColor?: ResourceColor;|component/common.d.ts|
|新增API|NA|类名：KeyEvent；<br>API声明：unicode?: number;<br>差异内容：unicode?: number;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface FadingEdgeOptions<br>差异内容：declare interface FadingEdgeOptions|component/common.d.ts|
|新增API|NA|类名：FadingEdgeOptions；<br>API声明：fadingEdgeLength?: LengthMetrics;<br>差异内容：fadingEdgeLength?: LengthMetrics;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：chainWeight(chainWeight: ChainWeightOptions): T;<br>差异内容：chainWeight(chainWeight: ChainWeightOptions): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：safeAreaPadding(paddingValue: Padding \| LengthMetrics \| LocalizedPadding): T;<br>差异内容：safeAreaPadding(paddingValue: Padding \| LengthMetrics \| LocalizedPadding): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：tabStop(isTabStop: boolean): T;<br>差异内容：tabStop(isTabStop: boolean): T;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ContentClipMode<br>差异内容：declare enum ContentClipMode|component/common.d.ts|
|新增API|NA|类名：ContentClipMode；<br>API声明：CONTENT_ONLY = 0<br>差异内容：CONTENT_ONLY = 0|component/common.d.ts|
|新增API|NA|类名：ContentClipMode；<br>API声明：BOUNDARY = 1<br>差异内容：BOUNDARY = 1|component/common.d.ts|
|新增API|NA|类名：ContentClipMode；<br>API声明：SAFE_AREA = 2<br>差异内容：SAFE_AREA = 2|component/common.d.ts|
|新增API|NA|类名：ScrollableCommonMethod；<br>API声明：fadingEdge(enabled: Optional\<boolean>, options?: FadingEdgeOptions): T;<br>差异内容：fadingEdge(enabled: Optional\<boolean>, options?: FadingEdgeOptions): T;|component/common.d.ts|
|新增API|NA|类名：ScrollableCommonMethod；<br>API声明：clipContent(clip: ContentClipMode \| RectShape): T;<br>差异内容：clipContent(clip: ContentClipMode \| RectShape): T;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum HoverModeAreaType<br>差异内容：declare enum HoverModeAreaType|component/common.d.ts|
|新增API|NA|类名：HoverModeAreaType；<br>API声明：TOP_SCREEN = 0<br>差异内容：TOP_SCREEN = 0|component/common.d.ts|
|新增API|NA|类名：HoverModeAreaType；<br>API声明：BOTTOM_SCREEN = 1<br>差异内容：BOTTOM_SCREEN = 1|component/common.d.ts|
|新增API|NA|类名：GridAttribute；<br>API声明：cachedCount(count: number, show: boolean): GridAttribute;<br>差异内容：cachedCount(count: number, show: boolean): GridAttribute;|component/grid.d.ts|
|新增API|NA|类名：ListAttribute；<br>API声明：cachedCount(count: number, show: boolean): ListAttribute;<br>差异内容：cachedCount(count: number, show: boolean): ListAttribute;|component/list.d.ts|
|新增API|NA|类名：ListScroller；<br>API声明：getVisibleListContentInfo(x: number, y: number): VisibleListContentInfo;<br>差异内容：getVisibleListContentInfo(x: number, y: number): VisibleListContentInfo;|component/list.d.ts|
|新增API|NA|类名：BarStyle；<br>API声明：SAFE_AREA_PADDING = 2<br>差异内容：SAFE_AREA_PADDING = 2|component/navigation.d.ts|
|新增API|NA|类名：NavigationToolbarOptions；<br>API声明：barStyle?: BarStyle;<br>差异内容：barStyle?: BarStyle;|component/navigation.d.ts|
|新增API|NA|类名：NavigationAttribute；<br>API声明：recoverable(recoverable: Optional\<boolean>): NavigationAttribute;<br>差异内容：recoverable(recoverable: Optional\<boolean>): NavigationAttribute;|component/navigation.d.ts|
|新增API|NA|类名：NavigationAttribute；<br>API声明：enableDragBar(isEnabled: Optional\<boolean>): NavigationAttribute;<br>差异内容：enableDragBar(isEnabled: Optional\<boolean>): NavigationAttribute;|component/navigation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum NavigationSystemTransitionType<br>差异内容：declare enum NavigationSystemTransitionType|component/nav_destination.d.ts|
|新增API|NA|类名：NavigationSystemTransitionType；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|component/nav_destination.d.ts|
|新增API|NA|类名：NavigationSystemTransitionType；<br>API声明：NONE = 1<br>差异内容：NONE = 1|component/nav_destination.d.ts|
|新增API|NA|类名：NavigationSystemTransitionType；<br>API声明：TITLE = 2<br>差异内容：TITLE = 2|component/nav_destination.d.ts|
|新增API|NA|类名：NavigationSystemTransitionType；<br>API声明：CONTENT = 3<br>差异内容：CONTENT = 3|component/nav_destination.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface NestedScrollInfo<br>差异内容：declare interface NestedScrollInfo|component/nav_destination.d.ts|
|新增API|NA|类名：NestedScrollInfo；<br>API声明：parent: Scroller;<br>差异内容：parent: Scroller;|component/nav_destination.d.ts|
|新增API|NA|类名：NestedScrollInfo；<br>API声明：child: Scroller;<br>差异内容：child: Scroller;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：systemTransition(type: NavigationSystemTransitionType): NavDestinationAttribute;<br>差异内容：systemTransition(type: NavigationSystemTransitionType): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：recoverable(recoverable: Optional\<boolean>): NavDestinationAttribute;<br>差异内容：recoverable(recoverable: Optional\<boolean>): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：bindToScrollable(scrollers: Array\<Scroller>): NavDestinationAttribute;<br>差异内容：bindToScrollable(scrollers: Array\<Scroller>): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：bindToNestedScrollable(scrollInfos: Array\<NestedScrollInfo>): NavDestinationAttribute;<br>差异内容：bindToNestedScrollable(scrollInfos: Array\<NestedScrollInfo>): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：RichEditorImageSpanOptions；<br>API声明：onHover?: OnHoverCallback;<br>差异内容：onHover?: OnHoverCallback;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type OnHoverCallback = (status: boolean, event: HoverEvent) => void;<br>差异内容：declare type OnHoverCallback = (status: boolean, event: HoverEvent) => void;|component/rich_editor.d.ts|
|新增API|NA|类名：Scroller；<br>API声明：getItemIndex(x: number, y: number): number;<br>差异内容：getItemIndex(x: number, y: number): number;|component/scroll.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ScrollPageOptions<br>差异内容：declare interface ScrollPageOptions|component/scroll.d.ts|
|新增API|NA|类名：ScrollPageOptions；<br>API声明：next: boolean;<br>差异内容：next: boolean;|component/scroll.d.ts|
|新增API|NA|类名：ScrollPageOptions；<br>API声明：animation?: boolean;<br>差异内容：animation?: boolean;|component/scroll.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：onSubmit(callback: SearchSubmitCallback): SearchAttribute;<br>差异内容：onSubmit(callback: SearchSubmitCallback): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type SearchSubmitCallback = (searchContent: string, event?: SubmitEvent) => void;<br>差异内容：declare type SearchSubmitCallback = (searchContent: string, event?: SubmitEvent) => void;|component/search.d.ts|
|新增API|NA|类名：StyledString；<br>API声明：static toHtml(styledString: StyledString): string;<br>差异内容：static toHtml(styledString: StyledString): string;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class BackgroundColorStyle<br>差异内容：declare class BackgroundColorStyle|component/styled_string.d.ts|
|新增API|NA|类名：BackgroundColorStyle；<br>API声明：readonly textBackgroundStyle: TextBackgroundStyle;<br>差异内容：readonly textBackgroundStyle: TextBackgroundStyle;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class UrlStyle<br>差异内容：declare class UrlStyle|component/styled_string.d.ts|
|新增API|NA|类名：UrlStyle；<br>API声明：readonly url: string;<br>差异内容：readonly url: string;|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：BACKGROUND_COLOR = 6<br>差异内容：BACKGROUND_COLOR = 6|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：URL = 7<br>差异内容：URL = 7|component/styled_string.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：onSubmit(callback: TextAreaSubmitCallback): TextAreaAttribute;<br>差异内容：onSubmit(callback: TextAreaSubmitCallback): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void;<br>差异内容：declare type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void;|component/text_area.d.ts|
|新增API|NA|类名：WaterFlowAttribute；<br>API声明：cachedCount(count: number, show: boolean): WaterFlowAttribute;<br>差异内容：cachedCount(count: number, show: boolean): WaterFlowAttribute;|component/water_flow.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare struct PopoverDialog<br>差异内容：export declare struct PopoverDialog|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：PopoverDialog；<br>API声明：@Link<br>    visible: boolean;<br>差异内容：@Link<br>    visible: boolean;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：PopoverDialog；<br>API声明：@Require<br>    @Prop<br>    popover: PopoverOptions;<br>差异内容：@Require<br>    @Prop<br>    popover: PopoverOptions;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：PopoverDialog；<br>API声明：@Require<br>    @BuilderParam<br>    targetBuilder: Callback\<void>;<br>差异内容：@Require<br>    @BuilderParam<br>    targetBuilder: Callback\<void>;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface PopoverOptions<br>差异内容：export declare interface PopoverOptions|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：SegmentButton；<br>API声明：@Prop<br>    maxFontScale: number \| Resource;<br>差异内容：@Prop<br>    maxFontScale: number \| Resource;|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|新增API|NA|类名：WindowProxy；<br>API声明：on(type: 'rectChange', reasons: number, callback: Callback\<RectChangeOptions>): void;<br>差异内容：on(type: 'rectChange', reasons: number, callback: Callback\<RectChangeOptions>): void;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：WindowProxy；<br>API声明：off(type: 'rectChange', callback?: Callback\<RectChangeOptions>): void;<br>差异内容：off(type: 'rectChange', callback?: Callback\<RectChangeOptions>): void;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：WindowProxy；<br>API声明：properties: WindowProxyProperties;<br>差异内容：properties: WindowProxyProperties;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：uiExtension；<br>API声明：interface WindowProxyProperties<br>差异内容：interface WindowProxyProperties|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：WindowProxyProperties；<br>API声明：uiExtensionHostWindowProxyRect: window.Rect;<br>差异内容：uiExtensionHostWindowProxyRect: window.Rect;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：uiExtension；<br>API声明：enum RectChangeReason<br>差异内容：enum RectChangeReason|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：RectChangeReason；<br>API声明：HOST_WINDOW_RECT_CHANGE = 0x0001<br>差异内容：HOST_WINDOW_RECT_CHANGE = 0x0001|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：uiExtension；<br>API声明：interface RectChangeOptions<br>差异内容：interface RectChangeOptions|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：RectChangeOptions；<br>API声明：rect: window.Rect;<br>差异内容：rect: window.Rect;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：RectChangeOptions；<br>API声明：reason: RectChangeReason;<br>差异内容：reason: RectChangeReason;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：display；<br>API声明：function getPrimaryDisplaySync(): Display;<br>差异内容：function getPrimaryDisplaySync(): Display;|api/@ohos.display.d.ts|
|新增API|NA|类名：ShowToastOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowToastOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowDialogOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowDialogOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：RouterOptions；<br>API声明：recoverable?: boolean;<br>差异内容：recoverable?: boolean;|api/@ohos.router.d.ts|
|新增API|NA|类名：NamedRouterOptions；<br>API声明：recoverable?: boolean;<br>差异内容：recoverable?: boolean;|api/@ohos.router.d.ts|
|新增API|NA|类名：screenshot；<br>API声明：function capture(options?: CaptureOption): Promise\<image.PixelMap>;<br>差异内容：function capture(options?: CaptureOption): Promise\<image.PixelMap>;|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：screenshot；<br>API声明：interface CaptureOption<br>差异内容：interface CaptureOption|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：CaptureOption；<br>API声明：displayId?: number;<br>差异内容：displayId?: number;|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|component/action_sheet.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|component/alert_dialog.d.ts|
|新增API|NA|类名：CalendarDialogOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|component/calendar_picker.d.ts|
|新增API|NA|类名：CalendarDialogOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|component/calendar_picker.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LunarSwitchStyle<br>差异内容：declare interface LunarSwitchStyle|component/date_picker.d.ts|
|新增API|NA|类名：LunarSwitchStyle；<br>API声明：selectedColor?: ResourceColor;<br>差异内容：selectedColor?: ResourceColor;|component/date_picker.d.ts|
|新增API|NA|类名：LunarSwitchStyle；<br>API声明：unselectedColor?: ResourceColor;<br>差异内容：unselectedColor?: ResourceColor;|component/date_picker.d.ts|
|新增API|NA|类名：LunarSwitchStyle；<br>API声明：strokeColor?: ResourceColor;<br>差异内容：strokeColor?: ResourceColor;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：lunarSwitchStyle?: LunarSwitchStyle;<br>差异内容：lunarSwitchStyle?: LunarSwitchStyle;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|component/date_picker.d.ts|
|新增API|NA|类名：GestureInterface；<br>API声明：allowedTypes(types: Array\<SourceTool>): T;<br>差异内容：allowedTypes(types: Array\<SourceTool>): T;|component/gesture.d.ts|
|新增API|NA|类名：GestureHandler；<br>API声明：allowedTypes(types: Array\<SourceTool>): T;<br>差异内容：allowedTypes(types: Array\<SourceTool>): T;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ImageRotateOrientation<br>差异内容：declare enum ImageRotateOrientation|component/image.d.ts|
|新增API|NA|类名：ImageRotateOrientation；<br>API声明：AUTO = 0<br>差异内容：AUTO = 0|component/image.d.ts|
|新增API|NA|类名：ImageRotateOrientation；<br>API声明：UP = 1<br>差异内容：UP = 1|component/image.d.ts|
|新增API|NA|类名：ImageRotateOrientation；<br>API声明：RIGHT = 2<br>差异内容：RIGHT = 2|component/image.d.ts|
|新增API|NA|类名：ImageRotateOrientation；<br>API声明：DOWN = 3<br>差异内容：DOWN = 3|component/image.d.ts|
|新增API|NA|类名：ImageRotateOrientation；<br>API声明：LEFT = 4<br>差异内容：LEFT = 4|component/image.d.ts|
|新增API|NA|类名：ImageAttribute；<br>API声明：orientation(orientation: ImageRotateOrientation): ImageAttribute;<br>差异内容：orientation(orientation: ImageRotateOrientation): ImageAttribute;|component/image.d.ts|
|新增API|NA|类名：ImageSpanAttribute；<br>API声明：colorFilter(filter: ColorFilter \| DrawingColorFilter): ImageSpanAttribute;<br>差异内容：colorFilter(filter: ColorFilter \| DrawingColorFilter): ImageSpanAttribute;|component/image_span.d.ts|
|新增API|NA|类名：ScrollBarAttribute；<br>API声明：enableNestedScroll(enabled: Optional\<boolean>): ScrollBarAttribute;<br>差异内容：enableNestedScroll(enabled: Optional\<boolean>): ScrollBarAttribute;|component/scroll_bar.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：caretColor(color: ResourceColor): TextAttribute;<br>差异内容：caretColor(color: ResourceColor): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：selectedBackgroundColor(color: ResourceColor): TextAttribute;<br>差异内容：selectedBackgroundColor(color: ResourceColor): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：LayoutManager；<br>API声明：getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array\<TextBox>;<br>差异内容：getRectsForRange(range: TextRange, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array\<TextBox>;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type RectWidthStyle = import('../api/@ohos.graphics.text').default.RectWidthStyle;<br>差异内容：declare type RectWidthStyle = import('../api/@ohos.graphics.text').default.RectWidthStyle;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type RectHeightStyle = import('../api/@ohos.graphics.text').default.RectHeightStyle;<br>差异内容：declare type RectHeightStyle = import('../api/@ohos.graphics.text').default.RectHeightStyle;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type TextBox = import('../api/@ohos.graphics.text').default.TextBox;<br>差异内容：declare type TextBox = import('../api/@ohos.graphics.text').default.TextBox;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type TextPickerScrollStopCallback = (value: string \| string[], index: number \| number[]) => void;<br>差异内容：declare type TextPickerScrollStopCallback = (value: string \| string[], index: number \| number[]) => void;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerAttribute；<br>API声明：onScrollStop(callback: TextPickerScrollStopCallback): TextPickerAttribute;<br>差异内容：onScrollStop(callback: TextPickerScrollStopCallback): TextPickerAttribute;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：onScrollStop?: Callback\<TextPickerResult>;<br>差异内容：onScrollStop?: Callback\<TextPickerResult>;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|component/text_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：enableHoverMode?: boolean;<br>差异内容：enableHoverMode?: boolean;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：hoverModeArea?: HoverModeAreaType;<br>差异内容：hoverModeArea?: HoverModeAreaType;|component/time_picker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ChainWeightOptions<br>差异内容：declare interface ChainWeightOptions|component/units.d.ts|
|新增API|NA|类名：ChainWeightOptions；<br>API声明：horizontal?: number;<br>差异内容：horizontal?: number;|component/units.d.ts|
|新增API|NA|类名：ChainWeightOptions；<br>API声明：vertical?: number;<br>差异内容：vertical?: number;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface AccessibilityOptions<br>差异内容：declare interface AccessibilityOptions|component/units.d.ts|
|新增API|NA|类名：AccessibilityOptions；<br>API声明：accessibilityPreferred?: boolean;<br>差异内容：accessibilityPreferred?: boolean;|component/units.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.advanced.MultiNavigation.d.ets<br>差异内容：ArkUI|api/@ohos.arkui.advanced.MultiNavigation.d.ets|
|函数变更|类名：Scroller；<br>API声明：scrollPage(value: {<br>        next: boolean;<br>    });<br>差异内容：value: {<br>        next: boolean;<br>    }|类名：Scroller；<br>API声明：scrollPage(value: ScrollPageOptions);<br>差异内容：value: ScrollPageOptions|component/scroll.d.ts|
|新增导出符号|类名：global；<br>API声明：export class MarqueeDynamicSyncScene<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export class MarqueeDynamicSyncScene|api/@ohos.arkui.UIContext.d.ts|
|新增导出符号|类名：global；<br>API声明：export const enum MarqueeDynamicSyncSceneType<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export const enum MarqueeDynamicSyncSceneType|api/@ohos.arkui.UIContext.d.ts|
