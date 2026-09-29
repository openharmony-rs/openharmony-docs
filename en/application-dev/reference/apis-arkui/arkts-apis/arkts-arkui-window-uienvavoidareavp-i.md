# UIEnvAvoidAreaVP

```TypeScript
interface UIEnvAvoidAreaVP
```

Describes the information about the window avoidance area in units of vp, which requires careful attention during [immersive layout](../../../windowmanager/window-terminology.md#immersive-layout) adaptation.

**Since:** 23

<!--Device-window-interface UIEnvAvoidAreaVP--><!--Device-window-interface UIEnvAvoidAreaVP-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## bottomRect

```TypeScript
bottomRect: RectInVP
```

Rectangle centered at the bottom of the window's two diagonals, in vp.

**Type:** [RectInVP](arkts-arkui-window-rectinvp-i.md)

**Since:** 23

<!--Device-UIEnvAvoidAreaVP-bottomRect: RectInVP--><!--Device-UIEnvAvoidAreaVP-bottomRect: RectInVP-End-->

**System capability:** SystemCapability.Window.SessionManager

## leftRect

```TypeScript
leftRect: RectInVP
```

Rectangle centered to the left of the window's two diagonals, in vp.

**Type:** [RectInVP](arkts-arkui-window-rectinvp-i.md)

**Since:** 23

<!--Device-UIEnvAvoidAreaVP-leftRect: RectInVP--><!--Device-UIEnvAvoidAreaVP-leftRect: RectInVP-End-->

**System capability:** SystemCapability.Window.SessionManager

## rightRect

```TypeScript
rightRect: RectInVP
```

Rectangle centered to the right of the window's two diagonals, in vp.

**Type:** [RectInVP](arkts-arkui-window-rectinvp-i.md)

**Since:** 23

<!--Device-UIEnvAvoidAreaVP-rightRect: RectInVP--><!--Device-UIEnvAvoidAreaVP-rightRect: RectInVP-End-->

**System capability:** SystemCapability.Window.SessionManager

## topRect

```TypeScript
topRect: RectInVP
```

Rectangle centered at the top of the window's two diagonals, in vp.

**Type:** [RectInVP](arkts-arkui-window-rectinvp-i.md)

**Since:** 23

<!--Device-UIEnvAvoidAreaVP-topRect: RectInVP--><!--Device-UIEnvAvoidAreaVP-topRect: RectInVP-End-->

**System capability:** SystemCapability.Window.SessionManager

## visible

```TypeScript
visible: boolean
```

Whether the avoid area is visible. **true** if visible, **false** otherwise.

**Type:** boolean

**Since:** 23

<!--Device-UIEnvAvoidAreaVP-visible: boolean--><!--Device-UIEnvAvoidAreaVP-visible: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager
