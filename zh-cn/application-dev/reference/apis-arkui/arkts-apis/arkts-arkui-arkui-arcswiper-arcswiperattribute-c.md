# ArcSwiperAttribute

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性。

**继承/实现关系：** ArcSwiperAttribute extends [CommonMethod<ArcSwiperAttribute>](CommonMethod<ArcSwiperAttribute>)

**起始版本：** 18

<!--Device-unnamed-declare class ArcSwiperAttribute extends CommonMethod<ArcSwiperAttribute>--><!--Device-unnamed-declare class ArcSwiperAttribute extends CommonMethod<ArcSwiperAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSwiperAttribute, ArcSwiper, ArcDirection, ArcSwiperController, ArcDotIndicator } from '@kit.ArkUI';
```

<a id="customcontenttransition"></a>
## customContentTransition

```TypeScript
customContentTransition(transition: Optional<SwiperContentAnimatedTransition>): ArcSwiperAttribute
```

自定义ArcSwiper页面切换动画。在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发回调。开发者可以在回调中设置透明度、缩放比例、位移等属性来自定义切换动画。

在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发[SwiperContentTransitionProxy](arkts-arkui-arkui-arcswiper-swipercontenttransitionproxy-i.md)回调。例如，当视窗内有下标为0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-customContentTransition(transition: Optional<SwiperContentAnimatedTransition>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-customContentTransition(transition: Optional<SwiperContentAnimatedTransition>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;SwiperContentAnimatedTransition&gt; | 是 | ArcSwiper自定义切换动画相关信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="digitalcrownsensitivity"></a>
## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcSwiperAttribute
```

设置旋转表冠的灵敏度。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;CrownSensitivity&gt; | 是 | 旋转表冠的灵敏度。<br/>默认值：CrownSensitivity.MEDIUM |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="disableswipe"></a>
## disableSwipe

```TypeScript
disableSwipe(disabled: Optional<boolean>): ArcSwiperAttribute
```

是否禁用组件滑动切换功能。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-disableSwipe(disabled: Optional<boolean>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-disableSwipe(disabled: Optional<boolean>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否禁用组件滑动切换功能。设置为true禁用，false不禁用。<br/>默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="disabletransitionanimation"></a>
## disableTransitionAnimation

```TypeScript
disableTransitionAnimation(disabled: Optional<boolean>): ArcSwiperAttribute
```

是否关闭特殊动效效果。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-disableTransitionAnimation(disabled: Optional<boolean>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-disableTransitionAnimation(disabled: Optional<boolean>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否关闭特殊动效效果。<br>true：关闭特殊动效效果；false：不关闭特殊动效效果。<br>传入参数非法时，按false处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="duration"></a>
## duration

```TypeScript
duration(duration: Optional<number>): ArcSwiperAttribute
```

设置子组件切换的动画时长。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-duration(duration: Optional<number>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-duration(duration: Optional<number>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 子组件切换的动画时长。<br/>默认值：400<br/>单位：毫秒 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="effectmode"></a>
## effectMode

```TypeScript
effectMode(edgeEffect: Optional<EdgeEffect>): ArcSwiperAttribute
```

设置边缘滑动效果。 目前支持的滑动效果参见[EdgeEffect](arkts-arkui-edgeeffect-e.md)的。调用控制器接口时回弹不生效。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-effectMode(edgeEffect: Optional<EdgeEffect>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-effectMode(edgeEffect: Optional<EdgeEffect>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;EdgeEffect&gt; | 是 | 边缘滑动效果。<br/>默认值：EdgeEffect.Spring |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="index"></a>
## index

```TypeScript
index(index: Optional<number>): ArcSwiperAttribute
```

设置当前在容器中显示的子组件的索引值。设置小于0或大于等于子组件数量时，按照默认值0处理。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-index(index: Optional<number>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-index(index: Optional<number>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 当前在容器中显示的子组件的索引值。<br/>当index值为undefined时，按取值为0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="indicator"></a>
## indicator

```TypeScript
indicator(style: Optional<ArcDotIndicator | boolean>): ArcSwiperAttribute
```

设置弧形圆点指示器样式。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-indicator(style: Optional<ArcDotIndicator | boolean>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-indicator(style: Optional<ArcDotIndicator | boolean>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;ArcDotIndicator \| boolean&gt; | 是 | 弧形圆点指示器样式。<br/> - ArcDotIndicator：弧形圆点指示器属性及功能。<br/> -boolean：是否启用弧形圆点指示器。设置为true启用，false不启用。<br/> 默认值：true<br/> 默认类型：ArcDotIndicator |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="onanimationend"></a>
## onAnimationEnd

```TypeScript
onAnimationEnd(handler: Optional<AnimationEndHandler>): ArcSwiperAttribute
```

切换动画结束时触发该回调。

当ArcSwiper切换动效结束时触发，包括动画过程中手势中断，通过[SwiperController](../arkts-components/arkts-arkui-swipercontroller-c.md)调用finishAnimation。参数为动画结束后的index值，多列ArcSwiper时，index为最左侧组件的索引。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-onAnimationEnd(handler: Optional<AnimationEndHandler>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-onAnimationEnd(handler: Optional<AnimationEndHandler>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;AnimationEndHandler&gt; | 是 | 切换动画结束时触发该回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="onanimationstart"></a>
## onAnimationStart

```TypeScript
onAnimationStart(handler: Optional<AnimationStartHandler>): ArcSwiperAttribute
```

切换动画开始时触发该回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-onAnimationStart(handler: Optional<AnimationStartHandler>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-onAnimationStart(handler: Optional<AnimationStartHandler>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;AnimationStartHandler&gt; | 是 | 切换动画开始时的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="onchange"></a>
## onChange

```TypeScript
onChange(handler: Optional<IndexChangedHandler>): ArcSwiperAttribute
```

当前显示子组件的索引变化时触发该事件，返回值为当前显示子组件的索引值。

ArcSwiper组件结合[LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，不能在onChange事件里触发子页面UI的刷新。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-onChange(handler: Optional<IndexChangedHandler>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-onChange(handler: Optional<IndexChangedHandler>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;IndexChangedHandler&gt; | 是 | 当前显示元素的索引回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="ongestureswipe"></a>
## onGestureSwipe

```TypeScript
onGestureSwipe(handler: Optional<GestureSwipeHandler>): ArcSwiperAttribute
```

在页面跟手滑动过程中，逐帧触发该回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-onGestureSwipe(handler: Optional<GestureSwipeHandler>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-onGestureSwipe(handler: Optional<GestureSwipeHandler>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;GestureSwipeHandler&gt; | 是 | 在页面跟手滑动过程中，逐帧触发该回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

<a id="vertical"></a>
## vertical

```TypeScript
vertical(isVertical: Optional<boolean>): ArcSwiperAttribute
```

设置是否为纵向滑动。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperAttribute-vertical(isVertical: Optional<boolean>): ArcSwiperAttribute--><!--Device-ArcSwiperAttribute-vertical(isVertical: Optional<boolean>): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVertical | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否为纵向滑动。<br/>true: 纵向滑动；false: 横向滑动。<br/>默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

