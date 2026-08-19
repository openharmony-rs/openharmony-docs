# SwipeGesture

用于触发快滑手势，滑动速度需大于速度阈值，默认最小速度为100vp/s。

**继承/实现关系：** SwipeGesture extends [Gesture](arkts-arkui-gesture-gesture-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class SwipeGesture--><!--Device-unnamed-export declare class SwipeGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate(factory: () => SwipeGesture, value?: SwipeGestureHandlerOptions): SwipeGesture
```

设置快滑手势事件。继承自[Gesture](arkts-arkui-gesture-gesture-c.md)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeGesture-static $_instantiate(factory: () => SwipeGesture, value?: SwipeGestureHandlerOptions): SwipeGesture--><!--Device-SwipeGesture-static $_instantiate(factory: () => SwipeGesture, value?: SwipeGestureHandlerOptions): SwipeGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | () =&gt; SwipeGesture | 是 |  |
| value | [SwipeGestureHandlerOptions](arkts-arkui-gesture-swipegesturehandleroptions-i.md) | 否 | 快滑事件处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SwipeGesture](arkts-arkui-gesture-swipegesture-c.md) |  |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): this
```

Swipe手势识别成功时触发回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeGesture-onAction(event: Callback<GestureEvent>): this--><!--Device-SwipeGesture-onAction(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

