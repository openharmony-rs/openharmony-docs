# tabs

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [Tabs](arkts-na-tabs-tabs-f.md#tabs) | 定义Tabs组件 |

### 类

| 名称 | 说明 |
| --- | --- |
| [TabsController](arkts-na-tabs-tabscontroller-c.md) | Tabs组件的控制器，用于控制Tabs组件进行页签切换。不支持一个TabsController控制多个Tabs组件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BarGridColumnOptions](arkts-na-tabs-bargridcolumnoptions-i.md) | TabBar栅格化方式设置的对象，包括栅格模式下的column边距和间隔，以及小、中、大屏下，页签占用的columns数量。 |
| [ScrollableBarModeOptions](arkts-na-tabs-scrollablebarmodeoptions-i.md) | Scrollable模式下的TabBar的布局样式对象。 |
| [TabContentAnimatedTransition](arkts-na-tabs-tabcontentanimatedtransition-i.md) | Tabs自定义切换动画相关信息。 |
| [TabContentTransitionProxy](arkts-na-tabs-tabcontenttransitionproxy-i.md) | Tabs自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画的起始和目标页面信息，同时，也可以通过调用该对象的finishTransition接口通知Tabs组件自定义动画已结束。 |
| [TabsAnimationEvent](arkts-na-tabs-tabsanimationevent-i.md) | Tabs组件动画相关信息集合。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AnimationMode](arkts-na-tabs-animationmode-e.md) | 点击[TabBar](../../../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md#tabbar)页签时切换TabContent的动画形式枚举。 |
| [BarMode](arkts-na-tabs-barmode-e.md) | TabBar布局模式枚举。 |
| [BarPosition](arkts-na-tabs-barposition-e.md) | Tabs页签位置枚举。 |
| [LayoutStyle](arkts-na-tabs-layoutstyle-e.md) | Scrollable模式下不滚动时的页签排布方式枚举。 |
| [TabsCacheMode](arkts-na-tabs-tabscachemode-e.md) | 子组件的缓存模式。 |
| [TabsNestedScrollMode](arkts-na-tabs-tabsnestedscrollmode-e.md) | Tabs组件和父组件的嵌套滚动模式枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnTabsAnimationEndCallback](arkts-na-ontabsanimationendcallback-t.md) | 切换动画结束时触发的回调。 |
| [OnTabsAnimationStartCallback](arkts-na-ontabsanimationstartcallback-t.md) | 切换动画开始时触发的回调。 |
| [OnTabsContentDidScrollCallback](arkts-na-ontabscontentdidscrollcallback-t.md) | Tabs滑动时触发的回调。 |
| [OnTabsContentWillChangeCallback](arkts-na-ontabscontentwillchangecallback-t.md) | 自定义Tabs页面切换拦截事件能力，新页面即将显示时触发的回调。 |
| [OnTabsGestureSwipeCallback](arkts-na-ontabsgestureswipecallback-t.md) | 在页面跟手滑动过程中，逐帧触发的回调。 |
| [TabsCustomContentTransitionCallback](arkts-na-tabscustomcontenttransitioncallback-t.md) | 自定义Tabs页面切换动画开始时触发的回调。 |

