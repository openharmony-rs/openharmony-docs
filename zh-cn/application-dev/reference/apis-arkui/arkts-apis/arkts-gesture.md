# gesture

定义手势竞争结果。

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [GestureControl](arkts-arkui-gesturecontrol-n.md) | 定义手势竞争结果。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [EventTargetInfo](arkts-arkui-eventtargetinfo-c.md) | 手势识别器对应组件的信息。 |
| [GestureGroupHandler](arkts-arkui-gesturegrouphandler-c.md) | 手势组处理器对象类型。 |
| [GestureHandler](arkts-arkui-gesturehandler-c.md) | 手势处理器的基础类型。 |
| [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md) | 手势识别器对象。 |
| [LongPressGestureHandler](arkts-arkui-longpressgesturehandler-c.md) | 长按手势处理器对象类型。 |
| [LongPressRecognizer](arkts-arkui-longpressrecognizer-c.md) | 长按手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)。 |
| [PanGestureHandler](arkts-arkui-pangesturehandler-c.md) | 滑动手势处理器对象类型。 |
| [PanGestureOptions](arkts-arkui-pangestureoptions-c.md) | 定义PanGesture配置参数选项。 |
| [PanRecognizer](arkts-arkui-panrecognizer-c.md) | 手势识别器对象。 |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | 捏合手势处理器对象类型。 |
| [PinchRecognizer](arkts-arkui-pinchrecognizer-c.md) | 捏合手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)。 |
| [RotationGestureHandler](arkts-arkui-rotationgesturehandler-c.md) | 旋转手势处理器对象类型。 |
| [RotationRecognizer](arkts-arkui-rotationrecognizer-c.md) | 旋转手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)。 |
| [ScrollableTargetInfo](arkts-arkui-scrollabletargetinfo-c.md) | 手势识别器对应的滚动类容器组件的信息，继承于[EventTargetInfo](arkts-arkui-eventtargetinfo-c.md)。 |
| [SwipeGestureHandler](arkts-arkui-swipegesturehandler-c.md) | 快滑手势处理器对象类型。 |
| [SwipeRecognizer](arkts-arkui-swiperecognizer-c.md) | 快滑手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)。 |
| [TapGestureHandler](arkts-arkui-tapgesturehandler-c.md) | 点击手势处理器对象类型。 |
| [TapRecognizer](arkts-arkui-taprecognizer-c.md) | 点击手势识别器对象，继承自[GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)。 |
| [TouchRecognizer](arkts-arkui-touchrecognizer-c.md) | 触摸识别器对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BaseGestureEvent](arkts-arkui-basegestureevent-i.md) | 基础手势事件类型。继承自[BaseEvent](../arkts-components/arkts-arkui-baseevent-i.md)。 |
| [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md) | 基础手势处理器配置参数。 |
| [EventLocationInfo](arkts-arkui-eventlocationinfo-i.md) | 用于点击手势获取点击位置坐标。 |
| [FingerInfo](arkts-arkui-fingerinfo-i.md) | 手指信息类型。 |
| [GestureEvent](arkts-arkui-gestureevent-i.md) | 定义手势的事件信息。继承自[BaseEvent](../arkts-components/arkts-arkui-baseevent-i.md)。 |
| [GestureGroupGestureHandlerOptions](arkts-arkui-gesturegroupgesturehandleroptions-i.md) | 手势组处理器配置参数。 |
| [GestureGroupInterface](arkts-arkui-gesturegroupinterface-i.md) | 手势识别组合，即两种及以上手势组合为复合手势，支持顺序识别、并发识别和互斥识别。 |
| [GestureInfo](arkts-arkui-gestureinfo-i.md) | 手势信息类型。 |
| [GestureInterface](arkts-arkui-gestureinterface-i.md) | 定义Gesture接口。 |
| [LongPressGestureEvent](arkts-arkui-longpressgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](../arkts-components/arkts-arkui-commonmethod-c.md#ongesturejudgebegin-1)的event参数来传递。 |
| [LongPressGestureHandlerOptions](arkts-arkui-longpressgesturehandleroptions-i.md) | 长按手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [LongPressGestureInterface](arkts-arkui-longpressgestureinterface-i.md) | 用于触发长按手势事件，触发长按手势的最少手指数为1，默认最短长按时间为500毫秒。可配置duration参数控制最短长按时长。 |
| [PanGestureEvent](arkts-arkui-pangestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](../arkts-components/arkts-arkui-commonmethod-c.md#ongesturejudgebegin-1)的event参数来传递。 |
| [PanGestureHandlerOptions](arkts-arkui-pangesturehandleroptions-i.md) | 滑动手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [PanGestureInterface](arkts-arkui-pangestureinterface-i.md) | 滑动手势事件，当滑动的最小距离达到设定的最小值时触发滑动手势事件。 |
| [PinchGestureEvent](arkts-arkui-pinchgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](../arkts-components/arkts-arkui-commonmethod-c.md#ongesturejudgebegin-1)的event参数来传递。 |
| [PinchGestureHandlerOptions](arkts-arkui-pinchgesturehandleroptions-i.md) | 捏合手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [PinchGestureInterface](arkts-arkui-pinchgestureinterface-i.md) | 用于触发捏合手势，最少需要2指，最多5指，最小识别距离为5vp。在支持鼠标和键盘输入的设备上，通过“Ctrl+鼠标滚轮”也可以触发捏合手势。 |
| [RotationGestureEvent](arkts-arkui-rotationgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](../arkts-components/arkts-arkui-commonmethod-c.md#ongesturejudgebegin-1)的event参数来传递。 |
| [RotationGestureHandlerOptions](arkts-arkui-rotationgesturehandleroptions-i.md) | 旋转手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [RotationGestureInterface](arkts-arkui-rotationgestureinterface-i.md) | 用于触发旋转手势，最少需要2指，最多5指，最小改变度数为1度。该手势不支持通过触控板双指旋转操作触发。 |
| [SwipeGestureEvent](arkts-arkui-swipegestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](../arkts-components/arkts-arkui-commonmethod-c.md#ongesturejudgebegin-1)的event参数来传递。 |
| [SwipeGestureHandlerOptions](arkts-arkui-swipegesturehandleroptions-i.md) | 快滑手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [SwipeGestureInterface](arkts-arkui-swipegestureinterface-i.md) | 用于触发快滑手势，滑动速度需大于速度阈值，默认最小速度为100vp/s。 |
| [TapGestureEvent](arkts-arkui-tapgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](../arkts-components/arkts-arkui-commonmethod-c.md#ongesturejudgebegin-1)的event参数来传递。 |
| [TapGestureHandlerOptions](arkts-arkui-tapgesturehandleroptions-i.md) | 点击手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。 |
| [TapGestureInterface](arkts-arkui-tapgestureinterface-i.md) | 支持单击、双击和多次点击事件的识别。 |
| [TapGestureParameters](arkts-arkui-tapgestureparameters-i.md) | 点击手势参数。继承自[BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)。  @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |

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

### 类型

| 名称 | 说明 |
| --- | --- |
| [GestureType](arkts-arkui-gesturetype-t.md) | Defines the Gesture Type. |

### 常量

| 名称 | 说明 |
| --- | --- |
| [GestureGroup](arkts-arkui-gesture-con.md#gesturegroup) | Defines GestureGroup Component. |
| [LongPressGesture](arkts-arkui-gesture-con.md#longpressgesture) | Defines LongPressGesture Component. |
| [PanGesture](arkts-arkui-gesture-con.md#pangesture) | Defines PanGesture Component. |
| [PinchGesture](arkts-arkui-gesture-con.md#pinchgesture) | Defines PinchGesture Component. |
| [RotationGesture](arkts-arkui-gesture-con.md#rotationgesture) | Defines RotationGesture Component. |
| [SwipeGesture](arkts-arkui-gesture-con.md#swipegesture) | Defines SwipeGesture Component. |
| [TapGesture](arkts-arkui-gesture-con.md#tapgesture) | Defines TapGesture Component. |

