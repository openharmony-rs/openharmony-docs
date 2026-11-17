# AvoidAreaInsets

```TypeScript
interface AvoidAreaInsets
```

Avoid area insets of the window.

The avoid area insets indicate the distances that the window content needs to avoid in the four directions(up, down, left, and right) due to the existence of the [avoid area](arkts-arkui-window-avoidarea-i.md).

> **NOTE:** 
> 
> The calculation of the avoid area insets does not include the avoid area of the
> [TYPE_KEYBOARD](arkts-arkui-window-avoidareatype-e.md) type.

**Since:** 26.1.0

<!--Device-window-interface AvoidAreaInsets--><!--Device-window-interface AvoidAreaInsets-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom: number
```

Distance to avoid from the bottom of the window. Unit: px. The value must be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AvoidAreaInsets-bottom: int--><!--Device-AvoidAreaInsets-bottom: int-End-->

**System capability:** SystemCapability.Window.SessionManager

## left

```TypeScript
left: number
```

Distance to avoid from the left of the window. Unit: px. The value must be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AvoidAreaInsets-left: int--><!--Device-AvoidAreaInsets-left: int-End-->

**System capability:** SystemCapability.Window.SessionManager

## right

```TypeScript
right: number
```

Distance to avoid from the right of the window. Unit: px. The value must be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AvoidAreaInsets-right: int--><!--Device-AvoidAreaInsets-right: int-End-->

**System capability:** SystemCapability.Window.SessionManager

## top

```TypeScript
top: number
```

Distance to avoid from the top of the window. Unit: px. The value must be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AvoidAreaInsets-top: int--><!--Device-AvoidAreaInsets-top: int-End-->

**System capability:** SystemCapability.Window.SessionManager
