| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API访问级别变更|类名：global；<br>API声明：declare function animateToImmediately(value: AnimateParam, event: () => void): void;<br>差异内容：systemapi|类名：global；<br>API声明：declare function animateToImmediately(value: AnimateParam, event: () => void): void;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：BlurStyleOptions；<br>API声明：scale?: number;<br>差异内容：systemapi|类名：BlurStyleOptions；<br>API声明：scale?: number;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：CommonMethod；<br>API声明：linearGradientBlur(value: number, options: LinearGradientBlurOptions): T;<br>差异内容：systemapi|类名：CommonMethod；<br>API声明：linearGradientBlur(value: number, options: LinearGradientBlurOptions): T;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：CommonMethod；<br>API声明：systemBarEffect(): T;<br>差异内容：systemapi|类名：CommonMethod；<br>API声明：systemBarEffect(): T;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：CommonMethod；<br>API声明：useEffect(value: boolean): T;<br>差异内容：systemapi|类名：CommonMethod；<br>API声明：useEffect(value: boolean): T;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：CommonMethod；<br>API声明：key(value: string): T;<br>差异内容：systemapi|类名：CommonMethod；<br>API声明：key(value: string): T;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：CommonMethod；<br>API声明：sphericalEffect(value: number): T;<br>差异内容：systemapi|类名：CommonMethod；<br>API声明：sphericalEffect(value: number): T;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：CommonMethod；<br>API声明：lightUpEffect(value: number): T;<br>差异内容：systemapi|类名：CommonMethod；<br>API声明：lightUpEffect(value: number): T;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：CommonMethod；<br>API声明：pixelStretchEffect(options: PixelStretchEffectOptions): T;<br>差异内容：systemapi|类名：CommonMethod；<br>API声明：pixelStretchEffect(options: PixelStretchEffectOptions): T;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：CommonMethod；<br>API声明：backgroundBrightness(params: BackgroundBrightnessOptions): T;<br>差异内容：systemapi|类名：CommonMethod；<br>API声明：backgroundBrightness(params: BackgroundBrightnessOptions): T;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：global；<br>API声明：declare type FractionStop = [ number, number ];<br>差异内容：systemapi|类名：global；<br>API声明：declare type FractionStop = [<br>    number,<br>    number<br>];<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：global；<br>API声明：declare interface LinearGradientBlurOptions<br>差异内容：systemapi|类名：global；<br>API声明：declare interface LinearGradientBlurOptions<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：LinearGradientBlurOptions；<br>API声明：fractionStops: FractionStop[];<br>差异内容：systemapi|类名：LinearGradientBlurOptions；<br>API声明：fractionStops: FractionStop[];<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：LinearGradientBlurOptions；<br>API声明：direction: GradientDirection;<br>差异内容：systemapi|类名：LinearGradientBlurOptions；<br>API声明：direction: GradientDirection;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：global；<br>API声明：declare interface BackgroundBrightnessOptions<br>差异内容：systemapi|类名：global；<br>API声明：declare interface BackgroundBrightnessOptions<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：BackgroundBrightnessOptions；<br>API声明：rate: number;<br>差异内容：systemapi|类名：BackgroundBrightnessOptions；<br>API声明：rate: number;<br>差异内容：NA|component/common.d.ts|
|API访问级别变更|类名：BackgroundBrightnessOptions；<br>API声明：lightUpDegree: number;<br>差异内容：systemapi|类名：BackgroundBrightnessOptions；<br>API声明：lightUpDegree: number;<br>差异内容：NA|component/common.d.ts|
|API卡片权限变更|类名：CommonMethod；<br>API声明：renderGroup(value: boolean): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：renderGroup(value: boolean): T;<br>差异内容：form|component/common.d.ts|
|API卡片权限变更|类名：CommonMethod；<br>API声明：accessibilityGroup(value: boolean): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：accessibilityGroup(value: boolean): T;<br>差异内容：form|component/common.d.ts|
|API卡片权限变更|类名：CommonMethod；<br>API声明：accessibilityText(value: string): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：accessibilityText(value: string): T;<br>差异内容：form|component/common.d.ts|
|API卡片权限变更|类名：CommonMethod；<br>API声明：accessibilityDescription(value: string): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：accessibilityDescription(value: string): T;<br>差异内容：form|component/common.d.ts|
|API卡片权限变更|类名：CommonMethod；<br>API声明：accessibilityLevel(value: string): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：accessibilityLevel(value: string): T;<br>差异内容：form|component/common.d.ts|
|API卡片权限变更|类名：CommonMethod；<br>API声明：accessibilityVirtualNode(builder: CustomBuilder): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：accessibilityVirtualNode(builder: CustomBuilder): T;<br>差异内容：form|component/common.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare class ScrollableCommonMethod<br>差异内容：NA|类名：global；<br>API声明：declare class ScrollableCommonMethod<br>差异内容：form|component/common.d.ts|
|API卡片权限变更|类名：global；<br>API声明：interface SymbolGlyphInterface<br>差异内容：NA|类名：global；<br>API声明：interface SymbolGlyphInterface<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare enum SymbolRenderingStrategy<br>差异内容：NA|类名：global；<br>API声明：declare enum SymbolRenderingStrategy<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolRenderingStrategy；<br>API声明：SINGLE = 0<br>差异内容：NA|类名：SymbolRenderingStrategy；<br>API声明：SINGLE = 0<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_COLOR = 1<br>差异内容：NA|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_COLOR = 1<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_OPACITY = 2<br>差异内容：NA|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_OPACITY = 2<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare enum SymbolEffectStrategy<br>差异内容：NA|类名：global；<br>API声明：declare enum SymbolEffectStrategy<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolEffectStrategy；<br>API声明：NONE = 0<br>差异内容：NA|类名：SymbolEffectStrategy；<br>API声明：NONE = 0<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolEffectStrategy；<br>API声明：SCALE = 1<br>差异内容：NA|类名：SymbolEffectStrategy；<br>API声明：SCALE = 1<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolEffectStrategy；<br>API声明：HIERARCHICAL = 2<br>差异内容：NA|类名：SymbolEffectStrategy；<br>API声明：HIERARCHICAL = 2<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare class SymbolGlyphAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class SymbolGlyphAttribute<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolGlyphAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolGlyphAttribute;<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolGlyphAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolGlyphAttribute;<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolGlyphAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolGlyphAttribute;<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolGlyphAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolGlyphAttribute;<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：SymbolGlyphAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolGlyphAttribute;<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare const SymbolGlyph: SymbolGlyphInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const SymbolGlyph: SymbolGlyphInterface;<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare const SymbolGlyphInstance: SymbolGlyphAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const SymbolGlyphInstance: SymbolGlyphAttribute;<br>差异内容：form|component/symbolglyph.d.ts|
|API卡片权限变更|类名：global；<br>API声明：interface SymbolSpanInterface<br>差异内容：NA|类名：global；<br>API声明：interface SymbolSpanInterface<br>差异内容：form|component/symbol_span.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare class SymbolSpanAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class SymbolSpanAttribute<br>差异内容：form|component/symbol_span.d.ts|
|API卡片权限变更|类名：SymbolSpanAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolSpanAttribute;<br>差异内容：form|component/symbol_span.d.ts|
|API卡片权限变更|类名：SymbolSpanAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolSpanAttribute;<br>差异内容：form|component/symbol_span.d.ts|
|API卡片权限变更|类名：SymbolSpanAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolSpanAttribute;<br>差异内容：form|component/symbol_span.d.ts|
|API卡片权限变更|类名：SymbolSpanAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolSpanAttribute;<br>差异内容：form|component/symbol_span.d.ts|
|API卡片权限变更|类名：SymbolSpanAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolSpanAttribute;<br>差异内容：form|component/symbol_span.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare const SymbolSpan: SymbolSpanInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const SymbolSpan: SymbolSpanInterface;<br>差异内容：form|component/symbol_span.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare const SymbolSpanInstance: SymbolSpanAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const SymbolSpanInstance: SymbolSpanAttribute;<br>差异内容：form|component/symbol_span.d.ts|
|API卡片权限变更|类名：global；<br>API声明：declare namespace mediaquery<br>差异内容：NA|类名：global；<br>API声明：declare namespace mediaquery<br>差异内容：form|api/@ohos.mediaquery.d.ts|
|API卡片权限变更|类名：mediaquery；<br>API声明：interface MediaQueryResult<br>差异内容：NA|类名：mediaquery；<br>API声明：interface MediaQueryResult<br>差异内容：form|api/@ohos.mediaquery.d.ts|
|API卡片权限变更|类名：MediaQueryResult；<br>API声明：readonly matches: boolean;<br>差异内容：NA|类名：MediaQueryResult；<br>API声明：readonly matches: boolean;<br>差异内容：form|api/@ohos.mediaquery.d.ts|
|API卡片权限变更|类名：MediaQueryResult；<br>API声明：readonly media: string;<br>差异内容：NA|类名：MediaQueryResult；<br>API声明：readonly media: string;<br>差异内容：form|api/@ohos.mediaquery.d.ts|
|API卡片权限变更|类名：mediaquery；<br>API声明：interface MediaQueryListener<br>差异内容：NA|类名：mediaquery；<br>API声明：interface MediaQueryListener<br>差异内容：form|api/@ohos.mediaquery.d.ts|
|API卡片权限变更|类名：MediaQueryListener；<br>API声明：on(type: 'change', callback: Callback\<MediaQueryResult>): void;<br>差异内容：NA|类名：MediaQueryListener；<br>API声明：on(type: 'change', callback: Callback\<MediaQueryResult>): void;<br>差异内容：form|api/@ohos.mediaquery.d.ts|
|API卡片权限变更|类名：MediaQueryListener；<br>API声明：off(type: 'change', callback?: Callback\<MediaQueryResult>): void;<br>差异内容：NA|类名：MediaQueryListener；<br>API声明：off(type: 'change', callback?: Callback\<MediaQueryResult>): void;<br>差异内容：form|api/@ohos.mediaquery.d.ts|
|API卡片权限变更|类名：mediaquery；<br>API声明：function matchMediaSync(condition: string): MediaQueryListener;<br>差异内容：NA|类名：mediaquery；<br>API声明：function matchMediaSync(condition: string): MediaQueryListener;<br>差异内容：form|api/@ohos.mediaquery.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum XComponentType<br>差异内容：NA|类名：global；<br>API声明：declare enum XComponentType<br>差异内容：crossplatform|component/enums.d.ts|
|API跨平台权限变更|类名：XComponentType；<br>API声明：SURFACE<br>差异内容：NA|类名：XComponentType；<br>API声明：SURFACE<br>差异内容：crossplatform|component/enums.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class XComponentController<br>差异内容：NA|类名：global；<br>API声明：declare class XComponentController<br>差异内容：crossplatform|component/xcomponent.d.ts|
|API跨平台权限变更|类名：XComponentController；<br>API声明：getXComponentSurfaceId(): string;<br>差异内容：NA|类名：XComponentController；<br>API声明：getXComponentSurfaceId(): string;<br>差异内容：crossplatform|component/xcomponent.d.ts|
|API跨平台权限变更|类名：XComponentController；<br>API声明：getXComponentContext(): Object;<br>差异内容：NA|类名：XComponentController；<br>API声明：getXComponentContext(): Object;<br>差异内容：crossplatform|component/xcomponent.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：interface XComponentInterface<br>差异内容：NA|类名：global；<br>API声明：interface XComponentInterface<br>差异内容：crossplatform|component/xcomponent.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class XComponentAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class XComponentAttribute<br>差异内容：crossplatform|component/xcomponent.d.ts|
|API跨平台权限变更|类名：XComponentAttribute；<br>API声明：onLoad(callback: (event?: object) => void): XComponentAttribute;<br>差异内容：NA|类名：XComponentAttribute；<br>API声明：onLoad(callback: (event?: object) => void): XComponentAttribute;<br>差异内容：crossplatform|component/xcomponent.d.ts|
|API跨平台权限变更|类名：XComponentAttribute；<br>API声明：onDestroy(event: () => void): XComponentAttribute;<br>差异内容：NA|类名：XComponentAttribute；<br>API声明：onDestroy(event: () => void): XComponentAttribute;<br>差异内容：crossplatform|component/xcomponent.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare const XComponent: XComponentInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const XComponent: XComponentInterface;<br>差异内容：crossplatform|component/xcomponent.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare const XComponentInstance: XComponentAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const XComponentInstance: XComponentAttribute;<br>差异内容：crossplatform|component/xcomponent.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace componentUtils<br>差异内容：NA|类名：global；<br>API声明：declare namespace componentUtils<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：componentUtils；<br>API声明：interface ComponentInfo<br>差异内容：NA|类名：componentUtils；<br>API声明：interface ComponentInfo<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ComponentInfo；<br>API声明：size: Size;<br>差异内容：NA|类名：ComponentInfo；<br>API声明：size: Size;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ComponentInfo；<br>API声明：localOffset: Offset;<br>差异内容：NA|类名：ComponentInfo；<br>API声明：localOffset: Offset;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ComponentInfo；<br>API声明：windowOffset: Offset;<br>差异内容：NA|类名：ComponentInfo；<br>API声明：windowOffset: Offset;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ComponentInfo；<br>API声明：screenOffset: Offset;<br>差异内容：NA|类名：ComponentInfo；<br>API声明：screenOffset: Offset;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ComponentInfo；<br>API声明：translate: TranslateResult;<br>差异内容：NA|类名：ComponentInfo；<br>API声明：translate: TranslateResult;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ComponentInfo；<br>API声明：scale: ScaleResult;<br>差异内容：NA|类名：ComponentInfo；<br>API声明：scale: ScaleResult;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ComponentInfo；<br>API声明：rotate: RotateResult;<br>差异内容：NA|类名：ComponentInfo；<br>API声明：rotate: RotateResult;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ComponentInfo；<br>API声明：transform: Matrix4Result;<br>差异内容：NA|类名：ComponentInfo；<br>API声明：transform: Matrix4Result;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：componentUtils；<br>API声明：interface Size<br>差异内容：NA|类名：componentUtils；<br>API声明：interface Size<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：Size；<br>API声明：width: number;<br>差异内容：NA|类名：Size；<br>API声明：width: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：Size；<br>API声明：height: number;<br>差异内容：NA|类名：Size；<br>API声明：height: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：componentUtils；<br>API声明：interface Offset<br>差异内容：NA|类名：componentUtils；<br>API声明：interface Offset<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：Offset；<br>API声明：x: number;<br>差异内容：NA|类名：Offset；<br>API声明：x: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：Offset；<br>API声明：y: number;<br>差异内容：NA|类名：Offset；<br>API声明：y: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：componentUtils；<br>API声明：interface TranslateResult<br>差异内容：NA|类名：componentUtils；<br>API声明：interface TranslateResult<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：TranslateResult；<br>API声明：x: number;<br>差异内容：NA|类名：TranslateResult；<br>API声明：x: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：TranslateResult；<br>API声明：y: number;<br>差异内容：NA|类名：TranslateResult；<br>API声明：y: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：TranslateResult；<br>API声明：z: number;<br>差异内容：NA|类名：TranslateResult；<br>API声明：z: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：componentUtils；<br>API声明：interface ScaleResult<br>差异内容：NA|类名：componentUtils；<br>API声明：interface ScaleResult<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ScaleResult；<br>API声明：x: number;<br>差异内容：NA|类名：ScaleResult；<br>API声明：x: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ScaleResult；<br>API声明：y: number;<br>差异内容：NA|类名：ScaleResult；<br>API声明：y: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ScaleResult；<br>API声明：z: number;<br>差异内容：NA|类名：ScaleResult；<br>API声明：z: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ScaleResult；<br>API声明：centerX: number;<br>差异内容：NA|类名：ScaleResult；<br>API声明：centerX: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：ScaleResult；<br>API声明：centerY: number;<br>差异内容：NA|类名：ScaleResult；<br>API声明：centerY: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：componentUtils；<br>API声明：interface RotateResult<br>差异内容：NA|类名：componentUtils；<br>API声明：interface RotateResult<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：RotateResult；<br>API声明：x: number;<br>差异内容：NA|类名：RotateResult；<br>API声明：x: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：RotateResult；<br>API声明：y: number;<br>差异内容：NA|类名：RotateResult；<br>API声明：y: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：RotateResult；<br>API声明：z: number;<br>差异内容：NA|类名：RotateResult；<br>API声明：z: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：RotateResult；<br>API声明：centerX: number;<br>差异内容：NA|类名：RotateResult；<br>API声明：centerX: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：RotateResult；<br>API声明：centerY: number;<br>差异内容：NA|类名：RotateResult；<br>API声明：centerY: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：RotateResult；<br>API声明：angle: number;<br>差异内容：NA|类名：RotateResult；<br>API声明：angle: number;<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：componentUtils；<br>API声明：type Matrix4Result = [<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number<br>    ];<br>差异内容：NA|类名：componentUtils；<br>API声明：type Matrix4Result = [<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number,<br>        number<br>    ];<br>差异内容：crossplatform|api/@ohos.arkui.componentUtils.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export class DrawableDescriptor<br>差异内容：NA|类名：global；<br>API声明：export class DrawableDescriptor<br>差异内容：crossplatform|api/@ohos.arkui.drawableDescriptor.d.ts|
|API跨平台权限变更|类名：DrawableDescriptor；<br>API声明：getPixelMap(): image.PixelMap;<br>差异内容：NA|类名：DrawableDescriptor；<br>API声明：getPixelMap(): image.PixelMap;<br>差异内容：crossplatform|api/@ohos.arkui.drawableDescriptor.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export class LayeredDrawableDescriptor<br>差异内容：NA|类名：global；<br>API声明：export class LayeredDrawableDescriptor<br>差异内容：crossplatform|api/@ohos.arkui.drawableDescriptor.d.ts|
|API跨平台权限变更|类名：LayeredDrawableDescriptor；<br>API声明：getForeground(): DrawableDescriptor;<br>差异内容：NA|类名：LayeredDrawableDescriptor；<br>API声明：getForeground(): DrawableDescriptor;<br>差异内容：crossplatform|api/@ohos.arkui.drawableDescriptor.d.ts|
|API跨平台权限变更|类名：LayeredDrawableDescriptor；<br>API声明：getBackground(): DrawableDescriptor;<br>差异内容：NA|类名：LayeredDrawableDescriptor；<br>API声明：getBackground(): DrawableDescriptor;<br>差异内容：crossplatform|api/@ohos.arkui.drawableDescriptor.d.ts|
|API跨平台权限变更|类名：LayeredDrawableDescriptor；<br>API声明：getMask(): DrawableDescriptor;<br>差异内容：NA|类名：LayeredDrawableDescriptor；<br>API声明：getMask(): DrawableDescriptor;<br>差异内容：crossplatform|api/@ohos.arkui.drawableDescriptor.d.ts|
|API跨平台权限变更|类名：LayeredDrawableDescriptor；<br>API声明：static getMaskClipPath(): string;<br>差异内容：NA|类名：LayeredDrawableDescriptor；<br>API声明：static getMaskClipPath(): string;<br>差异内容：crossplatform|api/@ohos.arkui.drawableDescriptor.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace font<br>差异内容：NA|类名：global；<br>API声明：declare namespace font<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：font；<br>API声明：interface FontOptions<br>差异内容：NA|类名：font；<br>API声明：interface FontOptions<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontOptions；<br>API声明：familyName: string \| Resource;<br>差异内容：NA|类名：FontOptions；<br>API声明：familyName: string \| Resource;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontOptions；<br>API声明：familySrc: string \| Resource;<br>差异内容：NA|类名：FontOptions；<br>API声明：familySrc: string \| Resource;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：font；<br>API声明：interface FontInfo<br>差异内容：NA|类名：font；<br>API声明：interface FontInfo<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：path: string;<br>差异内容：NA|类名：FontInfo；<br>API声明：path: string;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：postScriptName: string;<br>差异内容：NA|类名：FontInfo；<br>API声明：postScriptName: string;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：fullName: string;<br>差异内容：NA|类名：FontInfo；<br>API声明：fullName: string;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：family: string;<br>差异内容：NA|类名：FontInfo；<br>API声明：family: string;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：subfamily: string;<br>差异内容：NA|类名：FontInfo；<br>API声明：subfamily: string;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：weight: number;<br>差异内容：NA|类名：FontInfo；<br>API声明：weight: number;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：width: number;<br>差异内容：NA|类名：FontInfo；<br>API声明：width: number;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：italic: boolean;<br>差异内容：NA|类名：FontInfo；<br>API声明：italic: boolean;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：monoSpace: boolean;<br>差异内容：NA|类名：FontInfo；<br>API声明：monoSpace: boolean;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：FontInfo；<br>API声明：symbolic: boolean;<br>差异内容：NA|类名：FontInfo；<br>API声明：symbolic: boolean;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：font；<br>API声明：function registerFont(options: FontOptions): void;<br>差异内容：NA|类名：font；<br>API声明：function registerFont(options: FontOptions): void;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：font；<br>API声明：function getSystemFontList(): Array\<string>;<br>差异内容：NA|类名：font；<br>API声明：function getSystemFontList(): Array\<string>;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：font；<br>API声明：function getFontByName(fontName: string): FontInfo;<br>差异内容：NA|类名：font；<br>API声明：function getFontByName(fontName: string): FontInfo;<br>差异内容：crossplatform|api/@ohos.font.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：textContent: string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：textContent: string \| Resource;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：constraintWidth?: number \| string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：constraintWidth?: number \| string \| Resource;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：fontStyle?: number \| FontStyle;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：fontStyle?: number \| FontStyle;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：fontWeight?: number \| string \| FontWeight;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：fontWeight?: number \| string \| FontWeight;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：fontFamily?: string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：fontFamily?: string \| Resource;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：letterSpacing?: number \| string;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：letterSpacing?: number \| string;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：textAlign?: number \| TextAlign;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：textAlign?: number \| TextAlign;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：overflow?: number \| TextOverflow;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：overflow?: number \| TextOverflow;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：maxLines?: number;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：maxLines?: number;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：lineHeight?: number \| string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：lineHeight?: number \| string \| Resource;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：baselineOffset?: number \| string;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：baselineOffset?: number \| string;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：MeasureOptions；<br>API声明：textCase?: number \| TextCase;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：textCase?: number \| TextCase;<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：export default class MeasureText<br>差异内容：NA|类名：global；<br>API声明：export default class MeasureText<br>差异内容：crossplatform|api/@ohos.measure.d.ts|
|API跨平台权限变更|类名：ShowToastOptions；<br>API声明：showMode?: ToastShowMode;<br>差异内容：NA|类名：ShowToastOptions；<br>API声明：showMode?: ToastShowMode;<br>差异内容：crossplatform|api/@ohos.promptAction.d.ts|
|API跨平台权限变更|类名：promptAction；<br>API声明：export enum ToastShowMode<br>差异内容：NA|类名：promptAction；<br>API声明：export enum ToastShowMode<br>差异内容：crossplatform|api/@ohos.promptAction.d.ts|
|API跨平台权限变更|类名：ToastShowMode；<br>API声明：DEFAULT = 0<br>差异内容：NA|类名：ToastShowMode；<br>API声明：DEFAULT = 0<br>差异内容：crossplatform|api/@ohos.promptAction.d.ts|
|API跨平台权限变更|类名：ToastShowMode；<br>API声明：TOP_MOST = 1<br>差异内容：NA|类名：ToastShowMode；<br>API声明：TOP_MOST = 1<br>差异内容：crossplatform|api/@ohos.promptAction.d.ts|
|API跨平台权限变更|类名：window；<br>API声明：enum AvoidAreaType<br>差异内容：NA|类名：window；<br>API声明：enum AvoidAreaType<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：AvoidAreaType；<br>API声明：TYPE_SYSTEM<br>差异内容：NA|类名：AvoidAreaType；<br>API声明：TYPE_SYSTEM<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：AvoidAreaType；<br>API声明：TYPE_CUTOUT<br>差异内容：NA|类名：AvoidAreaType；<br>API声明：TYPE_CUTOUT<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：AvoidAreaType；<br>API声明：TYPE_SYSTEM_GESTURE<br>差异内容：NA|类名：AvoidAreaType；<br>API声明：TYPE_SYSTEM_GESTURE<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：AvoidAreaType；<br>API声明：TYPE_KEYBOARD<br>差异内容：NA|类名：AvoidAreaType；<br>API声明：TYPE_KEYBOARD<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：AvoidAreaType；<br>API声明：TYPE_NAVIGATION_INDICATOR<br>差异内容：NA|类名：AvoidAreaType；<br>API声明：TYPE_NAVIGATION_INDICATOR<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：window；<br>API声明：interface AvoidArea<br>差异内容：NA|类名：window；<br>API声明：interface AvoidArea<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：AvoidArea；<br>API声明：leftRect: Rect;<br>差异内容：NA|类名：AvoidArea；<br>API声明：leftRect: Rect;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：AvoidArea；<br>API声明：topRect: Rect;<br>差异内容：NA|类名：AvoidArea；<br>API声明：topRect: Rect;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：AvoidArea；<br>API声明：rightRect: Rect;<br>差异内容：NA|类名：AvoidArea；<br>API声明：rightRect: Rect;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：AvoidArea；<br>API声明：bottomRect: Rect;<br>差异内容：NA|类名：AvoidArea；<br>API声明：bottomRect: Rect;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：window；<br>API声明：type SpecificSystemBar = 'status' \| 'navigation' \| 'navigationIndicator';<br>差异内容：NA|类名：window；<br>API声明：type SpecificSystemBar = 'status' \| 'navigation' \| 'navigationIndicator';<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：Window；<br>API声明：getWindowAvoidArea(type: AvoidAreaType): AvoidArea;<br>差异内容：NA|类名：Window；<br>API声明：getWindowAvoidArea(type: AvoidAreaType): AvoidArea;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：Window；<br>API声明：setSpecificSystemBarEnabled(name: SpecificSystemBar, enable: boolean): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setSpecificSystemBarEnabled(name: SpecificSystemBar, enable: boolean, enableAnimation?: boolean): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：Window；<br>API声明：on(type: 'windowSizeChange', callback: Callback\<Size>): void;<br>差异内容：NA|类名：Window；<br>API声明：on(type: 'windowSizeChange', callback: Callback\<Size>): void;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API跨平台权限变更|类名：Window；<br>API声明：off(type: 'windowSizeChange', callback?: Callback\<Size>): void;<br>差异内容：NA|类名：Window；<br>API声明：off(type: 'windowSizeChange', callback?: Callback\<Size>): void;<br>差异内容：crossplatform|api/@ohos.window.d.ts|
|API废弃版本变更|类名：global；<br>API声明：export declare class XComponentNode<br>差异内容：NA|类名：global；<br>API声明：export declare class XComponentNode<br>差异内容：12|api/arkui/XComponentNode.d.ts|
|API废弃版本变更|类名：XComponentNode；<br>API声明：onCreate(event?: Object): void;<br>差异内容：NA|类名：XComponentNode；<br>API声明：onCreate(event?: Object): void;<br>差异内容：12|api/arkui/XComponentNode.d.ts|
|API废弃版本变更|类名：XComponentNode；<br>API声明：onDestroy(): void;<br>差异内容：NA|类名：XComponentNode；<br>API声明：onDestroy(): void;<br>差异内容：12|api/arkui/XComponentNode.d.ts|
|API废弃版本变更|类名：XComponentNode；<br>API声明：changeRenderType(type: NodeRenderType): boolean;<br>差异内容：NA|类名：XComponentNode；<br>API声明：changeRenderType(type: NodeRenderType): boolean;<br>差异内容：12|api/arkui/XComponentNode.d.ts|
|API废弃版本变更|类名：CommonMethod；<br>API声明：clip(value: boolean \| CircleAttribute \| EllipseAttribute \| PathAttribute \| RectAttribute): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：clip(value: boolean \| CircleAttribute \| EllipseAttribute \| PathAttribute \| RectAttribute): T;<br>差异内容：12|component/common.d.ts|
|API废弃版本变更|类名：CommonMethod；<br>API声明：mask(value: CircleAttribute \| EllipseAttribute \| PathAttribute \| RectAttribute \| ProgressMask): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：mask(value: CircleAttribute \| EllipseAttribute \| PathAttribute \| RectAttribute \| ProgressMask): T;<br>差异内容：12|component/common.d.ts|
|API废弃版本变更|类名：ScrollableCommonMethod；<br>API声明：onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T;<br>差异内容：NA|类名：ScrollableCommonMethod；<br>API声明：onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T;<br>差异内容：12|component/common.d.ts|
|API废弃版本变更|类名：CopyOptions；<br>API声明：CROSS_DEVICE = 3<br>差异内容：NA|类名：CopyOptions；<br>API声明：CROSS_DEVICE = 3<br>差异内容：12|component/enums.d.ts|
|API废弃版本变更|类名：XComponentType；<br>API声明：COMPONENT<br>差异内容：NA|类名：XComponentType；<br>API声明：COMPONENT<br>差异内容：12|component/enums.d.ts|
|API废弃版本变更|类名：GridAttribute；<br>API声明：onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): GridAttribute;<br>差异内容：NA|类名：GridAttribute；<br>API声明：onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): GridAttribute;<br>差异内容：12|component/grid.d.ts|
|API废弃版本变更|类名：ListAttribute；<br>API声明：onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): ListAttribute;<br>差异内容：NA|类名：ListAttribute；<br>API声明：onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): ListAttribute;<br>差异内容：12|component/list.d.ts|
|API废弃版本变更|类名：global；<br>API声明：declare enum PanelMode<br>差异内容：NA|类名：global；<br>API声明：declare enum PanelMode<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelMode；<br>API声明：Mini<br>差异内容：NA|类名：PanelMode；<br>API声明：Mini<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelMode；<br>API声明：Half<br>差异内容：NA|类名：PanelMode；<br>API声明：Half<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelMode；<br>API声明：Full<br>差异内容：NA|类名：PanelMode；<br>API声明：Full<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：global；<br>API声明：declare enum PanelType<br>差异内容：NA|类名：global；<br>API声明：declare enum PanelType<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelType；<br>API声明：Minibar = 0<br>差异内容：NA|类名：PanelType；<br>API声明：Minibar = 0<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelType；<br>API声明：Foldable = 1<br>差异内容：NA|类名：PanelType；<br>API声明：Foldable = 1<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelType；<br>API声明：Temporary = 2<br>差异内容：NA|类名：PanelType；<br>API声明：Temporary = 2<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelType；<br>API声明：CUSTOM = 3<br>差异内容：NA|类名：PanelType；<br>API声明：CUSTOM = 3<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：global；<br>API声明：declare enum PanelHeight<br>差异内容：NA|类名：global；<br>API声明：declare enum PanelHeight<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelHeight；<br>API声明：WRAP_CONTENT = 'wrapContent'<br>差异内容：NA|类名：PanelHeight；<br>API声明：WRAP_CONTENT = 'wrapContent'<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：global；<br>API声明：interface PanelInterface<br>差异内容：NA|类名：global；<br>API声明：interface PanelInterface<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：global；<br>API声明：declare class PanelAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class PanelAttribute<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：mode(value: PanelMode): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：mode(value: PanelMode): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：type(value: PanelType): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：type(value: PanelType): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：dragBar(value: boolean): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：dragBar(value: boolean): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：customHeight(value: Dimension \| PanelHeight): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：customHeight(value: Dimension \| PanelHeight): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：fullHeight(value: number \| string): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：fullHeight(value: number \| string): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：halfHeight(value: number \| string): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：halfHeight(value: number \| string): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：miniHeight(value: number \| string): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：miniHeight(value: number \| string): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：show(value: boolean): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：show(value: boolean): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：backgroundMask(color: ResourceColor): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：backgroundMask(color: ResourceColor): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：showCloseIcon(value: boolean): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：showCloseIcon(value: boolean): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：onChange(event: (<br>    /**<br>     * Width of content area.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @since 7<br>     */<br>    /**<br>     * Width of content area.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @atomicservice<br>     * @since 11<br>     */<br>    width: number, <br>    /**<br>     * Height of content area.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @since 7<br>     */<br>    /**<br>     * Height of content area.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @atomicservice<br>     * @since 11<br>     */<br>    height: number, <br>    /**<br>     * Initial state.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @since 7<br>     */<br>    /**<br>     * Initial state.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @atomicservice<br>     * @since 11<br>     */<br>    mode: PanelMode) => void): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：onChange(event: (<br>    /**<br>     * Width of content area.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @since 7<br>     */<br>    /**<br>     * Width of content area.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @atomicservice<br>     * @since 11<br>     * @deprecated since 12<br>     */<br>    width: number, <br>    /**<br>     * Height of content area.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @since 7<br>     */<br>    /**<br>     * Height of content area.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @atomicservice<br>     * @since 11<br>     * @deprecated since 12<br>     */<br>    height: number, <br>    /**<br>     * Initial state.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @since 7<br>     */<br>    /**<br>     * Initial state.<br>     *<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @atomicservice<br>     * @since 11<br>     * @deprecated since 12<br>     */<br>    mode: PanelMode) => void): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：PanelAttribute；<br>API声明：onHeightChange(callback: (value: number) => void): PanelAttribute;<br>差异内容：NA|类名：PanelAttribute；<br>API声明：onHeightChange(callback: (value: number) => void): PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：global；<br>API声明：declare const Panel: PanelInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const Panel: PanelInterface;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：global；<br>API声明：declare const PanelInstance: PanelAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const PanelInstance: PanelAttribute;<br>差异内容：12|component/panel.d.ts|
|API废弃版本变更|类名：ScrollAttribute；<br>API声明：onScroll(event: (xOffset: number, yOffset: number) => void): ScrollAttribute;<br>差异内容：NA|类名：ScrollAttribute；<br>API声明：onScroll(event: (xOffset: number, yOffset: number) => void): ScrollAttribute;<br>差异内容：12|component/scroll.d.ts|
|API废弃版本变更|类名：SwiperDisplayMode；<br>API声明：AUTO_LINEAR<br>差异内容：NA|类名：SwiperDisplayMode；<br>API声明：AUTO_LINEAR<br>差异内容：12|component/swiper.d.ts|
|API废弃版本变更|类名：XComponentController；<br>API声明：setXComponentSurfaceSize(value: {<br>        surfaceWidth: number;<br>        surfaceHeight: number;<br>    }): void;<br>差异内容：NA|类名：XComponentController；<br>API声明：setXComponentSurfaceSize(value: {<br>        surfaceWidth: number;<br>        surfaceHeight: number;<br>    }): void;<br>差异内容：12|component/xcomponent.d.ts|
|API废弃版本变更|类名：AnimatorResult；<br>API声明：onframe: (progress: number) => void;<br>差异内容：NA|类名：AnimatorResult；<br>API声明：onframe: (progress: number) => void;<br>差异内容：12|api/@ohos.animator.d.ts|
|API废弃版本变更|类名：AnimatorResult；<br>API声明：onfinish: () => void;<br>差异内容：NA|类名：AnimatorResult；<br>API声明：onfinish: () => void;<br>差异内容：12|api/@ohos.animator.d.ts|
|API废弃版本变更|类名：AnimatorResult；<br>API声明：oncancel: () => void;<br>差异内容：NA|类名：AnimatorResult；<br>API声明：oncancel: () => void;<br>差异内容：12|api/@ohos.animator.d.ts|
|API废弃版本变更|类名：AnimatorResult；<br>API声明：onrepeat: () => void;<br>差异内容：NA|类名：AnimatorResult；<br>API声明：onrepeat: () => void;<br>差异内容：12|api/@ohos.animator.d.ts|
|API废弃版本变更|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：12|api/@ohos.window.d.ts|
|API废弃版本变更|类名：Window；<br>API声明：setWindowSystemBarEnable(names: Array\<'status' \| 'navigation'>, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowSystemBarEnable(names: Array\<'status' \| 'navigation'>, callback: AsyncCallback\<void>): void;<br>差异内容：12|api/@ohos.window.d.ts|
|API废弃版本变更|类名：Window；<br>API声明：setWindowSystemBarProperties(systemBarProperties: SystemBarProperties, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowSystemBarProperties(systemBarProperties: SystemBarProperties, callback: AsyncCallback\<void>): void;<br>差异内容：12|api/@ohos.window.d.ts|
|新增错误码|类名：window；<br>API声明：function createWindow(config: Configuration, callback: AsyncCallback\<Window>): void;<br>差异内容：NA|类名：window；<br>API声明：function createWindow(config: Configuration, callback: AsyncCallback\<Window>): void;<br>差异内容：1300002,1300004,801|api/@ohos.window.d.ts|
|新增错误码|类名：window；<br>API声明：function createWindow(config: Configuration): Promise\<Window>;<br>差异内容：NA|类名：window；<br>API声明：function createWindow(config: Configuration): Promise\<Window>;<br>差异内容：1300002,1300004,801|api/@ohos.window.d.ts|
|删除错误码|类名：display；<br>API声明：function isFoldable(): boolean;<br>差异内容：801|类名：display；<br>API声明：function isFoldable(): boolean;<br>差异内容：NA|api/@ohos.display.d.ts|
|删除错误码|类名：display；<br>API声明：function getFoldStatus(): FoldStatus;<br>差异内容：801|类名：display；<br>API声明：function getFoldStatus(): FoldStatus;<br>差异内容：NA|api/@ohos.display.d.ts|
|删除错误码|类名：display；<br>API声明：function on(type: 'foldStatusChange', callback: Callback\<FoldStatus>): void;<br>差异内容：801|类名：display；<br>API声明：function on(type: 'foldStatusChange', callback: Callback\<FoldStatus>): void;<br>差异内容：NA|api/@ohos.display.d.ts|
|删除错误码|类名：display；<br>API声明：function off(type: 'foldStatusChange', callback?: Callback\<FoldStatus>): void;<br>差异内容：801|类名：display；<br>API声明：function off(type: 'foldStatusChange', callback?: Callback\<FoldStatus>): void;<br>差异内容：NA|api/@ohos.display.d.ts|
|删除错误码|类名：display；<br>API声明：function getFoldDisplayMode(): FoldDisplayMode;<br>差异内容：801|类名：display；<br>API声明：function getFoldDisplayMode(): FoldDisplayMode;<br>差异内容：NA|api/@ohos.display.d.ts|
|删除错误码|类名：display；<br>API声明：function on(type: 'foldDisplayModeChange', callback: Callback\<FoldDisplayMode>): void;<br>差异内容：801|类名：display；<br>API声明：function on(type: 'foldDisplayModeChange', callback: Callback\<FoldDisplayMode>): void;<br>差异内容：NA|api/@ohos.display.d.ts|
|删除错误码|类名：display；<br>API声明：function off(type: 'foldDisplayModeChange', callback?: Callback\<FoldDisplayMode>): void;<br>差异内容：801|类名：display；<br>API声明：function off(type: 'foldDisplayModeChange', callback?: Callback\<FoldDisplayMode>): void;<br>差异内容：NA|api/@ohos.display.d.ts|
|删除错误码|类名：display；<br>API声明：function getCurrentFoldCreaseRegion(): FoldCreaseRegion;<br>差异内容：801|类名：display；<br>API声明：function getCurrentFoldCreaseRegion(): FoldCreaseRegion;<br>差异内容：NA|api/@ohos.display.d.ts|
|删除错误码|类名：Window；<br>API声明：getUIContext(): UIContext;<br>差异内容：401|类名：Window；<br>API声明：getUIContext(): UIContext;<br>差异内容：NA|api/@ohos.window.d.ts|
|权限变更|类名：window；<br>API声明：function createWindow(config: Configuration, callback: AsyncCallback\<Window>): void;<br>差异内容：NA|类名：window；<br>API声明：function createWindow(config: Configuration, callback: AsyncCallback\<Window>): void;<br>差异内容：ohos.permission.SYSTEM_FLOAT_WINDOW|api/@ohos.window.d.ts|
|权限变更|类名：window；<br>API声明：function createWindow(config: Configuration): Promise\<Window>;<br>差异内容：NA|类名：window；<br>API声明：function createWindow(config: Configuration): Promise\<Window>;<br>差异内容：ohos.permission.SYSTEM_FLOAT_WINDOW|api/@ohos.window.d.ts|
|权限变更|类名：WindowType；<br>API声明：TYPE_FLOAT<br>差异内容：ohos.permission.SYSTEM_FLOAT_WINDOW|类名：WindowType；<br>API声明：TYPE_FLOAT<br>差异内容：NA|api/@ohos.window.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：dragPreviewOptions(value: DragPreviewOptions): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：dragPreviewOptions(value: DragPreviewOptions, options?: DragInteractionOptions): T;<br>差异内容：options?: DragInteractionOptions|component/common.d.ts|
|函数变更|类名：NavDestinationAttribute；<br>API声明：title(value: string \| CustomBuilder \| NavDestinationCommonTitle \| NavDestinationCustomTitle): NavDestinationAttribute;<br>差异内容：NA|类名：NavDestinationAttribute；<br>API声明：title(value: string \| CustomBuilder \| NavDestinationCommonTitle \| NavDestinationCustomTitle, options?: NavigationTitleOptions): NavDestinationAttribute;<br>差异内容：options?: NavigationTitleOptions|component/nav_destination.d.ts|
|函数变更|类名：RichEditorAttribute；<br>API声明：customKeyboard(value: CustomBuilder): RichEditorAttribute;<br>差异内容：NA|类名：RichEditorAttribute；<br>API声明：customKeyboard(value: CustomBuilder, options?: KeyboardOptions): RichEditorAttribute;<br>差异内容：options?: KeyboardOptions|component/rich_editor.d.ts|
|函数变更|类名：Scroller；<br>API声明：scrollEdge(value: Edge);<br>差异内容：NA|类名：Scroller；<br>API声明：scrollEdge(value: Edge, options?: ScrollEdgeOptions);<br>差异内容：options?: ScrollEdgeOptions|component/scroll.d.ts|
|函数变更|类名：Scroller；<br>API声明：scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign);<br>差异内容：NA|类名：Scroller；<br>API声明：scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions);<br>差异内容：options?: ScrollToIndexOptions|component/scroll.d.ts|
|函数变更|类名：SearchAttribute；<br>API声明：customKeyboard(value: CustomBuilder): SearchAttribute;<br>差异内容：NA|类名：SearchAttribute；<br>API声明：customKeyboard(value: CustomBuilder, options?: KeyboardOptions): SearchAttribute;<br>差异内容：options?: KeyboardOptions|component/search.d.ts|
|函数变更|类名：SwiperAttribute；<br>API声明：prevMargin(value: Length): SwiperAttribute;<br>差异内容：NA|类名：SwiperAttribute；<br>API声明：prevMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute;<br>差异内容：ignoreBlank?: boolean|component/swiper.d.ts|
|函数变更|类名：SwiperAttribute；<br>API声明：nextMargin(value: Length): SwiperAttribute;<br>差异内容：NA|类名：SwiperAttribute；<br>API声明：nextMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute;<br>差异内容：ignoreBlank?: boolean|component/swiper.d.ts|
|函数变更|类名：TextAreaController；<br>API声明：setTextSelection(selectionStart: number, selectionEnd: number): void;<br>差异内容：NA|类名：TextAreaController；<br>API声明：setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void;<br>差异内容：options?: SelectionOptions|component/text_area.d.ts|
|函数变更|类名：TextAreaAttribute；<br>API声明：customKeyboard(value: CustomBuilder): TextAreaAttribute;<br>差异内容：NA|类名：TextAreaAttribute；<br>API声明：customKeyboard(value: CustomBuilder, options?: KeyboardOptions): TextAreaAttribute;<br>差异内容：options?: KeyboardOptions|component/text_area.d.ts|
|函数变更|类名：TextInputController；<br>API声明：setTextSelection(selectionStart: number, selectionEnd: number): void;<br>差异内容：NA|类名：TextInputController；<br>API声明：setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void;<br>差异内容：options?: SelectionOptions|component/text_input.d.ts|
|函数变更|类名：TextInputAttribute；<br>API声明：customKeyboard(value: CustomBuilder): TextInputAttribute;<br>差异内容：NA|类名：TextInputAttribute；<br>API声明：customKeyboard(value: CustomBuilder, options?: KeyboardOptions): TextInputAttribute;<br>差异内容：options?: KeyboardOptions|component/text_input.d.ts|
|函数变更|类名：componentSnapshot；<br>API声明：function get(id: string, callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：NA|类名：componentSnapshot；<br>API声明：function get(id: string, callback: AsyncCallback\<image.PixelMap>, options?: SnapshotOptions): void;<br>差异内容：options?: SnapshotOptions|api/@ohos.arkui.componentSnapshot.d.ts|
|函数变更|类名：componentSnapshot；<br>API声明：function get(id: string): Promise\<image.PixelMap>;<br>差异内容：NA|类名：componentSnapshot；<br>API声明：function get(id: string, options?: SnapshotOptions): Promise\<image.PixelMap>;<br>差异内容：options?: SnapshotOptions|api/@ohos.arkui.componentSnapshot.d.ts|
|函数变更|类名：componentSnapshot；<br>API声明：function createFromBuilder(builder: CustomBuilder, callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：NA|类名：componentSnapshot；<br>API声明：function createFromBuilder(builder: CustomBuilder, callback: AsyncCallback\<image.PixelMap>, delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions): void;<br>差异内容：delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions|api/@ohos.arkui.componentSnapshot.d.ts|
|函数变更|类名：componentSnapshot；<br>API声明：function createFromBuilder(builder: CustomBuilder): Promise\<image.PixelMap>;<br>差异内容：NA|类名：componentSnapshot；<br>API声明：function createFromBuilder(builder: CustomBuilder, delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions): Promise\<image.PixelMap>;<br>差异内容：delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions|api/@ohos.arkui.componentSnapshot.d.ts|
|函数变更|类名：Window；<br>API声明：setSpecificSystemBarEnabled(name: SpecificSystemBar, enable: boolean): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setSpecificSystemBarEnabled(name: SpecificSystemBar, enable: boolean, enableAnimation?: boolean): Promise\<void>;<br>差异内容：enableAnimation?: boolean|api/@ohos.window.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：linearGradient(value: {<br>    angle?: number \| string;<br>    direction?: GradientDirection;<br>    colors: Array\<any>;<br>    repeating?: boolean;<br>  }): T;<br>差异内容：value: {<br>    angle?: number \| string;<br>    direction?: GradientDirection;<br>    colors: Array\<any>;<br>    repeating?: boolean;<br>  }|类名：CommonMethod；<br>API声明：linearGradient(value: {<br>        angle?: number \| string;<br>        direction?: GradientDirection;<br>        colors: Array\<[<br>            ResourceColor,<br>            number<br>        ]>;<br>        repeating?: boolean;<br>    }): T;<br>差异内容：value: {<br>        angle?: number \| string;<br>        direction?: GradientDirection;<br>        colors: Array\<[<br>            ResourceColor,<br>            number<br>        ]>;<br>        repeating?: boolean;<br>    }|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：sweepGradient(value: {<br>    center: Array\<any>;<br>    start?: number \| string;<br>    end?: number \| string;<br>    rotation?: number \| string;<br>    colors: Array\<any>;<br>    repeating?: boolean;<br>  }): T;<br>差异内容：value: {<br>    center: Array\<any>;<br>    start?: number \| string;<br>    end?: number \| string;<br>    rotation?: number \| string;<br>    colors: Array\<any>;<br>    repeating?: boolean;<br>  }|类名：CommonMethod；<br>API声明：sweepGradient(value: {<br>        center: [<br>            Length,<br>            Length<br>        ];<br>        start?: number \| string;<br>        end?: number \| string;<br>        rotation?: number \| string;<br>        colors: Array\<[<br>            ResourceColor,<br>            number<br>        ]>;<br>        repeating?: boolean;<br>    }): T;<br>差异内容：value: {<br>        center: [<br>            Length,<br>            Length<br>        ];<br>        start?: number \| string;<br>        end?: number \| string;<br>        rotation?: number \| string;<br>        colors: Array\<[<br>            ResourceColor,<br>            number<br>        ]>;<br>        repeating?: boolean;<br>    }|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：radialGradient(value: { center: Array\<any>; radius: number \| string; colors: Array\<any>; repeating?: boolean }): T;<br>差异内容：value: { center: Array\<any>; radius: number \| string; colors: Array\<any>; repeating?: boolean }|类名：CommonMethod；<br>API声明：radialGradient(value: {<br>        center: [<br>            Length,<br>            Length<br>        ];<br>        radius: number \| string;<br>        colors: Array\<[<br>            ResourceColor,<br>            number<br>        ]>;<br>        repeating?: boolean;<br>    }): T;<br>差异内容：value: {<br>        center: [<br>            Length,<br>            Length<br>        ];<br>        radius: number \| string;<br>        colors: Array\<[<br>            ResourceColor,<br>            number<br>        ]>;<br>        repeating?: boolean;<br>    }|component/common.d.ts|
|函数变更|类名：FolderStackAttribute；<br>API声明：onFolderStateChange(callback: (event: {<br>        /**<br>         * folder state.<br>         *<br>         * @type { FoldStatus }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 11<br>         */<br>        foldStatus: FoldStatus;<br>    }) => void): FolderStackAttribute;<br>差异内容：event: {<br>        /**<br>         * folder state.<br>         *<br>         * @type { FoldStatus }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 11<br>         */<br>        foldStatus: FoldStatus;<br>    }|类名：FolderStackAttribute；<br>API声明：onFolderStateChange(callback: (event: {<br>        /**<br>         * folder state.<br>         *<br>         * @type { FoldStatus }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 11<br>         */<br>        /**<br>         * folder state.<br>         *<br>         * @type { FoldStatus }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 12<br>         */<br>        foldStatus: FoldStatus;<br>    }) => void): FolderStackAttribute;<br>差异内容：event: {<br>        /**<br>         * folder state.<br>         *<br>         * @type { FoldStatus }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 11<br>         */<br>        /**<br>         * folder state.<br>         *<br>         * @type { FoldStatus }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 12<br>         */<br>        foldStatus: FoldStatus;<br>    }|component/folder_stack.d.ts|
|函数变更|类名：Scroller；<br>API声明：scrollTo(value: {<br>        /**<br>         * The X-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * The X-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        xOffset: number \| string;<br>        /**<br>         * The Y-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * The Y-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        yOffset: number \| string;<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?({ duration?: number; curve?: Curve \| ICurve } \| boolean) } The object type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?({ duration?: number; curve?: Curve \| ICurve } \| boolean) } The object type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        animation?: {<br>            duration?: number;<br>            curve?: Curve \| ICurve;<br>        } \| boolean;<br>    });<br>差异内容：value: {<br>        /**<br>         * The X-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * The X-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        xOffset: number \| string;<br>        /**<br>         * The Y-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * The Y-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        yOffset: number \| string;<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?({ duration?: number; curve?: Curve \| ICurve } \| boolean) } The object type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?({ duration?: number; curve?: Curve \| ICurve } \| boolean) } The object type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        animation?: {<br>            duration?: number;<br>            curve?: Curve \| ICurve;<br>        } \| boolean;<br>    }|类名：Scroller；<br>API声明：scrollTo(value: {<br>        /**<br>         * The X-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * The X-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        xOffset: number \| string;<br>        /**<br>         * The Y-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * The Y-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        yOffset: number \| string;<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?({ duration?: number; curve?: Curve \| ICurve } \| boolean) } The object type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?({ duration?: number; curve?: Curve \| ICurve } \| boolean) } The object type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?( ScrollAnimationOptions \| boolean) } The ScrollAnimationOptions type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 12<br>         */<br>        animation?: ScrollAnimationOptions \| boolean;<br>    });<br>差异内容：value: {<br>        /**<br>         * The X-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * The X-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        xOffset: number \| string;<br>        /**<br>         * The Y-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * The Y-axis offset.<br>         *<br>         * @type { number \| string }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        yOffset: number \| string;<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?({ duration?: number; curve?: Curve \| ICurve } \| boolean) } The object type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?({ duration?: number; curve?: Curve \| ICurve } \| boolean) } The object type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        /**<br>         * Descriptive animation.<br>         *<br>         * @type { ?( ScrollAnimationOptions \| boolean) } The ScrollAnimationOptions type provides custom animation parameters<br>         * and the boolean type enables default spring animation.<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 12<br>         */<br>        animation?: ScrollAnimationOptions \| boolean;<br>    }|component/scroll.d.ts|
|函数变更|类名：SearchAttribute；<br>API声明：cancelButton(value: {<br>        style?: CancelButtonStyle;<br>        icon?: IconOptions;<br>    }): SearchAttribute;<br>差异内容：value: {<br>        style?: CancelButtonStyle;<br>        icon?: IconOptions;<br>    }|类名：SearchAttribute；<br>API声明：cancelButton(value: CancelButtonOptions \| CancelButtonSymbolOptions): SearchAttribute;<br>差异内容：value: CancelButtonOptions \| CancelButtonSymbolOptions|component/search.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：padding(value: Padding \| Length): T;<br>差异内容：value: Padding \| Length|类名：CommonMethod；<br>API声明：padding(value: Padding \| Length \| LocalizedPadding): T;<br>差异内容：value: Padding \| Length \| LocalizedPadding|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：margin(value: Margin \| Length): T;<br>差异内容：value: Margin \| Length|类名：CommonMethod；<br>API声明：margin(value: Margin \| Length \| LocalizedMargin): T;<br>差异内容：value: Margin \| Length \| LocalizedMargin|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：backgroundImage(src: ResourceStr, repeat?: ImageRepeat): T;<br>差异内容：src: ResourceStr|类名：CommonMethod；<br>API声明：backgroundImage(src: ResourceStr \| PixelMap, repeat?: ImageRepeat): T;<br>差异内容：src: ResourceStr \| PixelMap|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：borderWidth(value: Length \| EdgeWidths): T;<br>差异内容：value: Length \| EdgeWidths|类名：CommonMethod；<br>API声明：borderWidth(value: Length \| EdgeWidths \| LocalizedEdgeWidths): T;<br>差异内容：value: Length \| EdgeWidths \| LocalizedEdgeWidths|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：borderColor(value: ResourceColor \| EdgeColors): T;<br>差异内容：value: ResourceColor \| EdgeColors|类名：CommonMethod；<br>API声明：borderColor(value: ResourceColor \| EdgeColors \| LocalizedEdgeColors): T;<br>差异内容：value: ResourceColor \| EdgeColors \| LocalizedEdgeColors|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：borderRadius(value: Length \| BorderRadiuses): T;<br>差异内容：value: Length \| BorderRadiuses|类名：CommonMethod；<br>API声明：borderRadius(value: Length \| BorderRadiuses \| LocalizedBorderRadiuses): T;<br>差异内容：value: Length \| BorderRadiuses \| LocalizedBorderRadiuses|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：outlineColor(value: ResourceColor \| EdgeColors): T;<br>差异内容：value: ResourceColor \| EdgeColors|类名：CommonMethod；<br>API声明：outlineColor(value: ResourceColor \| EdgeColors \| LocalizedEdgeColors): T;<br>差异内容：value: ResourceColor \| EdgeColors \| LocalizedEdgeColors|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：position(value: Position): T;<br>差异内容：value: Position|类名：CommonMethod；<br>API声明：position(value: Position \| Edges \| LocalizedEdges): T;<br>差异内容：value: Position \| Edges \| LocalizedEdges|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：markAnchor(value: Position): T;<br>差异内容：value: Position|类名：CommonMethod；<br>API声明：markAnchor(value: Position \| LocalizedPosition): T;<br>差异内容：value: Position \| LocalizedPosition|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：offset(value: Position): T;<br>差异内容：value: Position|类名：CommonMethod；<br>API声明：offset(value: Position \| Edges \| LocalizedEdges): T;<br>差异内容：value: Position \| Edges \| LocalizedEdges|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：allowDrop(value: Array\<UniformDataType>): T;<br>差异内容：value: Array\<UniformDataType>|类名：CommonMethod；<br>API声明：allowDrop(value: Array\<UniformDataType> \| null): T;<br>差异内容：value: Array\<UniformDataType> \| null|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：dragPreview(value: CustomBuilder \| DragItemInfo): T;<br>差异内容：value: CustomBuilder \| DragItemInfo|类名：CommonMethod；<br>API声明：dragPreview(value: CustomBuilder \| DragItemInfo \| string): T;<br>差异内容：value: CustomBuilder \| DragItemInfo \| string|component/common.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：overlay(value: string \| CustomBuilder, options?: { align?: Alignment; offset?: { x?: number; y?: number } }): T;<br>差异内容：value: string \| CustomBuilder|类名：CommonMethod；<br>API声明：overlay(value: string \| CustomBuilder \| ComponentContent, options?: OverlayOptions): T;<br>差异内容：value: string \| CustomBuilder \| ComponentContent|component/common.d.ts|
|函数变更|类名：ImageAttribute；<br>API声明：alt(value: string \| Resource): ImageAttribute;<br>差异内容：value: string \| Resource|类名：ImageAttribute；<br>API声明：alt(value: string \| Resource \| PixelMap): ImageAttribute;<br>差异内容：value: string \| Resource \| PixelMap|component/image.d.ts|
|函数变更|类名：ImageAttribute；<br>API声明：colorFilter(value: ColorFilter): ImageAttribute;<br>差异内容：value: ColorFilter|类名：ImageAttribute；<br>API声明：colorFilter(value: ColorFilter \| DrawingColorFilter): ImageAttribute;<br>差异内容：value: ColorFilter \| DrawingColorFilter|component/image.d.ts|
|函数变更|类名：MenuItemAttribute；<br>API声明：selectIcon(value: boolean \| ResourceStr): MenuItemAttribute;<br>差异内容：value: boolean \| ResourceStr|类名：MenuItemAttribute；<br>API声明：selectIcon(value: boolean \| ResourceStr \| SymbolGlyphModifier): MenuItemAttribute;<br>差异内容：value: boolean \| ResourceStr \| SymbolGlyphModifier|component/menu_item.d.ts|
|函数变更|类名：NavigationAttribute；<br>API声明：backButtonIcon(value: string \| PixelMap \| Resource): NavigationAttribute;<br>差异内容：value: string \| PixelMap \| Resource|类名：NavigationAttribute；<br>API声明：backButtonIcon(value: string \| PixelMap \| Resource \| SymbolGlyphModifier): NavigationAttribute;<br>差异内容：value: string \| PixelMap \| Resource \| SymbolGlyphModifier|component/navigation.d.ts|
|函数变更|类名：NavDestinationAttribute；<br>API声明：backButtonIcon(value: ResourceStr \| PixelMap): NavDestinationAttribute;<br>差异内容：value: ResourceStr \| PixelMap|类名：NavDestinationAttribute；<br>API声明：backButtonIcon(value: ResourceStr \| PixelMap \| SymbolGlyphModifier): NavDestinationAttribute;<br>差异内容：value: ResourceStr \| PixelMap \| SymbolGlyphModifier|component/nav_destination.d.ts|
|函数变更|类名：SearchAttribute；<br>API声明：searchIcon(value: IconOptions): SearchAttribute;<br>差异内容：value: IconOptions|类名：SearchAttribute；<br>API声明：searchIcon(value: IconOptions \| SymbolGlyphModifier): SearchAttribute;<br>差异内容：value: IconOptions \| SymbolGlyphModifier|component/search.d.ts|
|函数变更|类名：SecurityComponentMethod；<br>API声明：offset(value: Position): T;<br>差异内容：value: Position|类名：SecurityComponentMethod；<br>API声明：offset(value: Position \| Edges \| LocalizedEdges): T;<br>差异内容：value: Position \| Edges \| LocalizedEdges|component/security_component.d.ts|
|函数变更|类名：SliderAttribute；<br>API声明：trackColor(value: ResourceColor): SliderAttribute;<br>差异内容：value: ResourceColor|类名：SliderAttribute；<br>API声明：trackColor(value: ResourceColor \| LinearGradient): SliderAttribute;<br>差异内容：value: ResourceColor \| LinearGradient|component/slider.d.ts|
|函数变更|类名：BottomTabBarStyle；<br>API声明：static of(icon: ResourceStr, text: ResourceStr): BottomTabBarStyle;<br>差异内容：icon: ResourceStr|类名：BottomTabBarStyle；<br>API声明：static of(icon: ResourceStr \| TabBarSymbol, text: ResourceStr): BottomTabBarStyle;<br>差异内容：icon: ResourceStr \| TabBarSymbol|component/tab_content.d.ts|
|函数变更|类名：BottomTabBarStyle；<br>API声明：padding(value: Padding \| Dimension): BottomTabBarStyle;<br>差异内容：value: Padding \| Dimension|类名：BottomTabBarStyle；<br>API声明：padding(value: Padding \| Dimension \| LocalizedPadding): BottomTabBarStyle;<br>差异内容：value: Padding \| Dimension \| LocalizedPadding|component/tab_content.d.ts|
|函数变更|类名：TextInputAttribute；<br>API声明：showError(value?: string \| undefined): TextInputAttribute;<br>差异内容：value?: string \| undefined|类名：TextInputAttribute；<br>API声明：showError(value?: ResourceStr \| undefined): TextInputAttribute;<br>差异内容：value?: ResourceStr \| undefined|component/text_input.d.ts|
|属性变更|类名：TipsDialog；<br>API声明：imageSize: SizeOptions;<br>差异内容：imageSize: SizeOptions;|类名：TipsDialog；<br>API声明：imageSize?: SizeOptions;<br>差异内容：imageSize?: SizeOptions;|api/@ohos.arkui.advanced.Dialog.d.ets|
|属性变更|类名：TipsDialog；<br>API声明：title: ResourceStr;<br>差异内容：title: ResourceStr;|类名：TipsDialog；<br>API声明：title?: ResourceStr;<br>差异内容：title?: ResourceStr;|api/@ohos.arkui.advanced.Dialog.d.ets|
|属性变更|类名：LinearGradient；<br>API声明：colors: Array\<any>;<br>差异内容：Array\<any>|类名：LinearGradient；<br>API声明：colors: Array\<[<br>        ResourceColor,<br>        number<br>    ]>;<br>差异内容：Array\<[<br>        ResourceColor,<br>        number<br>    ]>|component/common.d.ts|
|属性变更|类名：EmitterOptions；<br>API声明：particle: {<br>        /**<br>         * Particle type.<br>         * @type { PARTICLE }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle type.<br>         * @type { PARTICLE }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        type: PARTICLE;<br>        /**<br>         * Particle config.<br>         * @type { ParticleConfigs[PARTICLE] }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle config.<br>         * @type { ParticleConfigs[PARTICLE] }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        config: ParticleConfigs[PARTICLE];<br>        /**<br>         * Particle count.<br>         * @type { number }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle count.<br>         * @type { number }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        count: number;<br>        /**<br>         * Particle lifetime.<br>         * @type { ?number }<br>         * @default 1000<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle lifetime.<br>         * @type { ?number }<br>         * @default 1000<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        lifetime?: number;<br>    };<br>差异内容：{<br>        /**<br>         * Particle type.<br>         * @type { PARTICLE }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle type.<br>         * @type { PARTICLE }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        type: PARTICLE;<br>        /**<br>         * Particle config.<br>         * @type { ParticleConfigs[PARTICLE] }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle config.<br>         * @type { ParticleConfigs[PARTICLE] }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        config: ParticleConfigs[PARTICLE];<br>        /**<br>         * Particle count.<br>         * @type { number }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle count.<br>         * @type { number }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        count: number;<br>        /**<br>         * Particle lifetime.<br>         * @type { ?number }<br>         * @default 1000<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle lifetime.<br>         * @type { ?number }<br>         * @default 1000<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        lifetime?: number;<br>    }|类名：EmitterOptions；<br>API声明：particle: {<br>        /**<br>         * Particle type.<br>         * @type { PARTICLE }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle type.<br>         * @type { PARTICLE }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        type: PARTICLE;<br>        /**<br>         * Particle config.<br>         * @type { ParticleConfigs[PARTICLE] }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle config.<br>         * @type { ParticleConfigs[PARTICLE] }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        config: ParticleConfigs[PARTICLE];<br>        /**<br>         * Particle count.<br>         * @type { number }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle count.<br>         * @type { number }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        count: number;<br>        /**<br>         * Particle lifetime.<br>         * @type { ?number }<br>         * @default 1000<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle lifetime.<br>         * @type { ?number }<br>         * @default 1000<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        lifetime?: number;<br>        /**<br>         * Particle lifetimeRange,value range [0, ∞).<br>         * when lifetimeRange>lifetime,minimum lifetime is 0.<br>         * @type { ?number }<br>         * @default 0<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 12<br>         */<br>        lifetimeRange?: number;<br>    };<br>差异内容：{<br>        /**<br>         * Particle type.<br>         * @type { PARTICLE }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle type.<br>         * @type { PARTICLE }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        type: PARTICLE;<br>        /**<br>         * Particle config.<br>         * @type { ParticleConfigs[PARTICLE] }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle config.<br>         * @type { ParticleConfigs[PARTICLE] }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        config: ParticleConfigs[PARTICLE];<br>        /**<br>         * Particle count.<br>         * @type { number }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle count.<br>         * @type { number }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        count: number;<br>        /**<br>         * Particle lifetime.<br>         * @type { ?number }<br>         * @default 1000<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * Particle lifetime.<br>         * @type { ?number }<br>         * @default 1000<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        lifetime?: number;<br>        /**<br>         * Particle lifetimeRange,value range [0, ∞).<br>         * when lifetimeRange>lifetime,minimum lifetime is 0.<br>         * @type { ?number }<br>         * @default 0<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 12<br>         */<br>        lifetimeRange?: number;<br>    }|component/particle.d.ts|
|属性变更|类名：TipsDialog；<br>API声明：imageRes: Resource;<br>差异内容：Resource|类名：TipsDialog；<br>API声明：imageRes: ResourceStr \| PixelMap;<br>差异内容：ResourceStr,PixelMap|api/@ohos.arkui.advanced.Dialog.d.ets|
|属性变更|类名：BorderImageOption；<br>API声明：slice?: Length \| EdgeWidths,<br>差异内容：Length,EdgeWidths|类名：BorderImageOption；<br>API声明：slice?: Length \| EdgeWidths \| LocalizedEdgeWidths;<br>差异内容：Length,EdgeWidths,LocalizedEdgeWidths|component/common.d.ts|
|属性变更|类名：BorderImageOption；<br>API声明：width?: Length \| EdgeWidths,<br>差异内容：Length,EdgeWidths|类名：BorderImageOption；<br>API声明：width?: Length \| EdgeWidths \| LocalizedEdgeWidths;<br>差异内容：Length,EdgeWidths,LocalizedEdgeWidths|component/common.d.ts|
|属性变更|类名：BorderImageOption；<br>API声明：outset?: Length \| EdgeWidths,<br>差异内容：Length,EdgeWidths|类名：BorderImageOption；<br>API声明：outset?: Length \| EdgeWidths \| LocalizedEdgeWidths;<br>差异内容：Length,EdgeWidths,LocalizedEdgeWidths|component/common.d.ts|
|属性变更|类名：DragPreviewOptions；<br>API声明：mode?: DragPreviewMode;<br>差异内容：DragPreviewMode|类名：DragPreviewOptions；<br>API声明：mode?: DragPreviewMode \| Array\<DragPreviewMode>;<br>差异内容：DragPreviewMode,Array\<DragPreviewMode>|component/common.d.ts|
|属性变更|类名：ImageFrameInfo；<br>API声明：src: string \| Resource;<br>差异内容：string,Resource|类名：ImageFrameInfo；<br>API声明：src: string \| Resource \| PixelMap;<br>差异内容：string,Resource,PixelMap|component/image_animator.d.ts|
|属性变更|类名：BorderOptions；<br>API声明：width?: EdgeWidths \| Length;<br>差异内容：EdgeWidths,Length|类名：BorderOptions；<br>API声明：width?: EdgeWidths \| Length \| LocalizedEdgeWidths;<br>差异内容：EdgeWidths,Length,LocalizedEdgeWidths|component/units.d.ts|
|属性变更|类名：BorderOptions；<br>API声明：color?: EdgeColors \| ResourceColor;<br>差异内容：EdgeColors,ResourceColor|类名：BorderOptions；<br>API声明：color?: EdgeColors \| ResourceColor \| LocalizedEdgeColors;<br>差异内容：EdgeColors,ResourceColor,LocalizedEdgeColors|component/units.d.ts|
|属性变更|类名：BorderOptions；<br>API声明：radius?: BorderRadiuses \| Length;<br>差异内容：BorderRadiuses,Length|类名：BorderOptions；<br>API声明：radius?: BorderRadiuses \| Length \| LocalizedBorderRadiuses;<br>差异内容：BorderRadiuses,Length,LocalizedBorderRadiuses|component/units.d.ts|
|属性变更|类名：OutlineOptions；<br>API声明：color?: EdgeColors \| ResourceColor;<br>差异内容：EdgeColors,ResourceColor|类名：OutlineOptions；<br>API声明：color?: EdgeColors \| ResourceColor \| LocalizedEdgeColors;<br>差异内容：EdgeColors,ResourceColor,LocalizedEdgeColors|component/units.d.ts|
|属性变更|类名：SheetOptions；<br>API声明：preferType?: SheetType.CENTER \| SheetType.POPUP;<br>差异内容：SheetType.CENTER,SheetType.POPUP|类名：SheetOptions；<br>API声明：preferType?: SheetType;<br>差异内容：SheetType|component/common.d.ts|
|属性变更|类名：AlignRuleOption；<br>API声明：left?: { anchor: string, align: HorizontalAlign };<br>差异内容：{ anchor: string, align: HorizontalAlign }|类名：AlignRuleOption；<br>API声明：left?: {<br>        anchor: string;<br>        align: HorizontalAlign;<br>    };<br>差异内容：{<br>        anchor: string;<br>        align: HorizontalAlign;<br>    }|component/common.d.ts|
|属性变更|类名：AlignRuleOption；<br>API声明：right?: { anchor: string, align: HorizontalAlign };<br>差异内容：{ anchor: string, align: HorizontalAlign }|类名：AlignRuleOption；<br>API声明：right?: {<br>        anchor: string;<br>        align: HorizontalAlign;<br>    };<br>差异内容：{<br>        anchor: string;<br>        align: HorizontalAlign;<br>    }|component/common.d.ts|
|属性变更|类名：AlignRuleOption；<br>API声明：middle?: { anchor: string, align: HorizontalAlign };<br>差异内容：{ anchor: string, align: HorizontalAlign }|类名：AlignRuleOption；<br>API声明：middle?: {<br>        anchor: string;<br>        align: HorizontalAlign;<br>    };<br>差异内容：{<br>        anchor: string;<br>        align: HorizontalAlign;<br>    }|component/common.d.ts|
|属性变更|类名：AlignRuleOption；<br>API声明：top?: { anchor: string, align: VerticalAlign };<br>差异内容：{ anchor: string, align: VerticalAlign }|类名：AlignRuleOption；<br>API声明：top?: {<br>        anchor: string;<br>        align: VerticalAlign;<br>    };<br>差异内容：{<br>        anchor: string;<br>        align: VerticalAlign;<br>    }|component/common.d.ts|
|属性变更|类名：AlignRuleOption；<br>API声明：bottom?: { anchor: string, align: VerticalAlign };<br>差异内容：{ anchor: string, align: VerticalAlign }|类名：AlignRuleOption；<br>API声明：bottom?: {<br>        anchor: string;<br>        align: VerticalAlign;<br>    };<br>差异内容：{<br>        anchor: string;<br>        align: VerticalAlign;<br>    }|component/common.d.ts|
|属性变更|类名：AlignRuleOption；<br>API声明：center?: { anchor: string, align: VerticalAlign };<br>差异内容：{ anchor: string, align: VerticalAlign }|类名：AlignRuleOption；<br>API声明：center?: {<br>        anchor: string;<br>        align: VerticalAlign;<br>    };<br>差异内容：{<br>        anchor: string;<br>        align: VerticalAlign;<br>    }|component/common.d.ts|
|属性变更|类名：PopupOptions；<br>API声明：onStateChange?: (event: {<br>    /**<br>     * is Visible.<br>     *<br>     * @type { boolean }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 10<br>     */<br>    /**<br>     * is Visible.<br>     *<br>     * @type { boolean }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @atomicservice<br>     * @since 11<br>     */<br>    isVisible: boolean<br>  }) => void;<br>差异内容：(event: {<br>    /**<br>     * is Visible.<br>     *<br>     * @type { boolean }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 10<br>     */<br>    /**<br>     * is Visible.<br>     *<br>     * @type { boolean }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @atomicservice<br>     * @since 11<br>     */<br>    isVisible: boolean<br>  }) => void|类名：PopupOptions；<br>API声明：onStateChange?: (event: {<br>        /**<br>         * is Visible.<br>         *<br>         * @type { boolean }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * is Visible.<br>         *<br>         * @type { boolean }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        isVisible: boolean;<br>    }) => void;<br>差异内容：(event: {<br>        /**<br>         * is Visible.<br>         *<br>         * @type { boolean }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * is Visible.<br>         *<br>         * @type { boolean }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        isVisible: boolean;<br>    }) => void|component/common.d.ts|
|属性变更|类名：PopupOptions；<br>API声明：mask?: boolean \| { color: ResourceColor };<br>差异内容：boolean,{ color: ResourceColor }|类名：PopupOptions；<br>API声明：mask?: boolean \| {<br>        color: ResourceColor;<br>    };<br>差异内容：boolean,{<br>        color: ResourceColor;<br>    }|component/common.d.ts|
|属性变更|类名：CustomPopupOptions；<br>API声明：onStateChange?: (event: {<br>    /**<br>     * is Visible.<br>     *<br>     * @type { boolean }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 10<br>     */<br>    /**<br>     * is Visible.<br>     *<br>     * @type { boolean }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @atomicservice<br>     * @since 11<br>     */<br>    isVisible: boolean<br>  }) => void;<br>差异内容：(event: {<br>    /**<br>     * is Visible.<br>     *<br>     * @type { boolean }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 10<br>     */<br>    /**<br>     * is Visible.<br>     *<br>     * @type { boolean }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @atomicservice<br>     * @since 11<br>     */<br>    isVisible: boolean<br>  }) => void|类名：CustomPopupOptions；<br>API声明：onStateChange?: (event: {<br>        /**<br>         * is Visible.<br>         *<br>         * @type { boolean }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * is Visible.<br>         *<br>         * @type { boolean }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        isVisible: boolean;<br>    }) => void;<br>差异内容：(event: {<br>        /**<br>         * is Visible.<br>         *<br>         * @type { boolean }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 10<br>         */<br>        /**<br>         * is Visible.<br>         *<br>         * @type { boolean }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 11<br>         */<br>        isVisible: boolean;<br>    }) => void|component/common.d.ts|
|属性变更|类名：CustomPopupOptions；<br>API声明：mask?: boolean \| { color: ResourceColor };<br>差异内容：boolean,{ color: ResourceColor }|类名：CustomPopupOptions；<br>API声明：mask?: boolean \| {<br>        color: ResourceColor;<br>    };<br>差异内容：boolean,{<br>        color: ResourceColor;<br>    }|component/common.d.ts|
|自定义类型变更|类名：PiPWindow；<br>API声明：type PiPVideoActionEvent = 'playbackStateChanged' \| 'nextVideo' \| 'previousVideo';<br>差异内容：'playbackStateChanged' \| 'nextVideo' \| 'previousVideo'|类名：PiPWindow；<br>API声明：type PiPVideoActionEvent = 'playbackStateChanged' \| 'nextVideo' \| 'previousVideo' \| 'fastForward' \| 'fastBackward';<br>差异内容：'playbackStateChanged' \| 'nextVideo' \| 'previousVideo' \| 'fastForward' \| 'fastBackward'|api/@ohos.PiPWindow.d.ts|
|自定义类型变更|类名：PiPWindow；<br>API声明：type PiPCallActionEvent = 'hangUp' \| 'micStateChanged' \| 'videoStateChanged';<br>差异内容：'hangUp' \| 'micStateChanged' \| 'videoStateChanged'|类名：PiPWindow；<br>API声明：type PiPCallActionEvent = 'hangUp' \| 'micStateChanged' \| 'videoStateChanged' \| 'voiceStateChanged';<br>差异内容：'hangUp' \| 'micStateChanged' \| 'videoStateChanged' \| 'voiceStateChanged'|api/@ohos.PiPWindow.d.ts|
|自定义类型变更|类名：PiPWindow；<br>API声明：type PiPMeetingActionEvent = 'hangUp' \| 'voiceStateChanged' \| 'videoStateChanged';<br>差异内容：'hangUp' \| 'voiceStateChanged' \| 'videoStateChanged'|类名：PiPWindow；<br>API声明：type PiPMeetingActionEvent = 'hangUp' \| 'voiceStateChanged' \| 'videoStateChanged' \| 'micStateChanged';<br>差异内容：'hangUp' \| 'voiceStateChanged' \| 'videoStateChanged' \| 'micStateChanged'|api/@ohos.PiPWindow.d.ts|
|自定义类型变更|类名：PiPWindow；<br>API声明：type PiPLiveActionEvent = 'playbackStateChanged';<br>差异内容：'playbackStateChanged'|类名：PiPWindow；<br>API声明：type PiPLiveActionEvent = 'playbackStateChanged' \| 'voiceStateChanged';<br>差异内容：'playbackStateChanged' \| 'voiceStateChanged'|api/@ohos.PiPWindow.d.ts|
|枚举赋值发生改变|类名：EnterKeyType；<br>API声明：Go<br>差异内容：0|类名：EnterKeyType；<br>API声明：Go = 2<br>差异内容：2|component/text_input.d.ts|
|枚举赋值发生改变|类名：EnterKeyType；<br>API声明：Search<br>差异内容：1|类名：EnterKeyType；<br>API声明：Search = 3<br>差异内容：3|component/text_input.d.ts|
|枚举赋值发生改变|类名：EnterKeyType；<br>API声明：Send<br>差异内容：2|类名：EnterKeyType；<br>API声明：Send = 4<br>差异内容：4|component/text_input.d.ts|
|枚举赋值发生改变|类名：EnterKeyType；<br>API声明：Next<br>差异内容：3|类名：EnterKeyType；<br>API声明：Next = 5<br>差异内容：5|component/text_input.d.ts|
|枚举赋值发生改变|类名：EnterKeyType；<br>API声明：Done<br>差异内容：4|类名：EnterKeyType；<br>API声明：Done = 6<br>差异内容：6|component/text_input.d.ts|
|新增API|NA|类名：console；<br>API声明：static traceHybridStack(): void;<br>差异内容：static traceHybridStack(): void;|api/@internal/full/global.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare function loadNativeModule(moduleName: string): Object;<br>差异内容：export declare function loadNativeModule(moduleName: string): Object;|api/@internal/full/global.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BuildOptions<br>差异内容：export interface BuildOptions|api/arkui/BuilderNode.d.ts|
|新增API|NA|类名：BuildOptions；<br>API声明：nestingBuilderSupported?: boolean;<br>差异内容：nestingBuilderSupported?: boolean;|api/arkui/BuilderNode.d.ts|
|新增API|NA|类名：BuilderNode；<br>API声明：dispose(): void;<br>差异内容：dispose(): void;|api/arkui/BuilderNode.d.ts|
|新增API|NA|类名：BuilderNode；<br>API声明：reuse(param?: Object): void;<br>差异内容：reuse(param?: Object): void;|api/arkui/BuilderNode.d.ts|
|新增API|NA|类名：BuilderNode；<br>API声明：recycle(): void;<br>差异内容：recycle(): void;|api/arkui/BuilderNode.d.ts|
|新增API|NA|类名：BuilderNode；<br>API声明：updateConfiguration(): void;<br>差异内容：updateConfiguration(): void;|api/arkui/BuilderNode.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LayoutConstraint<br>差异内容：declare interface LayoutConstraint|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：LayoutConstraint；<br>API声明：maxSize: Size;<br>差异内容：maxSize: Size;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：LayoutConstraint；<br>API声明：minSize: Size;<br>差异内容：minSize: Size;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：LayoutConstraint；<br>API声明：percentReference: Size;<br>差异内容：percentReference: Size;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：isModifiable(): boolean;<br>差异内容：isModifiable(): boolean;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：appendChild(node: FrameNode): void;<br>差异内容：appendChild(node: FrameNode): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：insertChildAfter(child: FrameNode, sibling: FrameNode \| null): void;<br>差异内容：insertChildAfter(child: FrameNode, sibling: FrameNode \| null): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：removeChild(node: FrameNode): void;<br>差异内容：removeChild(node: FrameNode): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：clearChildren(): void;<br>差异内容：clearChildren(): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getChild(index: number): FrameNode \| null;<br>差异内容：getChild(index: number): FrameNode \| null;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getFirstChild(): FrameNode \| null;<br>差异内容：getFirstChild(): FrameNode \| null;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getNextSibling(): FrameNode \| null;<br>差异内容：getNextSibling(): FrameNode \| null;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getPreviousSibling(): FrameNode \| null;<br>差异内容：getPreviousSibling(): FrameNode \| null;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getParent(): FrameNode \| null;<br>差异内容：getParent(): FrameNode \| null;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getChildrenCount(): number;<br>差异内容：getChildrenCount(): number;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：dispose(): void;<br>差异内容：dispose(): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getPositionToWindow(): Position;<br>差异内容：getPositionToWindow(): Position;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getPositionToParent(): Position;<br>差异内容：getPositionToParent(): Position;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getMeasuredSize(): Size;<br>差异内容：getMeasuredSize(): Size;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getLayoutPosition(): Position;<br>差异内容：getLayoutPosition(): Position;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getUserConfigBorderWidth(): Edges\<LengthMetrics>;<br>差异内容：getUserConfigBorderWidth(): Edges\<LengthMetrics>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getUserConfigPadding(): Edges\<LengthMetrics>;<br>差异内容：getUserConfigPadding(): Edges\<LengthMetrics>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getUserConfigMargin(): Edges\<LengthMetrics>;<br>差异内容：getUserConfigMargin(): Edges\<LengthMetrics>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getUserConfigSize(): SizeT\<LengthMetrics>;<br>差异内容：getUserConfigSize(): SizeT\<LengthMetrics>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getId(): string;<br>差异内容：getId(): string;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getUniqueId(): number;<br>差异内容：getUniqueId(): number;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getNodeType(): string;<br>差异内容：getNodeType(): string;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getOpacity(): number;<br>差异内容：getOpacity(): number;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：isVisible(): boolean;<br>差异内容：isVisible(): boolean;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：isClipToFrame(): boolean;<br>差异内容：isClipToFrame(): boolean;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：isAttached(): boolean;<br>差异内容：isAttached(): boolean;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getInspectorInfo(): Object;<br>差异内容：getInspectorInfo(): Object;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getCustomProperty(name: string): Object \| undefined;<br>差异内容：getCustomProperty(name: string): Object \| undefined;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：get commonEvent(): UICommonEvent;<br>差异内容：get commonEvent(): UICommonEvent;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：get commonAttribute(): CommonAttribute;<br>差异内容：get commonAttribute(): CommonAttribute;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：onDraw?(context: DrawContext): void;<br>差异内容：onDraw?(context: DrawContext): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：onMeasure(constraint: LayoutConstraint): void;<br>差异内容：onMeasure(constraint: LayoutConstraint): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：onLayout(position: Position): void;<br>差异内容：onLayout(position: Position): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：setMeasuredSize(size: Size): void;<br>差异内容：setMeasuredSize(size: Size): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：setLayoutPosition(position: Position): void;<br>差异内容：setLayoutPosition(position: Position): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：measure(constraint: LayoutConstraint): void;<br>差异内容：measure(constraint: LayoutConstraint): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：layout(position: Position): void;<br>差异内容：layout(position: Position): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：setNeedsLayout(): void;<br>差异内容：setNeedsLayout(): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：invalidate(): void;<br>差异内容：invalidate(): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getPositionToScreen(): Position;<br>差异内容：getPositionToScreen(): Position;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getPositionToWindowWithTransform(): Position;<br>差异内容：getPositionToWindowWithTransform(): Position;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getPositionToParentWithTransform(): Position;<br>差异内容：getPositionToParentWithTransform(): Position;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：getPositionToScreenWithTransform(): Position;<br>差异内容：getPositionToScreenWithTransform(): Position;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：disposeTree(): void;<br>差异内容：disposeTree(): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：FrameNode；<br>API声明：addComponentContent\<T>(content: ComponentContent\<T>): void;<br>差异内容：addComponentContent\<T>(content: ComponentContent\<T>): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface TypedFrameNode<br>差异内容：export interface TypedFrameNode|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：TypedFrameNode；<br>API声明：initialize: C;<br>差异内容：initialize: C;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：TypedFrameNode；<br>API声明：readonly attribute: T;<br>差异内容：readonly attribute: T;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：global；<br>API声明：export namespace typeNode<br>差异内容：export namespace typeNode|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Text = TypedFrameNode\<TextInterface, TextAttribute>;<br>差异内容：type Text = TypedFrameNode\<TextInterface, TextAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Text'): Text;<br>差异内容：function createNode(context: UIContext, nodeType: 'Text'): Text;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Column'): Column;<br>差异内容：function createNode(context: UIContext, nodeType: 'Column'): Column;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Row'): Row;<br>差异内容：function createNode(context: UIContext, nodeType: 'Row'): Row;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Stack'): Stack;<br>差异内容：function createNode(context: UIContext, nodeType: 'Stack'): Stack;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'GridRow'): GridRow;<br>差异内容：function createNode(context: UIContext, nodeType: 'GridRow'): GridRow;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'GridCol'): GridCol;<br>差异内容：function createNode(context: UIContext, nodeType: 'GridCol'): GridCol;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Flex'): Flex;<br>差异内容：function createNode(context: UIContext, nodeType: 'Flex'): Flex;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Swiper'): Swiper;<br>差异内容：function createNode(context: UIContext, nodeType: 'Swiper'): Swiper;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Progress'): Progress;<br>差异内容：function createNode(context: UIContext, nodeType: 'Progress'): Progress;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Scroll'): Scroll;<br>差异内容：function createNode(context: UIContext, nodeType: 'Scroll'): Scroll;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'RelativeContainer'): RelativeContainer;<br>差异内容：function createNode(context: UIContext, nodeType: 'RelativeContainer'): RelativeContainer;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Divider'): Divider;<br>差异内容：function createNode(context: UIContext, nodeType: 'Divider'): Divider;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'LoadingProgress'): LoadingProgress;<br>差异内容：function createNode(context: UIContext, nodeType: 'LoadingProgress'): LoadingProgress;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Search'): Search;<br>差异内容：function createNode(context: UIContext, nodeType: 'Search'): Search;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Blank'): Blank;<br>差异内容：function createNode(context: UIContext, nodeType: 'Blank'): Blank;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Image'): Image;<br>差异内容：function createNode(context: UIContext, nodeType: 'Image'): Image;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'List'): List;<br>差异内容：function createNode(context: UIContext, nodeType: 'List'): List;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'ListItem'): ListItem;<br>差异内容：function createNode(context: UIContext, nodeType: 'ListItem'): ListItem;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'TextInput'): TextInput;<br>差异内容：function createNode(context: UIContext, nodeType: 'TextInput'): TextInput;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'Button'): Button;<br>差异内容：function createNode(context: UIContext, nodeType: 'Button'): Button;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'ListItemGroup'): ListItemGroup;<br>差异内容：function createNode(context: UIContext, nodeType: 'ListItemGroup'): ListItemGroup;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'WaterFlow'): WaterFlow;<br>差异内容：function createNode(context: UIContext, nodeType: 'WaterFlow'): WaterFlow;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'FlowItem'): FlowItem;<br>差异内容：function createNode(context: UIContext, nodeType: 'FlowItem'): FlowItem;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'XComponent'): XComponent;<br>差异内容：function createNode(context: UIContext, nodeType: 'XComponent'): XComponent;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：function createNode(context: UIContext, nodeType: 'XComponent', options: XComponentOptions): XComponent;<br>差异内容：function createNode(context: UIContext, nodeType: 'XComponent', options: XComponentOptions): XComponent;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Column = TypedFrameNode\<ColumnInterface, ColumnAttribute>;<br>差异内容：type Column = TypedFrameNode\<ColumnInterface, ColumnAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Row = TypedFrameNode\<RowInterface, RowAttribute>;<br>差异内容：type Row = TypedFrameNode\<RowInterface, RowAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Stack = TypedFrameNode\<StackInterface, StackAttribute>;<br>差异内容：type Stack = TypedFrameNode\<StackInterface, StackAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type GridRow = TypedFrameNode\<GridRowInterface, GridRowAttribute>;<br>差异内容：type GridRow = TypedFrameNode\<GridRowInterface, GridRowAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type GridCol = TypedFrameNode\<GridColInterface, GridColAttribute>;<br>差异内容：type GridCol = TypedFrameNode\<GridColInterface, GridColAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Flex = TypedFrameNode\<FlexInterface, FlexAttribute>;<br>差异内容：type Flex = TypedFrameNode\<FlexInterface, FlexAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Swiper = TypedFrameNode\<SwiperInterface, SwiperAttribute>;<br>差异内容：type Swiper = TypedFrameNode\<SwiperInterface, SwiperAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Progress = TypedFrameNode\<ProgressInterface, ProgressAttribute>;<br>差异内容：type Progress = TypedFrameNode\<ProgressInterface, ProgressAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Scroll = TypedFrameNode\<ScrollInterface, ScrollAttribute>;<br>差异内容：type Scroll = TypedFrameNode\<ScrollInterface, ScrollAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type RelativeContainer = TypedFrameNode\<RelativeContainerInterface, RelativeContainerAttribute>;<br>差异内容：type RelativeContainer = TypedFrameNode\<RelativeContainerInterface, RelativeContainerAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Divider = TypedFrameNode\<DividerInterface, DividerAttribute>;<br>差异内容：type Divider = TypedFrameNode\<DividerInterface, DividerAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type LoadingProgress = TypedFrameNode\<LoadingProgressInterface, LoadingProgressAttribute>;<br>差异内容：type LoadingProgress = TypedFrameNode\<LoadingProgressInterface, LoadingProgressAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Search = TypedFrameNode\<SearchInterface, SearchAttribute>;<br>差异内容：type Search = TypedFrameNode\<SearchInterface, SearchAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Blank = TypedFrameNode\<BlankInterface, BlankAttribute>;<br>差异内容：type Blank = TypedFrameNode\<BlankInterface, BlankAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Image = TypedFrameNode\<ImageInterface, ImageAttribute>;<br>差异内容：type Image = TypedFrameNode\<ImageInterface, ImageAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type List = TypedFrameNode\<ListInterface, ListAttribute>;<br>差异内容：type List = TypedFrameNode\<ListInterface, ListAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type ListItem = TypedFrameNode\<ListItemInterface, ListItemAttribute>;<br>差异内容：type ListItem = TypedFrameNode\<ListItemInterface, ListItemAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type TextInput = TypedFrameNode\<TextInputInterface, TextInputAttribute>;<br>差异内容：type TextInput = TypedFrameNode\<TextInputInterface, TextInputAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type Button = TypedFrameNode\<ButtonInterface, ButtonAttribute>;<br>差异内容：type Button = TypedFrameNode\<ButtonInterface, ButtonAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type ListItemGroup = TypedFrameNode\<ListItemGroupInterface, ListItemGroupAttribute>;<br>差异内容：type ListItemGroup = TypedFrameNode\<ListItemGroupInterface, ListItemGroupAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type WaterFlow = TypedFrameNode\<WaterFlowInterface, WaterFlowAttribute>;<br>差异内容：type WaterFlow = TypedFrameNode\<WaterFlowInterface, WaterFlowAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type FlowItem = TypedFrameNode\<FlowItemInterface, FlowItemAttribute>;<br>差异内容：type FlowItem = TypedFrameNode\<FlowItemInterface, FlowItemAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：typeNode；<br>API声明：type XComponent = TypedFrameNode\<XComponentInterface, XComponentAttribute>;<br>差异内容：type XComponent = TypedFrameNode\<XComponentInterface, XComponentAttribute>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class NodeAdapter<br>差异内容：declare class NodeAdapter|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：dispose(): void;<br>差异内容：dispose(): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：get totalNodeCount(): number;<br>差异内容：get totalNodeCount(): number;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：reloadAllItems(): void;<br>差异内容：reloadAllItems(): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：reloadItem(start: number, count: number): void;<br>差异内容：reloadItem(start: number, count: number): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：removeItem(start: number, count: number): void;<br>差异内容：removeItem(start: number, count: number): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：insertItem(start: number, count: number): void;<br>差异内容：insertItem(start: number, count: number): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：moveItem(from: number, to: number): void;<br>差异内容：moveItem(from: number, to: number): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：getAllAvailableItems(): Array\<FrameNode>;<br>差异内容：getAllAvailableItems(): Array\<FrameNode>;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：onAttachToNode?(target: FrameNode): void;<br>差异内容：onAttachToNode?(target: FrameNode): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：onDetachFromNode?(): void;<br>差异内容：onDetachFromNode?(): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：onGetChildId?(index: number): number;<br>差异内容：onGetChildId?(index: number): number;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：onCreateChild?(index: number): FrameNode;<br>差异内容：onCreateChild?(index: number): FrameNode;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：onDisposeChild?(id: number, node: FrameNode): void;<br>差异内容：onDisposeChild?(id: number, node: FrameNode): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：onUpdateChild?(id: number, node: FrameNode): void;<br>差异内容：onUpdateChild?(id: number, node: FrameNode): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：static attachNodeAdapter(adapter: NodeAdapter, node: FrameNode): boolean;<br>差异内容：static attachNodeAdapter(adapter: NodeAdapter, node: FrameNode): boolean;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：NodeAdapter；<br>API声明：static detachNodeAdapter(node: FrameNode): void;<br>差异内容：static detachNodeAdapter(node: FrameNode): void;|api/arkui/FrameNode.d.ts|
|新增API|NA|类名：DrawContext；<br>API声明：get sizeInPixel(): Size;<br>差异内容：get sizeInPixel(): Size;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：interface Vector2T<br>差异内容：interface Vector2T|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Vector2T；<br>API声明：x: T;<br>差异内容：x: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Vector2T；<br>API声明：y: T;<br>差异内容：y: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export type PositionT\<T> = Vector2T\<T>;<br>差异内容：export type PositionT\<T> = Vector2T\<T>;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Edges<br>差异内容：export interface Edges|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Edges；<br>API声明：left: T;<br>差异内容：left: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Edges；<br>API声明：right: T;<br>差异内容：right: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Edges；<br>API声明：top: T;<br>差异内容：top: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Edges；<br>API声明：bottom: T;<br>差异内容：bottom: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum LengthUnit<br>差异内容：declare enum LengthUnit|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthUnit；<br>API声明：PX = 0<br>差异内容：PX = 0|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthUnit；<br>API声明：VP = 1<br>差异内容：VP = 1|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthUnit；<br>API声明：FP = 2<br>差异内容：FP = 2|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthUnit；<br>API声明：PERCENT = 3<br>差异内容：PERCENT = 3|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthUnit；<br>API声明：LPX = 4<br>差异内容：LPX = 4|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SizeT<br>差异内容：export interface SizeT|api/arkui/Graphics.d.ts|
|新增API|NA|类名：SizeT；<br>API声明：width: T;<br>差异内容：width: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：SizeT；<br>API声明：height: T;<br>差异内容：height: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum LengthMetricsUnit<br>差异内容：export enum LengthMetricsUnit|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetricsUnit；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetricsUnit；<br>API声明：PX = 1<br>差异内容：PX = 1|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class LengthMetrics<br>差异内容：declare class LengthMetrics|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetrics；<br>API声明：static px(value: number): LengthMetrics;<br>差异内容：static px(value: number): LengthMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetrics；<br>API声明：static vp(value: number): LengthMetrics;<br>差异内容：static vp(value: number): LengthMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetrics；<br>API声明：static fp(value: number): LengthMetrics;<br>差异内容：static fp(value: number): LengthMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetrics；<br>API声明：static percent(value: number): LengthMetrics;<br>差异内容：static percent(value: number): LengthMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetrics；<br>API声明：static lpx(value: number): LengthMetrics;<br>差异内容：static lpx(value: number): LengthMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetrics；<br>API声明：static resource(value: Resource): LengthMetrics;<br>差异内容：static resource(value: Resource): LengthMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetrics；<br>API声明：public unit: LengthUnit;<br>差异内容：public unit: LengthUnit;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：LengthMetrics；<br>API声明：public value: number;<br>差异内容：public value: number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ColorMetrics<br>差异内容：declare class ColorMetrics|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ColorMetrics；<br>API声明：static numeric(value: number): ColorMetrics;<br>差异内容：static numeric(value: number): ColorMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ColorMetrics；<br>API声明：static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics;<br>差异内容：static rgba(red: number, green: number, blue: number, alpha?: number): ColorMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ColorMetrics；<br>API声明：static resourceColor(color: ResourceColor): ColorMetrics;<br>差异内容：static resourceColor(color: ResourceColor): ColorMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ColorMetrics；<br>API声明：blendColor(overlayColor: ColorMetrics): ColorMetrics;<br>差异内容：blendColor(overlayColor: ColorMetrics): ColorMetrics;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ColorMetrics；<br>API声明：get color(): string;<br>差异内容：get color(): string;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ColorMetrics；<br>API声明：get red(): number;<br>差异内容：get red(): number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ColorMetrics；<br>API声明：get green(): number;<br>差异内容：get green(): number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ColorMetrics；<br>API声明：get blue(): number;<br>差异内容：get blue(): number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ColorMetrics；<br>API声明：get alpha(): number;<br>差异内容：get alpha(): number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：interface Corners<br>差异内容：interface Corners|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Corners；<br>API声明：topLeft: T;<br>差异内容：topLeft: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Corners；<br>API声明：topRight: T;<br>差异内容：topRight: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Corners；<br>API声明：bottomLeft: T;<br>差异内容：bottomLeft: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Corners；<br>API声明：bottomRight: T;<br>差异内容：bottomRight: T;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export type CornerRadius = Corners\<Vector2>;<br>差异内容：export type CornerRadius = Corners\<Vector2>;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export type BorderRadiuses = Corners\<number>;<br>差异内容：export type BorderRadiuses = Corners\<number>;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export type Rect = common2D.Rect;<br>差异内容：export type Rect = common2D.Rect;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface RoundRect<br>差异内容：export interface RoundRect|api/arkui/Graphics.d.ts|
|新增API|NA|类名：RoundRect；<br>API声明：rect: Rect;<br>差异内容：rect: Rect;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：RoundRect；<br>API声明：corners: CornerRadius;<br>差异内容：corners: CornerRadius;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Circle<br>差异内容：export interface Circle|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Circle；<br>API声明：centerX: number;<br>差异内容：centerX: number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Circle；<br>API声明：centerY: number;<br>差异内容：centerY: number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：Circle；<br>API声明：radius: number;<br>差异内容：radius: number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface CommandPath<br>差异内容：export interface CommandPath|api/arkui/Graphics.d.ts|
|新增API|NA|类名：CommandPath；<br>API声明：commands: string;<br>差异内容：commands: string;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ShapeMask<br>差异内容：export declare class ShapeMask|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeMask；<br>API声明：setRectShape(rect: Rect): void;<br>差异内容：setRectShape(rect: Rect): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeMask；<br>API声明：setRoundRectShape(roundRect: RoundRect): void;<br>差异内容：setRoundRectShape(roundRect: RoundRect): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeMask；<br>API声明：setCircleShape(circle: Circle): void;<br>差异内容：setCircleShape(circle: Circle): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeMask；<br>API声明：setOvalShape(oval: Rect): void;<br>差异内容：setOvalShape(oval: Rect): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeMask；<br>API声明：setCommandPath(path: CommandPath): void;<br>差异内容：setCommandPath(path: CommandPath): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeMask；<br>API声明：fillColor: number;<br>差异内容：fillColor: number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeMask；<br>API声明：strokeColor: number;<br>差异内容：strokeColor: number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeMask；<br>API声明：strokeWidth: number;<br>差异内容：strokeWidth: number;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ShapeClip<br>差异内容：export declare class ShapeClip|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeClip；<br>API声明：setRectShape(rect: Rect): void;<br>差异内容：setRectShape(rect: Rect): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeClip；<br>API声明：setRoundRectShape(roundRect: RoundRect): void;<br>差异内容：setRoundRectShape(roundRect: RoundRect): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeClip；<br>API声明：setCircleShape(circle: Circle): void;<br>差异内容：setCircleShape(circle: Circle): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeClip；<br>API声明：setOvalShape(oval: Rect): void;<br>差异内容：setOvalShape(oval: Rect): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：ShapeClip；<br>API声明：setCommandPath(path: CommandPath): void;<br>差异内容：setCommandPath(path: CommandPath): void;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export function edgeColors(all: number): Edges\<number>;<br>差异内容：export function edgeColors(all: number): Edges\<number>;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export function edgeWidths(all: number): Edges\<number>;<br>差异内容：export function edgeWidths(all: number): Edges\<number>;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export function borderStyles(all: BorderStyle): Edges\<BorderStyle>;<br>差异内容：export function borderStyles(all: BorderStyle): Edges\<BorderStyle>;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：global；<br>API声明：export function borderRadiuses(all: number): BorderRadiuses;<br>差异内容：export function borderRadiuses(all: number): BorderRadiuses;|api/arkui/Graphics.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：get label(): string;<br>差异内容：get label(): string;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：get borderStyle(): Edges\<BorderStyle>;<br>差异内容：get borderStyle(): Edges\<BorderStyle>;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：get borderWidth(): Edges\<number>;<br>差异内容：get borderWidth(): Edges\<number>;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：get borderColor(): Edges\<number>;<br>差异内容：get borderColor(): Edges\<number>;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：get borderRadius(): BorderRadiuses;<br>差异内容：get borderRadius(): BorderRadiuses;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：get shapeMask(): ShapeMask;<br>差异内容：get shapeMask(): ShapeMask;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：get shapeClip(): ShapeClip;<br>差异内容：get shapeClip(): ShapeClip;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：get markNodeGroup(): boolean;<br>差异内容：get markNodeGroup(): boolean;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：dispose(): void;<br>差异内容：dispose(): void;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：RenderNode；<br>API声明：get lengthMetricsUnit(): LengthMetricsUnit;<br>差异内容：get lengthMetricsUnit(): LengthMetricsUnit;|api/arkui/RenderNode.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DismissDialogAction<br>差异内容：declare interface DismissDialogAction|component/action_sheet.d.ts|
|新增API|NA|类名：DismissDialogAction；<br>API声明：dismiss: Callback\<void>;<br>差异内容：dismiss: Callback\<void>;|component/action_sheet.d.ts|
|新增API|NA|类名：DismissDialogAction；<br>API声明：reason: DismissReason;<br>差异内容：reason: DismissReason;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：onWillDismiss?: Callback\<DismissDialogAction>;<br>差异内容：onWillDismiss?: Callback\<DismissDialogAction>;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：transition?: TransitionEffect;<br>差异内容：transition?: TransitionEffect;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：cornerRadius?: Dimension \| BorderRadiuses \| LocalizedBorderRadiuses;<br>差异内容：cornerRadius?: Dimension \| BorderRadiuses \| LocalizedBorderRadiuses;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：width?: Dimension;<br>差异内容：width?: Dimension;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：height?: Dimension;<br>差异内容：height?: Dimension;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：borderWidth?: Dimension \| EdgeWidths \| LocalizedEdgeWidths;<br>差异内容：borderWidth?: Dimension \| EdgeWidths \| LocalizedEdgeWidths;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：borderColor?: ResourceColor \| EdgeColors \| LocalizedEdgeColors;<br>差异内容：borderColor?: ResourceColor \| EdgeColors \| LocalizedEdgeColors;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：borderStyle?: BorderStyle \| EdgeStyles;<br>差异内容：borderStyle?: BorderStyle \| EdgeStyles;|component/action_sheet.d.ts|
|新增API|NA|类名：ActionSheetOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|component/action_sheet.d.ts|
|新增API|NA|类名：AlertDialogButtonOptions；<br>API声明：primary?: boolean;<br>差异内容：primary?: boolean;|component/alert_dialog.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TextStyle<br>差异内容：declare interface TextStyle|component/alert_dialog.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：wordBreak?: WordBreak;<br>差异内容：wordBreak?: WordBreak;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：onWillDismiss?: Callback\<DismissDialogAction>;<br>差异内容：onWillDismiss?: Callback\<DismissDialogAction>;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：transition?: TransitionEffect;<br>差异内容：transition?: TransitionEffect;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：cornerRadius?: Dimension \| BorderRadiuses \| LocalizedBorderRadiuses;<br>差异内容：cornerRadius?: Dimension \| BorderRadiuses \| LocalizedBorderRadiuses;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：width?: Dimension;<br>差异内容：width?: Dimension;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：height?: Dimension;<br>差异内容：height?: Dimension;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：borderWidth?: Dimension \| EdgeWidths \| LocalizedEdgeWidths;<br>差异内容：borderWidth?: Dimension \| EdgeWidths \| LocalizedEdgeWidths;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：borderColor?: ResourceColor \| EdgeColors \| LocalizedEdgeColors;<br>差异内容：borderColor?: ResourceColor \| EdgeColors \| LocalizedEdgeColors;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：borderStyle?: BorderStyle \| EdgeStyles;<br>差异内容：borderStyle?: BorderStyle \| EdgeStyles;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|component/alert_dialog.d.ts|
|新增API|NA|类名：AlertDialogParam；<br>API声明：textStyle?: TextStyle;<br>差异内容：textStyle?: TextStyle;|component/alert_dialog.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DismissDialogAction<br>差异内容：declare interface DismissDialogAction|component/alert_dialog.d.ts|
|新增API|NA|类名：DismissDialogAction；<br>API声明：dismiss: Callback\<void>;<br>差异内容：dismiss: Callback\<void>;|component/alert_dialog.d.ts|
|新增API|NA|类名：DismissDialogAction；<br>API声明：reason: DismissReason;<br>差异内容：reason: DismissReason;|component/alert_dialog.d.ts|
|新增API|NA|类名：IndexerAlign；<br>API声明：START<br>差异内容：START|component/alphabet_indexer.d.ts|
|新增API|NA|类名：IndexerAlign；<br>API声明：END<br>差异内容：END|component/alphabet_indexer.d.ts|
|新增API|NA|类名：AlphabetIndexerAttribute；<br>API声明：popupItemBorderRadius(value: number): AlphabetIndexerAttribute;<br>差异内容：popupItemBorderRadius(value: number): AlphabetIndexerAttribute;|component/alphabet_indexer.d.ts|
|新增API|NA|类名：AlphabetIndexerAttribute；<br>API声明：itemBorderRadius(value: number): AlphabetIndexerAttribute;<br>差异内容：itemBorderRadius(value: number): AlphabetIndexerAttribute;|component/alphabet_indexer.d.ts|
|新增API|NA|类名：AlphabetIndexerAttribute；<br>API声明：popupBackgroundBlurStyle(value: BlurStyle): AlphabetIndexerAttribute;<br>差异内容：popupBackgroundBlurStyle(value: BlurStyle): AlphabetIndexerAttribute;|component/alphabet_indexer.d.ts|
|新增API|NA|类名：AlphabetIndexerAttribute；<br>API声明：popupTitleBackground(value: ResourceColor): AlphabetIndexerAttribute;<br>差异内容：popupTitleBackground(value: ResourceColor): AlphabetIndexerAttribute;|component/alphabet_indexer.d.ts|
|新增API|NA|类名：AlphabetIndexerAttribute；<br>API声明：enableHapticFeedback(value: boolean): AlphabetIndexerAttribute;<br>差异内容：enableHapticFeedback(value: boolean): AlphabetIndexerAttribute;|component/alphabet_indexer.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ButtonRole<br>差异内容：declare enum ButtonRole|component/button.d.ts|
|新增API|NA|类名：ButtonRole；<br>API声明：NORMAL = 0<br>差异内容：NORMAL = 0|component/button.d.ts|
|新增API|NA|类名：ButtonRole；<br>API声明：ERROR = 1<br>差异内容：ERROR = 1|component/button.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type ButtonTriggerClickCallback = (xPos: number, yPos: number) => void;<br>差异内容：declare type ButtonTriggerClickCallback = (xPos: number, yPos: number) => void;|component/button.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ButtonConfiguration<br>差异内容：declare interface ButtonConfiguration|component/button.d.ts|
|新增API|NA|类名：ButtonConfiguration；<br>API声明：label: string;<br>差异内容：label: string;|component/button.d.ts|
|新增API|NA|类名：ButtonConfiguration；<br>API声明：pressed: boolean;<br>差异内容：pressed: boolean;|component/button.d.ts|
|新增API|NA|类名：ButtonConfiguration；<br>API声明：triggerClick: ButtonTriggerClickCallback;<br>差异内容：triggerClick: ButtonTriggerClickCallback;|component/button.d.ts|
|新增API|NA|类名：ButtonOptions；<br>API声明：role?: ButtonRole;<br>差异内容：role?: ButtonRole;|component/button.d.ts|
|新增API|NA|类名：ButtonAttribute；<br>API声明：role(value: ButtonRole): ButtonAttribute;<br>差异内容：role(value: ButtonRole): ButtonAttribute;|component/button.d.ts|
|新增API|NA|类名：ButtonAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<ButtonConfiguration>): ButtonAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<ButtonConfiguration>): ButtonAttribute;|component/button.d.ts|
|新增API|NA|类名：CalendarDialogOptions；<br>API声明：acceptButtonStyle?: PickerDialogButtonStyle;<br>差异内容：acceptButtonStyle?: PickerDialogButtonStyle;|component/calendar_picker.d.ts|
|新增API|NA|类名：CalendarDialogOptions；<br>API声明：cancelButtonStyle?: PickerDialogButtonStyle;<br>差异内容：cancelButtonStyle?: PickerDialogButtonStyle;|component/calendar_picker.d.ts|
|新增API|NA|类名：CalendarDialogOptions；<br>API声明：onDidAppear?: () => void;<br>差异内容：onDidAppear?: () => void;|component/calendar_picker.d.ts|
|新增API|NA|类名：CalendarDialogOptions；<br>API声明：onDidDisappear?: () => void;<br>差异内容：onDidDisappear?: () => void;|component/calendar_picker.d.ts|
|新增API|NA|类名：CalendarDialogOptions；<br>API声明：onWillAppear?: () => void;<br>差异内容：onWillAppear?: () => void;|component/calendar_picker.d.ts|
|新增API|NA|类名：CalendarDialogOptions；<br>API声明：onWillDisappear?: () => void;<br>差异内容：onWillDisappear?: () => void;|component/calendar_picker.d.ts|
|新增API|NA|类名：CalendarDialogOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|component/calendar_picker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type DrawingCanvas = import('../api/@ohos.graphics.drawing').default.Canvas;<br>差异内容：declare type DrawingCanvas = import('../api/@ohos.graphics.drawing').default.Canvas;|component/canvas.d.ts|
|新增API|NA|类名：CanvasRenderer；<br>API声明：saveLayer(): void;<br>差异内容：saveLayer(): void;|component/canvas.d.ts|
|新增API|NA|类名：CanvasRenderer；<br>API声明：restoreLayer(): void;<br>差异内容：restoreLayer(): void;|component/canvas.d.ts|
|新增API|NA|类名：CanvasRenderer；<br>API声明：reset(): void;<br>差异内容：reset(): void;|component/canvas.d.ts|
|新增API|NA|类名：CanvasRenderingContext2D；<br>API声明：startImageAnalyzer(config: ImageAnalyzerConfig): Promise\<void>;<br>差异内容：startImageAnalyzer(config: ImageAnalyzerConfig): Promise\<void>;|component/canvas.d.ts|
|新增API|NA|类名：CanvasRenderingContext2D；<br>API声明：stopImageAnalyzer(): void;<br>差异内容：stopImageAnalyzer(): void;|component/canvas.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Size<br>差异内容：declare interface Size|component/canvas.d.ts|
|新增API|NA|类名：Size；<br>API声明：width: number;<br>差异内容：width: number;|component/canvas.d.ts|
|新增API|NA|类名：Size；<br>API声明：height: number;<br>差异内容：height: number;|component/canvas.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class DrawingRenderingContext<br>差异内容：declare class DrawingRenderingContext|component/canvas.d.ts|
|新增API|NA|类名：DrawingRenderingContext；<br>API声明：get size(): Size;<br>差异内容：get size(): Size;|component/canvas.d.ts|
|新增API|NA|类名：DrawingRenderingContext；<br>API声明：get canvas(): DrawingCanvas;<br>差异内容：get canvas(): DrawingCanvas;|component/canvas.d.ts|
|新增API|NA|类名：DrawingRenderingContext；<br>API声明：invalidate(): void;<br>差异内容：invalidate(): void;|component/canvas.d.ts|
|新增API|NA|类名：CanvasAttribute；<br>API声明：enableAnalyzer(enable: boolean): CanvasAttribute;<br>差异内容：enableAnalyzer(enable: boolean): CanvasAttribute;|component/canvas.d.ts|
|新增API|NA|类名：CheckboxOptions；<br>API声明：indicatorBuilder?: CustomBuilder;<br>差异内容：indicatorBuilder?: CustomBuilder;|component/checkbox.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface CheckBoxConfiguration<br>差异内容：declare interface CheckBoxConfiguration|component/checkbox.d.ts|
|新增API|NA|类名：CheckBoxConfiguration；<br>API声明：name: string;<br>差异内容：name: string;|component/checkbox.d.ts|
|新增API|NA|类名：CheckBoxConfiguration；<br>API声明：selected: boolean;<br>差异内容：selected: boolean;|component/checkbox.d.ts|
|新增API|NA|类名：CheckBoxConfiguration；<br>API声明：triggerChange: Callback\<boolean>;<br>差异内容：triggerChange: Callback\<boolean>;|component/checkbox.d.ts|
|新增API|NA|类名：CheckboxAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<CheckBoxConfiguration>): CheckboxAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<CheckBoxConfiguration>): CheckboxAttribute;|component/checkbox.d.ts|
|新增API|NA|类名：CheckboxGroupAttribute；<br>API声明：checkboxShape(value: CheckBoxShape): CheckboxGroupAttribute;<br>差异内容：checkboxShape(value: CheckBoxShape): CheckboxGroupAttribute;|component/checkboxgroup.d.ts|
|新增API|NA|类名：ColumnAttribute；<br>API声明：reverse(isReversed: Optional\<boolean>): ColumnAttribute;<br>差异内容：reverse(isReversed: Optional\<boolean>): ColumnAttribute;|component/column.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：bindContextMenu(isShown: boolean, content: CustomBuilder, options?: ContextMenuOptions): T;<br>差异内容：bindContextMenu(isShown: boolean, content: CustomBuilder, options?: ContextMenuOptions): T;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TextDecorationOptions<br>差异内容：declare interface TextDecorationOptions|component/common.d.ts|
|新增API|NA|类名：TextDecorationOptions；<br>API声明：type: TextDecorationType;<br>差异内容：type: TextDecorationType;|component/common.d.ts|
|新增API|NA|类名：TextDecorationOptions；<br>API声明：color?: ResourceColor;<br>差异内容：color?: ResourceColor;|component/common.d.ts|
|新增API|NA|类名：TextDecorationOptions；<br>API声明：style?: TextDecorationStyle;<br>差异内容：style?: TextDecorationStyle;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const ComponentV2: ClassDecorator & ((options: ComponentOptions) => ClassDecorator);<br>差异内容：declare const ComponentV2: ClassDecorator & ((options: ComponentOptions) => ClassDecorator);|component/common.d.ts|
|新增API|NA|类名：EntryOptions；<br>API声明：useSharedStorage?: boolean;<br>差异内容：useSharedStorage?: boolean;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const ObservedV2: ClassDecorator;<br>差异内容：declare const ObservedV2: ClassDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Local: PropertyDecorator;<br>差异内容：declare const Local: PropertyDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Param: PropertyDecorator;<br>差异内容：declare const Param: PropertyDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Once: PropertyDecorator;<br>差异内容：declare const Once: PropertyDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Event: PropertyDecorator;<br>差异内容：declare const Event: PropertyDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Trace: PropertyDecorator;<br>差异内容：declare const Trace: PropertyDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Provider: (aliasName?: string) => PropertyDecorator;<br>差异内容：declare const Provider: (aliasName?: string) => PropertyDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Consumer: (aliasName?: string) => PropertyDecorator;<br>差异内容：declare const Consumer: (aliasName?: string) => PropertyDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Computed: MethodDecorator;<br>差异内容：declare const Computed: MethodDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const LocalBuilder: MethodDecorator;<br>差异内容：declare const LocalBuilder: MethodDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Monitor: MonitorDecorator;<br>差异内容：declare const Monitor: MonitorDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type MonitorDecorator = (value: string, ...args: string[]) => MethodDecorator;<br>差异内容：declare type MonitorDecorator = (value: string, ...args: string[]) => MethodDecorator;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface IMonitor<br>差异内容：declare interface IMonitor|component/common.d.ts|
|新增API|NA|类名：IMonitor；<br>API声明：dirty: Array\<string>;<br>差异内容：dirty: Array\<string>;|component/common.d.ts|
|新增API|NA|类名：IMonitor；<br>API声明：value\<T>(path?: string): IMonitorValue\<T> \| undefined;<br>差异内容：value\<T>(path?: string): IMonitorValue\<T> \| undefined;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface IMonitorValue<br>差异内容：declare interface IMonitorValue|component/common.d.ts|
|新增API|NA|类名：IMonitorValue；<br>API声明：before: T;<br>差异内容：before: T;|component/common.d.ts|
|新增API|NA|类名：IMonitorValue；<br>API声明：now: T;<br>差异内容：now: T;|component/common.d.ts|
|新增API|NA|类名：IMonitorValue；<br>API声明：path: string;<br>差异内容：path: string;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedHorizontalAlignParam<br>差异内容：declare interface LocalizedHorizontalAlignParam|component/common.d.ts|
|新增API|NA|类名：LocalizedHorizontalAlignParam；<br>API声明：anchor: string;<br>差异内容：anchor: string;|component/common.d.ts|
|新增API|NA|类名：LocalizedHorizontalAlignParam；<br>API声明：align: HorizontalAlign;<br>差异内容：align: HorizontalAlign;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedVerticalAlignParam<br>差异内容：declare interface LocalizedVerticalAlignParam|component/common.d.ts|
|新增API|NA|类名：LocalizedVerticalAlignParam；<br>API声明：anchor: string;<br>差异内容：anchor: string;|component/common.d.ts|
|新增API|NA|类名：LocalizedVerticalAlignParam；<br>API声明：align: VerticalAlign;<br>差异内容：align: VerticalAlign;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedAlignRuleOptions<br>差异内容：declare interface LocalizedAlignRuleOptions|component/common.d.ts|
|新增API|NA|类名：LocalizedAlignRuleOptions；<br>API声明：start?: LocalizedHorizontalAlignParam;<br>差异内容：start?: LocalizedHorizontalAlignParam;|component/common.d.ts|
|新增API|NA|类名：LocalizedAlignRuleOptions；<br>API声明：end?: LocalizedHorizontalAlignParam;<br>差异内容：end?: LocalizedHorizontalAlignParam;|component/common.d.ts|
|新增API|NA|类名：LocalizedAlignRuleOptions；<br>API声明：middle?: LocalizedHorizontalAlignParam;<br>差异内容：middle?: LocalizedHorizontalAlignParam;|component/common.d.ts|
|新增API|NA|类名：LocalizedAlignRuleOptions；<br>API声明：top?: LocalizedVerticalAlignParam;<br>差异内容：top?: LocalizedVerticalAlignParam;|component/common.d.ts|
|新增API|NA|类名：LocalizedAlignRuleOptions；<br>API声明：bottom?: LocalizedVerticalAlignParam;<br>差异内容：bottom?: LocalizedVerticalAlignParam;|component/common.d.ts|
|新增API|NA|类名：LocalizedAlignRuleOptions；<br>API声明：center?: LocalizedVerticalAlignParam;<br>差异内容：center?: LocalizedVerticalAlignParam;|component/common.d.ts|
|新增API|NA|类名：LocalizedAlignRuleOptions；<br>API声明：bias?: Bias;<br>差异内容：bias?: Bias;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ChainStyle<br>差异内容：declare enum ChainStyle|component/common.d.ts|
|新增API|NA|类名：ChainStyle；<br>API声明：SPREAD<br>差异内容：SPREAD|component/common.d.ts|
|新增API|NA|类名：ChainStyle；<br>API声明：SPREAD_INSIDE<br>差异内容：SPREAD_INSIDE|component/common.d.ts|
|新增API|NA|类名：ChainStyle；<br>API声明：PACKED<br>差异内容：PACKED|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class DrawModifier<br>差异内容：declare class DrawModifier|component/common.d.ts|
|新增API|NA|类名：DrawModifier；<br>API声明：drawBehind?(drawContext: DrawContext): void;<br>差异内容：drawBehind?(drawContext: DrawContext): void;|component/common.d.ts|
|新增API|NA|类名：DrawModifier；<br>API声明：drawContent?(drawContext: DrawContext): void;<br>差异内容：drawContent?(drawContext: DrawContext): void;|component/common.d.ts|
|新增API|NA|类名：DrawModifier；<br>API声明：drawFront?(drawContext: DrawContext): void;<br>差异内容：drawFront?(drawContext: DrawContext): void;|component/common.d.ts|
|新增API|NA|类名：DrawModifier；<br>API声明：invalidate(): void;<br>差异内容：invalidate(): void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum PreDragStatus<br>差异内容：declare enum PreDragStatus|component/common.d.ts|
|新增API|NA|类名：PreDragStatus；<br>API声明：ACTION_DETECTING_STATUS = 0<br>差异内容：ACTION_DETECTING_STATUS = 0|component/common.d.ts|
|新增API|NA|类名：PreDragStatus；<br>API声明：READY_TO_TRIGGER_DRAG_ACTION = 1<br>差异内容：READY_TO_TRIGGER_DRAG_ACTION = 1|component/common.d.ts|
|新增API|NA|类名：PreDragStatus；<br>API声明：PREVIEW_LIFT_STARTED = 2<br>差异内容：PREVIEW_LIFT_STARTED = 2|component/common.d.ts|
|新增API|NA|类名：PreDragStatus；<br>API声明：PREVIEW_LIFT_FINISHED = 3<br>差异内容：PREVIEW_LIFT_FINISHED = 3|component/common.d.ts|
|新增API|NA|类名：PreDragStatus；<br>API声明：PREVIEW_LANDING_STARTED = 4<br>差异内容：PREVIEW_LANDING_STARTED = 4|component/common.d.ts|
|新增API|NA|类名：PreDragStatus；<br>API声明：PREVIEW_LANDING_FINISHED = 5<br>差异内容：PREVIEW_LANDING_FINISHED = 5|component/common.d.ts|
|新增API|NA|类名：PreDragStatus；<br>API声明：ACTION_CANCELED_BEFORE_DRAG = 6<br>差异内容：ACTION_CANCELED_BEFORE_DRAG = 6|component/common.d.ts|
|新增API|NA|类名：SourceTool；<br>API声明：MOUSE<br>差异内容：MOUSE|component/common.d.ts|
|新增API|NA|类名：SourceTool；<br>API声明：TOUCHPAD<br>差异内容：TOUCHPAD|component/common.d.ts|
|新增API|NA|类名：SourceTool；<br>API声明：JOYSTICK<br>差异内容：JOYSTICK|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ForegroundEffectOptions<br>差异内容：declare interface ForegroundEffectOptions|component/common.d.ts|
|新增API|NA|类名：ForegroundEffectOptions；<br>API声明：radius: number;<br>差异内容：radius: number;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface PickerDialogButtonStyle<br>差异内容：declare interface PickerDialogButtonStyle|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：type?: ButtonType;<br>差异内容：type?: ButtonType;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：style?: ButtonStyleMode;<br>差异内容：style?: ButtonStyleMode;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：role?: ButtonRole;<br>差异内容：role?: ButtonRole;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：fontSize?: Length;<br>差异内容：fontSize?: Length;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：fontColor?: ResourceColor;<br>差异内容：fontColor?: ResourceColor;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：fontWeight?: FontWeight \| number \| string;<br>差异内容：fontWeight?: FontWeight \| number \| string;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：fontStyle?: FontStyle;<br>差异内容：fontStyle?: FontStyle;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：fontFamily?: Resource \| string;<br>差异内容：fontFamily?: Resource \| string;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：backgroundColor?: ResourceColor;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：borderRadius?: Length \| BorderRadiuses;<br>差异内容：borderRadius?: Length \| BorderRadiuses;|component/common.d.ts|
|新增API|NA|类名：PickerDialogButtonStyle；<br>API声明：primary?: boolean;<br>差异内容：primary?: boolean;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum LayoutSafeAreaType<br>差异内容：declare enum LayoutSafeAreaType|component/common.d.ts|
|新增API|NA|类名：LayoutSafeAreaType；<br>API声明：SYSTEM = 0<br>差异内容：SYSTEM = 0|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum LayoutSafeAreaEdge<br>差异内容：declare enum LayoutSafeAreaEdge|component/common.d.ts|
|新增API|NA|类名：LayoutSafeAreaEdge；<br>API声明：TOP = 0<br>差异内容：TOP = 0|component/common.d.ts|
|新增API|NA|类名：LayoutSafeAreaEdge；<br>API声明：BOTTOM = 1<br>差异内容：BOTTOM = 1|component/common.d.ts|
|新增API|NA|类名：BaseEvent；<br>API声明：axisHorizontal?: number;<br>差异内容：axisHorizontal?: number;|component/common.d.ts|
|新增API|NA|类名：BaseEvent；<br>API声明：axisVertical?: number;<br>差异内容：axisVertical?: number;|component/common.d.ts|
|新增API|NA|类名：BaseEvent；<br>API声明：getModifierKeyState?(keys: Array\<string>): boolean;<br>差异内容：getModifierKeyState?(keys: Array\<string>): boolean;|component/common.d.ts|
|新增API|NA|类名：BaseEvent；<br>API声明：deviceId?: number;<br>差异内容：deviceId?: number;|component/common.d.ts|
|新增API|NA|类名：ClickEvent；<br>API声明：preventDefault: () => void;<br>差异内容：preventDefault: () => void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface AccessibilityHoverEvent<br>差异内容：declare interface AccessibilityHoverEvent|component/common.d.ts|
|新增API|NA|类名：AccessibilityHoverEvent；<br>API声明：type: AccessibilityHoverType;<br>差异内容：type: AccessibilityHoverType;|component/common.d.ts|
|新增API|NA|类名：AccessibilityHoverEvent；<br>API声明：x: number;<br>差异内容：x: number;|component/common.d.ts|
|新增API|NA|类名：AccessibilityHoverEvent；<br>API声明：y: number;<br>差异内容：y: number;|component/common.d.ts|
|新增API|NA|类名：AccessibilityHoverEvent；<br>API声明：displayX: number;<br>差异内容：displayX: number;|component/common.d.ts|
|新增API|NA|类名：AccessibilityHoverEvent；<br>API声明：displayY: number;<br>差异内容：displayY: number;|component/common.d.ts|
|新增API|NA|类名：AccessibilityHoverEvent；<br>API声明：windowX: number;<br>差异内容：windowX: number;|component/common.d.ts|
|新增API|NA|类名：AccessibilityHoverEvent；<br>API声明：windowY: number;<br>差异内容：windowY: number;|component/common.d.ts|
|新增API|NA|类名：TouchEvent；<br>API声明：preventDefault: () => void;<br>差异内容：preventDefault: () => void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void;<br>差异内容：declare type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type GestureRecognizerJudgeBeginCallback = (event: BaseGestureEvent, current: GestureRecognizer, recognizers: Array\<GestureRecognizer>) => GestureJudgeResult;<br>差异内容：declare type GestureRecognizerJudgeBeginCallback = (event: BaseGestureEvent, current: GestureRecognizer, recognizers: Array\<GestureRecognizer>) => GestureJudgeResult;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array\<GestureRecognizer>) => GestureRecognizer;<br>差异内容：declare type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array\<GestureRecognizer>) => GestureRecognizer;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type TransitionFinishCallback = (transitionIn: boolean) => void;<br>差异内容：declare type TransitionFinishCallback = (transitionIn: boolean) => void;|component/common.d.ts|
|新增API|NA|类名：DragEvent；<br>API声明：getModifierKeyState?(keys: Array\<string>): boolean;<br>差异内容：getModifierKeyState?(keys: Array\<string>): boolean;|component/common.d.ts|
|新增API|NA|类名：KeyEvent；<br>API声明：getModifierKeyState?(keys: Array\<string>): boolean;<br>差异内容：getModifierKeyState?(keys: Array\<string>): boolean;|component/common.d.ts|
|新增API|NA|类名：BindOptions；<br>API声明：onWillAppear?: () => void;<br>差异内容：onWillAppear?: () => void;|component/common.d.ts|
|新增API|NA|类名：BindOptions；<br>API声明：onWillDisappear?: () => void;<br>差异内容：onWillDisappear?: () => void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DismissContentCoverAction<br>差异内容：declare interface DismissContentCoverAction|component/common.d.ts|
|新增API|NA|类名：DismissContentCoverAction；<br>API声明：dismiss: Callback\<void>;<br>差异内容：dismiss: Callback\<void>;|component/common.d.ts|
|新增API|NA|类名：DismissContentCoverAction；<br>API声明：reason: DismissReason;<br>差异内容：reason: DismissReason;|component/common.d.ts|
|新增API|NA|类名：ContentCoverOptions；<br>API声明：onWillDismiss?: Callback\<DismissContentCoverAction>;<br>差异内容：onWillDismiss?: Callback\<DismissContentCoverAction>;|component/common.d.ts|
|新增API|NA|类名：ContentCoverOptions；<br>API声明：transition?: TransitionEffect;<br>差异内容：transition?: TransitionEffect;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum SheetMode<br>差异内容：declare enum SheetMode|component/common.d.ts|
|新增API|NA|类名：SheetMode；<br>API声明：OVERLAY = 0<br>差异内容：OVERLAY = 0|component/common.d.ts|
|新增API|NA|类名：SheetMode；<br>API声明：EMBEDDED = 1<br>差异内容：EMBEDDED = 1|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ScrollSizeMode<br>差异内容：declare enum ScrollSizeMode|component/common.d.ts|
|新增API|NA|类名：ScrollSizeMode；<br>API声明：FOLLOW_DETENT = 0<br>差异内容：FOLLOW_DETENT = 0|component/common.d.ts|
|新增API|NA|类名：ScrollSizeMode；<br>API声明：CONTINUOUS = 1<br>差异内容：CONTINUOUS = 1|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DismissSheetAction<br>差异内容：declare interface DismissSheetAction|component/common.d.ts|
|新增API|NA|类名：DismissSheetAction；<br>API声明：dismiss: Callback\<void>;<br>差异内容：dismiss: Callback\<void>;|component/common.d.ts|
|新增API|NA|类名：DismissSheetAction；<br>API声明：reason: DismissReason;<br>差异内容：reason: DismissReason;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SpringBackAction<br>差异内容：declare interface SpringBackAction|component/common.d.ts|
|新增API|NA|类名：SpringBackAction；<br>API声明：springBack: Callback\<void>;<br>差异内容：springBack: Callback\<void>;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：onWillDismiss?: Callback\<DismissSheetAction>;<br>差异内容：onWillDismiss?: Callback\<DismissSheetAction>;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：onWillSpringBackWhenDismiss?: Callback\<SpringBackAction>;<br>差异内容：onWillSpringBackWhenDismiss?: Callback\<SpringBackAction>;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：width?: Dimension;<br>差异内容：width?: Dimension;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：borderWidth?: Dimension \| EdgeWidths \| LocalizedEdgeWidths;<br>差异内容：borderWidth?: Dimension \| EdgeWidths \| LocalizedEdgeWidths;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：borderColor?: ResourceColor \| EdgeColors \| LocalizedEdgeColors;<br>差异内容：borderColor?: ResourceColor \| EdgeColors \| LocalizedEdgeColors;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：borderStyle?: BorderStyle \| EdgeStyles;<br>差异内容：borderStyle?: BorderStyle \| EdgeStyles;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：onHeightDidChange?: Callback\<number>;<br>差异内容：onHeightDidChange?: Callback\<number>;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：mode?: SheetMode;<br>差异内容：mode?: SheetMode;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：scrollSizeMode?: ScrollSizeMode;<br>差异内容：scrollSizeMode?: ScrollSizeMode;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：onDetentsDidChange?: Callback\<number>;<br>差异内容：onDetentsDidChange?: Callback\<number>;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：onWidthDidChange?: Callback\<number>;<br>差异内容：onWidthDidChange?: Callback\<number>;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：onTypeDidChange?: Callback\<SheetType>;<br>差异内容：onTypeDidChange?: Callback\<SheetType>;|component/common.d.ts|
|新增API|NA|类名：SheetOptions；<br>API声明：uiContext?: UIContext;<br>差异内容：uiContext?: UIContext;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum DismissReason<br>差异内容：declare enum DismissReason|component/common.d.ts|
|新增API|NA|类名：DismissReason；<br>API声明：PRESS_BACK = 0<br>差异内容：PRESS_BACK = 0|component/common.d.ts|
|新增API|NA|类名：DismissReason；<br>API声明：TOUCH_OUTSIDE = 1<br>差异内容：TOUCH_OUTSIDE = 1|component/common.d.ts|
|新增API|NA|类名：DismissReason；<br>API声明：CLOSE_BUTTON = 2<br>差异内容：CLOSE_BUTTON = 2|component/common.d.ts|
|新增API|NA|类名：DismissReason；<br>API声明：SLIDE_DOWN = 3<br>差异内容：SLIDE_DOWN = 3|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DismissPopupAction<br>差异内容：declare interface DismissPopupAction|component/common.d.ts|
|新增API|NA|类名：DismissPopupAction；<br>API声明：dismiss: Callback\<void>;<br>差异内容：dismiss: Callback\<void>;|component/common.d.ts|
|新增API|NA|类名：DismissPopupAction；<br>API声明：reason: DismissReason;<br>差异内容：reason: DismissReason;|component/common.d.ts|
|新增API|NA|类名：PopupOptions；<br>API声明：transition?: TransitionEffect;<br>差异内容：transition?: TransitionEffect;|component/common.d.ts|
|新增API|NA|类名：PopupOptions；<br>API声明：onWillDismiss?: boolean \| Callback\<DismissPopupAction>;<br>差异内容：onWillDismiss?: boolean \| Callback\<DismissPopupAction>;|component/common.d.ts|
|新增API|NA|类名：CustomPopupOptions；<br>API声明：transition?: TransitionEffect;<br>差异内容：transition?: TransitionEffect;|component/common.d.ts|
|新增API|NA|类名：CustomPopupOptions；<br>API声明：onWillDismiss?: boolean \| Callback\<DismissPopupAction>;<br>差异内容：onWillDismiss?: boolean \| Callback\<DismissPopupAction>;|component/common.d.ts|
|新增API|NA|类名：ContextMenuAnimationOptions；<br>API声明：transition?: TransitionEffect;<br>差异内容：transition?: TransitionEffect;|component/common.d.ts|
|新增API|NA|类名：ContextMenuAnimationOptions；<br>API声明：hoverScale?: AnimationRange\<number>;<br>差异内容：hoverScale?: AnimationRange\<number>;|component/common.d.ts|
|新增API|NA|类名：ContextMenuOptions；<br>API声明：borderRadius?: Length \| BorderRadiuses \| LocalizedBorderRadiuses;<br>差异内容：borderRadius?: Length \| BorderRadiuses \| LocalizedBorderRadiuses;|component/common.d.ts|
|新增API|NA|类名：ContextMenuOptions；<br>API声明：transition?: TransitionEffect;<br>差异内容：transition?: TransitionEffect;|component/common.d.ts|
|新增API|NA|类名：ProgressMask；<br>API声明：enableBreathingAnimation(value: boolean): void;<br>差异内容：enableBreathingAnimation(value: boolean): void;|component/common.d.ts|
|新增API|NA|类名：MenuElement；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：symbolIcon?: SymbolGlyphModifier;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ContentModifier<br>差异内容：declare interface ContentModifier|component/common.d.ts|
|新增API|NA|类名：ContentModifier；<br>API声明：applyContent(): WrappedBuilder\<[<br>        T<br>    ]>;<br>差异内容：applyContent(): WrappedBuilder\<[<br>        T<br>    ]>;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface CommonConfiguration<br>差异内容：declare interface CommonConfiguration|component/common.d.ts|
|新增API|NA|类名：CommonConfiguration；<br>API声明：enabled: boolean;<br>差异内容：enabled: boolean;|component/common.d.ts|
|新增API|NA|类名：CommonConfiguration；<br>API声明：contentModifier: ContentModifier\<T>;<br>差异内容：contentModifier: ContentModifier\<T>;|component/common.d.ts|
|新增API|NA|类名：DragPreviewMode；<br>API声明：ENABLE_DEFAULT_SHADOW = 3<br>差异内容：ENABLE_DEFAULT_SHADOW = 3|component/common.d.ts|
|新增API|NA|类名：DragPreviewMode；<br>API声明：ENABLE_DEFAULT_RADIUS = 4<br>差异内容：ENABLE_DEFAULT_RADIUS = 4|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum MenuPolicy<br>差异内容：declare enum MenuPolicy|component/common.d.ts|
|新增API|NA|类名：MenuPolicy；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|component/common.d.ts|
|新增API|NA|类名：MenuPolicy；<br>API声明：HIDE = 1<br>差异内容：HIDE = 1|component/common.d.ts|
|新增API|NA|类名：MenuPolicy；<br>API声明：SHOW = 2<br>差异内容：SHOW = 2|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type ImageModifier = import('../api/arkui/ImageModifier').ImageModifier;<br>差异内容：declare type ImageModifier = import('../api/arkui/ImageModifier').ImageModifier;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type SymbolGlyphModifier = import('../api/arkui/SymbolGlyphModifier').SymbolGlyphModifier;<br>差异内容：declare type SymbolGlyphModifier = import('../api/arkui/SymbolGlyphModifier').SymbolGlyphModifier;|component/common.d.ts|
|新增API|NA|类名：DragPreviewOptions；<br>API声明：modifier?: ImageModifier;<br>差异内容：modifier?: ImageModifier;|component/common.d.ts|
|新增API|NA|类名：DragPreviewOptions；<br>API声明：numberBadge?: boolean \| number;<br>差异内容：numberBadge?: boolean \| number;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DragInteractionOptions<br>差异内容：declare interface DragInteractionOptions|component/common.d.ts|
|新增API|NA|类名：DragInteractionOptions；<br>API声明：isMultiSelectionEnabled?: boolean;<br>差异内容：isMultiSelectionEnabled?: boolean;|component/common.d.ts|
|新增API|NA|类名：DragInteractionOptions；<br>API声明：defaultAnimationBeforeLifting?: boolean;<br>差异内容：defaultAnimationBeforeLifting?: boolean;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type CircleShape = import('../api/@ohos.arkui.shape').CircleShape;<br>差异内容：declare type CircleShape = import('../api/@ohos.arkui.shape').CircleShape;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type EllipseShape = import('../api/@ohos.arkui.shape').EllipseShape;<br>差异内容：declare type EllipseShape = import('../api/@ohos.arkui.shape').EllipseShape;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type PathShape = import('../api/@ohos.arkui.shape').PathShape;<br>差异内容：declare type PathShape = import('../api/@ohos.arkui.shape').PathShape;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type RectShape = import('../api/@ohos.arkui.shape').RectShape;<br>差异内容：declare type RectShape = import('../api/@ohos.arkui.shape').RectShape;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type Optional\<T> = T \| undefined;<br>差异内容：declare type Optional\<T> = T \| undefined;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：drawModifier(modifier: DrawModifier \| undefined): T;<br>差异内容：drawModifier(modifier: DrawModifier \| undefined): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：customProperty(name: string, value: Optional\<Object>): T;<br>差异内容：customProperty(name: string, value: Optional\<Object>): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：backgroundImageResizable(value: ResizableOptions): T;<br>差异内容：backgroundImageResizable(value: ResizableOptions): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：foregroundEffect(options: ForegroundEffectOptions): T;<br>差异内容：foregroundEffect(options: ForegroundEffectOptions): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：visualEffect(effect: VisualEffect): T;<br>差异内容：visualEffect(effect: VisualEffect): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：backgroundFilter(filter: Filter): T;<br>差异内容：backgroundFilter(filter: Filter): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：foregroundFilter(filter: Filter): T;<br>差异内容：foregroundFilter(filter: Filter): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：compositingFilter(filter: Filter): T;<br>差异内容：compositingFilter(filter: Filter): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：onAccessibilityHover(callback: AccessibilityCallback): T;<br>差异内容：onAccessibilityHover(callback: AccessibilityCallback): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：onKeyPreIme(event: Callback\<KeyEvent, boolean>): T;<br>差异内容：onKeyPreIme(event: Callback\<KeyEvent, boolean>): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：focusBox(style: FocusBoxStyle): T;<br>差异内容：focusBox(style: FocusBoxStyle): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：focusScopeId(id: string, isGroup?: boolean): T;<br>差异内容：focusScopeId(id: string, isGroup?: boolean): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：focusScopePriority(scopeId: string, priority?: FocusPriority): T;<br>差异内容：focusScopePriority(scopeId: string, priority?: FocusPriority): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：motionBlur(value: MotionBlurOptions): T;<br>差异内容：motionBlur(value: MotionBlurOptions): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：freeze(value: boolean): T;<br>差异内容：freeze(value: boolean): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：onAttach(callback: Callback\<void>): T;<br>差异内容：onAttach(callback: Callback\<void>): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：onDetach(callback: Callback\<void>): T;<br>差异内容：onDetach(callback: Callback\<void>): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：chainMode(direction: Axis, style: ChainStyle): T;<br>差异内容：chainMode(direction: Axis, style: ChainStyle): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：onPreDrag(callback: Callback\<PreDragStatus>): T;<br>差异内容：onPreDrag(callback: Callback\<PreDragStatus>): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：clipShape(value: CircleShape \| EllipseShape \| PathShape \| RectShape): T;<br>差异内容：clipShape(value: CircleShape \| EllipseShape \| PathShape \| RectShape): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：maskShape(value: CircleShape \| EllipseShape \| PathShape \| RectShape): T;<br>差异内容：maskShape(value: CircleShape \| EllipseShape \| PathShape \| RectShape): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：accessibilityTextHint(value: string): T;<br>差异内容：accessibilityTextHint(value: string): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：gestureModifier(modifier: GestureModifier): T;<br>差异内容：gestureModifier(modifier: GestureModifier): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback): T;<br>差异内容：onGestureRecognizerJudgeBegin(callback: GestureRecognizerJudgeBeginCallback): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：shouldBuiltInRecognizerParallelWith(callback: ShouldBuiltInRecognizerParallelWithCallback): T;<br>差异内容：shouldBuiltInRecognizerParallelWith(callback: ShouldBuiltInRecognizerParallelWithCallback): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：onTouchIntercept(callback: Callback\<TouchEvent, HitTestMode>): T;<br>差异内容：onTouchIntercept(callback: Callback\<TouchEvent, HitTestMode>): T;|component/common.d.ts|
|新增API|NA|类名：CommonMethod；<br>API声明：onSizeChange(event: SizeChangeCallback): T;<br>差异内容：onSizeChange(event: SizeChangeCallback): T;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface OverlayOptions<br>差异内容：declare interface OverlayOptions|component/common.d.ts|
|新增API|NA|类名：OverlayOptions；<br>API声明：align?: Alignment;<br>差异内容：align?: Alignment;|component/common.d.ts|
|新增API|NA|类名：OverlayOptions；<br>API声明：offset?: OverlayOffset;<br>差异内容：offset?: OverlayOffset;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface OverlayOffset<br>差异内容：declare interface OverlayOffset|component/common.d.ts|
|新增API|NA|类名：OverlayOffset；<br>API声明：x?: number;<br>差异内容：x?: number;|component/common.d.ts|
|新增API|NA|类名：OverlayOffset；<br>API声明：y?: number;<br>差异内容：y?: number;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface MotionBlurAnchor<br>差异内容：declare interface MotionBlurAnchor|component/common.d.ts|
|新增API|NA|类名：MotionBlurAnchor；<br>API声明：x: number;<br>差异内容：x: number;|component/common.d.ts|
|新增API|NA|类名：MotionBlurAnchor；<br>API声明：y: number;<br>差异内容：y: number;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface MotionBlurOptions<br>差异内容：declare interface MotionBlurOptions|component/common.d.ts|
|新增API|NA|类名：MotionBlurOptions；<br>API声明：radius: number;<br>差异内容：radius: number;|component/common.d.ts|
|新增API|NA|类名：MotionBlurOptions；<br>API声明：anchor: MotionBlurAnchor;<br>差异内容：anchor: MotionBlurAnchor;|component/common.d.ts|
|新增API|NA|类名：Layoutable；<br>API声明：getMargin(): DirectionalEdgesT\<number>;<br>差异内容：getMargin(): DirectionalEdgesT\<number>;|component/common.d.ts|
|新增API|NA|类名：Layoutable；<br>API声明：getPadding(): DirectionalEdgesT\<number>;<br>差异内容：getPadding(): DirectionalEdgesT\<number>;|component/common.d.ts|
|新增API|NA|类名：Layoutable；<br>API声明：getBorderWidth(): DirectionalEdgesT\<number>;<br>差异内容：getBorderWidth(): DirectionalEdgesT\<number>;|component/common.d.ts|
|新增API|NA|类名：Measurable；<br>API声明：getMargin(): DirectionalEdgesT\<number>;<br>差异内容：getMargin(): DirectionalEdgesT\<number>;|component/common.d.ts|
|新增API|NA|类名：Measurable；<br>API声明：getPadding(): DirectionalEdgesT\<number>;<br>差异内容：getPadding(): DirectionalEdgesT\<number>;|component/common.d.ts|
|新增API|NA|类名：Measurable；<br>API声明：getBorderWidth(): DirectionalEdgesT\<number>;<br>差异内容：getBorderWidth(): DirectionalEdgesT\<number>;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type NavigationInfo = import('../api/@ohos.arkui.observer').default.NavigationInfo;<br>差异内容：declare type NavigationInfo = import('../api/@ohos.arkui.observer').default.NavigationInfo;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type RouterPageInfo = import('../api/@ohos.arkui.observer').default.RouterPageInfo;<br>差异内容：declare type RouterPageInfo = import('../api/@ohos.arkui.observer').default.RouterPageInfo;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type DrawContext = import('../api/arkui/Graphics').DrawContext;<br>差异内容：declare type DrawContext = import('../api/arkui/Graphics').DrawContext;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type VisualEffect = import('../api/@ohos.graphics.uiEffect').default.VisualEffect;<br>差异内容：declare type VisualEffect = import('../api/@ohos.graphics.uiEffect').default.VisualEffect;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type Filter = import('../api/@ohos.graphics.uiEffect').default.Filter;<br>差异内容：declare type Filter = import('../api/@ohos.graphics.uiEffect').default.Filter;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type ComponentContent\<T = Object> = import('../api/arkui/ComponentContent').ComponentContent\<T>;<br>差异内容：declare type ComponentContent\<T = Object> = import('../api/arkui/ComponentContent').ComponentContent\<T>;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type Theme = import('../api/@ohos.arkui.theme').Theme;<br>差异内容：declare type Theme = import('../api/@ohos.arkui.theme').Theme;|component/common.d.ts|
|新增API|NA|类名：CustomComponent；<br>API声明：onWillApplyTheme?(theme: Theme): void;<br>差异内容：onWillApplyTheme?(theme: Theme): void;|component/common.d.ts|
|新增API|NA|类名：CustomComponent；<br>API声明：getUniqueId(): number;<br>差异内容：getUniqueId(): number;|component/common.d.ts|
|新增API|NA|类名：CustomComponent；<br>API声明：queryNavigationInfo(): NavigationInfo \| undefined;<br>差异内容：queryNavigationInfo(): NavigationInfo \| undefined;|component/common.d.ts|
|新增API|NA|类名：CustomComponent；<br>API声明：queryRouterPageInfo(): RouterPageInfo \| undefined;<br>差异内容：queryRouterPageInfo(): RouterPageInfo \| undefined;|component/common.d.ts|
|新增API|NA|类名：CustomComponent；<br>API声明：onDidBuild?(): void;<br>差异内容：onDidBuild?(): void;|component/common.d.ts|
|新增API|NA|类名：ScrollableCommonMethod；<br>API声明：onWillScroll(handler: Optional\<OnWillScrollCallback>): T;<br>差异内容：onWillScroll(handler: Optional\<OnWillScrollCallback>): T;|component/common.d.ts|
|新增API|NA|类名：ScrollableCommonMethod；<br>API声明：onDidScroll(handler: OnScrollCallback): T;<br>差异内容：onDidScroll(handler: OnScrollCallback): T;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ScrollResult<br>差异内容：declare class ScrollResult|component/common.d.ts|
|新增API|NA|类名：ScrollResult；<br>API声明：offsetRemain: number;<br>差异内容：offsetRemain: number;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type OnWillScrollCallback = (scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void \| ScrollResult;<br>差异内容：declare type OnWillScrollCallback = (scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void \| ScrollResult;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void;<br>差异内容：declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type OnMoveHandler = (from: number, to: number) => void;<br>差异内容：declare type OnMoveHandler = (from: number, to: number) => void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class DynamicNode<br>差异内容：declare class DynamicNode|component/common.d.ts|
|新增API|NA|类名：DynamicNode；<br>API声明：onMove(handler: Optional\<OnMoveHandler>): T;<br>差异内容：onMove(handler: Optional\<OnMoveHandler>): T;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ChildrenMainSize<br>差异内容：declare class ChildrenMainSize|component/common.d.ts|
|新增API|NA|类名：ChildrenMainSize；<br>API声明：get childDefaultSize(): number;<br>差异内容：get childDefaultSize(): number;|component/common.d.ts|
|新增API|NA|类名：ChildrenMainSize；<br>API声明：splice(start: number, deleteCount?: number, childrenSize?: Array\<number>): void;<br>差异内容：splice(start: number, deleteCount?: number, childrenSize?: Array\<number>): void;|component/common.d.ts|
|新增API|NA|类名：ChildrenMainSize；<br>API声明：update(index: number, childSize: number): void;<br>差异内容：update(index: number, childSize: number): void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Callback<br>差异内容：declare interface Callback|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type HoverCallback = (isHover: boolean, event: HoverEvent) => void;<br>差异内容：declare type HoverCallback = (isHover: boolean, event: HoverEvent) => void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void;<br>差异内容：declare type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface VisibleAreaEventOptions<br>差异内容：declare interface VisibleAreaEventOptions|component/common.d.ts|
|新增API|NA|类名：VisibleAreaEventOptions；<br>API声明：ratios: Array\<number>;<br>差异内容：ratios: Array\<number>;|component/common.d.ts|
|新增API|NA|类名：VisibleAreaEventOptions；<br>API声明：expectedUpdateInterval?: number;<br>差异内容：expectedUpdateInterval?: number;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type VisibleAreaChangeCallback = (isVisible: boolean, currentRatio: number) => void;<br>差异内容：declare type VisibleAreaChangeCallback = (isVisible: boolean, currentRatio: number) => void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface UICommonEvent<br>差异内容：declare interface UICommonEvent|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnClick(callback: Callback\<ClickEvent> \| undefined): void;<br>差异内容：setOnClick(callback: Callback\<ClickEvent> \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnTouch(callback: Callback\<TouchEvent> \| undefined): void;<br>差异内容：setOnTouch(callback: Callback\<TouchEvent> \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnAppear(callback: Callback\<void> \| undefined): void;<br>差异内容：setOnAppear(callback: Callback\<void> \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnDisappear(callback: Callback\<void> \| undefined): void;<br>差异内容：setOnDisappear(callback: Callback\<void> \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnKeyEvent(callback: Callback\<KeyEvent> \| undefined): void;<br>差异内容：setOnKeyEvent(callback: Callback\<KeyEvent> \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnFocus(callback: Callback\<void> \| undefined): void;<br>差异内容：setOnFocus(callback: Callback\<void> \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnBlur(callback: Callback\<void> \| undefined): void;<br>差异内容：setOnBlur(callback: Callback\<void> \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnHover(callback: HoverCallback \| undefined): void;<br>差异内容：setOnHover(callback: HoverCallback \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnMouse(callback: Callback\<MouseEvent> \| undefined): void;<br>差异内容：setOnMouse(callback: Callback\<MouseEvent> \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnSizeChange(callback: SizeChangeCallback \| undefined): void;<br>差异内容：setOnSizeChange(callback: SizeChangeCallback \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：UICommonEvent；<br>API声明：setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback \| undefined): void;<br>差异内容：setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback \| undefined): void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface UIGestureEvent<br>差异内容：declare interface UIGestureEvent|component/common.d.ts|
|新增API|NA|类名：UIGestureEvent；<br>API声明：addGesture\<T>(gesture: GestureHandler\<T>, priority?: GesturePriority, mask?: GestureMask): void;<br>差异内容：addGesture\<T>(gesture: GestureHandler\<T>, priority?: GesturePriority, mask?: GestureMask): void;|component/common.d.ts|
|新增API|NA|类名：UIGestureEvent；<br>API声明：addParallelGesture\<T>(gesture: GestureHandler\<T>, mask?: GestureMask): void;<br>差异内容：addParallelGesture\<T>(gesture: GestureHandler\<T>, mask?: GestureMask): void;|component/common.d.ts|
|新增API|NA|类名：UIGestureEvent；<br>API声明：removeGestureByTag(tag: string): void;<br>差异内容：removeGestureByTag(tag: string): void;|component/common.d.ts|
|新增API|NA|类名：UIGestureEvent；<br>API声明：clearGestures(): void;<br>差异内容：clearGestures(): void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface GestureModifier<br>差异内容：declare interface GestureModifier|component/common.d.ts|
|新增API|NA|类名：GestureModifier；<br>API声明：applyGesture(event: UIGestureEvent): void;<br>差异内容：applyGesture(event: UIGestureEvent): void;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SelectionOptions<br>差异内容：declare interface SelectionOptions|component/common.d.ts|
|新增API|NA|类名：SelectionOptions；<br>API声明：menuPolicy?: MenuPolicy;<br>差异内容：menuPolicy?: MenuPolicy;|component/common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum KeyboardAvoidMode<br>差异内容：declare enum KeyboardAvoidMode|component/common.d.ts|
|新增API|NA|类名：KeyboardAvoidMode；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|component/common.d.ts|
|新增API|NA|类名：KeyboardAvoidMode；<br>API声明：NONE = 1<br>差异内容：NONE = 1|component/common.d.ts|
|新增API|NA|类名：AppStorage；<br>API声明：static ref\<T>(propName: string): AbstractProperty\<T> \| undefined;<br>差异内容：static ref\<T>(propName: string): AbstractProperty\<T> \| undefined;|component/common_ts_ets_api.d.ts|
|新增API|NA|类名：AppStorage；<br>API声明：static setAndRef\<T>(propName: string, defaultValue: T): AbstractProperty\<T>;<br>差异内容：static setAndRef\<T>(propName: string, defaultValue: T): AbstractProperty\<T>;|component/common_ts_ets_api.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface AbstractProperty<br>差异内容：declare interface AbstractProperty|component/common_ts_ets_api.d.ts|
|新增API|NA|类名：AbstractProperty；<br>API声明：get(): T;<br>差异内容：get(): T;|component/common_ts_ets_api.d.ts|
|新增API|NA|类名：AbstractProperty；<br>API声明：set(newValue: T): void;<br>差异内容：set(newValue: T): void;|component/common_ts_ets_api.d.ts|
|新增API|NA|类名：AbstractProperty；<br>API声明：info(): string;<br>差异内容：info(): string;|component/common_ts_ets_api.d.ts|
|新增API|NA|类名：LocalStorage；<br>API声明：public ref\<T>(propName: string): AbstractProperty\<T> \| undefined;<br>差异内容：public ref\<T>(propName: string): AbstractProperty\<T> \| undefined;|component/common_ts_ets_api.d.ts|
|新增API|NA|类名：LocalStorage；<br>API声明：public setAndRef\<T>(propName: string, defaultValue: T): AbstractProperty\<T>;<br>差异内容：public setAndRef\<T>(propName: string, defaultValue: T): AbstractProperty\<T>;|component/common_ts_ets_api.d.ts|
|新增API|NA|类名：ContainerSpanAttribute；<br>API声明：attributeModifier(modifier: AttributeModifier\<ContainerSpanAttribute>): ContainerSpanAttribute;<br>差异内容：attributeModifier(modifier: AttributeModifier\<ContainerSpanAttribute>): ContainerSpanAttribute;|component/container_span.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：onWillDismiss?: Callback\<DismissDialogAction>;<br>差异内容：onWillDismiss?: Callback\<DismissDialogAction>;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：width?: Dimension;<br>差异内容：width?: Dimension;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：height?: Dimension;<br>差异内容：height?: Dimension;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：borderWidth?: Dimension \| EdgeWidths;<br>差异内容：borderWidth?: Dimension \| EdgeWidths;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：borderColor?: ResourceColor \| EdgeColors;<br>差异内容：borderColor?: ResourceColor \| EdgeColors;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：borderStyle?: BorderStyle \| EdgeStyles;<br>差异内容：borderStyle?: BorderStyle \| EdgeStyles;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：backgroundBlurStyle?: BlurStyle;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：CustomDialogControllerOptions；<br>API声明：keyboardAvoidMode?: KeyboardAvoidMode;<br>差异内容：keyboardAvoidMode?: KeyboardAvoidMode;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DismissDialogAction<br>差异内容：declare interface DismissDialogAction|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：DismissDialogAction；<br>API声明：dismiss: Callback\<void>;<br>差异内容：dismiss: Callback\<void>;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：DismissDialogAction；<br>API声明：reason: DismissReason;<br>差异内容：reason: DismissReason;|component/custom_dialog_controller.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DataPanelConfiguration<br>差异内容：declare interface DataPanelConfiguration|component/data_panel.d.ts|
|新增API|NA|类名：DataPanelConfiguration；<br>API声明：values: number[];<br>差异内容：values: number[];|component/data_panel.d.ts|
|新增API|NA|类名：DataPanelConfiguration；<br>API声明：maxValue: number;<br>差异内容：maxValue: number;|component/data_panel.d.ts|
|新增API|NA|类名：DataPanelAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<DataPanelConfiguration>): DataPanelAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<DataPanelConfiguration>): DataPanelAttribute;|component/data_panel.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：acceptButtonStyle?: PickerDialogButtonStyle;<br>差异内容：acceptButtonStyle?: PickerDialogButtonStyle;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：cancelButtonStyle?: PickerDialogButtonStyle;<br>差异内容：cancelButtonStyle?: PickerDialogButtonStyle;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：onDidAppear?: () => void;<br>差异内容：onDidAppear?: () => void;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：onDidDisappear?: () => void;<br>差异内容：onDidDisappear?: () => void;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：onWillAppear?: () => void;<br>差异内容：onWillAppear?: () => void;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：onWillDisappear?: () => void;<br>差异内容：onWillDisappear?: () => void;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|component/date_picker.d.ts|
|新增API|NA|类名：DatePickerDialogOptions；<br>API声明：dateTimeOptions?: DateTimeOptions;<br>差异内容：dateTimeOptions?: DateTimeOptions;|component/date_picker.d.ts|
|新增API|NA|类名：ImageFit；<br>API声明：TOP_START = 7<br>差异内容：TOP_START = 7|component/enums.d.ts|
|新增API|NA|类名：ImageFit；<br>API声明：TOP = 8<br>差异内容：TOP = 8|component/enums.d.ts|
|新增API|NA|类名：ImageFit；<br>API声明：TOP_END = 9<br>差异内容：TOP_END = 9|component/enums.d.ts|
|新增API|NA|类名：ImageFit；<br>API声明：START = 10<br>差异内容：START = 10|component/enums.d.ts|
|新增API|NA|类名：ImageFit；<br>API声明：CENTER = 11<br>差异内容：CENTER = 11|component/enums.d.ts|
|新增API|NA|类名：ImageFit；<br>API声明：END = 12<br>差异内容：END = 12|component/enums.d.ts|
|新增API|NA|类名：ImageFit；<br>API声明：BOTTOM_START = 13<br>差异内容：BOTTOM_START = 13|component/enums.d.ts|
|新增API|NA|类名：ImageFit；<br>API声明：BOTTOM = 14<br>差异内容：BOTTOM = 14|component/enums.d.ts|
|新增API|NA|类名：ImageFit；<br>API声明：BOTTOM_END = 15<br>差异内容：BOTTOM_END = 15|component/enums.d.ts|
|新增API|NA|类名：ImageSize；<br>API声明：FILL = 3<br>差异内容：FILL = 3|component/enums.d.ts|
|新增API|NA|类名：FunctionKey；<br>API声明：TAB<br>差异内容：TAB|component/enums.d.ts|
|新增API|NA|类名：FunctionKey；<br>API声明：DPAD_UP<br>差异内容：DPAD_UP|component/enums.d.ts|
|新增API|NA|类名：FunctionKey；<br>API声明：DPAD_DOWN<br>差异内容：DPAD_DOWN|component/enums.d.ts|
|新增API|NA|类名：FunctionKey；<br>API声明：DPAD_LEFT<br>差异内容：DPAD_LEFT|component/enums.d.ts|
|新增API|NA|类名：FunctionKey；<br>API声明：DPAD_RIGHT<br>差异内容：DPAD_RIGHT|component/enums.d.ts|
|新增API|NA|类名：XComponentType；<br>API声明：NODE<br>差异内容：NODE|component/enums.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ScrollSource<br>差异内容：declare enum ScrollSource|component/enums.d.ts|
|新增API|NA|类名：ScrollSource；<br>API声明：DRAG = 0<br>差异内容：DRAG = 0|component/enums.d.ts|
|新增API|NA|类名：ScrollSource；<br>API声明：FLING<br>差异内容：FLING|component/enums.d.ts|
|新增API|NA|类名：ScrollSource；<br>API声明：EDGE_EFFECT<br>差异内容：EDGE_EFFECT|component/enums.d.ts|
|新增API|NA|类名：ScrollSource；<br>API声明：OTHER_USER_INPUT<br>差异内容：OTHER_USER_INPUT|component/enums.d.ts|
|新增API|NA|类名：ScrollSource；<br>API声明：SCROLL_BAR<br>差异内容：SCROLL_BAR|component/enums.d.ts|
|新增API|NA|类名：ScrollSource；<br>API声明：SCROLL_BAR_FLING<br>差异内容：SCROLL_BAR_FLING|component/enums.d.ts|
|新增API|NA|类名：ScrollSource；<br>API声明：SCROLLER<br>差异内容：SCROLLER|component/enums.d.ts|
|新增API|NA|类名：ScrollSource；<br>API声明：SCROLLER_ANIMATION<br>差异内容：SCROLLER_ANIMATION|component/enums.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum LineBreakStrategy<br>差异内容：declare enum LineBreakStrategy|component/enums.d.ts|
|新增API|NA|类名：LineBreakStrategy；<br>API声明：GREEDY = 0<br>差异内容：GREEDY = 0|component/enums.d.ts|
|新增API|NA|类名：LineBreakStrategy；<br>API声明：HIGH_QUALITY = 1<br>差异内容：HIGH_QUALITY = 1|component/enums.d.ts|
|新增API|NA|类名：LineBreakStrategy；<br>API声明：BALANCED = 2<br>差异内容：BALANCED = 2|component/enums.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum AppRotation<br>差异内容：declare enum AppRotation|component/enums.d.ts|
|新增API|NA|类名：AppRotation；<br>API声明：ROTATION_0 = 0<br>差异内容：ROTATION_0 = 0|component/enums.d.ts|
|新增API|NA|类名：AppRotation；<br>API声明：ROTATION_90 = 1<br>差异内容：ROTATION_90 = 1|component/enums.d.ts|
|新增API|NA|类名：AppRotation；<br>API声明：ROTATION_180 = 2<br>差异内容：ROTATION_180 = 2|component/enums.d.ts|
|新增API|NA|类名：AppRotation；<br>API声明：ROTATION_270 = 3<br>差异内容：ROTATION_270 = 3|component/enums.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum EmbeddedType<br>差异内容：declare enum EmbeddedType|component/enums.d.ts|
|新增API|NA|类名：EmbeddedType；<br>API声明：EMBEDDED_UI_EXTENSION = 0<br>差异内容：EMBEDDED_UI_EXTENSION = 0|component/enums.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum MarqueeUpdateStrategy<br>差异内容：declare enum MarqueeUpdateStrategy|component/enums.d.ts|
|新增API|NA|类名：MarqueeUpdateStrategy；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|component/enums.d.ts|
|新增API|NA|类名：MarqueeUpdateStrategy；<br>API声明：PRESERVE_POSITION = 1<br>差异内容：PRESERVE_POSITION = 1|component/enums.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum TextDecorationStyle<br>差异内容：declare enum TextDecorationStyle|component/enums.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：SOLID = 0<br>差异内容：SOLID = 0|component/enums.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：DOUBLE = 1<br>差异内容：DOUBLE = 1|component/enums.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：DOTTED = 2<br>差异内容：DOTTED = 2|component/enums.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：DASHED = 3<br>差异内容：DASHED = 3|component/enums.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：WAVY = 4<br>差异内容：WAVY = 4|component/enums.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum TextSelectableMode<br>差异内容：declare enum TextSelectableMode|component/enums.d.ts|
|新增API|NA|类名：TextSelectableMode；<br>API声明：SELECTABLE_UNFOCUSABLE = 0<br>差异内容：SELECTABLE_UNFOCUSABLE = 0|component/enums.d.ts|
|新增API|NA|类名：TextSelectableMode；<br>API声明：SELECTABLE_FOCUSABLE = 1<br>差异内容：SELECTABLE_FOCUSABLE = 1|component/enums.d.ts|
|新增API|NA|类名：TextSelectableMode；<br>API声明：UNSELECTABLE = 2<br>差异内容：UNSELECTABLE = 2|component/enums.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum AccessibilityHoverType<br>差异内容：declare enum AccessibilityHoverType|component/enums.d.ts|
|新增API|NA|类名：AccessibilityHoverType；<br>API声明：HOVER_ENTER = 0<br>差异内容：HOVER_ENTER = 0|component/enums.d.ts|
|新增API|NA|类名：AccessibilityHoverType；<br>API声明：HOVER_MOVE = 1<br>差异内容：HOVER_MOVE = 1|component/enums.d.ts|
|新增API|NA|类名：AccessibilityHoverType；<br>API声明：HOVER_EXIT = 2<br>差异内容：HOVER_EXIT = 2|component/enums.d.ts|
|新增API|NA|类名：AccessibilityHoverType；<br>API声明：HOVER_CANCEL = 3<br>差异内容：HOVER_CANCEL = 3|component/enums.d.ts|
|新增API|NA|类名：FlexOptions；<br>API声明：space?: FlexSpaceOptions;<br>差异内容：space?: FlexSpaceOptions;|component/flex.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface FlexSpaceOptions<br>差异内容：declare interface FlexSpaceOptions|component/flex.d.ts|
|新增API|NA|类名：FlexSpaceOptions；<br>API声明：main?: LengthMetrics;<br>差异内容：main?: LengthMetrics;|component/flex.d.ts|
|新增API|NA|类名：FlexSpaceOptions；<br>API声明：cross?: LengthMetrics;<br>差异内容：cross?: LengthMetrics;|component/flex.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type WindowStatusType = import('../api/@ohos.window').default.WindowStatusType;<br>差异内容：declare type WindowStatusType = import('../api/@ohos.window').default.WindowStatusType;|component/folder_stack.d.ts|
|新增API|NA|类名：FolderStackAttribute；<br>API声明：onHoverStatusChange(handler: (param: HoverEventParam) => void): FolderStackAttribute;<br>差异内容：onHoverStatusChange(handler: (param: HoverEventParam) => void): FolderStackAttribute;|component/folder_stack.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface HoverEventParam<br>差异内容：declare interface HoverEventParam|component/folder_stack.d.ts|
|新增API|NA|类名：HoverEventParam；<br>API声明：foldStatus: FoldStatus;<br>差异内容：foldStatus: FoldStatus;|component/folder_stack.d.ts|
|新增API|NA|类名：HoverEventParam；<br>API声明：isHoverMode: boolean;<br>差异内容：isHoverMode: boolean;|component/folder_stack.d.ts|
|新增API|NA|类名：HoverEventParam；<br>API声明：appRotation: AppRotation;<br>差异内容：appRotation: AppRotation;|component/folder_stack.d.ts|
|新增API|NA|类名：HoverEventParam；<br>API声明：windowStatusType: WindowStatusType;<br>差异内容：windowStatusType: WindowStatusType;|component/folder_stack.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ForEachAttribute<br>差异内容：declare class ForEachAttribute|component/for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface GaugeConfiguration<br>差异内容：declare interface GaugeConfiguration|component/gauge.d.ts|
|新增API|NA|类名：GaugeConfiguration；<br>API声明：value: number;<br>差异内容：value: number;|component/gauge.d.ts|
|新增API|NA|类名：GaugeConfiguration；<br>API声明：min: number;<br>差异内容：min: number;|component/gauge.d.ts|
|新增API|NA|类名：GaugeConfiguration；<br>API声明：max: number;<br>差异内容：max: number;|component/gauge.d.ts|
|新增API|NA|类名：GaugeAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<GaugeConfiguration>): GaugeAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<GaugeConfiguration>): GaugeAttribute;|component/gauge.d.ts|
|新增API|NA|类名：GaugeAttribute；<br>API声明：privacySensitive(isPrivacySensitiveMode: Optional\<boolean>): GaugeAttribute;<br>差异内容：privacySensitive(isPrivacySensitiveMode: Optional\<boolean>): GaugeAttribute;|component/gauge.d.ts|
|新增API|NA|类名：FingerInfo；<br>API声明：displayX: number;<br>差异内容：displayX: number;|component/gesture.d.ts|
|新增API|NA|类名：FingerInfo；<br>API声明：displayY: number;<br>差异内容：displayY: number;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TapGestureParameters<br>差异内容：declare interface TapGestureParameters|component/gesture.d.ts|
|新增API|NA|类名：TapGestureParameters；<br>API声明：count?: number;<br>差异内容：count?: number;|component/gesture.d.ts|
|新增API|NA|类名：TapGestureParameters；<br>API声明：fingers?: number;<br>差异内容：fingers?: number;|component/gesture.d.ts|
|新增API|NA|类名：TapGestureParameters；<br>API声明：distanceThreshold?: number;<br>差异内容：distanceThreshold?: number;|component/gesture.d.ts|
|新增API|NA|类名：PanGestureOptions；<br>API声明：getDirection(): PanDirection;<br>差异内容：getDirection(): PanDirection;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class GestureHandler<br>差异内容：declare class GestureHandler|component/gesture.d.ts|
|新增API|NA|类名：GestureHandler；<br>API声明：tag(tag: string): T;<br>差异内容：tag(tag: string): T;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：interface TapGestureHandlerOptions<br>差异内容：interface TapGestureHandlerOptions|component/gesture.d.ts|
|新增API|NA|类名：TapGestureHandlerOptions；<br>API声明：count?: number;<br>差异内容：count?: number;|component/gesture.d.ts|
|新增API|NA|类名：TapGestureHandlerOptions；<br>API声明：fingers?: number;<br>差异内容：fingers?: number;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class TapGestureHandler<br>差异内容：declare class TapGestureHandler|component/gesture.d.ts|
|新增API|NA|类名：TapGestureHandler；<br>API声明：onAction(event: Callback\<GestureEvent>): TapGestureHandler;<br>差异内容：onAction(event: Callback\<GestureEvent>): TapGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：interface LongPressGestureHandlerOptions<br>差异内容：interface LongPressGestureHandlerOptions|component/gesture.d.ts|
|新增API|NA|类名：LongPressGestureHandlerOptions；<br>API声明：fingers?: number;<br>差异内容：fingers?: number;|component/gesture.d.ts|
|新增API|NA|类名：LongPressGestureHandlerOptions；<br>API声明：repeat?: boolean;<br>差异内容：repeat?: boolean;|component/gesture.d.ts|
|新增API|NA|类名：LongPressGestureHandlerOptions；<br>API声明：duration?: number;<br>差异内容：duration?: number;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class LongPressGestureHandler<br>差异内容：declare class LongPressGestureHandler|component/gesture.d.ts|
|新增API|NA|类名：LongPressGestureHandler；<br>API声明：onAction(event: Callback\<GestureEvent>): LongPressGestureHandler;<br>差异内容：onAction(event: Callback\<GestureEvent>): LongPressGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：LongPressGestureHandler；<br>API声明：onActionEnd(event: Callback\<GestureEvent>): LongPressGestureHandler;<br>差异内容：onActionEnd(event: Callback\<GestureEvent>): LongPressGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：LongPressGestureHandler；<br>API声明：onActionCancel(event: Callback\<void>): LongPressGestureHandler;<br>差异内容：onActionCancel(event: Callback\<void>): LongPressGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：interface PanGestureHandlerOptions<br>差异内容：interface PanGestureHandlerOptions|component/gesture.d.ts|
|新增API|NA|类名：PanGestureHandlerOptions；<br>API声明：fingers?: number;<br>差异内容：fingers?: number;|component/gesture.d.ts|
|新增API|NA|类名：PanGestureHandlerOptions；<br>API声明：direction?: PanDirection;<br>差异内容：direction?: PanDirection;|component/gesture.d.ts|
|新增API|NA|类名：PanGestureHandlerOptions；<br>API声明：distance?: number;<br>差异内容：distance?: number;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class PanGestureHandler<br>差异内容：declare class PanGestureHandler|component/gesture.d.ts|
|新增API|NA|类名：PanGestureHandler；<br>API声明：onActionStart(event: Callback\<GestureEvent>): PanGestureHandler;<br>差异内容：onActionStart(event: Callback\<GestureEvent>): PanGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：PanGestureHandler；<br>API声明：onActionUpdate(event: Callback\<GestureEvent>): PanGestureHandler;<br>差异内容：onActionUpdate(event: Callback\<GestureEvent>): PanGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：PanGestureHandler；<br>API声明：onActionEnd(event: Callback\<GestureEvent>): PanGestureHandler;<br>差异内容：onActionEnd(event: Callback\<GestureEvent>): PanGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：PanGestureHandler；<br>API声明：onActionCancel(event: Callback\<void>): PanGestureHandler;<br>差异内容：onActionCancel(event: Callback\<void>): PanGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：interface SwipeGestureHandlerOptions<br>差异内容：interface SwipeGestureHandlerOptions|component/gesture.d.ts|
|新增API|NA|类名：SwipeGestureHandlerOptions；<br>API声明：fingers?: number;<br>差异内容：fingers?: number;|component/gesture.d.ts|
|新增API|NA|类名：SwipeGestureHandlerOptions；<br>API声明：direction?: SwipeDirection;<br>差异内容：direction?: SwipeDirection;|component/gesture.d.ts|
|新增API|NA|类名：SwipeGestureHandlerOptions；<br>API声明：speed?: number;<br>差异内容：speed?: number;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class SwipeGestureHandler<br>差异内容：declare class SwipeGestureHandler|component/gesture.d.ts|
|新增API|NA|类名：SwipeGestureHandler；<br>API声明：onAction(event: Callback\<GestureEvent>): SwipeGestureHandler;<br>差异内容：onAction(event: Callback\<GestureEvent>): SwipeGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：interface PinchGestureHandlerOptions<br>差异内容：interface PinchGestureHandlerOptions|component/gesture.d.ts|
|新增API|NA|类名：PinchGestureHandlerOptions；<br>API声明：fingers?: number;<br>差异内容：fingers?: number;|component/gesture.d.ts|
|新增API|NA|类名：PinchGestureHandlerOptions；<br>API声明：distance?: number;<br>差异内容：distance?: number;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class PinchGestureHandler<br>差异内容：declare class PinchGestureHandler|component/gesture.d.ts|
|新增API|NA|类名：PinchGestureHandler；<br>API声明：onActionStart(event: Callback\<GestureEvent>): PinchGestureHandler;<br>差异内容：onActionStart(event: Callback\<GestureEvent>): PinchGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：PinchGestureHandler；<br>API声明：onActionUpdate(event: Callback\<GestureEvent>): PinchGestureHandler;<br>差异内容：onActionUpdate(event: Callback\<GestureEvent>): PinchGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：PinchGestureHandler；<br>API声明：onActionEnd(event: Callback\<GestureEvent>): PinchGestureHandler;<br>差异内容：onActionEnd(event: Callback\<GestureEvent>): PinchGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：PinchGestureHandler；<br>API声明：onActionCancel(event: Callback\<void>): PinchGestureHandler;<br>差异内容：onActionCancel(event: Callback\<void>): PinchGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：interface RotationGestureHandlerOptions<br>差异内容：interface RotationGestureHandlerOptions|component/gesture.d.ts|
|新增API|NA|类名：RotationGestureHandlerOptions；<br>API声明：fingers?: number;<br>差异内容：fingers?: number;|component/gesture.d.ts|
|新增API|NA|类名：RotationGestureHandlerOptions；<br>API声明：angle?: number;<br>差异内容：angle?: number;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class RotationGestureHandler<br>差异内容：declare class RotationGestureHandler|component/gesture.d.ts|
|新增API|NA|类名：RotationGestureHandler；<br>API声明：onActionStart(event: Callback\<GestureEvent>): RotationGestureHandler;<br>差异内容：onActionStart(event: Callback\<GestureEvent>): RotationGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：RotationGestureHandler；<br>API声明：onActionUpdate(event: Callback\<GestureEvent>): RotationGestureHandler;<br>差异内容：onActionUpdate(event: Callback\<GestureEvent>): RotationGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：RotationGestureHandler；<br>API声明：onActionEnd(event: Callback\<GestureEvent>): RotationGestureHandler;<br>差异内容：onActionEnd(event: Callback\<GestureEvent>): RotationGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：RotationGestureHandler；<br>API声明：onActionCancel(event: Callback\<void>): RotationGestureHandler;<br>差异内容：onActionCancel(event: Callback\<void>): RotationGestureHandler;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：interface GestureGroupGestureHandlerOptions<br>差异内容：interface GestureGroupGestureHandlerOptions|component/gesture.d.ts|
|新增API|NA|类名：GestureGroupGestureHandlerOptions；<br>API声明：mode: GestureMode;<br>差异内容：mode: GestureMode;|component/gesture.d.ts|
|新增API|NA|类名：GestureGroupGestureHandlerOptions；<br>API声明：gestures: GestureHandler\<TapGestureHandler \| LongPressGestureHandler \| PanGestureHandler \| SwipeGestureHandler \| PinchGestureHandler \| RotationGestureHandler \| GestureGroupHandler>[];<br>差异内容：gestures: GestureHandler\<TapGestureHandler \| LongPressGestureHandler \| PanGestureHandler \| SwipeGestureHandler \| PinchGestureHandler \| RotationGestureHandler \| GestureGroupHandler>[];|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class GestureGroupHandler<br>差异内容：declare class GestureGroupHandler|component/gesture.d.ts|
|新增API|NA|类名：GestureGroupHandler；<br>API声明：onCancel(event: Callback\<void>): GestureGroupHandler;<br>差异内容：onCancel(event: Callback\<void>): GestureGroupHandler;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum GesturePriority<br>差异内容：declare enum GesturePriority|component/gesture.d.ts|
|新增API|NA|类名：GesturePriority；<br>API声明：NORMAL = 0<br>差异内容：NORMAL = 0|component/gesture.d.ts|
|新增API|NA|类名：GesturePriority；<br>API声明：PRIORITY = 1<br>差异内容：PRIORITY = 1|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum GestureRecognizerState<br>差异内容：declare enum GestureRecognizerState|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizerState；<br>API声明：READY = 0<br>差异内容：READY = 0|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizerState；<br>API声明：DETECTING = 1<br>差异内容：DETECTING = 1|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizerState；<br>API声明：PENDING = 2<br>差异内容：PENDING = 2|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizerState；<br>API声明：BLOCKED = 3<br>差异内容：BLOCKED = 3|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizerState；<br>API声明：SUCCESSFUL = 4<br>差异内容：SUCCESSFUL = 4|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizerState；<br>API声明：FAILED = 5<br>差异内容：FAILED = 5|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ScrollableTargetInfo<br>差异内容：declare class ScrollableTargetInfo|component/gesture.d.ts|
|新增API|NA|类名：ScrollableTargetInfo；<br>API声明：isBegin(): boolean;<br>差异内容：isBegin(): boolean;|component/gesture.d.ts|
|新增API|NA|类名：ScrollableTargetInfo；<br>API声明：isEnd(): boolean;<br>差异内容：isEnd(): boolean;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class EventTargetInfo<br>差异内容：declare class EventTargetInfo|component/gesture.d.ts|
|新增API|NA|类名：EventTargetInfo；<br>API声明：getId(): string;<br>差异内容：getId(): string;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class GestureRecognizer<br>差异内容：declare class GestureRecognizer|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizer；<br>API声明：getTag(): string;<br>差异内容：getTag(): string;|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizer；<br>API声明：getType(): GestureControl.GestureType;<br>差异内容：getType(): GestureControl.GestureType;|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizer；<br>API声明：isBuiltIn(): boolean;<br>差异内容：isBuiltIn(): boolean;|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizer；<br>API声明：setEnabled(isEnabled: boolean): void;<br>差异内容：setEnabled(isEnabled: boolean): void;|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizer；<br>API声明：isEnabled(): boolean;<br>差异内容：isEnabled(): boolean;|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizer；<br>API声明：getState(): GestureRecognizerState;<br>差异内容：getState(): GestureRecognizerState;|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizer；<br>API声明：getEventTargetInfo(): EventTargetInfo;<br>差异内容：getEventTargetInfo(): EventTargetInfo;|component/gesture.d.ts|
|新增API|NA|类名：GestureRecognizer；<br>API声明：isValid(): boolean;<br>差异内容：isValid(): boolean;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class PanRecognizer<br>差异内容：declare class PanRecognizer|component/gesture.d.ts|
|新增API|NA|类名：PanRecognizer；<br>API声明：getPanGestureOptions(): PanGestureOptions;<br>差异内容：getPanGestureOptions(): PanGestureOptions;|component/gesture.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum GridItemAlignment<br>差异内容：declare enum GridItemAlignment|component/grid.d.ts|
|新增API|NA|类名：GridItemAlignment；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|component/grid.d.ts|
|新增API|NA|类名：GridItemAlignment；<br>API声明：STRETCH = 1<br>差异内容：STRETCH = 1|component/grid.d.ts|
|新增API|NA|类名：GridAttribute；<br>API声明：alignItems(alignment: Optional\<GridItemAlignment>): GridAttribute;<br>差异内容：alignItems(alignment: Optional\<GridItemAlignment>): GridAttribute;|component/grid.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type DrawingColorFilter = import('../api/@ohos.graphics.drawing').default.ColorFilter;<br>差异内容：declare type DrawingColorFilter = import('../api/@ohos.graphics.drawing').default.ColorFilter;|component/image.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type DrawingLattice = import('../api/@ohos.graphics.drawing').default.Lattice;<br>差异内容：declare type DrawingLattice = import('../api/@ohos.graphics.drawing').default.Lattice;|component/image.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ImageContent<br>差异内容：declare enum ImageContent|component/image.d.ts|
|新增API|NA|类名：ImageContent；<br>API声明：EMPTY = 0<br>差异内容：EMPTY = 0|component/image.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum DynamicRangeMode<br>差异内容：declare enum DynamicRangeMode|component/image.d.ts|
|新增API|NA|类名：DynamicRangeMode；<br>API声明：HIGH = 0<br>差异内容：HIGH = 0|component/image.d.ts|
|新增API|NA|类名：DynamicRangeMode；<br>API声明：CONSTRAINT = 1<br>差异内容：CONSTRAINT = 1|component/image.d.ts|
|新增API|NA|类名：DynamicRangeMode；<br>API声明：STANDARD = 2<br>差异内容：STANDARD = 2|component/image.d.ts|
|新增API|NA|类名：ImageAttribute；<br>API声明：dynamicRangeMode(value: DynamicRangeMode): ImageAttribute;<br>差异内容：dynamicRangeMode(value: DynamicRangeMode): ImageAttribute;|component/image.d.ts|
|新增API|NA|类名：ImageAttribute；<br>API声明：privacySensitive(supported: boolean): ImageAttribute;<br>差异内容：privacySensitive(supported: boolean): ImageAttribute;|component/image.d.ts|
|新增API|NA|类名：ResizableOptions；<br>API声明：lattice?: DrawingLattice;<br>差异内容：lattice?: DrawingLattice;|component/image.d.ts|
|新增API|NA|类名：ImageSpanAttribute；<br>API声明：onComplete(callback: ImageCompleteCallback): ImageSpanAttribute;<br>差异内容：onComplete(callback: ImageCompleteCallback): ImageSpanAttribute;|component/image_span.d.ts|
|新增API|NA|类名：ImageSpanAttribute；<br>API声明：onError(callback: ImageErrorCallback): ImageSpanAttribute;<br>差异内容：onError(callback: ImageErrorCallback): ImageSpanAttribute;|component/image_span.d.ts|
|新增API|NA|类名：ImageSpanAttribute；<br>API声明：alt(value: PixelMap): ImageSpanAttribute;<br>差异内容：alt(value: PixelMap): ImageSpanAttribute;|component/image_span.d.ts|
|新增API|NA|类名：global；<br>API声明：type ImageCompleteCallback = (result: ImageLoadResult) => void;<br>差异内容：type ImageCompleteCallback = (result: ImageLoadResult) => void;|component/image_span.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ImageLoadResult<br>差异内容：declare interface ImageLoadResult|component/image_span.d.ts|
|新增API|NA|类名：ImageLoadResult；<br>API声明：width: number;<br>差异内容：width: number;|component/image_span.d.ts|
|新增API|NA|类名：ImageLoadResult；<br>API声明：height: number;<br>差异内容：height: number;|component/image_span.d.ts|
|新增API|NA|类名：ImageLoadResult；<br>API声明：componentWidth: number;<br>差异内容：componentWidth: number;|component/image_span.d.ts|
|新增API|NA|类名：ImageLoadResult；<br>API声明：componentHeight: number;<br>差异内容：componentHeight: number;|component/image_span.d.ts|
|新增API|NA|类名：ImageLoadResult；<br>API声明：loadingStatus: number;<br>差异内容：loadingStatus: number;|component/image_span.d.ts|
|新增API|NA|类名：ImageLoadResult；<br>API声明：contentWidth: number;<br>差异内容：contentWidth: number;|component/image_span.d.ts|
|新增API|NA|类名：ImageLoadResult；<br>API声明：contentHeight: number;<br>差异内容：contentHeight: number;|component/image_span.d.ts|
|新增API|NA|类名：ImageLoadResult；<br>API声明：contentOffsetX: number;<br>差异内容：contentOffsetX: number;|component/image_span.d.ts|
|新增API|NA|类名：ImageLoadResult；<br>API声明：contentOffsetY: number;<br>差异内容：contentOffsetY: number;|component/image_span.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum DataOperationType<br>差异内容：declare enum DataOperationType|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataOperationType；<br>API声明：ADD = 'add'<br>差异内容：ADD = 'add'|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataOperationType；<br>API声明：DELETE = 'delete'<br>差异内容：DELETE = 'delete'|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataOperationType；<br>API声明：EXCHANGE = 'exchange'<br>差异内容：EXCHANGE = 'exchange'|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataOperationType；<br>API声明：MOVE = 'move'<br>差异内容：MOVE = 'move'|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataOperationType；<br>API声明：CHANGE = 'change'<br>差异内容：CHANGE = 'change'|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataOperationType；<br>API声明：RELOAD = 'reload'<br>差异内容：RELOAD = 'reload'|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：interface DataAddOperation<br>差异内容：interface DataAddOperation|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataAddOperation；<br>API声明：type: DataOperationType.ADD;<br>差异内容：type: DataOperationType.ADD;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataAddOperation；<br>API声明：index: number;<br>差异内容：index: number;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataAddOperation；<br>API声明：count?: number;<br>差异内容：count?: number;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataAddOperation；<br>API声明：key?: string \| Array\<string>;<br>差异内容：key?: string \| Array\<string>;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：interface DataDeleteOperation<br>差异内容：interface DataDeleteOperation|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataDeleteOperation；<br>API声明：type: DataOperationType.DELETE;<br>差异内容：type: DataOperationType.DELETE;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataDeleteOperation；<br>API声明：index: number;<br>差异内容：index: number;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataDeleteOperation；<br>API声明：count?: number;<br>差异内容：count?: number;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：interface DataChangeOperation<br>差异内容：interface DataChangeOperation|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataChangeOperation；<br>API声明：type: DataOperationType.CHANGE;<br>差异内容：type: DataOperationType.CHANGE;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataChangeOperation；<br>API声明：index: number;<br>差异内容：index: number;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataChangeOperation；<br>API声明：key?: string;<br>差异内容：key?: string;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：interface MoveIndex<br>差异内容：interface MoveIndex|component/lazy_for_each.d.ts|
|新增API|NA|类名：MoveIndex；<br>API声明：from: number;<br>差异内容：from: number;|component/lazy_for_each.d.ts|
|新增API|NA|类名：MoveIndex；<br>API声明：to: number;<br>差异内容：to: number;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：interface ExchangeIndex<br>差异内容：interface ExchangeIndex|component/lazy_for_each.d.ts|
|新增API|NA|类名：ExchangeIndex；<br>API声明：start: number;<br>差异内容：start: number;|component/lazy_for_each.d.ts|
|新增API|NA|类名：ExchangeIndex；<br>API声明：end: number;<br>差异内容：end: number;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：interface ExchangeKey<br>差异内容：interface ExchangeKey|component/lazy_for_each.d.ts|
|新增API|NA|类名：ExchangeKey；<br>API声明：start: string;<br>差异内容：start: string;|component/lazy_for_each.d.ts|
|新增API|NA|类名：ExchangeKey；<br>API声明：end: string;<br>差异内容：end: string;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：interface DataMoveOperation<br>差异内容：interface DataMoveOperation|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataMoveOperation；<br>API声明：type: DataOperationType.MOVE;<br>差异内容：type: DataOperationType.MOVE;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataMoveOperation；<br>API声明：index: MoveIndex;<br>差异内容：index: MoveIndex;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataMoveOperation；<br>API声明：key?: string;<br>差异内容：key?: string;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：interface DataExchangeOperation<br>差异内容：interface DataExchangeOperation|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataExchangeOperation；<br>API声明：type: DataOperationType.EXCHANGE;<br>差异内容：type: DataOperationType.EXCHANGE;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataExchangeOperation；<br>API声明：index: ExchangeIndex;<br>差异内容：index: ExchangeIndex;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataExchangeOperation；<br>API声明：key?: ExchangeKey;<br>差异内容：key?: ExchangeKey;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：interface DataReloadOperation<br>差异内容：interface DataReloadOperation|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataReloadOperation；<br>API声明：type: DataOperationType.RELOAD;<br>差异内容：type: DataOperationType.RELOAD;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type DataOperation = DataAddOperation \| DataDeleteOperation \| DataChangeOperation \| DataMoveOperation \| DataExchangeOperation \| DataReloadOperation;<br>差异内容：declare type DataOperation = DataAddOperation \| DataDeleteOperation \| DataChangeOperation \| DataMoveOperation \| DataExchangeOperation \| DataReloadOperation;|component/lazy_for_each.d.ts|
|新增API|NA|类名：DataChangeListener；<br>API声明：onDatasetChange(dataOperations: DataOperation[]): void;<br>差异内容：onDatasetChange(dataOperations: DataOperation[]): void;|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class LazyForEachAttribute<br>差异内容：declare class LazyForEachAttribute|component/lazy_for_each.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ListItemGroupArea<br>差异内容：declare enum ListItemGroupArea|component/list.d.ts|
|新增API|NA|类名：ListItemGroupArea；<br>API声明：NONE = 0<br>差异内容：NONE = 0|component/list.d.ts|
|新增API|NA|类名：ListItemGroupArea；<br>API声明：IN_LIST_ITEM_AREA = 1<br>差异内容：IN_LIST_ITEM_AREA = 1|component/list.d.ts|
|新增API|NA|类名：ListItemGroupArea；<br>API声明：IN_HEADER_AREA = 2<br>差异内容：IN_HEADER_AREA = 2|component/list.d.ts|
|新增API|NA|类名：ListItemGroupArea；<br>API声明：IN_FOOTER_AREA = 3<br>差异内容：IN_FOOTER_AREA = 3|component/list.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface VisibleListContentInfo<br>差异内容：declare interface VisibleListContentInfo|component/list.d.ts|
|新增API|NA|类名：VisibleListContentInfo；<br>API声明：index: number;<br>差异内容：index: number;|component/list.d.ts|
|新增API|NA|类名：VisibleListContentInfo；<br>API声明：itemGroupArea?: ListItemGroupArea;<br>差异内容：itemGroupArea?: ListItemGroupArea;|component/list.d.ts|
|新增API|NA|类名：VisibleListContentInfo；<br>API声明：itemIndexInGroup?: number;<br>差异内容：itemIndexInGroup?: number;|component/list.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type OnScrollVisibleContentChangeCallback = (start: VisibleListContentInfo, end: VisibleListContentInfo) => void;<br>差异内容：declare type OnScrollVisibleContentChangeCallback = (start: VisibleListContentInfo, end: VisibleListContentInfo) => void;|component/list.d.ts|
|新增API|NA|类名：ListAttribute；<br>API声明：childrenMainSize(value: ChildrenMainSize): ListAttribute;<br>差异内容：childrenMainSize(value: ChildrenMainSize): ListAttribute;|component/list.d.ts|
|新增API|NA|类名：ListAttribute；<br>API声明：maintainVisibleContentPosition(enabled: boolean): ListAttribute;<br>差异内容：maintainVisibleContentPosition(enabled: boolean): ListAttribute;|component/list.d.ts|
|新增API|NA|类名：ListAttribute；<br>API声明：onScrollVisibleContentChange(handler: OnScrollVisibleContentChangeCallback): ListAttribute;<br>差异内容：onScrollVisibleContentChange(handler: OnScrollVisibleContentChangeCallback): ListAttribute;|component/list.d.ts|
|新增API|NA|类名：ListItemGroupAttribute；<br>API声明：childrenMainSize(value: ChildrenMainSize): ListItemGroupAttribute;<br>差异内容：childrenMainSize(value: ChildrenMainSize): ListItemGroupAttribute;|component/list_item_group.d.ts|
|新增API|NA|类名：LoadingProgressAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<LoadingProgressConfiguration>): LoadingProgressAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<LoadingProgressConfiguration>): LoadingProgressAttribute;|component/loading_progress.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LoadingProgressConfiguration<br>差异内容：declare interface LoadingProgressConfiguration|component/loading_progress.d.ts|
|新增API|NA|类名：LoadingProgressConfiguration；<br>API声明：enableLoading: boolean;<br>差异内容：enableLoading: boolean;|component/loading_progress.d.ts|
|新增API|NA|类名：MarqueeAttribute；<br>API声明：marqueeUpdateStrategy(value: MarqueeUpdateStrategy): MarqueeAttribute;<br>差异内容：marqueeUpdateStrategy(value: MarqueeUpdateStrategy): MarqueeAttribute;|component/marquee.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum SubMenuExpandingMode<br>差异内容：declare enum SubMenuExpandingMode|component/menu.d.ts|
|新增API|NA|类名：SubMenuExpandingMode；<br>API声明：SIDE_EXPAND = 0<br>差异内容：SIDE_EXPAND = 0|component/menu.d.ts|
|新增API|NA|类名：SubMenuExpandingMode；<br>API声明：EMBEDDED_EXPAND = 1<br>差异内容：EMBEDDED_EXPAND = 1|component/menu.d.ts|
|新增API|NA|类名：SubMenuExpandingMode；<br>API声明：STACK_EXPAND = 2<br>差异内容：STACK_EXPAND = 2|component/menu.d.ts|
|新增API|NA|类名：MenuAttribute；<br>API声明：menuItemDivider(options: DividerStyleOptions \| undefined): MenuAttribute;<br>差异内容：menuItemDivider(options: DividerStyleOptions \| undefined): MenuAttribute;|component/menu.d.ts|
|新增API|NA|类名：MenuAttribute；<br>API声明：menuItemGroupDivider(options: DividerStyleOptions \| undefined): MenuAttribute;<br>差异内容：menuItemGroupDivider(options: DividerStyleOptions \| undefined): MenuAttribute;|component/menu.d.ts|
|新增API|NA|类名：MenuAttribute；<br>API声明：subMenuExpandingMode(mode: SubMenuExpandingMode): MenuAttribute;<br>差异内容：subMenuExpandingMode(mode: SubMenuExpandingMode): MenuAttribute;|component/menu.d.ts|
|新增API|NA|类名：MenuItemOptions；<br>API声明：symbolStartIcon?: SymbolGlyphModifier;<br>差异内容：symbolStartIcon?: SymbolGlyphModifier;|component/menu_item.d.ts|
|新增API|NA|类名：MenuItemOptions；<br>API声明：symbolEndIcon?: SymbolGlyphModifier;<br>差异内容：symbolEndIcon?: SymbolGlyphModifier;|component/menu_item.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type SystemBarStyle = import('../api/@ohos.window').default.SystemBarStyle;<br>差异内容：declare type SystemBarStyle = import('../api/@ohos.window').default.SystemBarStyle;|component/navigation.d.ts|
|新增API|NA|类名：NavigationMenuItem；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：symbolIcon?: SymbolGlyphModifier;|component/navigation.d.ts|
|新增API|NA|类名：NavigationMenuItem；<br>API声明：isEnabled?: boolean;<br>差异内容：isEnabled?: boolean;|component/navigation.d.ts|
|新增API|NA|类名：NavPathInfo；<br>API声明：isEntry?: boolean;<br>差异内容：isEntry?: boolean;|component/navigation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum LaunchMode<br>差异内容：declare enum LaunchMode|component/navigation.d.ts|
|新增API|NA|类名：LaunchMode；<br>API声明：STANDARD = 0<br>差异内容：STANDARD = 0|component/navigation.d.ts|
|新增API|NA|类名：LaunchMode；<br>API声明：MOVE_TO_TOP_SINGLETON = 1<br>差异内容：MOVE_TO_TOP_SINGLETON = 1|component/navigation.d.ts|
|新增API|NA|类名：LaunchMode；<br>API声明：POP_TO_SINGLETON = 2<br>差异内容：POP_TO_SINGLETON = 2|component/navigation.d.ts|
|新增API|NA|类名：LaunchMode；<br>API声明：NEW_INSTANCE = 3<br>差异内容：NEW_INSTANCE = 3|component/navigation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface NavigationOptions<br>差异内容：declare interface NavigationOptions|component/navigation.d.ts|
|新增API|NA|类名：NavigationOptions；<br>API声明：launchMode?: LaunchMode;<br>差异内容：launchMode?: LaunchMode;|component/navigation.d.ts|
|新增API|NA|类名：NavigationOptions；<br>API声明：animated?: boolean;<br>差异内容：animated?: boolean;|component/navigation.d.ts|
|新增API|NA|类名：NavPathStack；<br>API声明：removeByNavDestinationId(navDestinationId: string): boolean;<br>差异内容：removeByNavDestinationId(navDestinationId: string): boolean;|component/navigation.d.ts|
|新增API|NA|类名：NavPathStack；<br>API声明：setInterception(interception: NavigationInterception): void;<br>差异内容：setInterception(interception: NavigationInterception): void;|component/navigation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type NavBar = 'navBar';<br>差异内容：declare type NavBar = 'navBar';|component/navigation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type InterceptionShowCallback = (from: NavDestinationContext \| NavBar, to: NavDestinationContext \| NavBar, operation: NavigationOperation, isAnimated: boolean) => void;<br>差异内容：declare type InterceptionShowCallback = (from: NavDestinationContext \| NavBar, to: NavDestinationContext \| NavBar, operation: NavigationOperation, isAnimated: boolean) => void;|component/navigation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type InterceptionModeCallback = (mode: NavigationMode) => void;<br>差异内容：declare type InterceptionModeCallback = (mode: NavigationMode) => void;|component/navigation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface NavigationInterception<br>差异内容：declare interface NavigationInterception|component/navigation.d.ts|
|新增API|NA|类名：NavigationInterception；<br>API声明：willShow?: InterceptionShowCallback;<br>差异内容：willShow?: InterceptionShowCallback;|component/navigation.d.ts|
|新增API|NA|类名：NavigationInterception；<br>API声明：didShow?: InterceptionShowCallback;<br>差异内容：didShow?: InterceptionShowCallback;|component/navigation.d.ts|
|新增API|NA|类名：NavigationInterception；<br>API声明：modeChange?: InterceptionModeCallback;<br>差异内容：modeChange?: InterceptionModeCallback;|component/navigation.d.ts|
|新增API|NA|类名：ToolbarItem；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：symbolIcon?: SymbolGlyphModifier;|component/navigation.d.ts|
|新增API|NA|类名：ToolbarItem；<br>API声明：activeSymbolIcon?: SymbolGlyphModifier;<br>差异内容：activeSymbolIcon?: SymbolGlyphModifier;|component/navigation.d.ts|
|新增API|NA|类名：NavigationTitleOptions；<br>API声明：barStyle?: BarStyle;<br>差异内容：barStyle?: BarStyle;|component/navigation.d.ts|
|新增API|NA|类名：NavigationTitleOptions；<br>API声明：paddingStart?: LengthMetrics;<br>差异内容：paddingStart?: LengthMetrics;|component/navigation.d.ts|
|新增API|NA|类名：NavigationTitleOptions；<br>API声明：paddingEnd?: LengthMetrics;<br>差异内容：paddingEnd?: LengthMetrics;|component/navigation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum BarStyle<br>差异内容：declare enum BarStyle|component/navigation.d.ts|
|新增API|NA|类名：BarStyle；<br>API声明：STANDARD = 0<br>差异内容：STANDARD = 0|component/navigation.d.ts|
|新增API|NA|类名：BarStyle；<br>API声明：STACK = 1<br>差异内容：STACK = 1|component/navigation.d.ts|
|新增API|NA|类名：NavigationAttribute；<br>API声明：ignoreLayoutSafeArea(types?: Array\<LayoutSafeAreaType>, edges?: Array\<LayoutSafeAreaEdge>): NavigationAttribute;<br>差异内容：ignoreLayoutSafeArea(types?: Array\<LayoutSafeAreaType>, edges?: Array\<LayoutSafeAreaEdge>): NavigationAttribute;|component/navigation.d.ts|
|新增API|NA|类名：NavigationAttribute；<br>API声明：systemBarStyle(style: Optional\<SystemBarStyle>): NavigationAttribute;<br>差异内容：systemBarStyle(style: Optional\<SystemBarStyle>): NavigationAttribute;|component/navigation.d.ts|
|新增API|NA|类名：NavigationAnimatedTransition；<br>API声明：isInteractive?: boolean;<br>差异内容：isInteractive?: boolean;|component/navigation.d.ts|
|新增API|NA|类名：NavigationTransitionProxy；<br>API声明：isInteractive?: boolean;<br>差异内容：isInteractive?: boolean;|component/navigation.d.ts|
|新增API|NA|类名：NavigationTransitionProxy；<br>API声明：cancelTransition?(): void;<br>差异内容：cancelTransition?(): void;|component/navigation.d.ts|
|新增API|NA|类名：NavigationTransitionProxy；<br>API声明：updateTransition?(progress: number): void;<br>差异内容：updateTransition?(progress: number): void;|component/navigation.d.ts|
|新增API|NA|类名：NavContentInfo；<br>API声明：param?: Object;<br>差异内容：param?: Object;|component/navigation.d.ts|
|新增API|NA|类名：NavContentInfo；<br>API声明：navDestinationId?: string;<br>差异内容：navDestinationId?: string;|component/navigation.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface RouteMapConfig<br>差异内容：declare interface RouteMapConfig|component/nav_destination.d.ts|
|新增API|NA|类名：RouteMapConfig；<br>API声明：name: string;<br>差异内容：name: string;|component/nav_destination.d.ts|
|新增API|NA|类名：RouteMapConfig；<br>API声明：pageSourceFile: string;<br>差异内容：pageSourceFile: string;|component/nav_destination.d.ts|
|新增API|NA|类名：RouteMapConfig；<br>API声明：data: Object;<br>差异内容：data: Object;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationContext；<br>API声明：navDestinationId?: string;<br>差异内容：navDestinationId?: string;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationContext；<br>API声明：getConfigInRouteMap(): RouteMapConfig \| undefined;<br>差异内容：getConfigInRouteMap(): RouteMapConfig \| undefined;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：menus(value: Array\<NavigationMenuItem> \| CustomBuilder): NavDestinationAttribute;<br>差异内容：menus(value: Array\<NavigationMenuItem> \| CustomBuilder): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：onWillAppear(callback: Callback\<void>): NavDestinationAttribute;<br>差异内容：onWillAppear(callback: Callback\<void>): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：onWillDisappear(callback: Callback\<void>): NavDestinationAttribute;<br>差异内容：onWillDisappear(callback: Callback\<void>): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：onWillShow(callback: Callback\<void>): NavDestinationAttribute;<br>差异内容：onWillShow(callback: Callback\<void>): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：onWillHide(callback: Callback\<void>): NavDestinationAttribute;<br>差异内容：onWillHide(callback: Callback\<void>): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：ignoreLayoutSafeArea(types?: Array\<LayoutSafeAreaType>, edges?: Array\<LayoutSafeAreaEdge>): NavDestinationAttribute;<br>差异内容：ignoreLayoutSafeArea(types?: Array\<LayoutSafeAreaType>, edges?: Array\<LayoutSafeAreaEdge>): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：NavDestinationAttribute；<br>API声明：systemBarStyle(style: Optional\<SystemBarStyle>): NavDestinationAttribute;<br>差异内容：systemBarStyle(style: Optional\<SystemBarStyle>): NavDestinationAttribute;|component/nav_destination.d.ts|
|新增API|NA|类名：SlideEffect；<br>API声明：START = 5<br>差异内容：START = 5|component/page_transition.d.ts|
|新增API|NA|类名：SlideEffect；<br>API声明：END = 6<br>差异内容：END = 6|component/page_transition.d.ts|
|新增API|NA|类名：global；<br>API声明：interface EmitterProperty<br>差异内容：interface EmitterProperty|component/particle.d.ts|
|新增API|NA|类名：EmitterProperty；<br>API声明：index: number;<br>差异内容：index: number;|component/particle.d.ts|
|新增API|NA|类名：EmitterProperty；<br>API声明：emitRate?: number;<br>差异内容：emitRate?: number;|component/particle.d.ts|
|新增API|NA|类名：EmitterProperty；<br>API声明：position?: PositionT\<number>;<br>差异内容：position?: PositionT\<number>;|component/particle.d.ts|
|新增API|NA|类名：EmitterProperty；<br>API声明：size?: SizeT\<number>;<br>差异内容：size?: SizeT\<number>;|component/particle.d.ts|
|新增API|NA|类名：ParticleColorPropertyOptions；<br>API声明：distributionType?: DistributionType;<br>差异内容：distributionType?: DistributionType;|component/particle.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum DistributionType<br>差异内容：declare enum DistributionType|component/particle.d.ts|
|新增API|NA|类名：DistributionType；<br>API声明：UNIFORM = 0<br>差异内容：UNIFORM = 0|component/particle.d.ts|
|新增API|NA|类名：DistributionType；<br>API声明：GAUSSIAN = 1<br>差异内容：GAUSSIAN = 1|component/particle.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type SizeT\<T> = import('../api/arkui/Graphics').SizeT\<T>;<br>差异内容：declare type SizeT\<T> = import('../api/arkui/Graphics').SizeT\<T>;|component/particle.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type PositionT\<T> = import('../api/arkui/Graphics').PositionT\<T>;<br>差异内容：declare type PositionT\<T> = import('../api/arkui/Graphics').PositionT\<T>;|component/particle.d.ts|
|新增API|NA|类名：ParticleAttribute；<br>API声明：disturbanceFields(fields: Array\<DisturbanceFieldOptions>): ParticleAttribute;<br>差异内容：disturbanceFields(fields: Array\<DisturbanceFieldOptions>): ParticleAttribute;|component/particle.d.ts|
|新增API|NA|类名：ParticleAttribute；<br>API声明：emitter(value: Array\<EmitterProperty>): ParticleAttribute;<br>差异内容：emitter(value: Array\<EmitterProperty>): ParticleAttribute;|component/particle.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DisturbanceFieldOptions<br>差异内容：declare interface DisturbanceFieldOptions|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldOptions；<br>API声明：strength?: number;<br>差异内容：strength?: number;|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldOptions；<br>API声明：shape?: DisturbanceFieldShape;<br>差异内容：shape?: DisturbanceFieldShape;|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldOptions；<br>API声明：size?: SizeT\<number>;<br>差异内容：size?: SizeT\<number>;|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldOptions；<br>API声明：position?: PositionT\<number>;<br>差异内容：position?: PositionT\<number>;|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldOptions；<br>API声明：feather?: number;<br>差异内容：feather?: number;|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldOptions；<br>API声明：noiseScale?: number;<br>差异内容：noiseScale?: number;|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldOptions；<br>API声明：noiseFrequency?: number;<br>差异内容：noiseFrequency?: number;|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldOptions；<br>API声明：noiseAmplitude?: number;<br>差异内容：noiseAmplitude?: number;|component/particle.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum DisturbanceFieldShape<br>差异内容：declare enum DisturbanceFieldShape|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldShape；<br>API声明：RECT<br>差异内容：RECT|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldShape；<br>API声明：CIRCLE<br>差异内容：CIRCLE|component/particle.d.ts|
|新增API|NA|类名：DisturbanceFieldShape；<br>API声明：ELLIPSE<br>差异内容：ELLIPSE|component/particle.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface CircleStyleOptions<br>差异内容：declare interface CircleStyleOptions|component/pattern_lock.d.ts|
|新增API|NA|类名：CircleStyleOptions；<br>API声明：color?: ResourceColor;<br>差异内容：color?: ResourceColor;|component/pattern_lock.d.ts|
|新增API|NA|类名：CircleStyleOptions；<br>API声明：radius?: LengthMetrics;<br>差异内容：radius?: LengthMetrics;|component/pattern_lock.d.ts|
|新增API|NA|类名：CircleStyleOptions；<br>API声明：enableWaveEffect?: boolean;<br>差异内容：enableWaveEffect?: boolean;|component/pattern_lock.d.ts|
|新增API|NA|类名：PatternLockAttribute；<br>API声明：activateCircleStyle(options: Optional\<CircleStyleOptions>): PatternLockAttribute;<br>差异内容：activateCircleStyle(options: Optional\<CircleStyleOptions>): PatternLockAttribute;|component/pattern_lock.d.ts|
|新增API|NA|类名：ProgressAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<ProgressConfiguration>): ProgressAttribute\<Type>;<br>差异内容：contentModifier(modifier: ContentModifier\<ProgressConfiguration>): ProgressAttribute\<Type>;|component/progress.d.ts|
|新增API|NA|类名：ProgressAttribute；<br>API声明：privacySensitive(isPrivacySensitiveMode: Optional\<boolean>): ProgressAttribute\<Type>;<br>差异内容：privacySensitive(isPrivacySensitiveMode: Optional\<boolean>): ProgressAttribute\<Type>;|component/progress.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ProgressConfiguration<br>差异内容：declare interface ProgressConfiguration|component/progress.d.ts|
|新增API|NA|类名：ProgressConfiguration；<br>API声明：value: number;<br>差异内容：value: number;|component/progress.d.ts|
|新增API|NA|类名：ProgressConfiguration；<br>API声明：total: number;<br>差异内容：total: number;|component/progress.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum RadioIndicatorType<br>差异内容：declare enum RadioIndicatorType|component/radio.d.ts|
|新增API|NA|类名：RadioIndicatorType；<br>API声明：TICK = 0<br>差异内容：TICK = 0|component/radio.d.ts|
|新增API|NA|类名：RadioIndicatorType；<br>API声明：DOT = 1<br>差异内容：DOT = 1|component/radio.d.ts|
|新增API|NA|类名：RadioIndicatorType；<br>API声明：CUSTOM = 2<br>差异内容：CUSTOM = 2|component/radio.d.ts|
|新增API|NA|类名：RadioOptions；<br>API声明：indicatorType?: RadioIndicatorType;<br>差异内容：indicatorType?: RadioIndicatorType;|component/radio.d.ts|
|新增API|NA|类名：RadioOptions；<br>API声明：indicatorBuilder?: CustomBuilder;<br>差异内容：indicatorBuilder?: CustomBuilder;|component/radio.d.ts|
|新增API|NA|类名：RadioAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<RadioConfiguration>): RadioAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<RadioConfiguration>): RadioAttribute;|component/radio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface RadioConfiguration<br>差异内容：declare interface RadioConfiguration|component/radio.d.ts|
|新增API|NA|类名：RadioConfiguration；<br>API声明：value: string;<br>差异内容：value: string;|component/radio.d.ts|
|新增API|NA|类名：RadioConfiguration；<br>API声明：checked: boolean;<br>差异内容：checked: boolean;|component/radio.d.ts|
|新增API|NA|类名：RadioConfiguration；<br>API声明：triggerChange: Callback\<boolean>;<br>差异内容：triggerChange: Callback\<boolean>;|component/radio.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface RatingConfiguration<br>差异内容：declare interface RatingConfiguration|component/rating.d.ts|
|新增API|NA|类名：RatingConfiguration；<br>API声明：rating: number;<br>差异内容：rating: number;|component/rating.d.ts|
|新增API|NA|类名：RatingConfiguration；<br>API声明：indicator: boolean;<br>差异内容：indicator: boolean;|component/rating.d.ts|
|新增API|NA|类名：RatingConfiguration；<br>API声明：stars: number;<br>差异内容：stars: number;|component/rating.d.ts|
|新增API|NA|类名：RatingConfiguration；<br>API声明：stepSize: number;<br>差异内容：stepSize: number;|component/rating.d.ts|
|新增API|NA|类名：RatingConfiguration；<br>API声明：triggerChange: Callback\<number>;<br>差异内容：triggerChange: Callback\<number>;|component/rating.d.ts|
|新增API|NA|类名：RatingAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<RatingConfiguration>): RatingAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<RatingConfiguration>): RatingAttribute;|component/rating.d.ts|
|新增API|NA|类名：RefreshOptions；<br>API声明：promptText?: ResourceStr;<br>差异内容：promptText?: ResourceStr;|component/refresh.d.ts|
|新增API|NA|类名：RefreshOptions；<br>API声明：refreshingContent?: ComponentContent;<br>差异内容：refreshingContent?: ComponentContent;|component/refresh.d.ts|
|新增API|NA|类名：RefreshAttribute；<br>API声明：refreshOffset(value: number): RefreshAttribute;<br>差异内容：refreshOffset(value: number): RefreshAttribute;|component/refresh.d.ts|
|新增API|NA|类名：RefreshAttribute；<br>API声明：pullToRefresh(value: boolean): RefreshAttribute;<br>差异内容：pullToRefresh(value: boolean): RefreshAttribute;|component/refresh.d.ts|
|新增API|NA|类名：RefreshAttribute；<br>API声明：onOffsetChange(callback: Callback\<number>): RefreshAttribute;<br>差异内容：onOffsetChange(callback: Callback\<number>): RefreshAttribute;|component/refresh.d.ts|
|新增API|NA|类名：RefreshAttribute；<br>API声明：pullDownRatio(ratio: Optional\<number>): RefreshAttribute;<br>差异内容：pullDownRatio(ratio: Optional\<number>): RefreshAttribute;|component/refresh.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface GuideLinePosition<br>差异内容：declare interface GuideLinePosition|component/relative_container.d.ts|
|新增API|NA|类名：GuideLinePosition；<br>API声明：start?: Dimension;<br>差异内容：start?: Dimension;|component/relative_container.d.ts|
|新增API|NA|类名：GuideLinePosition；<br>API声明：end?: Dimension;<br>差异内容：end?: Dimension;|component/relative_container.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface GuideLineStyle<br>差异内容：declare interface GuideLineStyle|component/relative_container.d.ts|
|新增API|NA|类名：GuideLineStyle；<br>API声明：id: string;<br>差异内容：id: string;|component/relative_container.d.ts|
|新增API|NA|类名：GuideLineStyle；<br>API声明：direction: Axis;<br>差异内容：direction: Axis;|component/relative_container.d.ts|
|新增API|NA|类名：GuideLineStyle；<br>API声明：position: GuideLinePosition;<br>差异内容：position: GuideLinePosition;|component/relative_container.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum BarrierDirection<br>差异内容：declare enum BarrierDirection|component/relative_container.d.ts|
|新增API|NA|类名：BarrierDirection；<br>API声明：LEFT<br>差异内容：LEFT|component/relative_container.d.ts|
|新增API|NA|类名：BarrierDirection；<br>API声明：RIGHT<br>差异内容：RIGHT|component/relative_container.d.ts|
|新增API|NA|类名：BarrierDirection；<br>API声明：TOP<br>差异内容：TOP|component/relative_container.d.ts|
|新增API|NA|类名：BarrierDirection；<br>API声明：BOTTOM<br>差异内容：BOTTOM|component/relative_container.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum LocalizedBarrierDirection<br>差异内容：declare enum LocalizedBarrierDirection|component/relative_container.d.ts|
|新增API|NA|类名：LocalizedBarrierDirection；<br>API声明：START = 0<br>差异内容：START = 0|component/relative_container.d.ts|
|新增API|NA|类名：LocalizedBarrierDirection；<br>API声明：END = 1<br>差异内容：END = 1|component/relative_container.d.ts|
|新增API|NA|类名：LocalizedBarrierDirection；<br>API声明：TOP = 2<br>差异内容：TOP = 2|component/relative_container.d.ts|
|新增API|NA|类名：LocalizedBarrierDirection；<br>API声明：BOTTOM = 3<br>差异内容：BOTTOM = 3|component/relative_container.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface BarrierStyle<br>差异内容：declare interface BarrierStyle|component/relative_container.d.ts|
|新增API|NA|类名：BarrierStyle；<br>API声明：id: string;<br>差异内容：id: string;|component/relative_container.d.ts|
|新增API|NA|类名：BarrierStyle；<br>API声明：direction: BarrierDirection;<br>差异内容：direction: BarrierDirection;|component/relative_container.d.ts|
|新增API|NA|类名：BarrierStyle；<br>API声明：referencedId: Array\<string>;<br>差异内容：referencedId: Array\<string>;|component/relative_container.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedBarrierStyle<br>差异内容：declare interface LocalizedBarrierStyle|component/relative_container.d.ts|
|新增API|NA|类名：LocalizedBarrierStyle；<br>API声明：id: string;<br>差异内容：id: string;|component/relative_container.d.ts|
|新增API|NA|类名：LocalizedBarrierStyle；<br>API声明：localizedDirection: LocalizedBarrierDirection;<br>差异内容：localizedDirection: LocalizedBarrierDirection;|component/relative_container.d.ts|
|新增API|NA|类名：LocalizedBarrierStyle；<br>API声明：referencedId: Array\<string>;<br>差异内容：referencedId: Array\<string>;|component/relative_container.d.ts|
|新增API|NA|类名：RelativeContainerAttribute；<br>API声明：guideLine(value: Array\<GuideLineStyle>): RelativeContainerAttribute;<br>差异内容：guideLine(value: Array\<GuideLineStyle>): RelativeContainerAttribute;|component/relative_container.d.ts|
|新增API|NA|类名：RelativeContainerAttribute；<br>API声明：barrier(value: Array\<BarrierStyle>): RelativeContainerAttribute;<br>差异内容：barrier(value: Array\<BarrierStyle>): RelativeContainerAttribute;|component/relative_container.d.ts|
|新增API|NA|类名：RelativeContainerAttribute；<br>API声明：barrier(barrierStyle: Array\<LocalizedBarrierStyle>): RelativeContainerAttribute;<br>差异内容：barrier(barrierStyle: Array\<LocalizedBarrierStyle>): RelativeContainerAttribute;|component/relative_container.d.ts|
|新增API|NA|类名：RichEditorSpanType；<br>API声明：BUILDER = 3<br>差异内容：BUILDER = 3|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorTextStyle；<br>API声明：letterSpacing?: number \| string;<br>差异内容：letterSpacing?: number \| string;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorTextStyle；<br>API声明：lineHeight?: number \| string \| Resource;<br>差异内容：lineHeight?: number \| string \| Resource;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorTextStyle；<br>API声明：fontFeature?: string;<br>差异内容：fontFeature?: string;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorParagraphStyle；<br>API声明：wordBreak?: WordBreak;<br>差异内容：wordBreak?: WordBreak;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorParagraphStyle；<br>API声明：lineBreakStrategy?: LineBreakStrategy;<br>差异内容：lineBreakStrategy?: LineBreakStrategy;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorTextStyleResult；<br>API声明：textShadow?: Array\<ShadowOptions>;<br>差异内容：textShadow?: Array\<ShadowOptions>;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorTextStyleResult；<br>API声明：letterSpacing?: number;<br>差异内容：letterSpacing?: number;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorTextStyleResult；<br>API声明：lineHeight?: number;<br>差异内容：lineHeight?: number;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorTextStyleResult；<br>API声明：fontFeature?: string;<br>差异内容：fontFeature?: string;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorTextSpanResult；<br>API声明：paragraphStyle?: RichEditorParagraphStyle;<br>差异内容：paragraphStyle?: RichEditorParagraphStyle;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorTextSpanResult；<br>API声明：previewText?: string;<br>差异内容：previewText?: string;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorImageSpanStyleResult；<br>API声明：layoutStyle?: RichEditorLayoutStyle;<br>差异内容：layoutStyle?: RichEditorLayoutStyle;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface KeyboardOptions<br>差异内容：declare interface KeyboardOptions|component/rich_editor.d.ts|
|新增API|NA|类名：KeyboardOptions；<br>API声明：supportAvoidance?: boolean;<br>差异内容：supportAvoidance?: boolean;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface PlaceholderStyle<br>差异内容：declare interface PlaceholderStyle|component/rich_editor.d.ts|
|新增API|NA|类名：PlaceholderStyle；<br>API声明：font?: Font;<br>差异内容：font?: Font;|component/rich_editor.d.ts|
|新增API|NA|类名：PlaceholderStyle；<br>API声明：fontColor?: ResourceColor;<br>差异内容：fontColor?: ResourceColor;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorInsertValue；<br>API声明：previewText?: string;<br>差异内容：previewText?: string;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface RichEditorChangeValue<br>差异内容：declare interface RichEditorChangeValue|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorChangeValue；<br>API声明：rangeBefore: TextRange;<br>差异内容：rangeBefore: TextRange;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorChangeValue；<br>API声明：replacedSpans: Array\<RichEditorTextSpanResult>;<br>差异内容：replacedSpans: Array\<RichEditorTextSpanResult>;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorChangeValue；<br>API声明：replacedImageSpans: Array\<RichEditorImageSpanResult>;<br>差异内容：replacedImageSpans: Array\<RichEditorImageSpanResult>;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorChangeValue；<br>API声明：replacedSymbolSpans: Array\<RichEditorTextSpanResult>;<br>差异内容：replacedSymbolSpans: Array\<RichEditorTextSpanResult>;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface RichEditorStyledStringOptions<br>差异内容：declare interface RichEditorStyledStringOptions|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorStyledStringOptions；<br>API声明：controller: RichEditorStyledStringController;<br>差异内容：controller: RichEditorStyledStringController;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class RichEditorBaseController<br>差异内容：declare class RichEditorBaseController|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorBaseController；<br>API声明：isEditing(): boolean;<br>差异内容：isEditing(): boolean;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorBaseController；<br>API声明：stopEditing(): void;<br>差异内容：stopEditing(): void;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorBaseController；<br>API声明：getLayoutManager(): LayoutManager;<br>差异内容：getLayoutManager(): LayoutManager;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorBaseController；<br>API声明：getPreviewText(): PreviewText;<br>差异内容：getPreviewText(): PreviewText;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorController；<br>API声明：fromStyledString(value: StyledString): Array\<RichEditorSpan>;<br>差异内容：fromStyledString(value: StyledString): Array\<RichEditorSpan>;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorController；<br>API声明：toStyledString(value: RichEditorRange): StyledString;<br>差异内容：toStyledString(value: RichEditorRange): StyledString;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type RichEditorSpan = RichEditorImageSpanResult \| RichEditorTextSpanResult;<br>差异内容：declare type RichEditorSpan = RichEditorImageSpanResult \| RichEditorTextSpanResult;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class RichEditorStyledStringController<br>差异内容：declare class RichEditorStyledStringController|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorStyledStringController；<br>API声明：setStyledString(styledString: StyledString): void;<br>差异内容：setStyledString(styledString: StyledString): void;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorStyledStringController；<br>API声明：getStyledString(): MutableStyledString;<br>差异内容：getStyledString(): MutableStyledString;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorStyledStringController；<br>API声明：getSelection(): RichEditorRange;<br>差异内容：getSelection(): RichEditorRange;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorStyledStringController；<br>API声明：onContentChanged(listener: StyledStringChangedListener): void;<br>差异内容：onContentChanged(listener: StyledStringChangedListener): void;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：onSelectionChange(callback: Callback\<RichEditorRange>): RichEditorAttribute;<br>差异内容：onSelectionChange(callback: Callback\<RichEditorRange>): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：onDidIMEInput(callback: Callback\<TextRange>): RichEditorAttribute;<br>差异内容：onDidIMEInput(callback: Callback\<TextRange>): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：enablePreviewText(enable: boolean): RichEditorAttribute;<br>差异内容：enablePreviewText(enable: boolean): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：placeholder(value: ResourceStr, style?: PlaceholderStyle): RichEditorAttribute;<br>差异内容：placeholder(value: ResourceStr, style?: PlaceholderStyle): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：caretColor(value: ResourceColor): RichEditorAttribute;<br>差异内容：caretColor(value: ResourceColor): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：selectedBackgroundColor(value: ResourceColor): RichEditorAttribute;<br>差异内容：selectedBackgroundColor(value: ResourceColor): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：onEditingChange(callback: Callback\<boolean>): RichEditorAttribute;<br>差异内容：onEditingChange(callback: Callback\<boolean>): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：enterKeyType(value: EnterKeyType): RichEditorAttribute;<br>差异内容：enterKeyType(value: EnterKeyType): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：onSubmit(callback: SubmitCallback): RichEditorAttribute;<br>差异内容：onSubmit(callback: SubmitCallback): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：onWillChange(callback: Callback\<RichEditorChangeValue, boolean>): RichEditorAttribute;<br>差异内容：onWillChange(callback: Callback\<RichEditorChangeValue, boolean>): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：onDidChange(callback: OnDidChangeCallback): RichEditorAttribute;<br>差异内容：onDidChange(callback: OnDidChangeCallback): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：onCut(callback: Callback\<CutEvent>): RichEditorAttribute;<br>差异内容：onCut(callback: Callback\<CutEvent>): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：onCopy(callback: Callback\<CopyEvent>): RichEditorAttribute;<br>差异内容：onCopy(callback: Callback\<CopyEvent>): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：editMenuOptions(editMenu: EditMenuOptions): RichEditorAttribute;<br>差异内容：editMenuOptions(editMenu: EditMenuOptions): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：RichEditorAttribute；<br>API声明：enableKeyboardOnFocus(isEnabled: boolean): RichEditorAttribute;<br>差异内容：enableKeyboardOnFocus(isEnabled: boolean): RichEditorAttribute;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface CutEvent<br>差异内容：declare interface CutEvent|component/rich_editor.d.ts|
|新增API|NA|类名：CutEvent；<br>API声明：preventDefault?: Callback\<void>;<br>差异内容：preventDefault?: Callback\<void>;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface CopyEvent<br>差异内容：declare interface CopyEvent|component/rich_editor.d.ts|
|新增API|NA|类名：CopyEvent；<br>API声明：preventDefault?: Callback\<void>;<br>差异内容：preventDefault?: Callback\<void>;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type SubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void;<br>差异内容：declare type SubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type MenuOnAppearCallback = (start: number, end: number) => void;<br>差异内容：declare type MenuOnAppearCallback = (start: number, end: number) => void;|component/rich_editor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type PasteEventCallback = (event?: PasteEvent) => void;<br>差异内容：declare type PasteEventCallback = (event?: PasteEvent) => void;|component/rich_editor.d.ts|
|新增API|NA|类名：RowAttribute；<br>API声明：reverse(isReversed: Optional\<boolean>): RowAttribute;<br>差异内容：reverse(isReversed: Optional\<boolean>): RowAttribute;|component/row.d.ts|
|新增API|NA|类名：SaveDescription；<br>API声明：SAVE_TO_GALLERY = 8<br>差异内容：SAVE_TO_GALLERY = 8|component/save_button.d.ts|
|新增API|NA|类名：SaveDescription；<br>API声明：EXPORT_TO_GALLERY = 9<br>差异内容：EXPORT_TO_GALLERY = 9|component/save_button.d.ts|
|新增API|NA|类名：SaveDescription；<br>API声明：QUICK_SAVE_TO_GALLERY = 10<br>差异内容：QUICK_SAVE_TO_GALLERY = 10|component/save_button.d.ts|
|新增API|NA|类名：SaveDescription；<br>API声明：RESAVE_TO_GALLERY = 11<br>差异内容：RESAVE_TO_GALLERY = 11|component/save_button.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ScrollEdgeOptions<br>差异内容：declare interface ScrollEdgeOptions|component/scroll.d.ts|
|新增API|NA|类名：ScrollEdgeOptions；<br>API声明：velocity?: number;<br>差异内容：velocity?: number;|component/scroll.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ScrollToIndexOptions<br>差异内容：declare interface ScrollToIndexOptions|component/scroll.d.ts|
|新增API|NA|类名：ScrollToIndexOptions；<br>API声明：extraOffset?: LengthMetrics;<br>差异内容：extraOffset?: LengthMetrics;|component/scroll.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ScrollAnimationOptions<br>差异内容：declare interface ScrollAnimationOptions|component/scroll.d.ts|
|新增API|NA|类名：ScrollAnimationOptions；<br>API声明：duration?: number;<br>差异内容：duration?: number;|component/scroll.d.ts|
|新增API|NA|类名：ScrollAnimationOptions；<br>API声明：curve?: Curve \| ICurve;<br>差异内容：curve?: Curve \| ICurve;|component/scroll.d.ts|
|新增API|NA|类名：ScrollAnimationOptions；<br>API声明：canOverScroll?: boolean;<br>差异内容：canOverScroll?: boolean;|component/scroll.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface OffsetOptions<br>差异内容：declare interface OffsetOptions|component/scroll.d.ts|
|新增API|NA|类名：OffsetOptions；<br>API声明：xOffset?: Dimension;<br>差异内容：xOffset?: Dimension;|component/scroll.d.ts|
|新增API|NA|类名：OffsetOptions；<br>API声明：yOffset?: Dimension;<br>差异内容：yOffset?: Dimension;|component/scroll.d.ts|
|新增API|NA|类名：Scroller；<br>API声明：fling(velocity: number): void;<br>差异内容：fling(velocity: number): void;|component/scroll.d.ts|
|新增API|NA|类名：ScrollAttribute；<br>API声明：onWillScroll(handler: ScrollOnWillScrollCallback): ScrollAttribute;<br>差异内容：onWillScroll(handler: ScrollOnWillScrollCallback): ScrollAttribute;|component/scroll.d.ts|
|新增API|NA|类名：ScrollAttribute；<br>API声明：onDidScroll(handler: ScrollOnScrollCallback): ScrollAttribute;<br>差异内容：onDidScroll(handler: ScrollOnScrollCallback): ScrollAttribute;|component/scroll.d.ts|
|新增API|NA|类名：ScrollAttribute；<br>API声明：initialOffset(value: OffsetOptions): ScrollAttribute;<br>差异内容：initialOffset(value: OffsetOptions): ScrollAttribute;|component/scroll.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void;<br>差异内容：declare type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void;|component/scroll.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type ScrollOnWillScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void \| OffsetResult;<br>差异内容：declare type ScrollOnWillScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void \| OffsetResult;|component/scroll.d.ts|
|新增API|NA|类名：SearchController；<br>API声明：setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void;<br>差异内容：setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void;|component/search.d.ts|
|新增API|NA|类名：SearchType；<br>API声明：NUMBER_DECIMAL = 12<br>差异内容：NUMBER_DECIMAL = 12|component/search.d.ts|
|新增API|NA|类名：SearchType；<br>API声明：URL = 13<br>差异内容：URL = 13|component/search.d.ts|
|新增API|NA|类名：global；<br>API声明：interface CancelButtonOptions<br>差异内容：interface CancelButtonOptions|component/search.d.ts|
|新增API|NA|类名：CancelButtonOptions；<br>API声明：style?: CancelButtonStyle;<br>差异内容：style?: CancelButtonStyle;|component/search.d.ts|
|新增API|NA|类名：CancelButtonOptions；<br>API声明：icon?: IconOptions;<br>差异内容：icon?: IconOptions;|component/search.d.ts|
|新增API|NA|类名：global；<br>API声明：interface CancelButtonSymbolOptions<br>差异内容：interface CancelButtonSymbolOptions|component/search.d.ts|
|新增API|NA|类名：CancelButtonSymbolOptions；<br>API声明：style?: CancelButtonStyle;<br>差异内容：style?: CancelButtonStyle;|component/search.d.ts|
|新增API|NA|类名：CancelButtonSymbolOptions；<br>API声明：icon?: SymbolGlyphModifier;<br>差异内容：icon?: SymbolGlyphModifier;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：textIndent(value: Dimension): SearchAttribute;<br>差异内容：textIndent(value: Dimension): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：inputFilter(value: ResourceStr, error?: Callback\<string>): SearchAttribute;<br>差异内容：inputFilter(value: ResourceStr, error?: Callback\<string>): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：onEditChange(callback: Callback\<boolean>): SearchAttribute;<br>差异内容：onEditChange(callback: Callback\<boolean>): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：selectedBackgroundColor(value: ResourceColor): SearchAttribute;<br>差异内容：selectedBackgroundColor(value: ResourceColor): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：enterKeyType(value: EnterKeyType): SearchAttribute;<br>差异内容：enterKeyType(value: EnterKeyType): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：minFontSize(value: number \| string \| Resource): SearchAttribute;<br>差异内容：minFontSize(value: number \| string \| Resource): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：maxFontSize(value: number \| string \| Resource): SearchAttribute;<br>差异内容：maxFontSize(value: number \| string \| Resource): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：decoration(value: TextDecorationOptions): SearchAttribute;<br>差异内容：decoration(value: TextDecorationOptions): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：letterSpacing(value: number \| string \| Resource): SearchAttribute;<br>差异内容：letterSpacing(value: number \| string \| Resource): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：lineHeight(value: number \| string \| Resource): SearchAttribute;<br>差异内容：lineHeight(value: number \| string \| Resource): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：fontFeature(value: string): SearchAttribute;<br>差异内容：fontFeature(value: string): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：onWillInsert(callback: Callback\<InsertValue, boolean>): SearchAttribute;<br>差异内容：onWillInsert(callback: Callback\<InsertValue, boolean>): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：onDidInsert(callback: Callback\<InsertValue>): SearchAttribute;<br>差异内容：onDidInsert(callback: Callback\<InsertValue>): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：onWillDelete(callback: Callback\<DeleteValue, boolean>): SearchAttribute;<br>差异内容：onWillDelete(callback: Callback\<DeleteValue, boolean>): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：onDidDelete(callback: Callback\<DeleteValue>): SearchAttribute;<br>差异内容：onDidDelete(callback: Callback\<DeleteValue>): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：editMenuOptions(editMenu: EditMenuOptions): SearchAttribute;<br>差异内容：editMenuOptions(editMenu: EditMenuOptions): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SearchAttribute；<br>API声明：enablePreviewText(enable: boolean): SearchAttribute;<br>差异内容：enablePreviewText(enable: boolean): SearchAttribute;|component/search.d.ts|
|新增API|NA|类名：SelectOption；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：symbolIcon?: SymbolGlyphModifier;|component/select.d.ts|
|新增API|NA|类名：SelectAttribute；<br>API声明：controlSize(value: ControlSize): SelectAttribute;<br>差异内容：controlSize(value: ControlSize): SelectAttribute;|component/select.d.ts|
|新增API|NA|类名：SelectAttribute；<br>API声明：menuItemContentModifier(modifier: ContentModifier\<MenuItemConfiguration>): SelectAttribute;<br>差异内容：menuItemContentModifier(modifier: ContentModifier\<MenuItemConfiguration>): SelectAttribute;|component/select.d.ts|
|新增API|NA|类名：SelectAttribute；<br>API声明：divider(options: Optional\<DividerOptions> \| null): SelectAttribute;<br>差异内容：divider(options: Optional\<DividerOptions> \| null): SelectAttribute;|component/select.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface MenuItemConfiguration<br>差异内容：declare interface MenuItemConfiguration|component/select.d.ts|
|新增API|NA|类名：MenuItemConfiguration；<br>API声明：value: ResourceStr;<br>差异内容：value: ResourceStr;|component/select.d.ts|
|新增API|NA|类名：MenuItemConfiguration；<br>API声明：icon?: ResourceStr;<br>差异内容：icon?: ResourceStr;|component/select.d.ts|
|新增API|NA|类名：MenuItemConfiguration；<br>API声明：symbolIcon?: SymbolGlyphModifier;<br>差异内容：symbolIcon?: SymbolGlyphModifier;|component/select.d.ts|
|新增API|NA|类名：MenuItemConfiguration；<br>API声明：selected: boolean;<br>差异内容：selected: boolean;|component/select.d.ts|
|新增API|NA|类名：MenuItemConfiguration；<br>API声明：index: number;<br>差异内容：index: number;|component/select.d.ts|
|新增API|NA|类名：MenuItemConfiguration；<br>API声明：triggerSelect(index: number, value: string): void;<br>差异内容：triggerSelect(index: number, value: string): void;|component/select.d.ts|
|新增API|NA|类名：SliderStyle；<br>API声明：NONE<br>差异内容：NONE|component/slider.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum SliderInteraction<br>差异内容：declare enum SliderInteraction|component/slider.d.ts|
|新增API|NA|类名：SliderInteraction；<br>API声明：SLIDE_AND_CLICK<br>差异内容：SLIDE_AND_CLICK|component/slider.d.ts|
|新增API|NA|类名：SliderInteraction；<br>API声明：SLIDE_ONLY<br>差异内容：SLIDE_ONLY|component/slider.d.ts|
|新增API|NA|类名：SliderInteraction；<br>API声明：SLIDE_AND_CLICK_UP = 2<br>差异内容：SLIDE_AND_CLICK_UP = 2|component/slider.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SlideRange<br>差异内容：declare interface SlideRange|component/slider.d.ts|
|新增API|NA|类名：SlideRange；<br>API声明：from?: number;<br>差异内容：from?: number;|component/slider.d.ts|
|新增API|NA|类名：SlideRange；<br>API声明：to?: number;<br>差异内容：to?: number;|component/slider.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type SliderTriggerChangeCallback = (value: number, mode: SliderChangeMode) => void;<br>差异内容：declare type SliderTriggerChangeCallback = (value: number, mode: SliderChangeMode) => void;|component/slider.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SliderConfiguration<br>差异内容：declare interface SliderConfiguration|component/slider.d.ts|
|新增API|NA|类名：SliderConfiguration；<br>API声明：value: number;<br>差异内容：value: number;|component/slider.d.ts|
|新增API|NA|类名：SliderConfiguration；<br>API声明：min: number;<br>差异内容：min: number;|component/slider.d.ts|
|新增API|NA|类名：SliderConfiguration；<br>API声明：max: number;<br>差异内容：max: number;|component/slider.d.ts|
|新增API|NA|类名：SliderConfiguration；<br>API声明：step: number;<br>差异内容：step: number;|component/slider.d.ts|
|新增API|NA|类名：SliderConfiguration；<br>API声明：triggerChange: SliderTriggerChangeCallback;<br>差异内容：triggerChange: SliderTriggerChangeCallback;|component/slider.d.ts|
|新增API|NA|类名：SliderAttribute；<br>API声明：selectedBorderRadius(value: Dimension): SliderAttribute;<br>差异内容：selectedBorderRadius(value: Dimension): SliderAttribute;|component/slider.d.ts|
|新增API|NA|类名：SliderAttribute；<br>API声明：sliderInteractionMode(value: SliderInteraction): SliderAttribute;<br>差异内容：sliderInteractionMode(value: SliderInteraction): SliderAttribute;|component/slider.d.ts|
|新增API|NA|类名：SliderAttribute；<br>API声明：minResponsiveDistance(value: number): SliderAttribute;<br>差异内容：minResponsiveDistance(value: number): SliderAttribute;|component/slider.d.ts|
|新增API|NA|类名：SliderAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<SliderConfiguration>): SliderAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<SliderConfiguration>): SliderAttribute;|component/slider.d.ts|
|新增API|NA|类名：SliderAttribute；<br>API声明：slideRange(value: SlideRange): SliderAttribute;<br>差异内容：slideRange(value: SlideRange): SliderAttribute;|component/slider.d.ts|
|新增API|NA|类名：BaseSpan；<br>API声明：baselineOffset(value: LengthMetrics): T;<br>差异内容：baselineOffset(value: LengthMetrics): T;|component/span.d.ts|
|新增API|NA|类名：SwiperController；<br>API声明：changeIndex(index: number, useAnimation?: boolean);<br>差异内容：changeIndex(index: number, useAnimation?: boolean);|component/swiper.d.ts|
|新增API|NA|类名：Indicator；<br>API声明：start(value: LengthMetrics): T;<br>差异内容：start(value: LengthMetrics): T;|component/swiper.d.ts|
|新增API|NA|类名：Indicator；<br>API声明：end(value: LengthMetrics): T;<br>差异内容：end(value: LengthMetrics): T;|component/swiper.d.ts|
|新增API|NA|类名：DotIndicator；<br>API声明：maxDisplayCount(maxDisplayCount: number): DotIndicator;<br>差异内容：maxDisplayCount(maxDisplayCount: number): DotIndicator;|component/swiper.d.ts|
|新增API|NA|类名：SwiperAttribute；<br>API声明：customContentTransition(transition: SwiperContentAnimatedTransition): SwiperAttribute;<br>差异内容：customContentTransition(transition: SwiperContentAnimatedTransition): SwiperAttribute;|component/swiper.d.ts|
|新增API|NA|类名：SwiperAttribute；<br>API声明：onContentDidScroll(handler: ContentDidScrollCallback): SwiperAttribute;<br>差异内容：onContentDidScroll(handler: ContentDidScrollCallback): SwiperAttribute;|component/swiper.d.ts|
|新增API|NA|类名：SwiperAttribute；<br>API声明：indicatorInteractive(value: boolean): SwiperAttribute;<br>差异内容：indicatorInteractive(value: boolean): SwiperAttribute;|component/swiper.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SwiperContentAnimatedTransition<br>差异内容：declare interface SwiperContentAnimatedTransition|component/swiper.d.ts|
|新增API|NA|类名：SwiperContentAnimatedTransition；<br>API声明：timeout?: number;<br>差异内容：timeout?: number;|component/swiper.d.ts|
|新增API|NA|类名：SwiperContentAnimatedTransition；<br>API声明：transition: Callback\<SwiperContentTransitionProxy>;<br>差异内容：transition: Callback\<SwiperContentTransitionProxy>;|component/swiper.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SwiperContentTransitionProxy<br>差异内容：declare interface SwiperContentTransitionProxy|component/swiper.d.ts|
|新增API|NA|类名：SwiperContentTransitionProxy；<br>API声明：selectedIndex: number;<br>差异内容：selectedIndex: number;|component/swiper.d.ts|
|新增API|NA|类名：SwiperContentTransitionProxy；<br>API声明：index: number;<br>差异内容：index: number;|component/swiper.d.ts|
|新增API|NA|类名：SwiperContentTransitionProxy；<br>API声明：position: number;<br>差异内容：position: number;|component/swiper.d.ts|
|新增API|NA|类名：SwiperContentTransitionProxy；<br>API声明：mainAxisLength: number;<br>差异内容：mainAxisLength: number;|component/swiper.d.ts|
|新增API|NA|类名：SwiperContentTransitionProxy；<br>API声明：finishTransition(): void;<br>差异内容：finishTransition(): void;|component/swiper.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type ContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void;<br>差异内容：declare type ContentDidScrollCallback = (selectedIndex: number, index: number, position: number, mainAxisLength: number) => void;|component/swiper.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum EffectDirection<br>差异内容：declare enum EffectDirection|component/symbolglyph.d.ts|
|新增API|NA|类名：EffectDirection；<br>API声明：DOWN = 0<br>差异内容：DOWN = 0|component/symbolglyph.d.ts|
|新增API|NA|类名：EffectDirection；<br>API声明：UP = 1<br>差异内容：UP = 1|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum EffectScope<br>差异内容：declare enum EffectScope|component/symbolglyph.d.ts|
|新增API|NA|类名：EffectScope；<br>API声明：LAYER = 0<br>差异内容：LAYER = 0|component/symbolglyph.d.ts|
|新增API|NA|类名：EffectScope；<br>API声明：WHOLE = 1<br>差异内容：WHOLE = 1|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum EffectFillStyle<br>差异内容：declare enum EffectFillStyle|component/symbolglyph.d.ts|
|新增API|NA|类名：EffectFillStyle；<br>API声明：CUMULATIVE = 0<br>差异内容：CUMULATIVE = 0|component/symbolglyph.d.ts|
|新增API|NA|类名：EffectFillStyle；<br>API声明：ITERATIVE = 1<br>差异内容：ITERATIVE = 1|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class SymbolEffect<br>差异内容：declare class SymbolEffect|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ScaleSymbolEffect<br>差异内容：declare class ScaleSymbolEffect|component/symbolglyph.d.ts|
|新增API|NA|类名：ScaleSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：scope?: EffectScope;|component/symbolglyph.d.ts|
|新增API|NA|类名：ScaleSymbolEffect；<br>API声明：direction?: EffectDirection;<br>差异内容：direction?: EffectDirection;|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class HierarchicalSymbolEffect<br>差异内容：declare class HierarchicalSymbolEffect|component/symbolglyph.d.ts|
|新增API|NA|类名：HierarchicalSymbolEffect；<br>API声明：fillStyle?: EffectFillStyle;<br>差异内容：fillStyle?: EffectFillStyle;|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class AppearSymbolEffect<br>差异内容：declare class AppearSymbolEffect|component/symbolglyph.d.ts|
|新增API|NA|类名：AppearSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：scope?: EffectScope;|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class DisappearSymbolEffect<br>差异内容：declare class DisappearSymbolEffect|component/symbolglyph.d.ts|
|新增API|NA|类名：DisappearSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：scope?: EffectScope;|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class BounceSymbolEffect<br>差异内容：declare class BounceSymbolEffect|component/symbolglyph.d.ts|
|新增API|NA|类名：BounceSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：scope?: EffectScope;|component/symbolglyph.d.ts|
|新增API|NA|类名：BounceSymbolEffect；<br>API声明：direction?: EffectDirection;<br>差异内容：direction?: EffectDirection;|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ReplaceSymbolEffect<br>差异内容：declare class ReplaceSymbolEffect|component/symbolglyph.d.ts|
|新增API|NA|类名：ReplaceSymbolEffect；<br>API声明：scope?: EffectScope;<br>差异内容：scope?: EffectScope;|component/symbolglyph.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class PulseSymbolEffect<br>差异内容：declare class PulseSymbolEffect|component/symbolglyph.d.ts|
|新增API|NA|类名：SymbolGlyphAttribute；<br>API声明：symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean): SymbolGlyphAttribute;<br>差异内容：symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean): SymbolGlyphAttribute;|component/symbolglyph.d.ts|
|新增API|NA|类名：SymbolGlyphAttribute；<br>API声明：symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number): SymbolGlyphAttribute;<br>差异内容：symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number): SymbolGlyphAttribute;|component/symbolglyph.d.ts|
|新增API|NA|类名：SymbolSpanAttribute；<br>API声明：attributeModifier(modifier: AttributeModifier\<SymbolSpanAttribute>): SymbolSpanAttribute;<br>差异内容：attributeModifier(modifier: AttributeModifier\<SymbolSpanAttribute>): SymbolSpanAttribute;|component/symbol_span.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum AnimationMode<br>差异内容：declare enum AnimationMode|component/tabs.d.ts|
|新增API|NA|类名：AnimationMode；<br>API声明：CONTENT_FIRST = 0<br>差异内容：CONTENT_FIRST = 0|component/tabs.d.ts|
|新增API|NA|类名：AnimationMode；<br>API声明：ACTION_FIRST = 1<br>差异内容：ACTION_FIRST = 1|component/tabs.d.ts|
|新增API|NA|类名：AnimationMode；<br>API声明：NO_ANIMATION = 2<br>差异内容：NO_ANIMATION = 2|component/tabs.d.ts|
|新增API|NA|类名：TabsController；<br>API声明：preloadItems(indices: Optional\<Array\<number>>): Promise\<void>;<br>差异内容：preloadItems(indices: Optional\<Array\<number>>): Promise\<void>;|component/tabs.d.ts|
|新增API|NA|类名：TabsAttribute；<br>API声明：animationMode(mode: Optional\<AnimationMode>): TabsAttribute;<br>差异内容：animationMode(mode: Optional\<AnimationMode>): TabsAttribute;|component/tabs.d.ts|
|新增API|NA|类名：TabsAttribute；<br>API声明：edgeEffect(edgeEffect: Optional\<EdgeEffect>): TabsAttribute;<br>差异内容：edgeEffect(edgeEffect: Optional\<EdgeEffect>): TabsAttribute;|component/tabs.d.ts|
|新增API|NA|类名：TabsAttribute；<br>API声明：onContentWillChange(handler: (currentIndex: number, comingIndex: number) => boolean): TabsAttribute;<br>差异内容：onContentWillChange(handler: (currentIndex: number, comingIndex: number) => boolean): TabsAttribute;|component/tabs.d.ts|
|新增API|NA|类名：SubTabBarStyle；<br>API声明：static of(content: ResourceStr \| ComponentContent): SubTabBarStyle;<br>差异内容：static of(content: ResourceStr \| ComponentContent): SubTabBarStyle;|component/tab_content.d.ts|
|新增API|NA|类名：SubTabBarStyle；<br>API声明：padding(padding: LocalizedPadding): SubTabBarStyle;<br>差异内容：padding(padding: LocalizedPadding): SubTabBarStyle;|component/tab_content.d.ts|
|新增API|NA|类名：LabelStyle；<br>API声明：selectedColor?: ResourceColor;<br>差异内容：selectedColor?: ResourceColor;|component/tab_content.d.ts|
|新增API|NA|类名：LabelStyle；<br>API声明：unselectedColor?: ResourceColor;<br>差异内容：unselectedColor?: ResourceColor;|component/tab_content.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TabBarIconStyle<br>差异内容：declare interface TabBarIconStyle|component/tab_content.d.ts|
|新增API|NA|类名：TabBarIconStyle；<br>API声明：selectedColor?: ResourceColor;<br>差异内容：selectedColor?: ResourceColor;|component/tab_content.d.ts|
|新增API|NA|类名：TabBarIconStyle；<br>API声明：unselectedColor?: ResourceColor;<br>差异内容：unselectedColor?: ResourceColor;|component/tab_content.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class TabBarSymbol<br>差异内容：declare class TabBarSymbol|component/tab_content.d.ts|
|新增API|NA|类名：TabBarSymbol；<br>API声明：normal: SymbolGlyphModifier;<br>差异内容：normal: SymbolGlyphModifier;|component/tab_content.d.ts|
|新增API|NA|类名：TabBarSymbol；<br>API声明：selected?: SymbolGlyphModifier;<br>差异内容：selected?: SymbolGlyphModifier;|component/tab_content.d.ts|
|新增API|NA|类名：BottomTabBarStyle；<br>API声明：iconStyle(style: TabBarIconStyle): BottomTabBarStyle;<br>差异内容：iconStyle(style: TabBarIconStyle): BottomTabBarStyle;|component/tab_content.d.ts|
|新增API|NA|类名：TabContentAttribute；<br>API声明：onWillShow(event: VoidCallback): TabContentAttribute;<br>差异内容：onWillShow(event: VoidCallback): TabContentAttribute;|component/tab_content.d.ts|
|新增API|NA|类名：TabContentAttribute；<br>API声明：onWillHide(event: VoidCallback): TabContentAttribute;<br>差异内容：onWillHide(event: VoidCallback): TabContentAttribute;|component/tab_content.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：font(fontValue: Font, options?: FontSettingOptions): TextAttribute;<br>差异内容：font(fontValue: Font, options?: FontSettingOptions): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：minFontScale(scale: number \| Resource): TextAttribute;<br>差异内容：minFontScale(scale: number \| Resource): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：maxFontScale(scale: number \| Resource): TextAttribute;<br>差异内容：maxFontScale(scale: number \| Resource): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：lineSpacing(value: LengthMetrics): TextAttribute;<br>差异内容：lineSpacing(value: LengthMetrics): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：lineBreakStrategy(strategy: LineBreakStrategy): TextAttribute;<br>差异内容：lineBreakStrategy(strategy: LineBreakStrategy): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：fontFeature(value: string): TextAttribute;<br>差异内容：fontFeature(value: string): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：privacySensitive(supported: boolean): TextAttribute;<br>差异内容：privacySensitive(supported: boolean): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：textSelectable(mode: TextSelectableMode): TextAttribute;<br>差异内容：textSelectable(mode: TextSelectableMode): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：editMenuOptions(editMenu: EditMenuOptions): TextAttribute;<br>差异内容：editMenuOptions(editMenu: EditMenuOptions): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextAttribute；<br>API声明：halfLeading(halfLeading: boolean): TextAttribute;<br>差异内容：halfLeading(halfLeading: boolean): TextAttribute;|component/text.d.ts|
|新增API|NA|类名：TextController；<br>API声明：setStyledString(value: StyledString): void;<br>差异内容：setStyledString(value: StyledString): void;|component/text.d.ts|
|新增API|NA|类名：TextController；<br>API声明：getLayoutManager(): LayoutManager;<br>差异内容：getLayoutManager(): LayoutManager;|component/text.d.ts|
|新增API|NA|类名：TextAreaType；<br>API声明：NUMBER_DECIMAL = 12<br>差异内容：NUMBER_DECIMAL = 12|component/text_area.d.ts|
|新增API|NA|类名：TextAreaType；<br>API声明：URL = 13<br>差异内容：URL = 13|component/text_area.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ContentType<br>差异内容：declare enum ContentType|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：USER_NAME = 0<br>差异内容：USER_NAME = 0|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PASSWORD = 1<br>差异内容：PASSWORD = 1|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NEW_PASSWORD = 2<br>差异内容：NEW_PASSWORD = 2|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：FULL_STREET_ADDRESS = 3<br>差异内容：FULL_STREET_ADDRESS = 3|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：HOUSE_NUMBER = 4<br>差异内容：HOUSE_NUMBER = 4|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：DISTRICT_ADDRESS = 5<br>差异内容：DISTRICT_ADDRESS = 5|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：CITY_ADDRESS = 6<br>差异内容：CITY_ADDRESS = 6|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PROVINCE_ADDRESS = 7<br>差异内容：PROVINCE_ADDRESS = 7|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：COUNTRY_ADDRESS = 8<br>差异内容：COUNTRY_ADDRESS = 8|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PERSON_FULL_NAME = 9<br>差异内容：PERSON_FULL_NAME = 9|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PERSON_LAST_NAME = 10<br>差异内容：PERSON_LAST_NAME = 10|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PERSON_FIRST_NAME = 11<br>差异内容：PERSON_FIRST_NAME = 11|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PHONE_NUMBER = 12<br>差异内容：PHONE_NUMBER = 12|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PHONE_COUNTRY_CODE = 13<br>差异内容：PHONE_COUNTRY_CODE = 13|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：FULL_PHONE_NUMBER = 14<br>差异内容：FULL_PHONE_NUMBER = 14|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：EMAIL_ADDRESS = 15<br>差异内容：EMAIL_ADDRESS = 15|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：BANK_CARD_NUMBER = 16<br>差异内容：BANK_CARD_NUMBER = 16|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：ID_CARD_NUMBER = 17<br>差异内容：ID_CARD_NUMBER = 17|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NICKNAME = 23<br>差异内容：NICKNAME = 23|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：DETAIL_INFO_WITHOUT_STREET = 24<br>差异内容：DETAIL_INFO_WITHOUT_STREET = 24|component/text_area.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：FORMAT_ADDRESS = 25<br>差异内容：FORMAT_ADDRESS = 25|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：textOverflow(value: TextOverflow): TextAreaAttribute;<br>差异内容：textOverflow(value: TextOverflow): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：textIndent(value: Dimension): TextAreaAttribute;<br>差异内容：textIndent(value: Dimension): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：caretStyle(value: CaretStyle): TextAreaAttribute;<br>差异内容：caretStyle(value: CaretStyle): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：selectedBackgroundColor(value: ResourceColor): TextAreaAttribute;<br>差异内容：selectedBackgroundColor(value: ResourceColor): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：minFontSize(value: number \| string \| Resource): TextAreaAttribute;<br>差异内容：minFontSize(value: number \| string \| Resource): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：maxFontSize(value: number \| string \| Resource): TextAreaAttribute;<br>差异内容：maxFontSize(value: number \| string \| Resource): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextAreaAttribute;<br>差异内容：heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：wordBreak(value: WordBreak): TextAreaAttribute;<br>差异内容：wordBreak(value: WordBreak): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：lineBreakStrategy(strategy: LineBreakStrategy): TextAreaAttribute;<br>差异内容：lineBreakStrategy(strategy: LineBreakStrategy): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：decoration(value: TextDecorationOptions): TextAreaAttribute;<br>差异内容：decoration(value: TextDecorationOptions): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：letterSpacing(value: number \| string \| Resource): TextAreaAttribute;<br>差异内容：letterSpacing(value: number \| string \| Resource): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：lineSpacing(value: LengthMetrics): TextAreaAttribute;<br>差异内容：lineSpacing(value: LengthMetrics): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：lineHeight(value: number \| string \| Resource): TextAreaAttribute;<br>差异内容：lineHeight(value: number \| string \| Resource): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：enableAutoFill(value: boolean): TextAreaAttribute;<br>差异内容：enableAutoFill(value: boolean): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：contentType(contentType: ContentType): TextAreaAttribute;<br>差异内容：contentType(contentType: ContentType): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：fontFeature(value: string): TextAreaAttribute;<br>差异内容：fontFeature(value: string): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：onWillInsert(callback: Callback\<InsertValue, boolean>): TextAreaAttribute;<br>差异内容：onWillInsert(callback: Callback\<InsertValue, boolean>): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：onDidInsert(callback: Callback\<InsertValue>): TextAreaAttribute;<br>差异内容：onDidInsert(callback: Callback\<InsertValue>): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：onWillDelete(callback: Callback\<DeleteValue, boolean>): TextAreaAttribute;<br>差异内容：onWillDelete(callback: Callback\<DeleteValue, boolean>): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：onDidDelete(callback: Callback\<DeleteValue>): TextAreaAttribute;<br>差异内容：onDidDelete(callback: Callback\<DeleteValue>): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：editMenuOptions(editMenu: EditMenuOptions): TextAreaAttribute;<br>差异内容：editMenuOptions(editMenu: EditMenuOptions): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：TextAreaAttribute；<br>API声明：enablePreviewText(enable: boolean): TextAreaAttribute;<br>差异内容：enablePreviewText(enable: boolean): TextAreaAttribute;|component/text_area.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TextClockConfiguration<br>差异内容：declare interface TextClockConfiguration|component/text_clock.d.ts|
|新增API|NA|类名：TextClockConfiguration；<br>API声明：timeZoneOffset: number;<br>差异内容：timeZoneOffset: number;|component/text_clock.d.ts|
|新增API|NA|类名：TextClockConfiguration；<br>API声明：started: boolean;<br>差异内容：started: boolean;|component/text_clock.d.ts|
|新增API|NA|类名：TextClockConfiguration；<br>API声明：timeValue: number;<br>差异内容：timeValue: number;|component/text_clock.d.ts|
|新增API|NA|类名：TextClockAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<TextClockConfiguration>): TextClockAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<TextClockConfiguration>): TextClockAttribute;|component/text_clock.d.ts|
|新增API|NA|类名：TextClockAttribute；<br>API声明：dateTimeOptions(dateTimeOptions: Optional\<DateTimeOptions>): TextClockAttribute;<br>差异内容：dateTimeOptions(dateTimeOptions: Optional\<DateTimeOptions>): TextClockAttribute;|component/text_clock.d.ts|
|新增API|NA|类名：TextDataDetectorType；<br>API声明：DATE_TIME = 4<br>差异内容：DATE_TIME = 4|component/text_common.d.ts|
|新增API|NA|类名：TextDataDetectorConfig；<br>API声明：color?: ResourceColor;<br>差异内容：color?: ResourceColor;|component/text_common.d.ts|
|新增API|NA|类名：TextDataDetectorConfig；<br>API声明：decoration?: DecorationStyleInterface;<br>差异内容：decoration?: DecorationStyleInterface;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TextRange<br>差异内容：declare interface TextRange|component/text_common.d.ts|
|新增API|NA|类名：TextRange；<br>API声明：start?: number;<br>差异内容：start?: number;|component/text_common.d.ts|
|新增API|NA|类名：TextRange；<br>API声明：end?: number;<br>差异内容：end?: number;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface InsertValue<br>差异内容：declare interface InsertValue|component/text_common.d.ts|
|新增API|NA|类名：InsertValue；<br>API声明：insertOffset: number;<br>差异内容：insertOffset: number;|component/text_common.d.ts|
|新增API|NA|类名：InsertValue；<br>API声明：insertValue: string;<br>差异内容：insertValue: string;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum TextDeleteDirection<br>差异内容：declare enum TextDeleteDirection|component/text_common.d.ts|
|新增API|NA|类名：TextDeleteDirection；<br>API声明：BACKWARD = 0<br>差异内容：BACKWARD = 0|component/text_common.d.ts|
|新增API|NA|类名：TextDeleteDirection；<br>API声明：FORWARD = 1<br>差异内容：FORWARD = 1|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DeleteValue<br>差异内容：declare interface DeleteValue|component/text_common.d.ts|
|新增API|NA|类名：DeleteValue；<br>API声明：deleteOffset: number;<br>差异内容：deleteOffset: number;|component/text_common.d.ts|
|新增API|NA|类名：DeleteValue；<br>API声明：direction: TextDeleteDirection;<br>差异内容：direction: TextDeleteDirection;|component/text_common.d.ts|
|新增API|NA|类名：DeleteValue；<br>API声明：deleteValue: string;<br>差异内容：deleteValue: string;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type OnDidChangeCallback = (rangeBefore: TextRange, rangeAfter: TextRange) => void;<br>差异内容：declare type OnDidChangeCallback = (rangeBefore: TextRange, rangeAfter: TextRange) => void;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type EditableTextOnChangeCallback = (value: string, previewText?: PreviewText) => void;<br>差异内容：declare type EditableTextOnChangeCallback = (value: string, previewText?: PreviewText) => void;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TextBaseController<br>差异内容：declare interface TextBaseController|component/text_common.d.ts|
|新增API|NA|类名：TextBaseController；<br>API声明：setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void;<br>差异内容：setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void;|component/text_common.d.ts|
|新增API|NA|类名：TextBaseController；<br>API声明：closeSelectionMenu(): void;<br>差异内容：closeSelectionMenu(): void;|component/text_common.d.ts|
|新增API|NA|类名：TextBaseController；<br>API声明：getLayoutManager(): LayoutManager;<br>差异内容：getLayoutManager(): LayoutManager;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TextEditControllerEx<br>差异内容：declare interface TextEditControllerEx|component/text_common.d.ts|
|新增API|NA|类名：TextEditControllerEx；<br>API声明：isEditing(): boolean;<br>差异内容：isEditing(): boolean;|component/text_common.d.ts|
|新增API|NA|类名：TextEditControllerEx；<br>API声明：stopEditing(): void;<br>差异内容：stopEditing(): void;|component/text_common.d.ts|
|新增API|NA|类名：TextEditControllerEx；<br>API声明：setCaretOffset(offset: number): boolean;<br>差异内容：setCaretOffset(offset: number): boolean;|component/text_common.d.ts|
|新增API|NA|类名：TextEditControllerEx；<br>API声明：getCaretOffset(): number;<br>差异内容：getCaretOffset(): number;|component/text_common.d.ts|
|新增API|NA|类名：TextEditControllerEx；<br>API声明：getPreviewText?(): PreviewText;<br>差异内容：getPreviewText?(): PreviewText;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface PreviewText<br>差异内容：declare interface PreviewText|component/text_common.d.ts|
|新增API|NA|类名：PreviewText；<br>API声明：offset: number;<br>差异内容：offset: number;|component/text_common.d.ts|
|新增API|NA|类名：PreviewText；<br>API声明：value: string;<br>差异内容：value: string;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface StyledStringController<br>差异内容：declare interface StyledStringController|component/text_common.d.ts|
|新增API|NA|类名：StyledStringController；<br>API声明：setStyledString(styledString: StyledString): void;<br>差异内容：setStyledString(styledString: StyledString): void;|component/text_common.d.ts|
|新增API|NA|类名：StyledStringController；<br>API声明：getStyledString(): MutableStyledString;<br>差异内容：getStyledString(): MutableStyledString;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface StyledStringChangedListener<br>差异内容：declare interface StyledStringChangedListener|component/text_common.d.ts|
|新增API|NA|类名：StyledStringChangedListener；<br>API声明：onWillChange?: Callback\<StyledStringChangeValue, boolean>;<br>差异内容：onWillChange?: Callback\<StyledStringChangeValue, boolean>;|component/text_common.d.ts|
|新增API|NA|类名：StyledStringChangedListener；<br>API声明：onDidChange?: OnDidChangeCallback;<br>差异内容：onDidChange?: OnDidChangeCallback;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：interface StyledStringChangeValue<br>差异内容：interface StyledStringChangeValue|component/text_common.d.ts|
|新增API|NA|类名：StyledStringChangeValue；<br>API声明：range: TextRange;<br>差异内容：range: TextRange;|component/text_common.d.ts|
|新增API|NA|类名：StyledStringChangeValue；<br>API声明：replacementString: StyledString;<br>差异内容：replacementString: StyledString;|component/text_common.d.ts|
|新增API|NA|类名：StyledStringChangeValue；<br>API声明：previewText?: StyledString;<br>差异内容：previewText?: StyledString;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LayoutManager<br>差异内容：declare interface LayoutManager|component/text_common.d.ts|
|新增API|NA|类名：LayoutManager；<br>API声明：getLineCount(): number;<br>差异内容：getLineCount(): number;|component/text_common.d.ts|
|新增API|NA|类名：LayoutManager；<br>API声明：getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity;<br>差异内容：getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity;|component/text_common.d.ts|
|新增API|NA|类名：LayoutManager；<br>API声明：getLineMetrics(lineNumber: number): LineMetrics;<br>差异内容：getLineMetrics(lineNumber: number): LineMetrics;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：interface PositionWithAffinity<br>差异内容：interface PositionWithAffinity|component/text_common.d.ts|
|新增API|NA|类名：PositionWithAffinity；<br>API声明：position: number;<br>差异内容：position: number;|component/text_common.d.ts|
|新增API|NA|类名：PositionWithAffinity；<br>API声明：affinity: Affinity;<br>差异内容：affinity: Affinity;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type Affinity = import('../api/@ohos.graphics.text').default.Affinity;<br>差异内容：declare type Affinity = import('../api/@ohos.graphics.text').default.Affinity;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type LineMetrics = import('../api/@ohos.graphics.text').default.LineMetrics;<br>差异内容：declare type LineMetrics = import('../api/@ohos.graphics.text').default.LineMetrics;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：interface CaretStyle<br>差异内容：interface CaretStyle|component/text_common.d.ts|
|新增API|NA|类名：CaretStyle；<br>API声明：width?: Length;<br>差异内容：width?: Length;|component/text_common.d.ts|
|新增API|NA|类名：CaretStyle；<br>API声明：color?: ResourceColor;<br>差异内容：color?: ResourceColor;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class TextMenuItemId<br>差异内容：declare class TextMenuItemId|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItemId；<br>API声明：static of(id: ResourceStr): TextMenuItemId;<br>差异内容：static of(id: ResourceStr): TextMenuItemId;|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItemId；<br>API声明：equals(id: TextMenuItemId): boolean;<br>差异内容：equals(id: TextMenuItemId): boolean;|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItemId；<br>API声明：static readonly CUT: TextMenuItemId;<br>差异内容：static readonly CUT: TextMenuItemId;|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItemId；<br>API声明：static readonly COPY: TextMenuItemId;<br>差异内容：static readonly COPY: TextMenuItemId;|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItemId；<br>API声明：static readonly PASTE: TextMenuItemId;<br>差异内容：static readonly PASTE: TextMenuItemId;|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItemId；<br>API声明：static readonly SELECT_ALL: TextMenuItemId;<br>差异内容：static readonly SELECT_ALL: TextMenuItemId;|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItemId；<br>API声明：static readonly COLLABORATION_SERVICE: TextMenuItemId;<br>差异内容：static readonly COLLABORATION_SERVICE: TextMenuItemId;|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItemId；<br>API声明：static readonly CAMERA_INPUT: TextMenuItemId;<br>差异内容：static readonly CAMERA_INPUT: TextMenuItemId;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TextMenuItem<br>差异内容：declare interface TextMenuItem|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItem；<br>API声明：content: ResourceStr;<br>差异内容：content: ResourceStr;|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItem；<br>API声明：icon?: ResourceStr;<br>差异内容：icon?: ResourceStr;|component/text_common.d.ts|
|新增API|NA|类名：TextMenuItem；<br>API声明：id: TextMenuItemId;<br>差异内容：id: TextMenuItemId;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface EditMenuOptions<br>差异内容：declare interface EditMenuOptions|component/text_common.d.ts|
|新增API|NA|类名：EditMenuOptions；<br>API声明：onCreateMenu(menuItems: Array\<TextMenuItem>): Array\<TextMenuItem>;<br>差异内容：onCreateMenu(menuItems: Array\<TextMenuItem>): Array\<TextMenuItem>;|component/text_common.d.ts|
|新增API|NA|类名：EditMenuOptions；<br>API声明：onMenuItemClick(menuItem: TextMenuItem, range: TextRange): boolean;<br>差异内容：onMenuItemClick(menuItem: TextMenuItem, range: TextRange): boolean;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：interface DecorationStyleResult<br>差异内容：interface DecorationStyleResult|component/text_common.d.ts|
|新增API|NA|类名：DecorationStyleResult；<br>API声明：type: TextDecorationType;<br>差异内容：type: TextDecorationType;|component/text_common.d.ts|
|新增API|NA|类名：DecorationStyleResult；<br>API声明：color: ResourceColor;<br>差异内容：color: ResourceColor;|component/text_common.d.ts|
|新增API|NA|类名：DecorationStyleResult；<br>API声明：style?: TextDecorationStyle;<br>差异内容：style?: TextDecorationStyle;|component/text_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface FontSettingOptions<br>差异内容：declare interface FontSettingOptions|component/text_common.d.ts|
|新增API|NA|类名：FontSettingOptions；<br>API声明：enableVariableFontWeight?: boolean;<br>差异内容：enableVariableFontWeight?: boolean;|component/text_common.d.ts|
|新增API|NA|类名：InputType；<br>API声明：URL = 13<br>差异内容：URL = 13|component/text_input.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ContentType<br>差异内容：declare enum ContentType|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：USER_NAME = 0<br>差异内容：USER_NAME = 0|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PASSWORD = 1<br>差异内容：PASSWORD = 1|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NEW_PASSWORD = 2<br>差异内容：NEW_PASSWORD = 2|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：FULL_STREET_ADDRESS = 3<br>差异内容：FULL_STREET_ADDRESS = 3|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：HOUSE_NUMBER = 4<br>差异内容：HOUSE_NUMBER = 4|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：DISTRICT_ADDRESS = 5<br>差异内容：DISTRICT_ADDRESS = 5|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：CITY_ADDRESS = 6<br>差异内容：CITY_ADDRESS = 6|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PROVINCE_ADDRESS = 7<br>差异内容：PROVINCE_ADDRESS = 7|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：COUNTRY_ADDRESS = 8<br>差异内容：COUNTRY_ADDRESS = 8|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PERSON_FULL_NAME = 9<br>差异内容：PERSON_FULL_NAME = 9|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PERSON_LAST_NAME = 10<br>差异内容：PERSON_LAST_NAME = 10|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PERSON_FIRST_NAME = 11<br>差异内容：PERSON_FIRST_NAME = 11|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PHONE_NUMBER = 12<br>差异内容：PHONE_NUMBER = 12|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：PHONE_COUNTRY_CODE = 13<br>差异内容：PHONE_COUNTRY_CODE = 13|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：FULL_PHONE_NUMBER = 14<br>差异内容：FULL_PHONE_NUMBER = 14|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：EMAIL_ADDRESS = 15<br>差异内容：EMAIL_ADDRESS = 15|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：BANK_CARD_NUMBER = 16<br>差异内容：BANK_CARD_NUMBER = 16|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：ID_CARD_NUMBER = 17<br>差异内容：ID_CARD_NUMBER = 17|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NICKNAME = 23<br>差异内容：NICKNAME = 23|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：DETAIL_INFO_WITHOUT_STREET = 24<br>差异内容：DETAIL_INFO_WITHOUT_STREET = 24|component/text_input.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：FORMAT_ADDRESS = 25<br>差异内容：FORMAT_ADDRESS = 25|component/text_input.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface UnderlineColor<br>差异内容：declare interface UnderlineColor|component/text_input.d.ts|
|新增API|NA|类名：UnderlineColor；<br>API声明：typing?: ResourceColor \| undefined;<br>差异内容：typing?: ResourceColor \| undefined;|component/text_input.d.ts|
|新增API|NA|类名：UnderlineColor；<br>API声明：normal?: ResourceColor \| undefined;<br>差异内容：normal?: ResourceColor \| undefined;|component/text_input.d.ts|
|新增API|NA|类名：UnderlineColor；<br>API声明：error?: ResourceColor \| undefined;<br>差异内容：error?: ResourceColor \| undefined;|component/text_input.d.ts|
|新增API|NA|类名：UnderlineColor；<br>API声明：disable?: ResourceColor \| undefined;<br>差异内容：disable?: ResourceColor \| undefined;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：contentType(value: ContentType): TextInputAttribute;<br>差异内容：contentType(value: ContentType): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：textOverflow(value: TextOverflow): TextInputAttribute;<br>差异内容：textOverflow(value: TextOverflow): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：textIndent(value: Dimension): TextInputAttribute;<br>差异内容：textIndent(value: Dimension): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：underlineColor(value: ResourceColor \| UnderlineColor \| undefined): TextInputAttribute;<br>差异内容：underlineColor(value: ResourceColor \| UnderlineColor \| undefined): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：wordBreak(value: WordBreak): TextInputAttribute;<br>差异内容：wordBreak(value: WordBreak): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：lineBreakStrategy(strategy: LineBreakStrategy): TextInputAttribute;<br>差异内容：lineBreakStrategy(strategy: LineBreakStrategy): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：minFontSize(value: number \| string \| Resource): TextInputAttribute;<br>差异内容：minFontSize(value: number \| string \| Resource): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：maxFontSize(value: number \| string \| Resource): TextInputAttribute;<br>差异内容：maxFontSize(value: number \| string \| Resource): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextInputAttribute;<br>差异内容：heightAdaptivePolicy(value: TextHeightAdaptivePolicy): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：decoration(value: TextDecorationOptions): TextInputAttribute;<br>差异内容：decoration(value: TextDecorationOptions): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：letterSpacing(value: number \| string \| Resource): TextInputAttribute;<br>差异内容：letterSpacing(value: number \| string \| Resource): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：lineHeight(value: number \| string \| Resource): TextInputAttribute;<br>差异内容：lineHeight(value: number \| string \| Resource): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：fontFeature(value: string): TextInputAttribute;<br>差异内容：fontFeature(value: string): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：showPassword(visible: boolean): TextInputAttribute;<br>差异内容：showPassword(visible: boolean): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：onSecurityStateChange(callback: Callback\<boolean>): TextInputAttribute;<br>差异内容：onSecurityStateChange(callback: Callback\<boolean>): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：onWillInsert(callback: Callback\<InsertValue, boolean>): TextInputAttribute;<br>差异内容：onWillInsert(callback: Callback\<InsertValue, boolean>): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：onDidInsert(callback: Callback\<InsertValue>): TextInputAttribute;<br>差异内容：onDidInsert(callback: Callback\<InsertValue>): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：onWillDelete(callback: Callback\<DeleteValue, boolean>): TextInputAttribute;<br>差异内容：onWillDelete(callback: Callback\<DeleteValue, boolean>): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：onDidDelete(callback: Callback\<DeleteValue>): TextInputAttribute;<br>差异内容：onDidDelete(callback: Callback\<DeleteValue>): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：editMenuOptions(editMenu: EditMenuOptions): TextInputAttribute;<br>差异内容：editMenuOptions(editMenu: EditMenuOptions): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：TextInputAttribute；<br>API声明：enablePreviewText(enable: boolean): TextInputAttribute;<br>差异内容：enablePreviewText(enable: boolean): TextInputAttribute;|component/text_input.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DividerOptions<br>差异内容：declare interface DividerOptions|component/text_picker.d.ts|
|新增API|NA|类名：DividerOptions；<br>API声明：strokeWidth?: Dimension;<br>差异内容：strokeWidth?: Dimension;|component/text_picker.d.ts|
|新增API|NA|类名：DividerOptions；<br>API声明：color?: ResourceColor;<br>差异内容：color?: ResourceColor;|component/text_picker.d.ts|
|新增API|NA|类名：DividerOptions；<br>API声明：startMargin?: Dimension;<br>差异内容：startMargin?: Dimension;|component/text_picker.d.ts|
|新增API|NA|类名：DividerOptions；<br>API声明：endMargin?: Dimension;<br>差异内容：endMargin?: Dimension;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerAttribute；<br>API声明：divider(value: DividerOptions \| null): TextPickerAttribute;<br>差异内容：divider(value: DividerOptions \| null): TextPickerAttribute;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerAttribute；<br>API声明：gradientHeight(value: Dimension): TextPickerAttribute;<br>差异内容：gradientHeight(value: Dimension): TextPickerAttribute;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：acceptButtonStyle?: PickerDialogButtonStyle;<br>差异内容：acceptButtonStyle?: PickerDialogButtonStyle;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：cancelButtonStyle?: PickerDialogButtonStyle;<br>差异内容：cancelButtonStyle?: PickerDialogButtonStyle;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：onDidAppear?: () => void;<br>差异内容：onDidAppear?: () => void;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：onDidDisappear?: () => void;<br>差异内容：onDidDisappear?: () => void;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：onWillAppear?: () => void;<br>差异内容：onWillAppear?: () => void;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：onWillDisappear?: () => void;<br>差异内容：onWillDisappear?: () => void;|component/text_picker.d.ts|
|新增API|NA|类名：TextPickerDialogOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|component/text_picker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TextTimerConfiguration<br>差异内容：declare interface TextTimerConfiguration|component/text_timer.d.ts|
|新增API|NA|类名：TextTimerConfiguration；<br>API声明：count: number;<br>差异内容：count: number;|component/text_timer.d.ts|
|新增API|NA|类名：TextTimerConfiguration；<br>API声明：isCountDown: boolean;<br>差异内容：isCountDown: boolean;|component/text_timer.d.ts|
|新增API|NA|类名：TextTimerConfiguration；<br>API声明：started: boolean;<br>差异内容：started: boolean;|component/text_timer.d.ts|
|新增API|NA|类名：TextTimerConfiguration；<br>API声明：elapsedTime: number;<br>差异内容：elapsedTime: number;|component/text_timer.d.ts|
|新增API|NA|类名：TextTimerAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<TextTimerConfiguration>): TextTimerAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<TextTimerConfiguration>): TextTimerAttribute;|component/text_timer.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type DateTimeOptions = import('../api/@ohos.intl').default.DateTimeOptions;<br>差异内容：declare type DateTimeOptions = import('../api/@ohos.intl').default.DateTimeOptions;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerAttribute；<br>API声明：dateTimeOptions(value: DateTimeOptions): TimePickerAttribute;<br>差异内容：dateTimeOptions(value: DateTimeOptions): TimePickerAttribute;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerAttribute；<br>API声明：enableHapticFeedback(enable: boolean): TimePickerAttribute;<br>差异内容：enableHapticFeedback(enable: boolean): TimePickerAttribute;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：acceptButtonStyle?: PickerDialogButtonStyle;<br>差异内容：acceptButtonStyle?: PickerDialogButtonStyle;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：cancelButtonStyle?: PickerDialogButtonStyle;<br>差异内容：cancelButtonStyle?: PickerDialogButtonStyle;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：onDidAppear?: () => void;<br>差异内容：onDidAppear?: () => void;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：onDidDisappear?: () => void;<br>差异内容：onDidDisappear?: () => void;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：onWillAppear?: () => void;<br>差异内容：onWillAppear?: () => void;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：onWillDisappear?: () => void;<br>差异内容：onWillDisappear?: () => void;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|component/time_picker.d.ts|
|新增API|NA|类名：TimePickerDialogOptions；<br>API声明：dateTimeOptions?: DateTimeOptions;<br>差异内容：dateTimeOptions?: DateTimeOptions;|component/time_picker.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SwitchStyle<br>差异内容：declare interface SwitchStyle|component/toggle.d.ts|
|新增API|NA|类名：SwitchStyle；<br>API声明：pointRadius?: number \| Resource;<br>差异内容：pointRadius?: number \| Resource;|component/toggle.d.ts|
|新增API|NA|类名：SwitchStyle；<br>API声明：unselectedColor?: ResourceColor;<br>差异内容：unselectedColor?: ResourceColor;|component/toggle.d.ts|
|新增API|NA|类名：SwitchStyle；<br>API声明：pointColor?: ResourceColor;<br>差异内容：pointColor?: ResourceColor;|component/toggle.d.ts|
|新增API|NA|类名：SwitchStyle；<br>API声明：trackBorderRadius?: number \| Resource;<br>差异内容：trackBorderRadius?: number \| Resource;|component/toggle.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ToggleConfiguration<br>差异内容：declare interface ToggleConfiguration|component/toggle.d.ts|
|新增API|NA|类名：ToggleConfiguration；<br>API声明：isOn: boolean;<br>差异内容：isOn: boolean;|component/toggle.d.ts|
|新增API|NA|类名：ToggleConfiguration；<br>API声明：enabled: boolean;<br>差异内容：enabled: boolean;|component/toggle.d.ts|
|新增API|NA|类名：ToggleConfiguration；<br>API声明：triggerChange: Callback\<boolean>;<br>差异内容：triggerChange: Callback\<boolean>;|component/toggle.d.ts|
|新增API|NA|类名：ToggleAttribute；<br>API声明：contentModifier(modifier: ContentModifier\<ToggleConfiguration>): ToggleAttribute;<br>差异内容：contentModifier(modifier: ContentModifier\<ToggleConfiguration>): ToggleAttribute;|component/toggle.d.ts|
|新增API|NA|类名：ToggleAttribute；<br>API声明：switchStyle(value: SwitchStyle): ToggleAttribute;<br>差异内容：switchStyle(value: SwitchStyle): ToggleAttribute;|component/toggle.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedPadding<br>差异内容：declare interface LocalizedPadding|component/units.d.ts|
|新增API|NA|类名：LocalizedPadding；<br>API声明：top?: LengthMetrics;<br>差异内容：top?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedPadding；<br>API声明：end?: LengthMetrics;<br>差异内容：end?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedPadding；<br>API声明：bottom?: LengthMetrics;<br>差异内容：bottom?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedPadding；<br>API声明：start?: LengthMetrics;<br>差异内容：start?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedEdgeWidths<br>差异内容：declare interface LocalizedEdgeWidths|component/units.d.ts|
|新增API|NA|类名：LocalizedEdgeWidths；<br>API声明：top?: LengthMetrics;<br>差异内容：top?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedEdgeWidths；<br>API声明：end?: LengthMetrics;<br>差异内容：end?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedEdgeWidths；<br>API声明：bottom?: LengthMetrics;<br>差异内容：bottom?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedEdgeWidths；<br>API声明：start?: LengthMetrics;<br>差异内容：start?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedBorderRadiuses<br>差异内容：declare interface LocalizedBorderRadiuses|component/units.d.ts|
|新增API|NA|类名：LocalizedBorderRadiuses；<br>API声明：topStart?: LengthMetrics;<br>差异内容：topStart?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedBorderRadiuses；<br>API声明：topEnd?: LengthMetrics;<br>差异内容：topEnd?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedBorderRadiuses；<br>API声明：bottomStart?: LengthMetrics;<br>差异内容：bottomStart?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedBorderRadiuses；<br>API声明：bottomEnd?: LengthMetrics;<br>差异内容：bottomEnd?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedEdgeColors<br>差异内容：declare interface LocalizedEdgeColors|component/units.d.ts|
|新增API|NA|类名：LocalizedEdgeColors；<br>API声明：top?: ResourceColor;<br>差异内容：top?: ResourceColor;|component/units.d.ts|
|新增API|NA|类名：LocalizedEdgeColors；<br>API声明：end?: ResourceColor;<br>差异内容：end?: ResourceColor;|component/units.d.ts|
|新增API|NA|类名：LocalizedEdgeColors；<br>API声明：bottom?: ResourceColor;<br>差异内容：bottom?: ResourceColor;|component/units.d.ts|
|新增API|NA|类名：LocalizedEdgeColors；<br>API声明：start?: ResourceColor;<br>差异内容：start?: ResourceColor;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type LocalizedMargin = LocalizedPadding;<br>差异内容：declare type LocalizedMargin = LocalizedPadding;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type VoidCallback = () => void;<br>差异内容：declare type VoidCallback = () => void;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type LengthMetricsUnit = import('../api/arkui/Graphics').LengthMetricsUnit;<br>差异内容：declare type LengthMetricsUnit = import('../api/arkui/Graphics').LengthMetricsUnit;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type LengthMetrics = import('../api/arkui/Graphics').LengthMetrics;<br>差异内容：declare type LengthMetrics = import('../api/arkui/Graphics').LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type ColorMetrics = import('../api/arkui/Graphics').ColorMetrics;<br>差异内容：declare type ColorMetrics = import('../api/arkui/Graphics').ColorMetrics;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedPosition<br>差异内容：declare interface LocalizedPosition|component/units.d.ts|
|新增API|NA|类名：LocalizedPosition；<br>API声明：start?: LengthMetrics;<br>差异内容：start?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedPosition；<br>API声明：top?: LengthMetrics;<br>差异内容：top?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface Edges<br>差异内容：declare interface Edges|component/units.d.ts|
|新增API|NA|类名：Edges；<br>API声明：top?: Dimension;<br>差异内容：top?: Dimension;|component/units.d.ts|
|新增API|NA|类名：Edges；<br>API声明：left?: Dimension;<br>差异内容：left?: Dimension;|component/units.d.ts|
|新增API|NA|类名：Edges；<br>API声明：bottom?: Dimension;<br>差异内容：bottom?: Dimension;|component/units.d.ts|
|新增API|NA|类名：Edges；<br>API声明：right?: Dimension;<br>差异内容：right?: Dimension;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface LocalizedEdges<br>差异内容：declare interface LocalizedEdges|component/units.d.ts|
|新增API|NA|类名：LocalizedEdges；<br>API声明：top?: LengthMetrics;<br>差异内容：top?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedEdges；<br>API声明：start?: LengthMetrics;<br>差异内容：start?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedEdges；<br>API声明：bottom?: LengthMetrics;<br>差异内容：bottom?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：LocalizedEdges；<br>API声明：end?: LengthMetrics;<br>差异内容：end?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：BorderOptions；<br>API声明：dashGap?: EdgeWidths \| LengthMetrics \| LocalizedEdgeWidths;<br>差异内容：dashGap?: EdgeWidths \| LengthMetrics \| LocalizedEdgeWidths;|component/units.d.ts|
|新增API|NA|类名：BorderOptions；<br>API声明：dashWidth?: EdgeWidths \| LengthMetrics \| LocalizedEdgeWidths;<br>差异内容：dashWidth?: EdgeWidths \| LengthMetrics \| LocalizedEdgeWidths;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DirectionalEdgesT<br>差异内容：declare interface DirectionalEdgesT|component/units.d.ts|
|新增API|NA|类名：DirectionalEdgesT；<br>API声明：start: T;<br>差异内容：start: T;|component/units.d.ts|
|新增API|NA|类名：DirectionalEdgesT；<br>API声明：end: T;<br>差异内容：end: T;|component/units.d.ts|
|新增API|NA|类名：DirectionalEdgesT；<br>API声明：top: T;<br>差异内容：top: T;|component/units.d.ts|
|新增API|NA|类名：DirectionalEdgesT；<br>API声明：bottom: T;<br>差异内容：bottom: T;|component/units.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DividerStyleOptions<br>差异内容：declare interface DividerStyleOptions|component/units.d.ts|
|新增API|NA|类名：DividerStyleOptions；<br>API声明：strokeWidth?: LengthMetrics;<br>差异内容：strokeWidth?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：DividerStyleOptions；<br>API声明：color?: ResourceColor;<br>差异内容：color?: ResourceColor;|component/units.d.ts|
|新增API|NA|类名：DividerStyleOptions；<br>API声明：startMargin?: LengthMetrics;<br>差异内容：startMargin?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：DividerStyleOptions；<br>API声明：endMargin?: LengthMetrics;<br>差异内容：endMargin?: LengthMetrics;|component/units.d.ts|
|新增API|NA|类名：VideoOptions；<br>API声明：imageAIOptions?: ImageAIOptions;<br>差异内容：imageAIOptions?: ImageAIOptions;|component/video.d.ts|
|新增API|NA|类名：VideoController；<br>API声明：reset(): void;<br>差异内容：reset(): void;|component/video.d.ts|
|新增API|NA|类名：VideoAttribute；<br>API声明：onStop(event: Callback\<void>): VideoAttribute;<br>差异内容：onStop(event: Callback\<void>): VideoAttribute;|component/video.d.ts|
|新增API|NA|类名：VideoAttribute；<br>API声明：enableAnalyzer(enable: boolean): VideoAttribute;<br>差异内容：enableAnalyzer(enable: boolean): VideoAttribute;|component/video.d.ts|
|新增API|NA|类名：VideoAttribute；<br>API声明：analyzerConfig(config: ImageAnalyzerConfig): VideoAttribute;<br>差异内容：analyzerConfig(config: ImageAnalyzerConfig): VideoAttribute;|component/video.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type GetItemMainSizeByIndex = (index: number) => number;<br>差异内容：declare type GetItemMainSizeByIndex = (index: number) => number;|component/water_flow.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class SectionOptions<br>差异内容：declare class SectionOptions|component/water_flow.d.ts|
|新增API|NA|类名：SectionOptions；<br>API声明：itemsCount: number;<br>差异内容：itemsCount: number;|component/water_flow.d.ts|
|新增API|NA|类名：SectionOptions；<br>API声明：crossCount?: number;<br>差异内容：crossCount?: number;|component/water_flow.d.ts|
|新增API|NA|类名：SectionOptions；<br>API声明：onGetItemMainSizeByIndex?: GetItemMainSizeByIndex;<br>差异内容：onGetItemMainSizeByIndex?: GetItemMainSizeByIndex;|component/water_flow.d.ts|
|新增API|NA|类名：SectionOptions；<br>API声明：columnsGap?: Dimension;<br>差异内容：columnsGap?: Dimension;|component/water_flow.d.ts|
|新增API|NA|类名：SectionOptions；<br>API声明：rowsGap?: Dimension;<br>差异内容：rowsGap?: Dimension;|component/water_flow.d.ts|
|新增API|NA|类名：SectionOptions；<br>API声明：margin?: Margin \| Dimension;<br>差异内容：margin?: Margin \| Dimension;|component/water_flow.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class WaterFlowSections<br>差异内容：declare class WaterFlowSections|component/water_flow.d.ts|
|新增API|NA|类名：WaterFlowSections；<br>API声明：splice(start: number, deleteCount?: number, sections?: Array\<SectionOptions>): boolean;<br>差异内容：splice(start: number, deleteCount?: number, sections?: Array\<SectionOptions>): boolean;|component/water_flow.d.ts|
|新增API|NA|类名：WaterFlowSections；<br>API声明：push(section: SectionOptions): boolean;<br>差异内容：push(section: SectionOptions): boolean;|component/water_flow.d.ts|
|新增API|NA|类名：WaterFlowSections；<br>API声明：update(sectionIndex: number, section: SectionOptions): boolean;<br>差异内容：update(sectionIndex: number, section: SectionOptions): boolean;|component/water_flow.d.ts|
|新增API|NA|类名：WaterFlowSections；<br>API声明：values(): Array\<SectionOptions>;<br>差异内容：values(): Array\<SectionOptions>;|component/water_flow.d.ts|
|新增API|NA|类名：WaterFlowSections；<br>API声明：length(): number;<br>差异内容：length(): number;|component/water_flow.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum WaterFlowLayoutMode<br>差异内容：declare enum WaterFlowLayoutMode|component/water_flow.d.ts|
|新增API|NA|类名：WaterFlowLayoutMode；<br>API声明：ALWAYS_TOP_DOWN = 0<br>差异内容：ALWAYS_TOP_DOWN = 0|component/water_flow.d.ts|
|新增API|NA|类名：WaterFlowLayoutMode；<br>API声明：SLIDING_WINDOW = 1<br>差异内容：SLIDING_WINDOW = 1|component/water_flow.d.ts|
|新增API|NA|类名：WaterFlowOptions；<br>API声明：sections?: WaterFlowSections;<br>差异内容：sections?: WaterFlowSections;|component/water_flow.d.ts|
|新增API|NA|类名：WaterFlowOptions；<br>API声明：layoutMode?: WaterFlowLayoutMode;<br>差异内容：layoutMode?: WaterFlowLayoutMode;|component/water_flow.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SurfaceRect<br>差异内容：declare interface SurfaceRect|component/xcomponent.d.ts|
|新增API|NA|类名：SurfaceRect；<br>API声明：offsetX?: number;<br>差异内容：offsetX?: number;|component/xcomponent.d.ts|
|新增API|NA|类名：SurfaceRect；<br>API声明：offsetY?: number;<br>差异内容：offsetY?: number;|component/xcomponent.d.ts|
|新增API|NA|类名：SurfaceRect；<br>API声明：surfaceWidth: number;<br>差异内容：surfaceWidth: number;|component/xcomponent.d.ts|
|新增API|NA|类名：SurfaceRect；<br>API声明：surfaceHeight: number;<br>差异内容：surfaceHeight: number;|component/xcomponent.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SurfaceRotationOptions<br>差异内容：declare interface SurfaceRotationOptions|component/xcomponent.d.ts|
|新增API|NA|类名：SurfaceRotationOptions；<br>API声明：lock?: boolean;<br>差异内容：lock?: boolean;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentController；<br>API声明：setXComponentSurfaceRect(rect: SurfaceRect): void;<br>差异内容：setXComponentSurfaceRect(rect: SurfaceRect): void;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentController；<br>API声明：getXComponentSurfaceRect(): SurfaceRect;<br>差异内容：getXComponentSurfaceRect(): SurfaceRect;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentController；<br>API声明：setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void;<br>差异内容：setXComponentSurfaceRotation(rotationOptions: SurfaceRotationOptions): void;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentController；<br>API声明：getXComponentSurfaceRotation(): Required\<SurfaceRotationOptions>;<br>差异内容：getXComponentSurfaceRotation(): Required\<SurfaceRotationOptions>;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentController；<br>API声明：onSurfaceCreated(surfaceId: string): void;<br>差异内容：onSurfaceCreated(surfaceId: string): void;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentController；<br>API声明：onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void;<br>差异内容：onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentController；<br>API声明：onSurfaceDestroyed(surfaceId: string): void;<br>差异内容：onSurfaceDestroyed(surfaceId: string): void;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentController；<br>API声明：startImageAnalyzer(config: ImageAnalyzerConfig): Promise\<void>;<br>差异内容：startImageAnalyzer(config: ImageAnalyzerConfig): Promise\<void>;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentController；<br>API声明：stopImageAnalyzer(): void;<br>差异内容：stopImageAnalyzer(): void;|component/xcomponent.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface XComponentOptions<br>差异内容：declare interface XComponentOptions|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentOptions；<br>API声明：type: XComponentType;<br>差异内容：type: XComponentType;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentOptions；<br>API声明：controller: XComponentController;<br>差异内容：controller: XComponentController;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentOptions；<br>API声明：imageAIOptions?: ImageAIOptions;<br>差异内容：imageAIOptions?: ImageAIOptions;|component/xcomponent.d.ts|
|新增API|NA|类名：XComponentAttribute；<br>API声明：enableAnalyzer(enable: boolean): XComponentAttribute;<br>差异内容：enableAnalyzer(enable: boolean): XComponentAttribute;|component/xcomponent.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface IconOptions<br>差异内容：export interface IconOptions|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：IconOptions；<br>API声明：src: ResourceStr;<br>差异内容：src: ResourceStr;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：IconOptions；<br>API声明：size?: SizeOptions;<br>差异内容：size?: SizeOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface LabelOptions<br>差异内容：export interface LabelOptions|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：LabelOptions；<br>API声明：text: string;<br>差异内容：text: string;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface ChipGroupItemOptions<br>差异内容：export interface ChipGroupItemOptions|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：prefixIcon?: IconOptions;<br>差异内容：prefixIcon?: IconOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：prefixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：prefixSymbol?: ChipSymbolGlyphOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：label: LabelOptions;<br>差异内容：label: LabelOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：suffixIcon?: IconOptions;<br>差异内容：suffixIcon?: IconOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：suffixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：suffixSymbol?: ChipSymbolGlyphOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupItemOptions；<br>API声明：allowClose?: boolean;<br>差异内容：allowClose?: boolean;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface ChipItemStyle<br>差异内容：export interface ChipItemStyle|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipItemStyle；<br>API声明：size?: ChipSize \| SizeOptions;<br>差异内容：size?: ChipSize \| SizeOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipItemStyle；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：backgroundColor?: ResourceColor;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipItemStyle；<br>API声明：fontColor?: ResourceColor;<br>差异内容：fontColor?: ResourceColor;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipItemStyle；<br>API声明：selectedFontColor?: ResourceColor;<br>差异内容：selectedFontColor?: ResourceColor;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipItemStyle；<br>API声明：selectedBackgroundColor?: ResourceColor;<br>差异内容：selectedBackgroundColor?: ResourceColor;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface ChipGroupSpaceOptions<br>差异内容：export interface ChipGroupSpaceOptions|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupSpaceOptions；<br>API声明：itemSpace?: string \| number;<br>差异内容：itemSpace?: string \| number;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupSpaceOptions；<br>API声明：startSpace?: Length;<br>差异内容：startSpace?: Length;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupSpaceOptions；<br>API声明：endSpace?: Length;<br>差异内容：endSpace?: Length;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface IconItemOptions<br>差异内容：export interface IconItemOptions|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：IconItemOptions；<br>API声明：icon: IconOptions;<br>差异内容：icon: IconOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：IconItemOptions；<br>API声明：action: Callback\<void>;<br>差异内容：action: Callback\<void>;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface ChipGroupPaddingOptions<br>差异内容：export interface ChipGroupPaddingOptions|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupPaddingOptions；<br>API声明：top: Length;<br>差异内容：top: Length;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroupPaddingOptions；<br>API声明：bottom: Length;<br>差异内容：bottom: Length;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct IconGroupSuffix<br>差异内容：export declare struct IconGroupSuffix|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：IconGroupSuffix；<br>API声明：@Require<br>    @Prop<br>    items: Array\<IconItemOptions \| SymbolGlyphModifier>;<br>差异内容：@Require<br>    @Prop<br>    items: Array\<IconItemOptions \| SymbolGlyphModifier>;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct ChipGroup<br>差异内容：export declare struct ChipGroup|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroup；<br>API声明：@Require<br>    @Prop<br>    items: ChipGroupItemOptions[];<br>差异内容：@Require<br>    @Prop<br>    items: ChipGroupItemOptions[];|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroup；<br>API声明：@Prop<br>    itemStyle?: ChipItemStyle;<br>差异内容：@Prop<br>    itemStyle?: ChipItemStyle;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroup；<br>API声明：@Prop<br>    selectedIndexes?: Array\<number>;<br>差异内容：@Prop<br>    selectedIndexes?: Array\<number>;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroup；<br>API声明：@Prop<br>    multiple?: boolean;<br>差异内容：@Prop<br>    multiple?: boolean;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroup；<br>API声明：@Prop<br>    chipGroupSpace?: ChipGroupSpaceOptions;<br>差异内容：@Prop<br>    chipGroupSpace?: ChipGroupSpaceOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroup；<br>API声明：@Prop<br>    chipGroupPadding?: ChipGroupPaddingOptions;<br>差异内容：@Prop<br>    chipGroupPadding?: ChipGroupPaddingOptions;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroup；<br>API声明：onChange?: Callback\<Array\<number>>;<br>差异内容：onChange?: Callback\<Array\<number>>;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：ChipGroup；<br>API声明：@BuilderParam<br>    suffix?: Callback\<void>;<br>差异内容：@BuilderParam<br>    suffix?: Callback\<void>;|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum DownloadIconStyle<br>差异内容：export declare enum DownloadIconStyle|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadIconStyle；<br>API声明：FULL_FILLED = 1<br>差异内容：FULL_FILLED = 1|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadIconStyle；<br>API声明：LINES = 2<br>差异内容：LINES = 2|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum DownloadDescription<br>差异内容：export declare enum DownloadDescription|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadDescription；<br>API声明：DOWNLOAD = 1<br>差异内容：DOWNLOAD = 1|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadDescription；<br>API声明：DOWNLOAD_FILE = 2<br>差异内容：DOWNLOAD_FILE = 2|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadDescription；<br>API声明：SAVE = 3<br>差异内容：SAVE = 3|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadDescription；<br>API声明：SAVE_IMAGE = 4<br>差异内容：SAVE_IMAGE = 4|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadDescription；<br>API声明：SAVE_FILE = 5<br>差异内容：SAVE_FILE = 5|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadDescription；<br>API声明：DOWNLOAD_AND_SHARE = 6<br>差异内容：DOWNLOAD_AND_SHARE = 6|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadDescription；<br>API声明：RECEIVE = 7<br>差异内容：RECEIVE = 7|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadDescription；<br>API声明：CONTINUE_TO_RECEIVE = 8<br>差异内容：CONTINUE_TO_RECEIVE = 8|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum DownloadLayoutDirection<br>差异内容：export declare enum DownloadLayoutDirection|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadLayoutDirection；<br>API声明：HORIZONTAL = 0<br>差异内容：HORIZONTAL = 0|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadLayoutDirection；<br>API声明：VERTICAL = 1<br>差异内容：VERTICAL = 1|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface DownloadContentOptions<br>差异内容：export interface DownloadContentOptions|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadContentOptions；<br>API声明：icon?: DownloadIconStyle;<br>差异内容：icon?: DownloadIconStyle;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadContentOptions；<br>API声明：text?: DownloadDescription;<br>差异内容：text?: DownloadDescription;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface DownloadStyleOptions<br>差异内容：export interface DownloadStyleOptions|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadStyleOptions；<br>API声明：iconSize?: Dimension;<br>差异内容：iconSize?: Dimension;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadStyleOptions；<br>API声明：layoutDirection?: DownloadLayoutDirection;<br>差异内容：layoutDirection?: DownloadLayoutDirection;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadStyleOptions；<br>API声明：fontSize?: Dimension;<br>差异内容：fontSize?: Dimension;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadStyleOptions；<br>API声明：fontStyle?: FontStyle;<br>差异内容：fontStyle?: FontStyle;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadStyleOptions；<br>API声明：fontWeight?: number \| FontWeight \| string;<br>差异内容：fontWeight?: number \| FontWeight \| string;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadStyleOptions；<br>API声明：fontFamily?: string \| Resource;<br>差异内容：fontFamily?: string \| Resource;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadStyleOptions；<br>API声明：fontColor?: ResourceColor;<br>差异内容：fontColor?: ResourceColor;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadStyleOptions；<br>API声明：iconColor?: ResourceColor;<br>差异内容：iconColor?: ResourceColor;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadStyleOptions；<br>API声明：textIconSpace?: Dimension;<br>差异内容：textIconSpace?: Dimension;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct DownloadFileButton<br>差异内容：export declare struct DownloadFileButton|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadFileButton；<br>API声明：@State<br>    contentOptions: DownloadContentOptions;<br>差异内容：@State<br>    contentOptions: DownloadContentOptions;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：DownloadFileButton；<br>API声明：@State<br>    styleOptions: DownloadStyleOptions;<br>差异内容：@State<br>    styleOptions: DownloadStyleOptions;|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum ExtraRegionPosition<br>差异内容：export declare enum ExtraRegionPosition|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：ExtraRegionPosition；<br>API声明：TOP = 1<br>差异内容：TOP = 1|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：ExtraRegionPosition；<br>API声明：BOTTOM = 2<br>差异内容：BOTTOM = 2|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface ExpandedRegionLayoutOptions<br>差异内容：export interface ExpandedRegionLayoutOptions|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：ExpandedRegionLayoutOptions；<br>API声明：horizontalSplitRatio?: number;<br>差异内容：horizontalSplitRatio?: number;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：ExpandedRegionLayoutOptions；<br>API声明：verticalSplitRatio?: number;<br>差异内容：verticalSplitRatio?: number;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：ExpandedRegionLayoutOptions；<br>API声明：isExtraRegionPerpendicular?: boolean;<br>差异内容：isExtraRegionPerpendicular?: boolean;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：ExpandedRegionLayoutOptions；<br>API声明：extraRegionPosition?: ExtraRegionPosition;<br>差异内容：extraRegionPosition?: ExtraRegionPosition;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface HoverModeRegionLayoutOptions<br>差异内容：export interface HoverModeRegionLayoutOptions|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：HoverModeRegionLayoutOptions；<br>API声明：horizontalSplitRatio?: number;<br>差异内容：horizontalSplitRatio?: number;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：HoverModeRegionLayoutOptions；<br>API声明：showExtraRegion?: boolean;<br>差异内容：showExtraRegion?: boolean;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：HoverModeRegionLayoutOptions；<br>API声明：extraRegionPosition?: ExtraRegionPosition;<br>差异内容：extraRegionPosition?: ExtraRegionPosition;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface FoldedRegionLayoutOptions<br>差异内容：export interface FoldedRegionLayoutOptions|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：FoldedRegionLayoutOptions；<br>API声明：verticalSplitRatio?: number;<br>差异内容：verticalSplitRatio?: number;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum PresetSplitRatio<br>差异内容：export declare enum PresetSplitRatio|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：PresetSplitRatio；<br>API声明：LAYOUT_1V1 = 1<br>差异内容：LAYOUT_1V1 = 1|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：PresetSplitRatio；<br>API声明：LAYOUT_2V3 = 0.6666666666666666<br>差异内容：LAYOUT_2V3 = 0.6666666666666666|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：PresetSplitRatio；<br>API声明：LAYOUT_3V2 = 1.5<br>差异内容：LAYOUT_3V2 = 1.5|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface HoverModeStatus<br>差异内容：export interface HoverModeStatus|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：HoverModeStatus；<br>API声明：foldStatus: display.FoldStatus;<br>差异内容：foldStatus: display.FoldStatus;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：HoverModeStatus；<br>API声明：isHoverMode: boolean;<br>差异内容：isHoverMode: boolean;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：HoverModeStatus；<br>API声明：appRotation: number;<br>差异内容：appRotation: number;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：HoverModeStatus；<br>API声明：windowStatusType: window.WindowStatusType;<br>差异内容：windowStatusType: window.WindowStatusType;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：global；<br>API声明：export type OnHoverStatusChangeHandler = (status: HoverModeStatus) => void;<br>差异内容：export type OnHoverStatusChangeHandler = (status: HoverModeStatus) => void;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct FoldSplitContainer<br>差异内容：export declare struct FoldSplitContainer|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：FoldSplitContainer；<br>API声明：@BuilderParam<br>    primary: Callback\<void>;<br>差异内容：@BuilderParam<br>    primary: Callback\<void>;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：FoldSplitContainer；<br>API声明：@BuilderParam<br>    secondary: Callback\<void>;<br>差异内容：@BuilderParam<br>    secondary: Callback\<void>;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：FoldSplitContainer；<br>API声明：@BuilderParam<br>    extra?: Callback\<void>;<br>差异内容：@BuilderParam<br>    extra?: Callback\<void>;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：FoldSplitContainer；<br>API声明：@Prop<br>    expandedLayoutOptions: ExpandedRegionLayoutOptions;<br>差异内容：@Prop<br>    expandedLayoutOptions: ExpandedRegionLayoutOptions;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：FoldSplitContainer；<br>API声明：@Prop<br>    hoverModeLayoutOptions: HoverModeRegionLayoutOptions;<br>差异内容：@Prop<br>    hoverModeLayoutOptions: HoverModeRegionLayoutOptions;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：FoldSplitContainer；<br>API声明：@Prop<br>    foldedLayoutOptions: FoldedRegionLayoutOptions;<br>差异内容：@Prop<br>    foldedLayoutOptions: FoldedRegionLayoutOptions;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：FoldSplitContainer；<br>API声明：@Prop<br>    animationOptions?: AnimateParam \| null;<br>差异内容：@Prop<br>    animationOptions?: AnimateParam \| null;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：FoldSplitContainer；<br>API声明：onHoverStatusChange?: OnHoverStatusChangeHandler;<br>差异内容：onHoverStatusChange?: OnHoverStatusChangeHandler;|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface FormMenuItemStyle<br>差异内容：export interface FormMenuItemStyle|api/@ohos.arkui.advanced.FormMenu.d.ets|
|新增API|NA|类名：FormMenuItemStyle；<br>API声明：options?: MenuItemOptions;<br>差异内容：options?: MenuItemOptions;|api/@ohos.arkui.advanced.FormMenu.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface AddFormOptions<br>差异内容：export interface AddFormOptions|api/@ohos.arkui.advanced.FormMenu.d.ets|
|新增API|NA|类名：AddFormOptions；<br>API声明：formBindingData?: formBindingData.FormBindingData;<br>差异内容：formBindingData?: formBindingData.FormBindingData;|api/@ohos.arkui.advanced.FormMenu.d.ets|
|新增API|NA|类名：AddFormOptions；<br>API声明：callback?: AsyncCallback\<string>;<br>差异内容：callback?: AsyncCallback\<string>;|api/@ohos.arkui.advanced.FormMenu.d.ets|
|新增API|NA|类名：AddFormOptions；<br>API声明：style?: FormMenuItemStyle;<br>差异内容：style?: FormMenuItemStyle;|api/@ohos.arkui.advanced.FormMenu.d.ets|
|新增API|NA|类名：global；<br>API声明：@Builder<br>export declare function AddFormMenuItem(want: Want, componentId: string, options?: AddFormOptions): void;<br>差异内容：@Builder<br>export declare function AddFormMenuItem(want: Want, componentId: string, options?: AddFormOptions): void;|api/@ohos.arkui.advanced.FormMenu.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct FullScreenLaunchComponent<br>差异内容：export declare struct FullScreenLaunchComponent|api/@ohos.arkui.advanced.FullScreenLaunchComponent.d.ets|
|新增API|NA|类名：FullScreenLaunchComponent；<br>API声明：@BuilderParam<br>    content: Callback\<void>;<br>差异内容：@BuilderParam<br>    content: Callback\<void>;|api/@ohos.arkui.advanced.FullScreenLaunchComponent.d.ets|
|新增API|NA|类名：FullScreenLaunchComponent；<br>API声明：appId: string;<br>差异内容：appId: string;|api/@ohos.arkui.advanced.FullScreenLaunchComponent.d.ets|
|新增API|NA|类名：FullScreenLaunchComponent；<br>API声明：options?: AtomicServiceOptions;<br>差异内容：options?: AtomicServiceOptions;|api/@ohos.arkui.advanced.FullScreenLaunchComponent.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface IDataSourcePrefetching<br>差异内容：export interface IDataSourcePrefetching|api/@ohos.arkui.Prefetcher.d.ts|
|新增API|NA|类名：IDataSourcePrefetching；<br>API声明：prefetch(index: number): Promise\<void> \| void;<br>差异内容：prefetch(index: number): Promise\<void> \| void;|api/@ohos.arkui.Prefetcher.d.ts|
|新增API|NA|类名：IDataSourcePrefetching；<br>API声明：cancel?(index: number): Promise\<void> \| void;<br>差异内容：cancel?(index: number): Promise\<void> \| void;|api/@ohos.arkui.Prefetcher.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface IPrefetcher<br>差异内容：export interface IPrefetcher|api/@ohos.arkui.Prefetcher.d.ts|
|新增API|NA|类名：IPrefetcher；<br>API声明：setDataSource(dataSource: IDataSourcePrefetching): void;<br>差异内容：setDataSource(dataSource: IDataSourcePrefetching): void;|api/@ohos.arkui.Prefetcher.d.ts|
|新增API|NA|类名：IPrefetcher；<br>API声明：visibleAreaChanged(minVisible: number, maxVisible: number): void;<br>差异内容：visibleAreaChanged(minVisible: number, maxVisible: number): void;|api/@ohos.arkui.Prefetcher.d.ts|
|新增API|NA|类名：global；<br>API声明：export class BasicPrefetcher<br>差异内容：export class BasicPrefetcher|api/@ohos.arkui.Prefetcher.d.ts|
|新增API|NA|类名：BasicPrefetcher；<br>API声明：setDataSource(dataSource: IDataSourcePrefetching): void;<br>差异内容：setDataSource(dataSource: IDataSourcePrefetching): void;|api/@ohos.arkui.Prefetcher.d.ts|
|新增API|NA|类名：BasicPrefetcher；<br>API声明：visibleAreaChanged(minVisible: number, maxVisible: number): void;<br>差异内容：visibleAreaChanged(minVisible: number, maxVisible: number): void;|api/@ohos.arkui.Prefetcher.d.ts|
|新增API|NA|类名：global；<br>API声明：interface ShapeSize<br>差异内容：interface ShapeSize|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：ShapeSize；<br>API声明：width?: number \| string;<br>差异内容：width?: number \| string;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：ShapeSize；<br>API声明：height?: number \| string;<br>差异内容：height?: number \| string;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：interface RectShapeOptions<br>差异内容：interface RectShapeOptions|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：RectShapeOptions；<br>API声明：radius?: number \| string \| Array\<number \| string>;<br>差异内容：radius?: number \| string \| Array\<number \| string>;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：interface RoundRectShapeOptions<br>差异内容：interface RoundRectShapeOptions|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：RoundRectShapeOptions；<br>API声明：radiusWidth?: number \| string;<br>差异内容：radiusWidth?: number \| string;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：RoundRectShapeOptions；<br>API声明：radiusHeight?: number \| string;<br>差异内容：radiusHeight?: number \| string;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：interface PathShapeOptions<br>差异内容：interface PathShapeOptions|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：PathShapeOptions；<br>API声明：commands?: string;<br>差异内容：commands?: string;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class CommonShapeMethod<br>差异内容：declare class CommonShapeMethod|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：CommonShapeMethod；<br>API声明：offset(offset: Position): T;<br>差异内容：offset(offset: Position): T;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：CommonShapeMethod；<br>API声明：fill(color: ResourceColor): T;<br>差异内容：fill(color: ResourceColor): T;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：CommonShapeMethod；<br>API声明：position(position: Position): T;<br>差异内容：position(position: Position): T;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class BaseShape<br>差异内容：declare class BaseShape|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：BaseShape；<br>API声明：width(width: Length): T;<br>差异内容：width(width: Length): T;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：BaseShape；<br>API声明：height(height: Length): T;<br>差异内容：height(height: Length): T;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：BaseShape；<br>API声明：size(size: SizeOptions): T;<br>差异内容：size(size: SizeOptions): T;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class RectShape<br>差异内容：export declare class RectShape|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：RectShape；<br>API声明：radiusWidth(rWidth: number \| string): RectShape;<br>差异内容：radiusWidth(rWidth: number \| string): RectShape;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：RectShape；<br>API声明：radiusHeight(rHeight: number \| string): RectShape;<br>差异内容：radiusHeight(rHeight: number \| string): RectShape;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：RectShape；<br>API声明：radius(radius: number \| string \| Array\<number \| string>): RectShape;<br>差异内容：radius(radius: number \| string \| Array\<number \| string>): RectShape;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class CircleShape<br>差异内容：export declare class CircleShape|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class EllipseShape<br>差异内容：export declare class EllipseShape|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class PathShape<br>差异内容：export declare class PathShape|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：PathShape；<br>API声明：commands(commands: string): PathShape;<br>差异内容：commands(commands: string): PathShape;|api/@ohos.arkui.shape.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare type StorageDefaultCreator\<T> = () => T;<br>差异内容：export declare type StorageDefaultCreator\<T> = () => T;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface TypeConstructorWithArgs<br>差异内容：export interface TypeConstructorWithArgs|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class AppStorageV2<br>差异内容：export declare class AppStorageV2|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：AppStorageV2；<br>API声明：static connect\<T extends object>(type: TypeConstructorWithArgs\<T>, keyOrDefaultCreator?: string \| StorageDefaultCreator\<T>, defaultCreator?: StorageDefaultCreator\<T>): T \| undefined;<br>差异内容：static connect\<T extends object>(type: TypeConstructorWithArgs\<T>, keyOrDefaultCreator?: string \| StorageDefaultCreator\<T>, defaultCreator?: StorageDefaultCreator\<T>): T \| undefined;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：AppStorageV2；<br>API声明：static remove\<T>(keyOrType: string \| TypeConstructorWithArgs\<T>): void;<br>差异内容：static remove\<T>(keyOrType: string \| TypeConstructorWithArgs\<T>): void;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：AppStorageV2；<br>API声明：static keys(): Array\<string>;<br>差异内容：static keys(): Array\<string>;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare type PersistenceErrorCallback = (key: string, reason: 'quota' \| 'serialization' \| 'unknown', message: string) => void;<br>差异内容：export declare type PersistenceErrorCallback = (key: string, reason: 'quota' \| 'serialization' \| 'unknown', message: string) => void;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class PersistenceV2<br>差异内容：export declare class PersistenceV2|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：PersistenceV2；<br>API声明：static save\<T>(keyOrType: string \| TypeConstructorWithArgs\<T>): void;<br>差异内容：static save\<T>(keyOrType: string \| TypeConstructorWithArgs\<T>): void;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：PersistenceV2；<br>API声明：static notifyOnError(callback: PersistenceErrorCallback \| undefined): void;<br>差异内容：static notifyOnError(callback: PersistenceErrorCallback \| undefined): void;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface TypeConstructor<br>差异内容：export interface TypeConstructor|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare type TypeDecorator = \<T>(type: TypeConstructor\<T>) => PropertyDecorator;<br>差异内容：export declare type TypeDecorator = \<T>(type: TypeConstructor\<T>) => PropertyDecorator;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare const Type: TypeDecorator;<br>差异内容：export declare const Type: TypeDecorator;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class UIUtils<br>差异内容：export declare class UIUtils|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：UIUtils；<br>API声明：static getTarget\<T extends object>(source: T): T;<br>差异内容：static getTarget\<T extends object>(source: T): T;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：UIUtils；<br>API声明：static makeObserved\<T extends object>(source: T): T;<br>差异内容：static makeObserved\<T extends object>(source: T): T;|api/@ohos.arkui.StateManagement.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare interface Theme<br>差异内容：export declare interface Theme|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Theme；<br>API声明：colors: Colors;<br>差异内容：colors: Colors;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare interface Colors<br>差异内容：export declare interface Colors|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：brand: ResourceColor;<br>差异内容：brand: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：warning: ResourceColor;<br>差异内容：warning: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：alert: ResourceColor;<br>差异内容：alert: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：confirm: ResourceColor;<br>差异内容：confirm: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：fontPrimary: ResourceColor;<br>差异内容：fontPrimary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：fontSecondary: ResourceColor;<br>差异内容：fontSecondary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：fontTertiary: ResourceColor;<br>差异内容：fontTertiary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：fontFourth: ResourceColor;<br>差异内容：fontFourth: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：fontEmphasize: ResourceColor;<br>差异内容：fontEmphasize: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：fontOnPrimary: ResourceColor;<br>差异内容：fontOnPrimary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：fontOnSecondary: ResourceColor;<br>差异内容：fontOnSecondary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：fontOnTertiary: ResourceColor;<br>差异内容：fontOnTertiary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：fontOnFourth: ResourceColor;<br>差异内容：fontOnFourth: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconPrimary: ResourceColor;<br>差异内容：iconPrimary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconSecondary: ResourceColor;<br>差异内容：iconSecondary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconTertiary: ResourceColor;<br>差异内容：iconTertiary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconFourth: ResourceColor;<br>差异内容：iconFourth: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconEmphasize: ResourceColor;<br>差异内容：iconEmphasize: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconSubEmphasize: ResourceColor;<br>差异内容：iconSubEmphasize: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconOnPrimary: ResourceColor;<br>差异内容：iconOnPrimary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconOnSecondary: ResourceColor;<br>差异内容：iconOnSecondary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconOnTertiary: ResourceColor;<br>差异内容：iconOnTertiary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：iconOnFourth: ResourceColor;<br>差异内容：iconOnFourth: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：backgroundPrimary: ResourceColor;<br>差异内容：backgroundPrimary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：backgroundSecondary: ResourceColor;<br>差异内容：backgroundSecondary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：backgroundTertiary: ResourceColor;<br>差异内容：backgroundTertiary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：backgroundFourth: ResourceColor;<br>差异内容：backgroundFourth: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：backgroundEmphasize: ResourceColor;<br>差异内容：backgroundEmphasize: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compForegroundPrimary: ResourceColor;<br>差异内容：compForegroundPrimary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compBackgroundPrimary: ResourceColor;<br>差异内容：compBackgroundPrimary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compBackgroundPrimaryTran: ResourceColor;<br>差异内容：compBackgroundPrimaryTran: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compBackgroundPrimaryContrary: ResourceColor;<br>差异内容：compBackgroundPrimaryContrary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compBackgroundGray: ResourceColor;<br>差异内容：compBackgroundGray: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compBackgroundSecondary: ResourceColor;<br>差异内容：compBackgroundSecondary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compBackgroundTertiary: ResourceColor;<br>差异内容：compBackgroundTertiary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compBackgroundEmphasize: ResourceColor;<br>差异内容：compBackgroundEmphasize: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compBackgroundNeutral: ResourceColor;<br>差异内容：compBackgroundNeutral: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compEmphasizeSecondary: ResourceColor;<br>差异内容：compEmphasizeSecondary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compEmphasizeTertiary: ResourceColor;<br>差异内容：compEmphasizeTertiary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compDivider: ResourceColor;<br>差异内容：compDivider: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compCommonContrary: ResourceColor;<br>差异内容：compCommonContrary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compBackgroundFocus: ResourceColor;<br>差异内容：compBackgroundFocus: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compFocusedPrimary: ResourceColor;<br>差异内容：compFocusedPrimary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compFocusedSecondary: ResourceColor;<br>差异内容：compFocusedSecondary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：compFocusedTertiary: ResourceColor;<br>差异内容：compFocusedTertiary: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：interactiveHover: ResourceColor;<br>差异内容：interactiveHover: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：interactivePressed: ResourceColor;<br>差异内容：interactivePressed: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：interactiveFocus: ResourceColor;<br>差异内容：interactiveFocus: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：interactiveActive: ResourceColor;<br>差异内容：interactiveActive: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：interactiveSelect: ResourceColor;<br>差异内容：interactiveSelect: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：Colors；<br>API声明：interactiveClick: ResourceColor;<br>差异内容：interactiveClick: ResourceColor;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare interface CustomTheme<br>差异内容：export declare interface CustomTheme|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：CustomTheme；<br>API声明：colors?: CustomColors;<br>差异内容：colors?: CustomColors;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare type CustomColors = Partial\<Colors>;<br>差异内容：export declare type CustomColors = Partial\<Colors>;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ThemeControl<br>差异内容：export declare class ThemeControl|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：ThemeControl；<br>API声明：static setDefaultTheme(theme: CustomTheme): void;<br>差异内容：static setDefaultTheme(theme: CustomTheme): void;|api/@ohos.arkui.theme.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace uiExtension<br>差异内容：declare namespace uiExtension|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：uiExtension；<br>API声明：interface WindowProxy<br>差异内容：interface WindowProxy|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：WindowProxy；<br>API声明：getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea;<br>差异内容：getWindowAvoidArea(type: window.AvoidAreaType): window.AvoidArea;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：WindowProxy；<br>API声明：on(type: 'avoidAreaChange', callback: Callback\<AvoidAreaInfo>): void;<br>差异内容：on(type: 'avoidAreaChange', callback: Callback\<AvoidAreaInfo>): void;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：WindowProxy；<br>API声明：off(type: 'avoidAreaChange', callback?: Callback\<AvoidAreaInfo>): void;<br>差异内容：off(type: 'avoidAreaChange', callback?: Callback\<AvoidAreaInfo>): void;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：WindowProxy；<br>API声明：on(type: 'windowSizeChange', callback: Callback\<window.Size>): void;<br>差异内容：on(type: 'windowSizeChange', callback: Callback\<window.Size>): void;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：WindowProxy；<br>API声明：off(type: 'windowSizeChange', callback?: Callback\<window.Size>): void;<br>差异内容：off(type: 'windowSizeChange', callback?: Callback\<window.Size>): void;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：WindowProxy；<br>API声明：createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise\<window.Window>;<br>差异内容：createSubWindowWithOptions(name: string, subWindowOptions: window.SubWindowOptions): Promise\<window.Window>;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：uiExtension；<br>API声明：interface AvoidAreaInfo<br>差异内容：interface AvoidAreaInfo|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：AvoidAreaInfo；<br>API声明：type: window.AvoidAreaType;<br>差异内容：type: window.AvoidAreaType;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：AvoidAreaInfo；<br>API声明：area: window.AvoidArea;<br>差异内容：area: window.AvoidArea;|api/@ohos.arkui.uiExtension.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare struct AtomicServiceNavigation<br>差异内容：export declare struct AtomicServiceNavigation|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@State<br>    navPathStack?: NavPathStack;<br>差异内容：@State<br>    navPathStack?: NavPathStack;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@BuilderParam<br>    navigationContent?: Callback\<void>;<br>差异内容：@BuilderParam<br>    navigationContent?: Callback\<void>;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@Prop<br>    title?: ResourceStr;<br>差异内容：@Prop<br>    title?: ResourceStr;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@Prop<br>    titleOptions?: TitleOptions;<br>差异内容：@Prop<br>    titleOptions?: TitleOptions;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@Prop<br>    hideTitleBar?: boolean;<br>差异内容：@Prop<br>    hideTitleBar?: boolean;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@Prop<br>    navBarWidth?: Length;<br>差异内容：@Prop<br>    navBarWidth?: Length;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@Prop<br>    mode?: NavigationMode;<br>差异内容：@Prop<br>    mode?: NavigationMode;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@BuilderParam<br>    navDestinationBuilder?: NavDestinationBuilder;<br>差异内容：@BuilderParam<br>    navDestinationBuilder?: NavDestinationBuilder;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@Prop<br>    navBarWidthRange?: [<br>        Dimension,<br>        Dimension<br>    ];<br>差异内容：@Prop<br>    navBarWidthRange?: [<br>        Dimension,<br>        Dimension<br>    ];|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：@Prop<br>    minContentWidth?: Dimension;<br>差异内容：@Prop<br>    minContentWidth?: Dimension;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：stateChangeCallback?: Callback\<boolean>;<br>差异内容：stateChangeCallback?: Callback\<boolean>;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：AtomicServiceNavigation；<br>API声明：modeChangeCallback?: Callback\<NavigationMode>;<br>差异内容：modeChangeCallback?: Callback\<NavigationMode>;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface TitleOptions<br>差异内容：export interface TitleOptions|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：TitleOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：backgroundColor?: ResourceColor;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：TitleOptions；<br>API声明：isBlurEnabled?: boolean;<br>差异内容：isBlurEnabled?: boolean;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：TitleOptions；<br>API声明：barStyle?: BarStyle;<br>差异内容：barStyle?: BarStyle;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：global；<br>API声明：export type NavDestinationBuilder = (name: string, param?: Object) => void;<br>差异内容：export type NavDestinationBuilder = (name: string, param?: Object) => void;|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct AtomicServiceTabs<br>差异内容：export declare struct AtomicServiceTabs|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：@BuilderParam<br>    tabContents?: [<br>        TabContentBuilder?,<br>        TabContentBuilder?,<br>        TabContentBuilder?,<br>        TabContentBuilder?,<br>        TabContentBuilder?<br>    ];<br>差异内容：@BuilderParam<br>    tabContents?: [<br>        TabContentBuilder?,<br>        TabContentBuilder?,<br>        TabContentBuilder?,<br>        TabContentBuilder?,<br>        TabContentBuilder?<br>    ];|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：@Prop<br>    tabBarOptionsArray: [<br>        TabBarOptions,<br>        TabBarOptions,<br>        TabBarOptions?,<br>        TabBarOptions?,<br>        TabBarOptions?<br>    ];<br>差异内容：@Prop<br>    tabBarOptionsArray: [<br>        TabBarOptions,<br>        TabBarOptions,<br>        TabBarOptions?,<br>        TabBarOptions?,<br>        TabBarOptions?<br>    ];|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：@Prop<br>    tabBarPosition?: TabBarPosition;<br>差异内容：@Prop<br>    tabBarPosition?: TabBarPosition;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：@Prop<br>    barBackgroundColor?: ResourceColor;<br>差异内容：@Prop<br>    barBackgroundColor?: ResourceColor;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：@Prop<br>    index?: number;<br>差异内容：@Prop<br>    index?: number;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：@Prop<br>    barOverlap?: boolean;<br>差异内容：@Prop<br>    barOverlap?: boolean;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：controller?: TabsController;<br>差异内容：controller?: TabsController;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：onChange?: Callback\<number>;<br>差异内容：onChange?: Callback\<number>;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：onTabBarClick?: Callback\<number>;<br>差异内容：onTabBarClick?: Callback\<number>;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：AtomicServiceTabs；<br>API声明：onContentWillChange?: OnContentWillChangeCallback;<br>差异内容：onContentWillChange?: OnContentWillChangeCallback;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class TabBarOptions<br>差异内容：export declare class TabBarOptions|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum TabBarPosition<br>差异内容：export declare enum TabBarPosition|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：TabBarPosition；<br>API声明：LEFT = 0<br>差异内容：LEFT = 0|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：TabBarPosition；<br>API声明：BOTTOM = 1<br>差异内容：BOTTOM = 1|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：global；<br>API声明：export type TabContentBuilder = () => void;<br>差异内容：export type TabContentBuilder = () => void;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：global；<br>API声明：export type OnContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean;<br>差异内容：export type OnContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean;|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct AtomicServiceWeb<br>差异内容：export declare struct AtomicServiceWeb|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：src: ResourceStr;<br>差异内容：src: ResourceStr;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：@ObjectLink<br>    controller: AtomicServiceWebController;<br>差异内容：@ObjectLink<br>    controller: AtomicServiceWebController;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：@Prop<br>    mixedMode?: MixedMode;<br>差异内容：@Prop<br>    mixedMode?: MixedMode;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：@Prop<br>    darkMode?: WebDarkMode;<br>差异内容：@Prop<br>    darkMode?: WebDarkMode;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：@Prop<br>    forceDarkAccess?: boolean;<br>差异内容：@Prop<br>    forceDarkAccess?: boolean;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：navPathStack?: NavPathStack;<br>差异内容：navPathStack?: NavPathStack;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：onMessage?: Callback\<OnMessageEvent>;<br>差异内容：onMessage?: Callback\<OnMessageEvent>;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：onErrorReceive?: Callback\<OnErrorReceiveEvent>;<br>差异内容：onErrorReceive?: Callback\<OnErrorReceiveEvent>;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：onHttpErrorReceive?: Callback\<OnHttpErrorReceiveEvent>;<br>差异内容：onHttpErrorReceive?: Callback\<OnHttpErrorReceiveEvent>;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：onPageBegin?: Callback\<OnPageBeginEvent>;<br>差异内容：onPageBegin?: Callback\<OnPageBeginEvent>;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：onPageEnd?: Callback\<OnPageEndEvent>;<br>差异内容：onPageEnd?: Callback\<OnPageEndEvent>;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：onControllerAttached?: Callback\<void>;<br>差异内容：onControllerAttached?: Callback\<void>;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：onLoadIntercept?: OnLoadInterceptCallback;<br>差异内容：onLoadIntercept?: OnLoadInterceptCallback;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWeb；<br>API声明：onProgressChange?: Callback\<OnProgressChangeEvent>;<br>差异内容：onProgressChange?: Callback\<OnProgressChangeEvent>;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface OnMessageEvent<br>差异内容：export declare interface OnMessageEvent|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：OnMessageEvent；<br>API声明：data: object[];<br>差异内容：data: object[];|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface OnErrorReceiveEvent<br>差异内容：export declare interface OnErrorReceiveEvent|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：OnErrorReceiveEvent；<br>API声明：request: WebResourceRequest;<br>差异内容：request: WebResourceRequest;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：OnErrorReceiveEvent；<br>API声明：error: WebResourceError;<br>差异内容：error: WebResourceError;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface OnHttpErrorReceiveEvent<br>差异内容：export declare interface OnHttpErrorReceiveEvent|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：OnHttpErrorReceiveEvent；<br>API声明：request: WebResourceRequest;<br>差异内容：request: WebResourceRequest;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：OnHttpErrorReceiveEvent；<br>API声明：response: WebResourceResponse;<br>差异内容：response: WebResourceResponse;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface OnPageBeginEvent<br>差异内容：export declare interface OnPageBeginEvent|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：OnPageBeginEvent；<br>API声明：url: string;<br>差异内容：url: string;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface OnPageEndEvent<br>差异内容：export declare interface OnPageEndEvent|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：OnPageEndEvent；<br>API声明：url: string;<br>差异内容：url: string;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface OnLoadInterceptEvent<br>差异内容：export declare interface OnLoadInterceptEvent|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：OnLoadInterceptEvent；<br>API声明：data: WebResourceRequest;<br>差异内容：data: WebResourceRequest;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface OnProgressChangeEvent<br>差异内容：export declare interface OnProgressChangeEvent|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：OnProgressChangeEvent；<br>API声明：newProgress: number;<br>差异内容：newProgress: number;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class AtomicServiceWebController<br>差异内容：export declare class AtomicServiceWebController|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：getUserAgent(): string;<br>差异内容：getUserAgent(): string;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：getCustomUserAgent(): string;<br>差异内容：getCustomUserAgent(): string;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：setCustomUserAgent(userAgent: string): void;<br>差异内容：setCustomUserAgent(userAgent: string): void;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：refresh(): void;<br>差异内容：refresh(): void;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：forward(): void;<br>差异内容：forward(): void;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：backward(): void;<br>差异内容：backward(): void;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：accessForward(): boolean;<br>差异内容：accessForward(): boolean;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：accessBackward(): boolean;<br>差异内容：accessBackward(): boolean;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：accessStep(step: number): boolean;<br>差异内容：accessStep(step: number): boolean;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：AtomicServiceWebController；<br>API声明：loadUrl(url: string \| Resource, headers?: Array\<WebHeader>): void;<br>差异内容：loadUrl(url: string \| Resource, headers?: Array\<WebHeader>): void;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface WebHeader<br>差异内容：export declare interface WebHeader|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：WebHeader；<br>API声明：headerKey: string;<br>差异内容：headerKey: string;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：WebHeader；<br>API声明：headerValue: string;<br>差异内容：headerValue: string;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export type OnLoadInterceptCallback = (event: OnLoadInterceptEvent) => boolean;<br>差异内容：export type OnLoadInterceptCallback = (event: OnLoadInterceptEvent) => boolean;|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum IconStyle<br>差异内容：export declare enum IconStyle|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：IconStyle；<br>API声明：DARK = 0<br>差异内容：DARK = 0|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：IconStyle；<br>API声明：LIGHT = 1<br>差异内容：LIGHT = 1|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum TitlePosition<br>差异内容：export declare enum TitlePosition|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：TitlePosition；<br>API声明：TOP = 0<br>差异内容：TOP = 0|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：TitlePosition；<br>API声明：BOTTOM = 1<br>差异内容：BOTTOM = 1|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare enum BottomOffset<br>差异内容：export declare enum BottomOffset|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：BottomOffset；<br>API声明：OFFSET_FOR_BAR = 0<br>差异内容：OFFSET_FOR_BAR = 0|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：BottomOffset；<br>API声明：OFFSET_FOR_NONE = 1<br>差异内容：OFFSET_FOR_NONE = 1|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface DialogOptions<br>差异内容：export declare interface DialogOptions|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：uiContext: UIContext;<br>差异内容：uiContext: UIContext;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：bottomOffsetType?: BottomOffset;<br>差异内容：bottomOffsetType?: BottomOffset;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：title?: ResourceStr;<br>差异内容：title?: ResourceStr;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：subtitle?: ResourceStr;<br>差异内容：subtitle?: ResourceStr;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：titleColor?: ResourceStr \| Color;<br>差异内容：titleColor?: ResourceStr \| Color;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：subtitleColor?: ResourceStr \| Color;<br>差异内容：subtitleColor?: ResourceStr \| Color;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：backgroundImage?: Resource;<br>差异内容：backgroundImage?: Resource;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：foregroundImage?: Resource;<br>差异内容：foregroundImage?: Resource;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：iconStyle?: IconStyle;<br>差异内容：iconStyle?: IconStyle;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：titlePosition?: TitlePosition;<br>差异内容：titlePosition?: TitlePosition;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：onDialogClick?: Callback\<void>;<br>差异内容：onDialogClick?: Callback\<void>;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：DialogOptions；<br>API声明：onDialogClose?: Callback\<void>;<br>差异内容：onDialogClose?: Callback\<void>;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class InterstitialDialogAction<br>差异内容：export declare class InterstitialDialogAction|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：InterstitialDialogAction；<br>API声明：openDialog(): void;<br>差异内容：openDialog(): void;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：InterstitialDialogAction；<br>API声明：closeDialog(): void;<br>差异内容：closeDialog(): void;|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class NavPushPathHelper<br>差异内容：export declare class NavPushPathHelper|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：pushPath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise\<void>;<br>差异内容：pushPath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：pushPath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise\<void>;<br>差异内容：pushPath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：pushDestination(moduleName: string, info: NavPathInfo, animated?: boolean): Promise\<void>;<br>差异内容：pushDestination(moduleName: string, info: NavPathInfo, animated?: boolean): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：pushDestination(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise\<void>;<br>差异内容：pushDestination(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：pushPathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise\<void>;<br>差异内容：pushPathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：pushPathByName(moduleName: string, name: string, param: Object, onPop: Callback\<PopInfo>, animated?: boolean): Promise\<void>;<br>差异内容：pushPathByName(moduleName: string, name: string, param: Object, onPop: Callback\<PopInfo>, animated?: boolean): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：pushDestinationByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise\<void>;<br>差异内容：pushDestinationByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：pushDestinationByName(moduleName: string, name: string, param: Object, onPop: Callback\<PopInfo>, animated?: boolean): Promise\<void>;<br>差异内容：pushDestinationByName(moduleName: string, name: string, param: Object, onPop: Callback\<PopInfo>, animated?: boolean): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：replacePath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise\<void>;<br>差异内容：replacePath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：replacePath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise\<void>;<br>差异内容：replacePath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：NavPushPathHelper；<br>API声明：replacePathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise\<void>;<br>差异内容：replacePathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise\<void>;|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增API|NA|类名：global；<br>API声明：declare namespace screenshot<br>差异内容：declare namespace screenshot|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：screenshot；<br>API声明：function pick(): Promise\<PickInfo>;<br>差异内容：function pick(): Promise\<PickInfo>;|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：screenshot；<br>API声明：interface PickInfo<br>差异内容：interface PickInfo|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：PickInfo；<br>API声明：pickRect: Rect;<br>差异内容：pickRect: Rect;|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：PickInfo；<br>API声明：pixelMap: image.PixelMap;<br>差异内容：pixelMap: image.PixelMap;|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：screenshot；<br>API声明：interface Rect<br>差异内容：interface Rect|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：Rect；<br>API声明：left: number;<br>差异内容：left: number;|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：Rect；<br>API声明：top: number;<br>差异内容：top: number;|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：Rect；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：Rect；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.screenshot.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class AlphabetIndexerModifier<br>差异内容：export declare class AlphabetIndexerModifier|api/arkui/AlphabetIndexerModifier.d.ts|
|新增API|NA|类名：AlphabetIndexerModifier；<br>API声明：applyNormalAttribute?(instance: AlphabetIndexerAttribute): void;<br>差异内容：applyNormalAttribute?(instance: AlphabetIndexerAttribute): void;|api/arkui/AlphabetIndexerModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type Initializer\<T> = () => T;<br>差异内容：declare type Initializer\<T> = () => T;|api/arkui/AttributeUpdater.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class AttributeUpdater<br>差异内容：export declare class AttributeUpdater|api/arkui/AttributeUpdater.d.ts|
|新增API|NA|类名：AttributeUpdater；<br>API声明：applyNormalAttribute?(instance: T): void;<br>差异内容：applyNormalAttribute?(instance: T): void;|api/arkui/AttributeUpdater.d.ts|
|新增API|NA|类名：AttributeUpdater；<br>API声明：initializeModifier(instance: T): void;<br>差异内容：initializeModifier(instance: T): void;|api/arkui/AttributeUpdater.d.ts|
|新增API|NA|类名：AttributeUpdater；<br>API声明：get attribute(): T \| undefined;<br>差异内容：get attribute(): T \| undefined;|api/arkui/AttributeUpdater.d.ts|
|新增API|NA|类名：AttributeUpdater；<br>API声明：updateConstructorParams: C;<br>差异内容：updateConstructorParams: C;|api/arkui/AttributeUpdater.d.ts|
|新增API|NA|类名：AttributeUpdater；<br>API声明：onComponentChanged(component: T): void;<br>差异内容：onComponentChanged(component: T): void;|api/arkui/AttributeUpdater.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class BlankModifier<br>差异内容：export declare class BlankModifier|api/arkui/BlankModifier.d.ts|
|新增API|NA|类名：BlankModifier；<br>API声明：applyNormalAttribute?(instance: BlankAttribute): void;<br>差异内容：applyNormalAttribute?(instance: BlankAttribute): void;|api/arkui/BlankModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ButtonModifier<br>差异内容：export declare class ButtonModifier|api/arkui/ButtonModifier.d.ts|
|新增API|NA|类名：ButtonModifier；<br>API声明：applyNormalAttribute?(instance: ButtonAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ButtonAttribute): void;|api/arkui/ButtonModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class CalendarPickerModifier<br>差异内容：export declare class CalendarPickerModifier|api/arkui/CalendarPickerModifier.d.ts|
|新增API|NA|类名：CalendarPickerModifier；<br>API声明：applyNormalAttribute?(instance: CalendarPickerAttribute): void;<br>差异内容：applyNormalAttribute?(instance: CalendarPickerAttribute): void;|api/arkui/CalendarPickerModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class CheckboxGroupModifier<br>差异内容：export declare class CheckboxGroupModifier|api/arkui/CheckboxGroupModifier.d.ts|
|新增API|NA|类名：CheckboxGroupModifier；<br>API声明：applyNormalAttribute?(instance: CheckboxGroupAttribute): void;<br>差异内容：applyNormalAttribute?(instance: CheckboxGroupAttribute): void;|api/arkui/CheckboxGroupModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class CheckboxModifier<br>差异内容：export declare class CheckboxModifier|api/arkui/CheckboxModifier.d.ts|
|新增API|NA|类名：CheckboxModifier；<br>API声明：applyNormalAttribute?(instance: CheckboxAttribute): void;<br>差异内容：applyNormalAttribute?(instance: CheckboxAttribute): void;|api/arkui/CheckboxModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ColumnModifier<br>差异内容：export declare class ColumnModifier|api/arkui/ColumnModifier.d.ts|
|新增API|NA|类名：ColumnModifier；<br>API声明：applyNormalAttribute?(instance: ColumnAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ColumnAttribute): void;|api/arkui/ColumnModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ColumnSplitModifier<br>差异内容：export declare class ColumnSplitModifier|api/arkui/ColumnSplitModifier.d.ts|
|新增API|NA|类名：ColumnSplitModifier；<br>API声明：applyNormalAttribute?(instance: ColumnSplitAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ColumnSplitAttribute): void;|api/arkui/ColumnSplitModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class CommonModifier<br>差异内容：export declare class CommonModifier|api/arkui/CommonModifier.d.ts|
|新增API|NA|类名：CommonModifier；<br>API声明：applyNormalAttribute?(instance: CommonAttribute): void;<br>差异内容：applyNormalAttribute?(instance: CommonAttribute): void;|api/arkui/CommonModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export class ComponentContent<br>差异内容：export class ComponentContent|api/arkui/ComponentContent.d.ts|
|新增API|NA|类名：ComponentContent；<br>API声明：update(args: T): void;<br>差异内容：update(args: T): void;|api/arkui/ComponentContent.d.ts|
|新增API|NA|类名：ComponentContent；<br>API声明：reuse(param?: Object): void;<br>差异内容：reuse(param?: Object): void;|api/arkui/ComponentContent.d.ts|
|新增API|NA|类名：ComponentContent；<br>API声明：recycle(): void;<br>差异内容：recycle(): void;|api/arkui/ComponentContent.d.ts|
|新增API|NA|类名：ComponentContent；<br>API声明：dispose(): void;<br>差异内容：dispose(): void;|api/arkui/ComponentContent.d.ts|
|新增API|NA|类名：ComponentContent；<br>API声明：updateConfiguration(): void;<br>差异内容：updateConfiguration(): void;|api/arkui/ComponentContent.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ContainerSpanModifier<br>差异内容：export declare class ContainerSpanModifier|api/arkui/ContainerSpanModifier.d.ts|
|新增API|NA|类名：ContainerSpanModifier；<br>API声明：applyNormalAttribute?(containerSpanAttribute: ContainerSpanAttribute): void;<br>差异内容：applyNormalAttribute?(containerSpanAttribute: ContainerSpanAttribute): void;|api/arkui/ContainerSpanModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export abstract class Content<br>差异内容：export abstract class Content|api/arkui/Content.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class CounterModifier<br>差异内容：export declare class CounterModifier|api/arkui/CounterModifier.d.ts|
|新增API|NA|类名：CounterModifier；<br>API声明：applyNormalAttribute?(instance: CounterAttribute): void;<br>差异内容：applyNormalAttribute?(instance: CounterAttribute): void;|api/arkui/CounterModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class DataPanelModifier<br>差异内容：export declare class DataPanelModifier|api/arkui/DataPanelModifier.d.ts|
|新增API|NA|类名：DataPanelModifier；<br>API声明：applyNormalAttribute?(instance: DataPanelAttribute): void;<br>差异内容：applyNormalAttribute?(instance: DataPanelAttribute): void;|api/arkui/DataPanelModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class DatePickerModifier<br>差异内容：export declare class DatePickerModifier|api/arkui/DatePickerModifier.d.ts|
|新增API|NA|类名：DatePickerModifier；<br>API声明：applyNormalAttribute?(instance: DatePickerAttribute): void;<br>差异内容：applyNormalAttribute?(instance: DatePickerAttribute): void;|api/arkui/DatePickerModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class DividerModifier<br>差异内容：export declare class DividerModifier|api/arkui/DividerModifier.d.ts|
|新增API|NA|类名：DividerModifier；<br>API声明：applyNormalAttribute?(instance: DividerAttribute): void;<br>差异内容：applyNormalAttribute?(instance: DividerAttribute): void;|api/arkui/DividerModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class GaugeModifier<br>差异内容：export declare class GaugeModifier|api/arkui/GaugeModifier.d.ts|
|新增API|NA|类名：GaugeModifier；<br>API声明：applyNormalAttribute?(instance: GaugeAttribute): void;<br>差异内容：applyNormalAttribute?(instance: GaugeAttribute): void;|api/arkui/GaugeModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class GridColModifier<br>差异内容：export declare class GridColModifier|api/arkui/GridColModifier.d.ts|
|新增API|NA|类名：GridColModifier；<br>API声明：applyNormalAttribute?(instance: GridColAttribute): void;<br>差异内容：applyNormalAttribute?(instance: GridColAttribute): void;|api/arkui/GridColModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class GridItemModifier<br>差异内容：export declare class GridItemModifier|api/arkui/GridItemModifier.d.ts|
|新增API|NA|类名：GridItemModifier；<br>API声明：applyNormalAttribute?(instance: GridItemAttribute): void;<br>差异内容：applyNormalAttribute?(instance: GridItemAttribute): void;|api/arkui/GridItemModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class GridModifier<br>差异内容：export declare class GridModifier|api/arkui/GridModifier.d.ts|
|新增API|NA|类名：GridModifier；<br>API声明：applyNormalAttribute?(instance: GridAttribute): void;<br>差异内容：applyNormalAttribute?(instance: GridAttribute): void;|api/arkui/GridModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class GridRowModifier<br>差异内容：export declare class GridRowModifier|api/arkui/GridRowModifier.d.ts|
|新增API|NA|类名：GridRowModifier；<br>API声明：applyNormalAttribute?(instance: GridRowAttribute): void;<br>差异内容：applyNormalAttribute?(instance: GridRowAttribute): void;|api/arkui/GridRowModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class HyperlinkModifier<br>差异内容：export declare class HyperlinkModifier|api/arkui/HyperlinkModifier.d.ts|
|新增API|NA|类名：HyperlinkModifier；<br>API声明：applyNormalAttribute?(instance: HyperlinkAttribute): void;<br>差异内容：applyNormalAttribute?(instance: HyperlinkAttribute): void;|api/arkui/HyperlinkModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ImageAnimatorModifier<br>差异内容：export declare class ImageAnimatorModifier|api/arkui/ImageAnimatorModifier.d.ts|
|新增API|NA|类名：ImageAnimatorModifier；<br>API声明：applyNormalAttribute?(instance: ImageAnimatorAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ImageAnimatorAttribute): void;|api/arkui/ImageAnimatorModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ImageModifier<br>差异内容：export declare class ImageModifier|api/arkui/ImageModifier.d.ts|
|新增API|NA|类名：ImageModifier；<br>API声明：applyNormalAttribute?(instance: ImageAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ImageAttribute): void;|api/arkui/ImageModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ImageSpanModifier<br>差异内容：export declare class ImageSpanModifier|api/arkui/ImageSpanModifier.d.ts|
|新增API|NA|类名：ImageSpanModifier；<br>API声明：applyNormalAttribute?(instance: ImageSpanAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ImageSpanAttribute): void;|api/arkui/ImageSpanModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class LineModifier<br>差异内容：export declare class LineModifier|api/arkui/LineModifier.d.ts|
|新增API|NA|类名：LineModifier；<br>API声明：applyNormalAttribute?(instance: LineAttribute): void;<br>差异内容：applyNormalAttribute?(instance: LineAttribute): void;|api/arkui/LineModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ListItemGroupModifier<br>差异内容：export declare class ListItemGroupModifier|api/arkui/ListItemGroupModifier.d.ts|
|新增API|NA|类名：ListItemGroupModifier；<br>API声明：applyNormalAttribute?(instance: ListItemGroupAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ListItemGroupAttribute): void;|api/arkui/ListItemGroupModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ListItemModifier<br>差异内容：export declare class ListItemModifier|api/arkui/ListItemModifier.d.ts|
|新增API|NA|类名：ListItemModifier；<br>API声明：applyNormalAttribute?(instance: ListItemAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ListItemAttribute): void;|api/arkui/ListItemModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ListModifier<br>差异内容：export declare class ListModifier|api/arkui/ListModifier.d.ts|
|新增API|NA|类名：ListModifier；<br>API声明：applyNormalAttribute?(instance: ListAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ListAttribute): void;|api/arkui/ListModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class LoadingProgressModifier<br>差异内容：export declare class LoadingProgressModifier|api/arkui/LoadingProgressModifier.d.ts|
|新增API|NA|类名：LoadingProgressModifier；<br>API声明：applyNormalAttribute?(instance: LoadingProgressAttribute): void;<br>差异内容：applyNormalAttribute?(instance: LoadingProgressAttribute): void;|api/arkui/LoadingProgressModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class MarqueeModifier<br>差异内容：export declare class MarqueeModifier|api/arkui/MarqueeModifier.d.ts|
|新增API|NA|类名：MarqueeModifier；<br>API声明：applyNormalAttribute?(instance: MarqueeAttribute): void;<br>差异内容：applyNormalAttribute?(instance: MarqueeAttribute): void;|api/arkui/MarqueeModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class MenuItemModifier<br>差异内容：export declare class MenuItemModifier|api/arkui/MenuItemModifier.d.ts|
|新增API|NA|类名：MenuItemModifier；<br>API声明：applyNormalAttribute?(instance: MenuItemAttribute): void;<br>差异内容：applyNormalAttribute?(instance: MenuItemAttribute): void;|api/arkui/MenuItemModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class MenuModifier<br>差异内容：export declare class MenuModifier|api/arkui/MenuModifier.d.ts|
|新增API|NA|类名：MenuModifier；<br>API声明：applyNormalAttribute?(instance: MenuAttribute): void;<br>差异内容：applyNormalAttribute?(instance: MenuAttribute): void;|api/arkui/MenuModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class NavDestinationModifier<br>差异内容：export declare class NavDestinationModifier|api/arkui/NavDestinationModifier.d.ts|
|新增API|NA|类名：NavDestinationModifier；<br>API声明：applyNormalAttribute?(instance: NavDestinationAttribute): void;<br>差异内容：applyNormalAttribute?(instance: NavDestinationAttribute): void;|api/arkui/NavDestinationModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class NavigationModifier<br>差异内容：export declare class NavigationModifier|api/arkui/NavigationModifier.d.ts|
|新增API|NA|类名：NavigationModifier；<br>API声明：applyNormalAttribute?(instance: NavigationAttribute): void;<br>差异内容：applyNormalAttribute?(instance: NavigationAttribute): void;|api/arkui/NavigationModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class NavigatorModifier<br>差异内容：export declare class NavigatorModifier|api/arkui/NavigatorModifier.d.ts|
|新增API|NA|类名：NavigatorModifier；<br>API声明：applyNormalAttribute?(instance: NavigatorAttribute): void;<br>差异内容：applyNormalAttribute?(instance: NavigatorAttribute): void;|api/arkui/NavigatorModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class NavRouterModifier<br>差异内容：export declare class NavRouterModifier|api/arkui/NavRouterModifier.d.ts|
|新增API|NA|类名：NavRouterModifier；<br>API声明：applyNormalAttribute?(instance: NavRouterAttribute): void;<br>差异内容：applyNormalAttribute?(instance: NavRouterAttribute): void;|api/arkui/NavRouterModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export class NodeContent<br>差异内容：export class NodeContent|api/arkui/NodeContent.d.ts|
|新增API|NA|类名：NodeContent；<br>API声明：addFrameNode(node: FrameNode): void;<br>差异内容：addFrameNode(node: FrameNode): void;|api/arkui/NodeContent.d.ts|
|新增API|NA|类名：NodeContent；<br>API声明：removeFrameNode(node: FrameNode): void;<br>差异内容：removeFrameNode(node: FrameNode): void;|api/arkui/NodeContent.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class PanelModifier<br>差异内容：export declare class PanelModifier|api/arkui/PanelModifier.d.ts|
|新增API|NA|类名：PanelModifier；<br>API声明：applyNormalAttribute?(instance: PanelAttribute): void;<br>差异内容：applyNormalAttribute?(instance: PanelAttribute): void;|api/arkui/PanelModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ParticleModifier<br>差异内容：export declare class ParticleModifier|api/arkui/ParticleModifier.d.ts|
|新增API|NA|类名：ParticleModifier；<br>API声明：applyNormalAttribute?(particleAttribute: ParticleAttribute): void;<br>差异内容：applyNormalAttribute?(particleAttribute: ParticleAttribute): void;|api/arkui/ParticleModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class PathModifier<br>差异内容：export declare class PathModifier|api/arkui/PathModifier.d.ts|
|新增API|NA|类名：PathModifier；<br>API声明：applyNormalAttribute?(instance: PathAttribute): void;<br>差异内容：applyNormalAttribute?(instance: PathAttribute): void;|api/arkui/PathModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class PatternLockModifier<br>差异内容：export declare class PatternLockModifier|api/arkui/PatternLockModifier.d.ts|
|新增API|NA|类名：PatternLockModifier；<br>API声明：applyNormalAttribute?(instance: PatternLockAttribute): void;<br>差异内容：applyNormalAttribute?(instance: PatternLockAttribute): void;|api/arkui/PatternLockModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class PolygonModifier<br>差异内容：export declare class PolygonModifier|api/arkui/PolygonModifier.d.ts|
|新增API|NA|类名：PolygonModifier；<br>API声明：applyNormalAttribute?(instance: PolygonAttribute): void;<br>差异内容：applyNormalAttribute?(instance: PolygonAttribute): void;|api/arkui/PolygonModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class PolylineModifier<br>差异内容：export declare class PolylineModifier|api/arkui/PolylineModifier.d.ts|
|新增API|NA|类名：PolylineModifier；<br>API声明：applyNormalAttribute?(instance: PolylineAttribute): void;<br>差异内容：applyNormalAttribute?(instance: PolylineAttribute): void;|api/arkui/PolylineModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ProgressModifier<br>差异内容：export declare class ProgressModifier|api/arkui/ProgressModifier.d.ts|
|新增API|NA|类名：ProgressModifier；<br>API声明：applyNormalAttribute?(instance: ProgressAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ProgressAttribute): void;|api/arkui/ProgressModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class QRCodeModifier<br>差异内容：export declare class QRCodeModifier|api/arkui/QRCodeModifier.d.ts|
|新增API|NA|类名：QRCodeModifier；<br>API声明：applyNormalAttribute?(instance: QRCodeAttribute): void;<br>差异内容：applyNormalAttribute?(instance: QRCodeAttribute): void;|api/arkui/QRCodeModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class RadioModifier<br>差异内容：export declare class RadioModifier|api/arkui/RadioModifier.d.ts|
|新增API|NA|类名：RadioModifier；<br>API声明：applyNormalAttribute?(instance: RadioAttribute): void;<br>差异内容：applyNormalAttribute?(instance: RadioAttribute): void;|api/arkui/RadioModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class RatingModifier<br>差异内容：export declare class RatingModifier|api/arkui/RatingModifier.d.ts|
|新增API|NA|类名：RatingModifier；<br>API声明：applyNormalAttribute?(instance: RatingAttribute): void;<br>差异内容：applyNormalAttribute?(instance: RatingAttribute): void;|api/arkui/RatingModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class RectModifier<br>差异内容：export declare class RectModifier|api/arkui/RectModifier.d.ts|
|新增API|NA|类名：RectModifier；<br>API声明：applyNormalAttribute?(instance: RectAttribute): void;<br>差异内容：applyNormalAttribute?(instance: RectAttribute): void;|api/arkui/RectModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class RefreshModifier<br>差异内容：export declare class RefreshModifier|api/arkui/RefreshModifier.d.ts|
|新增API|NA|类名：RefreshModifier；<br>API声明：applyNormalAttribute?(instance: RefreshAttribute): void;<br>差异内容：applyNormalAttribute?(instance: RefreshAttribute): void;|api/arkui/RefreshModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class RichEditorModifier<br>差异内容：export declare class RichEditorModifier|api/arkui/RichEditorModifier.d.ts|
|新增API|NA|类名：RichEditorModifier；<br>API声明：applyNormalAttribute?(instance: RichEditorAttribute): void;<br>差异内容：applyNormalAttribute?(instance: RichEditorAttribute): void;|api/arkui/RichEditorModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class RowModifier<br>差异内容：export declare class RowModifier|api/arkui/RowModifier.d.ts|
|新增API|NA|类名：RowModifier；<br>API声明：applyNormalAttribute?(instance: RowAttribute): void;<br>差异内容：applyNormalAttribute?(instance: RowAttribute): void;|api/arkui/RowModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class RowSplitModifier<br>差异内容：export declare class RowSplitModifier|api/arkui/RowSplitModifier.d.ts|
|新增API|NA|类名：RowSplitModifier；<br>API声明：applyNormalAttribute?(instance: RowSplitAttribute): void;<br>差异内容：applyNormalAttribute?(instance: RowSplitAttribute): void;|api/arkui/RowSplitModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ScrollModifier<br>差异内容：export declare class ScrollModifier|api/arkui/ScrollModifier.d.ts|
|新增API|NA|类名：ScrollModifier；<br>API声明：applyNormalAttribute?(instance: ScrollAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ScrollAttribute): void;|api/arkui/ScrollModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class SearchModifier<br>差异内容：export declare class SearchModifier|api/arkui/SearchModifier.d.ts|
|新增API|NA|类名：SearchModifier；<br>API声明：applyNormalAttribute?(instance: SearchAttribute): void;<br>差异内容：applyNormalAttribute?(instance: SearchAttribute): void;|api/arkui/SearchModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class SelectModifier<br>差异内容：export declare class SelectModifier|api/arkui/SelectModifier.d.ts|
|新增API|NA|类名：SelectModifier；<br>API声明：applyNormalAttribute?(instance: SelectAttribute): void;<br>差异内容：applyNormalAttribute?(instance: SelectAttribute): void;|api/arkui/SelectModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ShapeModifier<br>差异内容：export declare class ShapeModifier|api/arkui/ShapeModifier.d.ts|
|新增API|NA|类名：ShapeModifier；<br>API声明：applyNormalAttribute?(instance: ShapeAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ShapeAttribute): void;|api/arkui/ShapeModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class SideBarContainerModifier<br>差异内容：export declare class SideBarContainerModifier|api/arkui/SideBarContainerModifier.d.ts|
|新增API|NA|类名：SideBarContainerModifier；<br>API声明：applyNormalAttribute?(instance: SideBarContainerAttribute): void;<br>差异内容：applyNormalAttribute?(instance: SideBarContainerAttribute): void;|api/arkui/SideBarContainerModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class SliderModifier<br>差异内容：export declare class SliderModifier|api/arkui/SliderModifier.d.ts|
|新增API|NA|类名：SliderModifier；<br>API声明：applyNormalAttribute?(instance: SliderAttribute): void;<br>差异内容：applyNormalAttribute?(instance: SliderAttribute): void;|api/arkui/SliderModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class SpanModifier<br>差异内容：export declare class SpanModifier|api/arkui/SpanModifier.d.ts|
|新增API|NA|类名：SpanModifier；<br>API声明：applyNormalAttribute?(instance: SpanAttribute): void;<br>差异内容：applyNormalAttribute?(instance: SpanAttribute): void;|api/arkui/SpanModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class StackModifier<br>差异内容：export declare class StackModifier|api/arkui/StackModifier.d.ts|
|新增API|NA|类名：StackModifier；<br>API声明：applyNormalAttribute?(instance: StackAttribute): void;<br>差异内容：applyNormalAttribute?(instance: StackAttribute): void;|api/arkui/StackModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class StepperItemModifier<br>差异内容：export declare class StepperItemModifier|api/arkui/StepperItemModifier.d.ts|
|新增API|NA|类名：StepperItemModifier；<br>API声明：applyNormalAttribute?(instance: StepperItemAttribute): void;<br>差异内容：applyNormalAttribute?(instance: StepperItemAttribute): void;|api/arkui/StepperItemModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class SwiperModifier<br>差异内容：export declare class SwiperModifier|api/arkui/SwiperModifier.d.ts|
|新增API|NA|类名：SwiperModifier；<br>API声明：applyNormalAttribute?(instance: SwiperAttribute): void;<br>差异内容：applyNormalAttribute?(instance: SwiperAttribute): void;|api/arkui/SwiperModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class SymbolGlyphModifier<br>差异内容：export declare class SymbolGlyphModifier|api/arkui/SymbolGlyphModifier.d.ts|
|新增API|NA|类名：SymbolGlyphModifier；<br>API声明：applyNormalAttribute?(instance: SymbolGlyphAttribute): void;<br>差异内容：applyNormalAttribute?(instance: SymbolGlyphAttribute): void;|api/arkui/SymbolGlyphModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class SymbolSpanModifier<br>差异内容：export declare class SymbolSpanModifier|api/arkui/SymbolSpanModifier.d.ts|
|新增API|NA|类名：SymbolSpanModifier；<br>API声明：applyNormalAttribute?(attribute: SymbolSpanAttribute): void;<br>差异内容：applyNormalAttribute?(attribute: SymbolSpanAttribute): void;|api/arkui/SymbolSpanModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class TabsModifier<br>差异内容：export declare class TabsModifier|api/arkui/TabsModifier.d.ts|
|新增API|NA|类名：TabsModifier；<br>API声明：applyNormalAttribute?(instance: TabsAttribute): void;<br>差异内容：applyNormalAttribute?(instance: TabsAttribute): void;|api/arkui/TabsModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class TextAreaModifier<br>差异内容：export declare class TextAreaModifier|api/arkui/TextAreaModifier.d.ts|
|新增API|NA|类名：TextAreaModifier；<br>API声明：applyNormalAttribute?(instance: TextAreaAttribute): void;<br>差异内容：applyNormalAttribute?(instance: TextAreaAttribute): void;|api/arkui/TextAreaModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class TextClockModifier<br>差异内容：export declare class TextClockModifier|api/arkui/TextClockModifier.d.ts|
|新增API|NA|类名：TextClockModifier；<br>API声明：applyNormalAttribute?(instance: TextClockAttribute): void;<br>差异内容：applyNormalAttribute?(instance: TextClockAttribute): void;|api/arkui/TextClockModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class TextInputModifier<br>差异内容：export declare class TextInputModifier|api/arkui/TextInputModifier.d.ts|
|新增API|NA|类名：TextInputModifier；<br>API声明：applyNormalAttribute?(instance: TextInputAttribute): void;<br>差异内容：applyNormalAttribute?(instance: TextInputAttribute): void;|api/arkui/TextInputModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class TextModifier<br>差异内容：export declare class TextModifier|api/arkui/TextModifier.d.ts|
|新增API|NA|类名：TextModifier；<br>API声明：applyNormalAttribute?(instance: TextAttribute): void;<br>差异内容：applyNormalAttribute?(instance: TextAttribute): void;|api/arkui/TextModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class TextPickerModifier<br>差异内容：export declare class TextPickerModifier|api/arkui/TextPickerModifier.d.ts|
|新增API|NA|类名：TextPickerModifier；<br>API声明：applyNormalAttribute?(instance: TextPickerAttribute): void;<br>差异内容：applyNormalAttribute?(instance: TextPickerAttribute): void;|api/arkui/TextPickerModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class TextTimerModifier<br>差异内容：export declare class TextTimerModifier|api/arkui/TextTimerModifier.d.ts|
|新增API|NA|类名：TextTimerModifier；<br>API声明：applyNormalAttribute?(instance: TextTimerAttribute): void;<br>差异内容：applyNormalAttribute?(instance: TextTimerAttribute): void;|api/arkui/TextTimerModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class TimePickerModifier<br>差异内容：export declare class TimePickerModifier|api/arkui/TimePickerModifier.d.ts|
|新增API|NA|类名：TimePickerModifier；<br>API声明：applyNormalAttribute?(instance: TimePickerAttribute): void;<br>差异内容：applyNormalAttribute?(instance: TimePickerAttribute): void;|api/arkui/TimePickerModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class ToggleModifier<br>差异内容：export declare class ToggleModifier|api/arkui/ToggleModifier.d.ts|
|新增API|NA|类名：ToggleModifier；<br>API声明：applyNormalAttribute?(instance: ToggleAttribute): void;<br>差异内容：applyNormalAttribute?(instance: ToggleAttribute): void;|api/arkui/ToggleModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class VideoModifier<br>差异内容：export declare class VideoModifier|api/arkui/VideoModifier.d.ts|
|新增API|NA|类名：VideoModifier；<br>API声明：applyNormalAttribute?(instance: VideoAttribute): void;<br>差异内容：applyNormalAttribute?(instance: VideoAttribute): void;|api/arkui/VideoModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class WaterFlowModifier<br>差异内容：export declare class WaterFlowModifier|api/arkui/WaterFlowModifier.d.ts|
|新增API|NA|类名：WaterFlowModifier；<br>API声明：applyNormalAttribute?(instance: WaterFlowAttribute): void;<br>差异内容：applyNormalAttribute?(instance: WaterFlowAttribute): void;|api/arkui/WaterFlowModifier.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type Scene = import('../api/@ohos.graphics.scene').Scene;<br>差异内容：declare type Scene = import('../api/@ohos.graphics.scene').Scene;|component/component3d.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ModelType<br>差异内容：declare enum ModelType|component/component3d.d.ts|
|新增API|NA|类名：ModelType；<br>API声明：TEXTURE = 0<br>差异内容：TEXTURE = 0|component/component3d.d.ts|
|新增API|NA|类名：ModelType；<br>API声明：SURFACE = 1<br>差异内容：SURFACE = 1|component/component3d.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SceneOptions<br>差异内容：declare interface SceneOptions|component/component3d.d.ts|
|新增API|NA|类名：SceneOptions；<br>API声明：scene?: ResourceStr \| Scene;<br>差异内容：scene?: ResourceStr \| Scene;|component/component3d.d.ts|
|新增API|NA|类名：SceneOptions；<br>API声明：modelType?: ModelType;<br>差异内容：modelType?: ModelType;|component/component3d.d.ts|
|新增API|NA|类名：global；<br>API声明：interface Component3DInterface<br>差异内容：interface Component3DInterface|component/component3d.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class Component3DAttribute<br>差异内容：declare class Component3DAttribute|component/component3d.d.ts|
|新增API|NA|类名：Component3DAttribute；<br>API声明：environment(uri: ResourceStr): Component3DAttribute;<br>差异内容：environment(uri: ResourceStr): Component3DAttribute;|component/component3d.d.ts|
|新增API|NA|类名：Component3DAttribute；<br>API声明：customRender(uri: ResourceStr, selfRenderUpdate: boolean): Component3DAttribute;<br>差异内容：customRender(uri: ResourceStr, selfRenderUpdate: boolean): Component3DAttribute;|component/component3d.d.ts|
|新增API|NA|类名：Component3DAttribute；<br>API声明：shader(uri: ResourceStr): Component3DAttribute;<br>差异内容：shader(uri: ResourceStr): Component3DAttribute;|component/component3d.d.ts|
|新增API|NA|类名：Component3DAttribute；<br>API声明：shaderImageTexture(uri: ResourceStr): Component3DAttribute;<br>差异内容：shaderImageTexture(uri: ResourceStr): Component3DAttribute;|component/component3d.d.ts|
|新增API|NA|类名：Component3DAttribute；<br>API声明：shaderInputBuffer(buffer: Array\<number>): Component3DAttribute;<br>差异内容：shaderInputBuffer(buffer: Array\<number>): Component3DAttribute;|component/component3d.d.ts|
|新增API|NA|类名：Component3DAttribute；<br>API声明：renderWidth(value: Dimension): Component3DAttribute;<br>差异内容：renderWidth(value: Dimension): Component3DAttribute;|component/component3d.d.ts|
|新增API|NA|类名：Component3DAttribute；<br>API声明：renderHeight(value: Dimension): Component3DAttribute;<br>差异内容：renderHeight(value: Dimension): Component3DAttribute;|component/component3d.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Component3D: Component3DInterface;<br>差异内容：declare const Component3D: Component3DInterface;|component/component3d.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Component3DInstance: Component3DAttribute;<br>差异内容：declare const Component3DInstance: Component3DAttribute;|component/component3d.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type Content = import('../api/@ohos.arkui.node').Content;<br>差异内容：declare type Content = import('../api/@ohos.arkui.node').Content;|component/content_slot.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ContentSlotAttribute<br>差异内容：declare class ContentSlotAttribute|component/content_slot.d.ts|
|新增API|NA|类名：global；<br>API声明：interface ContentSlotInterface<br>差异内容：interface ContentSlotInterface|component/content_slot.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const ContentSlot: ContentSlotInterface;<br>差异内容：declare const ContentSlot: ContentSlotInterface;|component/content_slot.d.ts|
|新增API|NA|类名：global；<br>API声明：interface EmbeddedComponentInterface<br>差异内容：interface EmbeddedComponentInterface|component/embedded_component.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TerminationInfo<br>差异内容：declare interface TerminationInfo|component/embedded_component.d.ts|
|新增API|NA|类名：TerminationInfo；<br>API声明：code: number;<br>差异内容：code: number;|component/embedded_component.d.ts|
|新增API|NA|类名：TerminationInfo；<br>API声明：want?: import('../api/@ohos.app.ability.Want').default;<br>差异内容：want?: import('../api/@ohos.app.ability.Want').default;|component/embedded_component.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class EmbeddedComponentAttribute<br>差异内容：declare class EmbeddedComponentAttribute|component/embedded_component.d.ts|
|新增API|NA|类名：EmbeddedComponentAttribute；<br>API声明：onTerminated(callback: import('../api/@ohos.base').Callback\<TerminationInfo>): EmbeddedComponentAttribute;<br>差异内容：onTerminated(callback: import('../api/@ohos.base').Callback\<TerminationInfo>): EmbeddedComponentAttribute;|component/embedded_component.d.ts|
|新增API|NA|类名：EmbeddedComponentAttribute；<br>API声明：onError(callback: import('../api/@ohos.base').ErrorCallback): EmbeddedComponentAttribute;<br>差异内容：onError(callback: import('../api/@ohos.base').ErrorCallback): EmbeddedComponentAttribute;|component/embedded_component.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const EmbeddedComponent: EmbeddedComponentInterface;<br>差异内容：declare const EmbeddedComponent: EmbeddedComponentInterface;|component/embedded_component.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const EmbeddedComponentInstance: EmbeddedComponentAttribute;<br>差异内容：declare const EmbeddedComponentInstance: EmbeddedComponentAttribute;|component/embedded_component.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface FocusBoxStyle<br>差异内容：declare interface FocusBoxStyle|component/focus.d.ts|
|新增API|NA|类名：FocusBoxStyle；<br>API声明：margin?: LengthMetrics;<br>差异内容：margin?: LengthMetrics;|component/focus.d.ts|
|新增API|NA|类名：FocusBoxStyle；<br>API声明：strokeColor?: ColorMetrics;<br>差异内容：strokeColor?: ColorMetrics;|component/focus.d.ts|
|新增API|NA|类名：FocusBoxStyle；<br>API声明：strokeWidth?: LengthMetrics;<br>差异内容：strokeWidth?: LengthMetrics;|component/focus.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum FocusPriority<br>差异内容：declare enum FocusPriority|component/focus.d.ts|
|新增API|NA|类名：FocusPriority；<br>API声明：AUTO = 0<br>差异内容：AUTO = 0|component/focus.d.ts|
|新增API|NA|类名：FocusPriority；<br>API声明：PRIOR = 2000<br>差异内容：PRIOR = 2000|component/focus.d.ts|
|新增API|NA|类名：FocusPriority；<br>API声明：PREVIOUS = 3000<br>差异内容：PREVIOUS = 3000|component/focus.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum ImageAnalyzerType<br>差异内容：declare enum ImageAnalyzerType|component/image_common.d.ts|
|新增API|NA|类名：ImageAnalyzerType；<br>API声明：SUBJECT = 0<br>差异内容：SUBJECT = 0|component/image_common.d.ts|
|新增API|NA|类名：ImageAnalyzerType；<br>API声明：TEXT<br>差异内容：TEXT|component/image_common.d.ts|
|新增API|NA|类名：ImageAnalyzerType；<br>API声明：OBJECT_LOOKUP<br>差异内容：OBJECT_LOOKUP|component/image_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ImageAnalyzerController<br>差异内容：declare class ImageAnalyzerController|component/image_common.d.ts|
|新增API|NA|类名：ImageAnalyzerController；<br>API声明：getImageAnalyzerSupportTypes(): ImageAnalyzerType[];<br>差异内容：getImageAnalyzerSupportTypes(): ImageAnalyzerType[];|component/image_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ImageAnalyzerConfig<br>差异内容：declare interface ImageAnalyzerConfig|component/image_common.d.ts|
|新增API|NA|类名：ImageAnalyzerConfig；<br>API声明：types: ImageAnalyzerType[];<br>差异内容：types: ImageAnalyzerType[];|component/image_common.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ImageAIOptions<br>差异内容：declare interface ImageAIOptions|component/image_common.d.ts|
|新增API|NA|类名：ImageAIOptions；<br>API声明：types?: ImageAnalyzerType[];<br>差异内容：types?: ImageAnalyzerType[];|component/image_common.d.ts|
|新增API|NA|类名：ImageAIOptions；<br>API声明：aiController?: ImageAnalyzerController;<br>差异内容：aiController?: ImageAnalyzerController;|component/image_common.d.ts|
|新增API|NA|类名：global；<br>API声明：interface RepeatItem<br>差异内容：interface RepeatItem|component/repeat.d.ts|
|新增API|NA|类名：RepeatItem；<br>API声明：item: T;<br>差异内容：item: T;|component/repeat.d.ts|
|新增API|NA|类名：RepeatItem；<br>API声明：index: number;<br>差异内容：index: number;|component/repeat.d.ts|
|新增API|NA|类名：global；<br>API声明：interface VirtualScrollOptions<br>差异内容：interface VirtualScrollOptions|component/repeat.d.ts|
|新增API|NA|类名：VirtualScrollOptions；<br>API声明：totalCount?: number;<br>差异内容：totalCount?: number;|component/repeat.d.ts|
|新增API|NA|类名：global；<br>API声明：interface TemplateOptions<br>差异内容：interface TemplateOptions|component/repeat.d.ts|
|新增API|NA|类名：TemplateOptions；<br>API声明：cachedCount?: number;<br>差异内容：cachedCount?: number;|component/repeat.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type TemplateTypedFunc\<T> = (item: T, index: number) => string;<br>差异内容：declare type TemplateTypedFunc\<T> = (item: T, index: number) => string;|component/repeat.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type RepeatItemBuilder\<T> = (repeatItem: RepeatItem\<T>) => void;<br>差异内容：declare type RepeatItemBuilder\<T> = (repeatItem: RepeatItem\<T>) => void;|component/repeat.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class RepeatAttribute<br>差异内容：declare class RepeatAttribute|component/repeat.d.ts|
|新增API|NA|类名：RepeatAttribute；<br>API声明：each(itemGenerator: (repeatItem: RepeatItem\<T>) => void): RepeatAttribute\<T>;<br>差异内容：each(itemGenerator: (repeatItem: RepeatItem\<T>) => void): RepeatAttribute\<T>;|component/repeat.d.ts|
|新增API|NA|类名：RepeatAttribute；<br>API声明：key(keyGenerator: (item: T, index: number) => string): RepeatAttribute\<T>;<br>差异内容：key(keyGenerator: (item: T, index: number) => string): RepeatAttribute\<T>;|component/repeat.d.ts|
|新增API|NA|类名：RepeatAttribute；<br>API声明：virtualScroll(virtualScrollOptions?: VirtualScrollOptions): RepeatAttribute\<T>;<br>差异内容：virtualScroll(virtualScrollOptions?: VirtualScrollOptions): RepeatAttribute\<T>;|component/repeat.d.ts|
|新增API|NA|类名：RepeatAttribute；<br>API声明：template(type: string, itemBuilder: RepeatItemBuilder\<T>, templateOptions?: TemplateOptions): RepeatAttribute\<T>;<br>差异内容：template(type: string, itemBuilder: RepeatItemBuilder\<T>, templateOptions?: TemplateOptions): RepeatAttribute\<T>;|component/repeat.d.ts|
|新增API|NA|类名：RepeatAttribute；<br>API声明：templateId(typedFunc: TemplateTypedFunc\<T>): RepeatAttribute\<T>;<br>差异内容：templateId(typedFunc: TemplateTypedFunc\<T>): RepeatAttribute\<T>;|component/repeat.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const Repeat: \<T>(arr: Array\<T>) => RepeatAttribute\<T>;<br>差异内容：declare const Repeat: \<T>(arr: Array\<T>) => RepeatAttribute\<T>;|component/repeat.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class StyledString<br>差异内容：declare class StyledString|component/styled_string.d.ts|
|新增API|NA|类名：StyledString；<br>API声明：readonly length: number;<br>差异内容：readonly length: number;|component/styled_string.d.ts|
|新增API|NA|类名：StyledString；<br>API声明：getString(): string;<br>差异内容：getString(): string;|component/styled_string.d.ts|
|新增API|NA|类名：StyledString；<br>API声明：getStyles(start: number, length: number, styledKey?: StyledStringKey): Array\<SpanStyle>;<br>差异内容：getStyles(start: number, length: number, styledKey?: StyledStringKey): Array\<SpanStyle>;|component/styled_string.d.ts|
|新增API|NA|类名：StyledString；<br>API声明：equals(other: StyledString): boolean;<br>差异内容：equals(other: StyledString): boolean;|component/styled_string.d.ts|
|新增API|NA|类名：StyledString；<br>API声明：subStyledString(start: number, length?: number): StyledString;<br>差异内容：subStyledString(start: number, length?: number): StyledString;|component/styled_string.d.ts|
|新增API|NA|类名：StyledString；<br>API声明：static fromHtml(html: string): Promise\<StyledString>;<br>差异内容：static fromHtml(html: string): Promise\<StyledString>;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface StyleOptions<br>差异内容：declare interface StyleOptions|component/styled_string.d.ts|
|新增API|NA|类名：StyleOptions；<br>API声明：start?: number;<br>差异内容：start?: number;|component/styled_string.d.ts|
|新增API|NA|类名：StyleOptions；<br>API声明：length?: number;<br>差异内容：length?: number;|component/styled_string.d.ts|
|新增API|NA|类名：StyleOptions；<br>API声明：styledKey: StyledStringKey;<br>差异内容：styledKey: StyledStringKey;|component/styled_string.d.ts|
|新增API|NA|类名：StyleOptions；<br>API声明：styledValue: StyledStringValue;<br>差异内容：styledValue: StyledStringValue;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SpanStyle<br>差异内容：declare interface SpanStyle|component/styled_string.d.ts|
|新增API|NA|类名：SpanStyle；<br>API声明：start: number;<br>差异内容：start: number;|component/styled_string.d.ts|
|新增API|NA|类名：SpanStyle；<br>API声明：length: number;<br>差异内容：length: number;|component/styled_string.d.ts|
|新增API|NA|类名：SpanStyle；<br>API声明：styledKey: StyledStringKey;<br>差异内容：styledKey: StyledStringKey;|component/styled_string.d.ts|
|新增API|NA|类名：SpanStyle；<br>API声明：styledValue: StyledStringValue;<br>差异内容：styledValue: StyledStringValue;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class TextStyle<br>差异内容：declare class TextStyle|component/styled_string.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：readonly fontColor?: ResourceColor;<br>差异内容：readonly fontColor?: ResourceColor;|component/styled_string.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：readonly fontFamily?: string;<br>差异内容：readonly fontFamily?: string;|component/styled_string.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：readonly fontSize?: number;<br>差异内容：readonly fontSize?: number;|component/styled_string.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：readonly fontWeight?: number;<br>差异内容：readonly fontWeight?: number;|component/styled_string.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：readonly fontStyle?: FontStyle;<br>差异内容：readonly fontStyle?: FontStyle;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TextStyleInterface<br>差异内容：declare interface TextStyleInterface|component/styled_string.d.ts|
|新增API|NA|类名：TextStyleInterface；<br>API声明：fontColor?: ResourceColor;<br>差异内容：fontColor?: ResourceColor;|component/styled_string.d.ts|
|新增API|NA|类名：TextStyleInterface；<br>API声明：fontFamily?: ResourceStr;<br>差异内容：fontFamily?: ResourceStr;|component/styled_string.d.ts|
|新增API|NA|类名：TextStyleInterface；<br>API声明：fontSize?: LengthMetrics;<br>差异内容：fontSize?: LengthMetrics;|component/styled_string.d.ts|
|新增API|NA|类名：TextStyleInterface；<br>API声明：fontWeight?: number \| FontWeight \| string;<br>差异内容：fontWeight?: number \| FontWeight \| string;|component/styled_string.d.ts|
|新增API|NA|类名：TextStyleInterface；<br>API声明：fontStyle?: FontStyle;<br>差异内容：fontStyle?: FontStyle;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class DecorationStyle<br>差异内容：declare class DecorationStyle|component/styled_string.d.ts|
|新增API|NA|类名：DecorationStyle；<br>API声明：readonly type: TextDecorationType;<br>差异内容：readonly type: TextDecorationType;|component/styled_string.d.ts|
|新增API|NA|类名：DecorationStyle；<br>API声明：readonly color?: ResourceColor;<br>差异内容：readonly color?: ResourceColor;|component/styled_string.d.ts|
|新增API|NA|类名：DecorationStyle；<br>API声明：readonly style?: TextDecorationStyle;<br>差异内容：readonly style?: TextDecorationStyle;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DecorationStyleInterface<br>差异内容：declare interface DecorationStyleInterface|component/styled_string.d.ts|
|新增API|NA|类名：DecorationStyleInterface；<br>API声明：type: TextDecorationType;<br>差异内容：type: TextDecorationType;|component/styled_string.d.ts|
|新增API|NA|类名：DecorationStyleInterface；<br>API声明：color?: ResourceColor;<br>差异内容：color?: ResourceColor;|component/styled_string.d.ts|
|新增API|NA|类名：DecorationStyleInterface；<br>API声明：style?: TextDecorationStyle;<br>差异内容：style?: TextDecorationStyle;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class BaselineOffsetStyle<br>差异内容：declare class BaselineOffsetStyle|component/styled_string.d.ts|
|新增API|NA|类名：BaselineOffsetStyle；<br>API声明：readonly baselineOffset: number;<br>差异内容：readonly baselineOffset: number;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class LetterSpacingStyle<br>差异内容：declare class LetterSpacingStyle|component/styled_string.d.ts|
|新增API|NA|类名：LetterSpacingStyle；<br>API声明：readonly letterSpacing: number;<br>差异内容：readonly letterSpacing: number;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class TextShadowStyle<br>差异内容：declare class TextShadowStyle|component/styled_string.d.ts|
|新增API|NA|类名：TextShadowStyle；<br>API声明：readonly textShadow: Array\<ShadowOptions>;<br>差异内容：readonly textShadow: Array\<ShadowOptions>;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class GestureStyle<br>差异内容：declare class GestureStyle|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface GestureStyleInterface<br>差异内容：declare interface GestureStyleInterface|component/styled_string.d.ts|
|新增API|NA|类名：GestureStyleInterface；<br>API声明：onClick?: Callback\<ClickEvent>;<br>差异内容：onClick?: Callback\<ClickEvent>;|component/styled_string.d.ts|
|新增API|NA|类名：GestureStyleInterface；<br>API声明：onLongPress?: Callback\<GestureEvent>;<br>差异内容：onLongPress?: Callback\<GestureEvent>;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ParagraphStyle<br>差异内容：declare class ParagraphStyle|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：readonly textAlign?: TextAlign;<br>差异内容：readonly textAlign?: TextAlign;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：readonly textIndent?: number;<br>差异内容：readonly textIndent?: number;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：readonly maxLines?: number;<br>差异内容：readonly maxLines?: number;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：readonly overflow?: TextOverflow;<br>差异内容：readonly overflow?: TextOverflow;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：readonly wordBreak?: WordBreak;<br>差异内容：readonly wordBreak?: WordBreak;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：readonly leadingMargin?: number \| LeadingMarginPlaceholder;<br>差异内容：readonly leadingMargin?: number \| LeadingMarginPlaceholder;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ParagraphStyleInterface<br>差异内容：declare interface ParagraphStyleInterface|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyleInterface；<br>API声明：textAlign?: TextAlign;<br>差异内容：textAlign?: TextAlign;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyleInterface；<br>API声明：textIndent?: LengthMetrics;<br>差异内容：textIndent?: LengthMetrics;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyleInterface；<br>API声明：maxLines?: number;<br>差异内容：maxLines?: number;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyleInterface；<br>API声明：overflow?: TextOverflow;<br>差异内容：overflow?: TextOverflow;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyleInterface；<br>API声明：wordBreak?: WordBreak;<br>差异内容：wordBreak?: WordBreak;|component/styled_string.d.ts|
|新增API|NA|类名：ParagraphStyleInterface；<br>API声明：leadingMargin?: LengthMetrics \| LeadingMarginPlaceholder;<br>差异内容：leadingMargin?: LengthMetrics \| LeadingMarginPlaceholder;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class LineHeightStyle<br>差异内容：declare class LineHeightStyle|component/styled_string.d.ts|
|新增API|NA|类名：LineHeightStyle；<br>API声明：readonly lineHeight: number;<br>差异内容：readonly lineHeight: number;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type StyledStringValue = TextStyle \| DecorationStyle \| BaselineOffsetStyle \| LetterSpacingStyle \| TextShadowStyle \| GestureStyle \| ImageAttachment \| ParagraphStyle \| LineHeightStyle \| CustomSpan \| UserDataSpan;<br>差异内容：declare type StyledStringValue = TextStyle \| DecorationStyle \| BaselineOffsetStyle \| LetterSpacingStyle \| TextShadowStyle \| GestureStyle \| ImageAttachment \| ParagraphStyle \| LineHeightStyle \| CustomSpan \| UserDataSpan;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class MutableStyledString<br>差异内容：declare class MutableStyledString|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：replaceString(start: number, length: number, other: string): void;<br>差异内容：replaceString(start: number, length: number, other: string): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：insertString(start: number, other: string): void;<br>差异内容：insertString(start: number, other: string): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：removeString(start: number, length: number): void;<br>差异内容：removeString(start: number, length: number): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：replaceStyle(spanStyle: SpanStyle): void;<br>差异内容：replaceStyle(spanStyle: SpanStyle): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：setStyle(spanStyle: SpanStyle): void;<br>差异内容：setStyle(spanStyle: SpanStyle): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：removeStyle(start: number, length: number, styledKey: StyledStringKey): void;<br>差异内容：removeStyle(start: number, length: number, styledKey: StyledStringKey): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：removeStyles(start: number, length: number): void;<br>差异内容：removeStyles(start: number, length: number): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：clearStyles(): void;<br>差异内容：clearStyles(): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：replaceStyledString(start: number, length: number, other: StyledString): void;<br>差异内容：replaceStyledString(start: number, length: number, other: StyledString): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：insertStyledString(start: number, other: StyledString): void;<br>差异内容：insertStyledString(start: number, other: StyledString): void;|component/styled_string.d.ts|
|新增API|NA|类名：MutableStyledString；<br>API声明：appendStyledString(other: StyledString): void;<br>差异内容：appendStyledString(other: StyledString): void;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum StyledStringKey<br>差异内容：declare enum StyledStringKey|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：FONT = 0<br>差异内容：FONT = 0|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：DECORATION = 1<br>差异内容：DECORATION = 1|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：BASELINE_OFFSET = 2<br>差异内容：BASELINE_OFFSET = 2|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：LETTER_SPACING = 3<br>差异内容：LETTER_SPACING = 3|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：TEXT_SHADOW = 4<br>差异内容：TEXT_SHADOW = 4|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：LINE_HEIGHT = 5<br>差异内容：LINE_HEIGHT = 5|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：GESTURE = 100<br>差异内容：GESTURE = 100|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：PARAGRAPH_STYLE = 200<br>差异内容：PARAGRAPH_STYLE = 200|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：IMAGE = 300<br>差异内容：IMAGE = 300|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：CUSTOM_SPAN = 400<br>差异内容：CUSTOM_SPAN = 400|component/styled_string.d.ts|
|新增API|NA|类名：StyledStringKey；<br>API声明：USER_DATA = 500<br>差异内容：USER_DATA = 500|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class ImageAttachment<br>差异内容：declare class ImageAttachment|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachment；<br>API声明：readonly value: PixelMap;<br>差异内容：readonly value: PixelMap;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachment；<br>API声明：readonly size?: SizeOptions;<br>差异内容：readonly size?: SizeOptions;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachment；<br>API声明：readonly verticalAlign?: ImageSpanAlignment;<br>差异内容：readonly verticalAlign?: ImageSpanAlignment;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachment；<br>API声明：readonly objectFit?: ImageFit;<br>差异内容：readonly objectFit?: ImageFit;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachment；<br>API声明：readonly layoutStyle?: ImageAttachmentLayoutStyle;<br>差异内容：readonly layoutStyle?: ImageAttachmentLayoutStyle;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ImageAttachmentInterface<br>差异内容：declare interface ImageAttachmentInterface|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachmentInterface；<br>API声明：value: PixelMap;<br>差异内容：value: PixelMap;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachmentInterface；<br>API声明：size?: SizeOptions;<br>差异内容：size?: SizeOptions;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachmentInterface；<br>API声明：verticalAlign?: ImageSpanAlignment;<br>差异内容：verticalAlign?: ImageSpanAlignment;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachmentInterface；<br>API声明：objectFit?: ImageFit;<br>差异内容：objectFit?: ImageFit;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachmentInterface；<br>API声明：layoutStyle?: ImageAttachmentLayoutStyle;<br>差异内容：layoutStyle?: ImageAttachmentLayoutStyle;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface ImageAttachmentLayoutStyle<br>差异内容：declare interface ImageAttachmentLayoutStyle|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachmentLayoutStyle；<br>API声明：margin?: LengthMetrics \| Margin;<br>差异内容：margin?: LengthMetrics \| Margin;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachmentLayoutStyle；<br>API声明：padding?: LengthMetrics \| Padding;<br>差异内容：padding?: LengthMetrics \| Padding;|component/styled_string.d.ts|
|新增API|NA|类名：ImageAttachmentLayoutStyle；<br>API声明：borderRadius?: LengthMetrics \| BorderRadiuses;<br>差异内容：borderRadius?: LengthMetrics \| BorderRadiuses;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface CustomSpanMetrics<br>差异内容：declare interface CustomSpanMetrics|component/styled_string.d.ts|
|新增API|NA|类名：CustomSpanMetrics；<br>API声明：width: number;<br>差异内容：width: number;|component/styled_string.d.ts|
|新增API|NA|类名：CustomSpanMetrics；<br>API声明：height?: number;<br>差异内容：height?: number;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface CustomSpanDrawInfo<br>差异内容：declare interface CustomSpanDrawInfo|component/styled_string.d.ts|
|新增API|NA|类名：CustomSpanDrawInfo；<br>API声明：x: number;<br>差异内容：x: number;|component/styled_string.d.ts|
|新增API|NA|类名：CustomSpanDrawInfo；<br>API声明：lineTop: number;<br>差异内容：lineTop: number;|component/styled_string.d.ts|
|新增API|NA|类名：CustomSpanDrawInfo；<br>API声明：lineBottom: number;<br>差异内容：lineBottom: number;|component/styled_string.d.ts|
|新增API|NA|类名：CustomSpanDrawInfo；<br>API声明：baseline: number;<br>差异内容：baseline: number;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface CustomSpanMeasureInfo<br>差异内容：declare interface CustomSpanMeasureInfo|component/styled_string.d.ts|
|新增API|NA|类名：CustomSpanMeasureInfo；<br>API声明：fontSize: number;<br>差异内容：fontSize: number;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare abstract class CustomSpan<br>差异内容：declare abstract class CustomSpan|component/styled_string.d.ts|
|新增API|NA|类名：CustomSpan；<br>API声明：abstract onMeasure(measureInfo: CustomSpanMeasureInfo): CustomSpanMetrics;<br>差异内容：abstract onMeasure(measureInfo: CustomSpanMeasureInfo): CustomSpanMetrics;|component/styled_string.d.ts|
|新增API|NA|类名：CustomSpan；<br>API声明：abstract onDraw(context: DrawContext, drawInfo: CustomSpanDrawInfo): void;<br>差异内容：abstract onDraw(context: DrawContext, drawInfo: CustomSpanDrawInfo): void;|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare abstract class UserDataSpan<br>差异内容：declare abstract class UserDataSpan|component/styled_string.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type CustomTheme = import('../api/@ohos.arkui.theme').CustomTheme;<br>差异内容：declare type CustomTheme = import('../api/@ohos.arkui.theme').CustomTheme;|component/with_theme.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface WithThemeOptions<br>差异内容：declare interface WithThemeOptions|component/with_theme.d.ts|
|新增API|NA|类名：WithThemeOptions；<br>API声明：theme?: CustomTheme;<br>差异内容：theme?: CustomTheme;|component/with_theme.d.ts|
|新增API|NA|类名：WithThemeOptions；<br>API声明：colorMode?: ThemeColorMode;<br>差异内容：colorMode?: ThemeColorMode;|component/with_theme.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type WithThemeInterface = (options: WithThemeOptions) => WithThemeAttribute;<br>差异内容：declare type WithThemeInterface = (options: WithThemeOptions) => WithThemeAttribute;|component/with_theme.d.ts|
|新增API|NA|类名：global；<br>API声明：declare class WithThemeAttribute<br>差异内容：declare class WithThemeAttribute|component/with_theme.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const WithTheme: WithThemeInterface;<br>差异内容：declare const WithTheme: WithThemeInterface;|component/with_theme.d.ts|
|新增API|NA|类名：global；<br>API声明：declare const WithThemeInstance: WithThemeAttribute;<br>差异内容：declare const WithThemeInstance: WithThemeAttribute;|component/with_theme.d.ts|
|新增API|NA|类名：IconCommonOptions；<br>API声明：activatedFillColor?: ResourceColor;<br>差异内容：activatedFillColor?: ResourceColor;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface ChipSymbolGlyphOptions<br>差异内容：export interface ChipSymbolGlyphOptions|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipSymbolGlyphOptions；<br>API声明：normal?: SymbolGlyphModifier;<br>差异内容：normal?: SymbolGlyphModifier;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipSymbolGlyphOptions；<br>API声明：activated?: SymbolGlyphModifier;<br>差异内容：activated?: SymbolGlyphModifier;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：global；<br>API声明：export interface LocalizedLabelMarginOptions<br>差异内容：export interface LocalizedLabelMarginOptions|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：LocalizedLabelMarginOptions；<br>API声明：start?: LengthMetrics;<br>差异内容：start?: LengthMetrics;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：LocalizedLabelMarginOptions；<br>API声明：end?: LengthMetrics;<br>差异内容：end?: LengthMetrics;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：LabelOptions；<br>API声明：activatedFontColor?: ResourceColor;<br>差异内容：activatedFontColor?: ResourceColor;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：LabelOptions；<br>API声明：localizedLabelMargin?: LocalizedLabelMarginOptions;<br>差异内容：localizedLabelMargin?: LocalizedLabelMarginOptions;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：prefixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：prefixSymbol?: ChipSymbolGlyphOptions;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：suffixSymbol?: ChipSymbolGlyphOptions;<br>差异内容：suffixSymbol?: ChipSymbolGlyphOptions;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：activated?: boolean;<br>差异内容：activated?: boolean;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：activatedBackgroundColor?: ResourceColor;<br>差异内容：activatedBackgroundColor?: ResourceColor;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：onClicked?: Callback\<void>;<br>差异内容：onClicked?: Callback\<void>;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：ChipOptions；<br>API声明：direction?: Direction;<br>差异内容：direction?: Direction;|api/@ohos.arkui.advanced.Chip.d.ets|
|新增API|NA|类名：Router；<br>API声明：back(index: number, params?: Object): void;<br>差异内容：back(index: number, params?: Object): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：Router；<br>API声明：getStateByIndex(index: number): router.RouterState \| undefined;<br>差异内容：getStateByIndex(index: number): router.RouterState \| undefined;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：Router；<br>API声明：getStateByUrl(url: string): Array\<router.RouterState>;<br>差异内容：getStateByUrl(url: string): Array\<router.RouterState>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：PromptAction；<br>API声明：openCustomDialog\<T extends Object>(dialogContent: ComponentContent\<T>, options?: promptAction.BaseDialogOptions): Promise\<void>;<br>差异内容：openCustomDialog\<T extends Object>(dialogContent: ComponentContent\<T>, options?: promptAction.BaseDialogOptions): Promise\<void>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：PromptAction；<br>API声明：openCustomDialog(options: promptAction.CustomDialogOptions): Promise\<number>;<br>差异内容：openCustomDialog(options: promptAction.CustomDialogOptions): Promise\<number>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：PromptAction；<br>API声明：updateCustomDialog\<T extends Object>(dialogContent: ComponentContent\<T>, options: promptAction.BaseDialogOptions): Promise\<void>;<br>差异内容：updateCustomDialog\<T extends Object>(dialogContent: ComponentContent\<T>, options: promptAction.BaseDialogOptions): Promise\<void>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：PromptAction；<br>API声明：closeCustomDialog\<T extends Object>(dialogContent: ComponentContent\<T>): Promise\<void>;<br>差异内容：closeCustomDialog\<T extends Object>(dialogContent: ComponentContent\<T>): Promise\<void>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：PromptAction；<br>API声明：closeCustomDialog(dialogId: number): void;<br>差异内容：closeCustomDialog(dialogId: number): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type ClickEventListenerCallback = (event: ClickEvent, node?: FrameNode) => void;<br>差异内容：declare type ClickEventListenerCallback = (event: ClickEvent, node?: FrameNode) => void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：declare type GestureEventListenerCallback = (event: GestureEvent, node?: FrameNode) => void;<br>差异内容：declare type GestureEventListenerCallback = (event: GestureEvent, node?: FrameNode) => void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface PageInfo<br>差异内容：export interface PageInfo|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：PageInfo；<br>API声明：routerPageInfo?: observer.RouterPageInfo;<br>差异内容：routerPageInfo?: observer.RouterPageInfo;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：PageInfo；<br>API声明：navDestinationInfo?: observer.NavDestinationInfo;<br>差异内容：navDestinationInfo?: observer.NavDestinationInfo;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'scrollEvent', options: observer.ObserverOptions, callback: Callback\<observer.ScrollEventInfo>): void;<br>差异内容：on(type: 'scrollEvent', options: observer.ObserverOptions, callback: Callback\<observer.ScrollEventInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'scrollEvent', callback: Callback\<observer.ScrollEventInfo>): void;<br>差异内容：on(type: 'scrollEvent', callback: Callback\<observer.ScrollEventInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'scrollEvent', options: observer.ObserverOptions, callback?: Callback\<observer.ScrollEventInfo>): void;<br>差异内容：off(type: 'scrollEvent', options: observer.ObserverOptions, callback?: Callback\<observer.ScrollEventInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'scrollEvent', callback?: Callback\<observer.ScrollEventInfo>): void;<br>差异内容：off(type: 'scrollEvent', callback?: Callback\<observer.ScrollEventInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'densityUpdate', callback: Callback\<observer.DensityInfo>): void;<br>差异内容：on(type: 'densityUpdate', callback: Callback\<observer.DensityInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'densityUpdate', callback?: Callback\<observer.DensityInfo>): void;<br>差异内容：off(type: 'densityUpdate', callback?: Callback\<observer.DensityInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'willDraw', callback: Callback\<void>): void;<br>差异内容：on(type: 'willDraw', callback: Callback\<void>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'willDraw', callback?: Callback\<void>): void;<br>差异内容：off(type: 'willDraw', callback?: Callback\<void>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'didLayout', callback: Callback\<void>): void;<br>差异内容：on(type: 'didLayout', callback: Callback\<void>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'didLayout', callback?: Callback\<void>): void;<br>差异内容：off(type: 'didLayout', callback?: Callback\<void>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'navDestinationSwitch', callback: Callback\<observer.NavDestinationSwitchInfo>): void;<br>差异内容：on(type: 'navDestinationSwitch', callback: Callback\<observer.NavDestinationSwitchInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'navDestinationSwitch', observerOptions: observer.NavDestinationSwitchObserverOptions, callback: Callback\<observer.NavDestinationSwitchInfo>): void;<br>差异内容：on(type: 'navDestinationSwitch', observerOptions: observer.NavDestinationSwitchObserverOptions, callback: Callback\<observer.NavDestinationSwitchInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'navDestinationSwitch', callback?: Callback\<observer.NavDestinationSwitchInfo>): void;<br>差异内容：off(type: 'navDestinationSwitch', callback?: Callback\<observer.NavDestinationSwitchInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'navDestinationSwitch', observerOptions: observer.NavDestinationSwitchObserverOptions, callback?: Callback\<observer.NavDestinationSwitchInfo>): void;<br>差异内容：off(type: 'navDestinationSwitch', observerOptions: observer.NavDestinationSwitchObserverOptions, callback?: Callback\<observer.NavDestinationSwitchInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'willClick', callback: ClickEventListenerCallback): void;<br>差异内容：on(type: 'willClick', callback: ClickEventListenerCallback): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'willClick', callback: GestureEventListenerCallback): void;<br>差异内容：on(type: 'willClick', callback: GestureEventListenerCallback): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'willClick', callback?: ClickEventListenerCallback): void;<br>差异内容：off(type: 'willClick', callback?: ClickEventListenerCallback): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'willClick', callback?: GestureEventListenerCallback): void;<br>差异内容：off(type: 'willClick', callback?: GestureEventListenerCallback): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'didClick', callback: ClickEventListenerCallback): void;<br>差异内容：on(type: 'didClick', callback: ClickEventListenerCallback): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'didClick', callback: GestureEventListenerCallback): void;<br>差异内容：on(type: 'didClick', callback: GestureEventListenerCallback): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'didClick', callback?: ClickEventListenerCallback): void;<br>差异内容：off(type: 'didClick', callback?: ClickEventListenerCallback): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'didClick', callback?: GestureEventListenerCallback): void;<br>差异内容：off(type: 'didClick', callback?: GestureEventListenerCallback): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'tabContentUpdate', options: observer.ObserverOptions, callback: Callback\<observer.TabContentInfo>): void;<br>差异内容：on(type: 'tabContentUpdate', options: observer.ObserverOptions, callback: Callback\<observer.TabContentInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：on(type: 'tabContentUpdate', callback: Callback\<observer.TabContentInfo>): void;<br>差异内容：on(type: 'tabContentUpdate', callback: Callback\<observer.TabContentInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'tabContentUpdate', options: observer.ObserverOptions, callback?: Callback\<observer.TabContentInfo>): void;<br>差异内容：off(type: 'tabContentUpdate', options: observer.ObserverOptions, callback?: Callback\<observer.TabContentInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIObserver；<br>API声明：off(type: 'tabContentUpdate', callback?: Callback\<observer.TabContentInfo>): void;<br>差异内容：off(type: 'tabContentUpdate', callback?: Callback\<observer.TabContentInfo>): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export class OverlayManager<br>差异内容：export class OverlayManager|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：OverlayManager；<br>API声明：addComponentContent(content: ComponentContent, index?: number): void;<br>差异内容：addComponentContent(content: ComponentContent, index?: number): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：OverlayManager；<br>API声明：removeComponentContent(content: ComponentContent): void;<br>差异内容：removeComponentContent(content: ComponentContent): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：OverlayManager；<br>API声明：showComponentContent(content: ComponentContent): void;<br>差异内容：showComponentContent(content: ComponentContent): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：OverlayManager；<br>API声明：hideComponentContent(content: ComponentContent): void;<br>差异内容：hideComponentContent(content: ComponentContent): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：OverlayManager；<br>API声明：showAllComponentContents(): void;<br>差异内容：showAllComponentContents(): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：OverlayManager；<br>API声明：hideAllComponentContents(): void;<br>差异内容：hideAllComponentContents(): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export class DynamicSyncScene<br>差异内容：export class DynamicSyncScene|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：DynamicSyncScene；<br>API声明：setFrameRateRange(range: ExpectedFrameRateRange): void;<br>差异内容：setFrameRateRange(range: ExpectedFrameRateRange): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：DynamicSyncScene；<br>API声明：getFrameRateRange(): ExpectedFrameRateRange;<br>差异内容：getFrameRateRange(): ExpectedFrameRateRange;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export class SwiperDynamicSyncScene<br>差异内容：export class SwiperDynamicSyncScene|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：SwiperDynamicSyncScene；<br>API声明：readonly type: SwiperDynamicSyncSceneType;<br>差异内容：readonly type: SwiperDynamicSyncSceneType;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：DragController；<br>API声明：setDragEventStrictReportingEnabled(enable: boolean): void;<br>差异内容：setDragEventStrictReportingEnabled(enable: boolean): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export class MeasureUtils<br>差异内容：export class MeasureUtils|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：MeasureUtils；<br>API声明：measureText(options: MeasureOptions): number;<br>差异内容：measureText(options: MeasureOptions): number;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：MeasureUtils；<br>API声明：measureTextSize(options: MeasureOptions): SizeOptions;<br>差异内容：measureTextSize(options: MeasureOptions): SizeOptions;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export class FocusController<br>差异内容：export class FocusController|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：FocusController；<br>API声明：clearFocus(): void;<br>差异内容：clearFocus(): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：FocusController；<br>API声明：requestFocus(key: string): void;<br>差异内容：requestFocus(key: string): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export type PointerStyle = pointer.PointerStyle;<br>差异内容：export type PointerStyle = pointer.PointerStyle;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export class CursorController<br>差异内容：export class CursorController|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：CursorController；<br>API声明：restoreDefault(): void;<br>差异内容：restoreDefault(): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：CursorController；<br>API声明：setCursor(value: PointerStyle): void;<br>差异内容：setCursor(value: PointerStyle): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export class ContextMenuController<br>差异内容：export class ContextMenuController|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：ContextMenuController；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export abstract class FrameCallback<br>差异内容：export abstract class FrameCallback|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：FrameCallback；<br>API声明：onFrame(frameTimeInNano: number): void;<br>差异内容：onFrame(frameTimeInNano: number): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：FrameCallback；<br>API声明：onIdle(timeLeftInNano: number): void;<br>差异内容：onIdle(timeLeftInNano: number): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export type Context = common.Context;<br>差异内容：export type Context = common.Context;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export class ComponentSnapshot<br>差异内容：export class ComponentSnapshot|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：ComponentSnapshot；<br>API声明：get(id: string, callback: AsyncCallback\<image.PixelMap>, options?: componentSnapshot.SnapshotOptions): void;<br>差异内容：get(id: string, callback: AsyncCallback\<image.PixelMap>, options?: componentSnapshot.SnapshotOptions): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：ComponentSnapshot；<br>API声明：get(id: string, options?: componentSnapshot.SnapshotOptions): Promise\<image.PixelMap>;<br>差异内容：get(id: string, options?: componentSnapshot.SnapshotOptions): Promise\<image.PixelMap>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：ComponentSnapshot；<br>API声明：createFromBuilder(builder: CustomBuilder, callback: AsyncCallback\<image.PixelMap>, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): void;<br>差异内容：createFromBuilder(builder: CustomBuilder, callback: AsyncCallback\<image.PixelMap>, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：ComponentSnapshot；<br>API声明：createFromBuilder(builder: CustomBuilder, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise\<image.PixelMap>;<br>差异内容：createFromBuilder(builder: CustomBuilder, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise\<image.PixelMap>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：ComponentSnapshot；<br>API声明：getSync(id: string, options?: componentSnapshot.SnapshotOptions): image.PixelMap;<br>差异内容：getSync(id: string, options?: componentSnapshot.SnapshotOptions): image.PixelMap;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getFilteredInspectorTree(filters?: Array\<string>): string;<br>差异内容：getFilteredInspectorTree(filters?: Array\<string>): string;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getFilteredInspectorTreeById(id: string, depth: number, filters?: Array\<string>): string;<br>差异内容：getFilteredInspectorTreeById(id: string, depth: number, filters?: Array\<string>): string;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getOverlayManager(): OverlayManager;<br>差异内容：getOverlayManager(): OverlayManager;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getMeasureUtils(): MeasureUtils;<br>差异内容：getMeasureUtils(): MeasureUtils;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getFocusController(): FocusController;<br>差异内容：getFocusController(): FocusController;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getFrameNodeById(id: string): FrameNode \| null;<br>差异内容：getFrameNodeById(id: string): FrameNode \| null;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getAttachedFrameNodeById(id: string): FrameNode \| null;<br>差异内容：getAttachedFrameNodeById(id: string): FrameNode \| null;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getFrameNodeByUniqueId(id: number): FrameNode \| null;<br>差异内容：getFrameNodeByUniqueId(id: number): FrameNode \| null;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getPageInfoByUniqueId(id: number): PageInfo;<br>差异内容：getPageInfoByUniqueId(id: number): PageInfo;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getNavigationInfoByUniqueId(id: number): observer.NavigationInfo \| undefined;<br>差异内容：getNavigationInfoByUniqueId(id: number): observer.NavigationInfo \| undefined;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getCursorController(): CursorController;<br>差异内容：getCursorController(): CursorController;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getContextMenuController(): ContextMenuController;<br>差异内容：getContextMenuController(): ContextMenuController;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getComponentSnapshot(): ComponentSnapshot;<br>差异内容：getComponentSnapshot(): ComponentSnapshot;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：vp2px(value: number): number;<br>差异内容：vp2px(value: number): number;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：px2vp(value: number): number;<br>差异内容：px2vp(value: number): number;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：fp2px(value: number): number;<br>差异内容：fp2px(value: number): number;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：px2fp(value: number): number;<br>差异内容：px2fp(value: number): number;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：lpx2px(value: number): number;<br>差异内容：lpx2px(value: number): number;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：px2lpx(value: number): number;<br>差异内容：px2lpx(value: number): number;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getSharedLocalStorage(): LocalStorage \| undefined;<br>差异内容：getSharedLocalStorage(): LocalStorage \| undefined;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getHostContext(): Context \| undefined;<br>差异内容：getHostContext(): Context \| undefined;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：getWindowName(): string \| undefined;<br>差异内容：getWindowName(): string \| undefined;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：openBindSheet\<T extends Object>(bindSheetContent: ComponentContent\<T>, sheetOptions?: SheetOptions, targetId?: number): Promise\<void>;<br>差异内容：openBindSheet\<T extends Object>(bindSheetContent: ComponentContent\<T>, sheetOptions?: SheetOptions, targetId?: number): Promise\<void>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：updateBindSheet\<T extends Object>(bindSheetContent: ComponentContent\<T>, sheetOptions: SheetOptions, partialUpdate?: boolean): Promise\<void>;<br>差异内容：updateBindSheet\<T extends Object>(bindSheetContent: ComponentContent\<T>, sheetOptions: SheetOptions, partialUpdate?: boolean): Promise\<void>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：closeBindSheet\<T extends Object>(bindSheetContent: ComponentContent\<T>): Promise\<void>;<br>差异内容：closeBindSheet\<T extends Object>(bindSheetContent: ComponentContent\<T>): Promise\<void>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：postFrameCallback(frameCallback: FrameCallback): void;<br>差异内容：postFrameCallback(frameCallback: FrameCallback): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：postDelayedFrameCallback(frameCallback: FrameCallback, delayTime: number): void;<br>差异内容：postDelayedFrameCallback(frameCallback: FrameCallback, delayTime: number): void;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：UIContext；<br>API声明：requireDynamicSyncScene(id: string): Array\<DynamicSyncScene>;<br>差异内容：requireDynamicSyncScene(id: string): Array\<DynamicSyncScene>;|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：global；<br>API声明：export const enum SwiperDynamicSyncSceneType<br>差异内容：export const enum SwiperDynamicSyncSceneType|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：SwiperDynamicSyncSceneType；<br>API声明：GESTURE = 0<br>差异内容：GESTURE = 0|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：SwiperDynamicSyncSceneType；<br>API声明：ANIMATION = 1<br>差异内容：ANIMATION = 1|api/@ohos.arkui.UIContext.d.ts|
|新增API|NA|类名：AnimatorResult；<br>API声明：onFrame: (progress: number) => void;<br>差异内容：onFrame: (progress: number) => void;|api/@ohos.animator.d.ts|
|新增API|NA|类名：AnimatorResult；<br>API声明：onFinish: () => void;<br>差异内容：onFinish: () => void;|api/@ohos.animator.d.ts|
|新增API|NA|类名：AnimatorResult；<br>API声明：onCancel: () => void;<br>差异内容：onCancel: () => void;|api/@ohos.animator.d.ts|
|新增API|NA|类名：AnimatorResult；<br>API声明：onRepeat: () => void;<br>差异内容：onRepeat: () => void;|api/@ohos.animator.d.ts|
|新增API|NA|类名：AnimatorResult；<br>API声明：setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void;<br>差异内容：setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void;|api/@ohos.animator.d.ts|
|新增API|NA|类名：CounterOptions；<br>API声明：direction?: Direction;<br>差异内容：direction?: Direction;|api/@ohos.arkui.advanced.Counter.d.ets|
|新增API|NA|类名：ButtonOptions；<br>API声明：buttonStyle?: ButtonStyleMode;<br>差异内容：buttonStyle?: ButtonStyleMode;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：ButtonOptions；<br>API声明：role?: ButtonRole;<br>差异内容：role?: ButtonRole;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：TipsDialog；<br>API声明：checkAction?: (isChecked: boolean) => void;<br>差异内容：checkAction?: (isChecked: boolean) => void;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：TipsDialog；<br>API声明：theme?: Theme \| CustomTheme;<br>差异内容：theme?: Theme \| CustomTheme;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：TipsDialog；<br>API声明：themeColorMode?: ThemeColorMode;<br>差异内容：themeColorMode?: ThemeColorMode;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：TipsDialog；<br>API声明：onCheckedChange?: Callback\<boolean>;<br>差异内容：onCheckedChange?: Callback\<boolean>;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：SelectDialog；<br>API声明：theme?: Theme \| CustomTheme;<br>差异内容：theme?: Theme \| CustomTheme;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：SelectDialog；<br>API声明：themeColorMode?: ThemeColorMode;<br>差异内容：themeColorMode?: ThemeColorMode;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：ConfirmDialog；<br>API声明：theme?: Theme \| CustomTheme;<br>差异内容：theme?: Theme \| CustomTheme;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：ConfirmDialog；<br>API声明：themeColorMode?: ThemeColorMode;<br>差异内容：themeColorMode?: ThemeColorMode;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：ConfirmDialog；<br>API声明：onCheckedChange?: Callback\<boolean>;<br>差异内容：onCheckedChange?: Callback\<boolean>;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：AlertDialog；<br>API声明：primaryTitle?: ResourceStr;<br>差异内容：primaryTitle?: ResourceStr;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：AlertDialog；<br>API声明：secondaryTitle?: ResourceStr;<br>差异内容：secondaryTitle?: ResourceStr;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：AlertDialog；<br>API声明：theme?: Theme \| CustomTheme;<br>差异内容：theme?: Theme \| CustomTheme;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：AlertDialog；<br>API声明：themeColorMode?: ThemeColorMode;<br>差异内容：themeColorMode?: ThemeColorMode;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：LoadingDialog；<br>API声明：theme?: Theme \| CustomTheme;<br>差异内容：theme?: Theme \| CustomTheme;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：LoadingDialog；<br>API声明：themeColorMode?: ThemeColorMode;<br>差异内容：themeColorMode?: ThemeColorMode;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare struct CustomContentDialog<br>差异内容：export declare struct CustomContentDialog|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：CustomContentDialog；<br>API声明：controller: CustomDialogController;<br>差异内容：controller: CustomDialogController;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：CustomContentDialog；<br>API声明：primaryTitle?: ResourceStr;<br>差异内容：primaryTitle?: ResourceStr;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：CustomContentDialog；<br>API声明：secondaryTitle?: ResourceStr;<br>差异内容：secondaryTitle?: ResourceStr;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：CustomContentDialog；<br>API声明：@BuilderParam<br>    contentBuilder: () => void;<br>差异内容：@BuilderParam<br>    contentBuilder: () => void;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：CustomContentDialog；<br>API声明：contentAreaPadding?: Padding;<br>差异内容：contentAreaPadding?: Padding;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：CustomContentDialog；<br>API声明：localizedContentAreaPadding?: LocalizedPadding;<br>差异内容：localizedContentAreaPadding?: LocalizedPadding;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：CustomContentDialog；<br>API声明：buttons?: ButtonOptions[];<br>差异内容：buttons?: ButtonOptions[];|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：CustomContentDialog；<br>API声明：theme?: Theme \| CustomTheme;<br>差异内容：theme?: Theme \| CustomTheme;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：CustomContentDialog；<br>API声明：themeColorMode?: ThemeColorMode;<br>差异内容：themeColorMode?: ThemeColorMode;|api/@ohos.arkui.advanced.Dialog.d.ets|
|新增API|NA|类名：PopupOptions；<br>API声明：direction?: Direction;<br>差异内容：direction?: Direction;|api/@ohos.arkui.advanced.Popup.d.ets|
|新增API|NA|类名：CommonSegmentButtonOptions；<br>API声明：localizedButtonPadding?: LocalizedPadding;<br>差异内容：localizedButtonPadding?: LocalizedPadding;|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|新增API|NA|类名：CommonSegmentButtonOptions；<br>API声明：localizedTextPadding?: LocalizedPadding;<br>差异内容：localizedTextPadding?: LocalizedPadding;|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|新增API|NA|类名：CommonSegmentButtonOptions；<br>API声明：direction?: Direction;<br>差异内容：direction?: Direction;|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|新增API|NA|类名：SegmentButtonOptions；<br>API声明：localizedButtonPadding?: LocalizedPadding;<br>差异内容：localizedButtonPadding?: LocalizedPadding;|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|新增API|NA|类名：SegmentButtonOptions；<br>API声明：localizedTextPadding?: LocalizedPadding;<br>差异内容：localizedTextPadding?: LocalizedPadding;|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|新增API|NA|类名：SegmentButtonOptions；<br>API声明：direction?: Direction;<br>差异内容：direction?: Direction;|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|新增API|NA|类名：componentSnapshot；<br>API声明：interface SnapshotOptions<br>差异内容：interface SnapshotOptions|api/@ohos.arkui.componentSnapshot.d.ts|
|新增API|NA|类名：SnapshotOptions；<br>API声明：scale?: number;<br>差异内容：scale?: number;|api/@ohos.arkui.componentSnapshot.d.ts|
|新增API|NA|类名：SnapshotOptions；<br>API声明：waitUntilRenderFinished?: boolean;<br>差异内容：waitUntilRenderFinished?: boolean;|api/@ohos.arkui.componentSnapshot.d.ts|
|新增API|NA|类名：componentSnapshot；<br>API声明：function getSync(id: string, options?: SnapshotOptions): image.PixelMap;<br>差异内容：function getSync(id: string, options?: SnapshotOptions): image.PixelMap;|api/@ohos.arkui.componentSnapshot.d.ts|
|新增API|NA|类名：dragController；<br>API声明：interface DragEventParam<br>差异内容：interface DragEventParam|api/@ohos.arkui.dragController.d.ts|
|新增API|NA|类名：DragEventParam；<br>API声明：event: DragEvent;<br>差异内容：event: DragEvent;|api/@ohos.arkui.dragController.d.ts|
|新增API|NA|类名：DragEventParam；<br>API声明：extraParams: string;<br>差异内容：extraParams: string;|api/@ohos.arkui.dragController.d.ts|
|新增API|NA|类名：global；<br>API声明：export class PixelMapDrawableDescriptor<br>差异内容：export class PixelMapDrawableDescriptor|api/@ohos.arkui.drawableDescriptor.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface AnimationOptions<br>差异内容：declare interface AnimationOptions|api/@ohos.arkui.drawableDescriptor.d.ts|
|新增API|NA|类名：AnimationOptions；<br>API声明：duration?: number;<br>差异内容：duration?: number;|api/@ohos.arkui.drawableDescriptor.d.ts|
|新增API|NA|类名：AnimationOptions；<br>API声明：iterations?: number;<br>差异内容：iterations?: number;|api/@ohos.arkui.drawableDescriptor.d.ts|
|新增API|NA|类名：global；<br>API声明：export class AnimatedDrawableDescriptor<br>差异内容：export class AnimatedDrawableDescriptor|api/@ohos.arkui.drawableDescriptor.d.ts|
|新增API|NA|类名：NavDestinationState；<br>API声明：ON_APPEAR = 2<br>差异内容：ON_APPEAR = 2|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationState；<br>API声明：ON_DISAPPEAR = 3<br>差异内容：ON_DISAPPEAR = 3|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationState；<br>API声明：ON_WILL_SHOW = 4<br>差异内容：ON_WILL_SHOW = 4|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationState；<br>API声明：ON_WILL_HIDE = 5<br>差异内容：ON_WILL_HIDE = 5|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationState；<br>API声明：ON_WILL_APPEAR = 6<br>差异内容：ON_WILL_APPEAR = 6|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationState；<br>API声明：ON_WILL_DISAPPEAR = 7<br>差异内容：ON_WILL_DISAPPEAR = 7|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationState；<br>API声明：ON_BACKPRESS = 100<br>差异内容：ON_BACKPRESS = 100|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export enum ScrollEventType<br>差异内容：export enum ScrollEventType|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：ScrollEventType；<br>API声明：SCROLL_START = 0<br>差异内容：SCROLL_START = 0|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：ScrollEventType；<br>API声明：SCROLL_STOP = 1<br>差异内容：SCROLL_STOP = 1|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export enum TabContentState<br>差异内容：export enum TabContentState|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：TabContentState；<br>API声明：ON_SHOW = 0<br>差异内容：ON_SHOW = 0|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：TabContentState；<br>API声明：ON_HIDE = 1<br>差异内容：ON_HIDE = 1|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationInfo；<br>API声明：index: number;<br>差异内容：index: number;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationInfo；<br>API声明：param?: Object;<br>差异内容：param?: Object;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationInfo；<br>API声明：navDestinationId: string;<br>差异内容：navDestinationId: string;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export interface NavigationInfo<br>差异内容：export interface NavigationInfo|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavigationInfo；<br>API声明：navigationId: string;<br>差异内容：navigationId: string;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavigationInfo；<br>API声明：pathStack: NavPathStack;<br>差异内容：pathStack: NavPathStack;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export interface ScrollEventInfo<br>差异内容：export interface ScrollEventInfo|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：ScrollEventInfo；<br>API声明：id: string;<br>差异内容：id: string;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：ScrollEventInfo；<br>API声明：uniqueId: number;<br>差异内容：uniqueId: number;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：ScrollEventInfo；<br>API声明：scrollEvent: ScrollEventType;<br>差异内容：scrollEvent: ScrollEventType;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：ScrollEventInfo；<br>API声明：offset: number;<br>差异内容：offset: number;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export interface TabContentInfo<br>差异内容：export interface TabContentInfo|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：TabContentInfo；<br>API声明：tabContentId: string;<br>差异内容：tabContentId: string;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：TabContentInfo；<br>API声明：tabContentUniqueId: number;<br>差异内容：tabContentUniqueId: number;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：TabContentInfo；<br>API声明：state: TabContentState;<br>差异内容：state: TabContentState;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：TabContentInfo；<br>API声明：index: number;<br>差异内容：index: number;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：TabContentInfo；<br>API声明：id: string;<br>差异内容：id: string;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：TabContentInfo；<br>API声明：uniqueId: number;<br>差异内容：uniqueId: number;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export interface ObserverOptions<br>差异内容：export interface ObserverOptions|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：ObserverOptions；<br>API声明：id: string;<br>差异内容：id: string;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：RouterPageInfo；<br>API声明：pageId: string;<br>差异内容：pageId: string;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export class DensityInfo<br>差异内容：export class DensityInfo|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：DensityInfo；<br>API声明：context: UIContext;<br>差异内容：context: UIContext;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：DensityInfo；<br>API声明：density: number;<br>差异内容：density: number;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export interface NavDestinationSwitchInfo<br>差异内容：export interface NavDestinationSwitchInfo|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationSwitchInfo；<br>API声明：context: UIAbilityContext \| UIContext;<br>差异内容：context: UIAbilityContext \| UIContext;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationSwitchInfo；<br>API声明：from: NavDestinationInfo \| NavBar;<br>差异内容：from: NavDestinationInfo \| NavBar;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationSwitchInfo；<br>API声明：to: NavDestinationInfo \| NavBar;<br>差异内容：to: NavDestinationInfo \| NavBar;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationSwitchInfo；<br>API声明：operation: NavigationOperation;<br>差异内容：operation: NavigationOperation;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export interface NavDestinationSwitchObserverOptions<br>差异内容：export interface NavDestinationSwitchObserverOptions|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：NavDestinationSwitchObserverOptions；<br>API声明：navigationId: ResourceStr;<br>差异内容：navigationId: ResourceStr;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function on(type: 'scrollEvent', options: ObserverOptions, callback: Callback\<ScrollEventInfo>): void;<br>差异内容：export function on(type: 'scrollEvent', options: ObserverOptions, callback: Callback\<ScrollEventInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function on(type: 'scrollEvent', callback: Callback\<ScrollEventInfo>): void;<br>差异内容：export function on(type: 'scrollEvent', callback: Callback\<ScrollEventInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback\<ScrollEventInfo>): void;<br>差异内容：export function off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback\<ScrollEventInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function off(type: 'scrollEvent', callback?: Callback\<ScrollEventInfo>): void;<br>差异内容：export function off(type: 'scrollEvent', callback?: Callback\<ScrollEventInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function on(type: 'densityUpdate', context: UIContext, callback: Callback\<DensityInfo>): void;<br>差异内容：export function on(type: 'densityUpdate', context: UIContext, callback: Callback\<DensityInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function off(type: 'densityUpdate', context: UIContext, callback?: Callback\<DensityInfo>): void;<br>差异内容：export function off(type: 'densityUpdate', context: UIContext, callback?: Callback\<DensityInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function on(type: 'willDraw', context: UIContext, callback: Callback\<void>): void;<br>差异内容：export function on(type: 'willDraw', context: UIContext, callback: Callback\<void>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function off(type: 'willDraw', context: UIContext, callback?: Callback\<void>): void;<br>差异内容：export function off(type: 'willDraw', context: UIContext, callback?: Callback\<void>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function on(type: 'didLayout', context: UIContext, callback: Callback\<void>): void;<br>差异内容：export function on(type: 'didLayout', context: UIContext, callback: Callback\<void>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function off(type: 'didLayout', context: UIContext, callback?: Callback\<void>): void;<br>差异内容：export function off(type: 'didLayout', context: UIContext, callback?: Callback\<void>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback\<TabContentInfo>): void;<br>差异内容：export function on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback\<TabContentInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function on(type: 'tabContentUpdate', callback: Callback\<TabContentInfo>): void;<br>差异内容：export function on(type: 'tabContentUpdate', callback: Callback\<TabContentInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback\<TabContentInfo>): void;<br>差异内容：export function off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback\<TabContentInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function off(type: 'tabContentUpdate', callback?: Callback\<TabContentInfo>): void;<br>差异内容：export function off(type: 'tabContentUpdate', callback?: Callback\<TabContentInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function on(type: 'navDestinationSwitch', context: UIAbilityContext \| UIContext, callback: Callback\<NavDestinationSwitchInfo>): void;<br>差异内容：export function on(type: 'navDestinationSwitch', context: UIAbilityContext \| UIContext, callback: Callback\<NavDestinationSwitchInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function on(type: 'navDestinationSwitch', context: UIAbilityContext \| UIContext, observerOptions: NavDestinationSwitchObserverOptions, callback: Callback\<NavDestinationSwitchInfo>): void;<br>差异内容：export function on(type: 'navDestinationSwitch', context: UIAbilityContext \| UIContext, observerOptions: NavDestinationSwitchObserverOptions, callback: Callback\<NavDestinationSwitchInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function off(type: 'navDestinationSwitch', context: UIAbilityContext \| UIContext, callback?: Callback\<NavDestinationSwitchInfo>): void;<br>差异内容：export function off(type: 'navDestinationSwitch', context: UIAbilityContext \| UIContext, callback?: Callback\<NavDestinationSwitchInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：uiObserver；<br>API声明：export function off(type: 'navDestinationSwitch', context: UIAbilityContext \| UIContext, observerOptions: NavDestinationSwitchObserverOptions, callback?: Callback\<NavDestinationSwitchInfo>): void;<br>差异内容：export function off(type: 'navDestinationSwitch', context: UIAbilityContext \| UIContext, observerOptions: NavDestinationSwitchObserverOptions, callback?: Callback\<NavDestinationSwitchInfo>): void;|api/@ohos.arkui.observer.d.ts|
|新增API|NA|类名：display；<br>API声明：function getDisplayByIdSync(displayId: number): Display;<br>差异内容：function getDisplayByIdSync(displayId: number): Display;|api/@ohos.display.d.ts|
|新增API|NA|类名：display；<br>API声明：function getAllDisplayPhysicalResolution(): Promise\<Array\<DisplayPhysicalResolution>>;<br>差异内容：function getAllDisplayPhysicalResolution(): Promise\<Array\<DisplayPhysicalResolution>>;|api/@ohos.display.d.ts|
|新增API|NA|类名：display；<br>API声明：function on(type: 'foldAngleChange', callback: Callback\<Array\<number>>): void;<br>差异内容：function on(type: 'foldAngleChange', callback: Callback\<Array\<number>>): void;|api/@ohos.display.d.ts|
|新增API|NA|类名：display；<br>API声明：function off(type: 'foldAngleChange', callback?: Callback\<Array\<number>>): void;<br>差异内容：function off(type: 'foldAngleChange', callback?: Callback\<Array\<number>>): void;|api/@ohos.display.d.ts|
|新增API|NA|类名：display；<br>API声明：function on(type: 'captureStatusChange', callback: Callback\<boolean>): void;<br>差异内容：function on(type: 'captureStatusChange', callback: Callback\<boolean>): void;|api/@ohos.display.d.ts|
|新增API|NA|类名：display；<br>API声明：function off(type: 'captureStatusChange', callback?: Callback\<boolean>): void;<br>差异内容：function off(type: 'captureStatusChange', callback?: Callback\<boolean>): void;|api/@ohos.display.d.ts|
|新增API|NA|类名：display；<br>API声明：function isCaptured(): boolean;<br>差异内容：function isCaptured(): boolean;|api/@ohos.display.d.ts|
|新增API|NA|类名：display；<br>API声明：interface DisplayPhysicalResolution<br>差异内容：interface DisplayPhysicalResolution|api/@ohos.display.d.ts|
|新增API|NA|类名：DisplayPhysicalResolution；<br>API声明：foldDisplayMode: FoldDisplayMode;<br>差异内容：foldDisplayMode: FoldDisplayMode;|api/@ohos.display.d.ts|
|新增API|NA|类名：DisplayPhysicalResolution；<br>API声明：physicalWidth: number;<br>差异内容：physicalWidth: number;|api/@ohos.display.d.ts|
|新增API|NA|类名：DisplayPhysicalResolution；<br>API声明：physicalHeight: number;<br>差异内容：physicalHeight: number;|api/@ohos.display.d.ts|
|新增API|NA|类名：Display；<br>API声明：availableWidth: number;<br>差异内容：availableWidth: number;|api/@ohos.display.d.ts|
|新增API|NA|类名：Display；<br>API声明：availableHeight: number;<br>差异内容：availableHeight: number;|api/@ohos.display.d.ts|
|新增API|NA|类名：Display；<br>API声明：getAvailableArea(): Promise\<Rect>;<br>差异内容：getAvailableArea(): Promise\<Rect>;|api/@ohos.display.d.ts|
|新增API|NA|类名：Display；<br>API声明：on(type: 'availableAreaChange', callback: Callback\<Rect>): void;<br>差异内容：on(type: 'availableAreaChange', callback: Callback\<Rect>): void;|api/@ohos.display.d.ts|
|新增API|NA|类名：Display；<br>API声明：off(type: 'availableAreaChange', callback?: Callback\<Rect>): void;<br>差异内容：off(type: 'availableAreaChange', callback?: Callback\<Rect>): void;|api/@ohos.display.d.ts|
|新增API|NA|类名：PiPConfiguration；<br>API声明：controlGroups?: Array\<PiPControlGroup>;<br>差异内容：controlGroups?: Array\<PiPControlGroup>;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPConfiguration；<br>API声明：customUIController?: NodeController;<br>差异内容：customUIController?: NodeController;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPWindow；<br>API声明：type PiPControlGroup = VideoPlayControlGroup \| VideoCallControlGroup \| VideoMeetingControlGroup \| VideoLiveControlGroup;<br>差异内容：type PiPControlGroup = VideoPlayControlGroup \| VideoCallControlGroup \| VideoMeetingControlGroup \| VideoLiveControlGroup;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPWindow；<br>API声明：enum VideoPlayControlGroup<br>差异内容：enum VideoPlayControlGroup|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoPlayControlGroup；<br>API声明：VIDEO_PREVIOUS_NEXT = 101<br>差异内容：VIDEO_PREVIOUS_NEXT = 101|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoPlayControlGroup；<br>API声明：FAST_FORWARD_BACKWARD = 102<br>差异内容：FAST_FORWARD_BACKWARD = 102|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPWindow；<br>API声明：enum VideoCallControlGroup<br>差异内容：enum VideoCallControlGroup|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoCallControlGroup；<br>API声明：MICROPHONE_SWITCH = 201<br>差异内容：MICROPHONE_SWITCH = 201|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoCallControlGroup；<br>API声明：HANG_UP_BUTTON = 202<br>差异内容：HANG_UP_BUTTON = 202|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoCallControlGroup；<br>API声明：CAMERA_SWITCH = 203<br>差异内容：CAMERA_SWITCH = 203|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoCallControlGroup；<br>API声明：MUTE_SWITCH = 204<br>差异内容：MUTE_SWITCH = 204|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPWindow；<br>API声明：enum VideoMeetingControlGroup<br>差异内容：enum VideoMeetingControlGroup|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoMeetingControlGroup；<br>API声明：HANG_UP_BUTTON = 301<br>差异内容：HANG_UP_BUTTON = 301|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoMeetingControlGroup；<br>API声明：CAMERA_SWITCH = 302<br>差异内容：CAMERA_SWITCH = 302|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoMeetingControlGroup；<br>API声明：MUTE_SWITCH = 303<br>差异内容：MUTE_SWITCH = 303|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoMeetingControlGroup；<br>API声明：MICROPHONE_SWITCH = 304<br>差异内容：MICROPHONE_SWITCH = 304|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPWindow；<br>API声明：enum VideoLiveControlGroup<br>差异内容：enum VideoLiveControlGroup|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoLiveControlGroup；<br>API声明：VIDEO_PLAY_PAUSE = 401<br>差异内容：VIDEO_PLAY_PAUSE = 401|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：VideoLiveControlGroup；<br>API声明：MUTE_SWITCH = 402<br>差异内容：MUTE_SWITCH = 402|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPWindow；<br>API声明：enum PiPControlStatus<br>差异内容：enum PiPControlStatus|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlStatus；<br>API声明：PLAY = 1<br>差异内容：PLAY = 1|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlStatus；<br>API声明：PAUSE = 0<br>差异内容：PAUSE = 0|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlStatus；<br>API声明：OPEN = 1<br>差异内容：OPEN = 1|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlStatus；<br>API声明：CLOSE = 0<br>差异内容：CLOSE = 0|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPWindow；<br>API声明：enum PiPControlType<br>差异内容：enum PiPControlType|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlType；<br>API声明：VIDEO_PLAY_PAUSE = 0<br>差异内容：VIDEO_PLAY_PAUSE = 0|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlType；<br>API声明：VIDEO_PREVIOUS = 1<br>差异内容：VIDEO_PREVIOUS = 1|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlType；<br>API声明：VIDEO_NEXT = 2<br>差异内容：VIDEO_NEXT = 2|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlType；<br>API声明：FAST_FORWARD = 3<br>差异内容：FAST_FORWARD = 3|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlType；<br>API声明：FAST_BACKWARD = 4<br>差异内容：FAST_BACKWARD = 4|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlType；<br>API声明：HANG_UP_BUTTON = 5<br>差异内容：HANG_UP_BUTTON = 5|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlType；<br>API声明：MICROPHONE_SWITCH = 6<br>差异内容：MICROPHONE_SWITCH = 6|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlType；<br>API声明：CAMERA_SWITCH = 7<br>差异内容：CAMERA_SWITCH = 7|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPControlType；<br>API声明：MUTE_SWITCH = 8<br>差异内容：MUTE_SWITCH = 8|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPWindow；<br>API声明：type ControlPanelActionEventCallback = (event: PiPActionEventType, status?: number) => void;<br>差异内容：type ControlPanelActionEventCallback = (event: PiPActionEventType, status?: number) => void;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPWindow；<br>API声明：interface ControlEventParam<br>差异内容：interface ControlEventParam|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：ControlEventParam；<br>API声明：controlType: PiPControlType;<br>差异内容：controlType: PiPControlType;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：ControlEventParam；<br>API声明：status?: PiPControlStatus;<br>差异内容：status?: PiPControlStatus;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPController；<br>API声明：updatePiPControlStatus(controlType: PiPControlType, status: PiPControlStatus): void;<br>差异内容：updatePiPControlStatus(controlType: PiPControlType, status: PiPControlStatus): void;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPController；<br>API声明：setPiPControlEnabled(controlType: PiPControlType, enabled: boolean): void;<br>差异内容：setPiPControlEnabled(controlType: PiPControlType, enabled: boolean): void;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPController；<br>API声明：on(type: 'controlEvent', callback: Callback\<ControlEventParam>): void;<br>差异内容：on(type: 'controlEvent', callback: Callback\<ControlEventParam>): void;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：PiPController；<br>API声明：off(type: 'controlEvent', callback?: Callback\<ControlEventParam>): void;<br>差异内容：off(type: 'controlEvent', callback?: Callback\<ControlEventParam>): void;|api/@ohos.PiPWindow.d.ts|
|新增API|NA|类名：ShowToastOptions；<br>API声明：alignment?: Alignment;<br>差异内容：alignment?: Alignment;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowToastOptions；<br>API声明：offset?: Offset;<br>差异内容：offset?: Offset;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowToastOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：backgroundColor?: ResourceColor;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowToastOptions；<br>API声明：textColor?: ResourceColor;<br>差异内容：textColor?: ResourceColor;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowToastOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：backgroundBlurStyle?: BlurStyle;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowToastOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：Button；<br>API声明：primary?: boolean;<br>差异内容：primary?: boolean;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：backgroundColor?: ResourceColor;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：backgroundBlurStyle?: BlurStyle;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：ShowDialogOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：autoCancel?: boolean;<br>差异内容：autoCancel?: boolean;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：transition?: TransitionEffect;<br>差异内容：transition?: TransitionEffect;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：maskColor?: ResourceColor;<br>差异内容：maskColor?: ResourceColor;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：onWillDismiss?: Callback\<DismissDialogAction>;<br>差异内容：onWillDismiss?: Callback\<DismissDialogAction>;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：onDidAppear?: () => void;<br>差异内容：onDidAppear?: () => void;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：onDidDisappear?: () => void;<br>差异内容：onDidDisappear?: () => void;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：onWillAppear?: () => void;<br>差异内容：onWillAppear?: () => void;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：onWillDisappear?: () => void;<br>差异内容：onWillDisappear?: () => void;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：BaseDialogOptions；<br>API声明：keyboardAvoidMode?: KeyboardAvoidMode;<br>差异内容：keyboardAvoidMode?: KeyboardAvoidMode;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：CustomDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：backgroundColor?: ResourceColor;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：CustomDialogOptions；<br>API声明：cornerRadius?: Dimension \| BorderRadiuses;<br>差异内容：cornerRadius?: Dimension \| BorderRadiuses;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：CustomDialogOptions；<br>API声明：width?: Dimension;<br>差异内容：width?: Dimension;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：CustomDialogOptions；<br>API声明：height?: Dimension;<br>差异内容：height?: Dimension;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：CustomDialogOptions；<br>API声明：borderWidth?: Dimension \| EdgeWidths;<br>差异内容：borderWidth?: Dimension \| EdgeWidths;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：CustomDialogOptions；<br>API声明：borderColor?: ResourceColor \| EdgeColors;<br>差异内容：borderColor?: ResourceColor \| EdgeColors;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：CustomDialogOptions；<br>API声明：borderStyle?: BorderStyle \| EdgeStyles;<br>差异内容：borderStyle?: BorderStyle \| EdgeStyles;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：CustomDialogOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：shadow?: ShadowOptions \| ShadowStyle;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：CustomDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：backgroundBlurStyle?: BlurStyle;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface DismissDialogAction<br>差异内容：declare interface DismissDialogAction|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：DismissDialogAction；<br>API声明：dismiss: Callback\<void>;<br>差异内容：dismiss: Callback\<void>;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：DismissDialogAction；<br>API声明：reason: DismissReason;<br>差异内容：reason: DismissReason;|api/@ohos.promptAction.d.ts|
|新增API|NA|类名：router；<br>API声明：function back(index: number, params?: Object): void;<br>差异内容：function back(index: number, params?: Object): void;|api/@ohos.router.d.ts|
|新增API|NA|类名：RouterState；<br>API声明：params: Object;<br>差异内容：params: Object;|api/@ohos.router.d.ts|
|新增API|NA|类名：router；<br>API声明：function getStateByIndex(index: number): RouterState \| undefined;<br>差异内容：function getStateByIndex(index: number): RouterState \| undefined;|api/@ohos.router.d.ts|
|新增API|NA|类名：router；<br>API声明：function getStateByUrl(url: string): Array\<RouterState>;<br>差异内容：function getStateByUrl(url: string): Array\<RouterState>;|api/@ohos.router.d.ts|
|新增API|NA|类名：SystemBarProperties；<br>API声明：enableStatusBarAnimation?: boolean;<br>差异内容：enableStatusBarAnimation?: boolean;|api/@ohos.window.d.ts|
|新增API|NA|类名：SystemBarProperties；<br>API声明：enableNavigationBarAnimation?: boolean;<br>差异内容：enableNavigationBarAnimation?: boolean;|api/@ohos.window.d.ts|
|新增API|NA|类名：window；<br>API声明：interface SystemBarStyle<br>差异内容：interface SystemBarStyle|api/@ohos.window.d.ts|
|新增API|NA|类名：SystemBarStyle；<br>API声明：statusBarContentColor?: string;<br>差异内容：statusBarContentColor?: string;|api/@ohos.window.d.ts|
|新增API|NA|类名：WindowProperties；<br>API声明：displayId?: number;<br>差异内容：displayId?: number;|api/@ohos.window.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：decorEnabled?: boolean;<br>差异内容：decorEnabled?: boolean;|api/@ohos.window.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.window.d.ts|
|新增API|NA|类名：window；<br>API声明：interface RectChangeOptions<br>差异内容：interface RectChangeOptions|api/@ohos.window.d.ts|
|新增API|NA|类名：RectChangeOptions；<br>API声明：rect: Rect;<br>差异内容：rect: Rect;|api/@ohos.window.d.ts|
|新增API|NA|类名：RectChangeOptions；<br>API声明：reason: RectChangeReason;<br>差异内容：reason: RectChangeReason;|api/@ohos.window.d.ts|
|新增API|NA|类名：window；<br>API声明：interface AvoidAreaOptions<br>差异内容：interface AvoidAreaOptions|api/@ohos.window.d.ts|
|新增API|NA|类名：AvoidAreaOptions；<br>API声明：type: AvoidAreaType;<br>差异内容：type: AvoidAreaType;|api/@ohos.window.d.ts|
|新增API|NA|类名：AvoidAreaOptions；<br>API声明：area: AvoidArea;<br>差异内容：area: AvoidArea;|api/@ohos.window.d.ts|
|新增API|NA|类名：window；<br>API声明：enum RectChangeReason<br>差异内容：enum RectChangeReason|api/@ohos.window.d.ts|
|新增API|NA|类名：RectChangeReason；<br>API声明：UNDEFINED = 0<br>差异内容：UNDEFINED = 0|api/@ohos.window.d.ts|
|新增API|NA|类名：RectChangeReason；<br>API声明：MAXIMIZE<br>差异内容：MAXIMIZE|api/@ohos.window.d.ts|
|新增API|NA|类名：RectChangeReason；<br>API声明：RECOVER<br>差异内容：RECOVER|api/@ohos.window.d.ts|
|新增API|NA|类名：RectChangeReason；<br>API声明：MOVE<br>差异内容：MOVE|api/@ohos.window.d.ts|
|新增API|NA|类名：RectChangeReason；<br>API声明：DRAG<br>差异内容：DRAG|api/@ohos.window.d.ts|
|新增API|NA|类名：RectChangeReason；<br>API声明：DRAG_START<br>差异内容：DRAG_START|api/@ohos.window.d.ts|
|新增API|NA|类名：RectChangeReason；<br>API声明：DRAG_END<br>差异内容：DRAG_END|api/@ohos.window.d.ts|
|新增API|NA|类名：Orientation；<br>API声明：AUTO_ROTATION_UNSPECIFIED = 12<br>差异内容：AUTO_ROTATION_UNSPECIFIED = 12|api/@ohos.window.d.ts|
|新增API|NA|类名：Orientation；<br>API声明：USER_ROTATION_PORTRAIT = 13<br>差异内容：USER_ROTATION_PORTRAIT = 13|api/@ohos.window.d.ts|
|新增API|NA|类名：Orientation；<br>API声明：USER_ROTATION_LANDSCAPE = 14<br>差异内容：USER_ROTATION_LANDSCAPE = 14|api/@ohos.window.d.ts|
|新增API|NA|类名：Orientation；<br>API声明：USER_ROTATION_PORTRAIT_INVERTED = 15<br>差异内容：USER_ROTATION_PORTRAIT_INVERTED = 15|api/@ohos.window.d.ts|
|新增API|NA|类名：Orientation；<br>API声明：USER_ROTATION_LANDSCAPE_INVERTED = 16<br>差异内容：USER_ROTATION_LANDSCAPE_INVERTED = 16|api/@ohos.window.d.ts|
|新增API|NA|类名：Orientation；<br>API声明：FOLLOW_DESKTOP = 17<br>差异内容：FOLLOW_DESKTOP = 17|api/@ohos.window.d.ts|
|新增API|NA|类名：window；<br>API声明：enum MaximizePresentation<br>差异内容：enum MaximizePresentation|api/@ohos.window.d.ts|
|新增API|NA|类名：MaximizePresentation；<br>API声明：FOLLOW_APP_IMMERSIVE_SETTING = 0<br>差异内容：FOLLOW_APP_IMMERSIVE_SETTING = 0|api/@ohos.window.d.ts|
|新增API|NA|类名：MaximizePresentation；<br>API声明：EXIT_IMMERSIVE = 1<br>差异内容：EXIT_IMMERSIVE = 1|api/@ohos.window.d.ts|
|新增API|NA|类名：MaximizePresentation；<br>API声明：ENTER_IMMERSIVE = 2<br>差异内容：ENTER_IMMERSIVE = 2|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：moveWindowToAsync(x: number, y: number): Promise\<void>;<br>差异内容：moveWindowToAsync(x: number, y: number): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：resizeAsync(width: number, height: number): Promise\<void>;<br>差异内容：resizeAsync(width: number, height: number): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：getWindowSystemBarProperties(): SystemBarProperties;<br>差异内容：getWindowSystemBarProperties(): SystemBarProperties;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：getPreferredOrientation(): Orientation;<br>差异内容：getPreferredOrientation(): Orientation;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：on(type: 'noInteractionDetected', timeout: number, callback: Callback\<void>): void;<br>差异内容：on(type: 'noInteractionDetected', timeout: number, callback: Callback\<void>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：off(type: 'noInteractionDetected', callback?: Callback\<void>): void;<br>差异内容：off(type: 'noInteractionDetected', callback?: Callback\<void>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：on(type: 'subWindowClose', callback: Callback\<void>): void;<br>差异内容：on(type: 'subWindowClose', callback: Callback\<void>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：off(type: 'subWindowClose', callback?: Callback\<void>): void;<br>差异内容：off(type: 'subWindowClose', callback?: Callback\<void>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setDialogBackGestureEnabled(enabled: boolean): Promise\<void>;<br>差异内容：setDialogBackGestureEnabled(enabled: boolean): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：maximize(presentation?: MaximizePresentation): Promise\<void>;<br>差异内容：maximize(presentation?: MaximizePresentation): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setSubWindowModal(isModal: boolean): Promise\<void>;<br>差异内容：setSubWindowModal(isModal: boolean): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：enableLandscapeMultiWindow(): Promise\<void>;<br>差异内容：enableLandscapeMultiWindow(): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：disableLandscapeMultiWindow(): Promise\<void>;<br>差异内容：disableLandscapeMultiWindow(): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setWindowMask(windowMask: Array\<Array\<number>>): Promise\<void>;<br>差异内容：setWindowMask(windowMask: Array\<Array\<number>>): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：on(type: 'windowRectChange', callback: Callback\<RectChangeOptions>): void;<br>差异内容：on(type: 'windowRectChange', callback: Callback\<RectChangeOptions>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：off(type: 'windowRectChange', callback?: Callback\<RectChangeOptions>): void;<br>差异内容：off(type: 'windowRectChange', callback?: Callback\<RectChangeOptions>): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setWindowGrayScale(grayScale: number): Promise\<void>;<br>差异内容：setWindowGrayScale(grayScale: number): Promise\<void>;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：setImmersiveModeEnabledState(enabled: boolean): void;<br>差异内容：setImmersiveModeEnabledState(enabled: boolean): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：getImmersiveModeEnabledState(): boolean;<br>差异内容：getImmersiveModeEnabledState(): boolean;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：getWindowStatus(): WindowStatusType;<br>差异内容：getWindowStatus(): WindowStatusType;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：isFocused(): boolean;<br>差异内容：isFocused(): boolean;|api/@ohos.window.d.ts|
|新增API|NA|类名：Window；<br>API声明：createSubWindowWithOptions(name: string, options: SubWindowOptions): Promise\<Window>;<br>差异内容：createSubWindowWithOptions(name: string, options: SubWindowOptions): Promise\<Window>;|api/@ohos.window.d.ts|
|新增API|NA|类名：SubWindowOptions；<br>API声明：isModal?: boolean;<br>差异内容：isModal?: boolean;|api/@ohos.window.d.ts|
|新增API|NA|类名：WindowStage；<br>API声明：setDefaultDensityEnabled(enabled: boolean): void;<br>差异内容：setDefaultDensityEnabled(enabled: boolean): void;|api/@ohos.window.d.ts|
|新增API|NA|类名：EditableTitleBarMenuItem；<br>API声明：label?: ResourceStr;<br>差异内容：label?: ResourceStr;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：global；<br>API声明：export type EditableTitleBarItem = EditableTitleBarMenuItem;<br>差异内容：export type EditableTitleBarItem = EditableTitleBarMenuItem;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare interface EditableTitleBarOptions<br>差异内容：export declare interface EditableTitleBarOptions|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：EditableTitleBarOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：backgroundColor?: ResourceColor;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：EditableTitleBarOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：backgroundBlurStyle?: BlurStyle;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：EditableTitleBarOptions；<br>API声明：safeAreaTypes?: Array\<SafeAreaType>;<br>差异内容：safeAreaTypes?: Array\<SafeAreaType>;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：EditableTitleBarOptions；<br>API声明：safeAreaEdges?: Array\<SafeAreaEdge>;<br>差异内容：safeAreaEdges?: Array\<SafeAreaEdge>;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：EditableTitleBar；<br>API声明：imageItem?: EditableTitleBarItem;<br>差异内容：imageItem?: EditableTitleBarItem;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：EditableTitleBar；<br>API声明：subtitle?: ResourceStr;<br>差异内容：subtitle?: ResourceStr;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：EditableTitleBar；<br>API声明：isSaveIconRequired: boolean;<br>差异内容：isSaveIconRequired: boolean;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：EditableTitleBar；<br>API声明：options: EditableTitleBarOptions;<br>差异内容：options: EditableTitleBarOptions;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：EditableTitleBar；<br>API声明：@Prop<br>    contentMargin?: LocalizedMargin;<br>差异内容：@Prop<br>    contentMargin?: LocalizedMargin;|api/@ohos.arkui.advanced.EditableTitleBar.d.ets|
|新增API|NA|类名：global；<br>API声明：export declare class SymbolOptions<br>差异内容：export declare class SymbolOptions|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SymbolOptions；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：fontSize?: number \| string \| Resource;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SymbolOptions；<br>API声明：fontColor?: Array\<ResourceColor>;<br>差异内容：fontColor?: Array\<ResourceColor>;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SymbolOptions；<br>API声明：fontWeight?: number \| FontWeight \| string;<br>差异内容：fontWeight?: number \| FontWeight \| string;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SymbolOptions；<br>API声明：effectStrategy?: SymbolEffectStrategy;<br>差异内容：effectStrategy?: SymbolEffectStrategy;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SymbolOptions；<br>API声明：renderingStrategy?: SymbolRenderingStrategy;<br>差异内容：renderingStrategy?: SymbolRenderingStrategy;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SubHeader；<br>API声明：iconSymbolOptions?: SymbolOptions;<br>差异内容：iconSymbolOptions?: SymbolOptions;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SubHeader；<br>API声明：operationSymbolOptions?: Array\<SymbolOptions>;<br>差异内容：operationSymbolOptions?: Array\<SymbolOptions>;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SubHeader；<br>API声明：primaryTitleModifier?: TextModifier;<br>差异内容：primaryTitleModifier?: TextModifier;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SubHeader；<br>API声明：secondaryTitleModifier?: TextModifier;<br>差异内容：secondaryTitleModifier?: TextModifier;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SubHeader；<br>API声明：@BuilderParam<br>    titleBuilder?: () => void;<br>差异内容：@BuilderParam<br>    titleBuilder?: () => void;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SubHeader；<br>API声明：@Prop<br>    contentMargin?: LocalizedMargin;<br>差异内容：@Prop<br>    contentMargin?: LocalizedMargin;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：SubHeader；<br>API声明：@Prop<br>    contentPadding?: LocalizedPadding;<br>差异内容：@Prop<br>    contentPadding?: LocalizedPadding;|api/@ohos.arkui.advanced.SubHeader.d.ets|
|新增API|NA|类名：matrix4；<br>API声明：export interface Point<br>差异内容：export interface Point|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：Point；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：Point；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：matrix4；<br>API声明：export interface PolyToPolyOptions<br>差异内容：export interface PolyToPolyOptions|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：PolyToPolyOptions；<br>API声明：src: Array\<Point>;<br>差异内容：src: Array\<Point>;|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：PolyToPolyOptions；<br>API声明：srcIndex?: number;<br>差异内容：srcIndex?: number;|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：PolyToPolyOptions；<br>API声明：dst: Array\<Point>;<br>差异内容：dst: Array\<Point>;|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：PolyToPolyOptions；<br>API声明：dstIndex?: number;<br>差异内容：dstIndex?: number;|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：PolyToPolyOptions；<br>API声明：pointCount?: number;<br>差异内容：pointCount?: number;|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：Matrix4Transit；<br>API声明：skew(x: number, y: number): Matrix4Transit;<br>差异内容：skew(x: number, y: number): Matrix4Transit;|api/@ohos.matrix4.d.ts|
|新增API|NA|类名：Matrix4Transit；<br>API声明：setPolyToPoly(options: PolyToPolyOptions): Matrix4Transit;<br>差异内容：setPolyToPoly(options: PolyToPolyOptions): Matrix4Transit;|api/@ohos.matrix4.d.ts|
|成员由子类迁移至父类|类名：RichEditorController；<br>API声明：getCaretOffset(): number;<br>差异内容：getCaretOffset(): number;|类名：RichEditorBaseController；<br>API声明：getCaretOffset(): number;<br>差异内容：getCaretOffset(): number;|component/rich_editor.d.ts|
|成员由子类迁移至父类|类名：RichEditorController；<br>API声明：setCaretOffset(offset: number): boolean;<br>差异内容：setCaretOffset(offset: number): boolean;|类名：RichEditorBaseController；<br>API声明：setCaretOffset(offset: number): boolean;<br>差异内容：setCaretOffset(offset: number): boolean;|component/rich_editor.d.ts|
|成员由子类迁移至父类|类名：RichEditorController；<br>API声明：closeSelectionMenu(): void;<br>差异内容：closeSelectionMenu(): void;|类名：RichEditorBaseController；<br>API声明：closeSelectionMenu(): void;<br>差异内容：closeSelectionMenu(): void;|component/rich_editor.d.ts|
|成员由子类迁移至父类|类名：RichEditorController；<br>API声明：getTypingStyle(): RichEditorTextStyle;<br>差异内容：getTypingStyle(): RichEditorTextStyle;|类名：RichEditorBaseController；<br>API声明：getTypingStyle(): RichEditorTextStyle;<br>差异内容：getTypingStyle(): RichEditorTextStyle;|component/rich_editor.d.ts|
|成员由子类迁移至父类|类名：RichEditorController；<br>API声明：setTypingStyle(value: RichEditorTextStyle): void;<br>差异内容：setTypingStyle(value: RichEditorTextStyle): void;|类名：RichEditorBaseController；<br>API声明：setTypingStyle(value: RichEditorTextStyle): void;<br>差异内容：setTypingStyle(value: RichEditorTextStyle): void;|component/rich_editor.d.ts|
|成员由子类迁移至父类|类名：RichEditorController；<br>API声明：setSelection(selectionStart: number, selectionEnd: number): void;<br>差异内容：setSelection(selectionStart: number, selectionEnd: number): void;|类名：RichEditorBaseController；<br>API声明：setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void;<br>差异内容：setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void;|component/rich_editor.d.ts|
|起始版本有变化|类名：global；<br>API声明：declare function animateToImmediately(value: AnimateParam, event: () => void): void;<br>差异内容：11|类名：global；<br>API声明：declare function animateToImmediately(value: AnimateParam, event: () => void): void;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：BlurStyleOptions；<br>API声明：scale?: number;<br>差异内容：10|类名：BlurStyleOptions；<br>API声明：scale?: number;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：CommonMethod；<br>API声明：linearGradientBlur(value: number, options: LinearGradientBlurOptions): T;<br>差异内容：10|类名：CommonMethod；<br>API声明：linearGradientBlur(value: number, options: LinearGradientBlurOptions): T;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：CommonMethod；<br>API声明：systemBarEffect(): T;<br>差异内容：11|类名：CommonMethod；<br>API声明：systemBarEffect(): T;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：CommonMethod；<br>API声明：useEffect(value: boolean): T;<br>差异内容：10|类名：CommonMethod；<br>API声明：useEffect(value: boolean): T;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：CommonMethod；<br>API声明：key(value: string): T;<br>差异内容：8|类名：CommonMethod；<br>API声明：key(value: string): T;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：CommonMethod；<br>API声明：sphericalEffect(value: number): T;<br>差异内容：10|类名：CommonMethod；<br>API声明：sphericalEffect(value: number): T;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：CommonMethod；<br>API声明：lightUpEffect(value: number): T;<br>差异内容：10|类名：CommonMethod；<br>API声明：lightUpEffect(value: number): T;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：CommonMethod；<br>API声明：pixelStretchEffect(options: PixelStretchEffectOptions): T;<br>差异内容：10|类名：CommonMethod；<br>API声明：pixelStretchEffect(options: PixelStretchEffectOptions): T;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：CommonMethod；<br>API声明：backgroundBrightness(params: BackgroundBrightnessOptions): T;<br>差异内容：11|类名：CommonMethod；<br>API声明：backgroundBrightness(params: BackgroundBrightnessOptions): T;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：global；<br>API声明：declare type FractionStop = [ number, number ];<br>差异内容：10|类名：global；<br>API声明：declare type FractionStop = [<br>    number,<br>    number<br>];<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：global；<br>API声明：declare interface LinearGradientBlurOptions<br>差异内容：10|类名：global；<br>API声明：declare interface LinearGradientBlurOptions<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：LinearGradientBlurOptions；<br>API声明：fractionStops: FractionStop[];<br>差异内容：10|类名：LinearGradientBlurOptions；<br>API声明：fractionStops: FractionStop[];<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：LinearGradientBlurOptions；<br>API声明：direction: GradientDirection;<br>差异内容：10|类名：LinearGradientBlurOptions；<br>API声明：direction: GradientDirection;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：global；<br>API声明：declare interface BackgroundBrightnessOptions<br>差异内容：11|类名：global；<br>API声明：declare interface BackgroundBrightnessOptions<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：BackgroundBrightnessOptions；<br>API声明：rate: number;<br>差异内容：11|类名：BackgroundBrightnessOptions；<br>API声明：rate: number;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：BackgroundBrightnessOptions；<br>API声明：lightUpDegree: number;<br>差异内容：11|类名：BackgroundBrightnessOptions；<br>API声明：lightUpDegree: number;<br>差异内容：12|component/common.d.ts|
|起始版本有变化|类名：TextAreaAttribute；<br>API声明：onCopy(callback: (value: string) => void): TextAreaAttribute;<br>差异内容：7|类名：TextAreaAttribute；<br>API声明：onCopy(callback: (value: string) => void): TextAreaAttribute;<br>差异内容：8|component/text_area.d.ts|
|起始版本有变化|类名：TextAreaAttribute；<br>API声明：onCut(callback: (value: string) => void): TextAreaAttribute;<br>差异内容：7|类名：TextAreaAttribute；<br>API声明：onCut(callback: (value: string) => void): TextAreaAttribute;<br>差异内容：8|component/text_area.d.ts|
|起始版本有变化|类名：InputType；<br>API声明：USER_NAME = 10<br>差异内容：11|类名：InputType；<br>API声明：USER_NAME = 10<br>差异内容：12|component/text_input.d.ts|
|新增kit|类名：global；<br>API声明：api\@internal\full\canvaspattern.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\@internal\full\canvaspattern.d.ts<br>差异内容：ArkUI|api/@internal/full/canvaspattern.d.ts|
|新增kit|类名：global；<br>API声明：api\@internal\full\featureability.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\@internal\full\featureability.d.ts<br>差异内容：ArkUI|api/@internal/full/featureability.d.ts|
|新增kit|类名：global；<br>API声明：api\@internal\full\global.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\@internal\full\global.d.ts<br>差异内容：ArkUI|api/@internal/full/global.d.ts|
|新增kit|类名：global；<br>API声明：api\arkui\BuilderNode.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\arkui\BuilderNode.d.ts<br>差异内容：ArkUI|api/arkui/BuilderNode.d.ts|
|新增kit|类名：global；<br>API声明：api\arkui\FrameNode.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\arkui\FrameNode.d.ts<br>差异内容：ArkUI|api/arkui/FrameNode.d.ts|
|新增kit|类名：global；<br>API声明：api\arkui\Graphics.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\arkui\Graphics.d.ts<br>差异内容：ArkUI|api/arkui/Graphics.d.ts|
|新增kit|类名：global；<br>API声明：api\arkui\NodeController.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\arkui\NodeController.d.ts<br>差异内容：ArkUI|api/arkui/NodeController.d.ts|
|新增kit|类名：global；<br>API声明：api\arkui\RenderNode.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\arkui\RenderNode.d.ts<br>差异内容：ArkUI|api/arkui/RenderNode.d.ts|
|新增kit|类名：global；<br>API声明：api\arkui\XComponentNode.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\arkui\XComponentNode.d.ts<br>差异内容：ArkUI|api/arkui/XComponentNode.d.ts|
|新增kit|类名：global；<br>API声明：component\action_sheet.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\action_sheet.d.ts<br>差异内容：ArkUI|component/action_sheet.d.ts|
|新增kit|类名：global；<br>API声明：component\alert_dialog.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\alert_dialog.d.ts<br>差异内容：ArkUI|component/alert_dialog.d.ts|
|新增kit|类名：global；<br>API声明：component\alphabet_indexer.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\alphabet_indexer.d.ts<br>差异内容：ArkUI|component/alphabet_indexer.d.ts|
|新增kit|类名：global；<br>API声明：component\badge.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\badge.d.ts<br>差异内容：ArkUI|component/badge.d.ts|
|新增kit|类名：global；<br>API声明：component\blank.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\blank.d.ts<br>差异内容：ArkUI|component/blank.d.ts|
|新增kit|类名：global；<br>API声明：component\button.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\button.d.ts<br>差异内容：ArkUI|component/button.d.ts|
|新增kit|类名：global；<br>API声明：component\calendar_picker.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\calendar_picker.d.ts<br>差异内容：ArkUI|component/calendar_picker.d.ts|
|新增kit|类名：global；<br>API声明：component\canvas.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\canvas.d.ts<br>差异内容：ArkUI|component/canvas.d.ts|
|新增kit|类名：global；<br>API声明：component\checkbox.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\checkbox.d.ts<br>差异内容：ArkUI|component/checkbox.d.ts|
|新增kit|类名：global；<br>API声明：component\checkboxgroup.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\checkboxgroup.d.ts<br>差异内容：ArkUI|component/checkboxgroup.d.ts|
|新增kit|类名：global；<br>API声明：component\circle.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\circle.d.ts<br>差异内容：ArkUI|component/circle.d.ts|
|新增kit|类名：global；<br>API声明：component\column.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\column.d.ts<br>差异内容：ArkUI|component/column.d.ts|
|新增kit|类名：global；<br>API声明：component\column_split.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\column_split.d.ts<br>差异内容：ArkUI|component/column_split.d.ts|
|新增kit|类名：global；<br>API声明：component\common.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\common.d.ts<br>差异内容：ArkUI|component/common.d.ts|
|新增kit|类名：global；<br>API声明：component\common_ts_ets_api.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\common_ts_ets_api.d.ts<br>差异内容：ArkUI|component/common_ts_ets_api.d.ts|
|新增kit|类名：global；<br>API声明：component\container_span.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\container_span.d.ts<br>差异内容：ArkUI|component/container_span.d.ts|
|新增kit|类名：global；<br>API声明：component\context_menu.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\context_menu.d.ts<br>差异内容：ArkUI|component/context_menu.d.ts|
|新增kit|类名：global；<br>API声明：component\counter.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\counter.d.ts<br>差异内容：ArkUI|component/counter.d.ts|
|新增kit|类名：global；<br>API声明：component\custom_dialog_controller.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\custom_dialog_controller.d.ts<br>差异内容：ArkUI|component/custom_dialog_controller.d.ts|
|新增kit|类名：global；<br>API声明：component\data_panel.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\data_panel.d.ts<br>差异内容：ArkUI|component/data_panel.d.ts|
|新增kit|类名：global；<br>API声明：component\date_picker.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\date_picker.d.ts<br>差异内容：ArkUI|component/date_picker.d.ts|
|新增kit|类名：global；<br>API声明：component\divider.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\divider.d.ts<br>差异内容：ArkUI|component/divider.d.ts|
|新增kit|类名：global；<br>API声明：component\ellipse.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\ellipse.d.ts<br>差异内容：ArkUI|component/ellipse.d.ts|
|新增kit|类名：global；<br>API声明：component\enums.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\enums.d.ts<br>差异内容：ArkUI|component/enums.d.ts|
|新增kit|类名：global；<br>API声明：component\flex.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\flex.d.ts<br>差异内容：ArkUI|component/flex.d.ts|
|新增kit|类名：global；<br>API声明：component\flow_item.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\flow_item.d.ts<br>差异内容：ArkUI|component/flow_item.d.ts|
|新增kit|类名：global；<br>API声明：component\folder_stack.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\folder_stack.d.ts<br>差异内容：ArkUI|component/folder_stack.d.ts|
|新增kit|类名：global；<br>API声明：component\form_link.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\form_link.d.ts<br>差异内容：ArkUI|component/form_link.d.ts|
|新增kit|类名：global；<br>API声明：component\for_each.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\for_each.d.ts<br>差异内容：ArkUI|component/for_each.d.ts|
|新增kit|类名：global；<br>API声明：component\gauge.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\gauge.d.ts<br>差异内容：ArkUI|component/gauge.d.ts|
|新增kit|类名：global；<br>API声明：component\gesture.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\gesture.d.ts<br>差异内容：ArkUI|component/gesture.d.ts|
|新增kit|类名：global；<br>API声明：component\grid.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\grid.d.ts<br>差异内容：ArkUI|component/grid.d.ts|
|新增kit|类名：global；<br>API声明：component\gridItem.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\gridItem.d.ts<br>差异内容：ArkUI|component/gridItem.d.ts|
|新增kit|类名：global；<br>API声明：component\grid_col.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\grid_col.d.ts<br>差异内容：ArkUI|component/grid_col.d.ts|
|新增kit|类名：global；<br>API声明：component\grid_container.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\grid_container.d.ts<br>差异内容：ArkUI|component/grid_container.d.ts|
|新增kit|类名：global；<br>API声明：component\grid_row.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\grid_row.d.ts<br>差异内容：ArkUI|component/grid_row.d.ts|
|新增kit|类名：global；<br>API声明：component\hyperlink.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\hyperlink.d.ts<br>差异内容：ArkUI|component/hyperlink.d.ts|
|新增kit|类名：global；<br>API声明：component\image.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\image.d.ts<br>差异内容：ArkUI|component/image.d.ts|
|新增kit|类名：global；<br>API声明：component\image_animator.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\image_animator.d.ts<br>差异内容：ArkUI|component/image_animator.d.ts|
|新增kit|类名：global；<br>API声明：component\image_span.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\image_span.d.ts<br>差异内容：ArkUI|component/image_span.d.ts|
|新增kit|类名：global；<br>API声明：component\index-full.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\index-full.d.ts<br>差异内容：ArkUI|component/index-full.d.ts|
|新增kit|类名：global；<br>API声明：component\lazy_for_each.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\lazy_for_each.d.ts<br>差异内容：ArkUI|component/lazy_for_each.d.ts|
|新增kit|类名：global；<br>API声明：component\line.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\line.d.ts<br>差异内容：ArkUI|component/line.d.ts|
|新增kit|类名：global；<br>API声明：component\list.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\list.d.ts<br>差异内容：ArkUI|component/list.d.ts|
|新增kit|类名：global；<br>API声明：component\list_item.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\list_item.d.ts<br>差异内容：ArkUI|component/list_item.d.ts|
|新增kit|类名：global；<br>API声明：component\list_item_group.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\list_item_group.d.ts<br>差异内容：ArkUI|component/list_item_group.d.ts|
|新增kit|类名：global；<br>API声明：component\loading_progress.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\loading_progress.d.ts<br>差异内容：ArkUI|component/loading_progress.d.ts|
|新增kit|类名：global；<br>API声明：component\location_button.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\location_button.d.ts<br>差异内容：ArkUI|component/location_button.d.ts|
|新增kit|类名：global；<br>API声明：component\marquee.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\marquee.d.ts<br>差异内容：ArkUI|component/marquee.d.ts|
|新增kit|类名：global；<br>API声明：component\matrix2d.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\matrix2d.d.ts<br>差异内容：ArkUI|component/matrix2d.d.ts|
|新增kit|类名：global；<br>API声明：component\menu.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\menu.d.ts<br>差异内容：ArkUI|component/menu.d.ts|
|新增kit|类名：global；<br>API声明：component\menu_item.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\menu_item.d.ts<br>差异内容：ArkUI|component/menu_item.d.ts|
|新增kit|类名：global；<br>API声明：component\menu_item_group.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\menu_item_group.d.ts<br>差异内容：ArkUI|component/menu_item_group.d.ts|
|新增kit|类名：global；<br>API声明：component\navigation.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\navigation.d.ts<br>差异内容：ArkUI|component/navigation.d.ts|
|新增kit|类名：global；<br>API声明：component\navigator.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\navigator.d.ts<br>差异内容：ArkUI|component/navigator.d.ts|
|新增kit|类名：global；<br>API声明：component\nav_destination.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\nav_destination.d.ts<br>差异内容：ArkUI|component/nav_destination.d.ts|
|新增kit|类名：global；<br>API声明：component\nav_router.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\nav_router.d.ts<br>差异内容：ArkUI|component/nav_router.d.ts|
|新增kit|类名：global；<br>API声明：component\node_container.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\node_container.d.ts<br>差异内容：ArkUI|component/node_container.d.ts|
|新增kit|类名：global；<br>API声明：component\page_transition.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\page_transition.d.ts<br>差异内容：ArkUI|component/page_transition.d.ts|
|新增kit|类名：global；<br>API声明：component\panel.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\panel.d.ts<br>差异内容：ArkUI|component/panel.d.ts|
|新增kit|类名：global；<br>API声明：component\particle.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\particle.d.ts<br>差异内容：ArkUI|component/particle.d.ts|
|新增kit|类名：global；<br>API声明：component\paste_button.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\paste_button.d.ts<br>差异内容：ArkUI|component/paste_button.d.ts|
|新增kit|类名：global；<br>API声明：component\path.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\path.d.ts<br>差异内容：ArkUI|component/path.d.ts|
|新增kit|类名：global；<br>API声明：component\pattern_lock.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\pattern_lock.d.ts<br>差异内容：ArkUI|component/pattern_lock.d.ts|
|新增kit|类名：global；<br>API声明：component\polygon.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\polygon.d.ts<br>差异内容：ArkUI|component/polygon.d.ts|
|新增kit|类名：global；<br>API声明：component\polyline.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\polyline.d.ts<br>差异内容：ArkUI|component/polyline.d.ts|
|新增kit|类名：global；<br>API声明：component\progress.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\progress.d.ts<br>差异内容：ArkUI|component/progress.d.ts|
|新增kit|类名：global；<br>API声明：component\qrcode.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\qrcode.d.ts<br>差异内容：ArkUI|component/qrcode.d.ts|
|新增kit|类名：global；<br>API声明：component\radio.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\radio.d.ts<br>差异内容：ArkUI|component/radio.d.ts|
|新增kit|类名：global；<br>API声明：component\rating.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\rating.d.ts<br>差异内容：ArkUI|component/rating.d.ts|
|新增kit|类名：global；<br>API声明：component\rect.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\rect.d.ts<br>差异内容：ArkUI|component/rect.d.ts|
|新增kit|类名：global；<br>API声明：component\refresh.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\refresh.d.ts<br>差异内容：ArkUI|component/refresh.d.ts|
|新增kit|类名：global；<br>API声明：component\relative_container.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\relative_container.d.ts<br>差异内容：ArkUI|component/relative_container.d.ts|
|新增kit|类名：global；<br>API声明：component\rich_editor.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\rich_editor.d.ts<br>差异内容：ArkUI|component/rich_editor.d.ts|
|新增kit|类名：global；<br>API声明：component\rich_text.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\rich_text.d.ts<br>差异内容：ArkUI|component/rich_text.d.ts|
|新增kit|类名：global；<br>API声明：component\row.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\row.d.ts<br>差异内容：ArkUI|component/row.d.ts|
|新增kit|类名：global；<br>API声明：component\row_split.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\row_split.d.ts<br>差异内容：ArkUI|component/row_split.d.ts|
|新增kit|类名：global；<br>API声明：component\save_button.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\save_button.d.ts<br>差异内容：ArkUI|component/save_button.d.ts|
|新增kit|类名：global；<br>API声明：component\scroll.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\scroll.d.ts<br>差异内容：ArkUI|component/scroll.d.ts|
|新增kit|类名：global；<br>API声明：component\scroll_bar.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\scroll_bar.d.ts<br>差异内容：ArkUI|component/scroll_bar.d.ts|
|新增kit|类名：global；<br>API声明：component\search.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\search.d.ts<br>差异内容：ArkUI|component/search.d.ts|
|新增kit|类名：global；<br>API声明：component\security_component.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\security_component.d.ts<br>差异内容：ArkUI|component/security_component.d.ts|
|新增kit|类名：global；<br>API声明：component\select.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\select.d.ts<br>差异内容：ArkUI|component/select.d.ts|
|新增kit|类名：global；<br>API声明：component\shape.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\shape.d.ts<br>差异内容：ArkUI|component/shape.d.ts|
|新增kit|类名：global；<br>API声明：component\sidebar.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\sidebar.d.ts<br>差异内容：ArkUI|component/sidebar.d.ts|
|新增kit|类名：global；<br>API声明：component\slider.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\slider.d.ts<br>差异内容：ArkUI|component/slider.d.ts|
|新增kit|类名：global；<br>API声明：component\span.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\span.d.ts<br>差异内容：ArkUI|component/span.d.ts|
|新增kit|类名：global；<br>API声明：component\stack.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\stack.d.ts<br>差异内容：ArkUI|component/stack.d.ts|
|新增kit|类名：global；<br>API声明：component\state_management.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\state_management.d.ts<br>差异内容：ArkUI|component/state_management.d.ts|
|新增kit|类名：global；<br>API声明：component\stepper.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\stepper.d.ts<br>差异内容：ArkUI|component/stepper.d.ts|
|新增kit|类名：global；<br>API声明：component\stepper_item.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\stepper_item.d.ts<br>差异内容：ArkUI|component/stepper_item.d.ts|
|新增kit|类名：global；<br>API声明：component\swiper.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\swiper.d.ts<br>差异内容：ArkUI|component/swiper.d.ts|
|新增kit|类名：global；<br>API声明：component\symbolglyph.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\symbolglyph.d.ts<br>差异内容：ArkUI|component/symbolglyph.d.ts|
|新增kit|类名：global；<br>API声明：component\symbol_span.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\symbol_span.d.ts<br>差异内容：ArkUI|component/symbol_span.d.ts|
|新增kit|类名：global；<br>API声明：component\tabs.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\tabs.d.ts<br>差异内容：ArkUI|component/tabs.d.ts|
|新增kit|类名：global；<br>API声明：component\tab_content.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\tab_content.d.ts<br>差异内容：ArkUI|component/tab_content.d.ts|
|新增kit|类名：global；<br>API声明：component\text.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\text.d.ts<br>差异内容：ArkUI|component/text.d.ts|
|新增kit|类名：global；<br>API声明：component\text_area.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\text_area.d.ts<br>差异内容：ArkUI|component/text_area.d.ts|
|新增kit|类名：global；<br>API声明：component\text_clock.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\text_clock.d.ts<br>差异内容：ArkUI|component/text_clock.d.ts|
|新增kit|类名：global；<br>API声明：component\text_common.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\text_common.d.ts<br>差异内容：ArkUI|component/text_common.d.ts|
|新增kit|类名：global；<br>API声明：component\text_input.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\text_input.d.ts<br>差异内容：ArkUI|component/text_input.d.ts|
|新增kit|类名：global；<br>API声明：component\text_picker.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\text_picker.d.ts<br>差异内容：ArkUI|component/text_picker.d.ts|
|新增kit|类名：global；<br>API声明：component\text_timer.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\text_timer.d.ts<br>差异内容：ArkUI|component/text_timer.d.ts|
|新增kit|类名：global；<br>API声明：component\time_picker.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\time_picker.d.ts<br>差异内容：ArkUI|component/time_picker.d.ts|
|新增kit|类名：global；<br>API声明：component\toggle.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\toggle.d.ts<br>差异内容：ArkUI|component/toggle.d.ts|
|新增kit|类名：global；<br>API声明：component\units.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\units.d.ts<br>差异内容：ArkUI|component/units.d.ts|
|新增kit|类名：global；<br>API声明：component\video.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\video.d.ts<br>差异内容：ArkUI|component/video.d.ts|
|新增kit|类名：global；<br>API声明：component\water_flow.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\water_flow.d.ts<br>差异内容：ArkUI|component/water_flow.d.ts|
|新增kit|类名：global；<br>API声明：component\xcomponent.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\xcomponent.d.ts<br>差异内容：ArkUI|component/xcomponent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.advanced.ChipGroup.d.ets<br>差异内容：ArkUI|api/@ohos.arkui.advanced.ChipGroup.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.advanced.DownloadFileButton.d.ets<br>差异内容：ArkUI|api/@ohos.arkui.advanced.DownloadFileButton.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.advanced.FoldSplitContainer.d.ets<br>差异内容：ArkUI|api/@ohos.arkui.advanced.FoldSplitContainer.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.advanced.FormMenu.d.ets<br>差异内容：ArkUI|api/@ohos.arkui.advanced.FormMenu.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.advanced.FullScreenLaunchComponent.d.ets<br>差异内容：ArkUI|api/@ohos.arkui.advanced.FullScreenLaunchComponent.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.Prefetcher.d.ts<br>差异内容：ArkUI|api/@ohos.arkui.Prefetcher.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.shape.d.ts<br>差异内容：ArkUI|api/@ohos.arkui.shape.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.StateManagement.d.ts<br>差异内容：ArkUI|api/@ohos.arkui.StateManagement.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.theme.d.ts<br>差异内容：ArkUI|api/@ohos.arkui.theme.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.arkui.uiExtension.d.ts<br>差异内容：ArkUI|api/@ohos.arkui.uiExtension.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.atomicservice.AtomicServiceNavigation.d.ets<br>差异内容：ArkUI|api/@ohos.atomicservice.AtomicServiceNavigation.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.atomicservice.AtomicServiceTabs.d.ets<br>差异内容：ArkUI|api/@ohos.atomicservice.AtomicServiceTabs.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.atomicservice.AtomicServiceWeb.d.ets<br>差异内容：ArkUI|api/@ohos.atomicservice.AtomicServiceWeb.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.atomicservice.InterstitialDialogAction.d.ets<br>差异内容：ArkUI|api/@ohos.atomicservice.InterstitialDialogAction.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.atomicservice.NavPushPathHelper.d.ets<br>差异内容：ArkUI|api/@ohos.atomicservice.NavPushPathHelper.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.screenshot.d.ts<br>差异内容：ArkUI|api/@ohos.screenshot.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\AlphabetIndexerModifier.d.ts<br>差异内容：ArkUI|api/arkui/AlphabetIndexerModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\AttributeUpdater.d.ts<br>差异内容：ArkUI|api/arkui/AttributeUpdater.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\BlankModifier.d.ts<br>差异内容：ArkUI|api/arkui/BlankModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ButtonModifier.d.ts<br>差异内容：ArkUI|api/arkui/ButtonModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\CalendarPickerModifier.d.ts<br>差异内容：ArkUI|api/arkui/CalendarPickerModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\CheckboxGroupModifier.d.ts<br>差异内容：ArkUI|api/arkui/CheckboxGroupModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\CheckboxModifier.d.ts<br>差异内容：ArkUI|api/arkui/CheckboxModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ColumnModifier.d.ts<br>差异内容：ArkUI|api/arkui/ColumnModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ColumnSplitModifier.d.ts<br>差异内容：ArkUI|api/arkui/ColumnSplitModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\CommonModifier.d.ts<br>差异内容：ArkUI|api/arkui/CommonModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ComponentContent.d.ts<br>差异内容：ArkUI|api/arkui/ComponentContent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ContainerSpanModifier.d.ts<br>差异内容：ArkUI|api/arkui/ContainerSpanModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\Content.d.ts<br>差异内容：ArkUI|api/arkui/Content.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\CounterModifier.d.ts<br>差异内容：ArkUI|api/arkui/CounterModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\DataPanelModifier.d.ts<br>差异内容：ArkUI|api/arkui/DataPanelModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\DatePickerModifier.d.ts<br>差异内容：ArkUI|api/arkui/DatePickerModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\DividerModifier.d.ts<br>差异内容：ArkUI|api/arkui/DividerModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\GaugeModifier.d.ts<br>差异内容：ArkUI|api/arkui/GaugeModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\GridColModifier.d.ts<br>差异内容：ArkUI|api/arkui/GridColModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\GridItemModifier.d.ts<br>差异内容：ArkUI|api/arkui/GridItemModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\GridModifier.d.ts<br>差异内容：ArkUI|api/arkui/GridModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\GridRowModifier.d.ts<br>差异内容：ArkUI|api/arkui/GridRowModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\HyperlinkModifier.d.ts<br>差异内容：ArkUI|api/arkui/HyperlinkModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ImageAnimatorModifier.d.ts<br>差异内容：ArkUI|api/arkui/ImageAnimatorModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ImageModifier.d.ts<br>差异内容：ArkUI|api/arkui/ImageModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ImageSpanModifier.d.ts<br>差异内容：ArkUI|api/arkui/ImageSpanModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\LineModifier.d.ts<br>差异内容：ArkUI|api/arkui/LineModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ListItemGroupModifier.d.ts<br>差异内容：ArkUI|api/arkui/ListItemGroupModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ListItemModifier.d.ts<br>差异内容：ArkUI|api/arkui/ListItemModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ListModifier.d.ts<br>差异内容：ArkUI|api/arkui/ListModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\LoadingProgressModifier.d.ts<br>差异内容：ArkUI|api/arkui/LoadingProgressModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\MarqueeModifier.d.ts<br>差异内容：ArkUI|api/arkui/MarqueeModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\MenuItemModifier.d.ts<br>差异内容：ArkUI|api/arkui/MenuItemModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\MenuModifier.d.ts<br>差异内容：ArkUI|api/arkui/MenuModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\NavDestinationModifier.d.ts<br>差异内容：ArkUI|api/arkui/NavDestinationModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\NavigationModifier.d.ts<br>差异内容：ArkUI|api/arkui/NavigationModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\NavigatorModifier.d.ts<br>差异内容：ArkUI|api/arkui/NavigatorModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\NavRouterModifier.d.ts<br>差异内容：ArkUI|api/arkui/NavRouterModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\NodeContent.d.ts<br>差异内容：ArkUI|api/arkui/NodeContent.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\PanelModifier.d.ts<br>差异内容：ArkUI|api/arkui/PanelModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ParticleModifier.d.ts<br>差异内容：ArkUI|api/arkui/ParticleModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\PathModifier.d.ts<br>差异内容：ArkUI|api/arkui/PathModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\PatternLockModifier.d.ts<br>差异内容：ArkUI|api/arkui/PatternLockModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\PolygonModifier.d.ts<br>差异内容：ArkUI|api/arkui/PolygonModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\PolylineModifier.d.ts<br>差异内容：ArkUI|api/arkui/PolylineModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ProgressModifier.d.ts<br>差异内容：ArkUI|api/arkui/ProgressModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\QRCodeModifier.d.ts<br>差异内容：ArkUI|api/arkui/QRCodeModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\RadioModifier.d.ts<br>差异内容：ArkUI|api/arkui/RadioModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\RatingModifier.d.ts<br>差异内容：ArkUI|api/arkui/RatingModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\RectModifier.d.ts<br>差异内容：ArkUI|api/arkui/RectModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\RefreshModifier.d.ts<br>差异内容：ArkUI|api/arkui/RefreshModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\RichEditorModifier.d.ts<br>差异内容：ArkUI|api/arkui/RichEditorModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\RowModifier.d.ts<br>差异内容：ArkUI|api/arkui/RowModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\RowSplitModifier.d.ts<br>差异内容：ArkUI|api/arkui/RowSplitModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ScrollModifier.d.ts<br>差异内容：ArkUI|api/arkui/ScrollModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\SearchModifier.d.ts<br>差异内容：ArkUI|api/arkui/SearchModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\SelectModifier.d.ts<br>差异内容：ArkUI|api/arkui/SelectModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ShapeModifier.d.ts<br>差异内容：ArkUI|api/arkui/ShapeModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\SideBarContainerModifier.d.ts<br>差异内容：ArkUI|api/arkui/SideBarContainerModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\SliderModifier.d.ts<br>差异内容：ArkUI|api/arkui/SliderModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\SpanModifier.d.ts<br>差异内容：ArkUI|api/arkui/SpanModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\StackModifier.d.ts<br>差异内容：ArkUI|api/arkui/StackModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\StepperItemModifier.d.ts<br>差异内容：ArkUI|api/arkui/StepperItemModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\SwiperModifier.d.ts<br>差异内容：ArkUI|api/arkui/SwiperModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\SymbolGlyphModifier.d.ts<br>差异内容：ArkUI|api/arkui/SymbolGlyphModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\SymbolSpanModifier.d.ts<br>差异内容：ArkUI|api/arkui/SymbolSpanModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\TabsModifier.d.ts<br>差异内容：ArkUI|api/arkui/TabsModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\TextAreaModifier.d.ts<br>差异内容：ArkUI|api/arkui/TextAreaModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\TextClockModifier.d.ts<br>差异内容：ArkUI|api/arkui/TextClockModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\TextInputModifier.d.ts<br>差异内容：ArkUI|api/arkui/TextInputModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\TextModifier.d.ts<br>差异内容：ArkUI|api/arkui/TextModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\TextPickerModifier.d.ts<br>差异内容：ArkUI|api/arkui/TextPickerModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\TextTimerModifier.d.ts<br>差异内容：ArkUI|api/arkui/TextTimerModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\TimePickerModifier.d.ts<br>差异内容：ArkUI|api/arkui/TimePickerModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\ToggleModifier.d.ts<br>差异内容：ArkUI|api/arkui/ToggleModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\VideoModifier.d.ts<br>差异内容：ArkUI|api/arkui/VideoModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\arkui\WaterFlowModifier.d.ts<br>差异内容：ArkUI|api/arkui/WaterFlowModifier.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：component\component3d.d.ts<br>差异内容：ArkUI|component/component3d.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：component\content_slot.d.ts<br>差异内容：ArkUI|component/content_slot.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：component\embedded_component.d.ts<br>差异内容：ArkUI|component/embedded_component.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：component\focus.d.ts<br>差异内容：ArkUI|component/focus.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：component\image_common.d.ts<br>差异内容：ArkUI|component/image_common.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：component\repeat.d.ts<br>差异内容：ArkUI|component/repeat.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：component\styled_string.d.ts<br>差异内容：ArkUI|component/styled_string.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：component\with_theme.d.ts<br>差异内容：ArkUI|component/with_theme.d.ts|
|API从支持元服务到不支持元服务|类名：global；<br>API声明：interface RichTextInterface<br>差异内容：atomicservice|类名：global；<br>API声明：interface RichTextInterface<br>差异内容：NA|component/rich_text.d.ts|
|API从支持元服务到不支持元服务|类名：global；<br>API声明：declare class RichTextAttribute<br>差异内容：atomicservice|类名：global；<br>API声明：declare class RichTextAttribute<br>差异内容：NA|component/rich_text.d.ts|
|API从支持元服务到不支持元服务|类名：RichTextAttribute；<br>API声明：onStart(callback: () => void): RichTextAttribute;<br>差异内容：atomicservice|类名：RichTextAttribute；<br>API声明：onStart(callback: () => void): RichTextAttribute;<br>差异内容：NA|component/rich_text.d.ts|
|API从支持元服务到不支持元服务|类名：RichTextAttribute；<br>API声明：onComplete(callback: () => void): RichTextAttribute;<br>差异内容：atomicservice|类名：RichTextAttribute；<br>API声明：onComplete(callback: () => void): RichTextAttribute;<br>差异内容：NA|component/rich_text.d.ts|
|API从支持元服务到不支持元服务|类名：global；<br>API声明：declare const RichText: RichTextInterface;<br>差异内容：atomicservice|类名：global；<br>API声明：declare const RichText: RichTextInterface;<br>差异内容：NA|component/rich_text.d.ts|
|API从支持元服务到不支持元服务|类名：global；<br>API声明：declare const RichTextInstance: RichTextAttribute;<br>差异内容：atomicservice|类名：global；<br>API声明：declare const RichTextInstance: RichTextAttribute;<br>差异内容：NA|component/rich_text.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static assert(value?: Object, ...arguments: Object[]): void;<br>差异内容：NA|类名：console；<br>API声明：static assert(value?: Object, ...arguments: Object[]): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static count(label?: string): void;<br>差异内容：NA|类名：console；<br>API声明：static count(label?: string): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static countReset(label?: string): void;<br>差异内容：NA|类名：console；<br>API声明：static countReset(label?: string): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static dir(dir?: Object): void;<br>差异内容：NA|类名：console；<br>API声明：static dir(dir?: Object): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static dirxml(...arguments: Object[]): void;<br>差异内容：NA|类名：console；<br>API声明：static dirxml(...arguments: Object[]): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static group(...arguments: Object[]): void;<br>差异内容：NA|类名：console；<br>API声明：static group(...arguments: Object[]): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static groupCollapsed(...arguments: Object[]): void;<br>差异内容：NA|类名：console；<br>API声明：static groupCollapsed(...arguments: Object[]): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static groupEnd(): void;<br>差异内容：NA|类名：console；<br>API声明：static groupEnd(): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static table(tableData?: Object): void;<br>差异内容：NA|类名：console；<br>API声明：static table(tableData?: Object): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static time(label?: string): void;<br>差异内容：NA|类名：console；<br>API声明：static time(label?: string): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static timeEnd(label?: string): void;<br>差异内容：NA|类名：console；<br>API声明：static timeEnd(label?: string): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static timeLog(label?: string, ...arguments: Object[]): void;<br>差异内容：NA|类名：console；<br>API声明：static timeLog(label?: string, ...arguments: Object[]): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：console；<br>API声明：static trace(...arguments: Object[]): void;<br>差异内容：NA|类名：console；<br>API声明：static trace(...arguments: Object[]): void;<br>差异内容：atomicservice|api/@internal/full/global.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum NodeRenderType<br>差异内容：NA|类名：global；<br>API声明：declare enum NodeRenderType<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：NodeRenderType；<br>API声明：RENDER_TYPE_DISPLAY = 0<br>差异内容：NA|类名：NodeRenderType；<br>API声明：RENDER_TYPE_DISPLAY = 0<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：NodeRenderType；<br>API声明：RENDER_TYPE_TEXTURE = 1<br>差异内容：NA|类名：NodeRenderType；<br>API声明：RENDER_TYPE_TEXTURE = 1<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface RenderOptions<br>差异内容：NA|类名：global；<br>API声明：export interface RenderOptions<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderOptions；<br>API声明：selfIdealSize?: Size;<br>差异内容：NA|类名：RenderOptions；<br>API声明：selfIdealSize?: Size;<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderOptions；<br>API声明：type?: NodeRenderType;<br>差异内容：NA|类名：RenderOptions；<br>API声明：type?: NodeRenderType;<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderOptions；<br>API声明：surfaceId?: string;<br>差异内容：NA|类名：RenderOptions；<br>API声明：surfaceId?: string;<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export class BuilderNode<br>差异内容：NA|类名：global；<br>API声明：export class BuilderNode<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：BuilderNode；<br>API声明：build(builder: WrappedBuilder\<Args>, arg?: Object): void;<br>差异内容：NA|类名：BuilderNode；<br>API声明：build(builder: WrappedBuilder\<Args>, arg?: Object): void;<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：BuilderNode；<br>API声明：update(arg: Object): void;<br>差异内容：NA|类名：BuilderNode；<br>API声明：update(arg: Object): void;<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：BuilderNode；<br>API声明：getFrameNode(): FrameNode \| null;<br>差异内容：NA|类名：BuilderNode；<br>API声明：getFrameNode(): FrameNode \| null;<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：BuilderNode；<br>API声明：postTouchEvent(event: TouchEvent): boolean;<br>差异内容：NA|类名：BuilderNode；<br>API声明：postTouchEvent(event: TouchEvent): boolean;<br>差异内容：atomicservice|api/arkui/BuilderNode.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export class FrameNode<br>差异内容：NA|类名：global；<br>API声明：export class FrameNode<br>差异内容：atomicservice|api/arkui/FrameNode.d.ts|
|API从不支持元服务到支持元服务|类名：FrameNode；<br>API声明：getRenderNode(): RenderNode \| null;<br>差异内容：NA|类名：FrameNode；<br>API声明：getRenderNode(): RenderNode \| null;<br>差异内容：atomicservice|api/arkui/FrameNode.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface Size<br>差异内容：NA|类名：global；<br>API声明：export interface Size<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Size；<br>API声明：width: number;<br>差异内容：NA|类名：Size；<br>API声明：width: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Size；<br>API声明：height: number;<br>差异内容：NA|类名：Size；<br>API声明：height: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export class DrawContext<br>差异内容：NA|类名：global；<br>API声明：export class DrawContext<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：DrawContext；<br>API声明：get size(): Size;<br>差异内容：NA|类名：DrawContext；<br>API声明：get size(): Size;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：DrawContext；<br>API声明：get canvas(): drawing.Canvas;<br>差异内容：NA|类名：DrawContext；<br>API声明：get canvas(): drawing.Canvas;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface Vector2<br>差异内容：NA|类名：global；<br>API声明：interface Vector2<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Vector2；<br>API声明：x: number;<br>差异内容：NA|类名：Vector2；<br>API声明：x: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Vector2；<br>API声明：y: number;<br>差异内容：NA|类名：Vector2；<br>API声明：y: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface Vector3<br>差异内容：NA|类名：global；<br>API声明：interface Vector3<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Vector3；<br>API声明：x: number;<br>差异内容：NA|类名：Vector3；<br>API声明：x: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Vector3；<br>API声明：y: number;<br>差异内容：NA|类名：Vector3；<br>API声明：y: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Vector3；<br>API声明：z: number;<br>差异内容：NA|类名：Vector3；<br>API声明：z: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export type Matrix4 = [<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number<br>];<br>差异内容：NA|类名：global；<br>API声明：export type Matrix4 = [<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number,<br>    number<br>];<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export type Offset = Vector2;<br>差异内容：NA|类名：global；<br>API声明：export type Offset = Vector2;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export type Position = Vector2;<br>差异内容：NA|类名：global；<br>API声明：export type Position = Vector2;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export type Pivot = Vector2;<br>差异内容：NA|类名：global；<br>API声明：export type Pivot = Vector2;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export type Scale = Vector2;<br>差异内容：NA|类名：global；<br>API声明：export type Scale = Vector2;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export type Translation = Vector2;<br>差异内容：NA|类名：global；<br>API声明：export type Translation = Vector2;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export type Rotation = Vector3;<br>差异内容：NA|类名：global；<br>API声明：export type Rotation = Vector3;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export declare interface Frame<br>差异内容：NA|类名：global；<br>API声明：export declare interface Frame<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Frame；<br>API声明：x: number;<br>差异内容：NA|类名：Frame；<br>API声明：x: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Frame；<br>API声明：y: number;<br>差异内容：NA|类名：Frame；<br>API声明：y: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Frame；<br>API声明：width: number;<br>差异内容：NA|类名：Frame；<br>API声明：width: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：Frame；<br>API声明：height: number;<br>差异内容：NA|类名：Frame；<br>API声明：height: number;<br>差异内容：atomicservice|api/arkui/Graphics.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export abstract class NodeController<br>差异内容：NA|类名：global；<br>API声明：export abstract class NodeController<br>差异内容：atomicservice|api/arkui/NodeController.d.ts|
|API从不支持元服务到支持元服务|类名：NodeController；<br>API声明：abstract makeNode(uiContext: UIContext): FrameNode \| null;<br>差异内容：NA|类名：NodeController；<br>API声明：abstract makeNode(uiContext: UIContext): FrameNode \| null;<br>差异内容：atomicservice|api/arkui/NodeController.d.ts|
|API从不支持元服务到支持元服务|类名：NodeController；<br>API声明：aboutToResize?(size: Size): void;<br>差异内容：NA|类名：NodeController；<br>API声明：aboutToResize?(size: Size): void;<br>差异内容：atomicservice|api/arkui/NodeController.d.ts|
|API从不支持元服务到支持元服务|类名：NodeController；<br>API声明：aboutToAppear?(): void;<br>差异内容：NA|类名：NodeController；<br>API声明：aboutToAppear?(): void;<br>差异内容：atomicservice|api/arkui/NodeController.d.ts|
|API从不支持元服务到支持元服务|类名：NodeController；<br>API声明：aboutToDisappear?(): void;<br>差异内容：NA|类名：NodeController；<br>API声明：aboutToDisappear?(): void;<br>差异内容：atomicservice|api/arkui/NodeController.d.ts|
|API从不支持元服务到支持元服务|类名：NodeController；<br>API声明：rebuild(): void;<br>差异内容：NA|类名：NodeController；<br>API声明：rebuild(): void;<br>差异内容：atomicservice|api/arkui/NodeController.d.ts|
|API从不支持元服务到支持元服务|类名：NodeController；<br>API声明：onTouchEvent?(event: TouchEvent): void;<br>差异内容：NA|类名：NodeController；<br>API声明：onTouchEvent?(event: TouchEvent): void;<br>差异内容：atomicservice|api/arkui/NodeController.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export class RenderNode<br>差异内容：NA|类名：global；<br>API声明：export class RenderNode<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：appendChild(node: RenderNode): void;<br>差异内容：NA|类名：RenderNode；<br>API声明：appendChild(node: RenderNode): void;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：insertChildAfter(child: RenderNode, sibling: RenderNode \| null): void;<br>差异内容：NA|类名：RenderNode；<br>API声明：insertChildAfter(child: RenderNode, sibling: RenderNode \| null): void;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：removeChild(node: RenderNode): void;<br>差异内容：NA|类名：RenderNode；<br>API声明：removeChild(node: RenderNode): void;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：clearChildren(): void;<br>差异内容：NA|类名：RenderNode；<br>API声明：clearChildren(): void;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：getChild(index: number): RenderNode \| null;<br>差异内容：NA|类名：RenderNode；<br>API声明：getChild(index: number): RenderNode \| null;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：getFirstChild(): RenderNode \| null;<br>差异内容：NA|类名：RenderNode；<br>API声明：getFirstChild(): RenderNode \| null;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：getNextSibling(): RenderNode \| null;<br>差异内容：NA|类名：RenderNode；<br>API声明：getNextSibling(): RenderNode \| null;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：getPreviousSibling(): RenderNode \| null;<br>差异内容：NA|类名：RenderNode；<br>API声明：getPreviousSibling(): RenderNode \| null;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get backgroundColor(): number;<br>差异内容：NA|类名：RenderNode；<br>API声明：get backgroundColor(): number;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get clipToFrame(): boolean;<br>差异内容：NA|类名：RenderNode；<br>API声明：get clipToFrame(): boolean;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get opacity(): number;<br>差异内容：NA|类名：RenderNode；<br>API声明：get opacity(): number;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get size(): Size;<br>差异内容：NA|类名：RenderNode；<br>API声明：get size(): Size;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get position(): Position;<br>差异内容：NA|类名：RenderNode；<br>API声明：get position(): Position;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get frame(): Frame;<br>差异内容：NA|类名：RenderNode；<br>API声明：get frame(): Frame;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get pivot(): Pivot;<br>差异内容：NA|类名：RenderNode；<br>API声明：get pivot(): Pivot;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get scale(): Scale;<br>差异内容：NA|类名：RenderNode；<br>API声明：get scale(): Scale;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get translation(): Translation;<br>差异内容：NA|类名：RenderNode；<br>API声明：get translation(): Translation;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get rotation(): Rotation;<br>差异内容：NA|类名：RenderNode；<br>API声明：get rotation(): Rotation;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get transform(): Matrix4;<br>差异内容：NA|类名：RenderNode；<br>API声明：get transform(): Matrix4;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get shadowColor(): number;<br>差异内容：NA|类名：RenderNode；<br>API声明：get shadowColor(): number;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get shadowOffset(): Offset;<br>差异内容：NA|类名：RenderNode；<br>API声明：get shadowOffset(): Offset;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get shadowAlpha(): number;<br>差异内容：NA|类名：RenderNode；<br>API声明：get shadowAlpha(): number;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get shadowElevation(): number;<br>差异内容：NA|类名：RenderNode；<br>API声明：get shadowElevation(): number;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：get shadowRadius(): number;<br>差异内容：NA|类名：RenderNode；<br>API声明：get shadowRadius(): number;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：draw(context: DrawContext): void;<br>差异内容：NA|类名：RenderNode；<br>API声明：draw(context: DrawContext): void;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：RenderNode；<br>API声明：invalidate(): void;<br>差异内容：NA|类名：RenderNode；<br>API声明：invalidate(): void;<br>差异内容：atomicservice|api/arkui/RenderNode.d.ts|
|API从不支持元服务到支持元服务|类名：ActionSheetOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：NA|类名：ActionSheetOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：atomicservice|component/action_sheet.d.ts|
|API从不支持元服务到支持元服务|类名：ActionSheetOptions；<br>API声明：isModal?: boolean;<br>差异内容：NA|类名：ActionSheetOptions；<br>API声明：isModal?: boolean;<br>差异内容：atomicservice|component/action_sheet.d.ts|
|API从不支持元服务到支持元服务|类名：ActionSheetOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：NA|类名：ActionSheetOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：atomicservice|component/action_sheet.d.ts|
|API从不支持元服务到支持元服务|类名：ActionSheetOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：ActionSheetOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|component/action_sheet.d.ts|
|API从不支持元服务到支持元服务|类名：AlertDialogParam；<br>API声明：showInSubWindow?: boolean;<br>差异内容：NA|类名：AlertDialogParam；<br>API声明：showInSubWindow?: boolean;<br>差异内容：atomicservice|component/alert_dialog.d.ts|
|API从不支持元服务到支持元服务|类名：AlertDialogParam；<br>API声明：isModal?: boolean;<br>差异内容：NA|类名：AlertDialogParam；<br>API声明：isModal?: boolean;<br>差异内容：atomicservice|component/alert_dialog.d.ts|
|API从不支持元服务到支持元服务|类名：AlertDialogParam；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：NA|类名：AlertDialogParam；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：atomicservice|component/alert_dialog.d.ts|
|API从不支持元服务到支持元服务|类名：AlertDialogParam；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：AlertDialogParam；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|component/alert_dialog.d.ts|
|API从不支持元服务到支持元服务|类名：AlphabetIndexerAttribute；<br>API声明：autoCollapse(value: boolean): AlphabetIndexerAttribute;<br>差异内容：NA|类名：AlphabetIndexerAttribute；<br>API声明：autoCollapse(value: boolean): AlphabetIndexerAttribute;<br>差异内容：atomicservice|component/alphabet_indexer.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum ButtonStyleMode<br>差异内容：NA|类名：global；<br>API声明：declare enum ButtonStyleMode<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：ButtonStyleMode；<br>API声明：NORMAL = 0<br>差异内容：NA|类名：ButtonStyleMode；<br>API声明：NORMAL = 0<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：ButtonStyleMode；<br>API声明：EMPHASIZED = 1<br>差异内容：NA|类名：ButtonStyleMode；<br>API声明：EMPHASIZED = 1<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：ButtonStyleMode；<br>API声明：TEXTUAL = 2<br>差异内容：NA|类名：ButtonStyleMode；<br>API声明：TEXTUAL = 2<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum ControlSize<br>差异内容：NA|类名：global；<br>API声明：declare enum ControlSize<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：ControlSize；<br>API声明：SMALL = 'small'<br>差异内容：NA|类名：ControlSize；<br>API声明：SMALL = 'small'<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：ControlSize；<br>API声明：NORMAL = 'normal'<br>差异内容：NA|类名：ControlSize；<br>API声明：NORMAL = 'normal'<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：ButtonOptions；<br>API声明：buttonStyle?: ButtonStyleMode;<br>差异内容：NA|类名：ButtonOptions；<br>API声明：buttonStyle?: ButtonStyleMode;<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：ButtonOptions；<br>API声明：controlSize?: ControlSize;<br>差异内容：NA|类名：ButtonOptions；<br>API声明：controlSize?: ControlSize;<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：ButtonAttribute；<br>API声明：buttonStyle(value: ButtonStyleMode): ButtonAttribute;<br>差异内容：NA|类名：ButtonAttribute；<br>API声明：buttonStyle(value: ButtonStyleMode): ButtonAttribute;<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：ButtonAttribute；<br>API声明：controlSize(value: ControlSize): ButtonAttribute;<br>差异内容：NA|类名：ButtonAttribute；<br>API声明：controlSize(value: ControlSize): ButtonAttribute;<br>差异内容：atomicservice|component/button.d.ts|
|API从不支持元服务到支持元服务|类名：CalendarDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：NA|类名：CalendarDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：atomicservice|component/calendar_picker.d.ts|
|API从不支持元服务到支持元服务|类名：CalendarDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：CalendarDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|component/calendar_picker.d.ts|
|API从不支持元服务到支持元服务|类名：CheckboxAttribute；<br>API声明：shape(value: CheckBoxShape): CheckboxAttribute;<br>差异内容：NA|类名：CheckboxAttribute；<br>API声明：shape(value: CheckBoxShape): CheckboxAttribute;<br>差异内容：atomicservice|component/checkbox.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface ComponentOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface ComponentOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ComponentOptions；<br>API声明：freezeWhenInactive : boolean,<br>差异内容：NA|类名：ComponentOptions；<br>API声明：freezeWhenInactive: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface InputCounterOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface InputCounterOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：InputCounterOptions；<br>API声明：thresholdPercentage?: number;<br>差异内容：NA|类名：InputCounterOptions；<br>API声明：thresholdPercentage?: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：InputCounterOptions；<br>API声明：highlightBorder?: boolean;<br>差异内容：NA|类名：InputCounterOptions；<br>API声明：highlightBorder?: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const Track: PropertyDecorator;<br>差异内容：NA|类名：global；<br>API声明：declare const Track: PropertyDecorator;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface ExpectedFrameRateRange<br>差异内容：NA|类名：global；<br>API声明：declare interface ExpectedFrameRateRange<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ExpectedFrameRateRange；<br>API声明：min: number,<br>差异内容：NA|类名：ExpectedFrameRateRange；<br>API声明：min: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ExpectedFrameRateRange；<br>API声明：max: number,<br>差异内容：NA|类名：ExpectedFrameRateRange；<br>API声明：max: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ExpectedFrameRateRange；<br>API声明：expected: number,<br>差异内容：NA|类名：ExpectedFrameRateRange；<br>API声明：expected: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum FinishCallbackType<br>差异内容：NA|类名：global；<br>API声明：declare enum FinishCallbackType<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：FinishCallbackType；<br>API声明：REMOVED = 0<br>差异内容：NA|类名：FinishCallbackType；<br>API声明：REMOVED = 0<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：FinishCallbackType；<br>API声明：LOGICALLY = 1<br>差异内容：NA|类名：FinishCallbackType；<br>API声明：LOGICALLY = 1<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum TouchTestStrategy<br>差异内容：NA|类名：global；<br>API声明：declare enum TouchTestStrategy<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestStrategy；<br>API声明：DEFAULT = 0<br>差异内容：NA|类名：TouchTestStrategy；<br>API声明：DEFAULT = 0<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestStrategy；<br>API声明：FORWARD_COMPETITION = 1<br>差异内容：NA|类名：TouchTestStrategy；<br>API声明：FORWARD_COMPETITION = 1<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestStrategy；<br>API声明：FORWARD = 2<br>差异内容：NA|类名：TouchTestStrategy；<br>API声明：FORWARD = 2<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：AnimateParam；<br>API声明：finishCallbackType?: FinishCallbackType;<br>差异内容：NA|类名：AnimateParam；<br>API声明：finishCallbackType?: FinishCallbackType;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：AnimateParam；<br>API声明：expectedFrameRateRange?: ExpectedFrameRateRange;<br>差异内容：NA|类名：AnimateParam；<br>API声明：expectedFrameRateRange?: ExpectedFrameRateRange;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface GeometryTransitionOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface GeometryTransitionOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：GeometryTransitionOptions；<br>API声明：follow?: boolean;<br>差异内容：NA|类名：GeometryTransitionOptions；<br>API声明：follow?: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：AlignRuleOption；<br>API声明：bias?: Bias;<br>差异内容：NA|类名：AlignRuleOption；<br>API声明：bias?: Bias;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare function animateToImmediately(value: AnimateParam, event: () => void): void;<br>差异内容：NA|类名：global；<br>API声明：declare function animateToImmediately(value: AnimateParam, event: () => void): void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type PointerStyle = import('../api/@ohos.multimodalInput.pointer').default.PointerStyle;<br>差异内容：NA|类名：global；<br>API声明：declare type PointerStyle = import('../api/@ohos.multimodalInput.pointer').default.PointerStyle;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace cursorControl<br>差异内容：NA|类名：global；<br>API声明：declare namespace cursorControl<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：cursorControl；<br>API声明：function setCursor(value: PointerStyle): void;<br>差异内容：NA|类名：cursorControl；<br>API声明：function setCursor(value: PointerStyle): void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：cursorControl；<br>API声明：function restoreDefault(): void;<br>差异内容：NA|类名：cursorControl；<br>API声明：function restoreDefault(): void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlurStyle；<br>API声明：COMPONENT_ULTRA_THIN = 8<br>差异内容：NA|类名：BlurStyle；<br>API声明：COMPONENT_ULTRA_THIN = 8<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlurStyle；<br>API声明：COMPONENT_THIN = 9<br>差异内容：NA|类名：BlurStyle；<br>API声明：COMPONENT_THIN = 9<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlurStyle；<br>API声明：COMPONENT_REGULAR = 10<br>差异内容：NA|类名：BlurStyle；<br>API声明：COMPONENT_REGULAR = 10<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlurStyle；<br>API声明：COMPONENT_THICK = 11<br>差异内容：NA|类名：BlurStyle；<br>API声明：COMPONENT_THICK = 11<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlurStyle；<br>API声明：COMPONENT_ULTRA_THICK = 12<br>差异内容：NA|类名：BlurStyle；<br>API声明：COMPONENT_ULTRA_THICK = 12<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface BlurOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface BlurOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlurOptions；<br>API声明：grayscale: [number, number];<br>差异内容：NA|类名：BlurOptions；<br>API声明：grayscale: [<br>        number,<br>        number<br>    ];<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlurStyleOptions；<br>API声明：scale?: number;<br>差异内容：NA|类名：BlurStyleOptions；<br>API声明：scale?: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlurStyleOptions；<br>API声明：blurOptions?: BlurOptions;<br>差异内容：NA|类名：BlurStyleOptions；<br>API声明：blurOptions?: BlurOptions;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface BackgroundEffectOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface BackgroundEffectOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BackgroundEffectOptions；<br>API声明：radius: number;<br>差异内容：NA|类名：BackgroundEffectOptions；<br>API声明：radius: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BackgroundEffectOptions；<br>API声明：saturation?: number;<br>差异内容：NA|类名：BackgroundEffectOptions；<br>API声明：saturation?: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BackgroundEffectOptions；<br>API声明：brightness?: number;<br>差异内容：NA|类名：BackgroundEffectOptions；<br>API声明：brightness?: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BackgroundEffectOptions；<br>API声明：color?: ResourceColor;<br>差异内容：NA|类名：BackgroundEffectOptions；<br>API声明：color?: ResourceColor;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BackgroundEffectOptions；<br>API声明：adaptiveColor?: AdaptiveColor;<br>差异内容：NA|类名：BackgroundEffectOptions；<br>API声明：adaptiveColor?: AdaptiveColor;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BackgroundEffectOptions；<br>API声明：blurOptions?: BlurOptions;<br>差异内容：NA|类名：BackgroundEffectOptions；<br>API声明：blurOptions?: BlurOptions;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ShadowOptions；<br>API声明：fill?: boolean;<br>差异内容：NA|类名：ShadowOptions；<br>API声明：fill?: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetSize；<br>API声明：FIT_CONTENT = 2<br>差异内容：NA|类名：SheetSize；<br>API声明：FIT_CONTENT = 2<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum BlendMode<br>差异内容：NA|类名：global；<br>API声明：declare enum BlendMode<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：NONE = 0<br>差异内容：NA|类名：BlendMode；<br>API声明：NONE = 0<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：CLEAR = 1<br>差异内容：NA|类名：BlendMode；<br>API声明：CLEAR = 1<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：SRC = 2<br>差异内容：NA|类名：BlendMode；<br>API声明：SRC = 2<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：DST = 3<br>差异内容：NA|类名：BlendMode；<br>API声明：DST = 3<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：SRC_OVER = 4<br>差异内容：NA|类名：BlendMode；<br>API声明：SRC_OVER = 4<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：DST_OVER = 5<br>差异内容：NA|类名：BlendMode；<br>API声明：DST_OVER = 5<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：SRC_IN = 6<br>差异内容：NA|类名：BlendMode；<br>API声明：SRC_IN = 6<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：DST_IN = 7<br>差异内容：NA|类名：BlendMode；<br>API声明：DST_IN = 7<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：SRC_OUT = 8<br>差异内容：NA|类名：BlendMode；<br>API声明：SRC_OUT = 8<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：DST_OUT = 9<br>差异内容：NA|类名：BlendMode；<br>API声明：DST_OUT = 9<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：SRC_ATOP = 10<br>差异内容：NA|类名：BlendMode；<br>API声明：SRC_ATOP = 10<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：DST_ATOP = 11<br>差异内容：NA|类名：BlendMode；<br>API声明：DST_ATOP = 11<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：XOR = 12<br>差异内容：NA|类名：BlendMode；<br>API声明：XOR = 12<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：PLUS = 13<br>差异内容：NA|类名：BlendMode；<br>API声明：PLUS = 13<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：MODULATE = 14<br>差异内容：NA|类名：BlendMode；<br>API声明：MODULATE = 14<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：SCREEN = 15<br>差异内容：NA|类名：BlendMode；<br>API声明：SCREEN = 15<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：OVERLAY = 16<br>差异内容：NA|类名：BlendMode；<br>API声明：OVERLAY = 16<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：DARKEN = 17<br>差异内容：NA|类名：BlendMode；<br>API声明：DARKEN = 17<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：LIGHTEN = 18<br>差异内容：NA|类名：BlendMode；<br>API声明：LIGHTEN = 18<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：COLOR_DODGE = 19<br>差异内容：NA|类名：BlendMode；<br>API声明：COLOR_DODGE = 19<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：COLOR_BURN = 20<br>差异内容：NA|类名：BlendMode；<br>API声明：COLOR_BURN = 20<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：HARD_LIGHT = 21<br>差异内容：NA|类名：BlendMode；<br>API声明：HARD_LIGHT = 21<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：SOFT_LIGHT = 22<br>差异内容：NA|类名：BlendMode；<br>API声明：SOFT_LIGHT = 22<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：DIFFERENCE = 23<br>差异内容：NA|类名：BlendMode；<br>API声明：DIFFERENCE = 23<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：EXCLUSION = 24<br>差异内容：NA|类名：BlendMode；<br>API声明：EXCLUSION = 24<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：MULTIPLY = 25<br>差异内容：NA|类名：BlendMode；<br>API声明：MULTIPLY = 25<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：HUE = 26<br>差异内容：NA|类名：BlendMode；<br>API声明：HUE = 26<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：SATURATION = 27<br>差异内容：NA|类名：BlendMode；<br>API声明：SATURATION = 27<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：COLOR = 28<br>差异内容：NA|类名：BlendMode；<br>API声明：COLOR = 28<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendMode；<br>API声明：LUMINOSITY = 29<br>差异内容：NA|类名：BlendMode；<br>API声明：LUMINOSITY = 29<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum BlendApplyType<br>差异内容：NA|类名：global；<br>API声明：declare enum BlendApplyType<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendApplyType；<br>API声明：FAST = 0<br>差异内容：NA|类名：BlendApplyType；<br>API声明：FAST = 0<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BlendApplyType；<br>API声明：OFFSCREEN = 1<br>差异内容：NA|类名：BlendApplyType；<br>API声明：OFFSCREEN = 1<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface SheetTitleOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface SheetTitleOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetTitleOptions；<br>API声明：title: ResourceStr;<br>差异内容：NA|类名：SheetTitleOptions；<br>API声明：title: ResourceStr;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetTitleOptions；<br>API声明：subtitle?: ResourceStr;<br>差异内容：NA|类名：SheetTitleOptions；<br>API声明：subtitle?: ResourceStr;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum SheetType<br>差异内容：NA|类名：global；<br>API声明：declare enum SheetType<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetType；<br>API声明：BOTTOM = 0<br>差异内容：NA|类名：SheetType；<br>API声明：BOTTOM = 0<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetType；<br>API声明：CENTER = 1<br>差异内容：NA|类名：SheetType；<br>API声明：CENTER = 1<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetType；<br>API声明：POPUP = 2<br>差异内容：NA|类名：SheetType；<br>API声明：POPUP = 2<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface SheetDismiss<br>差异内容：NA|类名：global；<br>API声明：declare interface SheetDismiss<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetDismiss；<br>API声明：dismiss: () => void;<br>差异内容：NA|类名：SheetDismiss；<br>API声明：dismiss: () => void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetOptions；<br>API声明：detents?: [(SheetSize \| Length), (SheetSize \| Length)?, (SheetSize \| Length)?];<br>差异内容：NA|类名：SheetOptions；<br>API声明：detents?: [<br>        (SheetSize \| Length),<br>        (SheetSize \| Length)?,<br>        (SheetSize \| Length)?<br>    ];<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetOptions；<br>API声明：blurStyle?: BlurStyle;<br>差异内容：NA|类名：SheetOptions；<br>API声明：blurStyle?: BlurStyle;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetOptions；<br>API声明：showClose?: boolean \| Resource;<br>差异内容：NA|类名：SheetOptions；<br>API声明：showClose?: boolean \| Resource;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetOptions；<br>API声明：preferType?: SheetType.CENTER \| SheetType.POPUP;<br>差异内容：NA|类名：SheetOptions；<br>API声明：preferType?: SheetType;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetOptions；<br>API声明：title?: SheetTitleOptions \| CustomBuilder;<br>差异内容：NA|类名：SheetOptions；<br>API声明：title?: SheetTitleOptions \| CustomBuilder;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetOptions；<br>API声明：shouldDismiss?: (sheetDismiss: SheetDismiss) => void;<br>差异内容：NA|类名：SheetOptions；<br>API声明：shouldDismiss?: (sheetDismiss: SheetDismiss) => void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：SheetOptions；<br>API声明：enableOutsideInteractive?: boolean;<br>差异内容：NA|类名：SheetOptions；<br>API声明：enableOutsideInteractive?: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：popupColor?: Color \| string \| Resource \| number;<br>差异内容：NA|类名：PopupOptions；<br>API声明：popupColor?: Color \| string \| Resource \| number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：autoCancel?: boolean;<br>差异内容：NA|类名：PopupOptions；<br>API声明：autoCancel?: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：width?: Dimension;<br>差异内容：NA|类名：PopupOptions；<br>API声明：width?: Dimension;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：arrowPointPosition?: ArrowPointPosition;<br>差异内容：NA|类名：PopupOptions；<br>API声明：arrowPointPosition?: ArrowPointPosition;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：arrowWidth?: Dimension;<br>差异内容：NA|类名：PopupOptions；<br>API声明：arrowWidth?: Dimension;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：arrowHeight?: Dimension;<br>差异内容：NA|类名：PopupOptions；<br>API声明：arrowHeight?: Dimension;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：radius?: Dimension;<br>差异内容：NA|类名：PopupOptions；<br>API声明：radius?: Dimension;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：NA|类名：PopupOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：PopupOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomPopupOptions；<br>API声明：width?: Dimension;<br>差异内容：NA|类名：CustomPopupOptions；<br>API声明：width?: Dimension;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomPopupOptions；<br>API声明：arrowPointPosition?: ArrowPointPosition;<br>差异内容：NA|类名：CustomPopupOptions；<br>API声明：arrowPointPosition?: ArrowPointPosition;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomPopupOptions；<br>API声明：arrowWidth?: Dimension;<br>差异内容：NA|类名：CustomPopupOptions；<br>API声明：arrowWidth?: Dimension;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomPopupOptions；<br>API声明：arrowHeight?: Dimension;<br>差异内容：NA|类名：CustomPopupOptions；<br>API声明：arrowHeight?: Dimension;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomPopupOptions；<br>API声明：radius?: Dimension;<br>差异内容：NA|类名：CustomPopupOptions；<br>API声明：radius?: Dimension;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomPopupOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：NA|类名：CustomPopupOptions；<br>API声明：shadow?: ShadowOptions \| ShadowStyle;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomPopupOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：CustomPopupOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomPopupOptions；<br>API声明：focusable?: boolean;<br>差异内容：NA|类名：CustomPopupOptions；<br>API声明：focusable?: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum MenuPreviewMode<br>差异内容：NA|类名：global；<br>API声明：declare enum MenuPreviewMode<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：MenuPreviewMode；<br>API声明：NONE = 0<br>差异内容：NA|类名：MenuPreviewMode；<br>API声明：NONE = 0<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：MenuPreviewMode；<br>API声明：IMAGE = 1<br>差异内容：NA|类名：MenuPreviewMode；<br>API声明：IMAGE = 1<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type AnimationRange\<T> = [from: T, to: T];<br>差异内容：NA|类名：global；<br>API声明：declare type AnimationRange\<T> = [<br>    from: T,<br>    to: T<br>];<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface ContextMenuAnimationOptions<br>差异内容：NA|类名：global；<br>API声明：interface ContextMenuAnimationOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ContextMenuAnimationOptions；<br>API声明：scale?: AnimationRange\<number>;<br>差异内容：NA|类名：ContextMenuAnimationOptions；<br>API声明：scale?: AnimationRange\<number>;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ContextMenuOptions；<br>API声明：preview?: MenuPreviewMode \| CustomBuilder;<br>差异内容：NA|类名：ContextMenuOptions；<br>API声明：preview?: MenuPreviewMode \| CustomBuilder;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ContextMenuOptions；<br>API声明：aboutToAppear?: () => void;<br>差异内容：NA|类名：ContextMenuOptions；<br>API声明：aboutToAppear?: () => void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ContextMenuOptions；<br>API声明：aboutToDisappear?: () => void;<br>差异内容：NA|类名：ContextMenuOptions；<br>API声明：aboutToDisappear?: () => void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ContextMenuOptions；<br>API声明：previewAnimationOptions?: ContextMenuAnimationOptions;<br>差异内容：NA|类名：ContextMenuOptions；<br>API声明：previewAnimationOptions?: ContextMenuAnimationOptions;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ContextMenuOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：NA|类名：ContextMenuOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：ContextMenuOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：ContextMenuOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：MenuOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：NA|类名：MenuOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class TouchTestInfo<br>差异内容：NA|类名：global；<br>API声明：declare class TouchTestInfo<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestInfo；<br>API声明：windowX: number;<br>差异内容：NA|类名：TouchTestInfo；<br>API声明：windowX: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestInfo；<br>API声明：windowY: number;<br>差异内容：NA|类名：TouchTestInfo；<br>API声明：windowY: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestInfo；<br>API声明：parentX: number;<br>差异内容：NA|类名：TouchTestInfo；<br>API声明：parentX: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestInfo；<br>API声明：parentY: number;<br>差异内容：NA|类名：TouchTestInfo；<br>API声明：parentY: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestInfo；<br>API声明：x: number;<br>差异内容：NA|类名：TouchTestInfo；<br>API声明：x: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestInfo；<br>API声明：y: number;<br>差异内容：NA|类名：TouchTestInfo；<br>API声明：y: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestInfo；<br>API声明：rect: RectResult;<br>差异内容：NA|类名：TouchTestInfo；<br>API声明：rect: RectResult;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchTestInfo；<br>API声明：id: string;<br>差异内容：NA|类名：TouchTestInfo；<br>API声明：id: string;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class TouchResult<br>差异内容：NA|类名：global；<br>API声明：declare class TouchResult<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchResult；<br>API声明：strategy: TouchTestStrategy;<br>差异内容：NA|类名：TouchResult；<br>API声明：strategy: TouchTestStrategy;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TouchResult；<br>API声明：id?: string;<br>差异内容：NA|类名：TouchResult；<br>API声明：id?: string;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：MenuElement；<br>API声明：enabled?: boolean;<br>差异内容：NA|类名：MenuElement；<br>API声明：enabled?: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface AttributeModifier<br>差异内容：NA|类名：global；<br>API声明：declare interface AttributeModifier<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：AttributeModifier；<br>API声明：applyNormalAttribute?(instance: T) : void;<br>差异内容：NA|类名：AttributeModifier；<br>API声明：applyNormalAttribute?(instance: T): void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：AttributeModifier；<br>API声明：applyPressedAttribute?(instance: T) : void;<br>差异内容：NA|类名：AttributeModifier；<br>API声明：applyPressedAttribute?(instance: T): void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：AttributeModifier；<br>API声明：applyFocusedAttribute?(instance: T) : void;<br>差异内容：NA|类名：AttributeModifier；<br>API声明：applyFocusedAttribute?(instance: T): void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：AttributeModifier；<br>API声明：applyDisabledAttribute?(instance: T) : void;<br>差异内容：NA|类名：AttributeModifier；<br>API声明：applyDisabledAttribute?(instance: T): void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：AttributeModifier；<br>API声明：applySelectedAttribute?(instance: T) : void;<br>差异内容：NA|类名：AttributeModifier；<br>API声明：applySelectedAttribute?(instance: T): void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum OutlineStyle<br>差异内容：NA|类名：global；<br>API声明：declare enum OutlineStyle<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineStyle；<br>API声明：SOLID = 0<br>差异内容：NA|类名：OutlineStyle；<br>API声明：SOLID = 0<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineStyle；<br>API声明：DASHED = 1<br>差异内容：NA|类名：OutlineStyle；<br>API声明：DASHED = 1<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineStyle；<br>API声明：DOTTED = 2<br>差异内容：NA|类名：OutlineStyle；<br>API声明：DOTTED = 2<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum DragPreviewMode<br>差异内容：NA|类名：global；<br>API声明：declare enum DragPreviewMode<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：DragPreviewMode；<br>API声明：AUTO = 1<br>差异内容：NA|类名：DragPreviewMode；<br>API声明：AUTO = 1<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：DragPreviewMode；<br>API声明：DISABLE_SCALE = 2<br>差异内容：NA|类名：DragPreviewMode；<br>API声明：DISABLE_SCALE = 2<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface DragPreviewOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface DragPreviewOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：DragPreviewOptions；<br>API声明：mode?: DragPreviewMode;<br>差异内容：NA|类名：DragPreviewOptions；<br>API声明：mode?: DragPreviewMode \| Array\<DragPreviewMode>;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface InvertOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface InvertOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：InvertOptions；<br>API声明：low: number;<br>差异内容：NA|类名：InvertOptions；<br>API声明：low: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：InvertOptions；<br>API声明：high: number;<br>差异内容：NA|类名：InvertOptions；<br>API声明：high: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：InvertOptions；<br>API声明：threshold: number;<br>差异内容：NA|类名：InvertOptions；<br>API声明：threshold: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：InvertOptions；<br>API声明：thresholdRange: number;<br>差异内容：NA|类名：InvertOptions；<br>API声明：thresholdRange: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：onChildTouchTest(event: (value: Array\<TouchTestInfo>) => TouchResult): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：onChildTouchTest(event: (value: Array\<TouchTestInfo>) => TouchResult): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：backgroundEffect(options: BackgroundEffectOptions): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：backgroundEffect(options: BackgroundEffectOptions): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：outline(value: OutlineOptions): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：outline(value: OutlineOptions): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：outlineStyle(value: OutlineStyle \| EdgeOutlineStyles): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：outlineStyle(value: OutlineStyle \| EdgeOutlineStyles): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：outlineWidth(value: Dimension \| EdgeOutlineWidths): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：outlineWidth(value: Dimension \| EdgeOutlineWidths): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：outlineColor(value: ResourceColor \| EdgeColors): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：outlineColor(value: ResourceColor \| EdgeColors \| LocalizedEdgeColors): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：outlineRadius(value: Dimension \| OutlineRadiuses): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：outlineRadius(value: Dimension \| OutlineRadiuses): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：linearGradientBlur(value: number, options: LinearGradientBlurOptions): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：linearGradientBlur(value: number, options: LinearGradientBlurOptions): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：systemBarEffect(): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：systemBarEffect(): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：useShadowBatching(value: boolean): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：useShadowBatching(value: boolean): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：useEffect(value: boolean): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：useEffect(value: boolean): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：dragPreview(value: CustomBuilder \| DragItemInfo): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：dragPreview(value: CustomBuilder \| DragItemInfo \| string): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：dragPreviewOptions(value: DragPreviewOptions): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：dragPreviewOptions(value: DragPreviewOptions, options?: DragInteractionOptions): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：blendMode(value: BlendMode, type?: BlendApplyType): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：blendMode(value: BlendMode, type?: BlendApplyType): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：key(value: string): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：key(value: string): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：geometryTransition(id: string, options?: GeometryTransitionOptions): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：geometryTransition(id: string, options?: GeometryTransitionOptions): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：bindMenu(isShow: boolean, content: Array\<MenuElement> \| CustomBuilder, options?: MenuOptions): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：bindMenu(isShow: boolean, content: Array\<MenuElement> \| CustomBuilder, options?: MenuOptions): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：sphericalEffect(value: number): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：sphericalEffect(value: number): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：lightUpEffect(value: number): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：lightUpEffect(value: number): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：pixelStretchEffect(options: PixelStretchEffectOptions): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：pixelStretchEffect(options: PixelStretchEffectOptions): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：attributeModifier(modifier: AttributeModifier\<T>): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：attributeModifier(modifier: AttributeModifier\<T>): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：backgroundBrightness(params: BackgroundBrightnessOptions): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：backgroundBrightness(params: BackgroundBrightnessOptions): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：onGestureJudgeBegin(callback: (gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：onGestureJudgeBegin(callback: (gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CommonMethod；<br>API声明：monopolizeEvents(monopolize: boolean): T;<br>差异内容：NA|类名：CommonMethod；<br>API声明：monopolizeEvents(monopolize: boolean): T;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type FractionStop = [ number, number ];<br>差异内容：NA|类名：global；<br>API声明：declare type FractionStop = [<br>    number,<br>    number<br>];<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface LinearGradientBlurOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface LinearGradientBlurOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：LinearGradientBlurOptions；<br>API声明：fractionStops: FractionStop[];<br>差异内容：NA|类名：LinearGradientBlurOptions；<br>API声明：fractionStops: FractionStop[];<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：LinearGradientBlurOptions；<br>API声明：direction: GradientDirection;<br>差异内容：NA|类名：LinearGradientBlurOptions；<br>API声明：direction: GradientDirection;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type NavDestinationInfo = import('../api/@ohos.arkui.observer').default.NavDestinationInfo;<br>差异内容：NA|类名：global；<br>API声明：declare type NavDestinationInfo = import('../api/@ohos.arkui.observer').default.NavDestinationInfo;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type UIContext = import('../api/@ohos.arkui.UIContext').UIContext;<br>差异内容：NA|类名：global；<br>API声明：declare type UIContext = import('../api/@ohos.arkui.UIContext').UIContext;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomComponent；<br>API声明：onFormRecycle?(): string;<br>差异内容：NA|类名：CustomComponent；<br>API声明：onFormRecycle?(): string;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomComponent；<br>API声明：onFormRecover?(statusData: string): void;<br>差异内容：NA|类名：CustomComponent；<br>API声明：onFormRecover?(statusData: string): void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomComponent；<br>API声明：getUIContext(): UIContext;<br>差异内容：NA|类名：CustomComponent；<br>API声明：getUIContext(): UIContext;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CustomComponent；<br>API声明：queryNavDestinationInfo(): NavDestinationInfo \| undefined;<br>差异内容：NA|类名：CustomComponent；<br>API声明：queryNavDestinationInfo(): NavDestinationInfo \| undefined;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface CaretOffset<br>差异内容：NA|类名：global；<br>API声明：declare interface CaretOffset<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CaretOffset；<br>API声明：index: number;<br>差异内容：NA|类名：CaretOffset；<br>API声明：index: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CaretOffset；<br>API声明：x: number;<br>差异内容：NA|类名：CaretOffset；<br>API声明：x: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：CaretOffset；<br>API声明：y: number;<br>差异内容：NA|类名：CaretOffset；<br>API声明：y: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：TextContentControllerBase；<br>API声明：getCaretOffset() : CaretOffset;<br>差异内容：NA|类名：TextContentControllerBase；<br>API声明：getCaretOffset(): CaretOffset;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface EdgeEffectOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface EdgeEffectOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：EdgeEffectOptions；<br>API声明：alwaysEnabled: boolean;<br>差异内容：NA|类名：EdgeEffectOptions；<br>API声明：alwaysEnabled: boolean;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface BackgroundBrightnessOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface BackgroundBrightnessOptions<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BackgroundBrightnessOptions；<br>API声明：rate: number;<br>差异内容：NA|类名：BackgroundBrightnessOptions；<br>API声明：rate: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：BackgroundBrightnessOptions；<br>API声明：lightUpDegree: number;<br>差异内容：NA|类名：BackgroundBrightnessOptions；<br>API声明：lightUpDegree: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare function wrapBuilder\<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder\<Args>;<br>差异内容：NA|类名：global；<br>API声明：declare function wrapBuilder\<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder\<Args>;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class WrappedBuilder<br>差异内容：NA|类名：global；<br>API声明：declare class WrappedBuilder<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：WrappedBuilder；<br>API声明：builder: (...args: Args) => void;<br>差异内容：NA|类名：WrappedBuilder；<br>API声明：builder: (...args: Args) => void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface KeyframeAnimateParam<br>差异内容：NA|类名：global；<br>API声明：declare interface KeyframeAnimateParam<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：KeyframeAnimateParam；<br>API声明：delay?: number;<br>差异内容：NA|类名：KeyframeAnimateParam；<br>API声明：delay?: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：KeyframeAnimateParam；<br>API声明：iterations?: number;<br>差异内容：NA|类名：KeyframeAnimateParam；<br>API声明：iterations?: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：KeyframeAnimateParam；<br>API声明：onFinish?: () => void;<br>差异内容：NA|类名：KeyframeAnimateParam；<br>API声明：onFinish?: () => void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface KeyframeState<br>差异内容：NA|类名：global；<br>API声明：declare interface KeyframeState<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：KeyframeState；<br>API声明：duration: number;<br>差异内容：NA|类名：KeyframeState；<br>API声明：duration: number;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：KeyframeState；<br>API声明：curve?: Curve \| string \| ICurve;<br>差异内容：NA|类名：KeyframeState；<br>API声明：curve?: Curve \| string \| ICurve;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：KeyframeState；<br>API声明：event: () => void;<br>差异内容：NA|类名：KeyframeState；<br>API声明：event: () => void;<br>差异内容：atomicservice|component/common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface ContainerSpanInterface<br>差异内容：NA|类名：global；<br>API声明：interface ContainerSpanInterface<br>差异内容：atomicservice|component/container_span.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class ContainerSpanAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class ContainerSpanAttribute<br>差异内容：atomicservice|component/container_span.d.ts|
|API从不支持元服务到支持元服务|类名：ContainerSpanAttribute；<br>API声明：textBackgroundStyle(style: TextBackgroundStyle): ContainerSpanAttribute;<br>差异内容：NA|类名：ContainerSpanAttribute；<br>API声明：textBackgroundStyle(style: TextBackgroundStyle): ContainerSpanAttribute;<br>差异内容：atomicservice|component/container_span.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const ContainerSpan: ContainerSpanInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const ContainerSpan: ContainerSpanInterface;<br>差异内容：atomicservice|component/container_span.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const ContainerSpanInstance: ContainerSpanAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const ContainerSpanInstance: ContainerSpanAttribute;<br>差异内容：atomicservice|component/container_span.d.ts|
|API从不支持元服务到支持元服务|类名：CustomDialogControllerOptions；<br>API声明：isModal?: boolean;<br>差异内容：NA|类名：CustomDialogControllerOptions；<br>API声明：isModal?: boolean;<br>差异内容：atomicservice|component/custom_dialog_controller.d.ts|
|API从不支持元服务到支持元服务|类名：DatePickerDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：NA|类名：DatePickerDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：atomicservice|component/date_picker.d.ts|
|API从不支持元服务到支持元服务|类名：DatePickerDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：DatePickerDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|component/date_picker.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum CheckBoxShape<br>差异内容：NA|类名：global；<br>API声明：declare enum CheckBoxShape<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：CheckBoxShape；<br>API声明：CIRCLE = 0<br>差异内容：NA|类名：CheckBoxShape；<br>API声明：CIRCLE = 0<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：CheckBoxShape；<br>API声明：ROUNDED_SQUARE = 1<br>差异内容：NA|类名：CheckBoxShape；<br>API声明：ROUNDED_SQUARE = 1<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：ColoringStrategy；<br>API声明：AVERAGE = 'average'<br>差异内容：NA|类名：ColoringStrategy；<br>API声明：AVERAGE = 'average'<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：ColoringStrategy；<br>API声明：PRIMARY = 'primary'<br>差异内容：NA|类名：ColoringStrategy；<br>API声明：PRIMARY = 'primary'<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum ArrowPointPosition<br>差异内容：NA|类名：global；<br>API声明：declare enum ArrowPointPosition<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：ArrowPointPosition；<br>API声明：START = 'Start'<br>差异内容：NA|类名：ArrowPointPosition；<br>API声明：START = 'Start'<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：ArrowPointPosition；<br>API声明：CENTER = 'Center'<br>差异内容：NA|类名：ArrowPointPosition；<br>API声明：CENTER = 'Center'<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：ArrowPointPosition；<br>API声明：END = 'End'<br>差异内容：NA|类名：ArrowPointPosition；<br>API声明：END = 'End'<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum EllipsisMode<br>差异内容：NA|类名：global；<br>API声明：declare enum EllipsisMode<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：EllipsisMode；<br>API声明：START = 0<br>差异内容：NA|类名：EllipsisMode；<br>API声明：START = 0<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：EllipsisMode；<br>API声明：CENTER = 1<br>差异内容：NA|类名：EllipsisMode；<br>API声明：CENTER = 1<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：EllipsisMode；<br>API声明：END = 2<br>差异内容：NA|类名：EllipsisMode；<br>API声明：END = 2<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type Nullable\<T> = T \| undefined;<br>差异内容：NA|类名：global；<br>API声明：declare type Nullable\<T> = T \| undefined;<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum OptionWidthMode<br>差异内容：NA|类名：global；<br>API声明：declare enum OptionWidthMode<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：OptionWidthMode；<br>API声明：FIT_CONTENT = 'fit_content'<br>差异内容：NA|类名：OptionWidthMode；<br>API声明：FIT_CONTENT = 'fit_content'<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：OptionWidthMode；<br>API声明：FIT_TRIGGER = 'fit_trigger'<br>差异内容：NA|类名：OptionWidthMode；<br>API声明：FIT_TRIGGER = 'fit_trigger'<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum FoldStatus<br>差异内容：NA|类名：global；<br>API声明：declare enum FoldStatus<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：FoldStatus；<br>API声明：FOLD_STATUS_UNKNOWN = 0<br>差异内容：NA|类名：FoldStatus；<br>API声明：FOLD_STATUS_UNKNOWN = 0<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：FoldStatus；<br>API声明：FOLD_STATUS_EXPANDED = 1<br>差异内容：NA|类名：FoldStatus；<br>API声明：FOLD_STATUS_EXPANDED = 1<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：FoldStatus；<br>API声明：FOLD_STATUS_FOLDED = 2<br>差异内容：NA|类名：FoldStatus；<br>API声明：FOLD_STATUS_FOLDED = 2<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：FoldStatus；<br>API声明：FOLD_STATUS_HALF_FOLDED = 3<br>差异内容：NA|类名：FoldStatus；<br>API声明：FOLD_STATUS_HALF_FOLDED = 3<br>差异内容：atomicservice|component/enums.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface FolderStackInterface<br>差异内容：NA|类名：global；<br>API声明：interface FolderStackInterface<br>差异内容：atomicservice|component/folder_stack.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class FolderStackAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class FolderStackAttribute<br>差异内容：atomicservice|component/folder_stack.d.ts|
|API从不支持元服务到支持元服务|类名：FolderStackAttribute；<br>API声明：alignContent(value: Alignment): FolderStackAttribute;<br>差异内容：NA|类名：FolderStackAttribute；<br>API声明：alignContent(value: Alignment): FolderStackAttribute;<br>差异内容：atomicservice|component/folder_stack.d.ts|
|API从不支持元服务到支持元服务|类名：FolderStackAttribute；<br>API声明：onFolderStateChange(callback: (event: {<br>        /**<br>         * folder state.<br>         *<br>         * @type { FoldStatus }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 11<br>         */<br>        foldStatus: FoldStatus;<br>    }) => void): FolderStackAttribute;<br>差异内容：NA|类名：FolderStackAttribute；<br>API声明：onFolderStateChange(callback: (event: {<br>        /**<br>         * folder state.<br>         *<br>         * @type { FoldStatus }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @since 11<br>         */<br>        /**<br>         * folder state.<br>         *<br>         * @type { FoldStatus }<br>         * @syscap SystemCapability.ArkUI.ArkUI.Full<br>         * @crossplatform<br>         * @atomicservice<br>         * @since 12<br>         */<br>        foldStatus: FoldStatus;<br>    }) => void): FolderStackAttribute;<br>差异内容：atomicservice|component/folder_stack.d.ts|
|API从不支持元服务到支持元服务|类名：FolderStackAttribute；<br>API声明：enableAnimation(value: boolean): FolderStackAttribute;<br>差异内容：NA|类名：FolderStackAttribute；<br>API声明：enableAnimation(value: boolean): FolderStackAttribute;<br>差异内容：atomicservice|component/folder_stack.d.ts|
|API从不支持元服务到支持元服务|类名：FolderStackAttribute；<br>API声明：autoHalfFold(value: boolean): FolderStackAttribute;<br>差异内容：NA|类名：FolderStackAttribute；<br>API声明：autoHalfFold(value: boolean): FolderStackAttribute;<br>差异内容：atomicservice|component/folder_stack.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const FolderStack: FolderStackInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const FolderStack: FolderStackInterface;<br>差异内容：atomicservice|component/folder_stack.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const FolderStackInstance: FolderStackAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const FolderStackInstance: FolderStackAttribute;<br>差异内容：atomicservice|component/folder_stack.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface GaugeShadowOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface GaugeShadowOptions<br>差异内容：atomicservice|component/gauge.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface GaugeIndicatorOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface GaugeIndicatorOptions<br>差异内容：atomicservice|component/gauge.d.ts|
|API从不支持元服务到支持元服务|类名：GaugeIndicatorOptions；<br>API声明：icon?: ResourceStr;<br>差异内容：NA|类名：GaugeIndicatorOptions；<br>API声明：icon?: ResourceStr;<br>差异内容：atomicservice|component/gauge.d.ts|
|API从不支持元服务到支持元服务|类名：GaugeIndicatorOptions；<br>API声明：space?: Dimension;<br>差异内容：NA|类名：GaugeIndicatorOptions；<br>API声明：space?: Dimension;<br>差异内容：atomicservice|component/gauge.d.ts|
|API从不支持元服务到支持元服务|类名：GaugeAttribute；<br>API声明：description(value: CustomBuilder): GaugeAttribute;<br>差异内容：NA|类名：GaugeAttribute；<br>API声明：description(value: CustomBuilder): GaugeAttribute;<br>差异内容：atomicservice|component/gauge.d.ts|
|API从不支持元服务到支持元服务|类名：GaugeAttribute；<br>API声明：trackShadow(value: GaugeShadowOptions): GaugeAttribute;<br>差异内容：NA|类名：GaugeAttribute；<br>API声明：trackShadow(value: GaugeShadowOptions): GaugeAttribute;<br>差异内容：atomicservice|component/gauge.d.ts|
|API从不支持元服务到支持元服务|类名：GaugeAttribute；<br>API声明：indicator(value: GaugeIndicatorOptions): GaugeAttribute;<br>差异内容：NA|类名：GaugeAttribute；<br>API声明：indicator(value: GaugeIndicatorOptions): GaugeAttribute;<br>差异内容：atomicservice|component/gauge.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum GestureJudgeResult<br>差异内容：NA|类名：global；<br>API声明：declare enum GestureJudgeResult<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureJudgeResult；<br>API声明：CONTINUE = 0<br>差异内容：NA|类名：GestureJudgeResult；<br>API声明：CONTINUE = 0<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureJudgeResult；<br>API声明：REJECT = 1<br>差异内容：NA|类名：GestureJudgeResult；<br>API声明：REJECT = 1<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace GestureControl<br>差异内容：NA|类名：global；<br>API声明：declare namespace GestureControl<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureControl；<br>API声明：enum GestureType<br>差异内容：NA|类名：GestureControl；<br>API声明：enum GestureType<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureType；<br>API声明：TAP_GESTURE = 0<br>差异内容：NA|类名：GestureType；<br>API声明：TAP_GESTURE = 0<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureType；<br>API声明：LONG_PRESS_GESTURE = 1<br>差异内容：NA|类名：GestureType；<br>API声明：LONG_PRESS_GESTURE = 1<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureType；<br>API声明：PAN_GESTURE = 2<br>差异内容：NA|类名：GestureType；<br>API声明：PAN_GESTURE = 2<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureType；<br>API声明：PINCH_GESTURE = 3<br>差异内容：NA|类名：GestureType；<br>API声明：PINCH_GESTURE = 3<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureType；<br>API声明：SWIPE_GESTURE = 4<br>差异内容：NA|类名：GestureType；<br>API声明：SWIPE_GESTURE = 4<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureType；<br>API声明：ROTATION_GESTURE = 5<br>差异内容：NA|类名：GestureType；<br>API声明：ROTATION_GESTURE = 5<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureType；<br>API声明：DRAG = 6<br>差异内容：NA|类名：GestureType；<br>API声明：DRAG = 6<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureType；<br>API声明：CLICK = 7<br>差异内容：NA|类名：GestureType；<br>API声明：CLICK = 7<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface GestureInfo<br>差异内容：NA|类名：global；<br>API声明：declare interface GestureInfo<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureInfo；<br>API声明：tag?: string;<br>差异内容：NA|类名：GestureInfo；<br>API声明：tag?: string;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureInfo；<br>API声明：type: GestureControl.GestureType;<br>差异内容：NA|类名：GestureInfo；<br>API声明：type: GestureControl.GestureType;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GestureInfo；<br>API声明：isSystemGesture: boolean;<br>差异内容：NA|类名：GestureInfo；<br>API声明：isSystemGesture: boolean;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface BaseGestureEvent<br>差异内容：NA|类名：global；<br>API声明：interface BaseGestureEvent<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：BaseGestureEvent；<br>API声明：fingerList: FingerInfo[];<br>差异内容：NA|类名：BaseGestureEvent；<br>API声明：fingerList: FingerInfo[];<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface TapGestureEvent<br>差异内容：NA|类名：global；<br>API声明：interface TapGestureEvent<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface LongPressGestureEvent<br>差异内容：NA|类名：global；<br>API声明：interface LongPressGestureEvent<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：LongPressGestureEvent；<br>API声明：repeat: boolean;<br>差异内容：NA|类名：LongPressGestureEvent；<br>API声明：repeat: boolean;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface PanGestureEvent<br>差异内容：NA|类名：global；<br>API声明：interface PanGestureEvent<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：PanGestureEvent；<br>API声明：offsetX: number;<br>差异内容：NA|类名：PanGestureEvent；<br>API声明：offsetX: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：PanGestureEvent；<br>API声明：offsetY: number;<br>差异内容：NA|类名：PanGestureEvent；<br>API声明：offsetY: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：PanGestureEvent；<br>API声明：velocityX: number;<br>差异内容：NA|类名：PanGestureEvent；<br>API声明：velocityX: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：PanGestureEvent；<br>API声明：velocityY: number;<br>差异内容：NA|类名：PanGestureEvent；<br>API声明：velocityY: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：PanGestureEvent；<br>API声明：velocity: number;<br>差异内容：NA|类名：PanGestureEvent；<br>API声明：velocity: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface PinchGestureEvent<br>差异内容：NA|类名：global；<br>API声明：interface PinchGestureEvent<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：PinchGestureEvent；<br>API声明：scale: number;<br>差异内容：NA|类名：PinchGestureEvent；<br>API声明：scale: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：PinchGestureEvent；<br>API声明：pinchCenterX: number;<br>差异内容：NA|类名：PinchGestureEvent；<br>API声明：pinchCenterX: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：PinchGestureEvent；<br>API声明：pinchCenterY: number;<br>差异内容：NA|类名：PinchGestureEvent；<br>API声明：pinchCenterY: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface RotationGestureEvent<br>差异内容：NA|类名：global；<br>API声明：interface RotationGestureEvent<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：RotationGestureEvent；<br>API声明：angle: number;<br>差异内容：NA|类名：RotationGestureEvent；<br>API声明：angle: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface SwipeGestureEvent<br>差异内容：NA|类名：global；<br>API声明：interface SwipeGestureEvent<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：SwipeGestureEvent；<br>API声明：angle: number;<br>差异内容：NA|类名：SwipeGestureEvent；<br>API声明：angle: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：SwipeGestureEvent；<br>API声明：speed: number;<br>差异内容：NA|类名：SwipeGestureEvent；<br>API声明：speed: number;<br>差异内容：atomicservice|component/gesture.d.ts|
|API从不支持元服务到支持元服务|类名：GridLayoutOptions；<br>API声明：onGetRectByIndex?: (index: number) => [<br>        number,<br>        number,<br>        number,<br>        number<br>    ];<br>差异内容：NA|类名：GridLayoutOptions；<br>API声明：onGetRectByIndex?: (index: number) => [<br>        number,<br>        number,<br>        number,<br>        number<br>    ];<br>差异内容：atomicservice|component/grid.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum GridItemStyle<br>差异内容：NA|类名：global；<br>API声明：declare enum GridItemStyle<br>差异内容：atomicservice|component/gridItem.d.ts|
|API从不支持元服务到支持元服务|类名：GridItemStyle；<br>API声明：NONE = 0<br>差异内容：NA|类名：GridItemStyle；<br>API声明：NONE = 0<br>差异内容：atomicservice|component/gridItem.d.ts|
|API从不支持元服务到支持元服务|类名：GridItemStyle；<br>API声明：PLAIN = 1<br>差异内容：NA|类名：GridItemStyle；<br>API声明：PLAIN = 1<br>差异内容：atomicservice|component/gridItem.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface GridItemOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface GridItemOptions<br>差异内容：atomicservice|component/gridItem.d.ts|
|API从不支持元服务到支持元服务|类名：GridItemOptions；<br>API声明：style?: GridItemStyle;<br>差异内容：NA|类名：GridItemOptions；<br>API声明：style?: GridItemStyle;<br>差异内容：atomicservice|component/gridItem.d.ts|
|API从不支持元服务到支持元服务|类名：ImageAttribute；<br>API声明：enableAnalyzer(enable: boolean): ImageAttribute;<br>差异内容：NA|类名：ImageAttribute；<br>API声明：enableAnalyzer(enable: boolean): ImageAttribute;<br>差异内容：atomicservice|component/image.d.ts|
|API从不支持元服务到支持元服务|类名：ImageAttribute；<br>API声明：resizable(value: ResizableOptions): ImageAttribute;<br>差异内容：NA|类名：ImageAttribute；<br>API声明：resizable(value: ResizableOptions): ImageAttribute;<br>差异内容：atomicservice|component/image.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface ResizableOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface ResizableOptions<br>差异内容：atomicservice|component/image.d.ts|
|API从不支持元服务到支持元服务|类名：ResizableOptions；<br>API声明：slice?: EdgeWidths;<br>差异内容：NA|类名：ResizableOptions；<br>API声明：slice?: EdgeWidths;<br>差异内容：atomicservice|component/image.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface CloseSwipeActionOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface CloseSwipeActionOptions<br>差异内容：atomicservice|component/list.d.ts|
|API从不支持元服务到支持元服务|类名：CloseSwipeActionOptions；<br>API声明：onFinish?: () => void;<br>差异内容：NA|类名：CloseSwipeActionOptions；<br>API声明：onFinish?: () => void;<br>差异内容：atomicservice|component/list.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class ListScroller<br>差异内容：NA|类名：global；<br>API声明：declare class ListScroller<br>差异内容：atomicservice|component/list.d.ts|
|API从不支持元服务到支持元服务|类名：ListScroller；<br>API声明：getItemRectInGroup(index: number, indexInGroup: number): RectResult;<br>差异内容：NA|类名：ListScroller；<br>API声明：getItemRectInGroup(index: number, indexInGroup: number): RectResult;<br>差异内容：atomicservice|component/list.d.ts|
|API从不支持元服务到支持元服务|类名：ListScroller；<br>API声明：scrollToItemInGroup(index: number, indexInGroup: number, smooth?: boolean, align?: ScrollAlign): void;<br>差异内容：NA|类名：ListScroller；<br>API声明：scrollToItemInGroup(index: number, indexInGroup: number, smooth?: boolean, align?: ScrollAlign): void;<br>差异内容：atomicservice|component/list.d.ts|
|API从不支持元服务到支持元服务|类名：ListScroller；<br>API声明：closeAllSwipeActions(options?: CloseSwipeActionOptions): void;<br>差异内容：NA|类名：ListScroller；<br>API声明：closeAllSwipeActions(options?: CloseSwipeActionOptions): void;<br>差异内容：atomicservice|component/list.d.ts|
|API从不支持元服务到支持元服务|类名：ListAttribute；<br>API声明：contentStartOffset(value: number): ListAttribute;<br>差异内容：NA|类名：ListAttribute；<br>API声明：contentStartOffset(value: number): ListAttribute;<br>差异内容：atomicservice|component/list.d.ts|
|API从不支持元服务到支持元服务|类名：ListAttribute；<br>API声明：contentEndOffset(value: number): ListAttribute;<br>差异内容：NA|类名：ListAttribute；<br>API声明：contentEndOffset(value: number): ListAttribute;<br>差异内容：atomicservice|component/list.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum SwipeActionState<br>差异内容：NA|类名：global；<br>API声明：declare enum SwipeActionState<br>差异内容：atomicservice|component/list_item.d.ts|
|API从不支持元服务到支持元服务|类名：SwipeActionState；<br>API声明：COLLAPSED<br>差异内容：NA|类名：SwipeActionState；<br>API声明：COLLAPSED<br>差异内容：atomicservice|component/list_item.d.ts|
|API从不支持元服务到支持元服务|类名：SwipeActionState；<br>API声明：EXPANDED<br>差异内容：NA|类名：SwipeActionState；<br>API声明：EXPANDED<br>差异内容：atomicservice|component/list_item.d.ts|
|API从不支持元服务到支持元服务|类名：SwipeActionState；<br>API声明：ACTIONING<br>差异内容：NA|类名：SwipeActionState；<br>API声明：ACTIONING<br>差异内容：atomicservice|component/list_item.d.ts|
|API从不支持元服务到支持元服务|类名：SwipeActionItem；<br>API声明：onStateChange?: (state: SwipeActionState) => void;<br>差异内容：NA|类名：SwipeActionItem；<br>API声明：onStateChange?: (state: SwipeActionState) => void;<br>差异内容：atomicservice|component/list_item.d.ts|
|API从不支持元服务到支持元服务|类名：SwipeActionOptions；<br>API声明：onOffsetChange?: (offset: number) => void;<br>差异内容：NA|类名：SwipeActionOptions；<br>API声明：onOffsetChange?: (offset: number) => void;<br>差异内容：atomicservice|component/list_item.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface PopInfo<br>差异内容：NA|类名：global；<br>API声明：declare interface PopInfo<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：PopInfo；<br>API声明：info: NavPathInfo;<br>差异内容：NA|类名：PopInfo；<br>API声明：info: NavPathInfo;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：PopInfo；<br>API声明：result: Object;<br>差异内容：NA|类名：PopInfo；<br>API声明：result: Object;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathInfo；<br>API声明：onPop?: import('../api/@ohos.base').Callback\<PopInfo>;<br>差异内容：NA|类名：NavPathInfo；<br>API声明：onPop?: import('../api/@ohos.base').Callback\<PopInfo>;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：pushDestination(info: NavPathInfo, animated?: boolean): Promise\<void>;<br>差异内容：NA|类名：NavPathStack；<br>API声明：pushDestination(info: NavPathInfo, animated?: boolean): Promise\<void>;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：pushPathByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback\<PopInfo>, animated?: boolean): void;<br>差异内容：NA|类名：NavPathStack；<br>API声明：pushPathByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback\<PopInfo>, animated?: boolean): void;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：pushDestinationByName(name: string, param: Object, animated?: boolean): Promise\<void>;<br>差异内容：NA|类名：NavPathStack；<br>API声明：pushDestinationByName(name: string, param: Object, animated?: boolean): Promise\<void>;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：pushDestinationByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback\<PopInfo>, animated?: boolean): Promise\<void>;<br>差异内容：NA|类名：NavPathStack；<br>API声明：pushDestinationByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback\<PopInfo>, animated?: boolean): Promise\<void>;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：replacePath(info: NavPathInfo, animated?: boolean): void;<br>差异内容：NA|类名：NavPathStack；<br>API声明：replacePath(info: NavPathInfo, animated?: boolean): void;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：replacePathByName(name: string, param: Object, animated?: boolean): void;<br>差异内容：NA|类名：NavPathStack；<br>API声明：replacePathByName(name: string, param: Object, animated?: boolean): void;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：removeByIndexes(indexes: Array\<number>): number;<br>差异内容：NA|类名：NavPathStack；<br>API声明：removeByIndexes(indexes: Array\<number>): number;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：removeByName(name: string): number;<br>差异内容：NA|类名：NavPathStack；<br>API声明：removeByName(name: string): number;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：pop(result: Object, animated?: boolean): NavPathInfo \| undefined;<br>差异内容：NA|类名：NavPathStack；<br>API声明：pop(result: Object, animated?: boolean): NavPathInfo \| undefined;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：popToName(name: string, result: Object, animated?: boolean): number;<br>差异内容：NA|类名：NavPathStack；<br>API声明：popToName(name: string, result: Object, animated?: boolean): number;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavPathStack；<br>API声明：disableAnimation(value: boolean): void;<br>差异内容：NA|类名：NavPathStack；<br>API声明：disableAnimation(value: boolean): void;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum NavigationOperation<br>差异内容：NA|类名：global；<br>API声明：declare enum NavigationOperation<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationOperation；<br>API声明：PUSH = 1<br>差异内容：NA|类名：NavigationOperation；<br>API声明：PUSH = 1<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationOperation；<br>API声明：POP = 2<br>差异内容：NA|类名：NavigationOperation；<br>API声明：POP = 2<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationOperation；<br>API声明：REPLACE = 3<br>差异内容：NA|类名：NavigationOperation；<br>API声明：REPLACE = 3<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationAttribute；<br>API声明：customNavContentTransition(delegate: (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => NavigationAnimatedTransition \| undefined): NavigationAttribute;<br>差异内容：NA|类名：NavigationAttribute；<br>API声明：customNavContentTransition(delegate: (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => NavigationAnimatedTransition \| undefined): NavigationAttribute;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface NavigationAnimatedTransition<br>差异内容：NA|类名：global；<br>API声明：declare interface NavigationAnimatedTransition<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationAnimatedTransition；<br>API声明：onTransitionEnd?: (success: boolean) => void;<br>差异内容：NA|类名：NavigationAnimatedTransition；<br>API声明：onTransitionEnd?: (success: boolean) => void;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationAnimatedTransition；<br>API声明：timeout?: number;<br>差异内容：NA|类名：NavigationAnimatedTransition；<br>API声明：timeout?: number;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationAnimatedTransition；<br>API声明：transition: (transitionProxy: NavigationTransitionProxy) => void;<br>差异内容：NA|类名：NavigationAnimatedTransition；<br>API声明：transition: (transitionProxy: NavigationTransitionProxy) => void;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface NavigationTransitionProxy<br>差异内容：NA|类名：global；<br>API声明：declare interface NavigationTransitionProxy<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationTransitionProxy；<br>API声明：from: NavContentInfo;<br>差异内容：NA|类名：NavigationTransitionProxy；<br>API声明：from: NavContentInfo;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationTransitionProxy；<br>API声明：to: NavContentInfo;<br>差异内容：NA|类名：NavigationTransitionProxy；<br>API声明：to: NavContentInfo;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavigationTransitionProxy；<br>API声明：finishTransition(): void;<br>差异内容：NA|类名：NavigationTransitionProxy；<br>API声明：finishTransition(): void;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface NavContentInfo<br>差异内容：NA|类名：global；<br>API声明：declare interface NavContentInfo<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavContentInfo；<br>API声明：name?: string;<br>差异内容：NA|类名：NavContentInfo；<br>API声明：name?: string;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavContentInfo；<br>API声明：index: number;<br>差异内容：NA|类名：NavContentInfo；<br>API声明：index: number;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：NavContentInfo；<br>API声明：mode?: NavDestinationMode;<br>差异内容：NA|类名：NavContentInfo；<br>API声明：mode?: NavDestinationMode;<br>差异内容：atomicservice|component/navigation.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum NavDestinationMode<br>差异内容：NA|类名：global；<br>API声明：declare enum NavDestinationMode<br>差异内容：atomicservice|component/nav_destination.d.ts|
|API从不支持元服务到支持元服务|类名：NavDestinationMode；<br>API声明：STANDARD = 0<br>差异内容：NA|类名：NavDestinationMode；<br>API声明：STANDARD = 0<br>差异内容：atomicservice|component/nav_destination.d.ts|
|API从不支持元服务到支持元服务|类名：NavDestinationMode；<br>API声明：DIALOG = 1<br>差异内容：NA|类名：NavDestinationMode；<br>API声明：DIALOG = 1<br>差异内容：atomicservice|component/nav_destination.d.ts|
|API从不支持元服务到支持元服务|类名：NavDestinationAttribute；<br>API声明：mode(value: NavDestinationMode): NavDestinationAttribute;<br>差异内容：NA|类名：NavDestinationAttribute；<br>API声明：mode(value: NavDestinationMode): NavDestinationAttribute;<br>差异内容：atomicservice|component/nav_destination.d.ts|
|API从不支持元服务到支持元服务|类名：NavDestinationAttribute；<br>API声明：backButtonIcon(value: ResourceStr \| PixelMap): NavDestinationAttribute;<br>差异内容：NA|类名：NavDestinationAttribute；<br>API声明：backButtonIcon(value: ResourceStr \| PixelMap \| SymbolGlyphModifier): NavDestinationAttribute;<br>差异内容：atomicservice|component/nav_destination.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface NodeContainerInterface<br>差异内容：NA|类名：global；<br>API声明：interface NodeContainerInterface<br>差异内容：atomicservice|component/node_container.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class NodeContainerAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class NodeContainerAttribute<br>差异内容：atomicservice|component/node_container.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const NodeContainer: NodeContainerInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const NodeContainer: NodeContainerInterface;<br>差异内容：atomicservice|component/node_container.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const NodeContainerInstance: NodeContainerAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const NodeContainerInstance: NodeContainerAttribute;<br>差异内容：atomicservice|component/node_container.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum PatternLockChallengeResult<br>差异内容：NA|类名：global；<br>API声明：declare enum PatternLockChallengeResult<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockChallengeResult；<br>API声明：CORRECT = 1<br>差异内容：NA|类名：PatternLockChallengeResult；<br>API声明：CORRECT = 1<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockChallengeResult；<br>API声明：WRONG = 2<br>差异内容：NA|类名：PatternLockChallengeResult；<br>API声明：WRONG = 2<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class PatternLockController<br>差异内容：NA|类名：global；<br>API声明：declare class PatternLockController<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockController；<br>API声明：reset();<br>差异内容：NA|类名：PatternLockController；<br>API声明：reset();<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockController；<br>API声明：setChallengeResult(result: PatternLockChallengeResult): void;<br>差异内容：NA|类名：PatternLockController；<br>API声明：setChallengeResult(result: PatternLockChallengeResult): void;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface PatternLockInterface<br>差异内容：NA|类名：global；<br>API声明：interface PatternLockInterface<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class PatternLockAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class PatternLockAttribute<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：sideLength(value: Length): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：sideLength(value: Length): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：circleRadius(value: Length): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：circleRadius(value: Length): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：backgroundColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：backgroundColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：regularColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：regularColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：selectedColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：selectedColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：activeColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：activeColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：pathColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：pathColor(value: ResourceColor): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：pathStrokeWidth(value: number \| string): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：pathStrokeWidth(value: number \| string): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：onPatternComplete(callback: (input: Array\<number>) => void): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：onPatternComplete(callback: (input: Array\<number>) => void): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：autoReset(value: boolean): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：autoReset(value: boolean): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：PatternLockAttribute；<br>API声明：onDotConnect(callback: import('../api/@ohos.base').Callback\<number>): PatternLockAttribute;<br>差异内容：NA|类名：PatternLockAttribute；<br>API声明：onDotConnect(callback: import('../api/@ohos.base').Callback\<number>): PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const PatternLock: PatternLockInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const PatternLock: PatternLockInterface;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const PatternLockInstance: PatternLockAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const PatternLockInstance: PatternLockAttribute;<br>差异内容：atomicservice|component/pattern_lock.d.ts|
|API从不支持元服务到支持元服务|类名：QRCodeAttribute；<br>API声明：contentOpacity(value: number \| Resource): QRCodeAttribute;<br>差异内容：NA|类名：QRCodeAttribute；<br>API声明：contentOpacity(value: number \| Resource): QRCodeAttribute;<br>差异内容：atomicservice|component/qrcode.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum RichEditorResponseType<br>差异内容：NA|类名：global；<br>API声明：declare enum RichEditorResponseType<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorResponseType；<br>API声明：RIGHT_CLICK = 0<br>差异内容：NA|类名：RichEditorResponseType；<br>API声明：RIGHT_CLICK = 0<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorResponseType；<br>API声明：LONG_PRESS = 1<br>差异内容：NA|类名：RichEditorResponseType；<br>API声明：LONG_PRESS = 1<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorResponseType；<br>API声明：SELECT = 2<br>差异内容：NA|类名：RichEditorResponseType；<br>API声明：SELECT = 2<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorTextStyle；<br>API声明：textShadow?: ShadowOptions \| Array\<ShadowOptions>;<br>差异内容：NA|类名：RichEditorTextStyle；<br>API声明：textShadow?: ShadowOptions \| Array\<ShadowOptions>;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface LeadingMarginPlaceholder<br>差异内容：NA|类名：global；<br>API声明：declare interface LeadingMarginPlaceholder<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：LeadingMarginPlaceholder；<br>API声明：pixelMap: PixelMap;<br>差异内容：NA|类名：LeadingMarginPlaceholder；<br>API声明：pixelMap: PixelMap;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：LeadingMarginPlaceholder；<br>API声明：size: [<br>        Dimension,<br>        Dimension<br>    ];<br>差异内容：NA|类名：LeadingMarginPlaceholder；<br>API声明：size: [<br>        Dimension,<br>        Dimension<br>    ];<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface RichEditorParagraphStyle<br>差异内容：NA|类名：global；<br>API声明：declare interface RichEditorParagraphStyle<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorParagraphStyle；<br>API声明：textAlign?: TextAlign;<br>差异内容：NA|类名：RichEditorParagraphStyle；<br>API声明：textAlign?: TextAlign;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorParagraphStyle；<br>API声明：leadingMargin?: Dimension \| LeadingMarginPlaceholder;<br>差异内容：NA|类名：RichEditorParagraphStyle；<br>API声明：leadingMargin?: Dimension \| LeadingMarginPlaceholder;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface RichEditorLayoutStyle<br>差异内容：NA|类名：global；<br>API声明：interface RichEditorLayoutStyle<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorLayoutStyle；<br>API声明：margin?: Dimension \| Margin;<br>差异内容：NA|类名：RichEditorLayoutStyle；<br>API声明：margin?: Dimension \| Margin;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorLayoutStyle；<br>API声明：borderRadius?: Dimension \| BorderRadiuses;<br>差异内容：NA|类名：RichEditorLayoutStyle；<br>API声明：borderRadius?: Dimension \| BorderRadiuses;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorImageSpanStyle；<br>API声明：layoutStyle?: RichEditorLayoutStyle;<br>差异内容：NA|类名：RichEditorImageSpanStyle；<br>API声明：layoutStyle?: RichEditorLayoutStyle;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface RichEditorSymbolSpanStyle<br>差异内容：NA|类名：global；<br>API声明：declare interface RichEditorSymbolSpanStyle<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyle；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：NA|类名：RichEditorSymbolSpanStyle；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyle；<br>API声明：fontColor?: Array\<ResourceColor>;<br>差异内容：NA|类名：RichEditorSymbolSpanStyle；<br>API声明：fontColor?: Array\<ResourceColor>;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyle；<br>API声明：fontWeight?: number \| FontWeight \| string;<br>差异内容：NA|类名：RichEditorSymbolSpanStyle；<br>API声明：fontWeight?: number \| FontWeight \| string;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyle；<br>API声明：effectStrategy?: SymbolEffectStrategy;<br>差异内容：NA|类名：RichEditorSymbolSpanStyle；<br>API声明：effectStrategy?: SymbolEffectStrategy;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyle；<br>API声明：renderingStrategy?: SymbolRenderingStrategy;<br>差异内容：NA|类名：RichEditorSymbolSpanStyle；<br>API声明：renderingStrategy?: SymbolRenderingStrategy;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface RichEditorParagraphResult<br>差异内容：NA|类名：global；<br>API声明：declare interface RichEditorParagraphResult<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorParagraphResult；<br>API声明：style: RichEditorParagraphStyle;<br>差异内容：NA|类名：RichEditorParagraphResult；<br>API声明：style: RichEditorParagraphStyle;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorParagraphResult；<br>API声明：range: [<br>        number,<br>        number<br>    ];<br>差异内容：NA|类名：RichEditorParagraphResult；<br>API声明：range: [<br>        number,<br>        number<br>    ];<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface RichEditorSymbolSpanStyleResult<br>差异内容：NA|类名：global；<br>API声明：declare interface RichEditorSymbolSpanStyleResult<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyleResult；<br>API声明：fontSize: number \| string \| Resource;<br>差异内容：NA|类名：RichEditorSymbolSpanStyleResult；<br>API声明：fontSize: number \| string \| Resource;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyleResult；<br>API声明：fontColor: Array\<ResourceColor>;<br>差异内容：NA|类名：RichEditorSymbolSpanStyleResult；<br>API声明：fontColor: Array\<ResourceColor>;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyleResult；<br>API声明：fontWeight: number \| FontWeight \| string;<br>差异内容：NA|类名：RichEditorSymbolSpanStyleResult；<br>API声明：fontWeight: number \| FontWeight \| string;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyleResult；<br>API声明：effectStrategy: SymbolEffectStrategy;<br>差异内容：NA|类名：RichEditorSymbolSpanStyleResult；<br>API声明：effectStrategy: SymbolEffectStrategy;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanStyleResult；<br>API声明：renderingStrategy: SymbolRenderingStrategy;<br>差异内容：NA|类名：RichEditorSymbolSpanStyleResult；<br>API声明：renderingStrategy: SymbolRenderingStrategy;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorTextSpanResult；<br>API声明：symbolSpanStyle?: RichEditorSymbolSpanStyle;<br>差异内容：NA|类名：RichEditorTextSpanResult；<br>API声明：symbolSpanStyle?: RichEditorSymbolSpanStyle;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorTextSpanResult；<br>API声明：valueResource?: Resource;<br>差异内容：NA|类名：RichEditorTextSpanResult；<br>API声明：valueResource?: Resource;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface RichEditorGesture<br>差异内容：NA|类名：global；<br>API声明：declare interface RichEditorGesture<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorGesture；<br>API声明：onClick?: (event: ClickEvent) => void;<br>差异内容：NA|类名：RichEditorGesture；<br>API声明：onClick?: Callback\<ClickEvent>;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorGesture；<br>API声明：onLongPress?: (event: GestureEvent) => void;<br>差异内容：NA|类名：RichEditorGesture；<br>API声明：onLongPress?: Callback\<GestureEvent>;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorTextSpanOptions；<br>API声明：paragraphStyle?: RichEditorParagraphStyle;<br>差异内容：NA|类名：RichEditorTextSpanOptions；<br>API声明：paragraphStyle?: RichEditorParagraphStyle;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorTextSpanOptions；<br>API声明：gesture?: RichEditorGesture;<br>差异内容：NA|类名：RichEditorTextSpanOptions；<br>API声明：gesture?: RichEditorGesture;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorImageSpanOptions；<br>API声明：gesture?: RichEditorGesture;<br>差异内容：NA|类名：RichEditorImageSpanOptions；<br>API声明：gesture?: RichEditorGesture;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface RichEditorBuilderSpanOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface RichEditorBuilderSpanOptions<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorBuilderSpanOptions；<br>API声明：offset?: number;<br>差异内容：NA|类名：RichEditorBuilderSpanOptions；<br>API声明：offset?: number;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface RichEditorParagraphStyleOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface RichEditorParagraphStyleOptions<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorParagraphStyleOptions；<br>API声明：style: RichEditorParagraphStyle;<br>差异内容：NA|类名：RichEditorParagraphStyleOptions；<br>API声明：style: RichEditorParagraphStyle;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface RichEditorUpdateSymbolSpanStyleOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface RichEditorUpdateSymbolSpanStyleOptions<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorUpdateSymbolSpanStyleOptions；<br>API声明：symbolStyle: RichEditorSymbolSpanStyle;<br>差异内容：NA|类名：RichEditorUpdateSymbolSpanStyleOptions；<br>API声明：symbolStyle: RichEditorSymbolSpanStyle;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface RichEditorSymbolSpanOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface RichEditorSymbolSpanOptions<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanOptions；<br>API声明：offset?: number;<br>差异内容：NA|类名：RichEditorSymbolSpanOptions；<br>API声明：offset?: number;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorSymbolSpanOptions；<br>API声明：style?: RichEditorSymbolSpanStyle;<br>差异内容：NA|类名：RichEditorSymbolSpanOptions；<br>API声明：style?: RichEditorSymbolSpanStyle;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorController；<br>API声明：addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number;<br>差异内容：NA|类名：RichEditorController；<br>API声明：addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorController；<br>API声明：addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions): number;<br>差异内容：NA|类名：RichEditorController；<br>API声明：addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions): number;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorController；<br>API声明：updateParagraphStyle(value: RichEditorParagraphStyleOptions): void;<br>差异内容：NA|类名：RichEditorController；<br>API声明：updateParagraphStyle(value: RichEditorParagraphStyleOptions): void;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorController；<br>API声明：getParagraphs(value?: RichEditorRange): Array\<RichEditorParagraphResult>;<br>差异内容：NA|类名：RichEditorController；<br>API声明：getParagraphs(value?: RichEditorRange): Array\<RichEditorParagraphResult>;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorController；<br>API声明：getSelection(): RichEditorSelection;<br>差异内容：NA|类名：RichEditorController；<br>API声明：getSelection(): RichEditorSelection;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorAttribute；<br>API声明：onPaste(callback: (event?: PasteEvent) => void): RichEditorAttribute;<br>差异内容：NA|类名：RichEditorAttribute；<br>API声明：onPaste(callback: PasteEventCallback): RichEditorAttribute;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorAttribute；<br>API声明：enableDataDetector(enable: boolean): RichEditorAttribute;<br>差异内容：NA|类名：RichEditorAttribute；<br>API声明：enableDataDetector(enable: boolean): RichEditorAttribute;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：RichEditorAttribute；<br>API声明：dataDetectorConfig(config: TextDataDetectorConfig): RichEditorAttribute;<br>差异内容：NA|类名：RichEditorAttribute；<br>API声明：dataDetectorConfig(config: TextDataDetectorConfig): RichEditorAttribute;<br>差异内容：atomicservice|component/rich_editor.d.ts|
|API从不支持元服务到支持元服务|类名：Scroller；<br>API声明：getItemRect(index: number): RectResult;<br>差异内容：NA|类名：Scroller；<br>API声明：getItemRect(index: number): RectResult;<br>差异内容：atomicservice|component/scroll.d.ts|
|API从不支持元服务到支持元服务|类名：ScrollAttribute；<br>API声明：enablePaging(value: boolean): ScrollAttribute;<br>差异内容：NA|类名：ScrollAttribute；<br>API声明：enablePaging(value: boolean): ScrollAttribute;<br>差异内容：atomicservice|component/scroll.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum SearchType<br>差异内容：NA|类名：global；<br>API声明：declare enum SearchType<br>差异内容：atomicservice|component/search.d.ts|
|API从不支持元服务到支持元服务|类名：SearchType；<br>API声明：NORMAL = 0<br>差异内容：NA|类名：SearchType；<br>API声明：NORMAL = 0<br>差异内容：atomicservice|component/search.d.ts|
|API从不支持元服务到支持元服务|类名：SearchType；<br>API声明：NUMBER = 2<br>差异内容：NA|类名：SearchType；<br>API声明：NUMBER = 2<br>差异内容：atomicservice|component/search.d.ts|
|API从不支持元服务到支持元服务|类名：SearchType；<br>API声明：PHONE_NUMBER = 3<br>差异内容：NA|类名：SearchType；<br>API声明：PHONE_NUMBER = 3<br>差异内容：atomicservice|component/search.d.ts|
|API从不支持元服务到支持元服务|类名：SearchType；<br>API声明：EMAIL = 5<br>差异内容：NA|类名：SearchType；<br>API声明：EMAIL = 5<br>差异内容：atomicservice|component/search.d.ts|
|API从不支持元服务到支持元服务|类名：SearchAttribute；<br>API声明：maxLength(value: number): SearchAttribute;<br>差异内容：NA|类名：SearchAttribute；<br>API声明：maxLength(value: number): SearchAttribute;<br>差异内容：atomicservice|component/search.d.ts|
|API从不支持元服务到支持元服务|类名：SearchAttribute；<br>API声明：type(value: SearchType): SearchAttribute;<br>差异内容：NA|类名：SearchAttribute；<br>API声明：type(value: SearchType): SearchAttribute;<br>差异内容：atomicservice|component/search.d.ts|
|API从不支持元服务到支持元服务|类名：SecurityComponentMethod；<br>API声明：width(value: Length): T;<br>差异内容：NA|类名：SecurityComponentMethod；<br>API声明：width(value: Length): T;<br>差异内容：atomicservice|component/security_component.d.ts|
|API从不支持元服务到支持元服务|类名：SecurityComponentMethod；<br>API声明：height(value: Length): T;<br>差异内容：NA|类名：SecurityComponentMethod；<br>API声明：height(value: Length): T;<br>差异内容：atomicservice|component/security_component.d.ts|
|API从不支持元服务到支持元服务|类名：SecurityComponentMethod；<br>API声明：size(value: SizeOptions): T;<br>差异内容：NA|类名：SecurityComponentMethod；<br>API声明：size(value: SizeOptions): T;<br>差异内容：atomicservice|component/security_component.d.ts|
|API从不支持元服务到支持元服务|类名：SecurityComponentMethod；<br>API声明：constraintSize(value: ConstraintSizeOptions): T;<br>差异内容：NA|类名：SecurityComponentMethod；<br>API声明：constraintSize(value: ConstraintSizeOptions): T;<br>差异内容：atomicservice|component/security_component.d.ts|
|API从不支持元服务到支持元服务|类名：SelectAttribute；<br>API声明：optionWidth(value: Dimension \| OptionWidthMode): SelectAttribute;<br>差异内容：NA|类名：SelectAttribute；<br>API声明：optionWidth(value: Dimension \| OptionWidthMode): SelectAttribute;<br>差异内容：atomicservice|component/select.d.ts|
|API从不支持元服务到支持元服务|类名：SelectAttribute；<br>API声明：optionHeight(value: Dimension): SelectAttribute;<br>差异内容：NA|类名：SelectAttribute；<br>API声明：optionHeight(value: Dimension): SelectAttribute;<br>差异内容：atomicservice|component/select.d.ts|
|API从不支持元服务到支持元服务|类名：SelectAttribute；<br>API声明：menuBackgroundColor(value: ResourceColor): SelectAttribute;<br>差异内容：NA|类名：SelectAttribute；<br>API声明：menuBackgroundColor(value: ResourceColor): SelectAttribute;<br>差异内容：atomicservice|component/select.d.ts|
|API从不支持元服务到支持元服务|类名：SelectAttribute；<br>API声明：menuBackgroundBlurStyle(value: BlurStyle): SelectAttribute;<br>差异内容：NA|类名：SelectAttribute；<br>API声明：menuBackgroundBlurStyle(value: BlurStyle): SelectAttribute;<br>差异内容：atomicservice|component/select.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface TextBackgroundStyle<br>差异内容：NA|类名：global；<br>API声明：declare interface TextBackgroundStyle<br>差异内容：atomicservice|component/span.d.ts|
|API从不支持元服务到支持元服务|类名：TextBackgroundStyle；<br>API声明：color?: ResourceColor;<br>差异内容：NA|类名：TextBackgroundStyle；<br>API声明：color?: ResourceColor;<br>差异内容：atomicservice|component/span.d.ts|
|API从不支持元服务到支持元服务|类名：TextBackgroundStyle；<br>API声明：radius?: Dimension \| BorderRadiuses;<br>差异内容：NA|类名：TextBackgroundStyle；<br>API声明：radius?: Dimension \| BorderRadiuses;<br>差异内容：atomicservice|component/span.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class BaseSpan<br>差异内容：NA|类名：global；<br>API声明：declare class BaseSpan<br>差异内容：atomicservice|component/span.d.ts|
|API从不支持元服务到支持元服务|类名：BaseSpan；<br>API声明：textBackgroundStyle(style: TextBackgroundStyle): T;<br>差异内容：NA|类名：BaseSpan；<br>API声明：textBackgroundStyle(style: TextBackgroundStyle): T;<br>差异内容：atomicservice|component/span.d.ts|
|API从不支持元服务到支持元服务|类名：SpanAttribute；<br>API声明：textShadow(value: ShadowOptions \| Array\<ShadowOptions>): SpanAttribute;<br>差异内容：NA|类名：SpanAttribute；<br>API声明：textShadow(value: ShadowOptions \| Array\<ShadowOptions>): SpanAttribute;<br>差异内容：atomicservice|component/span.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface SymbolGlyphInterface<br>差异内容：NA|类名：global；<br>API声明：interface SymbolGlyphInterface<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum SymbolRenderingStrategy<br>差异内容：NA|类名：global；<br>API声明：declare enum SymbolRenderingStrategy<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolRenderingStrategy；<br>API声明：SINGLE = 0<br>差异内容：NA|类名：SymbolRenderingStrategy；<br>API声明：SINGLE = 0<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_COLOR = 1<br>差异内容：NA|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_COLOR = 1<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_OPACITY = 2<br>差异内容：NA|类名：SymbolRenderingStrategy；<br>API声明：MULTIPLE_OPACITY = 2<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum SymbolEffectStrategy<br>差异内容：NA|类名：global；<br>API声明：declare enum SymbolEffectStrategy<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolEffectStrategy；<br>API声明：NONE = 0<br>差异内容：NA|类名：SymbolEffectStrategy；<br>API声明：NONE = 0<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolEffectStrategy；<br>API声明：SCALE = 1<br>差异内容：NA|类名：SymbolEffectStrategy；<br>API声明：SCALE = 1<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolEffectStrategy；<br>API声明：HIERARCHICAL = 2<br>差异内容：NA|类名：SymbolEffectStrategy；<br>API声明：HIERARCHICAL = 2<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class SymbolGlyphAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class SymbolGlyphAttribute<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolGlyphAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolGlyphAttribute;<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolGlyphAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolGlyphAttribute;<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolGlyphAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolGlyphAttribute;<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolGlyphAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolGlyphAttribute;<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolGlyphAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolGlyphAttribute;<br>差异内容：NA|类名：SymbolGlyphAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolGlyphAttribute;<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const SymbolGlyph: SymbolGlyphInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const SymbolGlyph: SymbolGlyphInterface;<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const SymbolGlyphInstance: SymbolGlyphAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const SymbolGlyphInstance: SymbolGlyphAttribute;<br>差异内容：atomicservice|component/symbolglyph.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface SymbolSpanInterface<br>差异内容：NA|类名：global；<br>API声明：interface SymbolSpanInterface<br>差异内容：atomicservice|component/symbol_span.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class SymbolSpanAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class SymbolSpanAttribute<br>差异内容：atomicservice|component/symbol_span.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolSpanAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：fontSize(value: number \| string \| Resource): SymbolSpanAttribute;<br>差异内容：atomicservice|component/symbol_span.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolSpanAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：fontColor(value: Array\<ResourceColor>): SymbolSpanAttribute;<br>差异内容：atomicservice|component/symbol_span.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolSpanAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：fontWeight(value: number \| FontWeight \| string): SymbolSpanAttribute;<br>差异内容：atomicservice|component/symbol_span.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolSpanAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：effectStrategy(value: SymbolEffectStrategy): SymbolSpanAttribute;<br>差异内容：atomicservice|component/symbol_span.d.ts|
|API从不支持元服务到支持元服务|类名：SymbolSpanAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolSpanAttribute;<br>差异内容：NA|类名：SymbolSpanAttribute；<br>API声明：renderingStrategy(value: SymbolRenderingStrategy): SymbolSpanAttribute;<br>差异内容：atomicservice|component/symbol_span.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const SymbolSpan: SymbolSpanInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const SymbolSpan: SymbolSpanInterface;<br>差异内容：atomicservice|component/symbol_span.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const SymbolSpanInstance: SymbolSpanAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const SymbolSpanInstance: SymbolSpanAttribute;<br>差异内容：atomicservice|component/symbol_span.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface TabsAnimationEvent<br>差异内容：NA|类名：global；<br>API声明：declare interface TabsAnimationEvent<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabsAnimationEvent；<br>API声明：currentOffset: number;<br>差异内容：NA|类名：TabsAnimationEvent；<br>API声明：currentOffset: number;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabsAnimationEvent；<br>API声明：targetOffset: number;<br>差异内容：NA|类名：TabsAnimationEvent；<br>API声明：targetOffset: number;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabsAnimationEvent；<br>API声明：velocity: number;<br>差异内容：NA|类名：TabsAnimationEvent；<br>API声明：velocity: number;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabsAttribute；<br>API声明：onAnimationStart(handler: (index: number, targetIndex: number, event: TabsAnimationEvent) => void): TabsAttribute;<br>差异内容：NA|类名：TabsAttribute；<br>API声明：onAnimationStart(handler: (index: number, targetIndex: number, event: TabsAnimationEvent) => void): TabsAttribute;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabsAttribute；<br>API声明：onAnimationEnd(handler: (index: number, event: TabsAnimationEvent) => void): TabsAttribute;<br>差异内容：NA|类名：TabsAttribute；<br>API声明：onAnimationEnd(handler: (index: number, event: TabsAnimationEvent) => void): TabsAttribute;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabsAttribute；<br>API声明：onGestureSwipe(handler: (index: number, event: TabsAnimationEvent) => void): TabsAttribute;<br>差异内容：NA|类名：TabsAttribute；<br>API声明：onGestureSwipe(handler: (index: number, event: TabsAnimationEvent) => void): TabsAttribute;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabsAttribute；<br>API声明：customContentTransition(delegate: (from: number, to: number) => TabContentAnimatedTransition \| undefined): TabsAttribute;<br>差异内容：NA|类名：TabsAttribute；<br>API声明：customContentTransition(delegate: (from: number, to: number) => TabContentAnimatedTransition \| undefined): TabsAttribute;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface TabContentAnimatedTransition<br>差异内容：NA|类名：global；<br>API声明：declare interface TabContentAnimatedTransition<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabContentAnimatedTransition；<br>API声明：timeout?: number;<br>差异内容：NA|类名：TabContentAnimatedTransition；<br>API声明：timeout?: number;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabContentAnimatedTransition；<br>API声明：transition: (proxy: TabContentTransitionProxy) => void;<br>差异内容：NA|类名：TabContentAnimatedTransition；<br>API声明：transition: (proxy: TabContentTransitionProxy) => void;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface TabContentTransitionProxy<br>差异内容：NA|类名：global；<br>API声明：declare interface TabContentTransitionProxy<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabContentTransitionProxy；<br>API声明：from: number;<br>差异内容：NA|类名：TabContentTransitionProxy；<br>API声明：from: number;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabContentTransitionProxy；<br>API声明：to: number;<br>差异内容：NA|类名：TabContentTransitionProxy；<br>API声明：to: number;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：TabContentTransitionProxy；<br>API声明：finishTransition(): void;<br>差异内容：NA|类名：TabContentTransitionProxy；<br>API声明：finishTransition(): void;<br>差异内容：atomicservice|component/tabs.d.ts|
|API从不支持元服务到支持元服务|类名：SubTabBarStyle；<br>API声明：id(value: string): SubTabBarStyle;<br>差异内容：NA|类名：SubTabBarStyle；<br>API声明：id(value: string): SubTabBarStyle;<br>差异内容：atomicservice|component/tab_content.d.ts|
|API从不支持元服务到支持元服务|类名：BottomTabBarStyle；<br>API声明：id(value: string): BottomTabBarStyle;<br>差异内容：NA|类名：BottomTabBarStyle；<br>API声明：id(value: string): BottomTabBarStyle;<br>差异内容：atomicservice|component/tab_content.d.ts|
|API从不支持元服务到支持元服务|类名：TextAttribute；<br>API声明：ellipsisMode(value: EllipsisMode): TextAttribute;<br>差异内容：NA|类名：TextAttribute；<br>API声明：ellipsisMode(value: EllipsisMode): TextAttribute;<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextAttribute；<br>API声明：enableDataDetector(enable: boolean): TextAttribute;<br>差异内容：NA|类名：TextAttribute；<br>API声明：enableDataDetector(enable: boolean): TextAttribute;<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextAttribute；<br>API声明：dataDetectorConfig(config: TextDataDetectorConfig): TextAttribute;<br>差异内容：NA|类名：TextAttribute；<br>API声明：dataDetectorConfig(config: TextDataDetectorConfig): TextAttribute;<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextAttribute；<br>API声明：bindSelectionMenu(spanType: TextSpanType, content: CustomBuilder, responseType: TextResponseType, options?: SelectionMenuOptions): TextAttribute;<br>差异内容：NA|类名：TextAttribute；<br>API声明：bindSelectionMenu(spanType: TextSpanType, content: CustomBuilder, responseType: TextResponseType, options?: SelectionMenuOptions): TextAttribute;<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextAttribute；<br>API声明：onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void): TextAttribute;<br>差异内容：NA|类名：TextAttribute；<br>API声明：onTextSelectionChange(callback: (selectionStart: number, selectionEnd: number) => void): TextAttribute;<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum TextSpanType<br>差异内容：NA|类名：global；<br>API声明：declare enum TextSpanType<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextSpanType；<br>API声明：TEXT = 0<br>差异内容：NA|类名：TextSpanType；<br>API声明：TEXT = 0<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextSpanType；<br>API声明：IMAGE = 1<br>差异内容：NA|类名：TextSpanType；<br>API声明：IMAGE = 1<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextSpanType；<br>API声明：MIXED = 2<br>差异内容：NA|类名：TextSpanType；<br>API声明：MIXED = 2<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum TextResponseType<br>差异内容：NA|类名：global；<br>API声明：declare enum TextResponseType<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextResponseType；<br>API声明：RIGHT_CLICK = 0<br>差异内容：NA|类名：TextResponseType；<br>API声明：RIGHT_CLICK = 0<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextResponseType；<br>API声明：LONG_PRESS = 1<br>差异内容：NA|类名：TextResponseType；<br>API声明：LONG_PRESS = 1<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextResponseType；<br>API声明：SELECT = 2<br>差异内容：NA|类名：TextResponseType；<br>API声明：SELECT = 2<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface TextOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface TextOptions<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextOptions；<br>API声明：controller: TextController;<br>差异内容：NA|类名：TextOptions；<br>API声明：controller: TextController;<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class TextController<br>差异内容：NA|类名：global；<br>API声明：declare class TextController<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：TextController；<br>API声明：closeSelectionMenu(): void;<br>差异内容：NA|类名：TextController；<br>API声明：closeSelectionMenu(): void;<br>差异内容：atomicservice|component/text.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum TextAreaType<br>差异内容：NA|类名：global；<br>API声明：declare enum TextAreaType<br>差异内容：atomicservice|component/text_area.d.ts|
|API从不支持元服务到支持元服务|类名：TextAreaType；<br>API声明：NORMAL = 0<br>差异内容：NA|类名：TextAreaType；<br>API声明：NORMAL = 0<br>差异内容：atomicservice|component/text_area.d.ts|
|API从不支持元服务到支持元服务|类名：TextAreaType；<br>API声明：NUMBER = 2<br>差异内容：NA|类名：TextAreaType；<br>API声明：NUMBER = 2<br>差异内容：atomicservice|component/text_area.d.ts|
|API从不支持元服务到支持元服务|类名：TextAreaType；<br>API声明：PHONE_NUMBER = 3<br>差异内容：NA|类名：TextAreaType；<br>API声明：PHONE_NUMBER = 3<br>差异内容：atomicservice|component/text_area.d.ts|
|API从不支持元服务到支持元服务|类名：TextAreaType；<br>API声明：EMAIL = 5<br>差异内容：NA|类名：TextAreaType；<br>API声明：EMAIL = 5<br>差异内容：atomicservice|component/text_area.d.ts|
|API从不支持元服务到支持元服务|类名：TextAreaAttribute；<br>API声明：enterKeyType(value: EnterKeyType): TextAreaAttribute;<br>差异内容：NA|类名：TextAreaAttribute；<br>API声明：enterKeyType(value: EnterKeyType): TextAreaAttribute;<br>差异内容：atomicservice|component/text_area.d.ts|
|API从不支持元服务到支持元服务|类名：TextAreaAttribute；<br>API声明：onSubmit(callback: (enterKey: EnterKeyType) => void): TextAreaAttribute;<br>差异内容：NA|类名：TextAreaAttribute；<br>API声明：onSubmit(callback: (enterKey: EnterKeyType) => void): TextAreaAttribute;<br>差异内容：atomicservice|component/text_area.d.ts|
|API从不支持元服务到支持元服务|类名：TextAreaAttribute；<br>API声明：type(value: TextAreaType): TextAreaAttribute;<br>差异内容：NA|类名：TextAreaAttribute；<br>API声明：type(value: TextAreaType): TextAreaAttribute;<br>差异内容：atomicservice|component/text_area.d.ts|
|API从不支持元服务到支持元服务|类名：TextClockAttribute；<br>API声明：textShadow(value: ShadowOptions \| Array\<ShadowOptions>): TextClockAttribute;<br>差异内容：NA|类名：TextClockAttribute；<br>API声明：textShadow(value: ShadowOptions \| Array\<ShadowOptions>): TextClockAttribute;<br>差异内容：atomicservice|component/text_clock.d.ts|
|API从不支持元服务到支持元服务|类名：TextClockAttribute；<br>API声明：fontFeature(value: string): TextClockAttribute;<br>差异内容：NA|类名：TextClockAttribute；<br>API声明：fontFeature(value: string): TextClockAttribute;<br>差异内容：atomicservice|component/text_clock.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum TextDataDetectorType<br>差异内容：NA|类名：global；<br>API声明：declare enum TextDataDetectorType<br>差异内容：atomicservice|component/text_common.d.ts|
|API从不支持元服务到支持元服务|类名：TextDataDetectorType；<br>API声明：PHONE_NUMBER = 0<br>差异内容：NA|类名：TextDataDetectorType；<br>API声明：PHONE_NUMBER = 0<br>差异内容：atomicservice|component/text_common.d.ts|
|API从不支持元服务到支持元服务|类名：TextDataDetectorType；<br>API声明：URL = 1<br>差异内容：NA|类名：TextDataDetectorType；<br>API声明：URL = 1<br>差异内容：atomicservice|component/text_common.d.ts|
|API从不支持元服务到支持元服务|类名：TextDataDetectorType；<br>API声明：EMAIL = 2<br>差异内容：NA|类名：TextDataDetectorType；<br>API声明：EMAIL = 2<br>差异内容：atomicservice|component/text_common.d.ts|
|API从不支持元服务到支持元服务|类名：TextDataDetectorType；<br>API声明：ADDRESS = 3<br>差异内容：NA|类名：TextDataDetectorType；<br>API声明：ADDRESS = 3<br>差异内容：atomicservice|component/text_common.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface TextDataDetectorConfig<br>差异内容：NA|类名：global；<br>API声明：declare interface TextDataDetectorConfig<br>差异内容：atomicservice|component/text_common.d.ts|
|API从不支持元服务到支持元服务|类名：TextDataDetectorConfig；<br>API声明：types: TextDataDetectorType[];<br>差异内容：NA|类名：TextDataDetectorConfig；<br>API声明：types: TextDataDetectorType[];<br>差异内容：atomicservice|component/text_common.d.ts|
|API从不支持元服务到支持元服务|类名：TextDataDetectorConfig；<br>API声明：onDetectResultUpdate?: (result: string) => void;<br>差异内容：NA|类名：TextDataDetectorConfig；<br>API声明：onDetectResultUpdate?: (result: string) => void;<br>差异内容：atomicservice|component/text_common.d.ts|
|API从不支持元服务到支持元服务|类名：InputType；<br>API声明：NUMBER_PASSWORD = 8<br>差异内容：NA|类名：InputType；<br>API声明：NUMBER_PASSWORD = 8<br>差异内容：atomicservice|component/text_input.d.ts|
|API从不支持元服务到支持元服务|类名：InputType；<br>API声明：USER_NAME = 10<br>差异内容：NA|类名：InputType；<br>API声明：USER_NAME = 10<br>差异内容：atomicservice|component/text_input.d.ts|
|API从不支持元服务到支持元服务|类名：InputType；<br>API声明：NEW_PASSWORD = 11<br>差异内容：NA|类名：InputType；<br>API声明：NEW_PASSWORD = 11<br>差异内容：atomicservice|component/text_input.d.ts|
|API从不支持元服务到支持元服务|类名：EnterKeyType；<br>API声明：PREVIOUS = 7<br>差异内容：NA|类名：EnterKeyType；<br>API声明：PREVIOUS = 7<br>差异内容：atomicservice|component/text_input.d.ts|
|API从不支持元服务到支持元服务|类名：EnterKeyType；<br>API声明：NEW_LINE = 8<br>差异内容：NA|类名：EnterKeyType；<br>API声明：NEW_LINE = 8<br>差异内容：atomicservice|component/text_input.d.ts|
|API从不支持元服务到支持元服务|类名：TextInputAttribute；<br>API声明：cancelButton(value: {<br>        style?: CancelButtonStyle;<br>        icon?: IconOptions;<br>    }): TextInputAttribute;<br>差异内容：NA|类名：TextInputAttribute；<br>API声明：cancelButton(value: {<br>        style?: CancelButtonStyle;<br>        icon?: IconOptions;<br>    }): TextInputAttribute;<br>差异内容：atomicservice|component/text_input.d.ts|
|API从不支持元服务到支持元服务|类名：TextInputAttribute；<br>API声明：selectAll(value: boolean): TextInputAttribute;<br>差异内容：NA|类名：TextInputAttribute；<br>API声明：selectAll(value: boolean): TextInputAttribute;<br>差异内容：atomicservice|component/text_input.d.ts|
|API从不支持元服务到支持元服务|类名：TextInputAttribute；<br>API声明：enableAutoFill(value: boolean): TextInputAttribute;<br>差异内容：NA|类名：TextInputAttribute；<br>API声明：enableAutoFill(value: boolean): TextInputAttribute;<br>差异内容：atomicservice|component/text_input.d.ts|
|API从不支持元服务到支持元服务|类名：TextInputAttribute；<br>API声明：passwordRules(value: string): TextInputAttribute;<br>差异内容：NA|类名：TextInputAttribute；<br>API声明：passwordRules(value: string): TextInputAttribute;<br>差异内容：atomicservice|component/text_input.d.ts|
|API从不支持元服务到支持元服务|类名：TextPickerDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：NA|类名：TextPickerDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：atomicservice|component/text_picker.d.ts|
|API从不支持元服务到支持元服务|类名：TextPickerDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：TextPickerDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|component/text_picker.d.ts|
|API从不支持元服务到支持元服务|类名：TextTimerAttribute；<br>API声明：textShadow(value: ShadowOptions \| Array\<ShadowOptions>): TextTimerAttribute;<br>差异内容：NA|类名：TextTimerAttribute；<br>API声明：textShadow(value: ShadowOptions \| Array\<ShadowOptions>): TextTimerAttribute;<br>差异内容：atomicservice|component/text_timer.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum TimePickerFormat<br>差异内容：NA|类名：global；<br>API声明：declare enum TimePickerFormat<br>差异内容：atomicservice|component/time_picker.d.ts|
|API从不支持元服务到支持元服务|类名：TimePickerFormat；<br>API声明：HOUR_MINUTE<br>差异内容：NA|类名：TimePickerFormat；<br>API声明：HOUR_MINUTE<br>差异内容：atomicservice|component/time_picker.d.ts|
|API从不支持元服务到支持元服务|类名：TimePickerFormat；<br>API声明：HOUR_MINUTE_SECOND<br>差异内容：NA|类名：TimePickerFormat；<br>API声明：HOUR_MINUTE_SECOND<br>差异内容：atomicservice|component/time_picker.d.ts|
|API从不支持元服务到支持元服务|类名：TimePickerOptions；<br>API声明：format?: TimePickerFormat;<br>差异内容：NA|类名：TimePickerOptions；<br>API声明：format?: TimePickerFormat;<br>差异内容：atomicservice|component/time_picker.d.ts|
|API从不支持元服务到支持元服务|类名：TimePickerAttribute；<br>API声明：loop(value: boolean): TimePickerAttribute;<br>差异内容：NA|类名：TimePickerAttribute；<br>API声明：loop(value: boolean): TimePickerAttribute;<br>差异内容：atomicservice|component/time_picker.d.ts|
|API从不支持元服务到支持元服务|类名：TimePickerDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：NA|类名：TimePickerDialogOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：atomicservice|component/time_picker.d.ts|
|API从不支持元服务到支持元服务|类名：TimePickerDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：TimePickerDialogOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|component/time_picker.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type EdgeOutlineWidths = {<br>    /**<br>     * top outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    top?: Dimension;<br>    /**<br>     * right outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    right?: Dimension;<br>    /**<br>     * bottom outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    bottom?: Dimension;<br>    /**<br>     * left outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    left?: Dimension;<br>};<br>差异内容：NA|类名：global；<br>API声明：declare type EdgeOutlineWidths = {<br>    /**<br>     * top outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * top outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    top?: Dimension;<br>    /**<br>     * right outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * right outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    right?: Dimension;<br>    /**<br>     * bottom outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * bottom outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    bottom?: Dimension;<br>    /**<br>     * left outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * left outline width property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    left?: Dimension;<br>};<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：EdgeOutlineWidths；<br>API声明：top?: Dimension;<br>差异内容：NA|类名：EdgeOutlineWidths；<br>API声明：top?: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：EdgeOutlineWidths；<br>API声明：right?: Dimension;<br>差异内容：NA|类名：EdgeOutlineWidths；<br>API声明：right?: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：EdgeOutlineWidths；<br>API声明：bottom?: Dimension;<br>差异内容：NA|类名：EdgeOutlineWidths；<br>API声明：bottom?: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：EdgeOutlineWidths；<br>API声明：left?: Dimension;<br>差异内容：NA|类名：EdgeOutlineWidths；<br>API声明：left?: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type OutlineRadiuses = {<br>    /**<br>     * top-left property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    topLeft?: Dimension;<br>    /**<br>     * top-right property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    topRight?: Dimension;<br>    /**<br>     * bottom-left property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    bottomLeft?: Dimension;<br>    /**<br>     * bottom-right property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    bottomRight?: Dimension;<br>};<br>差异内容：NA|类名：global；<br>API声明：declare type OutlineRadiuses = {<br>    /**<br>     * top-left property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * top-left property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    topLeft?: Dimension;<br>    /**<br>     * top-right property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * top-right property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    topRight?: Dimension;<br>    /**<br>     * bottom-left property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * bottom-left property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    bottomLeft?: Dimension;<br>    /**<br>     * bottom-right property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * bottom-right property.<br>     *<br>     * @type { ?Dimension }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    bottomRight?: Dimension;<br>};<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineRadiuses；<br>API声明：topLeft?: Dimension;<br>差异内容：NA|类名：OutlineRadiuses；<br>API声明：topLeft?: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineRadiuses；<br>API声明：topRight?: Dimension;<br>差异内容：NA|类名：OutlineRadiuses；<br>API声明：topRight?: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineRadiuses；<br>API声明：bottomLeft?: Dimension;<br>差异内容：NA|类名：OutlineRadiuses；<br>API声明：bottomLeft?: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineRadiuses；<br>API声明：bottomRight?: Dimension;<br>差异内容：NA|类名：OutlineRadiuses；<br>API声明：bottomRight?: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type EdgeOutlineStyles = {<br>    /**<br>     * top property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    top?: OutlineStyle;<br>    /**<br>     * right property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    right?: OutlineStyle;<br>    /**<br>     * bottom property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    bottom?: OutlineStyle;<br>    /**<br>     * left property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    left?: OutlineStyle;<br>};<br>差异内容：NA|类名：global；<br>API声明：declare type EdgeOutlineStyles = {<br>    /**<br>     * top property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * top property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    top?: OutlineStyle;<br>    /**<br>     * right property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * right property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    right?: OutlineStyle;<br>    /**<br>     * bottom property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * bottom property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    bottom?: OutlineStyle;<br>    /**<br>     * left property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @since 11<br>     * @form<br>     */<br>    /**<br>     * left property.<br>     *<br>     * @type { ?OutlineStyle }<br>     * @syscap SystemCapability.ArkUI.ArkUI.Full<br>     * @crossplatform<br>     * @form<br>     * @atomicservice<br>     * @since 12<br>     */<br>    left?: OutlineStyle;<br>};<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：EdgeOutlineStyles；<br>API声明：top?: OutlineStyle;<br>差异内容：NA|类名：EdgeOutlineStyles；<br>API声明：top?: OutlineStyle;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：EdgeOutlineStyles；<br>API声明：right?: OutlineStyle;<br>差异内容：NA|类名：EdgeOutlineStyles；<br>API声明：right?: OutlineStyle;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：EdgeOutlineStyles；<br>API声明：bottom?: OutlineStyle;<br>差异内容：NA|类名：EdgeOutlineStyles；<br>API声明：bottom?: OutlineStyle;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：EdgeOutlineStyles；<br>API声明：left?: OutlineStyle;<br>差异内容：NA|类名：EdgeOutlineStyles；<br>API声明：left?: OutlineStyle;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface Bias<br>差异内容：NA|类名：global；<br>API声明：declare interface Bias<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：Bias；<br>API声明：horizontal?: number;<br>差异内容：NA|类名：Bias；<br>API声明：horizontal?: number;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：Bias；<br>API声明：vertical?: number;<br>差异内容：NA|类名：Bias；<br>API声明：vertical?: number;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface OutlineOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface OutlineOptions<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineOptions；<br>API声明：width?: EdgeOutlineWidths \| Dimension;<br>差异内容：NA|类名：OutlineOptions；<br>API声明：width?: EdgeOutlineWidths \| Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineOptions；<br>API声明：color?: EdgeColors \| ResourceColor;<br>差异内容：NA|类名：OutlineOptions；<br>API声明：color?: EdgeColors \| ResourceColor \| LocalizedEdgeColors;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineOptions；<br>API声明：radius?: OutlineRadiuses \| Dimension;<br>差异内容：NA|类名：OutlineOptions；<br>API声明：radius?: OutlineRadiuses \| Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：OutlineOptions；<br>API声明：style?: EdgeOutlineStyles \| OutlineStyle;<br>差异内容：NA|类名：OutlineOptions；<br>API声明：style?: EdgeOutlineStyles \| OutlineStyle;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare interface TouchPoint<br>差异内容：NA|类名：global；<br>API声明：declare interface TouchPoint<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：TouchPoint；<br>API声明：x: Dimension;<br>差异内容：NA|类名：TouchPoint；<br>API声明：x: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：TouchPoint；<br>API声明：y: Dimension;<br>差异内容：NA|类名：TouchPoint；<br>API声明：y: Dimension;<br>差异内容：atomicservice|component/units.d.ts|
|API从不支持元服务到支持元服务|类名：WaterFlowAttribute；<br>API声明：cachedCount(value: number): WaterFlowAttribute;<br>差异内容：NA|类名：WaterFlowAttribute；<br>API声明：cachedCount(value: number): WaterFlowAttribute;<br>差异内容：atomicservice|component/water_flow.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class XComponentController<br>差异内容：NA|类名：global；<br>API声明：declare class XComponentController<br>差异内容：atomicservice|component/xcomponent.d.ts|
|API从不支持元服务到支持元服务|类名：XComponentController；<br>API声明：getXComponentSurfaceId(): string;<br>差异内容：NA|类名：XComponentController；<br>API声明：getXComponentSurfaceId(): string;<br>差异内容：atomicservice|component/xcomponent.d.ts|
|API从不支持元服务到支持元服务|类名：XComponentController；<br>API声明：getXComponentContext(): Object;<br>差异内容：NA|类名：XComponentController；<br>API声明：getXComponentContext(): Object;<br>差异内容：atomicservice|component/xcomponent.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface XComponentInterface<br>差异内容：NA|类名：global；<br>API声明：interface XComponentInterface<br>差异内容：atomicservice|component/xcomponent.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class XComponentAttribute<br>差异内容：NA|类名：global；<br>API声明：declare class XComponentAttribute<br>差异内容：atomicservice|component/xcomponent.d.ts|
|API从不支持元服务到支持元服务|类名：XComponentAttribute；<br>API声明：onLoad(callback: (event?: object) => void): XComponentAttribute;<br>差异内容：NA|类名：XComponentAttribute；<br>API声明：onLoad(callback: (event?: object) => void): XComponentAttribute;<br>差异内容：atomicservice|component/xcomponent.d.ts|
|API从不支持元服务到支持元服务|类名：XComponentAttribute；<br>API声明：onDestroy(event: () => void): XComponentAttribute;<br>差异内容：NA|类名：XComponentAttribute；<br>API声明：onDestroy(event: () => void): XComponentAttribute;<br>差异内容：atomicservice|component/xcomponent.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const XComponent: XComponentInterface;<br>差异内容：NA|类名：global；<br>API声明：declare const XComponent: XComponentInterface;<br>差异内容：atomicservice|component/xcomponent.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare const XComponentInstance: XComponentAttribute;<br>差异内容：NA|类名：global；<br>API声明：declare const XComponentInstance: XComponentAttribute;<br>差异内容：atomicservice|component/xcomponent.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export declare enum ChipSize<br>差异内容：NA|类名：global；<br>API声明：export declare enum ChipSize<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipSize；<br>API声明：NORMAL = "NORMAL"<br>差异内容：NA|类名：ChipSize；<br>API声明：NORMAL = "NORMAL"<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipSize；<br>API声明：SMALL = "SMALL"<br>差异内容：NA|类名：ChipSize；<br>API声明：SMALL = "SMALL"<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface IconCommonOptions<br>差异内容：NA|类名：global；<br>API声明：export interface IconCommonOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：IconCommonOptions；<br>API声明：src: ResourceStr;<br>差异内容：NA|类名：IconCommonOptions；<br>API声明：src: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：IconCommonOptions；<br>API声明：size?: SizeOptions;<br>差异内容：NA|类名：IconCommonOptions；<br>API声明：size?: SizeOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：IconCommonOptions；<br>API声明：fillColor?: ResourceColor;<br>差异内容：NA|类名：IconCommonOptions；<br>API声明：fillColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface SuffixIconOptions<br>差异内容：NA|类名：global；<br>API声明：export interface SuffixIconOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：SuffixIconOptions；<br>API声明：action?: () => void;<br>差异内容：NA|类名：SuffixIconOptions；<br>API声明：action?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface PrefixIconOptions<br>差异内容：NA|类名：global；<br>API声明：export interface PrefixIconOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface LabelMarginOptions<br>差异内容：NA|类名：global；<br>API声明：export interface LabelMarginOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：LabelMarginOptions；<br>API声明：left?: Dimension;<br>差异内容：NA|类名：LabelMarginOptions；<br>API声明：left?: Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：LabelMarginOptions；<br>API声明：right?: Dimension;<br>差异内容：NA|类名：LabelMarginOptions；<br>API声明：right?: Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface LabelOptions<br>差异内容：NA|类名：global；<br>API声明：export interface LabelOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：LabelOptions；<br>API声明：text: string;<br>差异内容：NA|类名：LabelOptions；<br>API声明：text: string;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：LabelOptions；<br>API声明：fontSize?: Dimension;<br>差异内容：NA|类名：LabelOptions；<br>API声明：fontSize?: Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：LabelOptions；<br>API声明：fontColor?: ResourceColor;<br>差异内容：NA|类名：LabelOptions；<br>API声明：fontColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：LabelOptions；<br>API声明：fontFamily?: string;<br>差异内容：NA|类名：LabelOptions；<br>API声明：fontFamily?: string;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：LabelOptions；<br>API声明：labelMargin?: LabelMarginOptions;<br>差异内容：NA|类名：LabelOptions；<br>API声明：labelMargin?: LabelMarginOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface ChipOptions<br>差异内容：NA|类名：global；<br>API声明：export interface ChipOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipOptions；<br>API声明：prefixIcon?: PrefixIconOptions;<br>差异内容：NA|类名：ChipOptions；<br>API声明：prefixIcon?: PrefixIconOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipOptions；<br>API声明：label: LabelOptions;<br>差异内容：NA|类名：ChipOptions；<br>API声明：label: LabelOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipOptions；<br>API声明：suffixIcon?: SuffixIconOptions;<br>差异内容：NA|类名：ChipOptions；<br>API声明：suffixIcon?: SuffixIconOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipOptions；<br>API声明：allowClose?: boolean;<br>差异内容：NA|类名：ChipOptions；<br>API声明：allowClose?: boolean;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipOptions；<br>API声明：enabled?: boolean;<br>差异内容：NA|类名：ChipOptions；<br>API声明：enabled?: boolean;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：NA|类名：ChipOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipOptions；<br>API声明：borderRadius?: Dimension;<br>差异内容：NA|类名：ChipOptions；<br>API声明：borderRadius?: Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipOptions；<br>API声明：size?: ChipSize \| SizeOptions;<br>差异内容：NA|类名：ChipOptions；<br>API声明：size?: ChipSize \| SizeOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：ChipOptions；<br>API声明：onClose?: () => void;<br>差异内容：NA|类名：ChipOptions；<br>API声明：onClose?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：@Builder<br>export declare function Chip(options: ChipOptions): void;<br>差异内容：NA|类名：global；<br>API声明：@Builder<br>export declare function Chip(options: ChipOptions): void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Chip.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export class UIObserver<br>差异内容：NA|类名：global；<br>API声明：export class UIObserver<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：UIObserver；<br>API声明：on(type: 'navDestinationUpdate', options: {<br>        navigationId: ResourceStr;<br>    }, callback: Callback\<observer.NavDestinationInfo>): void;<br>差异内容：NA|类名：UIObserver；<br>API声明：on(type: 'navDestinationUpdate', options: {<br>        navigationId: ResourceStr;<br>    }, callback: Callback\<observer.NavDestinationInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：UIObserver；<br>API声明：on(type: 'navDestinationUpdate', callback: Callback\<observer.NavDestinationInfo>): void;<br>差异内容：NA|类名：UIObserver；<br>API声明：on(type: 'navDestinationUpdate', callback: Callback\<observer.NavDestinationInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：UIObserver；<br>API声明：off(type: 'navDestinationUpdate', options: {<br>        navigationId: ResourceStr;<br>    }, callback?: Callback\<observer.NavDestinationInfo>): void;<br>差异内容：NA|类名：UIObserver；<br>API声明：off(type: 'navDestinationUpdate', options: {<br>        navigationId: ResourceStr;<br>    }, callback?: Callback\<observer.NavDestinationInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：UIObserver；<br>API声明：off(type: 'navDestinationUpdate', callback?: Callback\<observer.NavDestinationInfo>): void;<br>差异内容：NA|类名：UIObserver；<br>API声明：off(type: 'navDestinationUpdate', callback?: Callback\<observer.NavDestinationInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：UIObserver；<br>API声明：on(type: 'routerPageUpdate', callback: Callback\<observer.RouterPageInfo>): void;<br>差异内容：NA|类名：UIObserver；<br>API声明：on(type: 'routerPageUpdate', callback: Callback\<observer.RouterPageInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：UIObserver；<br>API声明：off(type: 'routerPageUpdate', callback?: Callback\<observer.RouterPageInfo>): void;<br>差异内容：NA|类名：UIObserver；<br>API声明：off(type: 'routerPageUpdate', callback?: Callback\<observer.RouterPageInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface AtomicServiceBar<br>差异内容：NA|类名：global；<br>API声明：export interface AtomicServiceBar<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：AtomicServiceBar；<br>API声明：setBackgroundColor(color: Nullable\<Color \| number \| string>): void;<br>差异内容：NA|类名：AtomicServiceBar；<br>API声明：setBackgroundColor(color: Nullable\<Color \| number \| string>): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：AtomicServiceBar；<br>API声明：setTitleContent(content: string): void;<br>差异内容：NA|类名：AtomicServiceBar；<br>API声明：setTitleContent(content: string): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：AtomicServiceBar；<br>API声明：setTitleFontStyle(font: FontStyle): void;<br>差异内容：NA|类名：AtomicServiceBar；<br>API声明：setTitleFontStyle(font: FontStyle): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：AtomicServiceBar；<br>API声明：setIconColor(color: Nullable\<Color \| number \| string>): void;<br>差异内容：NA|类名：AtomicServiceBar；<br>API声明：setIconColor(color: Nullable\<Color \| number \| string>): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export class DragController<br>差异内容：NA|类名：global；<br>API声明：export class DragController<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：DragController；<br>API声明：createDragAction(customArray: Array\<CustomBuilder \| DragItemInfo>, dragInfo: dragController.DragInfo): dragController.DragAction;<br>差异内容：NA|类名：DragController；<br>API声明：createDragAction(customArray: Array\<CustomBuilder \| DragItemInfo>, dragInfo: dragController.DragInfo): dragController.DragAction;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：DragController；<br>API声明：getDragPreview(): dragController.DragPreview;<br>差异内容：NA|类名：DragController；<br>API声明：getDragPreview(): dragController.DragPreview;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：UIContext；<br>API声明：getUIObserver(): UIObserver;<br>差异内容：NA|类名：UIContext；<br>API声明：getUIObserver(): UIObserver;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：UIContext；<br>API声明：getDragController(): DragController;<br>差异内容：NA|类名：UIContext；<br>API声明：getDragController(): DragController;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：UIContext；<br>API声明：keyframeAnimateTo(param: KeyframeAnimateParam, keyframes: Array\<KeyframeState>): void;<br>差异内容：NA|类名：UIContext；<br>API声明：keyframeAnimateTo(param: KeyframeAnimateParam, keyframes: Array\<KeyframeState>): void;<br>差异内容：atomicservice|api/@ohos.arkui.UIContext.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare enum CounterType<br>差异内容：NA|类名：global；<br>API声明：declare enum CounterType<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CounterType；<br>API声明：LIST = 0<br>差异内容：NA|类名：CounterType；<br>API声明：LIST = 0<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CounterType；<br>API声明：COMPACT = 1<br>差异内容：NA|类名：CounterType；<br>API声明：COMPACT = 1<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CounterType；<br>API声明：INLINE = 2<br>差异内容：NA|类名：CounterType；<br>API声明：INLINE = 2<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CounterType；<br>API声明：INLINE_DATE = 3<br>差异内容：NA|类名：CounterType；<br>API声明：INLINE_DATE = 3<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class CommonOptions<br>差异内容：NA|类名：global；<br>API声明：declare class CommonOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CommonOptions；<br>API声明：focusable?: boolean;<br>差异内容：NA|类名：CommonOptions；<br>API声明：focusable?: boolean;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CommonOptions；<br>API声明：step?: number;<br>差异内容：NA|类名：CommonOptions；<br>API声明：step?: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CommonOptions；<br>API声明：onHoverIncrease?: (isHover: boolean) => void;<br>差异内容：NA|类名：CommonOptions；<br>API声明：onHoverIncrease?: (isHover: boolean) => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CommonOptions；<br>API声明：onHoverDecrease?: (isHover: boolean) => void;<br>差异内容：NA|类名：CommonOptions；<br>API声明：onHoverDecrease?: (isHover: boolean) => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class InlineStyleOptions<br>差异内容：NA|类名：global；<br>API声明：declare class InlineStyleOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：InlineStyleOptions；<br>API声明：value?: number;<br>差异内容：NA|类名：InlineStyleOptions；<br>API声明：value?: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：InlineStyleOptions；<br>API声明：min?: number;<br>差异内容：NA|类名：InlineStyleOptions；<br>API声明：min?: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：InlineStyleOptions；<br>API声明：max?: number;<br>差异内容：NA|类名：InlineStyleOptions；<br>API声明：max?: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：InlineStyleOptions；<br>API声明：textWidth?: number;<br>差异内容：NA|类名：InlineStyleOptions；<br>API声明：textWidth?: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：InlineStyleOptions；<br>API声明：onChange?: (value: number) => void;<br>差异内容：NA|类名：InlineStyleOptions；<br>API声明：onChange?: (value: number) => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class NumberStyleOptions<br>差异内容：NA|类名：global；<br>API声明：declare class NumberStyleOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：NumberStyleOptions；<br>API声明：label?: ResourceStr;<br>差异内容：NA|类名：NumberStyleOptions；<br>API声明：label?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：NumberStyleOptions；<br>API声明：onFocusIncrease?: () => void;<br>差异内容：NA|类名：NumberStyleOptions；<br>API声明：onFocusIncrease?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：NumberStyleOptions；<br>API声明：onFocusDecrease?: () => void;<br>差异内容：NA|类名：NumberStyleOptions；<br>API声明：onFocusDecrease?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：NumberStyleOptions；<br>API声明：onBlurIncrease?: () => void;<br>差异内容：NA|类名：NumberStyleOptions；<br>API声明：onBlurIncrease?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：NumberStyleOptions；<br>API声明：onBlurDecrease?: () => void;<br>差异内容：NA|类名：NumberStyleOptions；<br>API声明：onBlurDecrease?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class DateData<br>差异内容：NA|类名：global；<br>API声明：declare class DateData<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：DateData；<br>API声明：year: number;<br>差异内容：NA|类名：DateData；<br>API声明：year: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：DateData；<br>API声明：month: number;<br>差异内容：NA|类名：DateData；<br>API声明：month: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：DateData；<br>API声明：day: number;<br>差异内容：NA|类名：DateData；<br>API声明：day: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：DateData；<br>API声明：toString(): string;<br>差异内容：NA|类名：DateData；<br>API声明：toString(): string;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class DateStyleOptions<br>差异内容：NA|类名：global；<br>API声明：declare class DateStyleOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：DateStyleOptions；<br>API声明：year?: number;<br>差异内容：NA|类名：DateStyleOptions；<br>API声明：year?: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：DateStyleOptions；<br>API声明：month?: number;<br>差异内容：NA|类名：DateStyleOptions；<br>API声明：month?: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：DateStyleOptions；<br>API声明：day?: number;<br>差异内容：NA|类名：DateStyleOptions；<br>API声明：day?: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：DateStyleOptions；<br>API声明：onDateChange?: (date: DateData) => void;<br>差异内容：NA|类名：DateStyleOptions；<br>API声明：onDateChange?: (date: DateData) => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class CounterOptions<br>差异内容：NA|类名：global；<br>API声明：declare class CounterOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CounterOptions；<br>API声明：type: CounterType;<br>差异内容：NA|类名：CounterOptions；<br>API声明：type: CounterType;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CounterOptions；<br>API声明：numberOptions?: NumberStyleOptions;<br>差异内容：NA|类名：CounterOptions；<br>API声明：numberOptions?: NumberStyleOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CounterOptions；<br>API声明：inlineOptions?: InlineStyleOptions;<br>差异内容：NA|类名：CounterOptions；<br>API声明：inlineOptions?: InlineStyleOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CounterOptions；<br>API声明：dateOptions?: DateStyleOptions;<br>差异内容：NA|类名：CounterOptions；<br>API声明：dateOptions?: DateStyleOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare struct CounterComponent<br>差异内容：NA|类名：global；<br>API声明：declare struct CounterComponent<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：CounterComponent；<br>API声明：@Prop<br>    options: CounterOptions;<br>差异内容：NA|类名：CounterComponent；<br>API声明：@Prop<br>    options: CounterOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Counter.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export declare enum MarginType<br>差异内容：NA|类名：global；<br>API声明：export declare enum MarginType<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：MarginType；<br>API声明：DEFAULT_MARGIN = 0<br>差异内容：NA|类名：MarginType；<br>API声明：DEFAULT_MARGIN = 0<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：MarginType；<br>API声明：FIT_MARGIN = 1<br>差异内容：NA|类名：MarginType；<br>API声明：FIT_MARGIN = 1<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface PromptOptions<br>差异内容：NA|类名：global；<br>API声明：export interface PromptOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：PromptOptions；<br>API声明：icon?: ResourceStr;<br>差异内容：NA|类名：PromptOptions；<br>API声明：icon?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：PromptOptions；<br>API声明：tip?: ResourceStr;<br>差异内容：NA|类名：PromptOptions；<br>API声明：tip?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：PromptOptions；<br>API声明：marginType: MarginType;<br>差异内容：NA|类名：PromptOptions；<br>API声明：marginType: MarginType;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：PromptOptions；<br>API声明：actionText?: ResourceStr;<br>差异内容：NA|类名：PromptOptions；<br>API声明：actionText?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：PromptOptions；<br>API声明：marginTop: Dimension;<br>差异内容：NA|类名：PromptOptions；<br>API声明：marginTop: Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：PromptOptions；<br>API声明：isShown?: boolean;<br>差异内容：NA|类名：PromptOptions；<br>API声明：isShown?: boolean;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export declare struct ExceptionPrompt<br>差异内容：NA|类名：global；<br>API声明：export declare struct ExceptionPrompt<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：ExceptionPrompt；<br>API声明：@Prop<br>    options: PromptOptions;<br>差异内容：NA|类名：ExceptionPrompt；<br>API声明：@Prop<br>    options: PromptOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：ExceptionPrompt；<br>API声明：onTipClick?: () => void;<br>差异内容：NA|类名：ExceptionPrompt；<br>API声明：onTipClick?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：ExceptionPrompt；<br>API声明：onActionTextClick?: () => void;<br>差异内容：NA|类名：ExceptionPrompt；<br>API声明：onActionTextClick?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：ExceptionPrompt；<br>API声明：build(): void;<br>差异内容：NA|类名：ExceptionPrompt；<br>API声明：build(): void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.ExceptionPrompt.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export declare enum GridObjectSortComponentType<br>差异内容：NA|类名：global；<br>API声明：export declare enum GridObjectSortComponentType<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentType；<br>API声明：IMAGE_TEXT = "image_text"<br>差异内容：NA|类名：GridObjectSortComponentType；<br>API声明：IMAGE_TEXT = "image_text"<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentType；<br>API声明：TEXT = "text"<br>差异内容：NA|类名：GridObjectSortComponentType；<br>API声明：TEXT = "text"<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface GridObjectSortComponentItem<br>差异内容：NA|类名：global；<br>API声明：export interface GridObjectSortComponentItem<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentItem；<br>API声明：id: number \| string;<br>差异内容：NA|类名：GridObjectSortComponentItem；<br>API声明：id: number \| string;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentItem；<br>API声明：text: ResourceStr;<br>差异内容：NA|类名：GridObjectSortComponentItem；<br>API声明：text: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentItem；<br>API声明：selected: boolean;<br>差异内容：NA|类名：GridObjectSortComponentItem；<br>API声明：selected: boolean;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentItem；<br>API声明：order: number;<br>差异内容：NA|类名：GridObjectSortComponentItem；<br>API声明：order: number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentItem；<br>API声明：url?: ResourceStr;<br>差异内容：NA|类名：GridObjectSortComponentItem；<br>API声明：url?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface GridObjectSortComponentOptions<br>差异内容：NA|类名：global；<br>API声明：export interface GridObjectSortComponentOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentOptions；<br>API声明：type?: GridObjectSortComponentType;<br>差异内容：NA|类名：GridObjectSortComponentOptions；<br>API声明：type?: GridObjectSortComponentType;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentOptions；<br>API声明：imageSize?: number \| Resource;<br>差异内容：NA|类名：GridObjectSortComponentOptions；<br>API声明：imageSize?: number \| Resource;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentOptions；<br>API声明：normalTitle?: ResourceStr;<br>差异内容：NA|类名：GridObjectSortComponentOptions；<br>API声明：normalTitle?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentOptions；<br>API声明：editTitle?: ResourceStr;<br>差异内容：NA|类名：GridObjectSortComponentOptions；<br>API声明：editTitle?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentOptions；<br>API声明：showAreaTitle?: ResourceStr;<br>差异内容：NA|类名：GridObjectSortComponentOptions；<br>API声明：showAreaTitle?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponentOptions；<br>API声明：addAreaTitle?: ResourceStr;<br>差异内容：NA|类名：GridObjectSortComponentOptions；<br>API声明：addAreaTitle?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export declare struct GridObjectSortComponent<br>差异内容：NA|类名：global；<br>API声明：export declare struct GridObjectSortComponent<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponent；<br>API声明：@Prop<br>    options: GridObjectSortComponentOptions;<br>差异内容：NA|类名：GridObjectSortComponent；<br>API声明：@Prop<br>    options: GridObjectSortComponentOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponent；<br>API声明：dataList: Array\<GridObjectSortComponentItem>;<br>差异内容：NA|类名：GridObjectSortComponent；<br>API声明：dataList: Array\<GridObjectSortComponentItem>;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponent；<br>API声明：onSave: (select: Array\<GridObjectSortComponentItem>, unselect: Array\<GridObjectSortComponentItem>) => void;<br>差异内容：NA|类名：GridObjectSortComponent；<br>API声明：onSave: (select: Array\<GridObjectSortComponentItem>, unselect: Array\<GridObjectSortComponentItem>) => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponent；<br>API声明：onCancel: () => void;<br>差异内容：NA|类名：GridObjectSortComponent；<br>API声明：onCancel: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：GridObjectSortComponent；<br>API声明：build(): void;<br>差异内容：NA|类名：GridObjectSortComponent；<br>API声明：build(): void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.GridObjectSortComponent.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface PopupTextOptions<br>差异内容：NA|类名：global；<br>API声明：export interface PopupTextOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupTextOptions；<br>API声明：text: ResourceStr;<br>差异内容：NA|类名：PopupTextOptions；<br>API声明：text: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupTextOptions；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：NA|类名：PopupTextOptions；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupTextOptions；<br>API声明：fontColor?: ResourceColor;<br>差异内容：NA|类名：PopupTextOptions；<br>API声明：fontColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupTextOptions；<br>API声明：fontWeight?: number \| FontWeight \| string;<br>差异内容：NA|类名：PopupTextOptions；<br>API声明：fontWeight?: number \| FontWeight \| string;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface PopupButtonOptions<br>差异内容：NA|类名：global；<br>API声明：export interface PopupButtonOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupButtonOptions；<br>API声明：text: ResourceStr;<br>差异内容：NA|类名：PopupButtonOptions；<br>API声明：text: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupButtonOptions；<br>API声明：action?: () => void;<br>差异内容：NA|类名：PopupButtonOptions；<br>API声明：action?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupButtonOptions；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：NA|类名：PopupButtonOptions；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupButtonOptions；<br>API声明：fontColor?: ResourceColor;<br>差异内容：NA|类名：PopupButtonOptions；<br>API声明：fontColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface PopupIconOptions<br>差异内容：NA|类名：global；<br>API声明：export interface PopupIconOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupIconOptions；<br>API声明：image: ResourceStr;<br>差异内容：NA|类名：PopupIconOptions；<br>API声明：image: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupIconOptions；<br>API声明：width?: Dimension;<br>差异内容：NA|类名：PopupIconOptions；<br>API声明：width?: Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupIconOptions；<br>API声明：height?: Dimension;<br>差异内容：NA|类名：PopupIconOptions；<br>API声明：height?: Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupIconOptions；<br>API声明：fillColor?: ResourceColor;<br>差异内容：NA|类名：PopupIconOptions；<br>API声明：fillColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupIconOptions；<br>API声明：borderRadius?: Length \| BorderRadiuses;<br>差异内容：NA|类名：PopupIconOptions；<br>API声明：borderRadius?: Length \| BorderRadiuses;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface PopupOptions<br>差异内容：NA|类名：global；<br>API声明：export interface PopupOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：icon?: PopupIconOptions;<br>差异内容：NA|类名：PopupOptions；<br>API声明：icon?: PopupIconOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：title?: PopupTextOptions;<br>差异内容：NA|类名：PopupOptions；<br>API声明：title?: PopupTextOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：message: PopupTextOptions;<br>差异内容：NA|类名：PopupOptions；<br>API声明：message: PopupTextOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：showClose?: boolean \| Resource;<br>差异内容：NA|类名：PopupOptions；<br>API声明：showClose?: boolean \| Resource;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：onClose?: () => void;<br>差异内容：NA|类名：PopupOptions；<br>API声明：onClose?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：PopupOptions；<br>API声明：buttons?: [<br>        PopupButtonOptions?,<br>        PopupButtonOptions?<br>    ];<br>差异内容：NA|类名：PopupOptions；<br>API声明：buttons?: [<br>        PopupButtonOptions?,<br>        PopupButtonOptions?<br>    ];<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：@Builder<br>export declare function Popup(options: PopupOptions): void;<br>差异内容：NA|类名：global；<br>API声明：@Builder<br>export declare function Popup(options: PopupOptions): void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.Popup.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface SegmentButtonTextItem<br>差异内容：NA|类名：global；<br>API声明：interface SegmentButtonTextItem<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonTextItem；<br>API声明：text: ResourceStr;<br>差异内容：NA|类名：SegmentButtonTextItem；<br>API声明：text: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface SegmentButtonIconItem<br>差异内容：NA|类名：global；<br>API声明：interface SegmentButtonIconItem<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonIconItem；<br>API声明：icon: ResourceStr;<br>差异内容：NA|类名：SegmentButtonIconItem；<br>API声明：icon: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonIconItem；<br>API声明：selectedIcon: ResourceStr;<br>差异内容：NA|类名：SegmentButtonIconItem；<br>API声明：selectedIcon: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface SegmentButtonIconTextItem<br>差异内容：NA|类名：global；<br>API声明：interface SegmentButtonIconTextItem<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonIconTextItem；<br>API声明：icon: ResourceStr;<br>差异内容：NA|类名：SegmentButtonIconTextItem；<br>API声明：icon: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonIconTextItem；<br>API声明：selectedIcon: ResourceStr;<br>差异内容：NA|类名：SegmentButtonIconTextItem；<br>API声明：selectedIcon: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonIconTextItem；<br>API声明：text: ResourceStr;<br>差异内容：NA|类名：SegmentButtonIconTextItem；<br>API声明：text: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type DimensionNoPercentage = PX \| VP \| FP \| LPX \| Resource;<br>差异内容：NA|类名：global；<br>API声明：declare type DimensionNoPercentage = PX \| VP \| FP \| LPX \| Resource;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface CommonSegmentButtonOptions<br>差异内容：NA|类名：global；<br>API声明：interface CommonSegmentButtonOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：fontColor?: ResourceColor;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：fontColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：selectedFontColor?: ResourceColor;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：selectedFontColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：fontSize?: DimensionNoPercentage;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：fontSize?: DimensionNoPercentage;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：selectedFontSize?: DimensionNoPercentage;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：selectedFontSize?: DimensionNoPercentage;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：fontWeight?: FontWeight;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：fontWeight?: FontWeight;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：selectedFontWeight?: FontWeight;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：selectedFontWeight?: FontWeight;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：backgroundColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：selectedBackgroundColor?: ResourceColor;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：selectedBackgroundColor?: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：imageSize?: SizeOptions;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：imageSize?: SizeOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：buttonPadding?: Padding \| Dimension;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：buttonPadding?: Padding \| Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：textPadding?: Padding \| Dimension;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：textPadding?: Padding \| Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CommonSegmentButtonOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：NA|类名：CommonSegmentButtonOptions；<br>API声明：backgroundBlurStyle?: BlurStyle;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type ItemRestriction\<T> = [<br>    T,<br>    T,<br>    T?,<br>    T?,<br>    T?<br>];<br>差异内容：NA|类名：global；<br>API声明：declare type ItemRestriction\<T> = [<br>    T,<br>    T,<br>    T?,<br>    T?,<br>    T?<br>];<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type SegmentButtonItemTuple = ItemRestriction\<SegmentButtonTextItem> \| ItemRestriction\<SegmentButtonIconItem> \| ItemRestriction\<SegmentButtonIconTextItem>;<br>差异内容：NA|类名：global；<br>API声明：declare type SegmentButtonItemTuple = ItemRestriction\<SegmentButtonTextItem> \| ItemRestriction\<SegmentButtonIconItem> \| ItemRestriction\<SegmentButtonIconTextItem>;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare type SegmentButtonItemArray = Array\<SegmentButtonTextItem> \| Array\<SegmentButtonIconItem> \| Array\<SegmentButtonIconTextItem>;<br>差异内容：NA|类名：global；<br>API声明：declare type SegmentButtonItemArray = Array\<SegmentButtonTextItem> \| Array\<SegmentButtonIconItem> \| Array\<SegmentButtonIconTextItem>;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface TabSegmentButtonConstructionOptions<br>差异内容：NA|类名：global；<br>API声明：interface TabSegmentButtonConstructionOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：TabSegmentButtonConstructionOptions；<br>API声明：buttons: ItemRestriction\<SegmentButtonTextItem>;<br>差异内容：NA|类名：TabSegmentButtonConstructionOptions；<br>API声明：buttons: ItemRestriction\<SegmentButtonTextItem>;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface CapsuleSegmentButtonConstructionOptions<br>差异内容：NA|类名：global；<br>API声明：interface CapsuleSegmentButtonConstructionOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CapsuleSegmentButtonConstructionOptions；<br>API声明：buttons: SegmentButtonItemTuple;<br>差异内容：NA|类名：CapsuleSegmentButtonConstructionOptions；<br>API声明：buttons: SegmentButtonItemTuple;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CapsuleSegmentButtonConstructionOptions；<br>API声明：multiply?: boolean;<br>差异内容：NA|类名：CapsuleSegmentButtonConstructionOptions；<br>API声明：multiply?: boolean;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface TabSegmentButtonOptions<br>差异内容：NA|类名：global；<br>API声明：interface TabSegmentButtonOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：TabSegmentButtonOptions；<br>API声明：type: "tab";<br>差异内容：NA|类名：TabSegmentButtonOptions；<br>API声明：type: "tab";<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface CapsuleSegmentButtonOptions<br>差异内容：NA|类名：global；<br>API声明：interface CapsuleSegmentButtonOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：CapsuleSegmentButtonOptions；<br>API声明：type: "capsule";<br>差异内容：NA|类名：CapsuleSegmentButtonOptions；<br>API声明：type: "capsule";<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface SegmentButtonItemOptionsConstructorOptions<br>差异内容：NA|类名：global；<br>API声明：interface SegmentButtonItemOptionsConstructorOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptionsConstructorOptions；<br>API声明：icon?: ResourceStr;<br>差异内容：NA|类名：SegmentButtonItemOptionsConstructorOptions；<br>API声明：icon?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptionsConstructorOptions；<br>API声明：selectedIcon?: ResourceStr;<br>差异内容：NA|类名：SegmentButtonItemOptionsConstructorOptions；<br>API声明：selectedIcon?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptionsConstructorOptions；<br>API声明：text?: ResourceStr;<br>差异内容：NA|类名：SegmentButtonItemOptionsConstructorOptions；<br>API声明：text?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class SegmentButtonItemOptions<br>差异内容：NA|类名：global；<br>API声明：declare class SegmentButtonItemOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptions；<br>API声明：icon?: ResourceStr;<br>差异内容：NA|类名：SegmentButtonItemOptions；<br>API声明：icon?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptions；<br>API声明：selectedIcon?: ResourceStr;<br>差异内容：NA|类名：SegmentButtonItemOptions；<br>API声明：selectedIcon?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptions；<br>API声明：text?: ResourceStr;<br>差异内容：NA|类名：SegmentButtonItemOptions；<br>API声明：text?: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class SegmentButtonItemOptionsArray<br>差异内容：NA|类名：global；<br>API声明：declare class SegmentButtonItemOptionsArray<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptionsArray；<br>API声明：push(...items: SegmentButtonItemArray): number;<br>差异内容：NA|类名：SegmentButtonItemOptionsArray；<br>API声明：push(...items: SegmentButtonItemArray): number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptionsArray；<br>API声明：pop(): SegmentButtonItemOptions \| undefined;<br>差异内容：NA|类名：SegmentButtonItemOptionsArray；<br>API声明：pop(): SegmentButtonItemOptions \| undefined;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptionsArray；<br>API声明：shift(): SegmentButtonItemOptions \| undefined;<br>差异内容：NA|类名：SegmentButtonItemOptionsArray；<br>API声明：shift(): SegmentButtonItemOptions \| undefined;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptionsArray；<br>API声明：unshift(...items: SegmentButtonItemArray): number;<br>差异内容：NA|类名：SegmentButtonItemOptionsArray；<br>API声明：unshift(...items: SegmentButtonItemArray): number;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptionsArray；<br>API声明：splice(start: number, deleteCount: number, ...items: SegmentButtonItemOptions[]): SegmentButtonItemOptions[];<br>差异内容：NA|类名：SegmentButtonItemOptionsArray；<br>API声明：splice(start: number, deleteCount: number, ...items: SegmentButtonItemOptions[]): SegmentButtonItemOptions[];<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonItemOptionsArray；<br>API声明：static create(elements: SegmentButtonItemTuple): SegmentButtonItemOptionsArray;<br>差异内容：NA|类名：SegmentButtonItemOptionsArray；<br>API声明：static create(elements: SegmentButtonItemTuple): SegmentButtonItemOptionsArray;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare class SegmentButtonOptions<br>差异内容：NA|类名：global；<br>API声明：declare class SegmentButtonOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：type: "tab" \| "capsule";<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：type: "tab" \| "capsule";<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：multiply: boolean;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：multiply: boolean;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：buttons: SegmentButtonItemOptionsArray;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：buttons: SegmentButtonItemOptionsArray;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：fontColor: ResourceColor;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：fontColor: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：selectedFontColor: ResourceColor;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：selectedFontColor: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：fontSize: DimensionNoPercentage;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：fontSize: DimensionNoPercentage;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：selectedFontSize: DimensionNoPercentage;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：selectedFontSize: DimensionNoPercentage;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：fontWeight: FontWeight;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：fontWeight: FontWeight;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：selectedFontWeight: FontWeight;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：selectedFontWeight: FontWeight;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：backgroundColor: ResourceColor;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：backgroundColor: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：selectedBackgroundColor: ResourceColor;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：selectedBackgroundColor: ResourceColor;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：imageSize: SizeOptions;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：imageSize: SizeOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：buttonPadding: Padding \| Dimension;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：buttonPadding: Padding \| Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：textPadding: Padding \| Dimension;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：textPadding: Padding \| Dimension;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：backgroundBlurStyle: BlurStyle;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：backgroundBlurStyle: BlurStyle;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：static tab(options: TabSegmentButtonConstructionOptions): SegmentButtonOptions;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：static tab(options: TabSegmentButtonConstructionOptions): SegmentButtonOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButtonOptions；<br>API声明：static capsule(options: CapsuleSegmentButtonConstructionOptions): SegmentButtonOptions;<br>差异内容：NA|类名：SegmentButtonOptions；<br>API声明：static capsule(options: CapsuleSegmentButtonConstructionOptions): SegmentButtonOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare struct SegmentButton<br>差异内容：NA|类名：global；<br>API声明：declare struct SegmentButton<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButton；<br>API声明：@ObjectLink<br>    options: SegmentButtonOptions;<br>差异内容：NA|类名：SegmentButton；<br>API声明：@ObjectLink<br>    options: SegmentButtonOptions;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：SegmentButton；<br>API声明：@Link<br>    selectedIndexes: number[];<br>差异内容：NA|类名：SegmentButton；<br>API声明：@Link<br>    selectedIndexes: number[];<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SegmentButton.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface EditorMenuOptions<br>差异内容：NA|类名：global；<br>API声明：export interface EditorMenuOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：EditorMenuOptions；<br>API声明：icon: ResourceStr;<br>差异内容：NA|类名：EditorMenuOptions；<br>API声明：icon: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：EditorMenuOptions；<br>API声明：action?: () => void;<br>差异内容：NA|类名：EditorMenuOptions；<br>API声明：action?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：EditorMenuOptions；<br>API声明：builder?: () => void;<br>差异内容：NA|类名：EditorMenuOptions；<br>API声明：builder?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface ExpandedMenuOptions<br>差异内容：NA|类名：global；<br>API声明：export interface ExpandedMenuOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：ExpandedMenuOptions；<br>API声明：action?: () => void;<br>差异内容：NA|类名：ExpandedMenuOptions；<br>API声明：action?: () => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface EditorEventInfo<br>差异内容：NA|类名：global；<br>API声明：export interface EditorEventInfo<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：EditorEventInfo；<br>API声明：content?: RichEditorSelection;<br>差异内容：NA|类名：EditorEventInfo；<br>API声明：content?: RichEditorSelection;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface SelectionMenuOptions<br>差异内容：NA|类名：global；<br>API声明：export interface SelectionMenuOptions<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：SelectionMenuOptions；<br>API声明：editorMenuOptions?: Array\<EditorMenuOptions>;<br>差异内容：NA|类名：SelectionMenuOptions；<br>API声明：editorMenuOptions?: Array\<EditorMenuOptions>;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：SelectionMenuOptions；<br>API声明：expandedMenuOptions?: Array\<ExpandedMenuOptions>;<br>差异内容：NA|类名：SelectionMenuOptions；<br>API声明：expandedMenuOptions?: Array\<ExpandedMenuOptions>;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：SelectionMenuOptions；<br>API声明：controller?: RichEditorController;<br>差异内容：NA|类名：SelectionMenuOptions；<br>API声明：controller?: RichEditorController;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：SelectionMenuOptions；<br>API声明：onPaste?: (event?: EditorEventInfo) => void;<br>差异内容：NA|类名：SelectionMenuOptions；<br>API声明：onPaste?: (event?: EditorEventInfo) => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：SelectionMenuOptions；<br>API声明：onCopy?: (event?: EditorEventInfo) => void;<br>差异内容：NA|类名：SelectionMenuOptions；<br>API声明：onCopy?: (event?: EditorEventInfo) => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：SelectionMenuOptions；<br>API声明：onCut?: (event?: EditorEventInfo) => void;<br>差异内容：NA|类名：SelectionMenuOptions；<br>API声明：onCut?: (event?: EditorEventInfo) => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：SelectionMenuOptions；<br>API声明：onSelectAll?: (event?: EditorEventInfo) => void;<br>差异内容：NA|类名：SelectionMenuOptions；<br>API声明：onSelectAll?: (event?: EditorEventInfo) => void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：@Builder<br>export declare function SelectionMenu(options: SelectionMenuOptions): void;<br>差异内容：NA|类名：global；<br>API声明：@Builder<br>export declare function SelectionMenu(options: SelectionMenuOptions): void;<br>差异内容：atomicservice|api/@ohos.arkui.advanced.SelectionMenu.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export declare struct TreeView<br>差异内容：NA|类名：global；<br>API声明：export declare struct TreeView<br>差异内容：atomicservice|api/@ohos.arkui.advanced.TreeView.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace componentSnapshot<br>差异内容：NA|类名：global；<br>API声明：declare namespace componentSnapshot<br>差异内容：atomicservice|api/@ohos.arkui.componentSnapshot.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace dragController<br>差异内容：NA|类名：global；<br>API声明：declare namespace dragController<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：dragController；<br>API声明：const enum DragStatus<br>差异内容：NA|类名：dragController；<br>API声明：const enum DragStatus<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragStatus；<br>API声明：STARTED = 0<br>差异内容：NA|类名：DragStatus；<br>API声明：STARTED = 0<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragStatus；<br>API声明：ENDED = 1<br>差异内容：NA|类名：DragStatus；<br>API声明：ENDED = 1<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：dragController；<br>API声明：interface DragAndDropInfo<br>差异内容：NA|类名：dragController；<br>API声明：interface DragAndDropInfo<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragAndDropInfo；<br>API声明：status: DragStatus;<br>差异内容：NA|类名：DragAndDropInfo；<br>API声明：status: DragStatus;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragAndDropInfo；<br>API声明：event: DragEvent;<br>差异内容：NA|类名：DragAndDropInfo；<br>API声明：event: DragEvent;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragAndDropInfo；<br>API声明：extraParams?: string;<br>差异内容：NA|类名：DragAndDropInfo；<br>API声明：extraParams?: string;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：dragController；<br>API声明：interface DragAction<br>差异内容：NA|类名：dragController；<br>API声明：interface DragAction<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragAction；<br>API声明：startDrag(): Promise\<void>;<br>差异内容：NA|类名：DragAction；<br>API声明：startDrag(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragAction；<br>API声明：on(type: 'statusChange', callback: Callback\<DragAndDropInfo>): void;<br>差异内容：NA|类名：DragAction；<br>API声明：on(type: 'statusChange', callback: Callback\<DragAndDropInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragAction；<br>API声明：off(type: 'statusChange', callback?: Callback\<DragAndDropInfo>): void;<br>差异内容：NA|类名：DragAction；<br>API声明：off(type: 'statusChange', callback?: Callback\<DragAndDropInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：dragController；<br>API声明：interface DragInfo<br>差异内容：NA|类名：dragController；<br>API声明：interface DragInfo<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragInfo；<br>API声明：pointerId: number;<br>差异内容：NA|类名：DragInfo；<br>API声明：pointerId: number;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragInfo；<br>API声明：data?: unifiedDataChannel.UnifiedData;<br>差异内容：NA|类名：DragInfo；<br>API声明：data?: unifiedDataChannel.UnifiedData;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragInfo；<br>API声明：extraParams?: string;<br>差异内容：NA|类名：DragInfo；<br>API声明：extraParams?: string;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragInfo；<br>API声明：touchPoint?: TouchPoint;<br>差异内容：NA|类名：DragInfo；<br>API声明：touchPoint?: TouchPoint;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragInfo；<br>API声明：previewOptions?: DragPreviewOptions;<br>差异内容：NA|类名：DragInfo；<br>API声明：previewOptions?: DragPreviewOptions;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：dragController；<br>API声明：interface AnimationOptions<br>差异内容：NA|类名：dragController；<br>API声明：interface AnimationOptions<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：AnimationOptions；<br>API声明：duration?: number;<br>差异内容：NA|类名：AnimationOptions；<br>API声明：duration?: number;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：AnimationOptions；<br>API声明：curve?: Curve \| ICurve;<br>差异内容：NA|类名：AnimationOptions；<br>API声明：curve?: Curve \| ICurve;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：dragController；<br>API声明：export class DragPreview<br>差异内容：NA|类名：dragController；<br>API声明：export class DragPreview<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragPreview；<br>API声明：setForegroundColor(color: ResourceColor): void;<br>差异内容：NA|类名：DragPreview；<br>API声明：setForegroundColor(color: ResourceColor): void;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：DragPreview；<br>API声明：animate(options: AnimationOptions, handler: () => void): void;<br>差异内容：NA|类名：DragPreview；<br>API声明：animate(options: AnimationOptions, handler: () => void): void;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：dragController；<br>API声明：function createDragAction(customArray: Array\<CustomBuilder \| DragItemInfo>, dragInfo: DragInfo): DragAction;<br>差异内容：NA|类名：dragController；<br>API声明：function createDragAction(customArray: Array\<CustomBuilder \| DragItemInfo>, dragInfo: DragInfo): DragAction;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：dragController；<br>API声明：function getDragPreview(): DragPreview;<br>差异内容：NA|类名：dragController；<br>API声明：function getDragPreview(): DragPreview;<br>差异内容：atomicservice|api/@ohos.arkui.dragController.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace inspector<br>差异内容：NA|类名：global；<br>API声明：declare namespace inspector<br>差异内容：atomicservice|api/@ohos.arkui.inspector.d.ts|
|API从不支持元服务到支持元服务|类名：inspector；<br>API声明：interface ComponentObserver<br>差异内容：NA|类名：inspector；<br>API声明：interface ComponentObserver<br>差异内容：atomicservice|api/@ohos.arkui.inspector.d.ts|
|API从不支持元服务到支持元服务|类名：ComponentObserver；<br>API声明：on(type: 'layout', callback: () => void): void;<br>差异内容：NA|类名：ComponentObserver；<br>API声明：on(type: 'layout', callback: () => void): void;<br>差异内容：atomicservice|api/@ohos.arkui.inspector.d.ts|
|API从不支持元服务到支持元服务|类名：ComponentObserver；<br>API声明：off(type: 'layout', callback?: () => void): void;<br>差异内容：NA|类名：ComponentObserver；<br>API声明：off(type: 'layout', callback?: () => void): void;<br>差异内容：atomicservice|api/@ohos.arkui.inspector.d.ts|
|API从不支持元服务到支持元服务|类名：ComponentObserver；<br>API声明：on(type: 'draw', callback: () => void): void;<br>差异内容：NA|类名：ComponentObserver；<br>API声明：on(type: 'draw', callback: () => void): void;<br>差异内容：atomicservice|api/@ohos.arkui.inspector.d.ts|
|API从不支持元服务到支持元服务|类名：ComponentObserver；<br>API声明：off(type: 'draw', callback?: () => void): void;<br>差异内容：NA|类名：ComponentObserver；<br>API声明：off(type: 'draw', callback?: () => void): void;<br>差异内容：atomicservice|api/@ohos.arkui.inspector.d.ts|
|API从不支持元服务到支持元服务|类名：inspector；<br>API声明：function createComponentObserver(id: string): ComponentObserver;<br>差异内容：NA|类名：inspector；<br>API声明：function createComponentObserver(id: string): ComponentObserver;<br>差异内容：atomicservice|api/@ohos.arkui.inspector.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace uiObserver<br>差异内容：NA|类名：global；<br>API声明：declare namespace uiObserver<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export enum NavDestinationState<br>差异内容：NA|类名：uiObserver；<br>API声明：export enum NavDestinationState<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：NavDestinationState；<br>API声明：ON_SHOWN = 0<br>差异内容：NA|类名：NavDestinationState；<br>API声明：ON_SHOWN = 0<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：NavDestinationState；<br>API声明：ON_HIDDEN = 1<br>差异内容：NA|类名：NavDestinationState；<br>API声明：ON_HIDDEN = 1<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export enum RouterPageState<br>差异内容：NA|类名：uiObserver；<br>API声明：export enum RouterPageState<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageState；<br>API声明：ABOUT_TO_APPEAR = 0<br>差异内容：NA|类名：RouterPageState；<br>API声明：ABOUT_TO_APPEAR = 0<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageState；<br>API声明：ABOUT_TO_DISAPPEAR = 1<br>差异内容：NA|类名：RouterPageState；<br>API声明：ABOUT_TO_DISAPPEAR = 1<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageState；<br>API声明：ON_PAGE_SHOW = 2<br>差异内容：NA|类名：RouterPageState；<br>API声明：ON_PAGE_SHOW = 2<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageState；<br>API声明：ON_PAGE_HIDE = 3<br>差异内容：NA|类名：RouterPageState；<br>API声明：ON_PAGE_HIDE = 3<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageState；<br>API声明：ON_BACK_PRESS = 4<br>差异内容：NA|类名：RouterPageState；<br>API声明：ON_BACK_PRESS = 4<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export interface NavDestinationInfo<br>差异内容：NA|类名：uiObserver；<br>API声明：export interface NavDestinationInfo<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：NavDestinationInfo；<br>API声明：navigationId: ResourceStr;<br>差异内容：NA|类名：NavDestinationInfo；<br>API声明：navigationId: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：NavDestinationInfo；<br>API声明：name: ResourceStr;<br>差异内容：NA|类名：NavDestinationInfo；<br>API声明：name: ResourceStr;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：NavDestinationInfo；<br>API声明：state: NavDestinationState;<br>差异内容：NA|类名：NavDestinationInfo；<br>API声明：state: NavDestinationState;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export class RouterPageInfo<br>差异内容：NA|类名：uiObserver；<br>API声明：export class RouterPageInfo<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageInfo；<br>API声明：context: UIAbilityContext \| UIContext;<br>差异内容：NA|类名：RouterPageInfo；<br>API声明：context: UIAbilityContext \| UIContext;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageInfo；<br>API声明：index: number;<br>差异内容：NA|类名：RouterPageInfo；<br>API声明：index: number;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageInfo；<br>API声明：name: string;<br>差异内容：NA|类名：RouterPageInfo；<br>API声明：name: string;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageInfo；<br>API声明：path: string;<br>差异内容：NA|类名：RouterPageInfo；<br>API声明：path: string;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：RouterPageInfo；<br>API声明：state: RouterPageState;<br>差异内容：NA|类名：RouterPageInfo；<br>API声明：state: RouterPageState;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export function on(type: 'navDestinationUpdate', options: {<br>        navigationId: ResourceStr;<br>    }, callback: Callback\<NavDestinationInfo>): void;<br>差异内容：NA|类名：uiObserver；<br>API声明：export function on(type: 'navDestinationUpdate', options: {<br>        navigationId: ResourceStr;<br>    }, callback: Callback\<NavDestinationInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export function on(type: 'navDestinationUpdate', callback: Callback\<NavDestinationInfo>): void;<br>差异内容：NA|类名：uiObserver；<br>API声明：export function on(type: 'navDestinationUpdate', callback: Callback\<NavDestinationInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export function off(type: 'navDestinationUpdate', options: {<br>        navigationId: ResourceStr;<br>    }, callback?: Callback\<NavDestinationInfo>): void;<br>差异内容：NA|类名：uiObserver；<br>API声明：export function off(type: 'navDestinationUpdate', options: {<br>        navigationId: ResourceStr;<br>    }, callback?: Callback\<NavDestinationInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export function off(type: 'navDestinationUpdate', callback?: Callback\<NavDestinationInfo>): void;<br>差异内容：NA|类名：uiObserver；<br>API声明：export function off(type: 'navDestinationUpdate', callback?: Callback\<NavDestinationInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export function on(type: 'routerPageUpdate', context: UIAbilityContext \| UIContext, callback: Callback\<RouterPageInfo>): void;<br>差异内容：NA|类名：uiObserver；<br>API声明：export function on(type: 'routerPageUpdate', context: UIAbilityContext \| UIContext, callback: Callback\<RouterPageInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：uiObserver；<br>API声明：export function off(type: 'routerPageUpdate', context: UIAbilityContext \| UIContext, callback?: Callback\<RouterPageInfo>): void;<br>差异内容：NA|类名：uiObserver；<br>API声明：export function off(type: 'routerPageUpdate', context: UIAbilityContext \| UIContext, callback?: Callback\<RouterPageInfo>): void;<br>差异内容：atomicservice|api/@ohos.arkui.observer.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function getAllDisplays(callback: AsyncCallback\<Array\<Display>>): void;<br>差异内容：NA|类名：display；<br>API声明：function getAllDisplays(callback: AsyncCallback\<Array\<Display>>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function getAllDisplays(): Promise\<Array\<Display>>;<br>差异内容：NA|类名：display；<br>API声明：function getAllDisplays(): Promise\<Array\<Display>>;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function on(type: 'add' \| 'remove' \| 'change', callback: Callback\<number>): void;<br>差异内容：NA|类名：display；<br>API声明：function on(type: 'add' \| 'remove' \| 'change', callback: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function on(type: 'add' \| 'remove' \| 'change', callback: Callback\<number>): void;<br>差异内容：NA|类名：display；<br>API声明：function on(type: 'add' \| 'remove' \| 'change', callback: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function on(type: 'add' \| 'remove' \| 'change', callback: Callback\<number>): void;<br>差异内容：NA|类名：display；<br>API声明：function on(type: 'add' \| 'remove' \| 'change', callback: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function off(type: 'add' \| 'remove' \| 'change', callback?: Callback\<number>): void;<br>差异内容：NA|类名：display；<br>API声明：function off(type: 'add' \| 'remove' \| 'change', callback?: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function off(type: 'add' \| 'remove' \| 'change', callback?: Callback\<number>): void;<br>差异内容：NA|类名：display；<br>API声明：function off(type: 'add' \| 'remove' \| 'change', callback?: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function off(type: 'add' \| 'remove' \| 'change', callback?: Callback\<number>): void;<br>差异内容：NA|类名：display；<br>API声明：function off(type: 'add' \| 'remove' \| 'change', callback?: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function isFoldable(): boolean;<br>差异内容：NA|类名：display；<br>API声明：function isFoldable(): boolean;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function getFoldStatus(): FoldStatus;<br>差异内容：NA|类名：display；<br>API声明：function getFoldStatus(): FoldStatus;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function on(type: 'foldStatusChange', callback: Callback\<FoldStatus>): void;<br>差异内容：NA|类名：display；<br>API声明：function on(type: 'foldStatusChange', callback: Callback\<FoldStatus>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function off(type: 'foldStatusChange', callback?: Callback\<FoldStatus>): void;<br>差异内容：NA|类名：display；<br>API声明：function off(type: 'foldStatusChange', callback?: Callback\<FoldStatus>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function getFoldDisplayMode(): FoldDisplayMode;<br>差异内容：NA|类名：display；<br>API声明：function getFoldDisplayMode(): FoldDisplayMode;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function on(type: 'foldDisplayModeChange', callback: Callback\<FoldDisplayMode>): void;<br>差异内容：NA|类名：display；<br>API声明：function on(type: 'foldDisplayModeChange', callback: Callback\<FoldDisplayMode>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function off(type: 'foldDisplayModeChange', callback?: Callback\<FoldDisplayMode>): void;<br>差异内容：NA|类名：display；<br>API声明：function off(type: 'foldDisplayModeChange', callback?: Callback\<FoldDisplayMode>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：function getCurrentFoldCreaseRegion(): FoldCreaseRegion;<br>差异内容：NA|类名：display；<br>API声明：function getCurrentFoldCreaseRegion(): FoldCreaseRegion;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：enum FoldStatus<br>差异内容：NA|类名：display；<br>API声明：enum FoldStatus<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldStatus；<br>API声明：FOLD_STATUS_UNKNOWN = 0<br>差异内容：NA|类名：FoldStatus；<br>API声明：FOLD_STATUS_UNKNOWN = 0<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldStatus；<br>API声明：FOLD_STATUS_EXPANDED<br>差异内容：NA|类名：FoldStatus；<br>API声明：FOLD_STATUS_EXPANDED<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldStatus；<br>API声明：FOLD_STATUS_FOLDED<br>差异内容：NA|类名：FoldStatus；<br>API声明：FOLD_STATUS_FOLDED<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldStatus；<br>API声明：FOLD_STATUS_HALF_FOLDED<br>差异内容：NA|类名：FoldStatus；<br>API声明：FOLD_STATUS_HALF_FOLDED<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：enum FoldDisplayMode<br>差异内容：NA|类名：display；<br>API声明：enum FoldDisplayMode<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_UNKNOWN = 0<br>差异内容：NA|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_UNKNOWN = 0<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_FULL<br>差异内容：NA|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_FULL<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_MAIN<br>差异内容：NA|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_MAIN<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_SUB<br>差异内容：NA|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_SUB<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_COORDINATION<br>差异内容：NA|类名：FoldDisplayMode；<br>API声明：FOLD_DISPLAY_MODE_COORDINATION<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：enum DisplayState<br>差异内容：NA|类名：display；<br>API声明：enum DisplayState<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：DisplayState；<br>API声明：STATE_UNKNOWN = 0<br>差异内容：NA|类名：DisplayState；<br>API声明：STATE_UNKNOWN = 0<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：DisplayState；<br>API声明：STATE_OFF<br>差异内容：NA|类名：DisplayState；<br>API声明：STATE_OFF<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：DisplayState；<br>API声明：STATE_ON<br>差异内容：NA|类名：DisplayState；<br>API声明：STATE_ON<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：DisplayState；<br>API声明：STATE_DOZE<br>差异内容：NA|类名：DisplayState；<br>API声明：STATE_DOZE<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：DisplayState；<br>API声明：STATE_DOZE_SUSPEND<br>差异内容：NA|类名：DisplayState；<br>API声明：STATE_DOZE_SUSPEND<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：DisplayState；<br>API声明：STATE_VR<br>差异内容：NA|类名：DisplayState；<br>API声明：STATE_VR<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：DisplayState；<br>API声明：STATE_ON_SUSPEND<br>差异内容：NA|类名：DisplayState；<br>API声明：STATE_ON_SUSPEND<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：enum Orientation<br>差异内容：NA|类名：display；<br>API声明：enum Orientation<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：PORTRAIT = 0<br>差异内容：NA|类名：Orientation；<br>API声明：PORTRAIT = 0<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：LANDSCAPE = 1<br>差异内容：NA|类名：Orientation；<br>API声明：LANDSCAPE = 1<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：PORTRAIT_INVERTED = 2<br>差异内容：NA|类名：Orientation；<br>API声明：PORTRAIT_INVERTED = 2<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：LANDSCAPE_INVERTED = 3<br>差异内容：NA|类名：Orientation；<br>API声明：LANDSCAPE_INVERTED = 3<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：interface FoldCreaseRegion<br>差异内容：NA|类名：display；<br>API声明：interface FoldCreaseRegion<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldCreaseRegion；<br>API声明：readonly displayId: number;<br>差异内容：NA|类名：FoldCreaseRegion；<br>API声明：readonly displayId: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：FoldCreaseRegion；<br>API声明：readonly creaseRects: Array\<Rect>;<br>差异内容：NA|类名：FoldCreaseRegion；<br>API声明：readonly creaseRects: Array\<Rect>;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：interface Rect<br>差异内容：NA|类名：display；<br>API声明：interface Rect<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Rect；<br>API声明：left: number;<br>差异内容：NA|类名：Rect；<br>API声明：left: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Rect；<br>API声明：top: number;<br>差异内容：NA|类名：Rect；<br>API声明：top: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Rect；<br>API声明：width: number;<br>差异内容：NA|类名：Rect；<br>API声明：width: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Rect；<br>API声明：height: number;<br>差异内容：NA|类名：Rect；<br>API声明：height: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：interface WaterfallDisplayAreaRects<br>差异内容：NA|类名：display；<br>API声明：interface WaterfallDisplayAreaRects<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：WaterfallDisplayAreaRects；<br>API声明：readonly left: Rect;<br>差异内容：NA|类名：WaterfallDisplayAreaRects；<br>API声明：readonly left: Rect;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：WaterfallDisplayAreaRects；<br>API声明：readonly right: Rect;<br>差异内容：NA|类名：WaterfallDisplayAreaRects；<br>API声明：readonly right: Rect;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：WaterfallDisplayAreaRects；<br>API声明：readonly top: Rect;<br>差异内容：NA|类名：WaterfallDisplayAreaRects；<br>API声明：readonly top: Rect;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：WaterfallDisplayAreaRects；<br>API声明：readonly bottom: Rect;<br>差异内容：NA|类名：WaterfallDisplayAreaRects；<br>API声明：readonly bottom: Rect;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：display；<br>API声明：interface CutoutInfo<br>差异内容：NA|类名：display；<br>API声明：interface CutoutInfo<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：CutoutInfo；<br>API声明：readonly boundingRects: Array\<Rect>;<br>差异内容：NA|类名：CutoutInfo；<br>API声明：readonly boundingRects: Array\<Rect>;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：CutoutInfo；<br>API声明：readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects;<br>差异内容：NA|类名：CutoutInfo；<br>API声明：readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：id: number;<br>差异内容：NA|类名：Display；<br>API声明：id: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：name: string;<br>差异内容：NA|类名：Display；<br>API声明：name: string;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：alive: boolean;<br>差异内容：NA|类名：Display；<br>API声明：alive: boolean;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：state: DisplayState;<br>差异内容：NA|类名：Display；<br>API声明：state: DisplayState;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：refreshRate: number;<br>差异内容：NA|类名：Display；<br>API声明：refreshRate: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：densityDPI: number;<br>差异内容：NA|类名：Display；<br>API声明：densityDPI: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：orientation: Orientation;<br>差异内容：NA|类名：Display；<br>API声明：orientation: Orientation;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：scaledDensity: number;<br>差异内容：NA|类名：Display；<br>API声明：scaledDensity: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：xDPI: number;<br>差异内容：NA|类名：Display；<br>API声明：xDPI: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：yDPI: number;<br>差异内容：NA|类名：Display；<br>API声明：yDPI: number;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：colorSpaces: Array\<colorSpaceManager.ColorSpace>;<br>差异内容：NA|类名：Display；<br>API声明：colorSpaces: Array\<colorSpaceManager.ColorSpace>;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：hdrFormats: Array\<hdrCapability.HDRFormat>;<br>差异内容：NA|类名：Display；<br>API声明：hdrFormats: Array\<hdrCapability.HDRFormat>;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：getCutoutInfo(callback: AsyncCallback\<CutoutInfo>): void;<br>差异内容：NA|类名：Display；<br>API声明：getCutoutInfo(callback: AsyncCallback\<CutoutInfo>): void;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：Display；<br>API声明：getCutoutInfo(): Promise\<CutoutInfo>;<br>差异内容：NA|类名：Display；<br>API声明：getCutoutInfo(): Promise\<CutoutInfo>;<br>差异内容：atomicservice|api/@ohos.display.d.ts|
|API从不支持元服务到支持元服务|类名：font；<br>API声明：interface UIFontConfig<br>差异内容：NA|类名：font；<br>API声明：interface UIFontConfig<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontConfig；<br>API声明：fontDir: Array\<string>;<br>差异内容：NA|类名：UIFontConfig；<br>API声明：fontDir: Array\<string>;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontConfig；<br>API声明：generic: Array\<UIFontGenericInfo>;<br>差异内容：NA|类名：UIFontConfig；<br>API声明：generic: Array\<UIFontGenericInfo>;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontConfig；<br>API声明：fallbackGroups: Array\<UIFontFallbackGroupInfo>;<br>差异内容：NA|类名：UIFontConfig；<br>API声明：fallbackGroups: Array\<UIFontFallbackGroupInfo>;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：font；<br>API声明：interface UIFontGenericInfo<br>差异内容：NA|类名：font；<br>API声明：interface UIFontGenericInfo<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontGenericInfo；<br>API声明：family: string;<br>差异内容：NA|类名：UIFontGenericInfo；<br>API声明：family: string;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontGenericInfo；<br>API声明：alias: Array\<UIFontAliasInfo>;<br>差异内容：NA|类名：UIFontGenericInfo；<br>API声明：alias: Array\<UIFontAliasInfo>;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontGenericInfo；<br>API声明：adjust: Array\<UIFontAdjustInfo>;<br>差异内容：NA|类名：UIFontGenericInfo；<br>API声明：adjust: Array\<UIFontAdjustInfo>;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：font；<br>API声明：interface UIFontAliasInfo<br>差异内容：NA|类名：font；<br>API声明：interface UIFontAliasInfo<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontAliasInfo；<br>API声明：name: string;<br>差异内容：NA|类名：UIFontAliasInfo；<br>API声明：name: string;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontAliasInfo；<br>API声明：weight: number;<br>差异内容：NA|类名：UIFontAliasInfo；<br>API声明：weight: number;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：font；<br>API声明：interface UIFontAdjustInfo<br>差异内容：NA|类名：font；<br>API声明：interface UIFontAdjustInfo<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontAdjustInfo；<br>API声明：weight: number;<br>差异内容：NA|类名：UIFontAdjustInfo；<br>API声明：weight: number;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontAdjustInfo；<br>API声明：to: number;<br>差异内容：NA|类名：UIFontAdjustInfo；<br>API声明：to: number;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：font；<br>API声明：interface UIFontFallbackGroupInfo<br>差异内容：NA|类名：font；<br>API声明：interface UIFontFallbackGroupInfo<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontFallbackGroupInfo；<br>API声明：fontSetName: string;<br>差异内容：NA|类名：UIFontFallbackGroupInfo；<br>API声明：fontSetName: string;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontFallbackGroupInfo；<br>API声明：fallback: Array\<UIFontFallbackInfo>;<br>差异内容：NA|类名：UIFontFallbackGroupInfo；<br>API声明：fallback: Array\<UIFontFallbackInfo>;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：font；<br>API声明：interface UIFontFallbackInfo<br>差异内容：NA|类名：font；<br>API声明：interface UIFontFallbackInfo<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontFallbackInfo；<br>API声明：language: string;<br>差异内容：NA|类名：UIFontFallbackInfo；<br>API声明：language: string;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：UIFontFallbackInfo；<br>API声明：family: string;<br>差异内容：NA|类名：UIFontFallbackInfo；<br>API声明：family: string;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：font；<br>API声明：function getUIFontConfig(): UIFontConfig;<br>差异内容：NA|类名：font；<br>API声明：function getUIFontConfig(): UIFontConfig;<br>差异内容：atomicservice|api/@ohos.font.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface MeasureOptions<br>差异内容：NA|类名：global；<br>API声明：export interface MeasureOptions<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：textContent: string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：textContent: string \| Resource;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：constraintWidth?: number \| string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：constraintWidth?: number \| string \| Resource;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：fontSize?: number \| string \| Resource;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：fontStyle?: number \| FontStyle;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：fontStyle?: number \| FontStyle;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：fontWeight?: number \| string \| FontWeight;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：fontWeight?: number \| string \| FontWeight;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：fontFamily?: string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：fontFamily?: string \| Resource;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：letterSpacing?: number \| string;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：letterSpacing?: number \| string;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：textAlign?: number \| TextAlign;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：textAlign?: number \| TextAlign;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：overflow?: number \| TextOverflow;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：overflow?: number \| TextOverflow;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：maxLines?: number;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：maxLines?: number;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：lineHeight?: number \| string \| Resource;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：lineHeight?: number \| string \| Resource;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：baselineOffset?: number \| string;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：baselineOffset?: number \| string;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：textCase?: number \| TextCase;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：textCase?: number \| TextCase;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：textIndent?: number \| string;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：textIndent?: number \| string;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureOptions；<br>API声明：wordBreak?: WordBreak;<br>差异内容：NA|类名：MeasureOptions；<br>API声明：wordBreak?: WordBreak;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export default class MeasureText<br>差异内容：NA|类名：global；<br>API声明：export default class MeasureText<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureText；<br>API声明：static measureText(options: MeasureOptions): number;<br>差异内容：NA|类名：MeasureText；<br>API声明：static measureText(options: MeasureOptions): number;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：MeasureText；<br>API声明：static measureTextSize(options: MeasureOptions): SizeOptions;<br>差异内容：NA|类名：MeasureText；<br>API声明：static measureTextSize(options: MeasureOptions): SizeOptions;<br>差异内容：atomicservice|api/@ohos.measure.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace PiPWindow<br>差异内容：NA|类名：global；<br>API声明：declare namespace PiPWindow<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：function isPiPEnabled(): boolean;<br>差异内容：NA|类名：PiPWindow；<br>API声明：function isPiPEnabled(): boolean;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：function create(config: PiPConfiguration): Promise\<PiPController>;<br>差异内容：NA|类名：PiPWindow；<br>API声明：function create(config: PiPConfiguration): Promise\<PiPController>;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：interface PiPConfiguration<br>差异内容：NA|类名：PiPWindow；<br>API声明：interface PiPConfiguration<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPConfiguration；<br>API声明：context: BaseContext;<br>差异内容：NA|类名：PiPConfiguration；<br>API声明：context: BaseContext;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPConfiguration；<br>API声明：componentController: XComponentController;<br>差异内容：NA|类名：PiPConfiguration；<br>API声明：componentController: XComponentController;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPConfiguration；<br>API声明：navigationId?: string;<br>差异内容：NA|类名：PiPConfiguration；<br>API声明：navigationId?: string;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPConfiguration；<br>API声明：templateType?: PiPTemplateType;<br>差异内容：NA|类名：PiPConfiguration；<br>API声明：templateType?: PiPTemplateType;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPConfiguration；<br>API声明：contentWidth?: number;<br>差异内容：NA|类名：PiPConfiguration；<br>API声明：contentWidth?: number;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPConfiguration；<br>API声明：contentHeight?: number;<br>差异内容：NA|类名：PiPConfiguration；<br>API声明：contentHeight?: number;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：enum PiPTemplateType<br>差异内容：NA|类名：PiPWindow；<br>API声明：enum PiPTemplateType<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPTemplateType；<br>API声明：VIDEO_PLAY<br>差异内容：NA|类名：PiPTemplateType；<br>API声明：VIDEO_PLAY<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPTemplateType；<br>API声明：VIDEO_CALL<br>差异内容：NA|类名：PiPTemplateType；<br>API声明：VIDEO_CALL<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPTemplateType；<br>API声明：VIDEO_MEETING<br>差异内容：NA|类名：PiPTemplateType；<br>API声明：VIDEO_MEETING<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPTemplateType；<br>API声明：VIDEO_LIVE<br>差异内容：NA|类名：PiPTemplateType；<br>API声明：VIDEO_LIVE<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：enum PiPState<br>差异内容：NA|类名：PiPWindow；<br>API声明：enum PiPState<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPState；<br>API声明：ABOUT_TO_START = 1<br>差异内容：NA|类名：PiPState；<br>API声明：ABOUT_TO_START = 1<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPState；<br>API声明：STARTED = 2<br>差异内容：NA|类名：PiPState；<br>API声明：STARTED = 2<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPState；<br>API声明：ABOUT_TO_STOP = 3<br>差异内容：NA|类名：PiPState；<br>API声明：ABOUT_TO_STOP = 3<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPState；<br>API声明：STOPPED = 4<br>差异内容：NA|类名：PiPState；<br>API声明：STOPPED = 4<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPState；<br>API声明：ABOUT_TO_RESTORE = 5<br>差异内容：NA|类名：PiPState；<br>API声明：ABOUT_TO_RESTORE = 5<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPState；<br>API声明：ERROR = 6<br>差异内容：NA|类名：PiPState；<br>API声明：ERROR = 6<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：type PiPActionEventType = PiPVideoActionEvent \| PiPCallActionEvent \| PiPMeetingActionEvent \| PiPLiveActionEvent;<br>差异内容：NA|类名：PiPWindow；<br>API声明：type PiPActionEventType = PiPVideoActionEvent \| PiPCallActionEvent \| PiPMeetingActionEvent \| PiPLiveActionEvent;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：type PiPVideoActionEvent = 'playbackStateChanged' \| 'nextVideo' \| 'previousVideo';<br>差异内容：NA|类名：PiPWindow；<br>API声明：type PiPVideoActionEvent = 'playbackStateChanged' \| 'nextVideo' \| 'previousVideo' \| 'fastForward' \| 'fastBackward';<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：type PiPCallActionEvent = 'hangUp' \| 'micStateChanged' \| 'videoStateChanged';<br>差异内容：NA|类名：PiPWindow；<br>API声明：type PiPCallActionEvent = 'hangUp' \| 'micStateChanged' \| 'videoStateChanged' \| 'voiceStateChanged';<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：type PiPMeetingActionEvent = 'hangUp' \| 'voiceStateChanged' \| 'videoStateChanged';<br>差异内容：NA|类名：PiPWindow；<br>API声明：type PiPMeetingActionEvent = 'hangUp' \| 'voiceStateChanged' \| 'videoStateChanged' \| 'micStateChanged';<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：type PiPLiveActionEvent = 'playbackStateChanged';<br>差异内容：NA|类名：PiPWindow；<br>API声明：type PiPLiveActionEvent = 'playbackStateChanged' \| 'voiceStateChanged';<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPWindow；<br>API声明：interface PiPController<br>差异内容：NA|类名：PiPWindow；<br>API声明：interface PiPController<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPController；<br>API声明：startPiP(): Promise\<void>;<br>差异内容：NA|类名：PiPController；<br>API声明：startPiP(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPController；<br>API声明：stopPiP(): Promise\<void>;<br>差异内容：NA|类名：PiPController；<br>API声明：stopPiP(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPController；<br>API声明：setAutoStartEnabled(enable: boolean): void;<br>差异内容：NA|类名：PiPController；<br>API声明：setAutoStartEnabled(enable: boolean): void;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPController；<br>API声明：updateContentSize(width: number, height: number): void;<br>差异内容：NA|类名：PiPController；<br>API声明：updateContentSize(width: number, height: number): void;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPController；<br>API声明：on(type: 'stateChange', callback: (state: PiPState, reason: string) => void): void;<br>差异内容：NA|类名：PiPController；<br>API声明：on(type: 'stateChange', callback: (state: PiPState, reason: string) => void): void;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPController；<br>API声明：off(type: 'stateChange'): void;<br>差异内容：NA|类名：PiPController；<br>API声明：off(type: 'stateChange'): void;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPController；<br>API声明：on(type: 'controlPanelActionEvent', callback: (event: PiPActionEventType) => void): void;<br>差异内容：NA|类名：PiPController；<br>API声明：on(type: 'controlPanelActionEvent', callback: ControlPanelActionEventCallback): void;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：PiPController；<br>API声明：off(type: 'controlPanelActionEvent'): void;<br>差异内容：NA|类名：PiPController；<br>API声明：off(type: 'controlPanelActionEvent'): void;<br>差异内容：atomicservice|api/@ohos.PiPWindow.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：interface PluginComponentTemplate<br>差异内容：NA|类名：global；<br>API声明：interface PluginComponentTemplate<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：PluginComponentTemplate；<br>API声明：source: string;<br>差异内容：NA|类名：PluginComponentTemplate；<br>API声明：source: string;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：PluginComponentTemplate；<br>API声明：ability: string;<br>差异内容：NA|类名：PluginComponentTemplate；<br>API声明：ability: string;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace pluginComponentManager<br>差异内容：NA|类名：global；<br>API声明：declare namespace pluginComponentManager<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：type KVObject = {<br>        [key: string]: number \| string \| boolean \| [<br>        ] \| KVObject;<br>    };<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：type KVObject = {<br>        [key: string]: number \| string \| boolean \| [<br>        ] \| KVObject;<br>    };<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：interface PushParameters<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：interface PushParameters<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：PushParameters；<br>API声明：want: Want;<br>差异内容：NA|类名：PushParameters；<br>API声明：want: Want;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：PushParameters；<br>API声明：name: string;<br>差异内容：NA|类名：PushParameters；<br>API声明：name: string;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：PushParameters；<br>API声明：data: KVObject;<br>差异内容：NA|类名：PushParameters；<br>API声明：data: KVObject;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：PushParameters；<br>API声明：extraData: KVObject;<br>差异内容：NA|类名：PushParameters；<br>API声明：extraData: KVObject;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：PushParameters；<br>API声明：jsonPath?: string;<br>差异内容：NA|类名：PushParameters；<br>API声明：jsonPath?: string;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：interface RequestParameters<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：interface RequestParameters<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestParameters；<br>API声明：want: Want;<br>差异内容：NA|类名：RequestParameters；<br>API声明：want: Want;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestParameters；<br>API声明：name: string;<br>差异内容：NA|类名：RequestParameters；<br>API声明：name: string;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestParameters；<br>API声明：data: KVObject;<br>差异内容：NA|类名：RequestParameters；<br>API声明：data: KVObject;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestParameters；<br>API声明：jsonPath?: string;<br>差异内容：NA|类名：RequestParameters；<br>API声明：jsonPath?: string;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：interface RequestCallbackParameters<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：interface RequestCallbackParameters<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestCallbackParameters；<br>API声明：componentTemplate: PluginComponentTemplate;<br>差异内容：NA|类名：RequestCallbackParameters；<br>API声明：componentTemplate: PluginComponentTemplate;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestCallbackParameters；<br>API声明：data: KVObject;<br>差异内容：NA|类名：RequestCallbackParameters；<br>API声明：data: KVObject;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestCallbackParameters；<br>API声明：extraData: KVObject;<br>差异内容：NA|类名：RequestCallbackParameters；<br>API声明：extraData: KVObject;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：interface RequestEventResult<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：interface RequestEventResult<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestEventResult；<br>API声明：template?: string;<br>差异内容：NA|类名：RequestEventResult；<br>API声明：template?: string;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestEventResult；<br>API声明：data?: KVObject;<br>差异内容：NA|类名：RequestEventResult；<br>API声明：data?: KVObject;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：RequestEventResult；<br>API声明：extraData?: KVObject;<br>差异内容：NA|类名：RequestEventResult；<br>API声明：extraData?: KVObject;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject, extraData: KVObject) => void;<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject, extraData: KVObject) => void;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult;<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：function push(param: PushParameters, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：function push(param: PushParameters, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：function request(param: RequestParameters, callback: AsyncCallback\<RequestCallbackParameters>): void;<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：function request(param: RequestParameters, callback: AsyncCallback\<RequestCallbackParameters>): void;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：pluginComponentManager；<br>API声明：function on(eventType: string, callback: OnPushEventCallback \| OnRequestEventCallback): void;<br>差异内容：NA|类名：pluginComponentManager；<br>API声明：function on(eventType: string, callback: OnPushEventCallback \| OnRequestEventCallback): void;<br>差异内容：atomicservice|api/@ohos.pluginComponent.d.ts|
|API从不支持元服务到支持元服务|类名：ShowToastOptions；<br>API声明：showMode?: ToastShowMode;<br>差异内容：NA|类名：ShowToastOptions；<br>API声明：showMode?: ToastShowMode;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：promptAction；<br>API声明：export enum ToastShowMode<br>差异内容：NA|类名：promptAction；<br>API声明：export enum ToastShowMode<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：ToastShowMode；<br>API声明：DEFAULT = 0<br>差异内容：NA|类名：ToastShowMode；<br>API声明：DEFAULT = 0<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：ToastShowMode；<br>API声明：TOP_MOST = 1<br>差异内容：NA|类名：ToastShowMode；<br>API声明：TOP_MOST = 1<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：ShowDialogOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：NA|类名：ShowDialogOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：ShowDialogOptions；<br>API声明：isModal?: boolean;<br>差异内容：NA|类名：ShowDialogOptions；<br>API声明：isModal?: boolean;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：promptAction；<br>API声明：interface BaseDialogOptions<br>差异内容：NA|类名：promptAction；<br>API声明：interface BaseDialogOptions<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：BaseDialogOptions；<br>API声明：maskRect?: Rectangle;<br>差异内容：NA|类名：BaseDialogOptions；<br>API声明：maskRect?: Rectangle;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：BaseDialogOptions；<br>API声明：alignment?: DialogAlignment;<br>差异内容：NA|类名：BaseDialogOptions；<br>API声明：alignment?: DialogAlignment;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：BaseDialogOptions；<br>API声明：offset?: Offset;<br>差异内容：NA|类名：BaseDialogOptions；<br>API声明：offset?: Offset;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：BaseDialogOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：NA|类名：BaseDialogOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：BaseDialogOptions；<br>API声明：isModal?: boolean;<br>差异内容：NA|类名：BaseDialogOptions；<br>API声明：isModal?: boolean;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：promptAction；<br>API声明：interface CustomDialogOptions<br>差异内容：NA|类名：promptAction；<br>API声明：interface CustomDialogOptions<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：CustomDialogOptions；<br>API声明：builder: CustomBuilder;<br>差异内容：NA|类名：CustomDialogOptions；<br>API声明：builder: CustomBuilder;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：ActionMenuOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：NA|类名：ActionMenuOptions；<br>API声明：showInSubWindow?: boolean;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：ActionMenuOptions；<br>API声明：isModal?: boolean;<br>差异内容：NA|类名：ActionMenuOptions；<br>API声明：isModal?: boolean;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：promptAction；<br>API声明：function openCustomDialog(options: CustomDialogOptions): Promise\<number>;<br>差异内容：NA|类名：promptAction；<br>API声明：function openCustomDialog(options: CustomDialogOptions): Promise\<number>;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：promptAction；<br>API声明：function closeCustomDialog(dialogId: number): void;<br>差异内容：NA|类名：promptAction；<br>API声明：function closeCustomDialog(dialogId: number): void;<br>差异内容：atomicservice|api/@ohos.promptAction.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：enum WindowType<br>差异内容：NA|类名：window；<br>API声明：enum WindowType<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowType；<br>API声明：TYPE_FLOAT<br>差异内容：NA|类名：WindowType；<br>API声明：TYPE_FLOAT<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowType；<br>API声明：TYPE_DIALOG<br>差异内容：NA|类名：WindowType；<br>API声明：TYPE_DIALOG<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：enum WindowStatusType<br>差异内容：NA|类名：window；<br>API声明：enum WindowStatusType<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowStatusType；<br>API声明：UNDEFINED = 0<br>差异内容：NA|类名：WindowStatusType；<br>API声明：UNDEFINED = 0<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowStatusType；<br>API声明：FULL_SCREEN<br>差异内容：NA|类名：WindowStatusType；<br>API声明：FULL_SCREEN<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowStatusType；<br>API声明：MAXIMIZE<br>差异内容：NA|类名：WindowStatusType；<br>API声明：MAXIMIZE<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowStatusType；<br>API声明：MINIMIZE<br>差异内容：NA|类名：WindowStatusType；<br>API声明：MINIMIZE<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowStatusType；<br>API声明：FLOATING<br>差异内容：NA|类名：WindowStatusType；<br>API声明：FLOATING<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowStatusType；<br>API声明：SPLIT_SCREEN<br>差异内容：NA|类名：WindowStatusType；<br>API声明：SPLIT_SCREEN<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：interface SystemBarProperties<br>差异内容：NA|类名：window；<br>API声明：interface SystemBarProperties<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：SystemBarProperties；<br>API声明：statusBarColor?: string;<br>差异内容：NA|类名：SystemBarProperties；<br>API声明：statusBarColor?: string;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：SystemBarProperties；<br>API声明：isStatusBarLightIcon?: boolean;<br>差异内容：NA|类名：SystemBarProperties；<br>API声明：isStatusBarLightIcon?: boolean;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：SystemBarProperties；<br>API声明：statusBarContentColor?: string;<br>差异内容：NA|类名：SystemBarProperties；<br>API声明：statusBarContentColor?: string;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：SystemBarProperties；<br>API声明：navigationBarColor?: string;<br>差异内容：NA|类名：SystemBarProperties；<br>API声明：navigationBarColor?: string;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：SystemBarProperties；<br>API声明：isNavigationBarLightIcon?: boolean;<br>差异内容：NA|类名：SystemBarProperties；<br>API声明：isNavigationBarLightIcon?: boolean;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：SystemBarProperties；<br>API声明：navigationBarContentColor?: string;<br>差异内容：NA|类名：SystemBarProperties；<br>API声明：navigationBarContentColor?: string;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowProperties；<br>API声明：drawableRect: Rect;<br>差异内容：NA|类名：WindowProperties；<br>API声明：drawableRect: Rect;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowProperties；<br>API声明：type: WindowType;<br>差异内容：NA|类名：WindowProperties；<br>API声明：type: WindowType;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowProperties；<br>API声明：isFullScreen: boolean;<br>差异内容：NA|类名：WindowProperties；<br>API声明：isFullScreen: boolean;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowProperties；<br>API声明：isLayoutFullScreen: boolean;<br>差异内容：NA|类名：WindowProperties；<br>API声明：isLayoutFullScreen: boolean;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowProperties；<br>API声明：focusable: boolean;<br>差异内容：NA|类名：WindowProperties；<br>API声明：focusable: boolean;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowProperties；<br>API声明：touchable: boolean;<br>差异内容：NA|类名：WindowProperties；<br>API声明：touchable: boolean;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowProperties；<br>API声明：isPrivacyMode: boolean;<br>差异内容：NA|类名：WindowProperties；<br>API声明：isPrivacyMode: boolean;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowProperties；<br>API声明：isTransparent: boolean;<br>差异内容：NA|类名：WindowProperties；<br>API声明：isTransparent: boolean;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowProperties；<br>API声明：id: number;<br>差异内容：NA|类名：WindowProperties；<br>API声明：id: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：enum ColorSpace<br>差异内容：NA|类名：window；<br>API声明：enum ColorSpace<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：DEFAULT<br>差异内容：NA|类名：ColorSpace；<br>API声明：DEFAULT<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：WIDE_GAMUT<br>差异内容：NA|类名：ColorSpace；<br>API声明：WIDE_GAMUT<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：interface Configuration<br>差异内容：NA|类名：window；<br>API声明：interface Configuration<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Configuration；<br>API声明：name: string;<br>差异内容：NA|类名：Configuration；<br>API声明：name: string;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Configuration；<br>API声明：windowType: WindowType;<br>差异内容：NA|类名：Configuration；<br>API声明：windowType: WindowType;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Configuration；<br>API声明：ctx?: BaseContext;<br>差异内容：NA|类名：Configuration；<br>API声明：ctx?: BaseContext;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Configuration；<br>API声明：displayId?: number;<br>差异内容：NA|类名：Configuration；<br>API声明：displayId?: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Configuration；<br>API声明：parentId?: number;<br>差异内容：NA|类名：Configuration；<br>API声明：parentId?: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：interface WindowLimits<br>差异内容：NA|类名：window；<br>API声明：interface WindowLimits<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowLimits；<br>API声明：maxWidth?: number;<br>差异内容：NA|类名：WindowLimits；<br>API声明：maxWidth?: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowLimits；<br>API声明：maxHeight?: number;<br>差异内容：NA|类名：WindowLimits；<br>API声明：maxHeight?: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowLimits；<br>API声明：minWidth?: number;<br>差异内容：NA|类名：WindowLimits；<br>API声明：minWidth?: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowLimits；<br>API声明：minHeight?: number;<br>差异内容：NA|类名：WindowLimits；<br>API声明：minHeight?: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：interface TitleButtonRect<br>差异内容：NA|类名：window；<br>API声明：interface TitleButtonRect<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：TitleButtonRect；<br>API声明：right: number;<br>差异内容：NA|类名：TitleButtonRect；<br>API声明：right: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：TitleButtonRect；<br>API声明：top: number;<br>差异内容：NA|类名：TitleButtonRect；<br>API声明：top: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：TitleButtonRect；<br>API声明：width: number;<br>差异内容：NA|类名：TitleButtonRect；<br>API声明：width: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：TitleButtonRect；<br>API声明：height: number;<br>差异内容：NA|类名：TitleButtonRect；<br>API声明：height: number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：function createWindow(config: Configuration, callback: AsyncCallback\<Window>): void;<br>差异内容：NA|类名：window；<br>API声明：function createWindow(config: Configuration, callback: AsyncCallback\<Window>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：function createWindow(config: Configuration): Promise\<Window>;<br>差异内容：NA|类名：window；<br>API声明：function createWindow(config: Configuration): Promise\<Window>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：function getLastWindow(ctx: BaseContext, callback: AsyncCallback\<Window>): void;<br>差异内容：NA|类名：window；<br>API声明：function getLastWindow(ctx: BaseContext, callback: AsyncCallback\<Window>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：function getLastWindow(ctx: BaseContext): Promise\<Window>;<br>差异内容：NA|类名：window；<br>API声明：function getLastWindow(ctx: BaseContext): Promise\<Window>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：function shiftAppWindowFocus(sourceWindowId: number, targetWindowId: number): Promise\<void>;<br>差异内容：NA|类名：window；<br>API声明：function shiftAppWindowFocus(sourceWindowId: number, targetWindowId: number): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：UNSPECIFIED = 0<br>差异内容：NA|类名：Orientation；<br>API声明：UNSPECIFIED = 0<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：LANDSCAPE = 2<br>差异内容：NA|类名：Orientation；<br>API声明：LANDSCAPE = 2<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：PORTRAIT_INVERTED = 3<br>差异内容：NA|类名：Orientation；<br>API声明：PORTRAIT_INVERTED = 3<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：LANDSCAPE_INVERTED = 4<br>差异内容：NA|类名：Orientation；<br>API声明：LANDSCAPE_INVERTED = 4<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：AUTO_ROTATION_PORTRAIT = 6<br>差异内容：NA|类名：Orientation；<br>API声明：AUTO_ROTATION_PORTRAIT = 6<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：AUTO_ROTATION_LANDSCAPE = 7<br>差异内容：NA|类名：Orientation；<br>API声明：AUTO_ROTATION_LANDSCAPE = 7<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：AUTO_ROTATION_RESTRICTED = 8<br>差异内容：NA|类名：Orientation；<br>API声明：AUTO_ROTATION_RESTRICTED = 8<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：AUTO_ROTATION_PORTRAIT_RESTRICTED = 9<br>差异内容：NA|类名：Orientation；<br>API声明：AUTO_ROTATION_PORTRAIT_RESTRICTED = 9<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10<br>差异内容：NA|类名：Orientation；<br>API声明：AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Orientation；<br>API声明：LOCKED = 11<br>差异内容：NA|类名：Orientation；<br>API声明：LOCKED = 11<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setWindowLayoutFullScreen(isLayoutFullScreen: boolean): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowSystemBarEnable(names: Array\<'status' \| 'navigation'>, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowSystemBarEnable(names: Array\<'status' \| 'navigation'>, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowSystemBarEnable(names: Array\<'status' \| 'navigation'>): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setWindowSystemBarEnable(names: Array\<'status' \| 'navigation'>): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowSystemBarProperties(systemBarProperties: SystemBarProperties, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowSystemBarProperties(systemBarProperties: SystemBarProperties, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowSystemBarProperties(systemBarProperties: SystemBarProperties): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setWindowSystemBarProperties(systemBarProperties: SystemBarProperties): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：on(type: 'keyboardHeightChange', callback: Callback\<number>): void;<br>差异内容：NA|类名：Window；<br>API声明：on(type: 'keyboardHeightChange', callback: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：off(type: 'keyboardHeightChange', callback?: Callback\<number>): void;<br>差异内容：NA|类名：Window；<br>API声明：off(type: 'keyboardHeightChange', callback?: Callback\<number>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：on(type: 'windowVisibilityChange', callback: Callback\<boolean>): void;<br>差异内容：NA|类名：Window；<br>API声明：on(type: 'windowVisibilityChange', callback: Callback\<boolean>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：off(type: 'windowVisibilityChange', callback?: Callback\<boolean>): void;<br>差异内容：NA|类名：Window；<br>API声明：off(type: 'windowVisibilityChange', callback?: Callback\<boolean>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：on(type: 'screenshot', callback: Callback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：on(type: 'screenshot', callback: Callback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：off(type: 'screenshot', callback?: Callback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：off(type: 'screenshot', callback?: Callback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：on(type: 'dialogTargetTouch', callback: Callback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：on(type: 'dialogTargetTouch', callback: Callback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：off(type: 'dialogTargetTouch', callback?: Callback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：off(type: 'dialogTargetTouch', callback?: Callback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：on(type: 'windowStatusChange', callback: Callback\<WindowStatusType>): void;<br>差异内容：NA|类名：Window；<br>API声明：on(type: 'windowStatusChange', callback: Callback\<WindowStatusType>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：off(type: 'windowStatusChange', callback?: Callback\<WindowStatusType>): void;<br>差异内容：NA|类名：Window；<br>API声明：off(type: 'windowStatusChange', callback?: Callback\<WindowStatusType>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：isWindowSupportWideGamut(): Promise\<boolean>;<br>差异内容：NA|类名：Window；<br>API声明：isWindowSupportWideGamut(): Promise\<boolean>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：isWindowSupportWideGamut(callback: AsyncCallback\<boolean>): void;<br>差异内容：NA|类名：Window；<br>API声明：isWindowSupportWideGamut(callback: AsyncCallback\<boolean>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowColorSpace(colorSpace: ColorSpace): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setWindowColorSpace(colorSpace: ColorSpace): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowColorSpace(colorSpace: ColorSpace, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowColorSpace(colorSpace: ColorSpace, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：getWindowColorSpace(): ColorSpace;<br>差异内容：NA|类名：Window；<br>API声明：getWindowColorSpace(): ColorSpace;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowFocusable(isFocusable: boolean): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setWindowFocusable(isFocusable: boolean): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowFocusable(isFocusable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowFocusable(isFocusable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowPrivacyMode(isPrivacyMode: boolean): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setWindowPrivacyMode(isPrivacyMode: boolean): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowTouchable(isTouchable: boolean): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setWindowTouchable(isTouchable: boolean): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowTouchable(isTouchable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowTouchable(isTouchable: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：snapshot(callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：NA|类名：Window；<br>API声明：snapshot(callback: AsyncCallback\<image.PixelMap>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：snapshot(): Promise\<image.PixelMap>;<br>差异内容：NA|类名：Window；<br>API声明：snapshot(): Promise\<image.PixelMap>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setAspectRatio(ratio: number, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：setAspectRatio(ratio: number, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setAspectRatio(ratio: number): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：setAspectRatio(ratio: number): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：resetAspectRatio(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：resetAspectRatio(callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：resetAspectRatio(): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：resetAspectRatio(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：minimize(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Window；<br>API声明：minimize(callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：minimize(): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：minimize(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：getWindowLimits(): WindowLimits;<br>差异内容：NA|类名：Window；<br>API声明：getWindowLimits(): WindowLimits;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowLimits(windowLimits: WindowLimits): Promise\<WindowLimits>;<br>差异内容：NA|类名：Window；<br>API声明：setWindowLimits(windowLimits: WindowLimits): Promise\<WindowLimits>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：keepKeyboardOnFocus(keepKeyboardFlag: boolean): void;<br>差异内容：NA|类名：Window；<br>API声明：keepKeyboardOnFocus(keepKeyboardFlag: boolean): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：recover(): Promise\<void>;<br>差异内容：NA|类名：Window；<br>API声明：recover(): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowDecorVisible(isVisible: boolean): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowDecorVisible(isVisible: boolean): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：setWindowDecorHeight(height: number): void;<br>差异内容：NA|类名：Window；<br>API声明：setWindowDecorHeight(height: number): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：getWindowDecorHeight(): number;<br>差异内容：NA|类名：Window；<br>API声明：getWindowDecorHeight(): number;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：getTitleButtonRect(): TitleButtonRect;<br>差异内容：NA|类名：Window；<br>API声明：getTitleButtonRect(): TitleButtonRect;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：on(type: 'windowTitleButtonRectChange', callback: Callback\<TitleButtonRect>): void;<br>差异内容：NA|类名：Window；<br>API声明：on(type: 'windowTitleButtonRectChange', callback: Callback\<TitleButtonRect>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：Window；<br>API声明：off(type: 'windowTitleButtonRectChange', callback?: Callback\<TitleButtonRect>): void;<br>差异内容：NA|类名：Window；<br>API声明：off(type: 'windowTitleButtonRectChange', callback?: Callback\<TitleButtonRect>): void;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：window；<br>API声明：interface SubWindowOptions<br>差异内容：NA|类名：window；<br>API声明：interface SubWindowOptions<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：SubWindowOptions；<br>API声明：title: string;<br>差异内容：NA|类名：SubWindowOptions；<br>API声明：title: string;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：SubWindowOptions；<br>API声明：decorEnabled: boolean;<br>差异内容：NA|类名：SubWindowOptions；<br>API声明：decorEnabled: boolean;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：WindowStage；<br>API声明：createSubWindowWithOptions(name: string, options: SubWindowOptions): Promise\<Window>;<br>差异内容：NA|类名：WindowStage；<br>API声明：createSubWindowWithOptions(name: string, options: SubWindowOptions): Promise\<Window>;<br>差异内容：atomicservice|api/@ohos.window.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface AppResponse<br>差异内容：NA|类名：global；<br>API声明：export interface AppResponse<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：AppResponse；<br>API声明：appID: string;<br>差异内容：NA|类名：AppResponse；<br>API声明：appID: string;<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：AppResponse；<br>API声明：appName: string;<br>差异内容：NA|类名：AppResponse；<br>API声明：appName: string;<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：AppResponse；<br>API声明：versionName: string;<br>差异内容：NA|类名：AppResponse；<br>API声明：versionName: string;<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：AppResponse；<br>API声明：versionCode: number;<br>差异内容：NA|类名：AppResponse；<br>API声明：versionCode: number;<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export default class App<br>差异内容：NA|类名：global；<br>API声明：export default class App<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：App；<br>API声明：static getInfo(): AppResponse;<br>差异内容：NA|类名：App；<br>API声明：static getInfo(): AppResponse;<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：App；<br>API声明：static terminate(): void;<br>差异内容：NA|类名：App；<br>API声明：static terminate(): void;<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：App；<br>API声明：static setImageCacheCount(value: number): void;<br>差异内容：NA|类名：App；<br>API声明：static setImageCacheCount(value: number): void;<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：App；<br>API声明：static setImageRawDataCacheSize(value: number): void;<br>差异内容：NA|类名：App；<br>API声明：static setImageRawDataCacheSize(value: number): void;<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：App；<br>API声明：static setImageFileCacheSize(value: number): void;<br>差异内容：NA|类名：App；<br>API声明：static setImageFileCacheSize(value: number): void;<br>差异内容：atomicservice|api/@system.app.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export interface LocaleResponse<br>差异内容：NA|类名：global；<br>API声明：export interface LocaleResponse<br>差异内容：atomicservice|api/@system.configuration.d.ts|
|API从不支持元服务到支持元服务|类名：LocaleResponse；<br>API声明：language: string;<br>差异内容：NA|类名：LocaleResponse；<br>API声明：language: string;<br>差异内容：atomicservice|api/@system.configuration.d.ts|
|API从不支持元服务到支持元服务|类名：LocaleResponse；<br>API声明：countryOrRegion: string;<br>差异内容：NA|类名：LocaleResponse；<br>API声明：countryOrRegion: string;<br>差异内容：atomicservice|api/@system.configuration.d.ts|
|API从不支持元服务到支持元服务|类名：LocaleResponse；<br>API声明：dir: "ltr" \| "rtl";<br>差异内容：NA|类名：LocaleResponse；<br>API声明：dir: "ltr" \| "rtl";<br>差异内容：atomicservice|api/@system.configuration.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export default class Configuration<br>差异内容：NA|类名：global；<br>API声明：export default class Configuration<br>差异内容：atomicservice|api/@system.configuration.d.ts|
|API从不支持元服务到支持元服务|类名：Configuration；<br>API声明：static getLocale(): LocaleResponse;<br>差异内容：NA|类名：Configuration；<br>API声明：static getLocale(): LocaleResponse;<br>差异内容：atomicservice|api/@system.configuration.d.ts|
|函数变更|类名：PasteEvent；<br>API声明：preventDefault?: () => void;<br>差异内容：() => void|类名：PasteEvent；<br>API声明：preventDefault?: Callback\<void>;<br>差异内容：Callback\<void>|component/rich_editor.d.ts|
|函数变更|类名：RichEditorGesture；<br>API声明：onClick?: (event: ClickEvent) => void;<br>差异内容：(event: ClickEvent) => void|类名：RichEditorGesture；<br>API声明：onClick?: Callback\<ClickEvent>;<br>差异内容：Callback\<ClickEvent>|component/rich_editor.d.ts|
|函数变更|类名：RichEditorGesture；<br>API声明：onLongPress?: (event: GestureEvent) => void;<br>差异内容：(event: GestureEvent) => void|类名：RichEditorGesture；<br>API声明：onLongPress?: Callback\<GestureEvent>;<br>差异内容：Callback\<GestureEvent>|component/rich_editor.d.ts|
|函数变更|类名：SelectionMenuOptions；<br>API声明：onAppear?: () => void;<br>差异内容：() => void|类名：SelectionMenuOptions；<br>API声明：onAppear?: MenuOnAppearCallback;<br>差异内容：MenuOnAppearCallback|component/rich_editor.d.ts|
|函数变更|类名：SelectionMenuOptions；<br>API声明：onDisappear?: () => void;<br>差异内容：() => void|类名：SelectionMenuOptions；<br>API声明：onDisappear?: Callback\<void>;<br>差异内容：Callback\<void>|component/rich_editor.d.ts|
|函数变更|类名：RichEditorAttribute；<br>API声明：onReady(callback: () => void): RichEditorAttribute;<br>差异内容：callback: () => void|类名：RichEditorAttribute；<br>API声明：onReady(callback: Callback\<void>): RichEditorAttribute;<br>差异内容：callback: Callback\<void>|component/rich_editor.d.ts|
|函数变更|类名：RichEditorAttribute；<br>API声明：onSelect(callback: (value: RichEditorSelection) => void): RichEditorAttribute;<br>差异内容：callback: (value: RichEditorSelection) => void|类名：RichEditorAttribute；<br>API声明：onSelect(callback: Callback\<RichEditorSelection>): RichEditorAttribute;<br>差异内容：callback: Callback\<RichEditorSelection>|component/rich_editor.d.ts|
|函数变更|类名：RichEditorAttribute；<br>API声明：aboutToIMEInput(callback: (value: RichEditorInsertValue) => boolean): RichEditorAttribute;<br>差异内容：callback: (value: RichEditorInsertValue) => boolean|类名：RichEditorAttribute；<br>API声明：aboutToIMEInput(callback: Callback\<RichEditorInsertValue, boolean>): RichEditorAttribute;<br>差异内容：callback: Callback\<RichEditorInsertValue, boolean>|component/rich_editor.d.ts|
|函数变更|类名：RichEditorAttribute；<br>API声明：onIMEInputComplete(callback: (value: RichEditorTextSpanResult) => void): RichEditorAttribute;<br>差异内容：callback: (value: RichEditorTextSpanResult) => void|类名：RichEditorAttribute；<br>API声明：onIMEInputComplete(callback: Callback\<RichEditorTextSpanResult>): RichEditorAttribute;<br>差异内容：callback: Callback\<RichEditorTextSpanResult>|component/rich_editor.d.ts|
|函数变更|类名：RichEditorAttribute；<br>API声明：aboutToDelete(callback: (value: RichEditorDeleteValue) => boolean): RichEditorAttribute;<br>差异内容：callback: (value: RichEditorDeleteValue) => boolean|类名：RichEditorAttribute；<br>API声明：aboutToDelete(callback: Callback\<RichEditorDeleteValue, boolean>): RichEditorAttribute;<br>差异内容：callback: Callback\<RichEditorDeleteValue, boolean>|component/rich_editor.d.ts|
|函数变更|类名：RichEditorAttribute；<br>API声明：onDeleteComplete(callback: () => void): RichEditorAttribute;<br>差异内容：callback: () => void|类名：RichEditorAttribute；<br>API声明：onDeleteComplete(callback: Callback\<void>): RichEditorAttribute;<br>差异内容：callback: Callback\<void>|component/rich_editor.d.ts|
|函数变更|类名：RichEditorAttribute；<br>API声明：onPaste(callback: (event?: PasteEvent) => void): RichEditorAttribute;<br>差异内容：callback: (event?: PasteEvent) => void|类名：RichEditorAttribute；<br>API声明：onPaste(callback: PasteEventCallback): RichEditorAttribute;<br>差异内容：callback: PasteEventCallback|component/rich_editor.d.ts|
|函数变更|类名：SearchAttribute；<br>API声明：onChange(callback: (value: string) => void): SearchAttribute;<br>差异内容：callback: (value: string) => void|类名：SearchAttribute；<br>API声明：onChange(callback: EditableTextOnChangeCallback): SearchAttribute;<br>差异内容：callback: EditableTextOnChangeCallback|component/search.d.ts|
|函数变更|类名：SpanAttribute；<br>API声明：decoration(value: {<br>        type: TextDecorationType;<br>        color?: ResourceColor;<br>    }): SpanAttribute;<br>差异内容：value: {<br>        type: TextDecorationType;<br>        color?: ResourceColor;<br>    }|类名：SpanAttribute；<br>API声明：decoration(value: DecorationStyleInterface): SpanAttribute;<br>差异内容：value: DecorationStyleInterface|component/span.d.ts|
|函数变更|类名：TextAttribute；<br>API声明：decoration(value: {<br>        type: TextDecorationType;<br>        color?: ResourceColor;<br>    }): TextAttribute;<br>差异内容：value: {<br>        type: TextDecorationType;<br>        color?: ResourceColor;<br>    }|类名：TextAttribute；<br>API声明：decoration(value: DecorationStyleInterface): TextAttribute;<br>差异内容：value: DecorationStyleInterface|component/text.d.ts|
|函数变更|类名：TextAreaAttribute；<br>API声明：onChange(callback: (value: string) => void): TextAreaAttribute;<br>差异内容：callback: (value: string) => void|类名：TextAreaAttribute；<br>API声明：onChange(callback: EditableTextOnChangeCallback): TextAreaAttribute;<br>差异内容：callback: EditableTextOnChangeCallback|component/text_area.d.ts|
|函数变更|类名：TextInputAttribute；<br>API声明：onChange(callback: (value: string) => void): TextInputAttribute;<br>差异内容：callback: (value: string) => void|类名：TextInputAttribute；<br>API声明：onChange(callback: EditableTextOnChangeCallback): TextInputAttribute;<br>差异内容：callback: EditableTextOnChangeCallback|component/text_input.d.ts|
|函数变更|类名：PiPController；<br>API声明：on(type: 'controlPanelActionEvent', callback: (event: PiPActionEventType) => void): void;<br>差异内容：callback: (event: PiPActionEventType) => void|类名：PiPController；<br>API声明：on(type: 'controlPanelActionEvent', callback: ControlPanelActionEventCallback): void;<br>差异内容：callback: ControlPanelActionEventCallback|api/@ohos.PiPWindow.d.ts|
|函数变更|类名：CommonMethod；<br>API声明：overlay(value: string \| CustomBuilder, options?: { align?: Alignment; offset?: { x?: number; y?: number } }): T;<br>差异内容：options?: { align?: Alignment; offset?: { x?: number; y?: number } }|类名：CommonMethod；<br>API声明：overlay(value: string \| CustomBuilder \| ComponentContent, options?: OverlayOptions): T;<br>差异内容：options?: OverlayOptions|component/common.d.ts|
|函数变更|类名：DragController；<br>API声明：executeDrag(custom: CustomBuilder \| DragItemInfo, dragInfo: dragController.DragInfo, callback: AsyncCallback\<{<br>        event: DragEvent;<br>        extraParams: string;<br>    }>): void;<br>差异内容：callback: AsyncCallback\<{<br>        event: DragEvent;<br>        extraParams: string;<br>    }>|类名：DragController；<br>API声明：executeDrag(custom: CustomBuilder \| DragItemInfo, dragInfo: dragController.DragInfo, callback: AsyncCallback\<dragController.DragEventParam>): void;<br>差异内容：callback: AsyncCallback\<dragController.DragEventParam>|api/@ohos.arkui.UIContext.d.ts|
|函数变更|类名：dragController；<br>API声明：function executeDrag(custom: CustomBuilder \| DragItemInfo, dragInfo: DragInfo, callback: AsyncCallback\<{<br>        event: DragEvent;<br>        extraParams: string;<br>    }>): void;<br>差异内容：callback: AsyncCallback\<{<br>        event: DragEvent;<br>        extraParams: string;<br>    }>|类名：dragController；<br>API声明：function executeDrag(custom: CustomBuilder \| DragItemInfo, dragInfo: DragInfo, callback: AsyncCallback\<DragEventParam>): void;<br>差异内容：callback: AsyncCallback\<DragEventParam>|api/@ohos.arkui.dragController.d.ts|
|函数变更|类名：Window；<br>API声明：on(type: 'avoidAreaChange', callback: Callback\<{<br>            type: AvoidAreaType;<br>            area: AvoidArea;<br>        }>): void;<br>差异内容：callback: Callback\<{<br>            type: AvoidAreaType;<br>            area: AvoidArea;<br>        }>|类名：Window；<br>API声明：on(type: 'avoidAreaChange', callback: Callback\<AvoidAreaOptions>): void;<br>差异内容：callback: Callback\<AvoidAreaOptions>|api/@ohos.window.d.ts|
|函数变更|类名：Window；<br>API声明：off(type: 'avoidAreaChange', callback?: Callback\<{<br>            type: AvoidAreaType;<br>            area: AvoidArea;<br>        }>): void;<br>差异内容：callback?: Callback\<{<br>            type: AvoidAreaType;<br>            area: AvoidArea;<br>        }>|类名：Window；<br>API声明：off(type: 'avoidAreaChange', callback?: Callback\<AvoidAreaOptions>): void;<br>差异内容：callback?: Callback\<AvoidAreaOptions>|api/@ohos.window.d.ts|
|新增导出符号|类名：global；<br>API声明：export declare function loadNativeModule(moduleName: string): Object;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export declare function loadNativeModule(moduleName: string): Object;|api/@internal/full/global.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface TypedFrameNode<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface TypedFrameNode|api/arkui/FrameNode.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface Circle<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface Circle|api/arkui/Graphics.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface CommandPath<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface CommandPath|api/arkui/Graphics.d.ts|
|新增导出符号|类名：global；<br>API声明：export type BorderRadiuses = Corners\<number>;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type BorderRadiuses = Corners\<number>;|api/arkui/Graphics.d.ts|
|新增导出符号|类名：global；<br>API声明：export type CornerRadius = Corners\<Vector2>;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type CornerRadius = Corners\<Vector2>;|api/arkui/Graphics.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface Edges<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface Edges|api/arkui/Graphics.d.ts|
|新增导出符号|类名：global；<br>API声明：export function edgeWidths(all: number): Edges\<number>;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export function edgeWidths(all: number): Edges\<number>;|api/arkui/Graphics.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface SizeT<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface SizeT|api/arkui/Graphics.d.ts|
|新增导出符号|类名：global；<br>API声明：export type PositionT\<T> = Vector2T\<T>;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type PositionT\<T> = Vector2T\<T>;|api/arkui/Graphics.d.ts|
|新增导出符号|类名：global；<br>API声明：export interface LocalizedLabelMarginOptions<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export interface LocalizedLabelMarginOptions|api/@ohos.arkui.advanced.Chip.d.ets|
|新增导出符号|类名：global；<br>API声明：export class DynamicSyncScene<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export class DynamicSyncScene|api/@ohos.arkui.UIContext.d.ts|
|新增导出符号|类名：global；<br>API声明：export class FocusController<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export class FocusController|api/@ohos.arkui.UIContext.d.ts|
|新增导出符号|类名：global；<br>API声明：export type PointerStyle = pointer.PointerStyle;<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export type PointerStyle = pointer.PointerStyle;|api/@ohos.arkui.UIContext.d.ts|
|新增导出符号|类名：global；<br>API声明：export class ComponentSnapshot<br>差异内容：NA|类名：global；<br>API声明：<br>差异内容：export class ComponentSnapshot|api/@ohos.arkui.UIContext.d.ts|
|新增继承父类|类名：global；<br>API声明：declare class RichEditorController<br>差异内容：NA|类名：global；<br>API声明：declare class RichEditorController<br>差异内容：declare class RichEditorController|component/rich_editor.d.ts|
|属性类型匿名对象整改兼容|类名：RichEditorTextStyle；<br>API声明：decoration?: {<br>        type: TextDecorationType;<br>        color?: ResourceColor;<br>    };<br>差异内容：{<br>        type: TextDecorationType;<br>        color?: ResourceColor;<br>    }|类名：RichEditorTextStyle；<br>API声明：decoration?: DecorationStyleInterface;<br>差异内容：DecorationStyleInterface|component/rich_editor.d.ts|
|属性类型匿名对象整改兼容|类名：RichEditorTextStyleResult；<br>API声明：decoration: {<br>        type: TextDecorationType;<br>        color: ResourceColor;<br>    };<br>差异内容：{<br>        type: TextDecorationType;<br>        color: ResourceColor;<br>    }|类名：RichEditorTextStyleResult；<br>API声明：decoration: DecorationStyleResult;<br>差异内容：DecorationStyleResult|component/rich_editor.d.ts|
