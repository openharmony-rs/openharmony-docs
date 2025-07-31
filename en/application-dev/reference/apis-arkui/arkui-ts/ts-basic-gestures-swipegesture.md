# SwipeGesture

**SwipeGesture** is used to implement a swipe gesture, which can be recognized when the swipe speed is 100 vp/s or higher.

>  **NOTE**
>
>  This gesture is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.


## APIs

SwipeGesture(value?: { fingers?: number, direction?: SwipeDirection, speed?: number, isFingerCountLimited?: boolean })

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fingers | number | No| Minimum number of fingers to trigger a swipe gesture. The value ranges from 1 to 10.<br>Default value: **1**|
| direction | [swipeDirection](#swipedirection)| No| Swipe direction.<br>Default value: **SwipeDirection.All**|
| speed | number | No| Minimum speed of the swipe gesture.<br>Default value: 100 vp/s<br>**NOTE**<br>If the value is less than or equal to 0, it will be converted to the default value.|
| isFingerCountLimited<sup>15+</sup> | boolean | No| Whether to enforce the exact number of fingers touching the screen. With the value **true**, the gesture recognition fails if the number of fingers touching the screen does not match the configured value of **fingers**.<br>**true**: Enforce the exact number of fingers touching the screen.<br>**false**: Do not enforce the exact number of fingers touching the screen.<br>Default Value: **false**.|

## SwipeDirection

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Description|
| -------- | -------- |
| All | All directions.|
| Horizontal | Horizontal direction. The gesture event is triggered when the angle between the finger moving direction and the x-axis is less than 45 degrees.|
| Vertical | Vertical direction. The gesture event is triggered when the angle between the finger moving direction and the y-axis is less than 45 degrees.|
| None | Swiping disabled.|


## Events

**System capability**: SystemCapability.ArkUI.ArkUI.Full

>  **NOTE**
>
>  In **fingerList** of [GestureEvent](ts-gesture-settings.md#gestureevent), the index of a finger corresponds to its position, that is, the ID of a finger in **fingerList[index]** refers to its index. If a finger is pressed first and does not participate in triggering of the current gesture, its position in **fingerList** is left empty. You are advised to use **fingerInfos** when possible.

| Name| Description|
| -------- | -------- |
| onAction(event:(event: [GestureEvent](ts-gesture-settings.md#gestureevent)) =&gt; void) | Invoked when the swipe gesture is recognized.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

## Attributes

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type   |Description                                       |
| ----  | ------  | ---------------------------------------- |
| tag<sup>11+</sup>   | string  | Tag for the swipe gesture. It is used to distinguish the gesture during custom gesture judgment.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| allowedTypes<sup>14+</sup> | Array\<[SourceTool](ts-gesture-settings.md#sourcetool9)> | Allowed event input types for the swipe gesture.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|

## Example

This example demonstrates the recognition of a swipe gesture using **SwipeGesture**.

```ts
// xxx.ets
@Entry
@Component
struct SwipeGestureExample {
  @State rotateAngle: number = 0;
  @State speed: number = 1;

  build() {
    Column() {
      Column() {
        Text("SwipeGesture speed\n" + this.speed)
        Text("SwipeGesture angle\n" + this.rotateAngle)
      }
      .border({ width: 3 })
      .width(300)
      .height(200)
      .margin(100)
      .rotate({ angle: this.rotateAngle })
      // The gesture event is triggered by swiping vertically with one finger.
      .gesture(
      SwipeGesture({ direction: SwipeDirection.Vertical })
        .onAction((event: GestureEvent) => {
          if (event) {
            this.speed = event.speed
            this.rotateAngle = event.angle
          }
        })
      )
    }.width('100%')
  }
}
```

 ![en-us_image_0000001231374559.png](figures/en-us_image_0000001231374559.png) 
