# PanGesture
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

**PanGesture** is used to trigger a pan gesture when the movement distance of a finger on the screen reaches the minimum value.

The table below describes the scenarios that can trigger a pan gesture:

| Trigger Mode             | Input Source Type          | Input Device Type           | Remarks                             | 
|----------------------|---------------------|------------------------|-----------------------------------|
| Swiping with a finger press         | [SourceTool](ts-gesture-settings.md#sourcetool9).Finger   | [SourceType](ts-gesture-settings.md#sourcetype8).TouchScreen | Both **axisVertical** and **axisHorizontal** are 0.|
| Swiping with a left mouse button press     | [SourceTool](ts-gesture-settings.md#sourcetool9).MOUSE    | [SourceType](ts-gesture-settings.md#sourcetype8).Mouse        | Both **axisVertical** and **axisHorizontal** are 0.|
| Scrolling with a mouse wheel         | [SourceTool](ts-gesture-settings.md#sourcetool9).MOUSE    | [SourceType](ts-gesture-settings.md#sourcetype8).Mouse        | Either **axisVertical** or **axisHorizontal** is non-zero.|
| Swiping after pressing the left button on a touchpad | [SourceTool](ts-gesture-settings.md#sourcetool9).MOUSE  | [SourceType](ts-gesture-settings.md#sourcetype8).Mouse     | Both **axisVertical** and **axisHorizontal** are 0.|
| Swiping with two fingers on a touchpad      | [SourceTool](ts-gesture-settings.md#sourcetool9).TOUCHPAD  | [SourceType](ts-gesture-settings.md#sourcetype8).Mouse      | Either **axisVertical** or **axisHorizontal** is non-zero.|
| Swiping with a stylus      | [SourceTool](ts-gesture-settings.md#sourcetool9).Pen  | [SourceType](ts-gesture-settings.md#sourcetype8).TouchScreen      | Both **axisVertical** and **axisHorizontal** are 0.|

>  **NOTE**
>
>  This API is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.


## APIs

### PanGesture

PanGesture(value?: { fingers?: number; direction?: PanDirection; distance?: number } | PanGestureOptions)

Creates a pan gesture. Inherits from [GestureInterface\<T>](ts-gesture-common.md#gestureinterfacet11).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | { fingers?: number; direction?: [PanDirection](ts-basic-gestures-pangesture.md#pandirection); distance?: number } \| [PanGestureOptions](#pangestureoptions) | No| Parameters for the pan gesture.<br> - **fingers**: minimum number of fingers to trigger a pan gesture. The value ranges from 1 to 10.<br>Default value: **1**.<br>Value range: [1, 10].<br>**NOTE**<br>If the value is less than 1 or is not set, the default value is used.<br> - **direction**: pan direction. The value supports the AND (&amp;) and OR (\|) operations.<br>Default value: **PanDirection.All**.<br> - **distance**: minimum pan distance to trigger the gesture, in vp.<br>Value range: [0, +∞).<br>Default value: **8** for the stylus and **5** for other input sources.<br>**NOTE**<br>If a pan gesture and a [tab](ts-container-tabs.md) swipe occur at the same time, set **distance** to **1** to make the gesture more easily recognizable.<br>If the value specified is less than **0**, the default value is used.|

### PanGesture<sup>15+</sup>

PanGesture(options?: PanGestureHandlerOptions)

Creates a pan gesture. Compared with [PanGesture](#pangesture-1), this API adds the **isFingerCountLimited** and **distanceMap** parameters to **options**, which control whether to enforce the exact number of fingers touching the screen and specify the minimum pan distance required to trigger the gesture for different input sources, respectively.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options   | [PanGestureHandlerOptions](./ts-gesturehandler.md#pangesturehandleroptions)   | No  | Parameters of the swipe gesture handler.|

## PanDirection

Enumerates the pan directions. Unlike **SwipeDirection**, **PanDirection** has no angular restrictions.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| ---- | -- | ----- |
| All | - | All directions.|
| Horizontal | - | Horizontal direction.|
| Vertical | - | Vertical direction.|
| Left | - | Leftward.|
| Right | - | Rightward.|
| Up | - | Upward.|
| Down | - | Downward.|
| None | - | Panning disabled.|


## PanGestureOptions

### constructor

constructor(value?: { fingers?: number; direction?: PanDirection; distance?: number })

Creates a pan gesture configuration object. The **PanGestureOptions** API enables dynamic updates to pan gesture properties without requiring state variable modifications that would trigger UI re-renders.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| --------- | ------------------------------------- | ---- | ------------------------------------------------------------ |
| value   | { fingers?: number; direction?: [PanDirection](#pandirection); distance?: number } | No  | Pan gesture configuration.<br>**fingers**: minimum number of fingers required. The value ranges from 1 to 10.<br>Default value: **1**.<br>**direction**: pan direction. The value supports the AND (&amp;) and OR (\|) operations.<br>Default value: **PanDirection.All**.<br>**distance**: minimum pan distance to trigger the gesture, in vp.<br>Default value: **8** for the stylus and **5** for other input sources.<br>**NOTE**<br>If a pan gesture and a [tab](ts-container-tabs.md) swipe occur at the same time, set **distance** to **1** to make the gesture more easily recognizable.<br>If the value specified is less than **0**, the default value is used.<br>To avoid slow response and lagging during scrolling, set a reasonable pan distance.|

### setDirection

setDirection(value: PanDirection)

Sets the pan direction.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                     |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  |  [PanDirection](#pandirection) | Yes  | Pan direction. The value supports the AND (&amp;) and OR (\|) operations.<br>Default value: **PanDirection.All**.|

### setDistance

setDistance(value: number)

Sets the minimum pan distance to trigger the gesture, in vp. To avoid performance degradation due to excessive response delays or accidental releases, avoid excessively large values. For best practices, see [Reducing the Pan Distance for Gesture Recognition](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-application-latency-optimization-cases#section1116134115286).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                       |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  |  number | Yes  | Minimum pan distance to trigger the gesture, in vp.<br>Default value: **8** for the stylus and **5** for other input sources.<br>**NOTE**<br>If a pan gesture and a [tab](ts-container-tabs.md) swipe occur at the same time, set **distance** to **1** to make the gesture more easily recognizable.<br>If the value specified is less than **0**, the default value is used.<br>To avoid slow response and lagging during scrolling, set a reasonable pan distance.|

### setFingers

setFingers(value: number)

Sets the minimum number of fingers to trigger the gesture.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| value  |  number | Yes  | Minimum number of fingers to trigger a pan gesture. The value ranges from 1 to 10.<br>Default value: **1**.|

### getDirection<sup>12+</sup>

getDirection(): PanDirection

Obtains the pan direction.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description       |
| ------ | --------- |
| [PanDirection](#pandirection) | Pan direction.|

### getDistance<sup>18+</sup>

getDistance(): number

Obtains the minimum pan distance to trigger the gesture.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description       |
| ------ | --------- |
| number | Minimum pan distance to trigger the gesture.|


## Events

>  **NOTE**
>
>  In **fingerList** of [GestureEvent](ts-gesture-common.md#gestureevent), the index of a finger corresponds to its position, that is, the ID of a finger in **fingerList[index]** refers to its index. If a finger is pressed first and does not participate in triggering of the current gesture, its position in **fingerList** is left empty. You are advised to use **fingerInfos** when possible.

### onActionStart

onActionStart(event: (event: GestureEvent) => void)

Registers the callback for successful pan gesture recognition.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| event  |  (event: [GestureEvent](ts-gesture-common.md#gestureevent)) => void | Yes  | Callback for successful pan gesture recognition.|

### onActionUpdate

onActionUpdate(event: (event: GestureEvent) => void)

Registers the callback for pan gesture updates. If **fingerList** contains multiple fingers, this callback updates the location information of only one finger each time.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| event  |  (event: [GestureEvent](ts-gesture-common.md#gestureevent)) => void | Yes  | Callback for pan gesture updates.|

### onActionEnd

onActionEnd(event: (event: GestureEvent) => void)

Registers the callback for pan gesture completion. This callback is triggered when all fingers are lifted after successful pan gesture recognition.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| event  |  (event: [GestureEvent](ts-gesture-common.md#gestureevent)) => void | Yes  | Callback for pan gesture completion.|

### onActionCancel

onActionCancel(event: () => void)

Registers the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful pan gesture recognition. No gesture event information is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| event  |  () => void | Yes  | Callback for pan gesture cancellation.|

### onActionCancel<sup>18+</sup>

onActionCancel(event: Callback\<GestureEvent\>)

Registers the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful pan gesture recognition. Gesture event information is returned.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| event  |  Callback\<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes  | Callback for pan gesture cancellation.|

## Example

This example demonstrates the recognition of single-finger and double-finger pan gestures using **PanGesture**.

```ts
// xxx.ets
@Entry
@Component
struct PanGestureExample {
  @State offsetX: number = 0;
  @State offsetY: number = 0;
  @State positionX: number = 0;
  @State positionY: number = 0;
  private panOption: PanGestureOptions = new PanGestureOptions({ direction: PanDirection.Left | PanDirection.Right });

  build() {
    Column() {
      Column() {
        Text('PanGesture offset:\nX: ' + this.offsetX + '\n' + 'Y: ' + this.offsetY)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .translate({ x: this.offsetX, y: this.offsetY, z: 0}) // Move the component with its upper left corner as the coordinate origin.
      // Pan left and right to trigger the gesture event
      .gesture(
      PanGesture(this.panOption)
        .onActionStart((event: GestureEvent) => {
          console.info('Pan start');
          console.info(`Pan start timeStamp is: ${event.timestamp}`);
        })
        .onActionUpdate((event: GestureEvent) => {
          if (event) {
            this.offsetX = this.positionX + event.offsetX;
            this.offsetY = this.positionY + event.offsetY;
          }
        })
        .onActionEnd((event: GestureEvent) => {
          this.positionX = this.offsetX;
          this.positionY = this.offsetY;
          console.info('Pan end');
          console.info(`Pan end timeStamp is: ${event.timestamp}`);
        })
      )

      Button('Set PanGesture Trigger Condition')
        .onClick(() => {
          // Change the trigger condition to double-finger panning in any direction.
          this.panOption.setDirection(PanDirection.All);
          this.panOption.setFingers(2);
        })
    }
  }
}
```

**Diagrams**

Panning left:

![en-us_image_0000001174264374](figures/en-us_image_0000001174264374.png) 

Click **Set PanGesture Trigger Condition** to set the pan gesture to be triggered by two fingers moving toward the lower left corner.

 ![en-us_image1_0000001174264374](figures/en-us_image1_0000001174264374.png) 
