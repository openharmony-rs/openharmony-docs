# TapGesture

Defines TapGesture Component.

## TapGesture

```TypeScript
TapGesture(value?: TapGestureParameters)
```

创建点击手势对象。继承自[GestureInterface&lt;T&gt;](arkts-arkui-gestureinterface-i.md)。

触发点击手势事件的设备类型为键盘或手柄时，事件的[SourceTool](arkts-arkui-sourcetool-e.md)值为Unknown，事件的SourceType值为KEY或JOYSTICK。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TapGestureParameters](arkts-arkui-tapgestureparameters-i.md) | 否 | 点击手势的相关参数。 |

## TapGesture

```TypeScript
TapGesture(event: (event: GestureEvent) => void)
```

点击手势识别成功回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 手势事件回调函数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BaseGestureEvent](arkts-arkui-basegestureevent-i.md) | 基础手势事件类型。继承自[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md) | 基础手势处理器配置参数。 |
| [EventLocationInfo](arkts-arkui-eventlocationinfo-i.md) | 用于点击手势获取点击位置坐标。 |
| [FingerInfo](arkts-arkui-fingerinfo-i.md) | 手指信息类型。 |
| [GestureEvent](arkts-arkui-gestureevent-i.md) | 定义手势的事件信息。继承自[BaseEvent](arkts-arkui-baseevent-i.md)。 |
| [GestureGroupGestureHandlerOptions](arkts-arkui-gesturegroupgesturehandleroptions-i.md) | 手势组处理器配置参数。 |
| [GestureGroupInterface](arkts-arkui-gesturegroupinterface-i.md) | 手势识别组合，即两种及以上手势组合为复合手势，支持顺序识别、并发识别和互斥识别。 |
| [GestureInfo](arkts-arkui-gestureinfo-i.md) | 手势信息类型。 |
| [GestureInterface](arkts-arkui-gestureinterface-i.md) | 定义Gesture接口。 |
| [LongPressGestureEvent](arkts-arkui-longpressgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [LongPressGestureHandlerOptions](arkts-arkui-longpressgesturehandleroptions-i.md) | 长按手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [LongPressGestureInterface](arkts-arkui-longpressgestureinterface-i.md) | 用于触发长按手势事件，触发长按手势的最少手指数为1，默认最短长按时间为500毫秒。可配置duration参数控制最短长按时长。 |
| [PanGestureEvent](arkts-arkui-pangestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [PanGestureHandlerOptions](arkts-arkui-pangesturehandleroptions-i.md) | 滑动手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [PanGestureInterface](arkts-arkui-pangestureinterface-i.md) | 滑动手势事件，当滑动的最小距离达到设定的最小值时触发滑动手势事件。 |
| [PinchGestureEvent](arkts-arkui-pinchgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [PinchGestureHandlerOptions](arkts-arkui-pinchgesturehandleroptions-i.md) | 捏合手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [PinchGestureInterface](arkts-arkui-pinchgestureinterface-i.md) | 用于触发捏合手势，最少需要2指，最多5指，最小识别距离为5vp。在支持鼠标和键盘输入的设备上，通过“Ctrl+鼠标滚轮”也可以触发捏合手势。 |
| [RotationGestureEvent](arkts-arkui-rotationgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [RotationGestureHandlerOptions](arkts-arkui-rotationgesturehandleroptions-i.md) | 旋转手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [RotationGestureInterface](arkts-arkui-rotationgestureinterface-i.md) | 用于触发旋转手势，最少需要2指，最多5指，最小改变度数为1度。该手势不支持通过触控板双指旋转操作触发。 |
| [SwipeGestureEvent](arkts-arkui-swipegestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [SwipeGestureHandlerOptions](arkts-arkui-swipegesturehandleroptions-i.md) | 快滑手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [SwipeGestureInterface](arkts-arkui-swipegestureinterface-i.md) | 用于触发快滑手势，滑动速度需大于速度阈值，默认最小速度为100vp/s。 |
| [TapGestureEvent](arkts-arkui-tapgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [TapGestureHandlerOptions](arkts-arkui-tapgesturehandleroptions-i.md) | 点击手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [TapGestureParameters](arkts-arkui-tapgestureparameters-i.md) | 点击手势参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [GestureType](arkts-arkui-gesturetype-t.md) | Defines the Gesture Type. |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GestureJudgeResult](arkts-arkui-gesturejudgeresult-e.md) | 定义手势竞争结果。 |
| [GestureMask](arkts-arkui-gesturemask-e.md) | 定义是否屏蔽子组件手势。 |
| [GestureMode](arkts-arkui-gesturemode-e.md) | 定义手势组的识别模式。 |
| [GesturePriority](arkts-arkui-gesturepriority-e.md) | 绑定手势的优先级。 |
| [GestureRecognizerState](arkts-arkui-gesturerecognizerstate-e.md) | 定义手势识别器状态。 |
| [PanDirection](arkts-arkui-pandirection-e.md) | 与SwipeDirection不同，PanDirection没有角度限制。 |
| [SwipeDirection](arkts-arkui-swipedirection-e.md) | 定义滑动手势的触发方向。 |

## 示例

```TypeScript
### 示例1（双击手势识别）

该示例通过TapGesture实现了双击手势的识别。


```

```TypeScript
### 示例2（获取单击手势坐标）

该示例通过TapGesture获取单击手势点击位置的坐标。


```

```TypeScript
### 示例3（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取点击位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```
