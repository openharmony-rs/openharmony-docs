# Tabs属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** TabsAttribute extends [CommonMethod<TabsAttribute>](CommonMethod<TabsAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class TabsAttribute extends CommonMethod<TabsAttribute>--><!--Device-unnamed-declare class TabsAttribute extends CommonMethod<TabsAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## animationCurve

```TypeScript
animationCurve(curve: Curve | ICurve)
```

设置Tabs翻页动画曲线。常用曲线参考[Curve](../arkts-apis/arkts-arkui-curve-e.md)，也可以通过[插值计算](../arkts-apis/arkts-curves.md)模块提供的接口创建自定义的插值曲线对象。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-animationCurve(curve: Curve | ICurve): TabsAttribute--><!--Device-TabsAttribute-animationCurve(curve: Curve | ICurve): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| curve | [Curve](../arkts-apis/arkts-arkui-curve-e.md) \| ICurve | 是 | Tabs翻页的动画曲线。<br/>默认值：<br/>滑动TabContent翻页时，默认值为interpolatingSpring(-1, 1, 228, 30)。<br/>点击TabBar页签和调用TabsController的changeIndex接口翻页时，默认值为cubicBezierCurve(0.2, 0.0, 0.1, 1.0)。<br/>设置自定义动画曲线时，滑动翻页和点击页签、调用changeIndex翻页都使用设置的动画曲线。 |

## animationDuration

```TypeScript
animationDuration(value: number)
```

设置Tabs翻页动画时长。

animationCurve不设置时，由于滑动TabContent翻页动画曲线interpolatingSpring(-1, 1, 228, 30)时长只受曲线自身参数影响，animationDuration只能控制点击TabBar页签和调用TabsController的changeIndex接口切换TabContent的动画时长。

不受animationDuration控制的曲线可以查阅[插值计算](../arkts-apis/arkts-curves.md)模块，比如[springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md#springmotion)、[responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md#responsivespringmotion)和[interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md#interpolatingspring)类型的曲线。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-animationDuration(value: number): TabsAttribute--><!--Device-TabsAttribute-animationDuration(value: number): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | Tabs翻页的动画时长。<br/>默认值：<br/>API version 10及以前，不设置该属性或设置为null时，默认值为0，即Tabs翻页无动画。设置为小于0或undefined时，默认值为300。<br/>API version 11及以后，不设置该属性或设置为异常值，且设置TabBar为BottomTabBarStyle样式时，默认值为0。设置TabBar为其他样式时，默认值为300。<br/>单位：ms<br/>取值范围：[0, +∞) |

## animationMode

```TypeScript
animationMode(mode: Optional<AnimationMode>)
```

设置点击TabBar页签或调用TabsController的changeIndex接口时切换TabContent的动画形式。
> **说明：**
> 此属性不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-animationMode(mode: Optional<AnimationMode>): TabsAttribute--><!--Device-TabsAttribute-animationMode(mode: Optional<AnimationMode>): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;AnimationMode&gt; | 是 | 点击TabBar页签或调用TabsController的changeIndex接口时切换TabContent的动画形式。<br/>默认值：AnimationMode.CONTENT_FIRST，表示在点击TabBar页签或调用TabsController的changeIndex接口切换TabContent时，先加载目标页内容，再开始切换动画。 |

## barBackgroundBlurStyle

```TypeScript
barBackgroundBlurStyle(value: BlurStyle)
```

设置TabBar的背景模糊材质。
> **说明：**
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barBackgroundBlurStyle(value: BlurStyle): TabsAttribute--><!--Device-TabsAttribute-barBackgroundBlurStyle(value: BlurStyle): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BlurStyle](arkts-arkui-blurstyle-e.md) | 是 | TabBar的背景模糊材质。<br />默认值：BlurStyle.NONE |

## barBackgroundBlurStyle

```TypeScript
barBackgroundBlurStyle(style: BlurStyle, options: BackgroundBlurStyleOptions)
```

为TabBar提供一种在背景和内容之间的模糊能力，通过枚举值的方式封装了不同的模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barBackgroundBlurStyle(style: BlurStyle, options: BackgroundBlurStyleOptions): TabsAttribute--><!--Device-TabsAttribute-barBackgroundBlurStyle(style: BlurStyle, options: BackgroundBlurStyleOptions): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [BlurStyle](arkts-arkui-blurstyle-e.md) | 是 | 背景模糊样式。模糊样式中封装了模糊半径、蒙版颜色、蒙版透明度、饱和度、亮度五个参数。 |
| options | [BackgroundBlurStyleOptions](arkts-arkui-backgroundblurstyleoptions-i.md) | 是 | 背景模糊选项。 |

## barBackgroundColor

```TypeScript
barBackgroundColor(value: ResourceColor)
```

设置TabBar的背景颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barBackgroundColor(value: ResourceColor): TabsAttribute--><!--Device-TabsAttribute-barBackgroundColor(value: ResourceColor): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | TabBar的背景颜色。<br />默认值：Color.Transparent，透明 |

## barBackgroundEffect

```TypeScript
barBackgroundEffect(options: BackgroundEffectOptions)
```

设置TabBar背景属性，包含背景模糊半径，亮度，饱和度，颜色等参数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barBackgroundEffect(options: BackgroundEffectOptions): TabsAttribute--><!--Device-TabsAttribute-barBackgroundEffect(options: BackgroundEffectOptions): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [BackgroundEffectOptions](arkts-arkui-backgroundeffectoptions-i.md) | 是 | 设置TabBar背景属性包括：模糊半径，亮度，饱和度，颜色等。 |

## barFloatingStyle

```TypeScript
barFloatingStyle(style: Optional<FloatingTabBarStyle>)
```

为页签栏启用浮动样式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barFloatingStyle(style: Optional<FloatingTabBarStyle>): TabsAttribute--><!--Device-TabsAttribute-barFloatingStyle(style: Optional<FloatingTabBarStyle>): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;FloatingTabBarStyle&gt; | 是 | 页签栏的浮动样式 |

## barGridAlign

```TypeScript
barGridAlign(value: BarGridColumnOptions)
```

以栅格化方式设置TabBar的可见区域。具体参见BarGridColumnOptions对象。仅水平模式下有效，[不适用于XS、XL和XXL设备](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barGridAlign(value: BarGridColumnOptions): TabsAttribute--><!--Device-TabsAttribute-barGridAlign(value: BarGridColumnOptions): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BarGridColumnOptions](arkts-arkui-bargridcolumnoptions-i.md) | 是 | 以栅格化方式设置TabBar的可见区域。 |

## barHeight

```TypeScript
barHeight(value: Length)
```

设置TabBar的高度值。横向Tabs可以设置height为'auto'，让TabBar自适应子组件高度。height设置为小于0或大于Tabs高度值时，按默认值显示。

API version 14之前的版本，若设置barHeight为固定值后，TabBar无法扩展底部安全区。从API version 14开始支持配合[safeAreaPadding](arkts-arkui-commonmethod-c.md#safeareapadding)属性，当safeAreaPadding不设置bottom或者bottom设置为0时，可以实现扩展安全区。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barHeight(value: Length): TabsAttribute--><!--Device-TabsAttribute-barHeight(value: Length): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | TabBar的高度值。<br/>默认值：<br/>未设置样式或者通过CustomBuilder设置自定义样式的TabBar且vertical属性为false时，默认值为56vp。<br/>未设置样式或者通过CustomBuilder设置自定义样式的TabBar且vertical属性为true时，默认值为Tabs的高度。<br/>设置[SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md)样式且vertical属性为false时，默认值为56vp。<br/>设置SubTabBarStyle样式且vertical属性为true时，默认值为Tabs的高度。<br/>设置[BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md)样式且vertical属性为true时，默认值为Tabs的高度。<br/>设置BottomTabBarStyle样式且vertical属性为false时，默认值为56vp，从API version 12开始，默认值变更为48vp。<br>**起始版本：** 8 |

## barHeight

```TypeScript
barHeight(height: Length, noMinHeightLimit: boolean)
```

设置TabBar的高度值。横向Tabs可以设置height为'auto'，让TabBar自适应子组件高度，并通过设置noMinHeightLimit为true让自适应高度可以小于TabBar默认高度。height设置为小于0或大于Tabs高度值时，按默认值显示。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barHeight(height: Length, noMinHeightLimit: boolean): TabsAttribute--><!--Device-TabsAttribute-barHeight(height: Length, noMinHeightLimit: boolean): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | TabBar的高度值。<br/>默认值：<br/>未设置样式或者通过CustomBuilder设置自定义样式的TabBar且vertical属性为false时，默认值为56vp。<br/>未设置样式或者通过CustomBuilder设置自定义样式的TabBar且vertical属性为true时，默认值为Tabs的高度。<br/>设置[SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md)样式且vertical属性为false时，默认值为56vp。<br/>设置SubTabBarStyle样式且vertical属性为true时，默认值为Tabs的高度。<br/>设置[BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md)样式且vertical属性为true时，默认值为Tabs的高度。<br/>设置BottomTabBarStyle样式且vertical属性为false时，默认值为48vp。 |
| noMinHeightLimit | boolean | 是 | height设置为'auto'时，设置是否取消TabBar的最小高度限制。默认值为false。<br/>**说明：** <br/>值为true表示取消TabBar的最小高度限制，即TabBar的高度值可以小于默认值。<br/>值为false表示限制TabBar的最小高度，即TabBar的最小高度值等于默认值。 |

## barMode

```TypeScript
barMode(value: BarMode.Fixed)
```

设置TabBar布局模式为BarMode.Fixed。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barMode(value: BarMode.Fixed): TabsAttribute--><!--Device-TabsAttribute-barMode(value: BarMode.Fixed): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BarMode.Fixed | 是 | 所有TabBar会平均分配barWidth宽度（纵向时平均分配barHeight高度）。 |

## barMode

```TypeScript
barMode(value: BarMode.Scrollable, options: ScrollableBarModeOptions)
```

设置TabBar布局模式为BarMode.Scrollable。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barMode(value: BarMode.Scrollable, options: ScrollableBarModeOptions): TabsAttribute--><!--Device-TabsAttribute-barMode(value: BarMode.Scrollable, options: ScrollableBarModeOptions): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | BarMode.Scrollable | 是 | 所有TabBar都使用实际布局宽度，超过总宽度（横向Tabs的barWidth，纵向Tabs的barHeight）后可滑动。 |
| options | [ScrollableBarModeOptions](arkts-arkui-scrollablebarmodeoptions-i.md) | 是 | Scrollable模式下的TabBar的布局样式。<br/>**说明：** <br/>仅水平模式下有效。 |

## barMode

```TypeScript
barMode(value: BarMode, options?: ScrollableBarModeOptions)
```

设置TabBar布局模式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barMode(value: BarMode, options?: ScrollableBarModeOptions): TabsAttribute--><!--Device-TabsAttribute-barMode(value: BarMode, options?: ScrollableBarModeOptions): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BarMode](arkts-arkui-barmode-e.md) | 是 | 布局模式。<br/>默认值：BarMode.Fixed |
| options | [ScrollableBarModeOptions](arkts-arkui-scrollablebarmodeoptions-i.md) | 否 | Scrollable模式下的TabBar的布局样式。<br/>**说明：** <br/>仅Scrollable且水平模式下有效。<br>**起始版本：** 10 |

## barOverlap

```TypeScript
barOverlap(value: boolean)
```

设置TabBar是否背后变模糊并叠加在TabContent之上。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barOverlap(value: boolean): TabsAttribute--><!--Device-TabsAttribute-barOverlap(value: boolean): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | TabBar是否背后变模糊并叠加在TabContent之上。当barOverlap设置为true时，TabBar背后变模糊并叠加在TabContent之上，并且TabBar默认模糊材质的[BlurStyle](arkts-arkui-blurstyle-e.md)值修改为'BlurStyle.COMPONENT_THICK'。当barOverlap设置为false时，无模糊和叠加效果。<br />默认值：false |

## barPosition

```TypeScript
barPosition(value: BarPosition)
```

设置Tabs的页签位置。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barPosition(value: BarPosition): TabsAttribute--><!--Device-TabsAttribute-barPosition(value: BarPosition): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BarPosition](arkts-arkui-barposition-e.md) | 是 | 设置Tabs的页签位置。<br/>默认值：BarPosition.Start |

## barWidth

```TypeScript
barWidth(value: Length)
```

设置TabBar的宽度值。设置为小于0或大于Tabs宽度值时，按默认值显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-barWidth(value: Length): TabsAttribute--><!--Device-TabsAttribute-barWidth(value: Length): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | TabBar的宽度值。<br/>默认值：<br/>未设置[SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md)和[BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md)的TabBar且vertical属性为false时，默认值为Tabs的宽度。<br/>未设置SubTabBarStyle和BottomTabBarStyle的TabBar且vertical属性为true时，默认值为56vp。<br/>设置SubTabBarStyle样式且vertical属性为false时，默认值为Tabs的宽度。<br/>设置SubTabBarStyle样式且vertical属性为true时，默认值为56vp。<br/>设置BottomTabBarStyle样式且vertical属性为true时，默认值为96vp。<br/>设置BottomTabBarStyle样式且vertical属性为false时，默认值为Tabs的宽度。<br>**起始版本：** 8 |

## cachedMaxCount

```TypeScript
cachedMaxCount(count: number, mode: TabsCacheMode)
```

设置子组件的最大缓存个数及缓存模式。未设置该属性时默认缓存所有子组件且缓存后不会释放。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-cachedMaxCount(count: number, mode: TabsCacheMode): TabsAttribute--><!--Device-TabsAttribute-cachedMaxCount(count: number, mode: TabsCacheMode): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 子组件的最大缓存个数。超出范围时自动释放不再需要的子组件。<br/>取值范围：[0, +∞)。 |
| mode | [TabsCacheMode](arkts-arkui-tabscachemode-e.md) | 是 | 子组件的缓存模式。<br/>默认值：TabsCacheMode.CACHE_BOTH_SIDE |

## customContentTransition

```TypeScript
customContentTransition(delegate: TabsCustomContentTransitionCallback)
```

自定义Tabs页面切换动画。

使用说明：

1. 当使用自定义切换动画时，Tabs组件自带的默认切换动画会被禁用，同时，页面也无法跟手滑动。2. 当设置为undefined时，表示不使用自定义切换动画，仍然使用组件自带的默认切换动画。3. 当前自定义切换动画不支持打断。4. 目前自定义切换动画只支持两种场景触发：点击页签和调用TabsController.changeIndex()接口。5. 当使用自定义切换动画时，Tabs组件支持的事件中，除了onGestureSwipe，其他事件均支持。6. [onChange](TabsAttribute#onChange)和[onAnimationEnd](TabsAttribute#onAnimationEnd)事件的触发时机需要特殊说明：如果在第一次自定义动画执行过程中，触发了第二次自定义动画，那么在开始第二次自定义动画时，就会触发第一次自定义动画的onChange和onAnimationEnd事件。7. 当使用自定义动画时，参与动画的页面布局方式会改为[Stack](../../apis-arkts/arkts-apis/arkts-arkts-util-stack-stack-c.md)布局。如果开发者未主动设置相关页面的[zIndex](arkts-arkui-commonmethod-c.md#zindex)属性，那么所有页面的zIndex值是一样的，页面的渲染层级会按照在组件树上的顺序（即页面的index值顺序）确定。因此，开发者需要主动修改页面的zIndex属性，来控制页面的渲染层级。8. 此属性不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。
> **说明：**
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-customContentTransition(delegate: TabsCustomContentTransitionCallback): TabsAttribute--><!--Device-TabsAttribute-customContentTransition(delegate: TabsCustomContentTransitionCallback): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | [TabsCustomContentTransitionCallback](arkts-arkui-tabscustomcontenttransitioncallback-t.md) | 是 | 自定义Tabs页面切换动画开始时触发的回调。<br>**起始版本：** 18 |

## divider

```TypeScript
divider(value: DividerStyle | null)
```

设置区分TabBar和TabContent的分割线样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-divider(value: DividerStyle | null): TabsAttribute--><!--Device-TabsAttribute-divider(value: DividerStyle | null): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DividerStyle](arkts-arkui-dividerstyle-i.md) \| null | 是 | 分割线样式，默认不显示分割线。<br/>DividerStyle：分割线的样式；<br/>null：不显示分割线。 |

## edgeEffect

```TypeScript
edgeEffect(edgeEffect: Optional<EdgeEffect>)
```

设置边缘滑动效果。
> **说明：**
> 从API version 17开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-edgeEffect(edgeEffect: Optional<EdgeEffect>): TabsAttribute--><!--Device-TabsAttribute-edgeEffect(edgeEffect: Optional<EdgeEffect>): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | [Optional](arkts-arkui-optional-t.md)&lt;EdgeEffect&gt; | 是 | 边缘滑动效果。<br/>默认值：EdgeEffect.Spring |

## fadingEdge

```TypeScript
fadingEdge(value: boolean)
```

设置页签超过容器宽度时是否渐隐消失。建议配合[barBackgroundColor](TabsAttribute#barBackgroundColor)属性一起使用，如果barBackgroundColor属性没有定义，会默认显示页签末端为白色的渐隐效果。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-fadingEdge(value: boolean): TabsAttribute--><!--Device-TabsAttribute-fadingEdge(value: boolean): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 页签超过容器宽度时是否渐隐消失。<br />默认值：true，页签超过容器宽度时会渐隐消失。设置为false时，页签超过容器宽度直接截断显示，不产生任何渐变效果?。 |

## nestedScroll

```TypeScript
nestedScroll(value: TabsNestedScrollMode | undefined)
```

设置Tabs组件与其父组件的嵌套滚动模式。未通过该接口设置时，默认嵌套滚动模式为[SELF_ONLY](arkts-arkui-tabsnestedscrollmode-e.md)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-nestedScroll(value: TabsNestedScrollMode | undefined): TabsAttribute--><!--Device-TabsAttribute-nestedScroll(value: TabsNestedScrollMode | undefined): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TabsNestedScrollMode](arkts-arkui-tabsnestedscrollmode-e.md) \| undefined | 是 | Tabs组件和父组件的嵌套滚动模式。<br/>设置undefined时，Tabs自身滚动，不与父组件联动。 |

## onAnimationEnd

```TypeScript
onAnimationEnd(handler: OnTabsAnimationEndCallback)
```

切换动画结束时触发该回调，包括动画过程中手势中断。当animationDuration为0时动画关闭，不触发该回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-onAnimationEnd(handler: OnTabsAnimationEndCallback): TabsAttribute--><!--Device-TabsAttribute-onAnimationEnd(handler: OnTabsAnimationEndCallback): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnTabsAnimationEndCallback](arkts-arkui-ontabsanimationendcallback-t.md) | 是 | 切换动画结束时触发的回调。<br>**起始版本：** 18 |

## onAnimationStart

```TypeScript
onAnimationStart(handler: OnTabsAnimationStartCallback)
```

切换动画开始时触发该回调。当[animationDuration](TabsAttribute#animationDuration)为0时动画关闭且[scrollable](TabsAttribute#scrollable)为false时，不触发该回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-onAnimationStart(handler: OnTabsAnimationStartCallback): TabsAttribute--><!--Device-TabsAttribute-onAnimationStart(handler: OnTabsAnimationStartCallback): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnTabsAnimationStartCallback](arkts-arkui-ontabsanimationstartcallback-t.md) | 是 | 切换动画开始时触发的回调。<br>**起始版本：** 18 |

## onChange

```TypeScript
onChange(event: Callback<number>)
```

Tab页签切换后触发的事件。

满足以下任一条件，即可触发该事件：

1、滑动页面进行页面切换时，组件滑动动画结束后触发。

2、通过[控制器](arkts-arkui-tabscontroller-c.md)调用[changeIndex](arkts-arkui-tabscontroller-c.md#changeindex)接口，Tab页签切换后触发。

3、动态修改[状态变量](../../../ui/state-management/arkts-state.md)构造的index属性值，Tab页签切换后触发。

4、点击TabBar页签，Tab页签切换后触发。
> **说明：**
> 使用自定义页签时，在onChange事件中联动可能会导致滑动页面切换后才执行页签联动，引起自定义页签切换效果延迟。建议在  
> [onAnimationStart](TabsAttribute#onAnimationStart)中监听并刷新当前索引，以确保动效能够及时触发。具体实现可参考  
> [示例3](../../../reference/apis-arkui/arkui-ts/ts-container-tabs.md#示例3自定义页签切换联动)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-onChange(event: Callback<number>): TabsAttribute--><!--Device-TabsAttribute-onChange(event: Callback<number>): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 当前显示的index索引，索引从0开始计算。<br>**起始版本：** 18 |

## onContentDidScroll

```TypeScript
onContentDidScroll(handler: OnTabsContentDidScrollCallback | undefined)
```

监听Tabs页面滑动事件。

在页面滑动过程中，会对视窗内所有页面逐帧触发[OnTabsContentDidScrollCallback](arkts-arkui-ontabscontentdidscrollcallback-t.md)回调。例如，当视窗内有下标为0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-onContentDidScroll(handler: OnTabsContentDidScrollCallback | undefined): TabsAttribute--><!--Device-TabsAttribute-onContentDidScroll(handler: OnTabsContentDidScrollCallback | undefined): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnTabsContentDidScrollCallback](arkts-arkui-ontabscontentdidscrollcallback-t.md) \| undefined | 是 | Tabs滑动时触发的回调，undefined会解绑原有回调。 |

## onContentWillChange

```TypeScript
onContentWillChange(handler: OnTabsContentWillChangeCallback)
```

自定义Tabs页面切换拦截事件能力，新页面即将显示时触发该回调。

满足以下任一条件，即可触发该事件：

1、滑动TabContent切换新页面时触发。

2、通过TabsController.[changeIndex](arkts-arkui-tabscontroller-c.md#changeindex)接口切换新页面时触发。

3、通过动态修改index属性值切换新页面时触发。

4、通过点击TabBar页签切换新页面时触发。

5、TabBar页签获焦后，通过键盘左右方向键等切换新页面时触发。
> **说明：**
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-onContentWillChange(handler: OnTabsContentWillChangeCallback): TabsAttribute--><!--Device-TabsAttribute-onContentWillChange(handler: OnTabsContentWillChangeCallback): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnTabsContentWillChangeCallback](arkts-arkui-ontabscontentwillchangecallback-t.md) | 是 | 自定义Tabs页面切换拦截事件能力，新页面即将显示时触发的回调。<br>**起始版本：** 18 |

## onGestureSwipe

```TypeScript
onGestureSwipe(handler: OnTabsGestureSwipeCallback)
```

在页面跟手滑动过程中，逐帧触发该回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-onGestureSwipe(handler: OnTabsGestureSwipeCallback): TabsAttribute--><!--Device-TabsAttribute-onGestureSwipe(handler: OnTabsGestureSwipeCallback): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnTabsGestureSwipeCallback](arkts-arkui-ontabsgestureswipecallback-t.md) | 是 | 在页面跟手滑动过程中，逐帧触发的回调。<br>**起始版本：** 18 |

## onSelected

```TypeScript
onSelected(event: Callback<number>)
```

当选中元素改变时触发该回调，返回值为当前选中的元素的索引值。

满足以下任一条件，即可触发该事件：

1. 滑动离手时满足翻页阈值，开始切换动画时触发。

2. 通过[TabsController控制器](arkts-arkui-tabscontroller-c.md)调用[changeIndex](arkts-arkui-tabscontroller-c.md#changeindex)接口，开始切换动画时触发。

3. 动态修改[状态变量](../../../ui/state-management/arkts-state.md)构造的index属性值后触发。

4. 通过页签处点击触发。
> **说明：**
> onSelected回调中不可通过[TabsOptions](arkts-arkui-tabsoptions-i.md)的index设置当前显示页的索引，不可调用TabsController.changeIndex()方法。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-onSelected(event: Callback<number>): TabsAttribute--><!--Device-TabsAttribute-onSelected(event: Callback<number>): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 当前选中元素的索引。 |

## onTabBarClick

```TypeScript
onTabBarClick(event: Callback<number>)
```

Tab页签点击后触发的事件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-onTabBarClick(event: Callback<number>): TabsAttribute--><!--Device-TabsAttribute-onTabBarClick(event: Callback<number>): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 被点击的index索引，索引从0开始计算。<br>**起始版本：** 18 |

## onUnselected

```TypeScript
onUnselected(event: Callback<number>)
```

当选中元素改变时触发该回调，返回值为将要隐藏的元素的索引值。

满足以下任一条件，即可触发该事件：

1. 滑动离手时满足翻页阈值，开始切换动画时触发。

2. 通过[TabsController控制器](arkts-arkui-tabscontroller-c.md)调用[changeIndex](arkts-arkui-tabscontroller-c.md#changeindex)接口，开始切换动画时触发。

3. 动态修改[状态变量](../../../ui/state-management/arkts-state.md)构造的index属性值后触发。

4. 通过页签处点击触发。
> **说明：**
> onUnselected回调中不可通过TabsOptions的index设置当前显示页的索引，不可调用TabsController.changeIndex()方法。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-onUnselected(event: Callback<number>): TabsAttribute--><!--Device-TabsAttribute-onUnselected(event: Callback<number>): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 将要隐藏元素的索引。 |

## pageFlipMode

```TypeScript
pageFlipMode(mode: Optional<PageFlipMode>)
```

设置鼠标滚轮翻页模式。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-pageFlipMode(mode: Optional<PageFlipMode>): TabsAttribute--><!--Device-TabsAttribute-pageFlipMode(mode: Optional<PageFlipMode>): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;PageFlipMode&gt; | 是 | 鼠标滚轮翻页模式。<br/>默认值：PageFlipMode.CONTINUOUS |

## scrollable

```TypeScript
scrollable(value: boolean)
```

设置是否可以通过滑动页面进行页面切换。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-scrollable(value: boolean): TabsAttribute--><!--Device-TabsAttribute-scrollable(value: boolean): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否可以通过滑动页面进行页面切换。<br/>默认值：true，可以通过滑动页面进行页面切换。为false时不可滑动切换页面。 |

## vertical

```TypeScript
vertical(value: boolean)
```

设置是否为纵向Tabs。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsAttribute-vertical(value: boolean): TabsAttribute--><!--Device-TabsAttribute-vertical(value: boolean): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否为纵向Tabs。<br/>默认值：false，横向Tabs，为true时纵向Tabs。<br/>当横向Tabs设置height为auto时，Tabs组件高度自适应子组件高度，即为[tabBar](TabContentAttribute#tabBar(options: string \| Resource \| CustomBuilder \| TabBarOptions))高度+divider线宽+TabContent高度+上下padding值+上下border宽度。<br/>当纵向Tabs设置width为auto时，Tabs组件宽度自适应子组件宽度，即为tabBar宽度+divider线宽+TabContent宽度+左右padding值+左右border宽度。<br/>尽量保持每一个页面中的子组件尺寸大小一致，避免滑动页面时出现页面切换动画跳动现象。 |

