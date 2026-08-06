# ArcSwiperAttribute

除支持[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_外，还支持以下属性，不支持[Menu控制]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**继承/实现关系：** ArcSwiperAttribute extends [CommonMethod](../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface ArcSwiperAttribute extends CommonMethod--><!--Device-unnamed-export declare interface ArcSwiperAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## customContentTransition

```TypeScript
default customContentTransition(transition: ArcSwiperContentAnimatedTransition | undefined): this
```

自定义ArcSwiper页面切换动画。在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发回调，开发者可在回调中设置透明度、缩放比例、位移等属性。 在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 回调。例如，当视窗内有下标为0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default customContentTransition(transition: ArcSwiperContentAnimatedTransition | undefined): this--><!--Device-ArcSwiperAttribute-default customContentTransition(transition: ArcSwiperContentAnimatedTransition | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | ArcSwiper自定义切换动画相关信息。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，无回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## digitalCrownSensitivity

```TypeScript
default digitalCrownSensitivity(sensitivity: CrownSensitivity | undefined): this
```

设置旋转表冠的灵敏度。未通过该接口设置时，旋转表冠的灵敏度默认为CrownSensitivity.MEDIUM。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default digitalCrownSensitivity(sensitivity: CrownSensitivity | undefined): this--><!--Device-ArcSwiperAttribute-default digitalCrownSensitivity(sensitivity: CrownSensitivity | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 旋转表冠的灵敏度。设置不同灵敏度级别可调整表冠滚动的响应速度。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，旋转表冠的灵敏度为CrownSensitivity.MEDIUM。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## disableSwipe

```TypeScript
default disableSwipe(disabled: boolean | undefined): this
```

设置是否禁用组件滑动切换功能。未通过该接口设置时，默认不禁用组件滑动切换功能。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default disableSwipe(disabled: boolean | undefined): this--><!--Device-ArcSwiperAttribute-default disableSwipe(disabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | boolean \| undefined | 是 | 是否禁用组件滑动切换功能。设置为true禁用，false不禁用。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，不禁用组件滑动切换功能。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## disableTransitionAnimation

```TypeScript
default disableTransitionAnimation(disabled: boolean | undefined): this
```

是否关闭特殊动效效果。未通过该接口设置时，默认不关闭特殊动效效果。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default disableTransitionAnimation(disabled: boolean | undefined): this--><!--Device-ArcSwiperAttribute-default disableTransitionAnimation(disabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disabled | boolean \| undefined | 是 | 是否关闭特殊动效效果。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传入参数非法时，按false处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，不关闭特殊动效效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## duration

```TypeScript
default duration(duration: int | undefined): this
```

设置子组件切换的动画时长。未通过该接口设置时，默认子组件切换的动画时长为400ms。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default duration(duration: int | undefined): this--><!--Device-ArcSwiperAttribute-default duration(duration: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | int \| undefined | 是 | 子组件切换的动画时长。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，子组件切换的动画时长为400。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_单位：毫秒 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## effectMode

```TypeScript
default effectMode(edgeEffect: EdgeEffect | undefined): this
```

设置边缘滑动效果。未通过该接口设置时，边缘滑动效果默认为EdgeEffect.Spring。通过[ArcSwiperController]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的showNext、showPrevious、finishAnimation接口控制翻页时，回弹效果不生效。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default effectMode(edgeEffect: EdgeEffect | undefined): this--><!--Device-ArcSwiperAttribute-default effectMode(edgeEffect: EdgeEffect | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 边缘滑动效果。通过ArcSwiperController接口控制翻页时，回弹效果不生效。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，边缘滑动效果为EdgeEffect.Spring。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## index

```TypeScript
default index(index: int | undefined): this
```

设置当前在容器中显示的子组件的索引值。设置小于0或大于等于子组件数量时，按照默认值0处理。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default index(index: int | undefined): this--><!--Device-ArcSwiperAttribute-default index(index: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int \| undefined | 是 | 当前在容器中显示的子组件的索引值。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，当前在容器中显示的子组件的索引值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## indicator

```TypeScript
default indicator(style: ArcDotIndicator | boolean | undefined): this
```

设置弧形圆点指示器样式。未通过该接口设置时，默认启用弧形圆点指示器样式。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default indicator(style: ArcDotIndicator | boolean | undefined): this--><!--Device-ArcSwiperAttribute-default indicator(style: ArcDotIndicator | boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| boolean \| undefined | 是 | ArcDotIndicator：弧形圆点指示器属性及功能。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- boolean：是否启用弧形圆点指示器。设置为true启用，false不启用。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，启用弧形圆点指示器样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认类型：ArcDotIndicator |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAnimationEnd

```TypeScript
default onAnimationEnd(handler: AnimationEndHandler | undefined): this
```

切换动画结束时触发该回调。默认无回调。 当ArcSwiper切换动效结束时触发，包括动画过程中手势中断，通过[SwiperController]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_调用 finishAnimation。参数为动画结束后的index值，多列ArcSwiper时，index为最左侧组件的索引。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default onAnimationEnd(handler: AnimationEndHandler | undefined): this--><!--Device-ArcSwiperAttribute-default onAnimationEnd(handler: AnimationEndHandler | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 切换动画结束时触发该回调。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，无回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAnimationStart

```TypeScript
default onAnimationStart(handler: AnimationStartHandler | undefined): this
```

切换动画开始时触发该回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default onAnimationStart(handler: AnimationStartHandler | undefined): this--><!--Device-ArcSwiperAttribute-default onAnimationStart(handler: AnimationStartHandler | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 切换动画开始时的回调。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，无回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChange

```TypeScript
default onChange(handler: IndexChangedHandler | undefined): this
```

当前显示子组件的索引变化时触发该事件，返回值为当前显示子组件的索引值。 ArcSwiper组件结合\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_使用时，不能在onChange事件里 触发子页面UI的刷新。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default onChange(handler: IndexChangedHandler | undefined): this--><!--Device-ArcSwiperAttribute-default onChange(handler: IndexChangedHandler | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 当前显示的子组件索引变化时触发该事件。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，无回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onGestureSwipe

```TypeScript
default onGestureSwipe(handler: GestureSwipeHandler | undefined): this
```

在页面跟手滑动过程中，逐帧触发该回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default onGestureSwipe(handler: GestureSwipeHandler | undefined): this--><!--Device-ArcSwiperAttribute-default onGestureSwipe(handler: GestureSwipeHandler | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 在页面跟手滑动过程中，逐帧触发该回调。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，无回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setArcSwiperOptions

```TypeScript
default setArcSwiperOptions(controller?: ArcSwiperController): this
```

设置arcSwiper选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default setArcSwiperOptions(controller?: ArcSwiperController): this--><!--Device-ArcSwiperAttribute-default setArcSwiperOptions(controller?: ArcSwiperController): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | ArcSwiper构造函数选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回ArcSwiperAttribute的实例。 |

## vertical

```TypeScript
default vertical(isVertical: boolean | undefined): this
```

设置是否为纵向滑动。未通过该接口设置时，默认为横向滑动。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperAttribute-default vertical(isVertical: boolean | undefined): this--><!--Device-ArcSwiperAttribute-default vertical(isVertical: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVertical | boolean \| undefined | 是 | 是否为纵向滑动。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true表示纵向滑动；false表示横向滑动。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，进行横向滑动。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

