# Custom Gesture Judgment
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

You can use the custom gesture judgment APIs to specify whether to respond to specific gestures when they are being recognized.

>  **NOTE**
>
>  This feature is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.


## onGestureJudgeBegin

onGestureJudgeBegin(callback: (gestureInfo: GestureInfo, event: BaseGestureEvent) => GestureJudgeResult): T

Binds a custom gesture determination callback to the component. When the gesture is about to succeed, the user-defined callback is triggered to obtain the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name       | Type                   | Mandatory | Description                         |
| ---------- | -------------------------- | ------- | ----------------------------- |
| callback      | (gestureInfo: [GestureInfo](./ts-gesture-common.md#gestureinfo11), event: [BaseGestureEvent](./ts-gesture-common.md#basegestureevent11)) => [GestureJudgeResult](./ts-gesture-common.md#gesturejudgeresult11) | Yes    | Custom gesture judgment callback. When the gesture is about to succeed, the user-defined callback is triggered to obtain the result.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## BaseEvent<sup>8+</sup>

Basic event type.

### Properties

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type                                      | Read-Only| Optional| Description        |
| ---------| ---------------------------------------- | ---- | ---- | -----------|
| target   | [EventTarget](ts-universal-events-click.md#eventtarget8) | No| No| Object that triggers the gesture event.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| timestamp| number | No| No| Timestamp of the event. It is the interval between the time when the event is triggered and the time when the system starts.<br>Unit: ns<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| source   | [SourceType](ts-gesture-settings.md#sourcetype8) | No| No| Type of the event input device.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| pressure<sup>9+</sup> | number | No| No| Press pressure.<br>Default value: **0**<br>Value range: [0, 1], typical value 0.913168, where higher values indicate greater pressure. On some devices, the return value may be greater than 1 due to different hardware parameter configurations.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| tiltX<sup>9+</sup> | number | No| No| Angle between the projection of the stylus on the device plane and the x-axis.<br>Default value: **0**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| tiltY<sup>9+</sup> | number | No| No|Angle between the projection of the stylus on the device plane and the y-axis.<br>Default value: **0**<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| rollAngle<sup>17+</sup> | number | No| Yes| Angle between the stylus and the device's surface.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 17.<br>**Atomic service API**: This API can be used in atomic services since API version 17.|
| sourceTool<sup>9+</sup> | [SourceTool](ts-gesture-settings.md#sourcetool9) | No| No| Event input source type.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 9.<br>**Atomic service API**: This API can be used in atomic services since API version 11. |
| axisHorizontal<sup>12+</sup> | number | No| Yes| Horizontal axis value.<br>Default value: **0**<br>**NOTE**<br>This value is available only when the pan gesture is triggered by mouse wheel scrolling or two-finger touchpad sliding, or when the pinch gesture is triggered by Ctrl + mouse wheel scrolling.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| axisVertical<sup>12+</sup> | number | No| Yes| Vertical axis value.<br>Default value: **0**<br>**NOTE**<br>This value is available only when the pan gesture is triggered by mouse wheel scrolling or two-finger touchpad sliding, or when the pinch gesture is triggered by Ctrl + mouse wheel scrolling.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| axisPinch<sup>21+</sup> | number | No| Yes|  Two-finger pinch scaling ratio.<br>Default value: **0**<br>**NOTE**<br>This value is available only when a pinch gesture is triggered by a two-finger scaling operation on a touchpad or during axis events.<br>In other scenarios, the default value is returned. The scaling ratio represents the ratio of the current two-finger distance to the initial two-finger distance when first pressed during a pinch gesture.<br>Value range: [0, +∞).<br>**Widget capability**: This API can be used in ArkTS widgets since API version 21.<br>**Atomic service API**: This API can be used in atomic services since API version 21.|
| deviceId<sup>12+</sup> | number | No| Yes| ID of the input device that triggers the event.<br>Default value: **0**<br>Value range: [0, +∞).<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| targetDisplayId<sup>15+</sup> | number | No| Yes| ID of the screen where the event occurs.<br>Default value: **0**<br>Value range: [0, +∞).<br>**Atomic service API**: This API can be used in atomic services since API version 15.|

### getModifierKeyState<sup>12+</sup>

getModifierKeyState?(keys: Array\<string>): boolean

Obtains the pressed status of modifier keys. For details about the error message, see the following error codes. The Ctrl, Alt, and Shift keys are supported.

>  **NOTE**
>
> This API is not supported in stylus scenarios.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| keys  | Array&lt;string&gt; | Yes  | Modifier key list.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Pressed status of modifier keys. Returns **true** if all modifier keys are pressed; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. 2. Parameter verification failed. |

## Example

### Example 1: Implementing Custom Gesture Judgment

This example demonstrates how to implement custom judgment for long press, swipe, and pan gestures using [onGestureJudgeBegin](#ongesturejudgebegin). Starting from API version 21, **axisPinch** property of [BaseEvent](#baseevent8) can be used to obtain the two-finger pinch scale ratio.

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State message: string = '';

  build() {
    Column() {
      Row({ space: 20 }) {
        Text(this.message).width(200).height(80).backgroundColor(Color.Pink)
          .fontSize(25)
      }.margin(20)
    }
    .width('100%')
    .height(200)
    .borderWidth(2)
    .onDragStart(() => {
      this.message = 'drag'
      console.info("Drag start.")
    })
    .gesture(
      TapGesture()
        .tag("tap1")// Tag for the tap gesture.
        .onAction(() => {
          this.message = 'tap1'
        })
    )
    .gesture(
      LongPressGesture()
        .tag("longPress1")// Tag for the long press gesture.
        .onAction(() => {
          this.message = 'longPress'
        })
    )
    .gesture(
      SwipeGesture()
        .tag("swipe1")// Tag for the swipe gesture.
        .onAction(() => {
          this.message = 'swipe1'
        })
    )
    .gesture(
      PanGesture()
        .tag("pan1")// Tag for the pan gesture.
        .onActionStart(() => {
          this.message = 'pan1'
        })
    )
    .gesture(
      PinchGesture()
        .tag("pinch1")// Tag for the pinch gesture.
        .onActionStart(() => {
          this.message = 'pinch1'
        })
    )
    .onGestureJudgeBegin((gestureInfo: GestureInfo, event: BaseGestureEvent) => {
      // If the gesture type is a long press gesture, convert the event to a long press gesture event.
      if (gestureInfo.type == GestureControl.GestureType.LONG_PRESS_GESTURE) {
        let longPressEvent = event as LongPressGestureEvent;
        console.info(`repeat ${longPressEvent.repeat}`)
      }
      // If the gesture type is a swipe gesture, convert the event to a swipe event.
      if (gestureInfo.type == GestureControl.GestureType.SWIPE_GESTURE) {
        let swipeEvent = event as SwipeGestureEvent;
        console.info(`angle ${swipeEvent.angle}`)
      }
      // If the gesture type is a swipe gesture, convert the event to a swipe gesture event.
      if (gestureInfo.type == GestureControl.GestureType.PAN_GESTURE) {
        let panEvent = event as PanGestureEvent;
        console.info(`velocity ${panEvent.velocity}`)
      }
      // If the gesture type is a pinch gesture, convert the event to a pinch event.
      if (gestureInfo.type == GestureControl.GestureType.PINCH_GESTURE) {
        let pinchEvent = event as PinchGestureEvent;
        console.info(`axisPinch ${pinchEvent.axisPinch}`)
      }
      // Custom criteria
      if (gestureInfo.type == GestureControl.GestureType.DRAG) {
        // If GestureJudgeResult.REJECT is returned, the pan gesture recognition fails.
        return GestureJudgeResult.REJECT;
      } else if (gestureInfo.tag === 'longPress1' && event.fingerList.length > 0 && event.fingerList[0].localY < 100) {
        // If GestureJudgeResult.CONTINUE is returned, the system recognition result is retained.
        return GestureJudgeResult.CONTINUE;
      }
      return GestureJudgeResult.CONTINUE;
    })
  }
}
```
![gestures1](figures/gestures1.gif)

### Example 2: Implementing Custom Area Gesture Judgment

This example demonstrates how to use **onGestureJudgeBegin** to determine whether to respond to long press and pan gestures based on the area.

```ts
// xxx.ets
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller()
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Scroll(this.scroller) {
      Column({ space: 8 }) {
        Text("The upper red area is bound to the long press gesture, and the lower blue area is bound to a drag gesture. If a pan is performed after a long press in the upper red area, the area only responds to the long press. In the same case, the lower blue area only responds to the drag.")
          .width('100%')
          .fontSize(20)
          .fontColor('0xffdd00')
          .backgroundColor(0xeeddaa00)
        Stack({ alignContent: Alignment.Center }) {
          Column() {
            // Simulate the upper and lower half areas.
            Stack().width('200vp').height('100vp').backgroundColor(Color.Red)
            Stack().width('200vp').height('100vp').backgroundColor(Color.Blue)
          }.width('200vp').height('200vp')

          // The lower part of the Stack component is the image area bound to the pan gesture.
          Image($r('sys.media.ohos_app_icon'))
            .draggable(true)
            .onDragStart(() => {
              this.promptAction.showToast({ message: "When the blue area is dragged, the image responds." })
            })
            .width('200vp').height('200vp')
          // The upper part of the Stack component is the floating area bound to the long press gesture.
          Stack() {
          }
          .width('200vp')
          .height('200vp')
          .hitTestBehavior(HitTestMode.Transparent)
          .onGestureJudgeBegin((gestureInfo: GestureInfo, event: BaseGestureEvent) => {
            // Check whether the tag of gestureInfo has a value.
            if (gestureInfo.tag) {
              console.info(`gestureInfo tag ${gestureInfo.tag.toString()}`)
            }
            console.info(`gestureInfo Type ${gestureInfo.type.toString()}`);
            console.info(`isSystemGesture ${gestureInfo.isSystemGesture}`);
            console.info(`zqs pressure ${event.pressure}\nfingerList.length ${event.fingerList.length}\ntimeStamp ${event.timestamp}\nsourceType ${event.source.toString()}\n` +
              `titleX ${event.tiltX}\ntitleY ${event.tiltY}\nrollAngle ${event.rollAngle}\nsourcePool ${event.sourceTool.toString()}`);
            // If the gesture is a long press gesture, check whether the touch position is in the upper half area.
            if (gestureInfo.type == GestureControl.GestureType.LONG_PRESS_GESTURE) {
              if (event.fingerList.length > 0 && event.fingerList[0].localY < 100) {
                return GestureJudgeResult.CONTINUE
              } else {
                return GestureJudgeResult.REJECT
              }
            }
            return GestureJudgeResult.CONTINUE
          })
          .gesture(GestureGroup(GestureMode.Parallel,
            LongPressGesture()
              .onAction((event: GestureEvent) => {
                this.promptAction.showToast({ message: "Long-press the upper red area. The red area responds." })
              })
              .tag("tap111")
          ))

        }.width('100%')
      }.width('100%')
    }
  }
}
```
![gestures2](figures/gestures2.gif)

### Example 3: Implementing Real-time Monitoring of Active Touch Points in Gestures

This example demonstrates real-time monitoring of active touch points participating in gestures, including their count, IDs, and coordinates, by configuring **fingerInfos**.

```ts
// xxx.ets
@Entry
@Component
struct GestureDetectorExample {
  @State message: string = 'Touch area'
  @State fingerCount: number = 0
  @State fingerDetails: string = ''

  build() {
    Column() {
      // Information display area
      Column() {
        Text(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)

        Text(`Active touch points: ${this.fingerCount}`)
          .fontSize(16)
          .margin({ top: 8 })


        Text(this.fingerDetails)
          .fontSize(14)
          .margin({ top: 8 })
      }
      .padding(10)
      .border({ width: 1, color: Color.Gray })

      // Gesture detection area
      Column()
        .width('90%')
        .height(200)
        .margin(20)
        .border({ width: 2, color: Color.Black })
        .gesture(
          GestureGroup(GestureMode.Exclusive,
            TapGesture()
              .onAction(() => {
                this.message = 'Click event'
              }),
            LongPressGesture()
              .onAction(() => {
                this.message = 'Long press event'
              }),
            PanGesture()
              .onActionStart(() => {
                this.message = 'Drag started'
              })
              .onActionUpdate(() => {
                this.message = 'Dragging...'
              })
              .onActionEnd(() => {
                this.message = 'Drag ended'
                this.fingerCount = 0
                this.fingerDetails = ''
              })
          )
        )
        .onGestureJudgeBegin((gestureInfo: GestureInfo, event: BaseGestureEvent) => {
          // Access fingerInfos data.
          if (event?.fingerInfos) {
            this.fingerCount = event.fingerInfos.length
            this.fingerDetails = event.fingerInfos.map(finger =>
            `ID: ${finger.id}: (${finger.localX.toFixed(1)}, ${finger.localY.toFixed(1)})`
            ).join('\n')
            console.info(`Touch point data: ${JSON.stringify(event.fingerInfos)}`)
          }
          if (this.fingerCount > 2) {
            return GestureJudgeResult.REJECT
          }
          return GestureJudgeResult.CONTINUE
        })
    }
    .width('100%')
    .height('100%')
    .padding(10)
  }
}

```

