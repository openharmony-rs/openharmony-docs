# Tabs properties/events

```TypeScript
declare class TabsAttribute extends CommonMethod<TabsAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** TabsAttribute extends CommonMethod&lt;TabsAttribute&gt;

**Since:** 7

<!--Device-unnamed-declare class TabsAttribute extends CommonMethod<TabsAttribute>--><!--Device-unnamed-declare class TabsAttribute extends CommonMethod<TabsAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## animationCurve

```TypeScript
animationCurve(curve: Curve | ICurve)
```

Sets the animation curve for page turning of the **Tabs**. For common curves, see Curve. You can also create a custom interpolation curve object through the APIs provided by the [interpolation calculation](../arkts-apis/arkts-arkui-curves.md) module.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TabsAttribute-animationCurve(curve: Curve | ICurve): TabsAttribute--><!--Device-TabsAttribute-animationCurve(curve: Curve | ICurve): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| curve | Curve &#124; ICurve | Yes | Animation curve for page turning of the **Tabs**.<br>Default value:<br>When a **TabContent** is swiped to turn pages, the default value is **interpolatingSpring(-1, 1, 228, 30)**.<br>When a tab bar tab is tapped or the **changeIndex** API of **TabsController** is called to turn pages, the default value is **cubicBezierCurve(0.2, 0.0, 0.1, 1.0)**.<br>When a custom animation curve is set, the set animation curve is used for both swiping to turn pages and tapping a tab or calling **changeIndex** to turn pages. |

## animationDuration

```TypeScript
animationDuration(value: number)
```

Sets the duration of the page switching animation for **Tabs**.

When animationCurve is not set, the duration of the page switching animation curve interpolatingSpring(-1, 1, 228, 30) for swiping **TabContent** is affected only by the curve's own parameters. Therefore, animationDuration can only control the animation duration for switching **TabContent** by tapping the tab bar tab or calling the **changeIndex** API of **TabsController**.

For curves not controlled by animationDuration, see the [Interpolation calculation](../arkts-apis/arkts-arkui-curves.md) module, such as [springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md), [responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md), and [interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-animationDuration(value: number): TabsAttribute--><!--Device-TabsAttribute-animationDuration(value: number): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Animation duration for page switching of **Tabs**.<br>Default value:<br>Since API version 10, when this attribute is not set or is set to null, the default value is 0, that is, no animation is applied to page switching of **Tabs**. When it is set to a value less than 0 or undefined, the default value is 300.<br>Since API version 11, when this attribute is not set or is set to an abnormal value, and tab bar is set to the BottomTabBarStyle style, the default value is 0. When tab bar is set to another style, the default value is 300.<br>Unit: ms<br>Value range: [0, +∞) |

## animationMode

```TypeScript
animationMode(mode: Optional<AnimationMode>)
```

Sets the animation form for switching **TabContent** when a tab bar tab is tapped or the **changeIndex** API of **TabsController** is called.

> **NOTE:** 
> 
> This attribute cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAttribute-animationMode(mode: Optional<AnimationMode>): TabsAttribute--><!--Device-TabsAttribute-animationMode(mode: Optional<AnimationMode>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[AnimationMode](arkts-arkui-tabs-comp-animationmode-e.md)&gt; | Yes | Animation form for switching **TabContent** when a tab bar tab is tapped or the **changeIndex** API of **TabsController** is called.<br>Default value: **AnimationMode.CONTENT_FIRST**, which means that when a tab bar tab is tapped or the **changeIndex** API of **TabsController** is called to switch TabContent, the content of the target page is loaded first, and then the switching animation starts. |

<a id="barbackgroundblurstyle1"></a>

## barBackgroundBlurStyle

```TypeScript
barBackgroundBlurStyle(value: BlurStyle)
```

Sets the background blur material of the tab bar. This is applicable to scenarios where a blur background effect needs to be added to the tab bar.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barBackgroundBlurStyle(value: BlurStyle): TabsAttribute--><!--Device-TabsAttribute-barBackgroundBlurStyle(value: BlurStyle): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md) | Yes | Background blur material of the tab bar.<br>Default value: **BlurStyle.NONE** |

<a id="barbackgroundblurstyle2"></a>

## barBackgroundBlurStyle

```TypeScript
barBackgroundBlurStyle(style: BlurStyle, options: BackgroundBlurStyleOptions)
```

Sets the background blur capability of the tab bar, encapsulating different blur radii, mask colors, mask opacity, saturation, and brightness through enum values.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabsAttribute-barBackgroundBlurStyle(style: BlurStyle, options: BackgroundBlurStyleOptions): TabsAttribute--><!--Device-TabsAttribute-barBackgroundBlurStyle(style: BlurStyle, options: BackgroundBlurStyleOptions): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [BlurStyle](arkts-arkui-common-comp-blurstyle-e.md) | Yes | Background blur style. The blur style encapsulates five parameters: blur radius, mask color, mask opacity, saturation, and brightness. |
| options | [BackgroundBlurStyleOptions](arkts-arkui-common-comp-backgroundblurstyleoptions-i.md) | Yes | Background blur options, used to customize the blur effect. |

## barBackgroundColor

```TypeScript
barBackgroundColor(value: ResourceColor)
```

Sets the background color of the tab bar.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barBackgroundColor(value: ResourceColor): TabsAttribute--><!--Device-TabsAttribute-barBackgroundColor(value: ResourceColor): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Background color of the tab bar.<br>**Note:** <br>It is recommended to use this attribute together with [fadingEdge](#fadingedge) to avoid the white fade effect at the end of the tab.<br>Default value: **Color.Transparent**, transparent |

## barBackgroundEffect

```TypeScript
barBackgroundEffect(options: BackgroundEffectOptions)
```

Sets the background attributes of the tab bar, including the background blur radius, brightness, saturation, and color. This is applicable to scenarios where fine-grained control over the tab bar background visual effect is required.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabsAttribute-barBackgroundEffect(options: BackgroundEffectOptions): TabsAttribute--><!--Device-TabsAttribute-barBackgroundEffect(options: BackgroundEffectOptions): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [BackgroundEffectOptions](arkts-arkui-common-comp-backgroundeffectoptions-i.md) | Yes | Sets the background attributes of the tab bar, including the blur radius, brightness, saturation, and color. |

## barDisplayModeBreakpoint

```TypeScript
barDisplayModeBreakpoint(style: Optional<TabsBreakpointType<TabBarDisplayMode>>)
```

Sets the display mode of the tab bar for different Tabs container sizes.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-barDisplayModeBreakpoint(style: Optional<TabsBreakpointType<TabBarDisplayMode>>): TabsAttribute--><!--Device-TabsAttribute-barDisplayModeBreakpoint(style: Optional<TabsBreakpointType<TabBarDisplayMode>>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TabsBreakpointType](arkts-arkui-tabs-comp-tabsbreakpointtype-i.md)&lt;[TabBarDisplayMode](arkts-arkui-tabs-comp-tabbardisplaymode-e.md)&gt;&gt; | Yes | Display mode of the tab bar for different Tabs container sizes. |

## barFloatingStyle

```TypeScript
barFloatingStyle(style: Optional<FloatingTabBarStyle>)
```

Sets the floating style of the tab bar.

> **NOTE:** 
> 
> The floating style allows the tab bar to be displayed in a floating manner at the bottom of the **Tabs**. This
> API takes effect only when [barOverlap](#baroverlap) is **true**,
> [vertical](#vertical) is **false**, and [barPosition](#barposition) is
> **BarPosition.End**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TabsAttribute-barFloatingStyle(style: Optional<FloatingTabBarStyle>): TabsAttribute--><!--Device-TabsAttribute-barFloatingStyle(style: Optional<FloatingTabBarStyle>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[FloatingTabBarStyle](arkts-arkui-tabs-comp-floatingtabbarstyle-i.md)&gt; | Yes | Floating style configuration of the tab bar.<br>When set to **undefined**, the floating style is canceled and the default style is restored. |

## barGridAlign

```TypeScript
barGridAlign(value: BarGridColumnOptions)
```

Sets the visible area of the tab bar in a grid-based manner. For details, see BarGridColumnOptions. This attribute is valid only in horizontal mode and is not applicable to XS, XL, and XXL devices (see [Grid Container Breakpoints](../../../ui/arkts-layout-development-grid-layout.md#breakpoints)).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barGridAlign(value: BarGridColumnOptions): TabsAttribute--><!--Device-TabsAttribute-barGridAlign(value: BarGridColumnOptions): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BarGridColumnOptions](arkts-arkui-tabs-comp-bargridcolumnoptions-i.md) | Yes | Sets the visible area of the tab bar in a grid-based manner. |

<a id="barheight1"></a>

## barHeight

```TypeScript
barHeight(value: Length)
```

Sets the height value of the tab bar. For a horizontal **Tabs**, height can be set to 'auto' so that the tab bar adaptively fits the child component height. If height is set to a value less than 0 or greater than the **Tabs** height, it is displayed by default value.

In versions earlier than API version 14, if **barHeight** is set to a fixed value, the tab bar cannot extend the bottom safe area. Starting from API version 14, it can be used together with the [safeAreaPadding](arkts-arkui-common-comp-commonmethod-c.md#safeareapadding) attribute. When **safeAreaPadding** does not set bottom or bottom is set to 0, the safe area can be extended.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barHeight(value: Length): TabsAttribute--><!--Device-TabsAttribute-barHeight(value: Length): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Height value of the tab bar.<br>Default value:<br>When the style is not set or a custom style is set through **CustomBuilder** and the **vertical** attribute is **false**, the default value is 56vp.<br>When the style is not set or a custom style is set through **CustomBuilder** and the **vertical** attribute is **true**, the default value is the height of the **Tabs**.<br>When the [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) style is set and the **vertical** attribute is **false**, the default value is 56vp.<br>When the **SubTabBarStyle** style is set and the **vertical** attribute is **true**, the default value is the height of the **Tabs**.<br>When the [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) style is set and the **vertical** attribute is **true**, the default value is the height of the **Tabs**.<br>When the BottomTabBarStyle style is set and the **vertical** attribute is **false**, the default value is 56vp. Starting from API version 12, the default value changes to 48vp.<br>**Since:** 8 |

<a id="barheight2"></a>

## barHeight

```TypeScript
barHeight(height: Length, noMinHeightLimit: boolean)
```

Sets the height value of the tab bar. For horizontal **Tabs**, you can set height to 'auto' so that the tab bar adapts to the height of its child components, and set **noMinHeightLimit** to true so that the adaptive height can be smaller than the default height of the **TabBar**. If height is set to a value smaller than 0 or greater than the height of **Tabs**, it is displayed by default value.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TabsAttribute-barHeight(height: Length, noMinHeightLimit: boolean): TabsAttribute--><!--Device-TabsAttribute-barHeight(height: Length, noMinHeightLimit: boolean): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Height value of the tab bar.<br>Default value:<br>If no style is set or a custom style is set through **CustomBuilder** and **vertical** is **false**, the default value is 56vp.<br>If no style is set or a custom style is set through **CustomBuilder** and **vertical** is **true**, the default value is the height of **Tabs**.<br>If the [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) style is set and **vertical** is **false**, the default value is 56vp.<br>If the **SubTabBarStyle** style is set and **vertical** is **true**, the default value is the height of **Tabs**.<br>If the [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) style is set and **vertical** is **true**, the default value is the height of **Tabs**.<br>If the BottomTabBarStyle style is set and **vertical** is **false**, the default value is 48vp. |
| noMinHeightLimit | boolean | Yes | Whether to cancel the minimum height limit of the tab bar when height is set to 'auto'. The default value is **false**.<br>**Note:** <br>The value true means to cancel the minimum height limit of the tab bar, that is, the height value of the tab bar can be smaller than the default value.<br>The value false means to limit the minimum height of the tab bar, that is, the minimum height value of the tab bar is equal to the default value. |

<a id="barmode1"></a>

## barMode

```TypeScript
barMode(value: BarMode.Fixed)
```

Sets the tab bar layout mode to BarMode.Fixed.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barMode(value: BarMode.Fixed): TabsAttribute--><!--Device-TabsAttribute-barMode(value: BarMode.Fixed): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BarMode.Fixed](arkts-arkui-tabs-comp-barmode-e.md) | Yes | All tab bars evenly share the bar width (evenly share the bar height in vertical mode). |

<a id="barmode2"></a>

## barMode

```TypeScript
barMode(value: BarMode.Scrollable, options: ScrollableBarModeOptions)
```

Sets the tab bar layout mode to **BarMode.Scrollable**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barMode(value: BarMode.Scrollable, options: ScrollableBarModeOptions): TabsAttribute--><!--Device-TabsAttribute-barMode(value: BarMode.Scrollable, options: ScrollableBarModeOptions): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BarMode.Scrollable](arkts-arkui-tabs-comp-barmode-e.md) | Yes | All tab bars use the actual layout width and can be scrolled when the total width (**barWidth** of horizontal **Tabs**, **barHeight** of vertical **Tabs**) is exceeded. |
| options | [ScrollableBarModeOptions](arkts-arkui-tabs-comp-scrollablebarmodeoptions-i.md) | Yes | Layout style of the tab bar in Scrollable mode.<br>**Note:** <br> Valid only in Scrollable and horizontal mode. |

<a id="barmode3"></a>

## barMode

```TypeScript
barMode(value: BarMode, options?: ScrollableBarModeOptions)
```

Sets the layout mode of the tab bar. The Fixed mode is suitable for scenarios with a fixed and small number of tabs; the Scrollable mode is suitable for scenarios with a large number of tabs or unfixed text length.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barMode(value: BarMode, options?: ScrollableBarModeOptions): TabsAttribute--><!--Device-TabsAttribute-barMode(value: BarMode, options?: ScrollableBarModeOptions): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BarMode](arkts-arkui-tabs-comp-barmode-e.md) | Yes | Layout mode.<br>Default value: **BarMode.Fixed** |
| options | [ScrollableBarModeOptions](arkts-arkui-tabs-comp-scrollablebarmodeoptions-i.md) | No | Layout style of the tab bar in Scrollable mode.<br>**Note:** <br> This parameter is valid only when **value** is **Scrollable** and the mode is horizontal.<br><br>**Since:** 10 |

## barOverlap

```TypeScript
barOverlap(value: boolean)
```

Sets whether the tab bar is blurred behind and overlaid on the **TabContent**. This is suitable for scenarios that require an immersive UI effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barOverlap(value: boolean): TabsAttribute--><!--Device-TabsAttribute-barOverlap(value: boolean): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the tab bar is blurred behind and overlaid on the TabContent. When barOverlap is set to true, the tab bar is blurred behind and overlaid on the TabContent, and the default blur material BlurStyle value of the tab bar is changed to 'BlurStyle.COMPONENT_THICK'. When barOverlap is set to false, there is no blur or overlay effect.<br>Default value: false |

## barPosition

```TypeScript
barPosition(value: BarPosition)
```

Sets the tab position of **Tabs**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barPosition(value: BarPosition): TabsAttribute--><!--Device-TabsAttribute-barPosition(value: BarPosition): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BarPosition](arkts-arkui-tabs-comp-barposition-e.md) | Yes | Sets the tab position of **Tabs**. The specific position of the tab is affected by the **vertical** attribute: when **vertical** is **true**, **Start** is on the left and **End** is on the right; when **vertical** is **false**, **Start** is at the top and **End** is at the bottom.<br>Default value: **BarPosition.Start** |

## barStyle

```TypeScript
barStyle(style: Optional<TabBarStyle>)
```

Sets the display style of the tab bar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-barStyle(style: Optional<TabBarStyle>): TabsAttribute--><!--Device-TabsAttribute-barStyle(style: Optional<TabBarStyle>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TabBarStyle](arkts-arkui-tabs-comp-tabbarstyle-e.md)&gt; | Yes | Display style of the tab bar.<br>Default value: **TabBarStyle.BOTTOM**. |

## barWidth

```TypeScript
barWidth(value: Length)
```

Sets the width of the tab bar. If the set value is less than 0 or greater than the width of the **Tabs** component, the default value is used.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-barWidth(value: Length): TabsAttribute--><!--Device-TabsAttribute-barWidth(value: Length): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Width of the tab bar.<br>Default value:<br>If [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) and [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) are not set for the tab bar and the **vertical** attribute is **false**, the default value is the width of the **Tabs**.<br>If **SubTabBarStyle** and **BottomTabBarStyle** are not set for the tab bar and the **vertical** attribute is **true**, the default value is 56 vp.<br>If **SubTabBarStyle** is set and the **vertical** attribute is **false**, the default value is the width of the **Tabs**.<br>If **SubTabBarStyle** is set and the **vertical** attribute is **true**, the default value is 56 vp.<br>If **BottomTabBarStyle** is set and the **vertical** attribute is **true**, the default value is 96 vp. <br>If **BottomTabBarStyle** is set and the **vertical** attribute is **false**, the default value is the width of the **Tabs**.<br>**Since:** 8 |

## cachedMaxCount

```TypeScript
cachedMaxCount(count: number, mode: TabsCacheMode)
```

Sets the maximum number of cached child components and the cache mode. If this attribute is not set, all child components are cached by default and are not released after caching. You are advised to set the value of **count** based on the number of tabs and the complexity of the child component content.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-TabsAttribute-cachedMaxCount(count: number, mode: TabsCacheMode): TabsAttribute--><!--Device-TabsAttribute-cachedMaxCount(count: number, mode: TabsCacheMode): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Maximum number of cached child components.<br>Value range: [0, +∞). If the value is set to a number less than 0, the child components are not subject to cache management. When the number of cached child components exceeds this value, the child components that are no longer needed are automatically released. |
| mode | [TabsCacheMode](arkts-arkui-tabs-comp-tabscachemode-e.md) | Yes | Cache mode of the child components.<br>Default value: **TabsCacheMode.CACHE_BOTH_SIDE** |

## customContentTransition

```TypeScript
customContentTransition(delegate: TabsCustomContentTransitionCallback)
```

Customizes the page switching animation of **Tabs**. This is applicable when you need personalized tab switching effects, such as flipping, fade in and fade out, and scaling.

Instructions:

1. When a custom switching animation is used, the default switching animation of the **Tabs** component is
disabled, and the page cannot be swiped along with the finger.
2. When this attribute is set to **undefined**, the custom switching animation is not used, and the default
switching animation of the component is used instead.
3. The custom switching animation does not support interruption.
4. Currently, the custom switching animation can be triggered only in two scenarios: tapping a tab and calling
the **TabsController.changeIndex()** API.
5. When the custom switching animation is used, all events supported by the **Tabs** component are available
except **onGestureSwipe**.
6. The triggering timing of the [onChange](#onchange) and
[onAnimationEnd](#onanimationend) events requires special explanation: if a second custom animation is triggered while the first custom animation is still in progress, the **onChange** and **onAnimationEnd** events of the first custom animation are triggered when the second custom animation starts.
7. When the custom animation is used, the layout mode of the pages participating in the animation is
changed to [Stack](arkts-arkui-stack-comp.md) layout. If the developer does not proactively set the [zIndex](arkts-arkui-common-comp-commonmethod-c.md#zindex) attribute of the related pages, all pages have the same **zIndex** value, and the rendering hierarchy of the pages is determined by their order in the component tree (that is, the order of the page index values). Therefore, the developer needs to proactively modify the **zIndex** attribute of the pages to control the rendering hierarchy.
8. This attribute cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAttribute-customContentTransition(delegate: TabsCustomContentTransitionCallback): TabsAttribute--><!--Device-TabsAttribute-customContentTransition(delegate: TabsCustomContentTransitionCallback): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delegate | [TabsCustomContentTransitionCallback](arkts-arkui-tabs-comp-tabscustomcontenttransitioncallback-t.md) | Yes | Callback invoked when the custom **Tabs** page switching animation starts.<br>**Since:** 18 |

## divider

```TypeScript
divider(value: DividerStyle | null)
```

Sets the style of the divider that separates the tab bar from the **TabContent**. If a visual separation is required between the tab bar and the **TabContent**, a divider can be added through this attribute.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-divider(value: DividerStyle | null): TabsAttribute--><!--Device-TabsAttribute-divider(value: DividerStyle | null): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DividerStyle](arkts-arkui-tabs-comp-dividerstyle-i.md) &#124; null | Yes | Style of the divider. By default, no divider is displayed.<br>DividerStyle: style of the divider;<br>null: no divider is displayed. |

## edgeEffect

```TypeScript
edgeEffect(edgeEffect: Optional<EdgeEffect>)
```

Sets the edge swipe effect. When the content is swiped to the edge, a rebound action is performed based on the specified edge effect type: the Spring mode uses a spring curve to implement an elastic rebound effect, the Fade mode uses gradient opacity to provide visual feedback, and the None mode does not perform any edge effect. The edge effect is triggered when the swiped content exceeds the container boundary.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 17.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAttribute-edgeEffect(edgeEffect: Optional<EdgeEffect>): TabsAttribute--><!--Device-TabsAttribute-edgeEffect(edgeEffect: Optional<EdgeEffect>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| edgeEffect | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md)&gt; | Yes | Edge swipe effect.<br>Default value: EdgeEffect.Spring |

## fadingEdge

```TypeScript
fadingEdge(value: boolean)
```

Sets whether tabs fade out when they exceed the container width. It is recommended to use this attribute together with [barBackgroundColor](#barbackgroundcolor). When the **barBackgroundColor** attribute is not defined, a white fading effect is displayed at the end of the tab by default.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-fadingEdge(value: boolean): TabsAttribute--><!--Device-TabsAttribute-fadingEdge(value: boolean): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether tabs fade out when they exceed the container width.<br>Default value: **true**, tabs fade out when they exceed the container width. When set to **false**, tabs are directly truncated when they exceed the container width. If the [barBackgroundColor](#barbackgroundcolor) attribute is not set, the default white fading effect is still displayed at the end of the tab. |

## maxSidebarWidth

```TypeScript
maxSidebarWidth(value: Optional<Length>)
```

Sets the maximum width of the sidebar tab bar. This attribute takes effect only when the tab bar is displayed as a sidebar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-maxSidebarWidth(value: Optional<Length>): TabsAttribute--><!--Device-TabsAttribute-maxSidebarWidth(value: Optional<Length>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Length](../arkts-apis/arkts-arkui-length-t.md)&gt; | Yes | Maximum width of the sidebar tab bar. The width of the sidebar tab bar does not exceed this value. <br>If this attribute is not set or is set to **undefined**, no maximum width is imposed on the sidebar tab bar, which means the sidebar tab bar can be as wide as the **Tabs** component. <br>The set value is expected to be greater than or equal to that of [minSidebarWidth](#minsidebarwidth). |

## minContentWidth

```TypeScript
minContentWidth(value: Optional<Length>)
```

Sets the minimum width of the content area of the **Tabs** component. This attribute takes effect only when the tab bar is displayed as a sidebar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-minContentWidth(value: Optional<Length>): TabsAttribute--><!--Device-TabsAttribute-minContentWidth(value: Optional<Length>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Length](../arkts-apis/arkts-arkui-length-t.md)&gt; | Yes | Minimum width of the content area. The width of the content area does not become smaller than this value; if the remaining space is insufficient, the content area is clipped.<br>If this attribute is not set or is set to **undefined**, no minimum width is imposed on the content area, which means the content area can be compressed to **0vp**. |

## minSidebarWidth

```TypeScript
minSidebarWidth(value: Optional<Length>)
```

Sets the minimum width of the sidebar tab bar. This attribute takes effect only when the tab bar is displayed as a sidebar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-minSidebarWidth(value: Optional<Length>): TabsAttribute--><!--Device-TabsAttribute-minSidebarWidth(value: Optional<Length>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Length](../arkts-apis/arkts-arkui-length-t.md)&gt; | Yes | Minimum width of the sidebar tab bar. The width of the sidebar tab bar does not become smaller than this value. <br>If this attribute is not set or is set to **undefined**, no minimum width is imposed on the sidebar tab bar, which means the sidebar tab bar can be compressed to **0vp**. <br>The set value is expected to be less than or equal to that of [maxSidebarWidth](#maxsidebarwidth). |

## nestedScroll

```TypeScript
nestedScroll(value: TabsNestedScrollMode | undefined)
```

Sets the nested scrolling mode between the **Tabs** component and its parent component. If not set, the default nested scrolling mode is [SELF_ONLY](arkts-arkui-tabs-comp-tabsnestedscrollmode-e.md).

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-TabsAttribute-nestedScroll(value: TabsNestedScrollMode | undefined): TabsAttribute--><!--Device-TabsAttribute-nestedScroll(value: TabsNestedScrollMode | undefined): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TabsNestedScrollMode](arkts-arkui-tabs-comp-tabsnestedscrollmode-e.md) &#124; undefined | Yes | Nested scrolling mode between the **Tabs** component and its parent component.<br>When set to undefined, the **Tabs** component scrolls on its own and does not interact with the parent component. |

## onAnimationEnd

```TypeScript
onAnimationEnd(handler: OnTabsAnimationEndCallback)
```

Triggered when the switching animation ends, including when the gesture is interrupted during the animation. When [animationDuration](#animationduration) is **0** (animation disabled), this callback is not triggered.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAttribute-onAnimationEnd(handler: OnTabsAnimationEndCallback): TabsAttribute--><!--Device-TabsAttribute-onAnimationEnd(handler: OnTabsAnimationEndCallback): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnTabsAnimationEndCallback](arkts-arkui-tabs-comp-ontabsanimationendcallback-t.md) | Yes | Callback invoked when the switching animation ends.<br>**Since:** 18 |

## onAnimationStart

```TypeScript
onAnimationStart(handler: OnTabsAnimationStartCallback)
```

Triggered when the switching animation starts. When [animationDuration](#animationduration) is **0**, the animation is disabled, and when [scrollable](#scrollable) is **false**, this callback is not triggered.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAttribute-onAnimationStart(handler: OnTabsAnimationStartCallback): TabsAttribute--><!--Device-TabsAttribute-onAnimationStart(handler: OnTabsAnimationStartCallback): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnTabsAnimationStartCallback](arkts-arkui-tabs-comp-ontabsanimationstartcallback-t.md) | Yes | Callback triggered when the switching animation starts.<br>**Since:** 18 |

## onBarDisplayModeChange

```TypeScript
onBarDisplayModeChange(callback: Optional<Callback<TabBarDisplayMode>>)
```

Triggered after the TabBar display mode changes.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-onBarDisplayModeChange(callback: Optional<Callback<TabBarDisplayMode>>): TabsAttribute--><!--Device-TabsAttribute-onBarDisplayModeChange(callback: Optional<Callback<TabBarDisplayMode>>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;[TabBarDisplayMode](arkts-arkui-tabs-comp-tabbardisplaymode-e.md)&gt;&gt; | Yes | Display mode change callback. |

## onChange

```TypeScript
onChange(event: Callback<number>)
```

Triggered after the tab is switched.

This event is triggered when any of the following conditions is met:

1. Triggered after the component sliding animation ends when the page is switched by swiping.
2. Triggered after the tab is switched by calling [changeIndex](arkts-arkui-tabs-comp-tabscontroller-c.md#changeindex) through the [controller](arkts-arkui-tabs-comp-tabscontroller-c.md).
3. Triggered after the tab is switched when the **index** attribute value constructed by the [state variable](../../../ui/state-management/arkts-state.md) is dynamically changed.
4. Triggered after the tab is switched when a tab bar tab is tapped.

> **NOTE:** 
> 
> When a custom tab is used, linking in the **onChange** event may cause the tab linkage to be executed only after
> the swipe page is switched, resulting in a delayed custom tab switching effect. It is recommended that you listen
> for and refresh the current index in [onAnimationStart](#onanimationstart) to ensure that the
> animation is triggered in a timely manner. For details, see
> [Example 3](../../../reference/apis-arkui/arkui-ts/ts-container-tabs.md#example-3-implementing-custom-tab-switching-synchronization).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-onChange(event: Callback<number>): TabsAttribute--><!--Device-TabsAttribute-onChange(event: Callback<number>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | Yes | Index of the currently displayed tab, starting from 0.<br>**Since:** 18 |

## onContentDidScroll

```TypeScript
onContentDidScroll(handler: OnTabsContentDidScrollCallback | undefined)
```

Triggered when content in the **Tabs** component scrolls.

During page scrolling, the [OnTabsContentDidScrollCallback](arkts-arkui-tabs-comp-ontabscontentdidscrollcallback-t.md) callback is invoked for all pages in the viewport on a frame-by-frame basis. For example, when there are two pages whose subscripts are 0 and 1 in the viewport, two callbacks whose indexes are 0 and 1 are invoked in each frame.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TabsAttribute-onContentDidScroll(handler: OnTabsContentDidScrollCallback | undefined): TabsAttribute--><!--Device-TabsAttribute-onContentDidScroll(handler: OnTabsContentDidScrollCallback | undefined): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnTabsContentDidScrollCallback](arkts-arkui-tabs-comp-ontabscontentdidscrollcallback-t.md) &#124; undefined | Yes | Callback triggered when a tab page is swiped. Passing **undefined** will unbind the previously registered callback. |

## onContentWillChange

```TypeScript
onContentWillChange(handler: OnTabsContentWillChangeCallback)
```

Customizes the capability of intercepting **Tabs** page switching. This callback is triggered when a new page is about to be displayed.

This event is triggered when any of the following conditions is met:

1. A new page is switched to by swiping the **TabContent**.
2. Triggered when a new page is switched to through the  
**TabsController**.[changeIndex](arkts-arkui-tabs-comp-tabscontroller-c.md#changeindex) API.
3. Triggered when a new page is switched to by dynamically changing the **index** attribute value.
4. Triggered when a new page is switched to by tapping a tab bar tab.
5. Triggered when a new page is switched to through the left and right arrow keys on
the keyboard after a tab bar tab gains focus.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAttribute-onContentWillChange(handler: OnTabsContentWillChangeCallback): TabsAttribute--><!--Device-TabsAttribute-onContentWillChange(handler: OnTabsContentWillChangeCallback): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnTabsContentWillChangeCallback](arkts-arkui-tabs-comp-ontabscontentwillchangecallback-t.md) | Yes | Callback for customizing the **Tabs** page switching interception capability, triggered when a new page is about to be displayed.<br>**Since:** 18 |

## onGestureSwipe

```TypeScript
onGestureSwipe(handler: OnTabsGestureSwipeCallback)
```

Triggered frame by frame during the swipe of the page, used to listen for the real-time swipe state of the currently displayed page.

> **NOTE:** 
> 
> When [customContentTransition](#customcontenttransition) is used to customize the switching
> animation, this event is not triggered.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabsAttribute-onGestureSwipe(handler: OnTabsGestureSwipeCallback): TabsAttribute--><!--Device-TabsAttribute-onGestureSwipe(handler: OnTabsGestureSwipeCallback): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnTabsGestureSwipeCallback](arkts-arkui-tabs-comp-ontabsgestureswipecallback-t.md) | Yes | Callback triggered frame by frame during the swipe of the page.<br>**Since:** 18 |

## onSelected

```TypeScript
onSelected(event: Callback<number>)
```

Triggered when the selected element changes. The index of the currently selected element is returned.

This event is triggered when any of the following occurs:

1. When the swipe gesture is released and the tab switching threshold is met, triggering the switching animation.

2. When the [changeIndex](arkts-arkui-tabs-comp-tabscontroller-c.md#changeindex) API of [TabsController](arkts-arkui-tabs-comp-tabscontroller-c.md)
is called, triggering the switching animation.

3. When the index of the active tab is changed through the bound
[state variable](../../../ui/state-management/arkts-state.md).

4. When a tab is tapped.

> **NOTE:** 
> 
> In the **onSelected** callback, the index of the current displayed page cannot be set using **index** of
> [TabsOptions](arkts-arkui-tabs-comp-tabsoptions-i.md), and **TabsController.changeIndex()** cannot be called.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabsAttribute-onSelected(event: Callback<number>): TabsAttribute--><!--Device-TabsAttribute-onSelected(event: Callback<number>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | Yes | Index of the currently selected element. |

## onTabBarClick

```TypeScript
onTabBarClick(event: Callback<number>)
```

Triggered when a tab is clicked.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-onTabBarClick(event: Callback<number>): TabsAttribute--><!--Device-TabsAttribute-onTabBarClick(event: Callback<number>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | Yes | Index of the clicked tab. The index starts from 0.<br>**Since:** 18 |

## onUnselected

```TypeScript
onUnselected(event: Callback<number>)
```

Triggered when the selected element changes. The index of the element that is about to be hidden is returned.

This event is triggered when any of the following occurs:

1. When the swipe gesture is released and the tab switching threshold is met, triggering the switching animation.

2. When the [changeIndex](arkts-arkui-tabs-comp-tabscontroller-c.md#changeindex) API of [TabsController](arkts-arkui-tabs-comp-tabscontroller-c.md) is called, triggering the switching animation.

3. When the index of the active tab is changed through the bound [state variable](../../../ui/state-management/arkts-state.md).

4. When a tab is tapped.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabsAttribute-onUnselected(event: Callback<number>): TabsAttribute--><!--Device-TabsAttribute-onUnselected(event: Callback<number>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | Yes | Index of the element that is about to be hidden. |

## pageFlipMode

```TypeScript
pageFlipMode(mode: Optional<PageFlipMode>)
```

Sets the mode for flipping pages using the mouse wheel.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TabsAttribute-pageFlipMode(mode: Optional<PageFlipMode>): TabsAttribute--><!--Device-TabsAttribute-pageFlipMode(mode: Optional<PageFlipMode>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PageFlipMode](../arkts-apis/arkts-arkui-pageflipmode-e.md)&gt; | Yes | Mode for flipping pages using the mouse wheel.<br>Default value: **PageFlipMode.CONTINUOUS** |

## scrollable

```TypeScript
scrollable(value: boolean)
```

Sets whether the page can be switched by swiping the page. When used with custom navigation buttons or tab bar tabs to control switching, it is recommended to set this parameter to false to avoid conflicts between swipe gestures and custom navigation logic.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-scrollable(value: boolean): TabsAttribute--><!--Device-TabsAttribute-scrollable(value: boolean): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the page can be switched by swiping the page.<br>Default value: **true**, the page can be switched by swiping the page. When set to **false**, the page cannot be switched by swiping. |

## sidebarBackgroundBlurStyle

```TypeScript
sidebarBackgroundBlurStyle(value: Optional<BlurStyle>)
```

Sets the background blur style of the sidebar tab bar. This attribute takes effect only when the tab bar is displayed as a sidebar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarBackgroundBlurStyle(value: Optional<BlurStyle>): TabsAttribute--><!--Device-TabsAttribute-sidebarBackgroundBlurStyle(value: Optional<BlurStyle>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BlurStyle](arkts-arkui-common-comp-blurstyle-e.md)&gt; | Yes | Background blur style of the sidebar tab bar.<br>Default value: **BlurStyle.NONE**. |

## sidebarBackgroundColor

```TypeScript
sidebarBackgroundColor(value: Optional<ResourceColor>)
```

Sets the background color of the sidebar tab bar. This attribute takes effect only when the tab bar is displayed as a sidebar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarBackgroundColor(value: Optional<ResourceColor>): TabsAttribute--><!--Device-TabsAttribute-sidebarBackgroundColor(value: Optional<ResourceColor>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Background color of the sidebar tab bar.<br>Default value: **Color.Transparent**. |

## sidebarBottomBar

```TypeScript
sidebarBottomBar(bottomBar: Optional<ComponentContent>)
```

Sets the bottom bar content of the sidebar tab bar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarBottomBar(bottomBar: Optional<ComponentContent>): TabsAttribute--><!--Device-TabsAttribute-sidebarBottomBar(bottomBar: Optional<ComponentContent>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bottomBar | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ComponentContent&gt; | Yes | bottom bar content of the sidebar tab bar. |

## sidebarDisplayStyle

```TypeScript
sidebarDisplayStyle(style: Optional<TabsSidebarDisplayStyle>)
```

Sets the display style of the sidebar for the **Tab** component.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarDisplayStyle(style: Optional<TabsSidebarDisplayStyle>): TabsAttribute--><!--Device-TabsAttribute-sidebarDisplayStyle(style: Optional<TabsSidebarDisplayStyle>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TabsSidebarDisplayStyle](arkts-arkui-tabs-comp-tabssidebardisplaystyle-e.md)&gt; | Yes |  |

## sidebarDivider

```TypeScript
sidebarDivider(value: Optional<DividerStyle>)
```

Sets the divider between the sidebar tab bar and the content area. This attribute takes effect only when the tab bar is displayed as a sidebar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarDivider(value: Optional<DividerStyle>): TabsAttribute--><!--Device-TabsAttribute-sidebarDivider(value: Optional<DividerStyle>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[DividerStyle](arkts-arkui-tabs-comp-dividerstyle-i.md)&gt; | Yes | Divider style between the sidebar tab bar and the content area. The divider is displayed vertically, where **strokeWidth** is its width, and **startMargin** and **endMargin** are the distances from the top and bottom of the sidebar, respectively.<br>**DividerStyle**: divider style.<br>**undefined**: no divider is displayed (default). |

## sidebarFooter

```TypeScript
sidebarFooter(footer: Optional<ComponentContent>)
```

Sets the footer content of the sidebar tab bar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarFooter(footer: Optional<ComponentContent>): TabsAttribute--><!--Device-TabsAttribute-sidebarFooter(footer: Optional<ComponentContent>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| footer | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ComponentContent&gt; | Yes | footer content of the sidebar tab bar. |

## sidebarHeader

```TypeScript
sidebarHeader(header: Optional<ComponentContent>)
```

Sets the header content of the sidebar tab bar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarHeader(header: Optional<ComponentContent>): TabsAttribute--><!--Device-TabsAttribute-sidebarHeader(header: Optional<ComponentContent>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| header | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ComponentContent&gt; | Yes | Header content of the sidebar tab bar. |

## sidebarPosition

```TypeScript
sidebarPosition(position: Optional<BarPosition>)
```

Sets the position of the sidebar tab bar. The sidebar tab bar position is not affected by the **vertical** attribute. It is always on the start or end side of the Tabs container, regardless of the **vertical** setting.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarPosition(position: Optional<BarPosition>): TabsAttribute--><!--Device-TabsAttribute-sidebarPosition(position: Optional<BarPosition>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BarPosition](arkts-arkui-tabs-comp-barposition-e.md)&gt; | Yes | Position of the sidebar tab bar.Start**.<br>Default value: **BarPosition. |

## sidebarSearchable

```TypeScript
sidebarSearchable(searchOptions?: TabsSidebarSearchableOptions)
```

Sets the search options for the sidebar tab bar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarSearchable(searchOptions?: TabsSidebarSearchableOptions): TabsAttribute--><!--Device-TabsAttribute-sidebarSearchable(searchOptions?: TabsSidebarSearchableOptions): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchOptions | [TabsSidebarSearchableOptions](arkts-arkui-tabs-comp-tabssidebarsearchableoptions-i.md) | No | Search options for the sidebar tab bar. |

## sidebarSelectedBoardColor

```TypeScript
sidebarSelectedBoardColor(value: Optional<ResourceColor>)
```

Sets the selected color of the tab board in sidebar mode.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarSelectedBoardColor(value: Optional<ResourceColor>): TabsAttribute--><!--Device-TabsAttribute-sidebarSelectedBoardColor(value: Optional<ResourceColor>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Selected color of the tab board in sidebar mode. |

## sidebarSelectedIconColor

```TypeScript
sidebarSelectedIconColor(value: Optional<ResourceColor>)
```

Sets the selected color of the tab icon in sidebar mode.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarSelectedIconColor(value: Optional<ResourceColor>): TabsAttribute--><!--Device-TabsAttribute-sidebarSelectedIconColor(value: Optional<ResourceColor>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Selected color of the tab icon in sidebar mode. |

## sidebarSelectedTextColor

```TypeScript
sidebarSelectedTextColor(value: Optional<ResourceColor>)
```

Sets the selected color of the tab text in sidebar mode.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarSelectedTextColor(value: Optional<ResourceColor>): TabsAttribute--><!--Device-TabsAttribute-sidebarSelectedTextColor(value: Optional<ResourceColor>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Selected color of the tab text in sidebar mode. |

## sidebarUnselectedIconColor

```TypeScript
sidebarUnselectedIconColor(value: Optional<ResourceColor>)
```

Sets the unselected color of the tab icon in sidebar mode.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarUnselectedIconColor(value: Optional<ResourceColor>): TabsAttribute--><!--Device-TabsAttribute-sidebarUnselectedIconColor(value: Optional<ResourceColor>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Unselected color of the tab icon in sidebar mode. |

## sidebarUnselectedTextColor

```TypeScript
sidebarUnselectedTextColor(value: Optional<ResourceColor>)
```

Sets the unselected color of the tab text in sidebar mode.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarUnselectedTextColor(value: Optional<ResourceColor>): TabsAttribute--><!--Device-TabsAttribute-sidebarUnselectedTextColor(value: Optional<ResourceColor>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | Yes | Unselected color of the tab text in sidebar mode. |

## sidebarWidth

```TypeScript
sidebarWidth(value: Optional<Length>)
```

Sets the width of the sidebar tab bar. This attribute takes effect only when the tab bar is displayed as a sidebar.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabsAttribute-sidebarWidth(value: Optional<Length>): TabsAttribute--><!--Device-TabsAttribute-sidebarWidth(value: Optional<Length>): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[Length](../arkts-apis/arkts-arkui-length-t.md)&gt; | Yes | Width of the sidebar tab bar.<br>Default value: **240vp**. |

## vertical

```TypeScript
vertical(value: boolean)
```

Sets whether the **Tabs** is vertical. A horizontal **Tabs** (default) is suitable for scenarios such as bottom navigation bars and top tab switching; a vertical **Tabs** is suitable for scenarios such as sidebar navigation and settings page categories.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabsAttribute-vertical(value: boolean): TabsAttribute--><!--Device-TabsAttribute-vertical(value: boolean): TabsAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the **Tabs** is vertical.<br>Default value: **false**, indicating a horizontal **Tabs**; **true** indicates a vertical **Tabs**.<br>When **height** of a horizontal **Tabs** is set to **auto**, the component height of the **Tabs** adapts to the height of its child components, that is, the height of [tabBar](arkts-arkui-tabcontent-comp-attribute.md#tabbar) + the width of the **divider** + the height of **TabContent** + the top and bottom **padding** values of the **Tabs** component + the top and bottom border widths of the **Tabs** component.<br>When **width** of a vertical **Tabs** is set to **auto**, the component width of the **Tabs** adapts to the width of its child components, that is, the width of **tabBar** + the width of the **divider** + the width of **TabContent** + the left and right **padding** values + the left and right **border** widths.<br>Keep the sizes of child components on each page as consistent as possible to avoid the page switching animation jumping when swiping pages. |
