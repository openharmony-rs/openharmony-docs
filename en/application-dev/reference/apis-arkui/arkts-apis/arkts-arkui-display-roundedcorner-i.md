# RoundedCorner

```TypeScript
interface RoundedCorner
```

Describes a single rounded corner on the screen.

**Since:** 23

<!--Device-display-interface RoundedCorner--><!--Device-display-interface RoundedCorner-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-RoundedCorner-readonly position: Position--><!--Device-RoundedCorner-readonly position: Position-End-->

**System capability:** SystemCapability.Window.SessionManager

## radius

```TypeScript
readonly radius: number
```

The radius of round corner, measured in px.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-RoundedCorner-readonly radius: int--><!--Device-RoundedCorner-readonly radius: int-End-->

**System capability:** SystemCapability.Window.SessionManager

## type

```TypeScript
readonly type: CornerType
```

Type of the rounded corner.

**Type:** [CornerType](arkts-arkui-display-cornertype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-RoundedCorner-readonly type: CornerType--><!--Device-RoundedCorner-readonly type: CornerType-End-->

**System capability:** SystemCapability.Window.SessionManager
