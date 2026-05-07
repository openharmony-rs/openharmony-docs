# Motion Blur
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

You can apply a motion blur effect to a component being scaled or moved. This effect must be used together with the **onFinish** parameter of [AnimateParam](ts-explicit-animation.md#animateparam).

>  **NOTE**
>
>  This feature is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## motionBlur

motionBlur(value: MotionBlurOptions): T

Applies a motion blur effect to the component being scaled or moved.

> **NOTE**
>
> - Do not use this API in intra-component transitions, shared element transitions, implicit element transitions, or particle animations. Doing so may cause unexpected results.
>
> - The **radius** parameter of **motionBlur** must be set to **0** for the initial state. Otherwise, there may be unexpected results during a cold start.
>
> - This API must be used together with the **onFinish** parameter of **AnimateParam**. Its **radius** parameter must be set to **0** when the animation ends; otherwise, there may be unexpected results.
>
> - When using this API, do not frequently change the blur radius of the same component; otherwise, there may be unexpected results. For example, if you frequently click the image in the example, the blur effect may not work sometimes.
>
> - To avoid unexpected results, make sure the coordinates of the motion blur anchor point are the same as those of the animation scaling anchor point.
>
> - To avoid unexpected results, set the blur radius to a value less than 1.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                           | Mandatory| Description              |
| ------ | ----------------------------------------------- | ---- | ------------------ |
| value  | [MotionBlurOptions](#motionbluroptions) | Yes  | Motion blur options.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## motionBlur<sup>18+</sup>

motionBlur(motionBlur: Optional\<MotionBlurOptions>): T

Applies a motion blur effect to the component being scaled or moved. Compared with [motionBlur](#motionblur), this API supports the **undefined** type for the **motionBlur** parameter.

1. Do not use this API in intra-component transitions, shared element transitions, implicit element transitions, or particle animations. Doing so may cause unexpected results.

2. The **radius** parameter of **motionBlur** must be set to **0** for the initial state. Otherwise, there may be unexpected results during a cold start.

3. This API must be used together with the **onFinish** parameter of **AnimateParam**. Its **radius** parameter must be set to **0** when the animation ends; otherwise, there may be unexpected results.

4. When using this API, do not frequently change the blur radius of the same component; otherwise, there may be unexpected results. For example, if you frequently click the image in the example, the blur effect may not work sometimes.

5. To avoid unexpected results, make sure the coordinates of the motion blur anchor point are the same as those of the animation scaling anchor point.

6. To avoid unexpected results, set the blur radius to a value less than 1.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|   Name   |    Type                                                     |  Mandatory |     Description                                                      |
| ---------- | ---------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| motionBlur | Optional\<[MotionBlurOptions](#motionbluroptions)> | Yes  | Motion blur options.<br>If **motionBlur** is set to **undefined**, the previous value is retained.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component.|

## MotionBlurOptions

Defines motion blur options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type                                                       | Read-Only | Optional | Description                                                        |
| ------------- | ----------------------------------------------------------- | ----- | ----- | ------------------------------------------------------------ |
| radius | number      | No   | No   | Blur radius. The value range is [0.0, ∞). You are advised to set it to a value less than 1.0.|
| anchor | [MotionBlurAnchor](#motionbluranchor) | No   | No   | Coordinates of the motion blur anchor. They must be the same as those of the animation scaling anchor.|

## MotionBlurAnchor

Describes the coordinates of the motion blur anchor.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type                                                       | Read-Only | Optional | Description                                                        |
| ------------- | ----------------------------------------------------------- | ----- | ----- | ------------------------------------------------------------ |
| x | number      | No   | No   | X-coordinate of the anchor. The value range is [0.0, 1.0].|
| y | number      | No   | No   | Y-coordinate of the anchor. The value range is [0.0, 1.0].|

## Example

This example demonstrates how to apply a motion blur effect.
```ts
// xxx.ets
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct motionBlurTest {
  @State widthSize: number = 300
  @State heightSize: number = 240
  @State flag: boolean = true
  @State radius: number = 0
  @State x: number = 0.5
  @State y: number = 0.5

  build() {
    Column() {
      Column() {
        // Replace $r('app.media.test') with the image resource file you use.
        Image($r('app.media.test'))
          .width(this.widthSize)
          .height(this.heightSize)
          .scale({ x: this.flag ? 1 : 0.8,y: this.flag ? 1 : 0.8 ,centerX: "50%", centerY: "50%" })
          .onClick(() => {
            this.radius = 50;
            this.x = 0.5;
            this.y = 0.5;
            this.flag = !this.flag;
          })
          .animation({
            duration: 2000, // Animation playback time.
            iterations:1, // Animation playback iterations.
            playMode:PlayMode.Alternate, // Animation playback mode: plays forward on odd-numbered iterations (1st, 3rd, 5th...) and reverse on even-numbered iterations (2nd, 4th, 6th...).
            curve: curves.springCurve(10, 1, 228, 30), // Animation curve.
            onFinish: () => {
              this.radius = 0;
              console.info("onFinish")
            },
          })
          .motionBlur({ radius: this.radius, anchor: { x: this.x, y: this.y } })
      }
    }.width('100%')
    .margin({ top: 50 })
  }
}
```

![motionBlurTest](figures/motionBlur.gif)
