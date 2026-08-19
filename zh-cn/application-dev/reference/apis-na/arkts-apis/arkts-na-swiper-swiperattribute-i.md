# SwiperAttribute

除支持通用属性外，还支持以下属性： > **说明：** > > Swiper组件通用属性[clip](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clip12)的默认值为 > true。

**继承/实现关系：** SwiperAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SwiperAttribute--><!--Device-unnamed-export declare interface SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<SwiperAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-attributeModifier(modifier: AttributeModifier<SwiperAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-SwiperAttribute-attributeModifier(modifier: AttributeModifier<SwiperAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[SwiperAttribute](arkts-na-swiper-swiperattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## autoPlay

```TypeScript
autoPlay(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-autoPlay(value: boolean | undefined): this--><!--Device-SwiperAttribute-autoPlay(value: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## autoPlay

```TypeScript
autoPlay(autoPlay: boolean | undefined, options: AutoPlayOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-autoPlay(autoPlay: boolean | undefined, options: AutoPlayOptions | undefined): this--><!--Device-SwiperAttribute-autoPlay(autoPlay: boolean | undefined, options: AutoPlayOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| autoPlay | boolean \| undefined | 是 |  |
| options | [AutoPlayOptions](arkts-na-swiper-autoplayoptions-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## cachedCount

```TypeScript
cachedCount(value: int | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-cachedCount(value: int | undefined): this--><!--Device-SwiperAttribute-cachedCount(value: int | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## cachedCount

```TypeScript
cachedCount(count: int | undefined, isShown: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-cachedCount(count: int | undefined, isShown: boolean | undefined): this--><!--Device-SwiperAttribute-cachedCount(count: int | undefined, isShown: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | int \| undefined | 是 |  |
| isShown | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## cachedCount

```TypeScript
cachedCount(count: int | undefined, options: CachedCountOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-cachedCount(count: int | undefined, options: CachedCountOptions | undefined): this--><!--Device-SwiperAttribute-cachedCount(count: int | undefined, options: CachedCountOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | int \| undefined | 是 |  |
| options | [CachedCountOptions](arkts-na-swiper-cachedcountoptions-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## curve

```TypeScript
curve(value: Curve | string | ICurve | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-curve(value: Curve | string | ICurve | undefined): this--><!--Device-SwiperAttribute-curve(value: Curve | string | ICurve | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Curve](../../apis-arkui/arkts-apis/arkts-arkui-curve-e.md) \| string \| [ICurve](../../apis-arkui/arkts-components/arkts-arkui-icurve-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## customContentTransition

```TypeScript
customContentTransition(transition: SwiperContentAnimatedTransition | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-customContentTransition(transition: SwiperContentAnimatedTransition | undefined): this--><!--Device-SwiperAttribute-customContentTransition(transition: SwiperContentAnimatedTransition | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | [SwiperContentAnimatedTransition](arkts-na-swiper-swipercontentanimatedtransition-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## disableSwipe

```TypeScript
disableSwipe(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-disableSwipe(value: boolean | undefined): this--><!--Device-SwiperAttribute-disableSwipe(value: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## displayArrow

```TypeScript
displayArrow(value: ArrowStyle | boolean | undefined, isHoverShow?: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-displayArrow(value: ArrowStyle | boolean | undefined, isHoverShow?: boolean | undefined): this--><!--Device-SwiperAttribute-displayArrow(value: ArrowStyle | boolean | undefined, isHoverShow?: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ArrowStyle](arkts-na-swiper-arrowstyle-i.md) \| boolean \| undefined | 是 |  |
| isHoverShow | boolean \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## displayCount

```TypeScript
displayCount(value: int | string | SwiperAutoFill | ItemFillPolicy| undefined, swipeByGroup?: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-displayCount(value: int | string | SwiperAutoFill | ItemFillPolicy| undefined, swipeByGroup?: boolean | undefined): this--><!--Device-SwiperAttribute-displayCount(value: int | string | SwiperAutoFill | ItemFillPolicy| undefined, swipeByGroup?: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| string \| [SwiperAutoFill](arkts-na-swiper-swiperautofill-i.md) \| [ItemFillPolicy](../../apis-arkui/arkts-apis/arkts-arkui-itemfillpolicy-i.md) \| undefined | 是 |  |
| swipeByGroup | boolean \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## displayMode

```TypeScript
displayMode(value: SwiperDisplayMode | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-displayMode(value: SwiperDisplayMode | undefined): this--><!--Device-SwiperAttribute-displayMode(value: SwiperDisplayMode | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SwiperDisplayMode](arkts-na-swiper-swiperdisplaymode-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## duration

```TypeScript
duration(value: int | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-duration(value: int | undefined): this--><!--Device-SwiperAttribute-duration(value: int | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## effectMode

```TypeScript
effectMode(value: EdgeEffect | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-effectMode(value: EdgeEffect | undefined): this--><!--Device-SwiperAttribute-effectMode(value: EdgeEffect | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [EdgeEffect](../../apis-arkui/arkts-apis/arkts-arkui-edgeeffect-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## index

```TypeScript
index(value: int | Bindable<int> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-index(value: int | Bindable<int> | undefined): this--><!--Device-SwiperAttribute-index(value: int | Bindable<int> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| [Bindable](arkts-na-common-bindable-i.md)&lt;int&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## indicator

```TypeScript
indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean | undefined): this--><!--Device-SwiperAttribute-indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indicator | [IndicatorComponentController](../../apis-arkui/arkts-components/arkts-arkui-indicatorcomponentcontroller-c.md) \| [DotIndicator](arkts-na-swiper-dotindicator-c.md) \| [DigitIndicator](arkts-na-swiper-digitindicator-c.md) \| boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## indicatorInteractive

```TypeScript
indicatorInteractive(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-indicatorInteractive(value: boolean | undefined): this--><!--Device-SwiperAttribute-indicatorInteractive(value: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## interval

```TypeScript
interval(value: int | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-interval(value: int | undefined): this--><!--Device-SwiperAttribute-interval(value: int | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## itemSpace

```TypeScript
itemSpace(value: double | string | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-itemSpace(value: double | string | undefined): this--><!--Device-SwiperAttribute-itemSpace(value: double | string | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| string \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## loop

```TypeScript
loop(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-loop(value: boolean | undefined): this--><!--Device-SwiperAttribute-loop(value: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## maintainVisibleContentPosition

```TypeScript
maintainVisibleContentPosition(enabled: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-maintainVisibleContentPosition(enabled: boolean | undefined): this--><!--Device-SwiperAttribute-maintainVisibleContentPosition(enabled: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## nestedScroll

```TypeScript
nestedScroll(value: SwiperNestedScrollMode | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-nestedScroll(value: SwiperNestedScrollMode | undefined): this--><!--Device-SwiperAttribute-nestedScroll(value: SwiperNestedScrollMode | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SwiperNestedScrollMode](arkts-na-swiper-swipernestedscrollmode-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## nextMargin

```TypeScript
nextMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-nextMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this--><!--Device-SwiperAttribute-nextMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| undefined | 是 |  |
| ignoreBlank | boolean \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAnimationEnd

```TypeScript
onAnimationEnd(event: OnSwiperAnimationEndCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-onAnimationEnd(event: OnSwiperAnimationEndCallback | undefined): this--><!--Device-SwiperAttribute-onAnimationEnd(event: OnSwiperAnimationEndCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnSwiperAnimationEndCallback](arkts-na-onswiperanimationendcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAnimationStart

```TypeScript
onAnimationStart(event: OnSwiperAnimationStartCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-onAnimationStart(event: OnSwiperAnimationStartCallback | undefined): this--><!--Device-SwiperAttribute-onAnimationStart(event: OnSwiperAnimationStartCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnSwiperAnimationStartCallback](arkts-na-onswiperanimationstartcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChange

```TypeScript
onChange(event: Callback<int> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-onChange(event: Callback<int> | undefined): this--><!--Device-SwiperAttribute-onChange(event: Callback<int> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;int&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onContentDidScroll

```TypeScript
onContentDidScroll(handler: ContentDidScrollCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-onContentDidScroll(handler: ContentDidScrollCallback | undefined): this--><!--Device-SwiperAttribute-onContentDidScroll(handler: ContentDidScrollCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [ContentDidScrollCallback](arkts-na-contentdidscrollcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onContentWillScroll

```TypeScript
onContentWillScroll(handler: ContentWillScrollCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-onContentWillScroll(handler: ContentWillScrollCallback | undefined): this--><!--Device-SwiperAttribute-onContentWillScroll(handler: ContentWillScrollCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [ContentWillScrollCallback](arkts-na-contentwillscrollcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onGestureSwipe

```TypeScript
onGestureSwipe(event: OnSwiperGestureSwipeCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-onGestureSwipe(event: OnSwiperGestureSwipeCallback | undefined): this--><!--Device-SwiperAttribute-onGestureSwipe(event: OnSwiperGestureSwipeCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnSwiperGestureSwipeCallback](arkts-na-onswipergestureswipecallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onScrollStateChanged

```TypeScript
onScrollStateChanged(event: Callback<ScrollState> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-onScrollStateChanged(event: Callback<ScrollState> | undefined): this--><!--Device-SwiperAttribute-onScrollStateChanged(event: Callback<ScrollState> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[ScrollState](../../apis-arkui/arkts-components/arkts-arkui-scrollstate-e.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onSelected

```TypeScript
onSelected(event: Callback<int> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-onSelected(event: Callback<int> | undefined): this--><!--Device-SwiperAttribute-onSelected(event: Callback<int> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;int&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onUnselected

```TypeScript
onUnselected(event: Callback<int> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-onUnselected(event: Callback<int> | undefined): this--><!--Device-SwiperAttribute-onUnselected(event: Callback<int> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;int&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## pageFlipMode

```TypeScript
pageFlipMode(mode: PageFlipMode | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-pageFlipMode(mode: PageFlipMode | undefined): this--><!--Device-SwiperAttribute-pageFlipMode(mode: PageFlipMode | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [PageFlipMode](../../apis-arkui/arkts-apis/arkts-arkui-pageflipmode-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## prevMargin

```TypeScript
prevMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-prevMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this--><!--Device-SwiperAttribute-prevMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| undefined | 是 |  |
| ignoreBlank | boolean \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setSwiperOptions

```TypeScript
setSwiperOptions(controller?: SwiperController): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-setSwiperOptions(controller?: SwiperController): this--><!--Device-SwiperAttribute-setSwiperOptions(controller?: SwiperController): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [SwiperController](arkts-na-swiper-swipercontroller-c.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## vertical

```TypeScript
vertical(value: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-SwiperAttribute-vertical(value: boolean | undefined): this--><!--Device-SwiperAttribute-vertical(value: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

设置滑动器选项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default--><!--Device-SwiperAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

