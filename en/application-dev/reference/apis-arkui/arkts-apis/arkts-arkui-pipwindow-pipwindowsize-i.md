# PiPWindowSize

Describes the size of a PiP window.

**Since:** 15

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## height

```TypeScript
height: number
```

Window height, in px. The value must be a positive integer and cannot be greater than the screen height.

**Type:** number

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

## scale

```TypeScript
scale: number
```

Scale factor of the window, representing the display size relative to the width and height. The value is a floating-point number in the range (0.0, 1.0]. The value **1** means that the window matches the specified width and height.

**Type:** number

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

## width

```TypeScript
width: number
```

Window width, in px. The value must be a positive integer and cannot be greater than the screen width.

**Type:** number

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager
