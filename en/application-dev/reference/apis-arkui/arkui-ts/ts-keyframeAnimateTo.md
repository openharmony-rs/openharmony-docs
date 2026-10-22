# Keyframe Animation (keyframeAnimateTo)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e10e7def4863f4f964c4d0cb425b7650081cb83e translatedAt=2026-08-28T01:40:00.344Z pushedAt=2026-09-01T06:23:05.554Z -->

The [UIContext](../arkts-apis-uicontext-uicontext.md) provides the **keyframeAnimateTo** API that allows you to define one or more keyframe states to implement segment-based animations. A keyframe animation divides the animation process into multiple segments based on the states at several key moments. For the same attribute, the transition is not a monotonic change from the start point to the end point, but a segment-based transition. Similar to the attribute animation of [animateTo](../arkts-apis-uicontext-uicontext.md#animateto), for layout animations that change the width and height, the content (for example, text and [Canvas](ts-components-canvas-canvas.md) content) directly reaches the end state. To make the content change with the width and height, use the [renderFit](ts-universal-attributes-renderfit.md#renderfit) attribute. **keyframeAnimateTo** and [animateTo](../arkts-apis-uicontext-uicontext.md#animateto) cannot be applied to the same attribute of the same component at the same time. If they are called on the same attribute in sequence, the animation called later overrides the effect of the previous one.

>  **NOTE**
>
> - This feature is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - This API is a member function of the [UIContext](../arkts-apis-uicontext-uicontext.md) class and must be called through a **UIContext** instance. Calling sequence: first call [getUIContext()](./ts-custom-component-api.md#getuicontext) to obtain a **UIContext** instance, and then call the **keyframeAnimateTo** method.

## keyframeAnimateTo

keyframeAnimateTo(param: KeyframeAnimateParam, keyframes: Array&lt;KeyframeState&gt;): void

Sets the keyframe animation. This API must be called through a UIContext instance. For layout animations that change the width and height, the content (for example, text and [Canvas](ts-components-canvas-canvas.md) content) directly reaches the end state. To make the content change with the width and height, use the [renderFit](ts-universal-attributes-renderfit.md#renderfit) attribute.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type                                             | Mandatory| Description                        |
| ------------ | ---------------------------------------------------- | ------- | ---------------------------- |
| param        | [KeyframeAnimateParam](#keyframeanimateparam) | Yes      | Overall parameter configuration of the keyframe animation, used to set the animation delay, playback count, completion callback, expected frame rate, and so on.     |
| keyframes    | Array&lt;[KeyframeState](#keyframestate)&gt;  | Yes      | All keyframe states. At least one keyframe is required. Each animation segment is executed in sequence according to the array order. Each keyframe defines the duration, animation curve, and target state of an animation segment.            |

## KeyframeAnimateParam

Provides animation configuration options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

<!--Table: 20%; 20%; 8%; 8%; 44%-->
| Name      | Type   | Read-Only| Optional| Description                                   |
| ---------- | ---------- | ---- | --- | ------------------------------------- |
| delay      | number     | No  | Yes    | Overall delay of the animation, in ms. By default, the animation is played without delay.<br>Default value: 0<br>Value range: (-∞, +∞)<br>**NOTE**<br>&nbsp;If delay >= 0, the animation is played after the delay. If delay < 0, the animation is played in advance. If the value is a floating-point number, truncation is performed. For example, if the value is set to 200.5, it is processed as 200. For delay < 0: if the absolute value of **delay** is less than the actual animation duration, the animation starts from the state at the moment corresponding to the absolute value of **delay**; if the absolute value of delay is greater than or equal to the actual animation duration, the animation moves directly to the end state in the first frame after it starts. The actual animation duration equals the duration of a single animation multiplied by the number of animation iterations.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| iterations | number     | No  | Yes    | Number of times that the animation is played. By default, the animation is played once. The value **-1** indicates that the animation is played for an unlimited number of times, in which case the **onFinish** callback is not triggered. The value **0** indicates no animation effect. If the value is greater than 1, the complete keyframe sequence is re-executed from the initial animation state in each iteration.<br>Default value: **1**<br>Value range: [-1, +∞)<br>**NOTE**<br>- If the value is a floating-point number, truncation is performed. For example, if the value is set to 1.2, it is processed as 1.<br>- If the value is less than -1, it is processed as -1, that is, the animation is played for an unlimited number of times.<br>- The value of **iterations** affects the animation behavior when delay < 0. For details, see the description of the delay parameter.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| onFinish   | () => void | No  | Yes    | Completion callback of the animation. It is invoked after all iterations of the **keyframe** animation are played. When **iterations** is set to **0**, there is no animation effect and this callback is not triggered. When **iterations** is set to **-1** (unlimited playback), the animation never finishes playing and this callback is not triggered. If transition animations are disabled in the developer options of system settings, or the **UIAbility** switches from the foreground to the background, a finite-loop keyframe animation that is still playing ends immediately and the completion callback is triggered.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| expectedFrameRateRange<sup>19+</sup>   | [ExpectedFrameRateRange](./ts-explicit-animation.md#expectedframeraterange11) | No | Yes | Expected frame rate range of the animation.<br>Default value: **{min:0, expected:0, max:0}**, that is, the frame rate follows the app frame rate.<br>**NOTE**<br>After the developer sets a valid expected frame rate, the system collects the requested frame rate, performs comprehensive evaluation and scheduling, and adjusts the frame rate on the rendering pipeline to meet the developer's expected frame rate as much as possible. The expected frame rate set by the developer does not represent the final actual effect, which is subject to the system capability and screen refresh rate.<br>**Atomic service API:** This API can be used in atomic services since API version 19.|

## KeyframeState

Sets the keyframe state.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 12.

| Name      | Type                             | Read-Only| Optional| Description                                      |
| ---------- | ------------------------------------ | --- | ---- | ---------------------------------------- |
| duration   | number                               | No | No      | Duration of this keyframe animation, in ms (milliseconds).<br>Value range: [0, +∞)<br>**NOTE**<br>- A value less than 0 is treated as 0.<br>- A floating-point value is truncated to an integer. For example, 1.2 is treated as 1.<br>- When **duration** is **0**, the transition to this keyframe state is instantaneous, without any animation process. |
| curve      | [Curve](ts-appendix-enums.md#curve)\|&nbsp;string&nbsp;\|&nbsp;[ICurve](./ts-explicit-animation.md#icurve9) | No | Yes  | Animation curve used for this keyframe.<br>It is recommended to specify the curve in the form of **Curve** or **ICurve**.<br>When the type is string, it is the animation interpolation curve. For the value, refer to the curve parameter of [AnimateParam](./ts-explicit-animation.md#animateparam). The valid values are "linear", "ease", "ease-in", "ease-out", "ease-in-out", "fast-out-slow-in", "linear-out-slow-in", "fast-out-linear-in", "friction", "extreme-deceleration", "rhythm", "sharp", "smooth", and strings in the "cubic-bezier(x1,y1,x2,y2)" and "steps(number,step-position)" formats. "springMotion", "responsiveSpringMotion", and "interpolatingSpring" are not supported.<br>Default value: **Curve.EaseInOut**<br>**NOTE**<br>Since the durations of the [springMotion](../js-apis-curve.md#curvesspringmotion9), [responsiveSpringMotion](../js-apis-curve.md#curvesresponsivespringmotion9), and [interpolatingSpring](../js-apis-curve.md#curvesinterpolatingspring10) curves do not take effect, these three curves are not supported. When an unsupported curve is set, the default curve **Curve.EaseInOut** is used. |
| event      | () => void                           | No | No | Closure function that sets the target state at this keyframe moment. In this closure, define the target values that the component attributes should reach. |

## Example

This example demonstrates how to set a keyframe animation through **keyframeAnimateTo**, including the **delay**, the **onFinish** completion callback, and the curve configuration of each keyframe.

```ts
// xxx.ets
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct KeyframeDemo {
  @State myScale: number = 1.0;
  uiContext: UIContext | undefined = undefined;

  aboutToAppear() {
    this.uiContext = this.getUIContext?.();
  }

  build() {
    Column() {
      Circle()
        .width(100)
        .height(100)
        .fill('#46B1E3')
        .margin(100)
        .scale({ x: this.myScale, y: this.myScale })
        .onClick(() => {
          if (!this.uiContext) {
            console.info('no uiContext, keyframe failed');
            return;
          }
          this.myScale = 1;
          // Set the keyframe animation to play three times in total, with a delay of 200 ms, and trigger the onFinish callback when it ends.
          this.uiContext.keyframeAnimateTo({
              iterations: 3,
              delay: 200,
              onFinish: () => {
                console.info('keyframe animate finish');
              },
              // expectedFrameRateRange is added since API version 19.
              expectedFrameRateRange: {
                min: 10,
                max: 120,
                expected: 60,
              }
            }, [
            {
              // The first keyframe animation lasts 800 ms, uses the EaseIn curve, and animates the scale attribute from 1 to 1.5.
              duration: 800,
              curve: Curve.EaseIn,
              event: () => {
                this.myScale = 1.5;
              }
            },
            {
              // The second keyframe animation lasts 500 ms, uses the EaseOut curve, and animates the scale attribute from 1.5 to 1.
              duration: 500,
              curve: Curve.EaseOut,
              event: () => {
                this.myScale = 1;
              }
            }
          ]);
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

![keyframeAnimateTo](figures/keyframeAnimateTo1.gif)