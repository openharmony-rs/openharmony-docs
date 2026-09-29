# KeyboardInfo

```TypeScript
interface KeyboardInfo
```

Describes the information about the soft keyboard window.

**Since:** 18

<!--Device-window-interface KeyboardInfo--><!--Device-window-interface KeyboardInfo-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## animated

```TypeScript
animated?: boolean
```

Whether there is a show/hide animation. **true** if there is a show/hide animation, **false** otherwise.

**Type:** boolean

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-KeyboardInfo-animated?: boolean--><!--Device-KeyboardInfo-animated?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## beginRect

```TypeScript
beginRect: Rect
```

Position and size of the soft keyboard before the animation starts.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-KeyboardInfo-beginRect: Rect--><!--Device-KeyboardInfo-beginRect: Rect-End-->

**System capability:** SystemCapability.Window.SessionManager

## config

```TypeScript
config?: WindowAnimationConfig
```

Animation configuration.

**Type:** [WindowAnimationConfig](arkts-arkui-window-windowanimationconfig-i.md)

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-KeyboardInfo-config?: WindowAnimationConfig--><!--Device-KeyboardInfo-config?: WindowAnimationConfig-End-->

**System capability:** SystemCapability.Window.SessionManager

## endRect

```TypeScript
endRect: Rect
```

Position and size of the soft keyboard after the animation ends.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-KeyboardInfo-endRect: Rect--><!--Device-KeyboardInfo-endRect: Rect-End-->

**System capability:** SystemCapability.Window.SessionManager
