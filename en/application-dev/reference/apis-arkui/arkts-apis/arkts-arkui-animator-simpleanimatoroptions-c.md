# SimpleAnimatorOptions

```TypeScript
export declare class SimpleAnimatorOptions
```

Defines a simple animation parameter object. Unlike **AnimatorOptions**, this object comes with some default values for certain animation parameters, so you do not have to set them manually.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(begin: number, end: number)
```

A constructor used to create a **SimpleAnimatorOptions** instance.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| begin | number | Yes | Start point of the animation interpolation. |
| end | number | Yes | End point of animation interpolation. |

**Examples**

See ArkTS-based Declarative Development Paradigm.

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200); // Animation interpolation from 100 to 200, with other animation parameters set to default values.

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}
```

## delay

```TypeScript
delay(delay: number): SimpleAnimatorOptions
```

Sets the playback delay for this animation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delay | number | Yes | Playback delay, in milliseconds. The value **0** indicates no delay. If the value specified is a negative number, the animation starts playing ahead of its scheduled time. If the amount of time by which the playback is advanced exceeds the total duration of the animation, the animation immediately skips to its end state.<br>Default value: **0** |

**Return value:**

| Type | Description |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | **SimpleAnimatorOptions** object for animation parameters. |

**Examples**

See ArkTS-based Declarative Development Paradigm.

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).delay(500);

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}
```

## direction

```TypeScript
direction(direction: PlayMode): SimpleAnimatorOptions
```

Sets the playback direction for this animator animation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [PlayMode](arkts-arkui-playmode-e.md) | Yes | Playback direction.<br>Default value: **PlayMode.Normal** |

**Return value:**

| Type | Description |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | **SimpleAnimatorOptions** object for animation parameters. |

**Examples**

See ArkTS-based Declarative Development Paradigm.

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).direction(PlayMode.Alternate);

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}
```

## duration

```TypeScript
duration(duration: number): SimpleAnimatorOptions
```

Sets the animation duration.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| duration | number | Yes | Animation duration, in milliseconds.<br>Default value: **1000** |

**Return value:**

| Type | Description |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | **SimpleAnimatorOptions** object for animation parameters. |

**Examples**

See ArkTS-based Declarative Development Paradigm.

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).duration(500);

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}
```

## easing

```TypeScript
easing(curve: string): SimpleAnimatorOptions
```

Sets the interpolation curve for this animation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| curve | string | Yes | Interpolation curve. For details, see [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md).<br> Default value: **"ease"** |

**Return value:**

| Type | Description |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | **SimpleAnimatorOptions** object for animation parameters. |

**Examples**

See ArkTS-based Declarative Development Paradigm.

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).easing("ease-in");

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}
```

## fill

```TypeScript
fill(fillMode: FillMode): SimpleAnimatorOptions
```

Sets the fill mode for this animation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fillMode | [FillMode](arkts-arkui-fillmode-e.md) | Yes | Fill mode, which affects how the animation behaves during the delay period and after it ends.<br>Default value: **FillMode.Forwards** |

**Return value:**

| Type | Description |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | **SimpleAnimatorOptions** object for animation parameters. |

**Examples**

See ArkTS-based Declarative Development Paradigm.

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).fill(FillMode.Forwards);

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}
```

## iterations

```TypeScript
iterations(iterations: number): SimpleAnimatorOptions
```

Sets the number of times that this animation is played.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| iterations | number | Yes | Number of times that the animation is played. The value **0** means the animation is not played, and **-1** means the animation is played for an unlimited number of times.<br>Default value: **1** |

**Return value:**

| Type | Description |
| --- | --- |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | **SimpleAnimatorOptions** object for animation parameters. |

**Examples**

See ArkTS-based Declarative Development Paradigm.

```TypeScript
import { AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';

@Entry
@Component
struct AnimatorTest {
  private animatorResult: AnimatorResult | undefined = undefined;
  options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).iterations(3);

  create() {
    this.animatorResult = this.getUIContext().createAnimator(this.options);
  }

  build() {
    // ......
  }
}
```
