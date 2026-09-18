# RoundedCorner

Describes a single rounded corner on the screen.

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## position

```TypeScript
readonly position: Position
```

Coordinates of the center point of the rounded corner.

**Type:** [Position](arkts-arkui-display-position-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Window.SessionManager

## radius

```TypeScript
readonly radius: number
```

The radius of round corner, measured in px.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Window.SessionManager

## type

```TypeScript
readonly type: CornerType
```

Type of the rounded corner.

**Type:** [CornerType](arkts-arkui-display-cornertype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Window.SessionManager
