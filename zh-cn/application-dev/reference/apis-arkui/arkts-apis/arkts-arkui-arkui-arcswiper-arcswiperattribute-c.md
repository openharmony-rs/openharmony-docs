# ArcSwiperAttribute

除支持通用属性外，还支持以下属性。

**继承/实现关系：** ArcSwiperAttribute extends CommonMethod<ArcSwiperAttribute>

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSwiper, ArcSwiperAttribute, ArcDotIndicator, ArcDirection, ArcSwiperController } from '@kit.ArkUI';
```

## customContentTransition

```TypeScript
customContentTransition(transition: Optional<SwiperContentAnimatedTransition>): ArcSwiperAttribute
```

自定义ArcSwiper页面切换动画。在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发回调，开发者可在回调中设置透明度、缩放比例、位移等属性。在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发[SwiperContentTransitionProxy](arkts-arkui-arkui-arcswiper-swipercontenttransitionproxy-i.md)回调。例如，当视窗内有下标为 0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[SwiperContentAnimatedTransition](arkts-arkui-arkui-arcswiper-swipercontentanimatedtransition-i.md)&gt; | 是 | ArcSwiper自定义切换动画相关信息，包含timeout和transition两个属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcSwiperAttribute
```

设置旋转表冠的灵敏度。通过旋转表冠可以控制ArcSwiper组件的翻页，设置不同灵敏度级别可调整表冠滚动的响应速度，灵敏度越高，单位旋转角度对应的页面切换步进越大。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[CrownSensitivity](arkts-arkui-crownsensitivity-e.md)&gt; | 是 | 旋转表冠的灵敏度。设置不同灵敏度级别可调整表冠滚动的响应速度。默认值：CrownSensitivity.MEDIUM |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## disableSwipe

```TypeScript
disableSwipe(disabled: Optional<boolean>): ArcSwiperAttribute
```

设置是否禁用组件滑动切换功能。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置是否禁用组件滑动切换功能。设置为true禁用，false不禁用。默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## disableTransitionAnimation

```TypeScript
disableTransitionAnimation(disabled: Optional<boolean>): ArcSwiperAttribute
```

设置是否关闭特殊动效效果。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否关闭特殊动效效果。true：关闭特殊动效效果；false：不关闭特殊动效效果。传入参数非法时，按false处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## duration

```TypeScript
duration(duration: Optional<number>): ArcSwiperAttribute
```

设置子组件切换的动画时长。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 子组件切换的动画时长。默认值：400单位：毫秒。传入负数时按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## effectMode

```TypeScript
effectMode(edgeEffect: Optional<EdgeEffect>): ArcSwiperAttribute
```

设置边缘滑动效果。目前支持的滑动效果参见[EdgeEffect](arkts-arkui-edgeeffect-e.md)的枚举说明。 通过[ArcSwiperController](arkts-arkui-arkui-arcswiper-arcswipercontroller-c.md)的showNext、showPrevious、finishAnimation接口控制翻页时，回弹效果不生效。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[EdgeEffect](arkts-arkui-edgeeffect-e.md)&gt; | 是 | 边缘滑动效果。通过ArcSwiperController接口控制翻页时，回弹效果不生效。默认值：EdgeEffect.Spring |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## index

```TypeScript
index(index: Optional<number>): ArcSwiperAttribute
```

设置当前在容器中显示的子组件的索引值。当index值为undefined、小于0或大于等于子组件数量时，按照默认值0处理。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 当前在容器中显示的子组件的索引值。当index值为undefined时，按取值为0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## indicator

```TypeScript
indicator(style: Optional<ArcDotIndicator | boolean>): ArcSwiperAttribute
```

设置弧形圆点指示器样式。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) \| boolean & gt; | 是 | 弧形圆点指示器样式。    - ArcDotIndicator：弧形圆点指示器属性及功能。    - boolean：是否启用弧形圆点指示器。设置为true启用，false不启用。    默认值：true默认类型：ArcDotIndicator |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## onAnimationEnd

```TypeScript
onAnimationEnd(handler: Optional<AnimationEndHandler>): ArcSwiperAttribute
```

切换动画结束时触发该回调。当ArcSwiper切换动效结束时触发，包括动画过程中手势中断或通过[SwiperController](../arkts-components/arkts-arkui-swipercontroller-c.md)调用finishAnimation。参数为动画结束后的index值，多列 ArcSwiper时，index为最左侧组件的索引。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[AnimationEndHandler](arkts-arkui-animationendhandler-t.md)&gt; | 是 | 切换动画结束时触发该回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## onAnimationStart

```TypeScript
onAnimationStart(handler: Optional<AnimationStartHandler>): ArcSwiperAttribute
```

切换动画开始时触发该回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[AnimationStartHandler](arkts-arkui-animationstarthandler-t.md)&gt; | 是 | 切换动画开始时的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## onChange

```TypeScript
onChange(handler: Optional<IndexChangedHandler>): ArcSwiperAttribute
```

当前显示子组件的索引变化时触发该事件，返回值为当前显示子组件的索引值。ArcSwiper组件结合[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，不能在onChange事件里 触发子页面UI的刷新。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[IndexChangedHandler](arkts-arkui-indexchangedhandler-t.md)&gt; | 是 | 当前显示元素的索引回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## onGestureSwipe

```TypeScript
onGestureSwipe(handler: Optional<GestureSwipeHandler>): ArcSwiperAttribute
```

在页面跟手滑动过程中，逐帧触发该回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[GestureSwipeHandler](arkts-arkui-gestureswipehandler-t.md)&gt; | 是 | 在页面跟手滑动过程中，逐帧触发该回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |

## vertical

```TypeScript
vertical(isVertical: Optional<boolean>): ArcSwiperAttribute
```

设置是否为纵向滑动。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVertical | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否为纵向滑动。true: 纵向滑动；false: 横向滑动。默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) |  |
