# Single Gesture
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

## Click Event (onClick)

Click is a common gesture, which can be easily implemented using the [onClick](../reference/apis-arkui/arkui-ts/ts-universal-events-click.md#onclick) API. Although it is called an event, it is actually a basic gesture type, which is equivalent to TapGesture with count set to 1, that is, the click gesture.

onClick is the same as other gesture types and also participates in processes such as hit testing and response chain collection. You can implement [intervention in gesture processing](./arkts-interaction-development-guide-support-gesture.md#intervention-in-gesture-processing) to dynamically decide onClick responses.


<!-- @[click_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/EventProject/entry/src/main/ets/pages/singlegesture/OnClickGesture.ets) -->

``` TypeScript
@Entry
@Component
export struct OnClickGesture {
  private judgeCount: number = 0

  increaseJudgeGuard(): void {
    this.judgeCount++
  }

  build() {
    NavDestination() {
      Column() {
        Column() {
          Column()
            .width('60%')
            .height('50%')
            .backgroundColor(Color.Grey)
            .onClick (() => { // 1. A click event is registered on the child component. In normal cases, when a click is performed on the child component, the child component is preferentially responded.
              console.info('Clicked on child')
              this.increaseJudgeGuard()
            })
            .onGestureJudgeBegin((gestureInfo: GestureInfo, event: BaseGestureEvent) => {
              // 3. Disable the tap gesture on the child component when the number of taps is a multiple of 5. In this way, the tap gesture on the parent component can be responded.
              if (this.judgeCount % 5 == 0 && gestureInfo.type == GestureControl.GestureType.CLICK) {
                return GestureJudgeResult.REJECT
              } else {
                return GestureJudgeResult.CONTINUE
              }
            })
        }
        .width('80%')
        .height('80%')
        .justifyContent(FlexAlign.Center)
        .backgroundColor(Color.Green)
        .gesture(
          TapGesture() // 2. The tap gesture is registered on the parent component. In normal cases, when the tap gesture is performed in the child component area, the tap gesture on the parent component has a lower priority than that on the child component.
            .onAction(() => {
              console.info('Clicked on parent')
              this.increaseJudgeGuard()
            }))
      }
      .height('100%')
      .width('100%')
      .justifyContent(FlexAlign.Center)
    }
    .backgroundColor('#f1f2f3')
    // Replace $r('app.string.singlegesture_Index_Click_title') with the string resource file you use.
    .title($r('app.string.singlegesture_Index_Click_title'))
  }
}
```

In the example, the tap event of the child component is temporarily disabled once every five taps to ensure that the tap event of the parent component is responded first.


## Tap Gesture (TapGesture)


```ts
TapGesture(value?: TapGestureParameters)
```

The tap gesture supports single-tap and multi-tap. For details about the parameter definition, see [TapGesture](../reference/apis-arkui/arkui-ts/ts-basic-gestures-tapgesture.md).

<!-- @[catch_click_twice_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/EventProject/entry/src/main/ets/pages/singlegesture/TapGesture.ets) -->

``` TypeScript
@Entry
@Component
export struct Tap {
  @State value: string = '';

  build() {
    NavDestination() {
      Column({ space: 12 }) {
        Column() {
          Text('Click twice').fontSize(28)
            .gesture(
              // Bind a tap gesture whose count value is 2.
              TapGesture({ count: 2 })
                .onAction((event: GestureEvent|undefined) => {
                  if(event){
                    this.value = JSON.stringify(event.fingerList[0]);
                  }
                }))
          Text(this.value)
        }
        .height(200)
        .width(250)
        .padding(20)
        .border({ width: 3 })
        .margin(30)
      }
      .width('100%')
      .height('100%')
      .padding({ left: 12, right: 12 })
    }
    .backgroundColor('#f1f2f3')
    .title($r('app.string.singlegesture_TapGesture_title'))
  }
}
```

  ![tap](figures/tap.gif)


## Long Press Gesture (LongPressGesture)


```ts
LongPressGesture(value?:{fingers?:number, repeat?:boolean, duration?:number})
```

The long press gesture is used to trigger a long press gesture event. For details about the parameter definition, see [LongPressGesture](../reference/apis-arkui/arkui-ts/ts-basic-gestures-longpressgesture.md).

The following exemplifies how to bind a long press gesture that can be repeatedly triggered to the **Text** component:

<!-- @[catch_long_press_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/EventProject/entry/src/main/ets/pages/singlegesture/LongPressGesture.ets) -->

``` TypeScript
@Entry
@Component
export struct LongPress {
  @State count: number = 0;

  build() {
    NavDestination() {
      Column({ space: 12 }) {
        Column() {
          Text('LongPress OnAction:' + this.count).fontSize(28)
            .gesture(
              // Bind a long press gesture that can be triggered repeatedly.
              LongPressGesture({ repeat: true })
                .onAction((event: GestureEvent | undefined) => {
                  if (event) {
                    if (event.repeat) {
                      this.count++;
                    }
                  }
                })
                .onActionEnd(() => {
                  this.count = 0;
                })
            )
        }
        .height(200)
        .width(250)
        .padding(20)
        .border({ width: 3 })
        .margin(30)
      }
      .width('100%')
      .height('100%')
      .padding({ left: 12, right: 12 })
    }
    .backgroundColor('#f1f2f3')
    .title($r('app.string.singlegesture_LongPressGesture_title'))
  }
}
```


![longPress](figures/longPress.gif)


## Pan Gesture (PanGesture)


```ts
PanGesture(value?: { fingers?: number; direction?: PanDirection; distance?: number } | PanGestureOptions)
```

A pan gesture is used to trigger a pan gesture event. When the pan distance reaches the minimum pan distance (5 vp by default), the pan gesture is successfully recognized. For details about the parameter definition, see [PanGesture](../reference/apis-arkui/arkui-ts/ts-basic-gestures-pangesture.md).

The following uses simple volume control as an example. You can use the callback function of the pan gesture to process the logic of increasing or decreasing the volume in different input scenarios.
The following five operation modes are supported:
1. Swipe up or down with one finger.
2. Hold down the left mouse button and swipe up or down.
3. Scroll the mouse wheel.
4. Hold down the touchpad with one finger and swipe up or down.
5. Swipe with two fingers on the touchpad.

<!-- @[sliding_gesture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/EventProject/entry/src/main/ets/pages/singlegesture/PanCombinationGesture.ets) -->

``` TypeScript
@Entry
@Component
export struct VolumeControlDemo {
  @State currentVolume: number = 50;
  private readonly MAX_VOLUME: number = 100;
  private readonly MIN_VOLUME: number = 0;

  private handlePanUpdate(event: GestureEvent) {
    const volumeChange = -event.offsetY * 0.1;
    this.handleVolumeChange(volumeChange);
  }

  private handleWheelEvent(event: GestureEvent) {
    const volumeChange = event.offsetY * 0.1;
    this.handleVolumeChange(volumeChange);
  }

  private handleTouchPadScroll(event: GestureEvent) {
    const volumeChange = -event.offsetY * 0.02;
    this.handleVolumeChange(volumeChange);
  }

  private handleVolumeChange(delta: number) {
    this.currentVolume = Math.min(
      this.MAX_VOLUME,
      Math.max(this.MIN_VOLUME, this.currentVolume + delta)
    )
  }

  build() {
    NavDestination() {
      Column() {
        Row() {
          // Replace $r('app.string.video') with the string resource file you use.
          Text($r('app.string.video'))
          Text(`: ${this.currentVolume}`).fontSize(20)
        }.margin(10)
        Column()
          .width('100%')
          .height(250)
          .backgroundColor('#F5F5F5')
          .borderRadius(12)
          .gesture(
            PanGesture()
              .onActionStart(() => {
                console.info('Pan start');
              })
              .onActionUpdate((event: GestureEvent) => {
                if (event.source === SourceType.TouchScreen) {
                  console.info('finger move triggered PanGesture');
                  this.handlePanUpdate(event);
                }
                if (event.source === SourceType.Mouse && event.sourceTool === SourceTool.MOUSE) {
                  if (event.axisHorizontal === 0 && event.axisVertical === 0) {
                    console.info('mouse move with left button pressed triggered PanGesture');
                    this.handlePanUpdate(event);
                  } else { 
                    console.info('mouse wheel triggered PanGesture');
                    this.handleWheelEvent(event);
                  }
                }
                if (event.sourceTool === SourceTool.TOUCHPAD &&
                  (event.axisHorizontal !== 0 || event.axisVertical !== 0)) {
                  console.info('touchpad double finger move triggered PanGesture');
                  this.handleTouchPadScroll(event);
                }
              })
          )
      }
      .width('100%')
      .height('100%')
      .padding(20)
    }
    .backgroundColor('#f1f2f3')
    // Replace $r('app.string.singlegesture_Index_Pancom_title') with the string resource file you use.
    .title($r('app.string.singlegesture_Index_Pancom_title'))
  }
}
```


![pan](figures/pan.gif)


>**NOTE**
>
>Most swipeable components, such as **List**, **Grid**, **Scroll**, and **Tab**, allow for swiping through the pan gesture. If you bind the [pan gesture](#pan-gesture-pangesture) or [swipe gesture](#swipe-gesture-swipegesture) to a child of these components, competition for gesture recognition will result.
>
>If the pan gesture is bound to a child component, the component, instead of its parent, responds to the pan gestures recognized. If the parent component needs to respond, you need to modify the gesture binding method or the child component needs to transfer messages to the parent component, or modify the PanGesture parameter distance of the parent and child components to make the sliding more sensitive. If the swipe gesture is bound to a child component, to allow the parent component to respond to gestures, you need to modify the parameters of **PanGesture** and **SwipeGesture**, since the swipe gesture and pan gesture are recognized with different conditions.
>
>An inappropriate value can lead to slow response or lagging.


## Pinch Gesture (PinchGesture)


```ts
PinchGesture(value?: { fingers?: number; distance?: number })
```

The pinch gesture is used to trigger pinch gesture events. For details about the parameter definition, see [PinchGesture](../reference/apis-arkui/arkui-ts/ts-basic-gestures-pinchgesture.md).

The following exemplifies how to bind a three-finger pinch gesture to the **Column** component. You can obtain the scale factor from the callback of **PinchGesture** to scale the component.

<!-- @[catch_pinch_gesture_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/EventProject/entry/src/main/ets/pages/singlegesture/PinchGesture.ets) -->

``` TypeScript
@Entry
@Component
export struct Pinch {
  @State scaleValue: number = 1;
  @State pinchValue: number = 1;
  @State pinchX: number = 0;
  @State pinchY: number = 0;

  build() {
    NavDestination() {
      Column({ space: 12 }) {
        Column() {
          Column() {
            Text('PinchGesture scale:\n' + this.scaleValue)
            Text('PinchGesture center:\n(' + this.pinchX + ',' + this.pinchY + ')')
          }
          .height(200)
          .width(300)
          .border({ width: 3 })
          .margin({ top: 100 })
          // Bind the scale factor to the component so that it is scaled by changing the scale factor.
          .scale({ x: this.scaleValue, y: this.scaleValue, z: 1 })
          .gesture(
            // Bind a three-finger pinch gesture to the component.
            PinchGesture({ fingers: 3 })
              .onActionStart((event: GestureEvent | undefined) => {
                console.info('Pinch start');
              })// When the pinch gesture is triggered, you can obtain the zoom ratio through the callback function and change the zoom ratio of the component.
              .onActionUpdate((event: GestureEvent | undefined) => {
                if (event) {
                  this.scaleValue = this.pinchValue * event.scale;
                  this.pinchX = event.pinchCenterX;
                  this.pinchY = event.pinchCenterY;
                }
              })
              .onActionEnd(() => {
                this.pinchValue = this.scaleValue;
                console.info('Pinch end');
              })
          )
        }
      }
      .width('100%')
      .height('100%')
      .padding({ left: 12, right: 12 })
    }
    .backgroundColor('#f1f2f3')
    .title($r('app.string.singlegesture_PinchGesture_title'))
  }
}
```


![pinch](figures/pinch.png)


## Rotation Gesture (RotationGesture)


```ts
RotationGesture(value?: { fingers?: number; angle?: number })
```

RotationGesture is used to trigger rotation gesture events. For details about the parameter definition, see [RotationGesture](../reference/apis-arkui/arkui-ts/ts-basic-gestures-rotationgesture.md).

The following exemplifies how to bind a rotation gesture to the **Text** component. You can obtain the rotation angle from the callback of **RotationGesture** and implement rotation on the component.

<!-- @[catch_rotation_gesture_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/EventProject/entry/src/main/ets/pages/singlegesture/RotationGesture.ets) -->

``` TypeScript
@Entry
@Component
export struct Rotation {
  @State angle: number = 0;
  @State rotateValue: number = 0;

  build() {
    NavDestination() {
      Column({ space: 12 }) {
        Column() {
          Text('RotationGesture angle:' + this.angle).fontSize(28)
            // Bind the rotation to the component so that it is rotated by changing the rotation angle.
            .rotate({ angle: this.angle })
            .gesture(
              RotationGesture()
                .onActionStart((event: GestureEvent|undefined) => {
                  console.info('RotationGesture is onActionStart');
                })
                  // When the rotation gesture takes effect, the rotation angle is obtained through the callback and the component is rotated accordingly.
                .onActionUpdate((event: GestureEvent|undefined) => {
                  if(event){
                    this.angle = this.rotateValue + event.angle;
                  }
                  console.info('RotationGesture is onActionEnd');
                })
                  // When the fingers lift from the screen, the component is fixed at the angle where rotation ends.
                .onActionEnd(() => {
                  this.rotateValue = this.angle;
                  console.info('RotationGesture is onActionEnd');
                })
                .onActionCancel(() => {
                  console.info('RotationGesture is onActionCancel');
                })
            )
            .height(200)
            .width(300)
            .padding(20)
            .border({ width: 3 })
            .margin(100)
        }
      }
      .width('100%')
      .height('100%')
      .padding({ left: 12, right: 12 })
    }
    .backgroundColor('#f1f2f3')
    .title($r('app.string.singlegesture_RotationGesture_title'))
  }
}
```


![rotation](figures/rotation.png)


## Swipe Gesture (SwipeGesture)


```ts
SwipeGesture(value?: { fingers?: number; direction?: SwipeDirection; speed?: number })
```

A swipe gesture is used to trigger a swipe event. When the swipe speed is greater than 100 vp/s, the swipe gesture can be successfully identified. For details about the parameter definition, see [SwipeGesture](../reference/apis-arkui/arkui-ts/ts-basic-gestures-swipegesture.md).

The following example shows how to bind a swipe gesture to a **Column** component to rotate the component:

<!-- @[catch_swipe_gesture_event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/EventProject/entry/src/main/ets/pages/singlegesture/SwipeGesture.ets) -->

``` TypeScript
@Entry
@Component
export struct Swipe {
  @State rotateAngle: number = 0;
  @State speed: number = 1;

  build() {
    NavDestination() {
      Column({ space: 12 }) {
        Column() {
          Column() {
            Text('SwipeGesture speed\n' + this.speed)
            Text('SwipeGesture angle\n' + this.rotateAngle)
          }
          .border({ width: 3 })
          .width(300)
          .height(200)
          .margin(100)
          // Bind rotation to the <Column> component and change the rotation angle through the swipe speed and angle.
          .rotate({ angle: this.rotateAngle })
          .gesture(
            // Bind to the component the swipe gesture that can be triggered only when the user swipes in the vertical direction.
            SwipeGesture({ direction: SwipeDirection.Vertical })
              // When the swipe gesture is triggered, the swipe speed and angle are obtained, which can be used to modify the layout parameters.
              .onAction((event: GestureEvent|undefined) => {
                if(event){
                  this.speed = event.speed;
                  this.rotateAngle = event.angle;
                }
              })
          )
        }
      }
      .width('100%')
      .height('100%')
      .padding({ left: 12, right: 12 })
    }
    .backgroundColor('#f1f2f3')
    .title($r('app.string.singlegesture_SwipeGesture_title'))
  }
}
```


![swipe](figures/swipe.gif)


>**NOTE**
>
>When the swipe gesture and pan gesture are simultaneously bound to a component in default or mutually exclusive mode, competition for gesture recognition occurs. Whichever gesture meets the trigger condition first is recognized. By default, a swipe gesture is recognized when the swipe speed reaches 100 vp/s, and a pan gesture is recognized when the amount of finger movement reaches 5 vp. To allow a specific gesture to be recognized before the other, you can modify the parameter settings in **SwipeGesture** and **PanGesture**.
