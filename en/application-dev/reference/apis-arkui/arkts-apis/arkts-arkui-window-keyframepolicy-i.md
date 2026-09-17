# KeyFramePolicy

Describes the configuration for keyframe policies.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## animationDelay

```TypeScript
animationDelay?: number
```

Delay before the animation for keyframe layout changes starts, in ms. The default value is **100**. The value is **0** or a positive integer. Floating-point values are rounded down.

**Type:** number

**Default:** 100

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## animationDuration

```TypeScript
animationDuration?: number
```

Duration of the animation for keyframe layout changes, in ms. The default value is **100**. The value is **0** or a positive integer. Floating-point values are rounded down.

**Type:** number

**Default:** 100

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## distance

```TypeScript
distance?: number
```

Distance interval for triggering keyframe layout changes via dragging, in px. The default value is **1000**. The value is **0** or a positive integer. Floating-point values are rounded down. If the value is 0, the drag distance is ignored. It works with **interval** using an OR condition. If either of them is met, the layout change starts.

**Type:** number

**Default:** 1000

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## enable

```TypeScript
enable: boolean
```

Whether to enable keyframes. **true** to enable, **false** otherwise.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## interval

```TypeScript
interval?: number
```

Time interval for triggering keyframe layout changes via dragging, in ms. The default value is **1000**. The value is a positive integer. Floating-point values are rounded down. It works with **distance** using an OR condition. If either of them is met, the layout change starts.

**Type:** number

**Default:** 1000

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager
