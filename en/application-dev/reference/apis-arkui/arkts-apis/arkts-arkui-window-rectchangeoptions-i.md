# RectChangeOptions

```TypeScript
interface RectChangeOptions
```

Describes the value and reason returned upon a window rectangle (position and size) change.

**Since:** 12

<!--Device-window-interface RectChangeOptions--><!--Device-window-interface RectChangeOptions-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## reason

```TypeScript
reason: RectChangeReason
```

Reason for the window rectangle change.

**Type:** [RectChangeReason](arkts-arkui-window-rectchangereason-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RectChangeOptions-reason: RectChangeReason--><!--Device-RectChangeOptions-reason: RectChangeReason-End-->

**System capability:** SystemCapability.Window.SessionManager

## rect

```TypeScript
rect: Rect
```

New value of the window rectangle.

**Type:** [Rect](arkts-arkui-window-rect-i.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RectChangeOptions-rect: Rect--><!--Device-RectChangeOptions-rect: Rect-End-->

**System capability:** SystemCapability.Window.SessionManager
