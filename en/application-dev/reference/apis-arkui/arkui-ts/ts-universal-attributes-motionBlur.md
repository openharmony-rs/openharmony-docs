# Motion Blur

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=4d06e6d604d64a9b64c2360f42cbd3fd13c9290b translatedAt=2026-08-26T06:23:01.719Z pushedAt=2026-08-26T09:20:29.340Z -->

Sets a motion blur effect for the component during motion caused by scaling or displacement. This effect must be used together with the **onFinish** parameter of [AnimateParam](ts-explicit-animation.md#animateparam).

> **NOTE**
>
> - This feature is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## motionBlur

motionBlur(value: MotionBlurOptions): T

Applies a motion blur effect to the component being scaled or moved.

> **NOTE**
>
> - Do not use this attribute in intra-component transitions, shared element transitions, implicit element transitions, or particle animations. Doing so may cause unexpected results.
>
> - The **radius** parameter of **motionBlur** must be set to **0** for the initial state of the component. Otherwise, there may be unexpected results during a cold start.
>
> - This attribute must be used together with the **onFinish** parameter of [AnimateParam](ts-explicit-animation.md#animateparam). The **radius** parameter of **motionBlur** must be set to **0** after the motion blur animation ends. Otherwise, there may be unexpected results.
>
> - When using this attribute, do not change the blur radius of the same component frequently. Otherwise, there may be unexpected results. For example, in the animation in the example, frequent taps may cause the blur effect to occasionally fail.
>
> - The motion blur anchor coordinates must be consistent with the anchor (**centerX**/**centerY**) of the [scale](ts-universal-attributes-transformation.md#scale) attribute used for the animation. Otherwise, there may be unexpected results.
>
> - The recommended blur radius does not exceed 1.0. Otherwise, there may be unexpected results.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                           | Mandatory| Description              |
| ------ | ----------------------------------------------- | ---- | ------------------ |
| value  | [MotionBlurOptions](#motionbluroptions) | Yes  | Motion blur options.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## motionBlur<sup>18+</sup>

motionBlur(motionBlur: Optional\<MotionBlurOptions>): T

Applies a motion blur effect to the component being scaled or moved. Compared with [motionBlur](#motionblur), this API supports the **undefined** type for the **motionBlur** parameter.

> **NOTE**
>
> - Do not use this attribute in intra-component transitions, shared element transitions, implicit element transitions, or particle animations. Doing so may cause unexpected results.
>
> - The **radius** parameter of **motionBlur** must be set to **0** for the initial state. Otherwise, there may be unexpected results during a cold start.
>
> - This attribute must be used together with the **onFinish** parameter of [AnimateParam](ts-explicit-animation.md#animateparam). The **radius** parameter of **motionBlur** must be set to **0** after the motion blur animation ends. Otherwise, there may be unexpected results.
>
> - When using this attribute, do not change the blur radius of the same component frequently. Otherwise, there may be unexpected results. For example, in the animation in the example, frequent taps may cause the blur effect to occasionally fail.
>
> - The motion blur anchor coordinates must be consistent with the anchor (**centerX**/**centerY**) of the [scale](ts-universal-attributes-transformation.md#scale) attribute. Otherwise, there may be unexpected results.
>
> - The recommended blur radius does not exceed 1.0. Otherwise, there may be unexpected results.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|   Name   |    Type                                                     |  Mandatory |     Description                                                      |
| ---------- | ---------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| motionBlur | Optional\<[MotionBlurOptions](#motionbluroptions)> | Yes | Motion blur parameters.<br>When the value of **motionBlur** is **undefined**, the previously set value is retained. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## MotionBlurOptions

Defines motion blur options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type                                                       | Read-Only | Optional | Description                                                        |
| ------------- | ----------------------------------------------------------- | ----- | ----- | ------------------------------------------------------------ |
| radius | number      | No    | No    | Blur radius, in vp. The value range is [0.0, +∞). A value not greater than 1.0 is recommended for a better visual effect. A negative value is automatically corrected to 0.0, and a value greater than the recommended 1.0 may cause unexpected effects. |
| anchor | [MotionBlurAnchor](#motionbluranchor) | No    | No    | Anchor coordinates of the motion blur. They must be consistent with the anchor (**centerX**/**centerY**) of the animation [scale](ts-universal-attributes-transformation.md#scale) attribute; otherwise, unexpected effects may occur. |

## MotionBlurAnchor

Defines the motion blur anchor coordinates.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name         | Type                                                       | Read-Only | Optional | Description                                                        |
| ------------- | ----------------------------------------------------------- | ----- | ----- | ------------------------------------------------------------ |
| x | number      | No    | No    | Anchor coordinate x value. The value range is [0.0, 1.0], where 0.0 indicates the left edge of the component, 1.0 indicates the right edge of the component, and 0.5 indicates the horizontal center. |
| y | number      | No    | No    | Anchor coordinate y value. The value range is [0.0, 1.0], where 0.0 indicates the top edge of the component, 1.0 indicates the bottom edge of the component, and 0.5 indicates the vertical center. |

## Example

This example demonstrates how to apply a motion blur effect.

```ts
// xxx.ets
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct MotionBlurTest {
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
          .scale({ x: this.flag ? 1 : 0.8, y: this.flag ? 1 : 0.8, centerX: '50%', centerY: '50%' })
          .onClick(() => {
            // Set the motion blur parameters and trigger the zoom animation when tapped.
            this.radius = 50;
            this.x = 0.5;
            this.y = 0.5;
            this.flag = !this.flag;
          })
          .animation({
            duration: 2000, // Animation playback time.
            iterations: 1, // Number of animation plays.
            playMode: PlayMode.Alternate, // Animation play mode. The animation plays forward on odd-numbered plays (1, 3, 5...) and backward on even-numbered plays (2, 4, 6...).
            curve: curves.springCurve(10, 1, 228, 30), // Animation curve.
            onFinish: () => {
              // After the animation ends, set the blur radius to 0 to clear the motion blur effect.
              this.radius = 0;
              console.info('onFinish');
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