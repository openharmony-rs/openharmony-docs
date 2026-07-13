# ArcSwiperAttribute

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性。

**继承/实现关系：** ArcSwiperAttribute extends [CommonMethod<ArcSwiperAttribute>](CommonMethod<ArcSwiperAttribute>)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## customContentTransition

```TypeScript
customContentTransition(transition: Optional<SwiperContentAnimatedTransition>): ArcSwiperAttribute
```

自定义ArcSwiper页面切换动画。在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发回调。开发者可以在回调中设置透明度、缩放比例、位移等属性来自定义切换动画。

在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发[SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md)回调。例如，当视窗内有下标为
0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | Optional&lt;SwiperContentAnimatedTransition&gt; | 是 | ArcSwiper自定义切换动画相关信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcSwiperAttribute
```

设置旋转表冠的灵敏度。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | Optional&lt;CrownSensitivity&gt; | 是 | 旋转表冠的灵敏度。<br/>默认值：CrownSensitivity.MEDIUM |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## disableSwipe

```TypeScript
disableSwipe(disabled: Optional<boolean>): ArcSwiperAttribute
```

是否禁用组件滑动切换功能。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | Optional&lt;boolean&gt; | 是 | 是否禁用组件滑动切换功能。设置为true禁用，false不禁用。<br/>默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## disableTransitionAnimation

```TypeScript
disableTransitionAnimation(disabled: Optional<boolean>): ArcSwiperAttribute
```

是否关闭特殊动效效果。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | Optional&lt;boolean&gt; | 是 | 是否关闭特殊动效效果。<br>true：关闭特殊动效效果；false：不关闭特殊动效效果。<br>传入参数非法时，按false处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## duration

```TypeScript
duration(duration: Optional<number>): ArcSwiperAttribute
```

设置子组件切换的动画时长。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | Optional&lt;number&gt; | 是 | 子组件切换的动画时长。<br/>默认值：400<br/>单位：毫秒 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## effectMode

```TypeScript
effectMode(edgeEffect: Optional<EdgeEffect>): ArcSwiperAttribute
```

设置边缘滑动效果。 目前支持的滑动效果参见[EdgeEffect](../arkts-components/arkts-arkui-edgeeffect-e.md)的。调用控制器接口时回弹不生效。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | Optional&lt;EdgeEffect&gt; | 是 | 边缘滑动效果。<br/>默认值：EdgeEffect.Spring |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## index

```TypeScript
index(index: Optional<number>): ArcSwiperAttribute
```

设置当前在容器中显示的子组件的索引值。设置小于0或大于等于子组件数量时，按照默认值0处理。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | Optional&lt;number&gt; | 是 | 当前在容器中显示的子组件的索引值。<br/>当index值为undefined时，按取值为0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## indicator

```TypeScript
indicator(style: Optional<ArcDotIndicator | boolean>): ArcSwiperAttribute
```

设置弧形圆点指示器样式。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;ArcDotIndicator \| boolean&gt; | 是 | 弧形圆点指示器样式。<br/> - ArcDotIndicator：弧形圆点指示器属性及功能。<br/> -boolean：是否启用弧形圆点指示器。设置为true启用，false不启用。<br/> 默认值：true<br/> 默认类型：ArcDotIndicator |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## onAnimationEnd

```TypeScript
onAnimationEnd(handler: Optional<AnimationEndHandler>): ArcSwiperAttribute
```

切换动画结束时触发该回调。

当ArcSwiper切换动效结束时触发，包括动画过程中手势中断，通过[SwiperController](../arkts-components/arkts-arkui-swipercontroller-c.md)调用finishAnimation。参数为动画结束后的index值，多列
ArcSwiper时，index为最左侧组件的索引。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;AnimationEndHandler&gt; | 是 | 切换动画结束时触发该回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## onAnimationStart

```TypeScript
onAnimationStart(handler: Optional<AnimationStartHandler>): ArcSwiperAttribute
```

切换动画开始时触发该回调。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;AnimationStartHandler&gt; | 是 | 切换动画开始时的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## onChange

```TypeScript
onChange(handler: Optional<IndexChangedHandler>): ArcSwiperAttribute
```

当前显示子组件的索引变化时触发该事件，返回值为当前显示子组件的索引值。

ArcSwiper组件结合[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，不能在onChange事件里
触发子页面UI的刷新。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;IndexChangedHandler&gt; | 是 | 当前显示元素的索引回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## onGestureSwipe

```TypeScript
onGestureSwipe(handler: Optional<GestureSwipeHandler>): ArcSwiperAttribute
```

在页面跟手滑动过程中，逐帧触发该回调。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;GestureSwipeHandler&gt; | 是 | 在页面跟手滑动过程中，逐帧触发该回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

## vertical

```TypeScript
vertical(isVertical: Optional<boolean>): ArcSwiperAttribute
```

设置是否为纵向滑动。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVertical | Optional&lt;boolean&gt; | 是 | 是否为纵向滑动。<br/>true: 纵向滑动；false: 横向滑动。<br/>默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcSwiperAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

