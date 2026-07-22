# Navigation属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** NavigationAttribute extends [CommonMethod<NavigationAttribute>](CommonMethod<NavigationAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class NavigationAttribute extends CommonMethod<NavigationAttribute>--><!--Device-unnamed-declare class NavigationAttribute extends CommonMethod<NavigationAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backButtonIcon

```TypeScript
backButtonIcon(value: string | PixelMap | Resource | SymbolGlyphModifier)
```

设置标题栏中返回键图标。
> **说明：**  
>  
> 不支持通过[SymbolGlyphModifier](arkts-arkui-symbolglyphmodifier-t.md)对象的  
> [fontSize](SymbolGlyphAttribute#fontSize)属性修改图标大小、  
> [effectStrategy](SymbolGlyphAttribute#effectStrategy)属性修改动效、  
> [symbolEffect](SymbolGlyphAttribute#symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean))属性修改动效类型。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-backButtonIcon(value: string | PixelMap | Resource | SymbolGlyphModifier): NavigationAttribute--><!--Device-NavigationAttribute-backButtonIcon(value: string | PixelMap | Resource | SymbolGlyphModifier): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| PixelMap \| Resource \| SymbolGlyphModifier | 是 | 标题栏中返回键图标。<br>**起始版本：** 9 - 11 |

## backButtonIcon

```TypeScript
backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier, accessibilityText?: ResourceStr)
```

设置标题栏中返回键图标和无障碍播报内容。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。  
>  
> 不支持通过[SymbolGlyphModifier](arkts-arkui-symbolglyphmodifier-t.md)对象的  
> [fontSize](SymbolGlyphAttribute#fontSize)属性修改图标大小、  
> [effectStrategy](SymbolGlyphAttribute#effectStrategy)属性修改动效、  
> [symbolEffect](SymbolGlyphAttribute#symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean))属性修改动效类型。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier, accessibilityText?: ResourceStr): NavigationAttribute--><!--Device-NavigationAttribute-backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier, accessibilityText?: ResourceStr): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | string \| PixelMap \| Resource \| SymbolGlyphModifier | 是 | 标题栏中返回键图标。 |
| accessibilityText | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 否 | 返回键无障碍播报内容。</br>默认值：系统语言是中文时为“返回”，系统语言是英文时为“back”。 |

## configuration

```TypeScript
configuration(config: NavigationConfiguration)
```

设置导航配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-configuration(config: NavigationConfiguration): NavigationAttribute--><!--Device-NavigationAttribute-configuration(config: NavigationConfiguration): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [NavigationConfiguration](arkts-arkui-navigationconfiguration-i.md) | 是 | 导航配置选项。 |

## customNavContentTransition

```TypeScript
customNavContentTransition(delegate: (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation)
    => NavigationAnimatedTransition | undefined)
```

自定义转场动画回调。
> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-customNavContentTransition(delegate: (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation)    => NavigationAnimatedTransition | undefined): NavigationAttribute--><!--Device-NavigationAttribute-customNavContentTransition(delegate: (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation)    => NavigationAnimatedTransition | undefined): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation)     =&gt; NavigationAnimatedTransition \| undefined | 是 | 自定义转场动画回调。<br/>from：退场Destination的页面。<br/>to：进场Destination的页面。operation：转场类型。 <br/>返回NavigationAnimatedTransition时，表示自定义转场动画协议。<br/>undefined: 返回未定义，执行默认转场动效。 |

## divider

```TypeScript
divider(style: NavigationDividerStyle | null)
```

设置Navigation双栏模式下的分割线样式。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-divider(style: NavigationDividerStyle | null): NavigationAttribute--><!--Device-NavigationAttribute-divider(style: NavigationDividerStyle | null): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [NavigationDividerStyle](arkts-arkui-navigationdividerstyle-i.md) \| null | 是 | 设置双栏分割线样式。<br> - null：隐藏分割线。 |

## enableDragBar

```TypeScript
enableDragBar(isEnabled: Optional<boolean>)
```

控制分栏场景下是否显示拖拽条。该属性在PC/2in1设备上不生效。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-enableDragBar(isEnabled: Optional<boolean>): NavigationAttribute--><!--Device-NavigationAttribute-enableDragBar(isEnabled: Optional<boolean>): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启拖拽条，默认为无拖拽条样式。<br/>true：有拖拽条样式；false：无拖拽条样式。<br/>传入参数非法时，按false处理。 |

## enableModeChangeAnimation

```TypeScript
enableModeChangeAnimation(isEnabled: Optional<boolean>)
```

控制是否开启单双栏切换时的动效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-enableModeChangeAnimation(isEnabled: Optional<boolean>): NavigationAttribute--><!--Device-NavigationAttribute-enableModeChangeAnimation(isEnabled: Optional<boolean>): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启单双栏切换动效。<br/>true：开启单双栏切换动效；false：关闭单双栏切换动效。<br/>传入参数非法时，按true处理。 |

## enableToolBarAdaptation

```TypeScript
enableToolBarAdaptation(enable: Optional<boolean>)
```

设置是否启用Navigation和NavDestination的工具栏[toolbarConfiguration](NavigationAttribute#toolbarConfiguration)自适应能力。关闭此能力后，底部工具栏[toolbarConfiguration](NavigationAttribute#toolbarConfiguration)将不会再移动至页面右上角的菜单中。该接口不适配于自定义菜单，使用该接口需采用[NavigationMenuItem](arkts-arkui-navigationmenuitem-i.md)接口来定义[菜单](NavigationAttribute#menus(value: Array<NavigationMenuItem> | CustomBuilder))。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-enableToolBarAdaptation(enable: Optional<boolean>): NavigationAttribute--><!--Device-NavigationAttribute-enableToolBarAdaptation(enable: Optional<boolean>): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否启用Navigation和NavDestination的工具栏自适应能力。<br/>默认值：true<br/>true：启用Navigation和NavDestination的工具栏自适应能力。<br/>false：不启用Navigation和NavDestination的工具栏自适应能力。 |

## enableVisibilityLifecycleWithContentCover

```TypeScript
enableVisibilityLifecycleWithContentCover(isEnabled: Optional<boolean>)
```

设置是否启用[NavDestination](arkts-arkui-navdestination.md)页面[onHidden](NavDestinationAttribute#onHidden)、[onShown](NavDestinationAttribute#onShown)生命周期与全模态的联动触发。
> **说明：**  
>  
> 从API version 23开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-enableVisibilityLifecycleWithContentCover(isEnabled: Optional<boolean>): NavigationAttribute--><!--Device-NavigationAttribute-enableVisibilityLifecycleWithContentCover(isEnabled: Optional<boolean>): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否启用NavDestination页面onShown、onHidden生命周期与全模态的联动触发。<br/>默认值：true<br/>true：全模态拉起时，会触发当前NavDestination页面的onHidden生命周期；全模态关闭时会触发当前NavDestination页面的onShown生命周期<br/>false：NavDestination页面onHidden、onShown生命周期不会因为全模态的拉起、关闭而触发。 |

## hideBackButton

```TypeScript
hideBackButton(value: boolean)
```

设置是否隐藏标题栏中的返回键。返回键仅在[titleMode](NavigationAttribute#titleMode)设置为NavigationTitleMode.Mini时才生效。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-hideBackButton(value: boolean): NavigationAttribute--><!--Device-NavigationAttribute-hideBackButton(value: boolean): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否隐藏标题栏中的返回键。<br/>true：隐藏返回键。<br/>false：显示返回键。<br/>传入参数非法时，按false处理。 |

## hideNavBar

```TypeScript
hideNavBar(value: boolean)
```

设置是否隐藏导航页。设置为true时，隐藏Navigation的导航页，包括标题栏、内容区和工具栏。如果此时路由栈中存在NavDestination页面，则直接显示栈顶NavDestination页面，反之显示空白。

从API version 9开始到API version 10仅在双栏模式下生效。从API version 11开始在单栏、双栏与自适应模式均生效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-hideNavBar(value: boolean): NavigationAttribute--><!--Device-NavigationAttribute-hideNavBar(value: boolean): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否隐藏导航页。<br>默认值：false<br/>true：隐藏导航页；false：显示导航页。<br/>传入参数非法时，按false处理。 |

## hideTitleBar

```TypeScript
hideTitleBar(value: boolean)
```

设置是否隐藏标题栏。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-hideTitleBar(value: boolean): NavigationAttribute--><!--Device-NavigationAttribute-hideTitleBar(value: boolean): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否隐藏标题栏。<br>默认值：false<br/>true：隐藏标题栏；false：显示标题栏。<br/>传入参数非法时，按false处理。 |

## hideTitleBar

```TypeScript
hideTitleBar(hide: boolean, animated: boolean)
```

设置是否隐藏标题栏。与[hideTitleBar](NavigationAttribute#hideTitleBar(value: boolean))相比，新增标题栏显隐时是否使用动画。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-hideTitleBar(hide: boolean, animated: boolean): NavigationAttribute--><!--Device-NavigationAttribute-hideTitleBar(hide: boolean, animated: boolean): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean | 是 | 是否隐藏标题栏。<br>默认值：false<br/>true：隐藏标题栏；false：显示标题栏。<br/>传入参数非法时，按false处理。 |
| animated | boolean | 是 | 设置是否使用动画显隐标题栏。<br>默认值：false<br/>true：使用动画显示隐藏标题栏；false：不使用动画显示隐藏标题栏。<br/>传入参数非法时，按false处理。 |

## hideToolBar

```TypeScript
hideToolBar(value: boolean)
```

设置是否隐藏工具栏。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-hideToolBar(value: boolean): NavigationAttribute--><!--Device-NavigationAttribute-hideToolBar(value: boolean): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否隐藏工具栏。<br>默认值：false<br/>true：隐藏工具栏；false：显示工具栏。<br/>传入参数非法时，按false处理。 |

## hideToolBar

```TypeScript
hideToolBar(hide: boolean, animated: boolean)
```

设置是否隐藏工具栏。与[hideToolBar](NavigationAttribute#hideToolBar(value: boolean))相比，新增工具栏显隐时是否使用动画。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-hideToolBar(hide: boolean, animated: boolean): NavigationAttribute--><!--Device-NavigationAttribute-hideToolBar(hide: boolean, animated: boolean): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean | 是 | 是否隐藏工具栏。<br>默认值：false<br/>true：隐藏工具栏；false：显示工具栏。<br/>传入参数非法时，按false处理。 |
| animated | boolean | 是 | 设置是否使用动画显隐工具栏。<br>默认值：false<br/>true：使用动画显示隐藏工具栏；false：不使用动画显示隐藏工具栏。<br/>传入参数非法时，按false处理。 |

## ignoreLayoutSafeArea

```TypeScript
ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>)
```

控制组件的布局，使其扩展到非安全区域。
> **说明：**  
>  
> - 组件设置ignoreLayoutSafeArea之后生效的条件为：  
> > 设置LayoutSafeAreaType.SYSTEM时，组件的边界与非安全区域重合时组件能够延伸到非安全区域下。  
>  
> - 若组件扩展到非安全区域内，此时在非安全区域里触发的事件（例如：点击事件）等可能会被系统拦截，优先响应状态栏等系统组件。  
>  
> - 组件想要扩展到非安全区域内，需隐藏或者设置标题栏和工具栏为[STACK](arkts-arkui-barstyle-e.md)模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>): NavigationAttribute--><!--Device-NavigationAttribute-ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;LayoutSafeAreaType&gt; | 否 | 配置扩展安全区域的类型。<br />默认值：<br />[LayoutSafeAreaType.SYSTEM] |
| edges | Array&lt;LayoutSafeAreaEdge&gt; | 否 | 配置扩展安全区域的方向。<br /> 默认值：<br />[LayoutSafeAreaEdge.TOP, LayoutSafeAreaEdge.BOTTOM]。 |

## menus

```TypeScript
menus(value: Array<NavigationMenuItem> | CustomBuilder)
```

设置页面右上角菜单。不设置时不显示菜单项。使用Array<[NavigationMenuItem](arkts-arkui-navigationmenuitem-i.md)&gt; 写法时，竖屏最多支持显示3个图标，横屏最多支持显示5个图标，多余的图标会被放入自动生成的更多图标。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-menus(value: Array<NavigationMenuItem> | CustomBuilder): NavigationAttribute--><!--Device-NavigationAttribute-menus(value: Array<NavigationMenuItem> | CustomBuilder): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;NavigationMenuItem&gt; \| CustomBuilder | 是 | 页面右上角菜单。 |

## menus

```TypeScript
menus(items: Array<NavigationMenuItem> | CustomBuilder, options?: NavigationMenuOptions)
```

设置页面右上角菜单。不设置时不显示菜单项。与[menus](NavigationAttribute#menus(value: Array<NavigationMenuItem> | CustomBuilder))相比，新增菜单选项。使用Array<[NavigationMenuItem](arkts-arkui-navigationmenuitem-i.md)&gt; 写法时，竖屏最多支持显示3个图标，横屏最多支持显示5个图标，多余的图标会被放入自动生成的更多图标。
> **说明：**  
>  
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-menus(items: Array<NavigationMenuItem> | CustomBuilder, options?: NavigationMenuOptions): NavigationAttribute--><!--Device-NavigationAttribute-menus(items: Array<NavigationMenuItem> | CustomBuilder, options?: NavigationMenuOptions): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;NavigationMenuItem&gt; \| CustomBuilder | 是 | 页面右上角菜单。 |
| options | [NavigationMenuOptions](arkts-arkui-navigationmenuoptions-i.md) | 否 | 页面右上角菜单选项。 |

## minContentWidth

```TypeScript
minContentWidth(value: Dimension)
```

设置导航页内容区最小宽度（双栏模式下生效）。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-minContentWidth(value: Dimension): NavigationAttribute--><!--Device-NavigationAttribute-minContentWidth(value: Dimension): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | 导航页内容区最小宽度。<br/>默认值：360<br/>单位：vp<br/>undefined：行为不做处理，导航页内容区最小宽度与默认值保持一致。<br/>Auto模式断点计算：默认600vp，minNavBarWidth(240vp) + minContentWidth (360vp) |

## mode

```TypeScript
mode(value: NavigationMode)
```

设置导航页的显示模式，支持单栏（Stack）、分栏（Split）和自适应（Auto）。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-mode(value: NavigationMode): NavigationAttribute--><!--Device-NavigationAttribute-mode(value: NavigationMode): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NavigationMode](arkts-arkui-navigationmode-e.md) | 是 | 导航页的显示模式。<br/>默认值：NavigationMode.Auto<br/>自适应：基于组件宽度自适应单栏和双栏。 |

## navBarPosition

```TypeScript
navBarPosition(value: NavBarPosition)
```

设置导航页位置。仅在[mode](NavigationAttribute#mode)设置为NavigationMode.Auto或NavigationMode.Split时生效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-navBarPosition(value: NavBarPosition): NavigationAttribute--><!--Device-NavigationAttribute-navBarPosition(value: NavBarPosition): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NavBarPosition](arkts-arkui-navbarposition-e.md) | 是 | 导航页位置。<br/>默认值：NavBarPosition.Start |

## navBarWidth

```TypeScript
navBarWidth(value: Length)
```

设置导航页宽度。仅在[mode](NavigationAttribute#mode)设置为NavigationMode.Auto或NavigationMode.Split时生效。

从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md)双向绑定变量。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-navBarWidth(value: Length): NavigationAttribute--><!--Device-NavigationAttribute-navBarWidth(value: Length): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 导航页宽度。<br/>默认值：240<br/>单位：vp<br/>undefined：行为不做处理，导航页宽度与默认值保持一致。 |

## navBarWidthRange

```TypeScript
navBarWidthRange(value: [Dimension, Dimension])
```

设置导航页最小和最大宽度（双栏模式下生效）。未设置该接口时，最小宽度默认为240vp，最大宽度默认为组件宽度的40%，且不大于432vp，即导航页和内容区之间的分割线可以在此范围内进行拖拽。拖拽分割线使导航页宽度变化时，内容区的内容会被压缩。

分割线的拖拽范围：

| 条件| 拖拽范围 |  
| ----| ----------- |  
|navBarWidthRange和minContentWidth同时设置 | 满足minContentWidth所设置的值后，在navBarWidthRange所设置的范围内进行拖拽 |  
|navBarWidthRange和minContentWidth均不设置 | 在navBarWidthRange默认的最小和最大范围内进行拖拽 |  
|仅设置navBarWidthRange属性 | 在navBarWidthRange所设置的范围内进行拖拽，最大拖拽范围不能超过minContentWidth的默认值 |  
|仅设置minContentWidth属性 | 在navBarWidthRange默认的最小和最大范围内进行拖拽 |  
|仅设置navBarWidth属性 | 不支持拖拽 |

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-navBarWidthRange(value: [Dimension, Dimension]): NavigationAttribute--><!--Device-NavigationAttribute-navBarWidthRange(value: [Dimension, Dimension]): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension, Dimension] | 是 | 导航页最小和最大宽度。设置异常值时按默认值处理。 |

## navDestination

```TypeScript
navDestination(builder: (name: string, param: unknown) => void)
```

创建NavDestination组件。使用builder函数，基于name和param构造NavDestination组件。builder下只能有一个根节点。builder中允许在NavDestination组件外包含一层自定义组件， 但自定义组件不允许设置属性和事件，否则仅显示空白。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-navDestination(builder: (name: string, param: unknown) => void): NavigationAttribute--><!--Device-NavigationAttribute-navDestination(builder: (name: string, param: unknown) => void): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | (name: string, param: unknown) =&gt; void | 是 | 创建NavDestination组件。name：NavDestination页面名称。param：开发者设置的NavDestination页面详细参数，unknown可以是用户自定义的类型。 |

## onNavBarStateChange

```TypeScript
onNavBarStateChange(callback: (isVisible: boolean) => void)
```

导航页显示状态切换时触发该回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-onNavBarStateChange(callback: (isVisible: boolean) => void): NavigationAttribute--><!--Device-NavigationAttribute-onNavBarStateChange(callback: (isVisible: boolean) => void): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (isVisible: boolean) =&gt; void | 是 | isVisible为true时表示显示，为false时表示隐藏。<br>**起始版本：** 10 |

## onNavigationModeChange

```TypeScript
onNavigationModeChange(callback: (mode: NavigationMode) => void)
```

当Navigation首次显示或者单双栏状态发生变化时触发该回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-onNavigationModeChange(callback: (mode: NavigationMode) => void): NavigationAttribute--><!--Device-NavigationAttribute-onNavigationModeChange(callback: (mode: NavigationMode) => void): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (mode: NavigationMode) =&gt; void | 是 | NavigationMode.Split：当前Navigation显示为双栏;<br/>NavigationMode.Stack：当前Navigation显示为单栏。 |

## onTitleModeChange

```TypeScript
onTitleModeChange(callback: (titleMode: NavigationTitleMode) => void)
```

当[titleMode](NavigationAttribute#titleMode)为NavigationTitleMode.Free时，随着可滚动组件的滑动标题栏模式发生变化时触发此回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-onTitleModeChange(callback: (titleMode: NavigationTitleMode) => void): NavigationAttribute--><!--Device-NavigationAttribute-onTitleModeChange(callback: (titleMode: NavigationTitleMode) => void): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (titleMode: NavigationTitleMode) =&gt; void | 是 | 标题模式。<br>**起始版本：** 10 |

## recoverable

```TypeScript
recoverable(recoverable: Optional<boolean>)
```

配置Navigation是否可恢复。如配置为可恢复，当应用进程异常退出并重新冷启动时，可自动创建该Navigation，并恢复至异常退出时的路由栈。
> **说明：**  
>  
> 1. 使用该接口需要先设置Navigation的通用属性[id](arkts-arkui-commonmethod-c.md#id)，否则该接口无效。  
>  
> 2. 该接口需要配合NavDestination的[recoverable](NavDestinationAttribute#recoverable)接口使用。  
>  
> 3. 恢复的过程中不可序列化的信息，例如不可序列化的参数与用户设置的onPop等，会被丢弃，无法恢复。  
>  
> 4. 当应用退到后台，因系统资源不足等原因被系统终止后，如果某页面已配置为可恢复，当应用再次被唤醒至前台时，系统将自动恢复该页面。详细说明请参考  
> [UIAbility备份恢复](../../../application-models/ability-recover-guideline.md)，详细使用请参考  
> [示例18](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例18设置navigation可恢复)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-recoverable(recoverable: Optional<boolean>): NavigationAttribute--><!--Device-NavigationAttribute-recoverable(recoverable: Optional<boolean>): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recoverable | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | Navigation是否可恢复，默认为不可恢复。<br/>true：路由栈可恢复；false：路由栈不可恢复。<br/>传入参数非法时，按false处理。 |

## splitPlaceholder

```TypeScript
splitPlaceholder(placeholder: ComponentContent)
```

Navigation双栏模式下，支持设置右侧页面显示默认占位页，占位页仅作为UI展示页，不可获焦和响应事件。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-splitPlaceholder(placeholder: ComponentContent): NavigationAttribute--><!--Device-NavigationAttribute-splitPlaceholder(placeholder: ComponentContent): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| placeholder | [ComponentContent](../arkts-apis/arkts-arkui-componentcontent-c.md) | 是 | 设置Navigation双栏模式下右侧的默认占位页。 |

## subTitle

```TypeScript
subTitle(value: string)
```

设置页面副标题。
> **说明：**

**起始版本：** 8

**废弃版本：** 9

**替代接口：** title

<!--Device-NavigationAttribute-subTitle(value: string): NavigationAttribute--><!--Device-NavigationAttribute-subTitle(value: string): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 页面副标题。 |

## systemBarStyle

```TypeScript
systemBarStyle(style: Optional<SystemBarStyle>)
```

当Navigation中显示Navigation首页时，设置对应系统状态栏的样式。
> **说明：**  
>  
> 1. 不建议混合使用systemBarStyle属性和window设置状态栏样式的相关接口，例如：  
> [setWindowSystemBarProperties](../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowsystembarproperties9)。  
>  
>  
> 2. 初次设置Navigation/NavDestination的systemBarStyle属性时，会备份当前状态栏样式用于后续的恢复场景。  
>  
> 3. Navigation总是以首页（路由栈内没有NavDestination时）或者栈顶NavDestination设置的状态栏样式为准。  
>  
> 4. Navigation首页或者任何栈顶NavDestination页面，如果设置了有效的systemBarStyle，则会使用设置的样式，反之如果之前已经备份了样式，则使用备份的样式，否则不做任何处理。  
>  
> 5. [Split](arkts-arkui-navigationmode-e.md)模式下的Navigation，如果内容区没有NavDestination，则遵从Navigation首页的设置，反之则遵从栈顶NavDestination的设置。  
>  
>  
> 6. 仅支持在主窗口的主页面中使用systemBarStyle设置状态栏样式。  
>  
> 7. 仅当Navigation占满整个页面时，设置的样式才会生效，当Navigation没有占满整个页面时，如果有备份的样式，则恢复备份的样式。  
>  
> 8. 当页面设置不同样式时，在页面转场开始时生效。  
>  
> 9. 非全屏窗口下，Navigation/NavDestination设置的状态栏不生效。  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-systemBarStyle(style: Optional<SystemBarStyle>): NavigationAttribute--><!--Device-NavigationAttribute-systemBarStyle(style: Optional<SystemBarStyle>): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;SystemBarStyle&gt; | 是 | 系统状态栏样式。 |

## title

```TypeScript
title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle, options?: NavigationTitleOptions)
```

设置页面标题。
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle, options?: NavigationTitleOptions): NavigationAttribute--><!--Device-NavigationAttribute-title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle, options?: NavigationTitleOptions): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| CustomBuilder \| NavigationCommonTitle \| NavigationCustomTitle | 是 | 页面标题，使用NavigationCustomTitle类型设置height高度时，[titleMode](NavigationAttribute#titleMode)属性不会生效。<br/>字符串超长时，如果不设置副标题，先缩小再换行（2行）最后截断。如果设置副标题，先缩小最后截断。<br>**起始版本：** 10 |
| options | [NavigationTitleOptions](arkts-arkui-navigationtitleoptions-i.md) | 否 | 标题栏选项。 包含标题栏背景颜色、标题栏背景模糊样式及模糊选项、标题栏背景属性、标题栏布局方式、标题栏起始端内间距、标题栏结束端内间距、主标题属性修改器、子标题属性修改器、是否响应悬停态。<br>**起始版本：** 11 |

## titleMode

```TypeScript
titleMode(value: NavigationTitleMode)
```

设置页面标题栏显示模式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-titleMode(value: NavigationTitleMode): NavigationAttribute--><!--Device-NavigationAttribute-titleMode(value: NavigationTitleMode): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NavigationTitleMode](arkts-arkui-navigationtitlemode-e.md) | 是 | 页面标题栏显示模式。<br/>默认值：NavigationTitleMode.Free |

## toolBar

```TypeScript
toolBar(value: object | CustomBuilder)
```

设置工具栏内容。不设置时不显示工具栏。items均分底部工具栏，在每个均分内容区布局文本和图标，文本超长时，逐级缩小，缩小之后换行，最后截断。

**object类型说明：**

| 名称 | 类型 | 必填 | 说明 |  
| ------ | ------------- | ---- | --------------- |  
| value | string | 是 | 工具栏单个选项的显示文本。 |  
| icon | string | 否 | 工具栏单个选项的图标资源路径。 |  
| action | () =&gt; void | 否 | 当前选项被选中的事件回调。 |

**起始版本：** 8

**废弃版本：** 10

**替代接口：** toolbarConfiguration

<!--Device-NavigationAttribute-toolBar(value: object | CustomBuilder): NavigationAttribute--><!--Device-NavigationAttribute-toolBar(value: object | CustomBuilder): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | object \| CustomBuilder | 是 | 工具栏内容。 |

## toolbarConfiguration

```TypeScript
toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions)
```

设置工具栏内容。不设置时不显示工具栏。
> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationAttribute-toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions): NavigationAttribute--><!--Device-NavigationAttribute-toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;ToolbarItem&gt; \| CustomBuilder | 是 | 工具栏内容，使用Array&lt;[ToolbarItem](arkts-arkui-toolbaritem-i.md)&gt;设置的工具栏有如下特性：<br/>工具栏所有选项均分底部工具栏，在每个均分内容区布局文本和图标。<br/>竖屏模式最多支持显示5个图标，多余的图标会被放入自动生成的更多图标。横屏模式时，如果为[Split](arkts-arkui-navigationmode-e.md)模式，仍按照竖屏模式显示，如果为[Stack](arkts-arkui-navigationmode-e.md)模式需配合menus属性的Array&lt;[NavigationMenuItem](arkts-arkui-navigationmenuitem-i.md)&gt;使用，底部工具栏会自动隐藏，同时底部工具栏所有选项移动至页面右上角菜单。<br/>使用[CustomBuilder](../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8)写法为用户自定义工具栏选项，不具备以上功能。 |
| options | [NavigationToolbarOptions](arkts-arkui-navigationtoolbaroptions-i.md) | 否 | 工具栏选项。 包含工具栏背景颜色、工具栏背景模糊样式及模糊选项、工具栏背景属性、工具栏布局方式、是否隐藏工具栏的文本、工具栏更多图标的菜单选项。<br>**起始版本：** 11 |

