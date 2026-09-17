# AnimatorResult

Defines the animator result.

**Since:** 6

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## cancel

```TypeScript
cancel(): void
```

Cancels the animation, triggering the [onCancel](../../../reference/apis-arkui/js-apis-animator.md#properties) callback. This API is functionally identical to [finish](#finish) except for the callback it triggers. It is recommended that you use the **finish** API to end animations.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See ArkTS-based Declarative Development Paradigm.
```

## finish

```TypeScript
finish(): void
```

Ends the animation, triggering the [onFinish](../../../reference/apis-arkui/js-apis-animator.md#properties) callback.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See ArkTS-based Declarative Development Paradigm.
```

## oncancel

```TypeScript
oncancel: () => void
```

Called when this animation is canceled.

Note: This API is supported since API version 6 and deprecated since API version 12. You are advised to use **onCancel** instead.

**Since:** 6

**Deprecated since:** 12

**Substitutes:** onCancel

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onCancel

```TypeScript
onCancel: () => void
```

Called when this animation is canceled.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onfinish

```TypeScript
onfinish: () => void
```

Called when this animation is finished.

Note: This API is supported since API version 6 and deprecated since API version 12. You are advised to use **onFinish** instead.

**Since:** 6

**Deprecated since:** 12

**Substitutes:** onFinish

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onFinish

```TypeScript
onFinish: () => void
```

Called when this animation is finished.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onframe

```TypeScript
onframe: (progress: number) => void
```

Called when a frame is received.

Note: This API is supported since API version 6 and deprecated since API version 12. You are advised to use **onFrame** instead.

**Since:** 6

**Deprecated since:** 12

**Substitutes:** onFrame

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progress | number | Yes |  |

## onFrame

```TypeScript
onFrame: (progress: number) => void
```

Called when a frame is received.

**progress**: current value of the animation. Value range: [begin, end] defined in [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md). Default value range: [0, 1]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progress | number | Yes |  |

## onrepeat

```TypeScript
onrepeat: () => void
```

Called when this animation repeats.

Note: This API is supported since API version 6 and deprecated since API version 12. You are advised to use **onRepeat** instead.

**Since:** 6

**Deprecated since:** 12

**Substitutes:** onRepeat

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onRepeat

```TypeScript
onRepeat: () => void
```

Called when this animation repeats.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause(): void
```

Pauses this animation.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See ArkTS-based Declarative Development Paradigm.
```

## play

```TypeScript
play(): void
```

Plays this animation. The animation retains the previous playback state. For example, if the animation is set to **reverse** and paused, it will remain in **reverse** when resumed.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See ArkTS-based Declarative Development Paradigm.
```

## reset

```TypeScript
reset(options: AnimatorOptions): void
```

Resets the animation parameters of this animator.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | Yes | Animator options. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The specified page is not found or the object property list is not obtained. |

**Examples**

```TypeScript
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
    // ...
  }
}
```

```TypeScript
See ArkTS-based Declarative Development Paradigm.
```

## reset

```TypeScript
reset(options: AnimatorOptions | SimpleAnimatorOptions): void
```

Resets the animation parameters of this animator. Compared with [reset](#reset), this API accepts parameters of the [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) type.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) &#124; [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | Yes | Animator options. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The specified page is not found or the object property list is not obtained. |

**Examples**

See [reset](#reset)

## reverse

```TypeScript
reverse(): void
```

Plays this animation in reverse order. This API does not take effect when the interpolating spring curve is used.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
See ArkTS-based Declarative Development Paradigm.
```

## setExpectedFrameRateRange

```TypeScript
setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void
```

Sets the expected frame rate range.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rateRange | [ExpectedFrameRateRange](../arkts-components/arkts-arkui-expectedframeraterange-i.md) | Yes | Expected frame rate range. |

**Examples**

```TypeScript
import { AnimatorResult } from '@kit.ArkUI';

let expectedFrameRate: ExpectedFrameRateRange = {
  min: 0,
  max: 120,
  expected: 30
}

@Entry
@Component
struct AnimatorTest {
  private backAnimator: AnimatorResult | undefined = undefined;

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
    // ...
  }
}
```

## update

```TypeScript
update(options: AnimatorOptions): void
```

Updates this animator.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** reset

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | Yes | Animator options. |

**Examples**

```TypeScript
See ArkTS-based Declarative Development Paradigm.
```
