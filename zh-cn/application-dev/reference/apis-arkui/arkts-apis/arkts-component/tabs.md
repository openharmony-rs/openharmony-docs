# component/tabs

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [Tabs](tabs-tabs-f.md#tabs) | 定义Tabs组件 |

### 类

| 名称 | 说明 |
| --- | --- |
| [TabsController](tabs-tabscontroller-c.md) | Tabs组件的控制器，用于控制Tabs组件进行页签切换。不支持一个TabsController控制多个Tabs组件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BarGridColumnOptions](tabs-bargridcolumnoptions-i.md) | TabBar栅格化方式设置的对象，包括栅格模式下的column边距和间隔，以及小、中、大屏下，页签占用的columns数量。 |
| [ScrollableBarModeOptions](tabs-scrollablebarmodeoptions-i.md) | Scrollable模式下的TabBar的布局样式对象。 |
| [TabContentAnimatedTransition](tabs-tabcontentanimatedtransition-i.md) | Tabs自定义切换动画相关信息。 |
| [TabContentTransitionProxy](tabs-tabcontenttransitionproxy-i.md) | Tabs自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画的起始和目标页面信息，同时，也可以通过调用该对象的finishTransition接口通知Tabs组件自定义动画已结束。 |
| [TabsAnimationEvent](tabs-tabsanimationevent-i.md) | Tabs组件动画相关信息集合。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AnimationMode](tabs-animationmode-e.md) | 点击\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_页签时切换TabContent的动画形式枚举。 |
| [BarMode](tabs-barmode-e.md) | TabBar布局模式枚举。 |
| [BarPosition](tabs-barposition-e.md) | Tabs页签位置枚举。 |
| [LayoutStyle](tabs-layoutstyle-e.md) | [Scrollable]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_模式下不滚动时的页签排布方式枚举。 |
| [TabsCacheMode](tabs-tabscachemode-e.md) | 子组件的缓存模式。 |
| [TabsNestedScrollMode](tabs-tabsnestedscrollmode-e.md) | Tabs组件和父组件的嵌套滚动模式枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnTabsAnimationEndCallback](arkts-arkui-ontabsanimationendcallback-t.md) | 切换动画结束时触发的回调。 |
| [OnTabsAnimationStartCallback](arkts-arkui-ontabsanimationstartcallback-t.md) | 切换动画开始时触发的回调。 |
| [OnTabsContentDidScrollCallback](arkts-arkui-ontabscontentdidscrollcallback-t.md) | Tabs滑动时触发的回调。 |
| [OnTabsContentWillChangeCallback](arkts-arkui-ontabscontentwillchangecallback-t.md) | 自定义Tabs页面切换拦截事件能力，新页面即将显示时触发的回调。 |
| [OnTabsGestureSwipeCallback](arkts-arkui-ontabsgestureswipecallback-t.md) | 在页面跟手滑动过程中，逐帧触发的回调。 |
| [TabsCustomContentTransitionCallback](arkts-arkui-tabscustomcontenttransitioncallback-t.md) | 自定义Tabs页面切换动画开始时触发的回调。 |

