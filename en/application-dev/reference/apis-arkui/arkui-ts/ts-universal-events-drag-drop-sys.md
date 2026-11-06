# Drag Event (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9430c77017ca73641537d932a3d7d8a4c99c078b translatedAt=2026-09-02T12:24:56.976Z -->

A drag event refers to a sequence of events triggered in the UI when a user drags an object (such as a file, component, or element). These events allow you to customize drag and drop behaviors, enabling functionalities like drag and drop operations and position adjustments.

>  **NOTE**
>
>  This API is supported since API version 7. For newly added APIs in later versions, the earliest supported version is marked with a superscript.
>
>  Resource files preset in the application (that is, resource files that already exist in the HAP package before the application is installed) support drag and drop only within the local application.
>
>  This document describes only the system APIs of the current module. For details about other public APIs, see [Drag Event](ts-universal-events-drag-drop.md).

## DragEvent<sup>7+</sup>

DragEvent represents drag event information and provides the event data and drag animation configuration capabilities during the drag process. It is used to obtain or set drag behaviors at each stage of the drag process.

### Attributes

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type | Read-only | Optional | Description |
| --------- | ----------------------------------------- | --------- | --------- | ---------------------------------- |
| dragAnimationType | [DragAnimationType](#draganimationtype) | No | Yes | Sets the drag animation type. This attribute can be set only in the [onDragStart](ts-universal-events-drag-drop.md#ondragstart) phase, and can be obtained in the [onDragStart](ts-universal-events-drag-drop.md#ondragstart), [onDragEnter](ts-universal-events-drag-drop.md#ondragenter), [onDragMove](ts-universal-events-drag-drop.md#ondragmove), [onDragLeave](ts-universal-events-drag-drop.md#ondragleave), [onDrop](ts-universal-events-drag-drop.md#ondrop), and [onDragEnd](ts-universal-events-drag-drop.md#ondragend10) callbacks.<br> The default value is DEFAULT.<br>**Since Version:** 26.0.0<br>**Model Constraint:** This API can be used only in the stage model. <br>**System API:** This is a system API.|

### enableInternalDropAnimation<sup>20+</sup>

enableInternalDropAnimation(configuration: string): void

Uses the system's built-in animation, which is available only to system applications. It can be used only in the onDrop phase, and is suitable for scenarios where a system application needs a unified built-in drop animation after the drag is released.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name   | Type                                     | Mandatory| Description                              |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| configuration | string | Yes | Configuration parameter of the system built-in drag animation. The string content is in JSON format and is used to configure the execution effect of the system built-in drag animation. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md) and [Drag Event Error Codes](../errorcode-drag-event.md).

| ID  | Error Message|
| --------- | ------- |
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 801       | Capability not supported.|
| 190003    | Operation not allowed for current phase. |

### executeFollowHandMorphDropAnimation

executeFollowHandMorphDropAnimation(onAnimationFinished: Callback\<void\>, animationOption?: string): void

Executes the follow-hand morph drop animation. After the animation is complete, the callback is triggered. The callback is triggered by the system after the drag framework animation ends. This API uses an asynchronous callback.

> **NOTE**
>
> 1. This API takes effect only when [dragAnimationType](#attributes) is set to DragAnimationType.FOLLOW_HAND_MORPH.
> 2. Do not implement logic unrelated to the animation in the callback to avoid affecting execution efficiency.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| --------- | ----------------------------------------- | ---- | ---------------------------------- |
| onAnimationFinished | [Callback](../../../reference/apis-basic-services-kit/js-apis-base.md#callback)\<void\> | Yes | Callback invoked when the drag framework animation ends. It takes effect only when [dragAnimationType](#attributes) is set to DragAnimationType.FOLLOW_HAND_MORPH. |
| animationOption | string | No | Drop animation parameter. Passed in when the curve, drop position, or drop size of the follow-hand morph drop animation needs to be customized. If not passed in, the default follow-hand morph drop animation configuration of the system is used.<br> The parameter is a JSON string that contains the following fields:<br> **CubicCurveEnable**: boolean. Whether to enable the cubic curve animation. When set to true, the cubic curve animation is enabled, which applies to scenarios where a custom Bezier curve is required to control the drop rhythm. When set to false, it is disabled.<br> **SpringEnable**: boolean. Whether to enable the spring animation. When set to true, the spring animation effect is enabled, which applies to scenarios where an elastic rebound effect is required. When set to false, it is disabled. <br> **dropAnimationCurve**: number[]. Drop animation curve parameters, whose meaning is determined by SpringEnable and CubicCurveEnable (SpringEnable has a higher priority). When SpringEnable is true, the array length is 3, in the format [response, dampingRatio, blendDuration], corresponding to the spring curve parameters of [curves.springMotion](../../../reference/apis-arkui/js-apis-curve.md#curvesspringmotion9). When SpringEnable is false and CubicCurveEnable is true, the array length is 4, in the format [x1, y1, x2, y2], corresponding to the cubic Bezier curve control point parameters of [curves.cubicBezierCurve](../../../reference/apis-arkui/js-apis-curve.md#curvescubicbeziercurve9).<br> **Note:** SpringEnable has a higher priority than CubicCurveEnable. When both are true, the spring animation takes effect. When neither SpringEnable nor CubicCurveEnable is set to true, the default spring animation is used.<br> **dropPosition**: number[]. Drop position coordinates. The array length is 2, in the format [x, y], in px, indicating the target position coordinates when the dragged element drops. The value range is (-∞, +∞).<br> **dropSize**: number[]. Drop size. The array length is 2, in the format [width, height], in px, indicating the target size when the dragged element drops. The value range is (0, +∞). |

## DragAnimationType

Enumerates the drag animation types.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value | Description |
| --------- | ------- | ---------------------------------- |
| DEFAULT | 0 | Uses the default drag animation, which applies to common drag scenarios that do not require a custom drop animation. |
| FOLLOW_HAND_MORPH | 1 | Uses the follow-hand morph drag animation, which applies to scenarios where the dragged element morphs with the gesture and a custom drop animation is executed. |

## DragController<sup>11+</sup>

Provides the capability to initiate active dragging. When the application receives an event such as touch or long press, it can actively initiate a drag action and carry drag information in it. This document describes only the system APIs of DragController. For other public APIs, see [DragController](../arkts-apis-uicontext-dragcontroller.md).

### interruptFollowHandMorphDropAnimation

interruptFollowHandMorphDropAnimation(): boolean

Interrupts the pending follow-hand morph drop animation triggered by [executeFollowHandMorphDropAnimation](#executefollowhandmorphdropanimation), and immediately invokes its registered callback [onAnimationFinished](#executefollowhandmorphdropanimation). This API applies to scenarios where the user cancels the drag, the page switches, or an unfinished follow-hand morph drop animation needs to be terminated.


**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type | Description |
| -------- | -------- |
| boolean | Returns the interruption result.<br>Returns **true** if the interruption succeeds, and **false** if there is no pending follow-hand morph drop animation to interrupt. |

## Examples

### Example 1: Setting the Follow-Hand Morph Drag Animation

This example sets [dragAnimationType](#attributes) to FOLLOW_HAND_MORPH to implement the follow-hand morph drag animation effect, and executes a custom drop animation through [executeFollowHandMorphDropAnimation](#executefollowhandmorphdropanimation) when the drag ends.

Since API version 26.0.0, the [dragAnimationType](#attributes) attribute, the [executeFollowHandMorphDropAnimation](#executefollowhandmorphdropanimation) method, and the [interruptFollowHandMorphDropAnimation](#interruptfollowhandmorphdropanimation) method are added.

```ts
// xxx.ets
// Animation parameter class.
class AnimationOption {
  CubicCurveEnable: boolean = false;
  SpringEnable: boolean = false;
  dropAnimationCurve: number[] = [];
  dropPosition: number[] = [];
  dropSize: number[] = [];
}

@Entry
@Component
struct FollowHandMorphDemo {
  @State dragInfo: string = 'Not dragged';
  @State animationInfo: string = '';
  @State interruptResult: string = '';

  build() {
    Column({ space: 20 }) {
      Text('Follow-hand morph drag animation example')
        .fontSize(20)
        .fontWeight(FontWeight.Bold)

      Text('Instructions: Long press the square on the left and drag it to the area on the right')
        .fontSize(14)
        .fontColor('#666666')

      Row({ space: 30 }) {
        // Drag source
        Column() {
          Text('Drag source')
            .fontSize(14)
          Text('Long press to drag')
            .fontSize(12)
            .fontColor('#999999')
        }
        .width(100)
        .height(100)
        .backgroundColor('#DDEEFF')
        .borderRadius(12)
        .justifyContent(FlexAlign.Center)
        .draggable(true)
        .onDragStart((event: DragEvent) => {
          // Set the follow-hand morph animation mode.
          event.dragAnimationType = DragAnimationType.FOLLOW_HAND_MORPH;
          this.dragInfo = 'onDragStart: dragAnimationType=1';
        })

        // Target area
        Column() {
          Text('Target area')
            .fontSize(14)
          Text('Release here')
            .fontSize(12)
            .fontColor('#999999')
        }
        .width(100)
        .height(100)
        .backgroundColor('#EAF8EA')
        .borderRadius(12)
        .justifyContent(FlexAlign.Center)
        .onDrop((event: DragEvent) => {
          this.dragInfo = 'onDrop triggered';

          // Build the animation parameters.
          let animationOption = new AnimationOption();
          animationOption.CubicCurveEnable = false;
          animationOption.SpringEnable = true;
          animationOption.dropAnimationCurve = [0.416, 0.99, 0];
          animationOption.dropPosition = [830, 600];
          animationOption.dropSize = [100, 100];

          // Execute the follow-hand morph drop animation.
          event.executeFollowHandMorphDropAnimation(() => {
            this.animationInfo = 'Follow-hand morph animation completed';
          }, JSON.stringify(animationOption));
        })
      }

      // Status display
      Column({ space: 8 }) {
        Text(`Drag status: ${this.dragInfo}`).fontSize(12)
        Text(`Animation status: ${this.animationInfo}`).fontSize(12)
        Text(`Interruption result: ${this.interruptResult}`).fontSize(12)
      }
      .width('100%')
      .padding(12)
      .backgroundColor('#F7F7F7')
      .borderRadius(8)

      // Button for interrupting the animation
      Button('Interrupt the pending follow-hand morph animation')
        .onClick(() => {
          let result = this.getUIContext().getDragController().interruptFollowHandMorphDropAnimation();
          this.interruptResult = result ? 'Interrupted successfully' : 'No pending animation to interrupt';
        })
    }
    .width('100%')
    .height('100%')
    .padding(20)
    .backgroundColor('#FFFFFF')
  }
}
```
<!--Del--> <!--DelEnd-->