# WindowCreateParams

```TypeScript
interface WindowCreateParams
```

Describes the window parameters during application startup.

**Since:** 20

<!--Device-window-interface WindowCreateParams--><!--Device-window-interface WindowCreateParams-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## animationParams

```TypeScript
animationParams?: StartAnimationParams
```

The params of start animation

**Type:** [StartAnimationParams](arkts-arkui-window-startanimationparams-i.md)

**Since:** 20

<!--Device-WindowCreateParams-animationParams?: StartAnimationParams--><!--Device-WindowCreateParams-animationParams?: StartAnimationParams-End-->

**System capability:** SystemCapability.Window.SessionManager

## excludeFromDock

```TypeScript
excludeFromDock?: boolean
```

Whether to hide the dock icon and the hover thumbnail preview. If true, the current window will not display its icon and hover thumbnail preview on the dock. This parameter only takes effect within the same application.

**Type:** boolean

**Default:** false

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowCreateParams-excludeFromDock?: boolean--><!--Device-WindowCreateParams-excludeFromDock?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## excludeFromRecent

```TypeScript
excludeFromRecent?: boolean
```

Whether to hide the window from the multitasking center. If true, the current window will not be displayed in the multitasking center. This parameter only takes effect within the same application.

**Type:** boolean

**Default:** false

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowCreateParams-excludeFromRecent?: boolean--><!--Device-WindowCreateParams-excludeFromRecent?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## minimizeOnStart

```TypeScript
minimizeOnStart?: boolean
```

Whether the window starts in a minimized state. If true, the window will not be brought to the foreground. This parameter only takes effect within the same application.

**Type:** boolean

**Default:** false

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowCreateParams-minimizeOnStart?: boolean--><!--Device-WindowCreateParams-minimizeOnStart?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager

## needAnimation

```TypeScript
needAnimation?: boolean
```

Whether to need start animation

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowCreateParams-needAnimation?: boolean--><!--Device-WindowCreateParams-needAnimation?: boolean-End-->

**System capability:** SystemCapability.Window.SessionManager
