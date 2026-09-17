# Position

Describes a coordinate position. In the global coordinate system, the origin is the top-left corner of the primary screen. In the relative coordinate system, the origin is the top-left corner of the specified screen.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## x

```TypeScript
x: number
```

X coordinate relative to the origin, measured in px. The value must be a 32-bit signed integer, and floating- point numbers are rounded down.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## y

```TypeScript
y: number
```

Y coordinate relative to the origin, measured in px. The value must be a 32-bit signed integer, and floating- point numbers are rounded down.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager
