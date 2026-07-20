# NavDestination属性/事件

支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持如下事件：

**继承/实现关系：** NavDestinationAttribute extends [CommonMethod<NavDestinationAttribute>](CommonMethod<NavDestinationAttribute>)

**起始版本：** 9

<!--Device-unnamed-declare class NavDestinationAttribute extends CommonMethod<NavDestinationAttribute>--><!--Device-unnamed-declare class NavDestinationAttribute extends CommonMethod<NavDestinationAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="backbuttonicon"></a>
## backButtonIcon

```TypeScript
backButtonIcon(value: ResourceStr | PixelMap | SymbolGlyphModifier)
```

设置标题栏返回键图标。

> **说明：**

> - 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。  
>  
> - 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-backButtonIcon(value: ResourceStr | PixelMap | SymbolGlyphModifier): NavDestinationAttribute--><!--Device-NavDestinationAttribute-backButtonIcon(value: ResourceStr | PixelMap | SymbolGlyphModifier): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| PixelMap \| SymbolGlyphModifier | 是 | 标题栏返回键图标。<br>**起始版本：** 11 |

<a id="backbuttonicon-1"></a>
## backButtonIcon

```TypeScript
backButtonIcon(icon: ResourceStr | PixelMap | SymbolGlyphModifier, accessibilityText?: ResourceStr)
```

设置标题栏返回键图标和无障碍播报内容。

> **说明：**

> - 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。  
>  
> - 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-backButtonIcon(icon: ResourceStr | PixelMap | SymbolGlyphModifier, accessibilityText?: ResourceStr): NavDestinationAttribute--><!--Device-NavDestinationAttribute-backButtonIcon(icon: ResourceStr | PixelMap | SymbolGlyphModifier, accessibilityText?: ResourceStr): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| PixelMap \| SymbolGlyphModifier | 是 | 标题栏返回键图标。 |
| accessibilityText | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 否 | 返回键无障碍播报内容。</br>默认值：系统语言是中文时为“返回”，系统语言是英文时为“back”。 |

<a id="bindtonestedscrollable"></a>
## bindToNestedScrollable

```TypeScript
bindToNestedScrollable(scrollInfos: Array<NestedScrollInfo>)
```

绑定NavDestination组件和嵌套的可滚动容器组件（支持[List](../../apis-arkts/arkts-apis/arkts-arkts-util-list-list-c.md)、[Scroll](arkts-arkui-scroll.md)、[Grid](arkts-arkui-grid.md)、[WaterFlow](arkts-arkui-waterflow.md)），当滑动父组件或子组件时，会触发所有与其绑定的NavDestination组件的标题栏和工具栏的显示和隐藏动效，上滑隐藏，下滑显示。一个NavDestination可与多个嵌套的可滚动容器组件绑定，嵌套的可滚动容器组件也可与多个NavDestination绑定。使用示例参见[示例1](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#示例1标题栏工具栏与可滚动类组件联动)。

> **说明：**

> - 只有NavDestination的标题栏或工具栏设置为可见时，联动效果才会生效。  
>  
> - 当多个可滚动容器组件绑定了同一个NavDestination组件时，滚动任何一个容器都会触发标题栏和工具栏的显示或隐藏效果。且当任何一个可滚动容器组件滑动到底部或顶部位置时，会立即触发标题栏和工具栏的显示动效。因此，为了获  
> 得最佳用户体验，不建议同时触发多个可滚动容器组件的滚动事件。  
>  
> - 从API version 22开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-bindToNestedScrollable(scrollInfos: Array<NestedScrollInfo>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-bindToNestedScrollable(scrollInfos: Array<NestedScrollInfo>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollInfos | Array&lt;NestedScrollInfo&gt; | 是 | 嵌套的可滚动容器组件的控制器。 |

<a id="bindtoscrollable"></a>
## bindToScrollable

```TypeScript
bindToScrollable(scrollers: Array<Scroller>)
```

绑定NavDestination组件和可滚动容器组件（支持[List](../../apis-arkts/arkts-apis/arkts-arkts-util-list-list-c.md)、[Scroll](arkts-arkui-scroll.md)、[Grid](arkts-arkui-grid.md)、[WaterFlow](arkts-arkui-waterflow.md)），当滑动可滚动容器组件时，会触发所有与其绑定的NavDestination组件的标题栏和工具栏的显示和隐藏动效，上滑隐藏，下滑显示。一个NavDestination可与多个可滚动容器组件绑定，一个可滚动容器组件也可与多个NavDestination绑定。使用示例参见[示例1](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#示例1标题栏工具栏与可滚动类组件联动)。

> **说明：**

> - 只有NavDestination的标题栏或工具栏设置为可见时，联动效果才会生效。  
>  
> - 当多个可滚动容器组件绑定了同一个NavDestination组件时，滚动任何一个容器都会触发标题栏和工具栏的显示或隐藏效果。且当任何一个可滚动容器组件滑动到底部或顶部位置时，会立即触发标题栏和工具栏的显示动效。因此，为了获  
> 得最佳用户体验，不建议同时触发多个可滚动容器组件的滚动事件。  
>  
> - 从API version 22开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-bindToScrollable(scrollers: Array<Scroller>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-bindToScrollable(scrollers: Array<Scroller>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollers | Array&lt;Scroller&gt; | 是 | 可滚动容器组件的控制器。 |

<a id="customtransition"></a>
## customTransition

```TypeScript
customTransition(delegate: NavDestinationTransitionDelegate)
```

设置NavDestination自定义转场动画。

> **说明：**

> - 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。  
>  
> - 该属性与[systemTransition](NavDestinationAttribute#systemTransition)同时设置时，后设置的属性生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-customTransition(delegate: NavDestinationTransitionDelegate): NavDestinationAttribute--><!--Device-NavDestinationAttribute-customTransition(delegate: NavDestinationTransitionDelegate): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | [NavDestinationTransitionDelegate](arkts-arkui-navdestinationtransitiondelegate-t.md) | 是 | NavDestination自定义动画的代理函数。 |

<a id="enablenavigationindicator"></a>
## enableNavigationIndicator

```TypeScript
enableNavigationIndicator(enabled: Optional<boolean>)
```

设置进入该NavDestination后，显示或者隐藏系统的导航条。

> **说明：**

> 该属性满足如下全部条件时才生效：

> 设置系统导航条的实际效果依赖于具体的设备支持情况，具体参考窗口的  
> [setSpecificSystemBarEnabled](docroot://reference/apis-arkui/arkts-apis-window-Window.md#setspecificsystembarenabled11)  
> 接口。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-enableNavigationIndicator(enabled: Optional<boolean>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-enableNavigationIndicator(enabled: Optional<boolean>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 进入该NavDestination后，系统导航条的显示/隐藏状态。<br/>true：显示导航条。<br/>false：隐藏导航条。 |

<a id="enablestatusbar"></a>
## enableStatusBar

```TypeScript
enableStatusBar(enabled: Optional<boolean>, animated?: boolean)
```

设置进入该NavDestination后，显示或者隐藏系统的状态栏。

> **说明：**

> - 该属性满足如下全部条件时才生效：  
> > 1. NavDestination属于应用主窗口页面，并且主窗口为全屏窗口；  
> > 2. NavDestination所属的Navigation的大小占满整个页面；  
> > 3. NavDestination的大小占满整个Navigation组件；  
> > 4. NavDestination类型为[NavDestinationMode](arkts-arkui-navdestinationmode-e.md).STANDARD。  
>  
> - 设置系统状态栏的实际效果依赖于具体的设备支持情况，具体参考窗口的  
> [setSpecificSystemBarEnabled](docroot://reference/apis-arkui/arkts-apis-window-Window.md#setspecificsystembarenabled11)  
> 接口。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-enableStatusBar(enabled: Optional<boolean>, animated?: boolean): NavDestinationAttribute--><!--Device-NavDestinationAttribute-enableStatusBar(enabled: Optional<boolean>, animated?: boolean): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 进入该NavDestination后，系统状态栏的显示/隐藏状态。<br/>true：显示状态栏。<br/>false：隐藏状态栏。 |
| animated | boolean | 否 | 是否使用动画的方式显示/隐藏系统状态栏。<br/>默认值：false<br/>true：使用动画的方式显示/隐藏系统状态栏。<br/>false：不使用动画的方式显示/隐藏系统状态栏。 |

<a id="fullscreenoverlay"></a>
## fullScreenOverlay

```TypeScript
fullScreenOverlay(fullScreenOverlay: Optional<boolean>)
```

设置NavDestination是否以全屏覆盖模式显示。

当参数设置为true时，在Navigation分栏模式下，当前页面会覆盖整个Navigation容器，包括NavBar和内容区。该配置作用于当前NavDestination的所有实例；当路由栈中已有页面以全屏覆盖模式显示时，其后入栈的[DIALOG](arkts-arkui-navdestinationmode-e.md)页面与未设置fullScreenOverlay为false的[STANDARD](arkts-arkui-navdestinationmode-e.md)页面也会继承为全屏覆盖显示。未通过该接口设置时，NavDestination默认是普通显示模式，遵循Navigation分栏显示规则。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-fullScreenOverlay(fullScreenOverlay: Optional<boolean>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-fullScreenOverlay(fullScreenOverlay: Optional<boolean>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullScreenOverlay | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否以全屏覆盖模式显示。<br/>true：全屏覆盖模式，覆盖整个Navigation容器。<br/>false：普通显示模式，遵循Navigation分栏显示规则。指定为false的STANDARD类型页面不会继承全屏显示。<br/>undefined：普通显示模式，遵循Navigation分栏显示规则。指定为undefined的页面会继承全屏显示。 |

<a id="hidebackbutton"></a>
## hideBackButton

```TypeScript
hideBackButton(hide: Optional<boolean>)
```

设置是否隐藏标题栏中的返回键。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-hideBackButton(hide: Optional<boolean>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-hideBackButton(hide: Optional<boolean>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否隐藏标题栏中的返回键。 <br/>默认值：false<br/>true：隐藏返回键。<br/>false：显示返回键。 |

<a id="hidetitlebar"></a>
## hideTitleBar

```TypeScript
hideTitleBar(value: boolean)
```

设置是否隐藏标题栏。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-hideTitleBar(value: boolean): NavDestinationAttribute--><!--Device-NavDestinationAttribute-hideTitleBar(value: boolean): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否隐藏标题栏。<br/>默认值：false<br/>true：隐藏标题栏。<br/>false：显示标题栏。 |

<a id="hidetitlebar-1"></a>
## hideTitleBar

```TypeScript
hideTitleBar(hide: boolean, animated: boolean)
```

设置是否隐藏标题栏。与[hideTitleBar](NavDestinationAttribute#hideTitleBar(value: boolean))相比，新增标题栏显隐时是否使用动画。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-hideTitleBar(hide: boolean, animated: boolean): NavDestinationAttribute--><!--Device-NavDestinationAttribute-hideTitleBar(hide: boolean, animated: boolean): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean | 是 | 是否隐藏标题栏。<br/>默认值：false<br/>true：隐藏标题栏。<br/>false：显示标题栏。 |
| animated | boolean | 是 | 设置是否使用动画显隐标题栏。<br/>默认值：false<br/>true：使用动画显示隐藏标题栏。<br/>false：不使用动画显示隐藏标题栏。 |

<a id="hidetoolbar"></a>
## hideToolBar

```TypeScript
hideToolBar(hide: boolean, animated?: boolean)
```

设置是否隐藏工具栏。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-hideToolBar(hide: boolean, animated?: boolean): NavDestinationAttribute--><!--Device-NavDestinationAttribute-hideToolBar(hide: boolean, animated?: boolean): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean | 是 | 是否隐藏工具栏。<br/>默认值：false<br/>true：隐藏工具栏。<br/>false：显示工具栏。 |
| animated | boolean | 否 | 设置是否使用动画显隐工具栏。<br/>默认值：false<br/>true：使用动画显示隐藏工具栏。<br/>false：不使用动画显示隐藏工具栏。 |

<a id="ignorelayoutsafearea"></a>
## ignoreLayoutSafeArea

```TypeScript
ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>)
```

控制组件的布局，使其扩展到非安全区域。

> **说明：**

> - 组件设置ignoreLayoutSafeArea之后生效的条件为：  
> > 设置LayoutSafeAreaType.SYSTEM时，组件的边界与非安全区域重合时组件能够延伸到非安全区域下。  
>  
> - 若组件扩展到非安全区域内，此时在非安全区域里触发的事件（例如：点击事件）等可能会被系统拦截，优先响应状态栏等系统组件。  
>  
> - 组件想要扩展到非安全区域内，需隐藏或者设置标题栏和工具栏为[STACK](arkts-arkui-barstyle-e.md)模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;LayoutSafeAreaType&gt; | 否 | 配置扩展安全区域的类型。<br />默认值：<br />[LayoutSafeAreaType.SYSTEM] |
| edges | Array&lt;LayoutSafeAreaEdge&gt; | 否 | 配置扩展安全区域的方向。<br /> 默认值：<br />[LayoutSafeAreaEdge.TOP, LayoutSafeAreaEdge.BOTTOM]。 |

<a id="menus"></a>
## menus

```TypeScript
menus(value: Array<NavigationMenuItem> | CustomBuilder)
```

设置页面右上角菜单。不设置时不显示菜单项。使用Array<[NavigationMenuItem](arkts-arkui-navigationmenuitem-i.md)&gt; 写法时，竖屏最多支持显示3个图标，横屏最多支持显示5个图标，多余的图标会被放入自动生成的更多图标。

> **说明：**

> - 从API version 14开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。  
>  
> - 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-menus(value: Array<NavigationMenuItem> | CustomBuilder): NavDestinationAttribute--><!--Device-NavDestinationAttribute-menus(value: Array<NavigationMenuItem> | CustomBuilder): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;NavigationMenuItem&gt; \| CustomBuilder | 是 | 页面右上角菜单。 |

<a id="menus-1"></a>
## menus

```TypeScript
menus(items: Array<NavigationMenuItem> | CustomBuilder, options?: NavigationMenuOptions)
```

设置页面右上角菜单。不设置时不显示菜单项。与[menus](NavDestinationAttribute#menus(value: Array<NavigationMenuItem> | CustomBuilder))相比，新增菜单选项。使用Array<[NavigationMenuItem](arkts-arkui-navigationmenuitem-i.md)&gt; 写法时，竖屏最多支持显示3个图标，横屏最多支持显示5个图标，多余的图标会被放入自动生成的更多图标。

> **说明：**

> - 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。  
>  
> - 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-menus(items: Array<NavigationMenuItem> | CustomBuilder, options?: NavigationMenuOptions): NavDestinationAttribute--><!--Device-NavDestinationAttribute-menus(items: Array<NavigationMenuItem> | CustomBuilder, options?: NavigationMenuOptions): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;NavigationMenuItem&gt; \| CustomBuilder | 是 | 页面右上角菜单。 |
| options | [NavigationMenuOptions](arkts-arkui-navigationmenuoptions-i.md) | 否 | 页面右上角菜单选项。 |

<a id="mode"></a>
## mode

```TypeScript
mode(value: NavDestinationMode)
```

设置NavDestination类型，不支持动态修改。

> **说明：**

> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-mode(value: NavDestinationMode): NavDestinationAttribute--><!--Device-NavDestinationAttribute-mode(value: NavDestinationMode): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NavDestinationMode](arkts-arkui-navdestinationmode-e.md) | 是 | NavDestination类型。<br/>默认值：NavDestinationMode.STANDARD |

<a id="onactive"></a>
## onActive

```TypeScript
onActive(callback: Optional<Callback<NavDestinationActiveReason>>)
```

NavDestination处于激活态（处于栈顶可操作，且上层无特殊组件遮挡）时，触发该回调。使用示例参见[示例5](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#示例5navdestination的onactive与oninactive生命周期)。

> **说明：**

> 从API version 22开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onActive(callback: Optional<Callback<NavDestinationActiveReason>>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onActive(callback: Optional<Callback<NavDestinationActiveReason>>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;Callback&lt;NavDestinationActiveReason&gt;&gt; | 是 | Indicates callback when destination is active. |

<a id="onbackpressed"></a>
## onBackPressed

```TypeScript
onBackPressed(callback: () => boolean)
```

当与Navigation绑定的导航控制器中存在内容时，此回调生效。当点击返回键时，触发该回调。

返回值为true时，表示重写返回键逻辑，返回值为false时，表示回退到上一个页面。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onBackPressed(callback: () => boolean): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onBackPressed(callback: () => boolean): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; boolean | 是 | 当与Navigation绑定的导航控制器中存在内容时，此回调生效。当点击返回键时，触发该回调。 |

<a id="onhidden"></a>
## onHidden

```TypeScript
onHidden(callback: Callback<VisibilityChangeReason>)
```

当该NavDestination页面隐藏时触发此回调。从API version 21开始，支持通过VisibilityChangeReason说明onHidden触发的原因。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onHidden(callback: Callback<VisibilityChangeReason>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onHidden(callback: Callback<VisibilityChangeReason>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;VisibilityChangeReason&gt; | 是 | 当该NavDestination页面隐藏时触发此回调。<br/>在API version 21之前，当NavDestination页面隐藏时触发回调。<br/>从API version 21开始，该回调会提供入参VisibilityChangeReason以说明onHidden触发的原因。<br>**起始版本：** 21 |

<a id="oninactive"></a>
## onInactive

```TypeScript
onInactive(callback: Optional<Callback<NavDestinationActiveReason>>)
```

NavDestination处于非激活态（处于非栈顶不可操作，或处于栈顶时上层有特殊组件遮挡）时，触发该回调。使用示例参见[示例5](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#示例5navdestination的onactive与oninactive生命周期)。

> **说明：**

> 从API version 22开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onInactive(callback: Optional<Callback<NavDestinationActiveReason>>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onInactive(callback: Optional<Callback<NavDestinationActiveReason>>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;Callback&lt;NavDestinationActiveReason&gt;&gt; | 是 | Indicates callback when destination is inactive. |

<a id="onnewparam"></a>
## onNewParam

```TypeScript
onNewParam(callback: Optional<Callback<ESObject>>)
```

当之前存在于栈中的NavDestination页面通过[launchMode.MOVE_TO_TOP_SINGLETON](arkts-arkui-launchmode-e.md)或[launchMode.POP_TO_SINGLETON](arkts-arkui-launchmode-e.md)移动到栈顶时，触发该回调。

> **说明：**

> - [replacePath](arkts-arkui-navpathstack-c.md#replacepath-1)、  
> [replaceDestination](arkts-arkui-navpathstack-c.md#replacedestination-1)不会触发该回调。  
>  
> - 从API version 22开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onNewParam(callback: Optional<Callback<ESObject>>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onNewParam(callback: Optional<Callback<ESObject>>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;Callback&lt;ESObject&gt;&gt; | 是 | Indicates callback when destination be pushed with singleton mode. |

<a id="onready"></a>
## onReady

```TypeScript
onReady(callback: import('../api/@ohos.base').Callback<NavDestinationContext>)
```

当NavDestination即将构建子组件之前会触发此回调。

> **说明：**

> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onReady(callback: import('../api/@ohos.base').Callback<NavDestinationContext>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onReady(callback: import('../api/@ohos.base').Callback<NavDestinationContext>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').Callback&lt;NavDestinationContext&gt; | 是 | 当NavDestination即将构建子组件之前会触发此回调。 |

<a id="onrestorestate"></a>
## onRestoreState

```TypeScript
onRestoreState(callback: Optional<RestoreStateCallback>)
```

设置自定义页面状态恢复回调。

当页面重构时触发。由onSaveState保存的自定义状态将传递给此回调。如果没有保存自定义状态，则传递Null。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onRestoreState(callback: Optional<RestoreStateCallback>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onRestoreState(callback: Optional<RestoreStateCallback>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;RestoreStateCallback&gt; | 是 | 自定义状态恢复回调 |

<a id="onresult"></a>
## onResult

```TypeScript
onResult(callback: Optional<Callback<ESObject>>)
```

NavDestination返回时触发该回调。

> **说明：**

> 从API version 22开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onResult(callback: Optional<Callback<ESObject>>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onResult(callback: Optional<Callback<ESObject>>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;Callback&lt;ESObject&gt;&gt; | 是 | Indicates callback when pop to the navDestination with result. |

<a id="onsavestate"></a>
## onSaveState

```TypeScript
onSaveState(callback: Optional<SaveStateCallback>)
```

设置自定义页面状态保存回调。

当页面被隐藏时触发。保存自定义页面状态以备恢复。用于创建页面的初始参数由导航单独保留。状态对象必须是可序列化的。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onSaveState(callback: Optional<SaveStateCallback>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onSaveState(callback: Optional<SaveStateCallback>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;SaveStateCallback&gt; | 是 | 自定义状态保存回调 |

<a id="onshown"></a>
## onShown

```TypeScript
onShown(callback: Callback<VisibilityChangeReason>)
```

当该NavDestination页面显示时触发此回调。从API version 21开始，支持通过VisibilityChangeReason说明onShown触发的原因。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onShown(callback: Callback<VisibilityChangeReason>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onShown(callback: Callback<VisibilityChangeReason>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;VisibilityChangeReason&gt; | 是 | 当该NavDestination页面显示时触发此回调。<br/>在API version 21之前，当NavDestination页面显示时触发回调。<br/>从API version 21开始，回调会提供入参VisibilityChangeReason以说明onShown触发的原因。<br>**起始版本：** 21 |

<a id="onwillappear"></a>
## onWillAppear

```TypeScript
onWillAppear(callback: Callback<void>)
```

当该NavDestination挂载之前触发此回调。在该回调中允许修改路由栈，当前帧生效。

> **说明：**

> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onWillAppear(callback: Callback<void>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onWillAppear(callback: Callback<void>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 当该NavDestination挂载之前触发此回调。在该回调中允许修改路由栈，当前帧生效。 |

<a id="onwilldisappear"></a>
## onWillDisappear

```TypeScript
onWillDisappear(callback: Callback<void>)
```

当该NavDestination卸载之前触发的生命周期(有转场动画时，在转场动画开始之前触发)。

> **说明：**

> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onWillDisappear(callback: Callback<void>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onWillDisappear(callback: Callback<void>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 当该NavDestination卸载之前触发的生命周期(有转场动画时，在转场动画开始之前触发)。 |

<a id="onwillhide"></a>
## onWillHide

```TypeScript
onWillHide(callback: Callback<void>)
```

当该NavDestination隐藏之前触发此回调。

> **说明：**

> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onWillHide(callback: Callback<void>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onWillHide(callback: Callback<void>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 当该NavDestination隐藏之前触发此回调。 |

<a id="onwillshow"></a>
## onWillShow

```TypeScript
onWillShow(callback: Callback<void>)
```

当该NavDestination显示之前触发此回调。

> **说明：**

> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-onWillShow(callback: Callback<void>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-onWillShow(callback: Callback<void>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 当该NavDestination显示之前触发此回调。 |

<a id="preferredorientation"></a>
## preferredOrientation

```TypeScript
preferredOrientation(orientation: Optional<Orientation>)
```

设置NavDestination对应的显示方向。转场到该NavDestination后，系统也会将应用主窗口切到该显示方向。

> **说明：**

> - 该属性满足如下全部条件时才有效：  
> > 1. NavDestination属于应用主窗口页面，并且主窗口为全屏窗口；  
> > 2. NavDestination所属的Navigation的大小占满整个应用页面；  
> > 3. NavDestination类型为[NavDestinationMode](arkts-arkui-navdestinationmode-e.md).STANDARD。  
>  
> - 设置显示方向的实际效果依赖于具体的设备支持情况，具体参考窗口的  
> [setPreferredOrientation](docroot://reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1)接  
> 口。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-preferredOrientation(orientation: Optional<Orientation>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-preferredOrientation(orientation: Optional<Orientation>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | [Optional](arkts-arkui-optional-t.md)&lt;Orientation&gt; | 是 | NavDestination页面对应的Orientation。 |

<a id="recoverable"></a>
## recoverable

```TypeScript
recoverable(recoverable: Optional<boolean>)
```

配置NavDestination是否可恢复。如配置为可恢复，当应用进程异常退出并重新冷启动时，可自动创建该NavDestination。该功能需NavDestination对应的Navigation也配置了[可恢复属性](NavigationAttribute#recoverable)。

> **说明：**

> 该接口需要配合Navigation的[recoverable](NavigationAttribute#recoverable)接口使用。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavDestinationAttribute-recoverable(recoverable: Optional<boolean>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-recoverable(recoverable: Optional<boolean>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recoverable | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | NavDestination是否可恢复，默认为不可恢复。<br/>默认值：false<br/>true：路由栈可恢复。<br/>false：路由栈不可恢复。 |

<a id="systembarstyle"></a>
## systemBarStyle

```TypeScript
systemBarStyle(style: Optional<SystemBarStyle>)
```

当Navigation中显示当前NavDestination时，设置对应系统状态栏的样式。

> **说明：**

> - 必须配合Navigation使用，作为其Navigation目的页面的根节点时才能生效。  
>  
> - 其他使用限制请参考Navigation对应的[systemBarStyle](NavigationAttribute#systemBarStyle)属性说明。  
>  
> - 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-systemBarStyle(style: Optional<SystemBarStyle>): NavDestinationAttribute--><!--Device-NavDestinationAttribute-systemBarStyle(style: Optional<SystemBarStyle>): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;SystemBarStyle&gt; | 是 | 系统状态栏样式。 |

<a id="systemtransition"></a>
## systemTransition

```TypeScript
systemTransition(type: NavigationSystemTransitionType)
```

设置NavDestination系统转场动画，支持分别设置系统标题栏动画和内容动画。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-systemTransition(type: NavigationSystemTransitionType): NavDestinationAttribute--><!--Device-NavDestinationAttribute-systemTransition(type: NavigationSystemTransitionType): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [NavigationSystemTransitionType](arkts-arkui-navigationsystemtransitiontype-e.md) | 是 | 系统转场动画类型。<br/>默认值：NavigationSystemTransitionType.DEFAULT |

<a id="title"></a>
## title

```TypeScript
title(value: string | CustomBuilder | NavDestinationCommonTitle | NavDestinationCustomTitle | Resource,
          options?: NavigationTitleOptions)
```

设置页面标题。字符串超长时，如果不设置副标题，先缩小再换行2行后以"..."截断。如果设置副标题，先缩小后以"..."截断。

> **说明：**

> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-title(value: string | CustomBuilder | NavDestinationCommonTitle | NavDestinationCustomTitle | Resource,
          options?: NavigationTitleOptions): NavDestinationAttribute--><!--Device-NavDestinationAttribute-title(value: string | CustomBuilder | NavDestinationCommonTitle | NavDestinationCustomTitle | Resource,
          options?: NavigationTitleOptions): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| CustomBuilder \| NavDestinationCommonTitle \| NavDestinationCustomTitle \| Resource | 是 | 页面标题。<br>**起始版本：** 9 - 13 |
| options | [NavigationTitleOptions](arkts-arkui-navigationtitleoptions-i.md) | 否 | Title bar options.<br>**起始版本：** 12 |

<a id="toolbarconfiguration"></a>
## toolbarConfiguration

```TypeScript
toolbarConfiguration(toolbarParam: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions)
```

设置工具栏内容。未调用本接口时不显示工具栏。

> **说明：**

> - 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。  
>  
> - 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-NavDestinationAttribute-toolbarConfiguration(toolbarParam: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions): NavDestinationAttribute--><!--Device-NavDestinationAttribute-toolbarConfiguration(toolbarParam: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions): NavDestinationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toolbarParam | Array&lt;ToolbarItem&gt; \| CustomBuilder | 是 | 工具栏内容。<br/>使用Array<[ToolbarItem](arkts-arkui-toolbaritem-i.md)>写法设置的工具栏有如下特性：<br/>-工具栏所有选项均分底部工具栏，在每个均分内容区布局文本和图标。<br/>-竖屏模式最多支持显示5个图标，多余的图标会被放入自动生成的更多图标中，点击更多图标，可以展示剩余内容。横屏模式时，如果为[Split](arkts-arkui-navigationmode-e.md)模式，仍按照竖屏模式显示，如果为[Stack](arkts-arkui-navigationmode-e.md)模式需配合[menus](NavDestinationAttribute#menus(value: Array<NavigationMenuItem> \| CustomBuilder))属性的Array<[NavigationMenuItem](arkts-arkui-navigationmenuitem-i.md)>使用，底部工具栏会自动隐藏，同时底部工具栏所有选项移动至页面右上角菜单。<br/>使用[CustomBuilder](docroot://reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8)写法为用户自定义工具栏选项，不具备以上功能。 |
| options | [NavigationToolbarOptions](arkts-arkui-navigationtoolbaroptions-i.md) | 否 | 工具栏选项。包含工具栏背景颜色、工具栏背景模糊样式及模糊选项、工具栏背景属性、工具栏布局方式、是否隐藏工具栏的文本、工具栏更多图标的菜单选项。 |

