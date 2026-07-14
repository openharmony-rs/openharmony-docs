# @ohos.arkui.ArcSwiper

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |
| [ArcSwiperAttribute](arkts-arkui-arcswiperattribute-c.md) | 除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性。 |
| [ArcSwiperController](arkts-arkui-arcswipercontroller-c.md) | ArcSwiper容器组件的控制器，可以将此对象绑定至ArcSwiper组件，可以通过它控制翻页。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcSwiperInterface](arkts-arkui-arcswiperinterface-i.md) | Provide an interface for ArcSwiper. |
| [SwiperContentAnimatedTransition](arkts-arkui-swipercontentanimatedtransition-i.md) | ArcSwiper自定义切换动画相关信息。 |
| [SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md) | ArcSwiper自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画视窗内的页面信息，同时，也可以通过调用该对象的finishTransition接口通知ArcSwiper组件页面自定义动画已结束。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ArcDirection](arkts-arkui-arcdirection-e.md) | 弧形方向。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AnimationEndHandler](arkts-arkui-animationendhandler-t.md) | 切换动画结束时的回调。 |
| [AnimationStartHandler](arkts-arkui-animationstarthandler-t.md) | 切换动画开始时的回调。 |
| [FinishAnimationHandler](arkts-arkui-finishanimationhandler-t.md) | 停止播放动画时，告知应用。 |
| [GestureSwipeHandler](arkts-arkui-gestureswipehandler-t.md) | 在页面跟手滑动过程中，逐帧触发的回调。 |
| [IndexChangedHandler](arkts-arkui-indexchangedhandler-t.md) | 当前显示元素的索引变化时，告知应用。 |

