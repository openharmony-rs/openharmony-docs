# TransitionAnimation

Describes the window transition animation.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## config

```TypeScript
config: WindowAnimationConfig
```

Transition animation configuration.

**Type:** [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

## opacity

```TypeScript
opacity?: number
```

Opacity of the window during the transition animation. If this parameter is set to **0**, the window is completely transparent. The default value is **1.0**. When the animation type is **WindowTransitionType.DESTROY**, this represents the opacity at the end of the animation. The value ranges from 0 to 1.0. The value is reset to **1.0** when the animation ends.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager
