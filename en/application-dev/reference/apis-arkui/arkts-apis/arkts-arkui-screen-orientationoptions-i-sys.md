# OrientationOptions (System API)

The parameters for setting orientation

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { screen } from '@kit.ArkUI';
```

## ignoreRotationLock

```TypeScript
ignoreRotationLock?: boolean
```

Whether to ignore rotation lock. The value true means allowing the screen to rotate even if some system windows lock screen rotation, while false means preventing the screen from rotating when any system windows lock it.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## needAnimation

```TypeScript
needAnimation?: boolean
```

Whether to need animation. The value true means rotating the screen with animation, while false means rotating the screen without animation.

**Type:** boolean

**Default:** true

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.
