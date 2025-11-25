# @ohos.animator (Animator)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->

The **Animator** module provides APIs for applying animation effects, including defining animations, starting animations, and playing animations in reverse order.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module can be used in ArkTS since API version 9.
>
> - This module cannot be used in the file declaration of the [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md). In other words, the APIs of this module can be used only after a component instance is created; they cannot be called in the lifecycle of the UIAbility.
>
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Custom components typically retain the [AnimatorResult](#animatorresult) returned by [create](#create18) to prevent animation object destruction during execution. This object holds references to the custom component via callbacks. Release the animation object in [aboutToDisappear](../apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttodisappear) to avoid circular reference memory leaks. For implementation examples, see [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).
>
> - Both Animator destruction and explicit [cancel](#cancel) or [finish](#finish) calls trigger an additional [onFrame](#onframe12) callback with the animation's endpoint value. Therefore, if [cancel](#cancel) or [finish](#finish) is called during animation execution, there will be an immediate jump to the endpoint in one frame. For smooth mid-point termination, first clear the [onFrame](#onframe12) callback before calling [finish](#finish).

## Modules to Import

```ts
import { Animator as animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## Animator

Creates an **Animator** object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### create<sup>(deprecated)</sup>

create(options: AnimatorOptions): AnimatorResult

Creates an **AnimatorResult** object for animations.

> **NOTE**
> 
> - This API is supported since API version 9 and deprecated since API version 18. You are advised to use [createAnimator](arkts-apis-uicontext-uicontext.md#createanimator) in [UIContext](arkts-apis-uicontext-uicontext.md) instead.
>
> - Since API version 10, you can use the [createAnimator](arkts-apis-uicontext-uicontext.md#createanimator) API in [UIContext](arkts-apis-uicontext-uicontext.md), which ensures that the object is created in the intended UI instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| options | [AnimatorOptions](#animatoroptions) | Yes   | Animator options.|

**Return value**

| Type                               | Description           |
| --------------------------------- | ------------- |
| [AnimatorResult](#animatorresult) | Animator result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

> **NOTE**
>
> For precise UI context management, use the [createAnimator](arkts-apis-uicontext-uicontext.md#createanimator) API in [UIContext](arkts-apis-uicontext-uicontext.md) to specify the execution context.

<!--deprecated_code_no_check-->
```ts
import { Animator as animator, AnimatorOptions } from '@kit.ArkUI';

let options: AnimatorOptions = {
  duration: 1500,
  easing: "friction",
  delay: 0,
  fill: "forwards",
  direction: "normal",
  iterations: 3,
  begin: 200.0,
  end: 400.0
};
animator.create(options); // You are advised to use UIContext.createAnimator().
```

### create<sup>18+</sup>

create(options: AnimatorOptions \| SimpleAnimatorOptions): AnimatorResult

Creates an **AnimatorResult** object for animations. Compared with[create](#createdeprecated), this API accepts parameters of the [SimpleAnimatorOptions](#simpleanimatoroptions18) type.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| options | [AnimatorOptions](#animatoroptions) \| [SimpleAnimatorOptions](#simpleanimatoroptions18) | Yes   | Parameters of the animation.|

**Return value**

| Type                               | Description           |
| --------------------------------- | ------------- |
| [AnimatorResult](#animatorresult) | Animator result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

> **NOTE**
>
> For precise UI context management, use the [createAnimator](arkts-apis-uicontext-uicontext.md#createanimator) API in [UIContext](arkts-apis-uicontext-uicontext.md) to specify the execution context.

<!--deprecated_code_no_check-->
```ts
import { Animator as animator, SimpleAnimatorOptions } from '@kit.ArkUI';
let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).duration(2000);
animator.create(options);// You are advised to use UIContext.createAnimator().
```

### createAnimator<sup>(deprecated)</sup>

createAnimator(options: AnimatorOptions): AnimatorResult

Creates an animation.

This API is deprecated since API version 9. You are advised to use[createAnimator](arkts-apis-uicontext-uicontext.md#createanimator) in [UIContext](arkts-apis-uicontext-uicontext.md) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| options | [AnimatorOptions](#animatoroptions) | Yes   | Animator options.|

**Return value**

| Type                               | Description           |
| --------------------------------- | ------------- |
| [AnimatorResult](#animatorresult) | Animator result.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator } from '@kit.ArkUI';

let options: AnimatorOptions = {
  // There is no need to explicitly specify the type AnimatorOptions in the xxx.js file.
  duration: 1500,
  easing: "friction",
  delay: 0,
  fill: "forwards",
  direction: "normal",
  iterations: 3,
  begin: 200.0,
  end: 400.0,
};
this.animator = animator.createAnimator(options);
```

## AnimatorResult

Defines the animator result.

### reset<sup>9+</sup>

reset(options: AnimatorOptions): void

Resets the animation parameters of this animator.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| options | [AnimatorOptions](#animatoroptions) | Yes   | Animator options.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [API Call Error Codes](errorcode-internal.md).

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | The specified page is not found or the object property list is not obtained.|


**Example**

```ts
import { AnimatorResult } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;

  create() {
    this.animatorResult = this.getUIContext().createAnimator({
      duration: 1500,
      easing: "friction",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 3,
      begin: 200.0,
      end: 400.0
    })
    this.animatorResult.reset({
      duration: 1500,
      easing: "friction",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 5,
      begin: 200.0,
      end: 400.0
    });
  }

  build() {
    // ......
  }
}
```

### reset<sup>18+</sup>

reset(options: AnimatorOptions \| SimpleAnimatorOptions): void

Resets the animation parameters of this animator. Compared to [reset](#reset9), this API accepts parameters of the [SimpleAnimatorOptions](#simpleanimatoroptions18) type.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| options | [AnimatorOptions](#animatoroptions) \| [SimpleAnimatorOptions](#simpleanimatoroptions18) | Yes   | Animator options.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [API Call Error Codes](errorcode-internal.md).

| ID  | Error Message|
| --------- | ------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001    | The specified page is not found or the object property list is not obtained.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

<!--deprecated_code_no_check-->
```ts
import { Animator as animator, AnimatorResult, AnimatorOptions, SimpleAnimatorOptions } from '@kit.ArkUI';
let options: AnimatorOptions = {
  duration: 1500,
  easing: "ease",
  delay: 0,
  fill: "forwards",
  direction: "normal",
  iterations: 1,
  begin: 100,
  end: 200
};
let optionsNew: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200)
  .duration(2000)
  .iterations(3)
  .delay(1000)
let animatorResult:AnimatorResult = animator.create(options);
animatorResult.reset(optionsNew);
```

### play

play(): void

Plays this animation. The animation retains the previous playback state. For example, if the animation is set to **reverse** and paused, it will remain in **reverse** when resumed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
animator.play();
```

### finish

finish(): void

Ends the animation, triggering the [onFinish](#onfinish12) callback.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
animator.finish();
```

### pause

pause(): void

Pauses this animation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
animator.pause();
```

### cancel

cancel(): void

Cancels the animation, triggering the [onCancel](#oncancel12) callback. This API is functionally identical to [finish](#finish) except for the callback it triggers. It is recommended that you use the **finish** API to end animations.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
animator.cancel();
```

### reverse

reverse(): void

Plays this animation in reverse order. This API does not take effect when the interpolating spring curve is used.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
animator.reverse();
```

### onFrame<sup>12+</sup>

onFrame: (progress: number) => void

Called when a frame is received.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description      |
| -------- | ------ | ---- | -------- |
| progress | number | Yes   | Current value of the animation.<br>Value range: [begin, end] defined in [AnimatorOptions](#animatoroptions)<br>Default value range: [0, 1]|

**Example**

```ts
import { AnimatorResult } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private backAnimator: AnimatorResult | undefined = undefined

  create() {
    this.backAnimator = this.getUIContext().createAnimator({
      duration: 2000,
      easing: "ease",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 1,
      begin: 100, // Start point of the animation interpolation.
      end: 200 // End point of the animation interpolation.
    })
    this.backAnimator.onFrame = (value: number) => {
      console.info("onFrame callback")
    }
  }

  build() {
    // ......
  }
}
```

### onFinish<sup>12+</sup>

onFinish: () => void

Called when this animation is finished.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
import { AnimatorResult } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private backAnimator: AnimatorResult | undefined = undefined

  create() {
    this.backAnimator = this.getUIContext().createAnimator({
      duration: 2000,
      easing: "ease",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 1,
      begin: 100, // Start point of the animation interpolation.
      end: 200 // End point of the animation interpolation.
    })
    this.backAnimator.onFinish = ()=> {
      console.info("onFinish callback")
    }
  }

  build() {
    // ......
  }
}
```

### onCancel<sup>12+</sup>

onCancel: () => void

Called when this animation is canceled.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
import { AnimatorResult } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private backAnimator: AnimatorResult | undefined = undefined

  create() {
    this.backAnimator = this.getUIContext().createAnimator({
      duration: 2000,
      easing: "ease",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 1,
      begin: 100, // Start point of the animation interpolation.
      end: 200 // End point of the animation interpolation.
    })
    this.backAnimator.onCancel = () => {
      console.info("onCancel callback")
    }
  }

  build() {
    // ......
  }
}
```

### onRepeat<sup>12+</sup>

onRepeat: () => void

Called when this animation repeats.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
import { AnimatorResult } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private backAnimator: AnimatorResult | undefined = undefined

  create() {
    this.backAnimator = this.getUIContext().createAnimator({
      duration: 2000,
      easing: "ease",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 1,
      begin: 100, // Start point of the animation interpolation.
      end: 200 // End point of the animation interpolation.
    })
    this.backAnimator.onRepeat = () => {
      console.info("onRepeat callback")
    }
  }

  build() {
    // ......
  }
}
```

### onframe<sup>(deprecated)</sup>

> **NOTE**
>
> This API is deprecated since API version 12. You are advised to use [onFrame](#onframe12) instead.

onframe: (progress: number) => void

Called when a frame is received.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description      |
| -------- | ------ | ---- | -------- |
| progress | number | Yes   | Current progress of the animation.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult } from '@kit.ArkUI';

let animatorResult: AnimatorResult | undefined = animator.create(options)
animatorResult.onframe = (value) => {
  console.info("onframe callback")
}
```

### onfinish<sup>(deprecated)</sup>

> **NOTE**
>
> This API is deprecated since API version 12. You are advised to use [onFinish](#onfinish12) instead.

onfinish: () => void

Called when this animation is finished.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult } from '@kit.ArkUI';

let animatorResult: AnimatorResult | undefined = animator.create(options)
animatorResult.onfinish = () => {
  console.info("onfinish callback")
}
```

### oncancel<sup>(deprecated)</sup>

> **NOTE**
>
> This API is deprecated since API version 12. You are advised to use [onCancel](#oncancel12) instead.


oncancel: () => void

Called when this animation is canceled.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

<!--deprecated_code_no_check-->
```ts
import { Animator as animator, AnimatorResult } from '@kit.ArkUI';

let animatorResult: AnimatorResult | undefined = animator.create(options)
animatorResult.oncancel = () => {
  console.info("oncancel callback")
}
```

### onrepeat<sup>(deprecated)</sup>

> **NOTE**
>
> This API is deprecated since API version 12. You are advised to use [onRepeat](#onrepeat12) instead.

onrepeat: () => void

Called when this animation repeats.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult } from '@kit.ArkUI';

let animatorResult: AnimatorResult | undefined = animator.create(options)
animatorResult.onrepeat = () => {
  console.info("onrepeat callback")
}
```

### setExpectedFrameRateRange<sup>12+</sup>

setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void

Sets the expected frame rate range.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name          | Type                                      | Mandatory| Description                         |
| --------------- | ------------------------------------------ | ---- | -----------------------------|
| rateRange       | [ExpectedFrameRateRange](../apis-arkui/arkui-ts/ts-explicit-animation.md#expectedframeraterange11)| Yes  | Expected frame rate range.|

> **NOTE**
>
> After a valid expected frame rate is set, the system collects the configured frame rate and divides the frequency on the rendering pipeline. The actual frame rate may be different from the expected one configured. It is limited by the system capability and screen refresh rate.

**Example**

```ts
import { AnimatorResult } from '@kit.ArkUI';

let expectedFrameRate: ExpectedFrameRateRange = {
  min: 0,
  max: 120,
  expected: 30
}

@Entry
@Component
struct AnimatorTest {
  private backAnimator: AnimatorResult | undefined = undefined

  create() {
    this.backAnimator = this.getUIContext().createAnimator({
      duration: 2000,
      easing: "ease",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 1,
      begin: 100, // Start point of the animation interpolation.
      end: 200 // End point of the animation interpolation.
    })
    this.backAnimator.setExpectedFrameRateRange(expectedFrameRate);
  }

  build() {
    // ......
  }
}
```

### update<sup>(deprecated)</sup>

update(options: AnimatorOptions): void

Updates this animator.

This API is deprecated since API version 9. You are advised to use [reset<sup>9+</sup>](#reset9) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| options | [AnimatorOptions](#animatoroptions) | Yes   | Animator options.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
animator.update(options);
```

## AnimatorOptions

Animator options.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### Properties

| Name      | Type                                                       | Read-Only| Optional| Description                                                        |
| ---------- | ----------------------------------------------------------- | ---- | ------- | ----------------------------------------------------- |
| duration   | number                                                      | No| No  | Duration for playing the animation, in milliseconds.<br> Value range: [0, +∞).<br>Default value: **0**                        |
| easing     | string                                                      | No| No  | Animation interpolation curve. Only the following values are supported:<br>**"linear"**: The animation speed keeps unchanged.<br>**"ease"**: The animation starts slowly, accelerates, and then slows down towards the end. The cubic-bezier curve (0.25, 0.1, 0.25, 1.0) is used.<br>**"ease-in"**: The animation starts at a low speed and then picks up speed until the end. The cubic-bezier curve (0.42, 0.0, 1.0, 1.0) is used.<br>**"ease-out"**: The animation ends at a low speed. The cubic-bezier curve (0.0, 0.0, 0.58, 1.0) is used.<br>**"ease-in-out"**: The animation starts and ends at a low speed. The cubic-bezier curve (0.42, 0.0, 0.58, 1.0) is used.<br>**"fast-out-slow-in"**: The animation uses the standard cubic-bezier curve (0.4, 0.0, 0.2, 1.0).<br>**"linear-out-slow-in"**: The animation uses the deceleration cubic-bezier curve (0.0, 0.0, 0.2, 1.0).<br>**"fast-out-linear-in"**: The animation uses acceleration cubic-bezier curve (0.4, 0.0, 1.0, 1.0)<br>**"friction"**: The animation uses the damping cubic-bezier curve (0.2, 0.0, 0.2, 1.0).<br>**"extreme-deceleration"**: The animation uses the extreme deceleration cubic-bezier curve (0.0, 0.0, 0.0, 1.0).<br>**"rhythm"**: The animation uses the rhythm cubic-bezier curve (0.7, 0.0, 0.2, 1.0).<br>**"sharp"**: The animation uses the sharp cubic-bezier curve (0.33, 0.0, 0.67, 1.0).<br>**"smooth"**: The animation uses the smooth cubic-bezier curve (0.4, 0.0, 0.4, 1.0).<br>**"cubic-bezier(x1,y1,x2,y2)"**: The animation uses the defined cubic bezier curve, where the value of **x1** and **x2** must range from 0 to 1. For example, **"cubic-bezier(0.42,0.0,0.58,1.0)"**.<br>**"steps(number,step-position)"**: The animation uses a step curve. The **number** parameter is mandatory and must be set to a positive integer. The **step-position** parameter is optional and can be set to **start** or **end** (default value). For example, **"steps(3,start)"**.<br>**"interpolating-spring(velocity,mass,stiffness,damping)"**: The animation uses an interpolating spring curve. This API is supported since API version 11 and can be used only in ArkTS. The **velocity**, **mass**, **stiffness**, and **damping** parameters are of the numeric type, and the values of **mass**, **stiffness**, and **damping** must be greater than 0. For details about the parameters, see [Curves.interpolatingSpring](./js-apis-curve.md#curvesinterpolatingspring10). When an interpolating spring curve is used, settings for the **duration**, **fill**, **direction**, and **iterations** do not take effect. Rather, the value of **duration** is subject to the spring settings, **fill** is fixed at **forwards**, **direction** at **normal**, and **iterations** at **1**. In addition, invoking [reverse](#reverse) of **animator** is not effective. In other words, when using an interpolating spring curve, the animation can play only once in forward mode.<br>If the provided string is invalid, **"ease"** is used.|
| delay      | number                                                      | No| No  | Animation delay duration, in milliseconds. Value **0** means that there is no delay. If the value specified is a negative number, the animation starts playing ahead of its scheduled time. If the amount of time by which the playback is advanced is greater than the total duration of the animation, the animation skips to the end state immediately.<br>Default value: **0**       |
| fill       | 'none' \| 'forwards' \| 'backwards' \| 'both'               | No| No  | State of the animated target after the animation is executed.<br>**'none'**: No style is applied to the target before or after the animation is executed.<br>**'forwards'**: The target keeps the state at the end of the animation (defined in the last key frame) after the animation is executed.<br>**'backwards'**: During the delay period specified in [AnimatorOptions](#animatoroptions), the animation uses the value defined in the first keyframe. When **direction** in [AnimatorOptions](#animatoroptions) is **'normal'** or **'alternate'**, the animation uses the **from** keyframe value. When **direction** in [AnimatorOptions](#animatoroptions) is **'reverse'** or **'alternate-reverse'**, the animation uses the **to** keyframe value.<br>**'both'**: The animation follows the **'forwards'** and **'backwards'** rules.|
| direction  | 'normal' \| 'reverse' \| 'alternate' \| 'alternate-reverse' | No| No  | Animation playback mode.<br>**'normal'**: plays the animation in forward loop mode.<br>**'reverse'**: plays the animation in reverse loop mode.<br>**'alternate'**: plays the animation in alternating loop mode. When the animation is played for an odd number of times, the playback is in forward direction. When the animation is played for an even number of times, the playback is in reverse direction.<br>**'alternate-reverse'**: plays the animation in reverse alternating loop mode. When the animation is played for an odd number of times, the playback is in reverse direction. When the animation is played for an even number of times, the playback is in forward direction.<br>Default value: **'normal'**|
| iterations | number                                                      | No| No  | Number of times that the animation is played. The value **0** means the animation is not played, **-1** means the animation is played for an unlimited number of times, and a positive integer means the animation is played that specific number of times.<br>**NOTE**<br>Any negative value other than **-1** is considered invalid. For invalid values, the animation is played once.|
| begin      | number                                                      | No| No  | Start point of the animation interpolation.<br>**NOTE**<br>This setting affects the input parameter value of the [onFrame](#onframe12) callback.<br>Default value: **0**                                             |
| end        | number                                                      | No| No  | End point of animation interpolation.<br>**NOTE**<br>This setting affects the input parameter value of the [onFrame](#onframe12) callback.<br>Default value: **1**                                           |

## SimpleAnimatorOptions<sup>18+</sup>

Defines a simple animation parameter object. Unlike **AnimatorOptions**, this object comes with some default values for certain animation parameters, so you do not have to set them manually.

### constructor<sup>18+</sup>

constructor(begin: number, end: number)

A constructor used to create a **SimpleAnimatorOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type                                                       | Mandatory| Description                                                        |
| ---------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
|  begin      | number                                                      | Yes  | Start point of the animation interpolation.                                              |
|  end        | number                                                      | Yes  | End point of animation interpolation.

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200); // Animation interpolation from 100 to 200, with other animation parameters set to default values.
let animatorResult:AnimatorResult = animator.create(options);
```

### duration<sup>18+</sup>

duration(duration: number): SimpleAnimatorOptions

Sets the animation duration.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| duration | number | Yes   | Animation duration, in milliseconds.<br>Default value: **1000**|

**Return value**

| Type                               | Description           |
| --------------------------------- | ------------- |
| [SimpleAnimatorOptions](#simpleanimatoroptions18) | **SimpleAnimatorOptions** object for animation parameters.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).duration(500);
let animatorResult:AnimatorResult = animator.create(options);
```

### easing<sup>18+</sup>

easing(curve: string): SimpleAnimatorOptions

Sets the interpolation curve for this animation.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| curve | string | Yes   | Interpolation curve. For details, see [AnimatorOptions](#animatoroptions).<br>Default value: **"ease"**|

**Return value**

| Type                               | Description           |
| --------------------------------- | ------------- |
| [SimpleAnimatorOptions](#simpleanimatoroptions18) | **SimpleAnimatorOptions** object for animation parameters.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).easing("ease-in");
let animatorResult:AnimatorResult = animator.create(options);
```

### delay<sup>18+</sup>

delay(delay: number): SimpleAnimatorOptions

Sets the playback delay for this animation.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| delay | number | Yes   | Playback delay, in milliseconds. The value **0** indicates no delay. If the value specified is a negative number, the animation starts playing ahead of its scheduled time. If the amount of time by which the playback is advanced is greater than the total duration of the animation, the animation skips to the end state immediately.<br>Default value: **0**|

**Return value**

| Type                               | Description           |
| --------------------------------- | ------------- |
| [SimpleAnimatorOptions](#simpleanimatoroptions18) | **SimpleAnimatorOptions** object for animation parameters.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).delay(500);
let animatorResult:AnimatorResult = animator.create(options);
```

### fill<sup>18+</sup>

fill(fillMode: [FillMode](./arkui-ts/ts-appendix-enums.md#fillmode)): SimpleAnimatorOptions

Sets the fill mode for this animation.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| fillMode | [FillMode](./arkui-ts/ts-appendix-enums.md#fillmode) | Yes   | Fill mode, which affects how the animation behaves during the delay period and after it ends.<br>Default value: **FillMode.Forwards**|

**Return value**

| Type                               | Description           |
| --------------------------------- | ------------- |
| [SimpleAnimatorOptions](#simpleanimatoroptions18) | **SimpleAnimatorOptions** object for animation parameters.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).fill(FillMode.Forwards);
let animatorResult:AnimatorResult = animator.create(options);
```

### direction<sup>18+</sup>

direction(direction: [PlayMode](./arkui-ts/ts-appendix-enums.md#playmode)): SimpleAnimatorOptions

Sets the playback direction for this animation.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| direction | [PlayMode](./arkui-ts/ts-appendix-enums.md#playmode) | Yes   | Playback direction.<br>Default value: **PlayMode.Normal**|

**Return value**

| Type                               | Description           |
| --------------------------------- | ------------- |
| [SimpleAnimatorOptions](#simpleanimatoroptions18) | **SimpleAnimatorOptions** object for animation parameters.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).direction(PlayMode.Alternate);
let animatorResult:AnimatorResult = animator.create(options);
```

### iterations<sup>18+</sup>

iterations(iterations: number): SimpleAnimatorOptions

Sets the number of times that this animation is played.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                                 | Mandatory  | Description     |
| ------- | ----------------------------------- | ---- | ------- |
| iterations | number | Yes   | Number of times that the animation is played. The value **0** means the animation is not played, and **-1** means the animation is played for an unlimited number of times.<br>Default value: **1**|

**Return value**

| Type                               | Description           |
| --------------------------------- | ------------- |
| [SimpleAnimatorOptions](#simpleanimatoroptions18) | **SimpleAnimatorOptions** object for animation parameters.|

**Example**

See [ArkTS-based Declarative Development Paradigm](#arkts-based-declarative-development-paradigm).

```ts
import { Animator as animator, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).iterations(3);
let animatorResult:AnimatorResult = animator.create(options);
```

## Example
### JavaScript-compatible Web-like Development Paradigm

```html
<!-- hml -->
<div class="container">
  <div class="Animation" style="height: {{divHeight}}px; width: {{divWidth}}px; background-color: red;" onclick="Show">
  </div>
</div>
```

<!--code_no_check-->
<!--deprecated_code_no_check-->
```ts
import { Animator as animator, AnimatorResult } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let DataTmp: Record<string, Animator> = {
  'divWidth': 200,
  'divHeight': 200,
  'animator': animator
}

class Tmp {
  data: animator = DataTmp
  onInit: Function = () => {
  }
  Show: Function = () => {
  }
}

class DateT {
  divWidth: number = 0
  divHeight: number = 0
  animator: AnimatorResult | null = null
}

(Fn: (v: Tmp) => void) => {
  Fn({
    data: DataTmp,
    onInit() {
      let options: AnimatorOptions = {
        duration: 1500,
        easing: "friction",
        delay: 0,
        fill: "forwards",
        direction: "normal",
        iterations: 2,
        begin: 200.0,
        end: 400.0
      };
      let DataTmp: DateT = {
        divWidth: 200,
        divHeight: 200,
        animator: null
      }
      DataTmp.animator = animator.create(options);
    },
    Show() {
      let options1: AnimatorOptions = {
        duration: 1500,
        easing: "friction",
        delay: 0,
        fill: "forwards",
        direction: "normal",
        iterations: 2,
        begin: 0,
        end: 400.0,
      };
      let DataTmp: DateT = {
        divWidth: 200,
        divHeight: 200,
        animator: null
      }
      try {
        DataTmp.animator = animator.create(options1);
        DataTmp.animator.reset(options1);
      } catch (error) {
        let message = (error as BusinessError).message
        let code = (error as BusinessError).code
        console.error(`Animator reset failed, error code: ${code}, message: ${message}.`);
      }
      let _this = DataTmp;
      if (DataTmp.animator) {
        DataTmp.animator.onFrame = (value: number) => {
          _this.divWidth = value;
          _this.divHeight = value;
        };
        DataTmp.animator.play();
      }
    }
  })
}
```

  ![en-us_image_00007](figures/en-us_image_00007.gif)

### ArkTS-based Declarative Development Paradigm

> **NOTE**
>
> For precise UI context management, use the [createAnimator](arkts-apis-uicontext-uicontext.md#createanimator) API in [UIContext](arkts-apis-uicontext-uicontext.md) to specify the execution context.

<!--deprecated_code_no_check-->
```ts
import { AnimatorResult } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private TAG: string = '[AnimatorTest]'
  private backAnimator: AnimatorResult | undefined = undefined
  private flag: boolean = false
  @State columnWidth: number = 100
  @State columnHeight: number = 100

  create() {
    this.backAnimator = this.getUIContext().createAnimator({
      // You are advised to use this.getUIContext().createAnimator().
      duration: 2000,
      easing: "ease",
      delay: 0,
      fill: "forwards",
      direction: "normal",
      iterations: 1,
      begin: 100, // Start point of the animation interpolation.
      end: 200 // End point of the animation interpolation.
    })
    this.backAnimator.onFinish = () => {
      this.flag = true
      console.info(this.TAG, 'backAnimator onFinish')
    }
    this.backAnimator.onRepeat = () => {
      console.info(this.TAG, 'backAnimator repeat')
    }
    this.backAnimator.onCancel = () => {
      console.info(this.TAG, 'backAnimator cancel')
    }
    this.backAnimator.onFrame = (value: number) => {
      this.columnWidth = value
      this.columnHeight = value
    }
  }

  aboutToDisappear() {
    // When the custom component disappears, call finish to end incomplete animations and prevent them from continuing.
    // Since backAnimator references this in onFrame, and this holds backAnimator,
    // set backAnimator stored in the custom component to undefined when the component disappears to avoid memory leak.
    this.backAnimator?.finish();
    this.backAnimator = undefined;
  }

  build() {
    Column() {
      Column() {
        Column()
          .width(this.columnWidth)
          .height(this.columnHeight)
          .backgroundColor(Color.Red)
      }
      .width('100%')
      .height(300)

      Column() {
        Row() {
          Button('create')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              this.create()
            })
        }
        .padding(10)

        Row() {
          Button('play')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              this.flag = false
              if (this.backAnimator) {
                this.backAnimator.play()
              }
            })
        }
        .padding(10)

        Row() {
          Button('pause')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              if (this.backAnimator) {
                this.backAnimator.pause()
              }
            })
        }
        .padding(10)

        Row() {
          Button('finish')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              this.flag = true
              if (this.backAnimator) {
                this.backAnimator.finish()
              }
            })
        }
        .padding(10)

        Row() {
          Button('reverse')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              this.flag = false
              if (this.backAnimator) {
                this.backAnimator.reverse()
              }
            })
        }
        .padding(10)

        Row() {
          Button('cancel')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              if (this.backAnimator) {
                this.backAnimator.cancel()
              }
            })
        }
        .padding(10)

        Row() {
          Button('reset')
            .fontSize(30)
            .fontColor(Color.Black)
            .onClick(() => {
              if (this.flag) {
                this.flag = false
                if (this.backAnimator) {
                  this.backAnimator.reset({
                    duration: 3000,
                    easing: "ease-in",
                    delay: 0,
                    fill: "forwards",
                    direction: "alternate",
                    iterations: 3,
                    begin: 100,
                    end: 300
                  })
                }
              } else {
                console.info(this.TAG, 'Animation not ended')
              }
            })
        }
        .padding(10)
      }
    }
  }
}
```

### Example: Implementing a Translation Animation with Simple Parameters

```ts
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private TAG: string = '[AnimatorTest]'
  private backAnimator: AnimatorResult | undefined = undefined
  private flag: boolean = false
  @State translate_: number = 0

  create() {
    this.backAnimator = this.getUIContext()?.createAnimator(
      new SimpleAnimatorOptions(0, 100)
    )
    this.backAnimator.onFinish = ()=> {
      this.flag = true
      console.info(this.TAG, 'backAnimator onFinish')
    }
    this.backAnimator.onFrame = (value:number)=> {
      this.translate_ = value
    }
  }

  aboutToDisappear() {
    // When the custom component disappears, call finish to end incomplete animations and prevent them from continuing.
    // Since backAnimator references this in onFrame, and this holds backAnimator,
    // set backAnimator stored in the custom component to undefined when the component disappears to avoid memory leak.
    this.backAnimator?.finish();
    this.backAnimator = undefined;
  }

  build() {
    Column() {
      Column() {
        Column()
          .width(100)
          .height(100)
          .translate({x: this.translate_})
          .backgroundColor(Color.Green)
      }
      .width('100%')
      .height(300)

      Column() {
        Column() {
          Button('create')
            .fontSize(30)
            .fontColor(Color.White)
            .onClick(() => {
              this.create()
            })
        }
        .padding(10)

        Column() {
          Button('play')
            .fontSize(30)
            .fontColor(Color.White)
            .onClick(() => {
              this.flag = false
              if(this.backAnimator){
                this.backAnimator.play()
              }
            })
        }
        .padding(10)

        Column() {
          Button('reset')
            .fontSize(30)
            .fontColor(Color.White)
            .onClick(() => {
              if (this.flag) {
                this.flag = false
                if(this.backAnimator){
                  this.backAnimator.reset(
                    new SimpleAnimatorOptions(0, -100)
                      .duration(2000)
                      .easing("ease-in")
                      .fill(FillMode.Forwards)
                      .direction(PlayMode.Alternate)
                      .iterations(2)
                  )
                }
              } else {
                console.info(this.TAG, 'Animation not ended')
              }
            })
        }
        .padding(10)
      }
    }
  }
}
```

![animator](figures/animator.gif)
