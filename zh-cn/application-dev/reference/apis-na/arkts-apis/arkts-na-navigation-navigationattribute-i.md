# NavigationAttribute

除支持通用属性外，还支持以下属性：

**继承/实现关系：** NavigationAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface NavigationAttribute--><!--Device-unnamed-export declare interface NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<NavigationAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-attributeModifier(modifier: AttributeModifier<NavigationAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-NavigationAttribute-attributeModifier(modifier: AttributeModifier<NavigationAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[NavigationAttribute](arkts-na-navigation-navigationattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backButtonIcon

```TypeScript
backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier | undefined, accessibilityText?: ResourceStr | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier | undefined, accessibilityText?: ResourceStr | undefined): this--><!--Device-NavigationAttribute-backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier | undefined, accessibilityText?: ResourceStr | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | string \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| [SymbolGlyphModifier](../../apis-arkui/arkts-components/arkts-arkui-symbolglyphmodifier-t.md) \| undefined | 是 |  |
| accessibilityText | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## customNavContentTransition

```TypeScript
customNavContentTransition(delegate: ((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => NavigationAnimatedTransition | undefined) | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-customNavContentTransition(delegate: ((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => NavigationAnimatedTransition | undefined) | undefined): this--><!--Device-NavigationAttribute-customNavContentTransition(delegate: ((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => NavigationAnimatedTransition | undefined) | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | ((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) =&gt; NavigationAnimatedTransition \| undefined) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## divider

```TypeScript
divider(style: NavigationDividerStyle | null): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-divider(style: NavigationDividerStyle | null): this--><!--Device-NavigationAttribute-divider(style: NavigationDividerStyle | null): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [NavigationDividerStyle](arkts-na-navigation-navigationdividerstyle-i.md) \| null | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableDragBar

```TypeScript
enableDragBar(isEnabled: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-enableDragBar(isEnabled: boolean | undefined): this--><!--Device-NavigationAttribute-enableDragBar(isEnabled: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableModeChangeAnimation

```TypeScript
enableModeChangeAnimation(isEnabled: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-enableModeChangeAnimation(isEnabled: boolean | undefined): this--><!--Device-NavigationAttribute-enableModeChangeAnimation(isEnabled: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableToolBarAdaptation

```TypeScript
enableToolBarAdaptation(enable: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-enableToolBarAdaptation(enable: boolean | undefined): this--><!--Device-NavigationAttribute-enableToolBarAdaptation(enable: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableVisibilityLifecycleWithContentCover

```TypeScript
enableVisibilityLifecycleWithContentCover(isEnabled: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-enableVisibilityLifecycleWithContentCover(isEnabled: boolean | undefined): this--><!--Device-NavigationAttribute-enableVisibilityLifecycleWithContentCover(isEnabled: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideBackButton

```TypeScript
hideBackButton(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-hideBackButton(value: boolean | undefined): this--><!--Device-NavigationAttribute-hideBackButton(value: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideNavBar

```TypeScript
hideNavBar(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-hideNavBar(value: boolean | undefined): this--><!--Device-NavigationAttribute-hideNavBar(value: boolean | undefined): this-End-->

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
hideTitleBar(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-hideTitleBar(value: boolean | undefined): this--><!--Device-NavigationAttribute-hideTitleBar(value: boolean | undefined): this-End-->

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-hideTitleBar(hide: boolean | undefined, animated: boolean | undefined): this--><!--Device-NavigationAttribute-hideTitleBar(hide: boolean | undefined, animated: boolean | undefined): this-End-->

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
hideToolBar(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-hideToolBar(value: boolean | undefined): this--><!--Device-NavigationAttribute-hideToolBar(value: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideToolBar

```TypeScript
hideToolBar(hide: boolean | undefined, animated: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-hideToolBar(hide: boolean | undefined, animated: boolean | undefined): this--><!--Device-NavigationAttribute-hideToolBar(hide: boolean | undefined, animated: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean \| undefined | 是 |  |
| animated | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## ignoreLayoutSafeArea

```TypeScript
ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this--><!--Device-NavigationAttribute-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this-End-->

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-menus(items: Array<NavigationMenuItem> | CustomBuilder | undefined, options?: NavigationMenuOptions | undefined): this--><!--Device-NavigationAttribute-menus(items: Array<NavigationMenuItem> | CustomBuilder | undefined, options?: NavigationMenuOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;[NavigationMenuItem](arkts-na-navigation-navigationmenuitem-i.md)&gt; \| CustomBuilder \| undefined | 是 |  |
| options | [NavigationMenuOptions](arkts-na-navigation-navigationmenuoptions-i.md) \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## minContentWidth

```TypeScript
minContentWidth(value: Dimension | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-minContentWidth(value: Dimension | undefined): this--><!--Device-NavigationAttribute-minContentWidth(value: Dimension | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../../apis-arkui/arkts-apis/arkts-arkui-dimension-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## mode

```TypeScript
mode(value: NavigationMode | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-mode(value: NavigationMode | undefined): this--><!--Device-NavigationAttribute-mode(value: NavigationMode | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NavigationMode](arkts-na-navigation-navigationmode-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## navBarPosition

```TypeScript
navBarPosition(value: NavBarPosition | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-navBarPosition(value: NavBarPosition | undefined): this--><!--Device-NavigationAttribute-navBarPosition(value: NavBarPosition | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NavBarPosition](arkts-na-navigation-navbarposition-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## navBarWidth

```TypeScript
navBarWidth(value: Length | Bindable<Length> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-navBarWidth(value: Length | Bindable<Length> | undefined): this--><!--Device-NavigationAttribute-navBarWidth(value: Length | Bindable<Length> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| [Bindable](arkts-na-common-bindable-i.md)&lt;[Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## navBarWidthRange

```TypeScript
navBarWidthRange(value: [
        Dimension,
        Dimension
    ] | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-navBarWidthRange(value: [        Dimension,        Dimension    ] | undefined): this--><!--Device-NavigationAttribute-navBarWidthRange(value: [        Dimension,        Dimension    ] | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [         Dimension,         Dimension     ] \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## navDestination

```TypeScript
navDestination(builder: PageMapBuilder | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-navDestination(builder: PageMapBuilder | undefined): this--><!--Device-NavigationAttribute-navDestination(builder: PageMapBuilder | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | PageMapBuilder \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onNavBarStateChange

```TypeScript
onNavBarStateChange(callback: ((isVisible: boolean) => void) | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-onNavBarStateChange(callback: ((isVisible: boolean) => void) | undefined): this--><!--Device-NavigationAttribute-onNavBarStateChange(callback: ((isVisible: boolean) => void) | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ((isVisible: boolean) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onNavigationModeChange

```TypeScript
onNavigationModeChange(callback: ((mode: NavigationMode) => void) | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-onNavigationModeChange(callback: ((mode: NavigationMode) => void) | undefined): this--><!--Device-NavigationAttribute-onNavigationModeChange(callback: ((mode: NavigationMode) => void) | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ((mode: NavigationMode) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onTitleModeChange

```TypeScript
onTitleModeChange(callback: ((titleMode: NavigationTitleMode) => void) | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-onTitleModeChange(callback: ((titleMode: NavigationTitleMode) => void) | undefined): this--><!--Device-NavigationAttribute-onTitleModeChange(callback: ((titleMode: NavigationTitleMode) => void) | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ((titleMode: NavigationTitleMode) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## recoverable

```TypeScript
recoverable(recoverable: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-recoverable(recoverable: boolean | undefined): this--><!--Device-NavigationAttribute-recoverable(recoverable: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recoverable | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setNavigationOptions

```TypeScript
setNavigationOptions(pathInfos?: NavPathStack, homeDestination?: HomePathInfo, moduleInfo?: NavigationModuleInfo): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-setNavigationOptions(pathInfos?: NavPathStack, homeDestination?: HomePathInfo, moduleInfo?: NavigationModuleInfo): this--><!--Device-NavigationAttribute-setNavigationOptions(pathInfos?: NavPathStack, homeDestination?: HomePathInfo, moduleInfo?: NavigationModuleInfo): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-na-navigation-navpathstack-c.md) | 否 |  |
| homeDestination | [HomePathInfo](arkts-na-navigation-homepathinfo-i.md) | 否 |  |
| moduleInfo | [NavigationModuleInfo](arkts-na-navigation-navigationmoduleinfo-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setNavigationOptions

```TypeScript
setNavigationOptions(pathInfos?: NavPathStack,  moduleInfo?: NavigationModuleInfo): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-setNavigationOptions(pathInfos?: NavPathStack,  moduleInfo?: NavigationModuleInfo): this--><!--Device-NavigationAttribute-setNavigationOptions(pathInfos?: NavPathStack,  moduleInfo?: NavigationModuleInfo): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-na-navigation-navpathstack-c.md) | 否 |  |
| moduleInfo | [NavigationModuleInfo](arkts-na-navigation-navigationmoduleinfo-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## splitPlaceholder

```TypeScript
splitPlaceholder<T extends Object>(placeholder: ComponentContent<T>): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-splitPlaceholder<T extends Object>(placeholder: ComponentContent<T>): this--><!--Device-NavigationAttribute-splitPlaceholder<T extends Object>(placeholder: ComponentContent<T>): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| placeholder | ComponentContent&lt;T&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## systemBarStyle

```TypeScript
systemBarStyle(style: SystemBarStyle | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-systemBarStyle(style: SystemBarStyle | undefined): this--><!--Device-NavigationAttribute-systemBarStyle(style: SystemBarStyle | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [SystemBarStyle](arkts-na-systembarstyle-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## title

```TypeScript
title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle | undefined, options?: NavigationTitleOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle | undefined, options?: NavigationTitleOptions | undefined): this--><!--Device-NavigationAttribute-title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle | undefined, options?: NavigationTitleOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| CustomBuilder \| [NavigationCommonTitle](arkts-na-navigation-navigationcommontitle-i.md) \| [NavigationCustomTitle](arkts-na-navigation-navigationcustomtitle-i.md) \| undefined | 是 |  |
| options | [NavigationTitleOptions](arkts-na-navigation-navigationtitleoptions-i.md) \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## titleMode

```TypeScript
titleMode(value: NavigationTitleMode | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-titleMode(value: NavigationTitleMode | undefined): this--><!--Device-NavigationAttribute-titleMode(value: NavigationTitleMode | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NavigationTitleMode](arkts-na-navigation-navigationtitlemode-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## toolbarConfiguration

```TypeScript
toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-NavigationAttribute-toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined): this--><!--Device-NavigationAttribute-toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[ToolbarItem](arkts-na-navigation-toolbaritem-i.md)&gt; \| CustomBuilder \| undefined | 是 |  |
| options | [NavigationToolbarOptions](arkts-na-navigation-navigationtoolbaroptions-i.md) \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

Navigation双栏模式下，支持设置右侧页面显示默认占位页，占位页仅作为UI展示页，不可获焦和响应事件。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default--><!--Device-NavigationAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

