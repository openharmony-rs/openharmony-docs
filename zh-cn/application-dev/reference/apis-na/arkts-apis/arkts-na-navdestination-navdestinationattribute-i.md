# NavDestinationAttribute

支持通用属性。

**继承/实现关系：** NavDestinationAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface NavDestinationAttribute--><!--Device-unnamed-export declare interface NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<NavDestinationAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-attributeModifier(modifier: AttributeModifier<NavDestinationAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-NavDestinationAttribute-attributeModifier(modifier: AttributeModifier<NavDestinationAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[NavDestinationAttribute](arkts-na-navdestination-navdestinationattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backButtonIcon

```TypeScript
backButtonIcon(icon: ResourceStr | PixelMap | SymbolGlyphModifier | undefined, accessibilityText?: ResourceStr | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-backButtonIcon(icon: ResourceStr | PixelMap | SymbolGlyphModifier | undefined, accessibilityText?: ResourceStr | undefined): this--><!--Device-NavDestinationAttribute-backButtonIcon(icon: ResourceStr | PixelMap | SymbolGlyphModifier | undefined, accessibilityText?: ResourceStr | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| SymbolGlyphModifier \| undefined | 是 |  |
| accessibilityText | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindToNestedScrollable

```TypeScript
bindToNestedScrollable(scrollInfos: Array<NestedScrollInfo> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-bindToNestedScrollable(scrollInfos: Array<NestedScrollInfo> | undefined): this--><!--Device-NavDestinationAttribute-bindToNestedScrollable(scrollInfos: Array<NestedScrollInfo> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollInfos | Array&lt;[NestedScrollInfo](arkts-na-navdestination-nestedscrollinfo-i.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindToScrollable

```TypeScript
bindToScrollable(scrollers: Array<Scroller> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-bindToScrollable(scrollers: Array<Scroller> | undefined): this--><!--Device-NavDestinationAttribute-bindToScrollable(scrollers: Array<Scroller> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollers | Array&lt;[Scroller](../../apis-arkui/arkts-components/arkts-arkui-scroller-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## customTransition

```TypeScript
customTransition(delegate: NavDestinationTransitionDelegate | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-customTransition(delegate: NavDestinationTransitionDelegate | undefined): this--><!--Device-NavDestinationAttribute-customTransition(delegate: NavDestinationTransitionDelegate | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | [NavDestinationTransitionDelegate](arkts-na-navdestinationtransitiondelegate-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableNavigationIndicator

```TypeScript
enableNavigationIndicator(enabled: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-enableNavigationIndicator(enabled: boolean | undefined): this--><!--Device-NavDestinationAttribute-enableNavigationIndicator(enabled: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableStatusBar

```TypeScript
enableStatusBar(enabled: boolean | undefined, animated?: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-enableStatusBar(enabled: boolean | undefined, animated?: boolean | undefined): this--><!--Device-NavDestinationAttribute-enableStatusBar(enabled: boolean | undefined, animated?: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 |  |
| animated | boolean \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## fullScreenOverlay

```TypeScript
fullScreenOverlay(fullScreenOverlay: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-fullScreenOverlay(fullScreenOverlay: boolean | undefined): this--><!--Device-NavDestinationAttribute-fullScreenOverlay(fullScreenOverlay: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullScreenOverlay | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideBackButton

```TypeScript
hideBackButton(hide: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-hideBackButton(hide: boolean | undefined): this--><!--Device-NavDestinationAttribute-hideBackButton(hide: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideTitleBar

```TypeScript
hideTitleBar(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-hideTitleBar(value: boolean | undefined): this--><!--Device-NavDestinationAttribute-hideTitleBar(value: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideTitleBar

```TypeScript
hideTitleBar(hide: boolean | undefined, animated: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-hideTitleBar(hide: boolean | undefined, animated: boolean | undefined): this--><!--Device-NavDestinationAttribute-hideTitleBar(hide: boolean | undefined, animated: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean \| undefined | 是 |  |
| animated | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideToolBar

```TypeScript
hideToolBar(hide: boolean | undefined, animated?: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-hideToolBar(hide: boolean | undefined, animated?: boolean | undefined): this--><!--Device-NavDestinationAttribute-hideToolBar(hide: boolean | undefined, animated?: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean \| undefined | 是 |  |
| animated | boolean \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## ignoreLayoutSafeArea

```TypeScript
ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this--><!--Device-NavDestinationAttribute-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;[LayoutSafeAreaType](../../apis-arkui/arkts-components/arkts-arkui-layoutsafeareatype-e.md)&gt; \| undefined | 否 |  |
| edges | Array&lt;[LayoutSafeAreaEdge](../../apis-arkui/arkts-components/arkts-arkui-layoutsafeareaedge-e.md)&gt; \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## menus

```TypeScript
menus(items: Array<NavigationMenuItem> | CustomBuilder | undefined, options?: NavigationMenuOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-menus(items: Array<NavigationMenuItem> | CustomBuilder | undefined, options?: NavigationMenuOptions | undefined): this--><!--Device-NavDestinationAttribute-menus(items: Array<NavigationMenuItem> | CustomBuilder | undefined, options?: NavigationMenuOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;NavigationMenuItem&gt; \| CustomBuilder \| undefined | 是 |  |
| options | [NavigationMenuOptions](../../apis-arkui/arkts-components/arkts-arkui-navigationmenuoptions-i.md) \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## mode

```TypeScript
mode(value: NavDestinationMode | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-mode(value: NavDestinationMode | undefined): this--><!--Device-NavDestinationAttribute-mode(value: NavDestinationMode | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NavDestinationMode](arkts-na-navdestination-navdestinationmode-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActive

```TypeScript
onActive(callback: Callback<NavDestinationActiveReason> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onActive(callback: Callback<NavDestinationActiveReason> | undefined): this--><!--Device-NavDestinationAttribute-onActive(callback: Callback<NavDestinationActiveReason> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[NavDestinationActiveReason](arkts-na-navdestination-navdestinationactivereason-e.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onBackPressed

```TypeScript
onBackPressed(callback: (() => boolean) | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onBackPressed(callback: (() => boolean) | undefined): this--><!--Device-NavDestinationAttribute-onBackPressed(callback: (() => boolean) | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (() =&gt; boolean) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onHidden

```TypeScript
onHidden(callback: Callback<VisibilityChangeReason> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onHidden(callback: Callback<VisibilityChangeReason> | undefined): this--><!--Device-NavDestinationAttribute-onHidden(callback: Callback<VisibilityChangeReason> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[VisibilityChangeReason](arkts-na-navdestination-visibilitychangereason-e.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onInactive

```TypeScript
onInactive(callback: Callback<NavDestinationActiveReason> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onInactive(callback: Callback<NavDestinationActiveReason> | undefined): this--><!--Device-NavDestinationAttribute-onInactive(callback: Callback<NavDestinationActiveReason> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[NavDestinationActiveReason](arkts-na-navdestination-navdestinationactivereason-e.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onNewParam

```TypeScript
onNewParam(callback: Callback<Object | null | undefined> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onNewParam(callback: Callback<Object | null | undefined> | undefined): this--><!--Device-NavDestinationAttribute-onNewParam(callback: Callback<Object | null | undefined> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Object \| null \| undefined&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onReady

```TypeScript
onReady(callback: Callback<NavDestinationContext> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onReady(callback: Callback<NavDestinationContext> | undefined): this--><!--Device-NavDestinationAttribute-onReady(callback: Callback<NavDestinationContext> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[NavDestinationContext](arkts-na-navdestination-navdestinationcontext-i.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onResult

```TypeScript
onResult(callback: Callback<Object | null | undefined> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onResult(callback: Callback<Object | null | undefined> | undefined): this--><!--Device-NavDestinationAttribute-onResult(callback: Callback<Object | null | undefined> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Object \| null \| undefined&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onShown

```TypeScript
onShown(callback: Callback<VisibilityChangeReason> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onShown(callback: Callback<VisibilityChangeReason> | undefined): this--><!--Device-NavDestinationAttribute-onShown(callback: Callback<VisibilityChangeReason> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[VisibilityChangeReason](arkts-na-navdestination-visibilitychangereason-e.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onWillAppear

```TypeScript
onWillAppear(callback: VoidCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onWillAppear(callback: VoidCallback | undefined): this--><!--Device-NavDestinationAttribute-onWillAppear(callback: VoidCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onWillDisappear

```TypeScript
onWillDisappear(callback: VoidCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onWillDisappear(callback: VoidCallback | undefined): this--><!--Device-NavDestinationAttribute-onWillDisappear(callback: VoidCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onWillHide

```TypeScript
onWillHide(callback: VoidCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onWillHide(callback: VoidCallback | undefined): this--><!--Device-NavDestinationAttribute-onWillHide(callback: VoidCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onWillShow

```TypeScript
onWillShow(callback: VoidCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-onWillShow(callback: VoidCallback | undefined): this--><!--Device-NavDestinationAttribute-onWillShow(callback: VoidCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## preferredOrientation

```TypeScript
preferredOrientation(orientation: Orientation | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-preferredOrientation(orientation: Orientation | undefined): this--><!--Device-NavDestinationAttribute-preferredOrientation(orientation: Orientation | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | [Orientation](arkts-na-orientation-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## recoverable

```TypeScript
recoverable(recoverable: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-recoverable(recoverable: boolean | undefined): this--><!--Device-NavDestinationAttribute-recoverable(recoverable: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recoverable | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setNavDestinationOptions

```TypeScript
setNavDestinationOptions(moduleInfo?: NavDestinationModuleInfo): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-setNavDestinationOptions(moduleInfo?: NavDestinationModuleInfo): this--><!--Device-NavDestinationAttribute-setNavDestinationOptions(moduleInfo?: NavDestinationModuleInfo): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleInfo | [NavDestinationModuleInfo](arkts-na-navdestination-navdestinationmoduleinfo-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## systemBarStyle

```TypeScript
systemBarStyle(style: SystemBarStyle | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-systemBarStyle(style: SystemBarStyle | undefined): this--><!--Device-NavDestinationAttribute-systemBarStyle(style: SystemBarStyle | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [SystemBarStyle](../../apis-arkui/arkts-components/arkts-arkui-systembarstyle-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## systemTransition

```TypeScript
systemTransition(type: NavigationSystemTransitionType | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-systemTransition(type: NavigationSystemTransitionType | undefined): this--><!--Device-NavDestinationAttribute-systemTransition(type: NavigationSystemTransitionType | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [NavigationSystemTransitionType](arkts-na-navdestination-navigationsystemtransitiontype-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## title

```TypeScript
title(value: string | CustomBuilder | NavDestinationCommonTitle | NavDestinationCustomTitle | Resource | undefined, options?: NavigationTitleOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-title(value: string | CustomBuilder | NavDestinationCommonTitle | NavDestinationCustomTitle | Resource | undefined, options?: NavigationTitleOptions | undefined): this--><!--Device-NavDestinationAttribute-title(value: string | CustomBuilder | NavDestinationCommonTitle | NavDestinationCustomTitle | Resource | undefined, options?: NavigationTitleOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| CustomBuilder \| [NavDestinationCommonTitle](arkts-na-navdestination-navdestinationcommontitle-i.md) \| [NavDestinationCustomTitle](arkts-na-navdestination-navdestinationcustomtitle-i.md) \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| undefined | 是 |  |
| options | NavigationTitleOptions \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## toolbarConfiguration

```TypeScript
toolbarConfiguration(toolbarParam: Array<ToolbarItem> | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-NavDestinationAttribute-toolbarConfiguration(toolbarParam: Array<ToolbarItem> | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined): this--><!--Device-NavDestinationAttribute-toolbarConfiguration(toolbarParam: Array<ToolbarItem> | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toolbarParam | Array&lt;ToolbarItem&gt; \| CustomBuilder \| undefined | 是 |  |
| options | [NavigationToolbarOptions](../../apis-arkui/arkts-components/arkts-arkui-navigationtoolbaroptions-i.md) \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

设置navDestination选项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationAttribute-default--><!--Device-NavDestinationAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

