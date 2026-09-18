# StartAnimationSystemParams (System API)

Describes the start animation configuration. This API works only for full-screen applications.

The configuration does not take effect for inter-application transitions, where the default animation of the system is used.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## animationConfig

```TypeScript
animationConfig?: WindowAnimationConfig
```

Configuration for the window animation. The default animation curve is **WindowAnimationCurve.LINEAR**, and the duration is **0**.

**Type:** [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md)

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## type

```TypeScript
type: AnimationType
```

Type of the window animation.

**Type:** [AnimationType](arkts-arkui-window-animationtype-e.md)

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.
