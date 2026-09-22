# TapGesture

Defines TapGesture Component.

## TapGesture

```TypeScript
TapGesture(value?: TapGestureParameters)
```

创建点击手势对象。继承自[GestureInterface&lt;T&gt;](arkts-arkui-tapgesture-comp-gestureinterface-i.md)。

触发点击手势事件的设备类型为键盘或手柄时，事件的[SourceTool](arkts-arkui-common-comp-sourcetool-e.md)值为Unknown，事件的SourceType值为KEY或JOYSTICK。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TapGestureParameters](arkts-arkui-tapgesture-comp-tapgestureparameters-i.md) | 否 | 点击手势的相关参数。 |

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
| [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md) | 基础手势事件类型。继承自[BaseEvent](arkts-arkui-common-comp-baseevent-i.md)。 |
| [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md) | 基础手势处理器配置参数。 |
| [EventLocationInfo](arkts-arkui-tapgesture-comp-eventlocationinfo-i.md) | 用于点击手势获取点击位置坐标。 |
| [FingerInfo](arkts-arkui-tapgesture-comp-fingerinfo-i.md) | 手指信息类型。 |
| [GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md) | 定义手势的事件信息。继承自[BaseEvent](arkts-arkui-common-comp-baseevent-i.md)。 |
| [GestureGroupGestureHandlerOptions](arkts-arkui-tapgesture-comp-gesturegroupgesturehandleroptions-i.md) | 手势组处理器配置参数。 |
| [GestureGroupInterface](arkts-arkui-tapgesture-comp-gesturegroupinterface-i.md) | 手势识别组合，即两种及以上手势组合为复合手势，支持顺序识别、并发识别和互斥识别。 |
| [GestureInfo](arkts-arkui-tapgesture-comp-gestureinfo-i.md) | 手势信息类型。 |
| [GestureInterface](arkts-arkui-tapgesture-comp-gestureinterface-i.md) | 定义Gesture接口。 |
| [LongPressGestureEvent](arkts-arkui-tapgesture-comp-longpressgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [LongPressGestureHandlerOptions](arkts-arkui-tapgesture-comp-longpressgesturehandleroptions-i.md) | 长按手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)。 |
| [LongPressGestureInterface](arkts-arkui-tapgesture-comp-longpressgestureinterface-i.md) | 用于触发长按手势事件，触发长按手势的最少手指数为1，默认最短长按时间为500毫秒。可配置duration参数控制最短长按时长。 |
| [PanGestureEvent](arkts-arkui-tapgesture-comp-pangestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [PanGestureHandlerOptions](arkts-arkui-tapgesture-comp-pangesturehandleroptions-i.md) | 滑动手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)。 |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) | 滑动手势事件，当滑动的最小距离达到设定的最小值时触发滑动手势事件。 |
| [PinchGestureEvent](arkts-arkui-tapgesture-comp-pinchgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [PinchGestureHandlerOptions](arkts-arkui-tapgesture-comp-pinchgesturehandleroptions-i.md) | 捏合手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)。 |
| [PinchGestureInterface](arkts-arkui-tapgesture-comp-pinchgestureinterface-i.md) | 用于触发捏合手势，最少需要2指，最多5指，最小识别距离为5vp。在支持鼠标和键盘输入的设备上，通过“Ctrl+鼠标滚轮”也可以触发捏合手势。 |
| [RotationGestureEvent](arkts-arkui-tapgesture-comp-rotationgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [RotationGestureHandlerOptions](arkts-arkui-tapgesture-comp-rotationgesturehandleroptions-i.md) | 旋转手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)。 |
| [RotationGestureInterface](arkts-arkui-tapgesture-comp-rotationgestureinterface-i.md) | 用于触发旋转手势，最少需要2指，最多5指，最小改变度数为1度。该手势不支持通过触控板双指旋转操作触发。 |
| [SwipeGestureEvent](arkts-arkui-tapgesture-comp-swipegestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [SwipeGestureHandlerOptions](arkts-arkui-tapgesture-comp-swipegesturehandleroptions-i.md) | 快滑手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)。 |
| [SwipeGestureInterface](arkts-arkui-tapgesture-comp-swipegestureinterface-i.md) | 用于触发快滑手势，滑动速度需大于速度阈值，默认最小速度为100vp/s。 |
| [TapGestureEvent](arkts-arkui-tapgesture-comp-tapgestureevent-i.md) | 继承自[BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。 |
| [TapGestureHandlerOptions](arkts-arkui-tapgesture-comp-tapgesturehandleroptions-i.md) | 点击手势处理器配置参数。继承自[BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)。 |
| [TapGestureParameters](arkts-arkui-tapgesture-comp-tapgestureparameters-i.md) | 点击手势参数。继承自[BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [GestureType](arkts-arkui-tapgesture-comp-gesturetype-t.md) | Defines the Gesture Type. |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GestureJudgeResult](arkts-arkui-tapgesture-comp-gesturejudgeresult-e.md) | 定义手势竞争结果。 |
| [GestureMask](arkts-arkui-tapgesture-comp-gesturemask-e.md) | 定义是否屏蔽子组件手势。 |
| [GestureMode](arkts-arkui-tapgesture-comp-gesturemode-e.md) | 定义手势组的识别模式。 |
| [GesturePriority](arkts-arkui-tapgesture-comp-gesturepriority-e.md) | 绑定手势的优先级。 |
| [GestureRecognizerState](arkts-arkui-tapgesture-comp-gesturerecognizerstate-e.md) | 定义手势识别器状态。 |
| [PanDirection](arkts-arkui-tapgesture-comp-pandirection-e.md) | 与SwipeDirection不同，PanDirection没有角度限制。 |
| [SwipeDirection](arkts-arkui-tapgesture-comp-swipedirection-e.md) | 定义滑动手势的触发方向。 |

## 示例

### 示例1（双击手势识别）

该示例通过TapGesture实现了双击手势的识别。



```TypeScript
// xxx.ets
@Entry
@Component
struct TapGestureExample {
  @State value: string = '';

  build() {
    Column() {
      // 单指双击文本触发手势事件
      Text('Click twice').fontSize(28)
        .gesture(
        TapGesture({ count: 2 })
          .onAction((event: GestureEvent) => {
            if (event) {
              this.value = JSON.stringify(event.fingerList[0]);
            }
          })
        );
      Text(this.value);
    }
    .height(300)
    .width(300)
    .padding(20)
    .border({ width: 3 })
    .margin(30);
  }
}
```

### 示例2（获取单击手势坐标）

该示例通过TapGesture获取单击手势点击位置的坐标。



```TypeScript
// xxx.ets
@Entry
@Component
struct TapGestureExample {

  build() {
    Column() {
      Text('Click Once').fontSize(28)
        .gesture(
          TapGesture({ count: 1, fingers: 1 })
            .onAction((event: GestureEvent | undefined) => {
              if (event) {
                console.info(`x = ${JSON.stringify(event.tapLocation?.x)}`);
                console.info(`y = ${JSON.stringify(event.tapLocation?.y)}`);
                console.info(`windowX = ${JSON.stringify(event.tapLocation?.windowX)}`);
                console.info(`windowY = ${JSON.stringify(event.tapLocation?.windowY)}`);
                console.info(`displayX = ${JSON.stringify(event.tapLocation?.displayX)}`);
                console.info(`displayY = ${JSON.stringify(event.tapLocation?.displayY)}`);
                // 从API version 23开始，新增globalDisplayX和globalDisplayY属性。
                console.info(`globalDisplayX = ${JSON.stringify(event.tapLocation?.globalDisplayX)}`);
                console.info(`globalDisplayY = ${JSON.stringify(event.tapLocation?.globalDisplayY)}`);
              }
            })
        );
    }
    .height(200)
    .width(300)
    .padding(20)
    .border({ width: 3 })
    .margin(30)
  }
}
```

### 示例3（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取点击位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。

```TypeScript
// xxx.ets
@Entry
@Component
struct GetCurrentLocalPositionExample {
  @State positionText: string = '';
  @State textOffsetY: number = 0;

  build() {
    Column() {
      Button('点击获取点击位置相对于当前组件实时位置左上角的坐标').translate({ y: this.textOffsetY })
        .gesture(
          TapGesture({ count: 1 })
            .onAction((event: GestureEvent) => {
              if (event) {
                // 移动组件后延迟获取点击位置相对于组件实时位置左上角的坐标。
                this.textOffsetY = -200;
                setTimeout(() => {
                  let localPos: Coordinate2D | undefined = event?.tapLocation?.getCurrentLocalPosition?.();
                  this.positionText = `相对于当前组件实时位置左上角的坐标:\n  x: ${localPos?.x ?? 0}\n  y: ${localPos?.y ?? 0}`;
                }, 2000);
              }
            })
        );

      Text(this.positionText);
    }.width('100%');
  }
}
```
