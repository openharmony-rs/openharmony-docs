# MaximizeOptions

Optional configuration for maximizing.

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## acrossDisplayPresentation

```TypeScript
acrossDisplayPresentation?: AcrossDisplayPresentation
```

The parameter controls the across-display mode policy of main windows. This parameter can be called properly only on 2-in-1 devices with folding capabilities. If it is called on other device types, it has no effect.

**Type:** [AcrossDisplayPresentation](arkts-arkui-window-acrossdisplaypresentation-e.md)

**Default:** AcrossDisplayPresentation.FOLLOW_ACROSS_DISPLAY_SETTING

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## maximizePresentation

```TypeScript
maximizePresentation?: MaximizePresentation
```

Layout when the window is maximized.

**Type:** [MaximizePresentation](arkts-arkui-window-maximizepresentation-e.md)

**Default:** MaximizePresentation.ENTER_IMMERSIVE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## snapshotAnimationConfig

```TypeScript
snapshotAnimationConfig?: WindowSnapshotAnimationConfig
```

The configuration of snapshot animation. If not specified, the system default animation will be used. When both the duration and delay parameters are set to 0, it means the snapshot animation is canceled.

**Type:** [WindowSnapshotAnimationConfig](arkts-arkui-window-windowsnapshotanimationconfig-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
