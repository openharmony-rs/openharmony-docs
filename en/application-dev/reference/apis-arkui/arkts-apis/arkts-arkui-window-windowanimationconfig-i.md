# WindowAnimationConfig

Describes the configuration for window animation.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## curve

```TypeScript
curve: WindowAnimationCurve
```

Type of animation curve.

**Type:** [WindowAnimationCurve](arkts-arkui-window-windowanimationcurve-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

## duration

```TypeScript
duration?: number
```

Duration for playing the animation, in milliseconds (ms).

The default value is 0, and the maximum value is 3000.

Whether it is required depends on the animation curve type.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

## param

```TypeScript
param?: WindowAnimationCurveParam
```

Parameters for the animation curve. Whether it is required depends on the animation curve type.

**Type:** [WindowAnimationCurveParam](arkts-arkui-windowanimationcurveparam-t.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager
