# RelativePosition

Describes a coordinate position in the relative coordinate system, with the origin in the top-left corner of the screen specified by **displayId**.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## displayId

```TypeScript
displayId: number
```

Display ID for the relative coordinates. Only integers are supported, and the value must be greater than or equal to 0.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## position

```TypeScript
position: Position
```

Coordinates with the top-left corner of the screen specified by **displayId** as the origin.

**Type:** [Position](arkts-arkui-display-position-i.md)

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager
