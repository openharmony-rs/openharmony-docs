# SwipeGestureInterface

用于触发快滑手势，滑动速度需大于速度阈值，默认最小速度为100vp/s。

**继承/实现关系：** SwipeGestureInterface extends [GestureInterface<SwipeGestureInterface>](GestureInterface<SwipeGestureInterface>)

**起始版本：** 8

<!--Device-unnamed-interface SwipeGestureInterface extends GestureInterface<SwipeGestureInterface>--><!--Device-unnamed-interface SwipeGestureInterface extends GestureInterface<SwipeGestureInterface>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
(value?: { fingers?: number; direction?: SwipeDirection; speed?: number }): SwipeGestureInterface
```

继承自[GestureInterface<T>](arkts-arkui-gestureinterface-i.md)，设置快滑手势事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeGestureInterface-(value?: { fingers?: number; direction?: SwipeDirection; speed?: number }): SwipeGestureInterface--><!--Device-SwipeGestureInterface-(value?: { fingers?: number; direction?: SwipeDirection; speed?: number }): SwipeGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { fingers?: number; direction?: SwipeDirection; speed?: number } | 否 | 设置快滑事件参数。<br> - fingers：触发快滑的最少手指数。<br/>默认值：1 <br/>取值范围：[1, 10]<br> - direction：触发快滑手势的滑动方向。<br/>默认值：SwipeDirection.All<br> - speed：识别快滑的最小速度。<br/>默认值：100VP/s <br/>取值范围：(0, +∞) <br/>**说明：** <br/>当滑动速度的值小于等于0时，会被转化为默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SwipeGestureInterface](arkts-arkui-swipegestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

<a id="constructor-1"></a>
## constructor

```TypeScript
(options?: SwipeGestureHandlerOptions): SwipeGestureInterface
```

设置快滑手势事件。与[SwipeGesture](arkts-arkui-swipegestureinterface-i.md))}相比，options参数新增了isFingerCountLimited，表示是否检查触摸屏幕的手指数量。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeGestureInterface-(options?: SwipeGestureHandlerOptions): SwipeGestureInterface--><!--Device-SwipeGestureInterface-(options?: SwipeGestureHandlerOptions): SwipeGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SwipeGestureHandlerOptions](arkts-arkui-swipegesturehandleroptions-i.md) | 否 | 快滑事件处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SwipeGestureInterface](arkts-arkui-swipegestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="onaction"></a>
## onAction

```TypeScript
onAction(event: (event: GestureEvent) => void): SwipeGestureInterface
```

Swipe手势识别成功时触发回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwipeGestureInterface-onAction(event: (event: GestureEvent) => void): SwipeGestureInterface--><!--Device-SwipeGestureInterface-onAction(event: (event: GestureEvent) => void): SwipeGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SwipeGestureInterface](arkts-arkui-swipegestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

