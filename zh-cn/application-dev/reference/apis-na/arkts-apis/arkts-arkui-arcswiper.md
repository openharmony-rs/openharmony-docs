# @ohos.arkui.ArcSwiper

## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-na-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |
| [ArcSwiperController](arkts-na-arkui-arcswiper-arcswipercontroller-c.md) | ArcSwiper容器组件的控制器，可以将此对象绑定至ArcSwiper组件，实现控制ArcSwiper翻页等功能。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-na-arkui-arcswiper-arcswiperattribute-i.md) | 除支持通用属性外，还支持以下属性，不支持Menu控制。 |
| [ArcSwiperContentAnimatedTransition](arkts-na-arkui-arcswiper-arcswipercontentanimatedtransition-i.md) | ArcSwiper自定义切换动画相关信息。 |
| [ArcSwiperContentTransitionProxy](arkts-na-arkui-arcswiper-arcswipercontenttransitionproxy-i.md) | ArcSwiper自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画视窗内的页面信息，同时，也可以通过调用该对象的finishTransition接口通知ArcSwiper组件页面自定义动画已结束 。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ArcDirection](arkts-na-arkui-arcswiper-arcdirection-e.md) | 弧形方向。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AnimationEndHandler](arkts-na-animationendhandler-t.md) | 切换动画结束时的回调。 |
| [AnimationStartHandler](arkts-na-animationstarthandler-t.md) | 切换动画开始时的回调。 |
| [FinishAnimationHandler](arkts-na-finishanimationhandler-t.md) | 停止播放动画时，告知应用。 |
| [GestureSwipeHandler](arkts-na-gestureswipehandler-t.md) | 在页面跟手滑动过程中，逐帧触发的回调。 |
| [IndexChangedHandler](arkts-na-indexchangedhandler-t.md) | 当前显示元素的索引变化时，告知应用。 |

