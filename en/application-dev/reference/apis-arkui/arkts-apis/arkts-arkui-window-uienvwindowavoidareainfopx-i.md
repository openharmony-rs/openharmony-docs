# UIEnvWindowAvoidAreaInfoPX

Describes [environment variable](../../../ui/arkts-env-system-property.md) data types for window avoidance areas of different types. All types of window avoidance areas are measured in px.

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## cutout

```TypeScript
cutout: AvoidArea
```

Avoidance area whose [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_CUTOUT** type, in px.

**Type:** [AvoidArea](arkts-arkui-window-avoidarea-i.md)

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

## keyboard

```TypeScript
keyboard: AvoidArea
```

Avoidance area whose [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_KEYBOARD** type, in px.

**Type:** [AvoidArea](arkts-arkui-window-avoidarea-i.md)

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

## navigationIndicator

```TypeScript
navigationIndicator: AvoidArea
```

Avoidance area whose [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_NAVIGATION_INDICATOR** type, in px.

**Type:** [AvoidArea](arkts-arkui-window-avoidarea-i.md)

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

## statusBar

```TypeScript
statusBar: AvoidArea
```

Avoidance area whose [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md) is **TYPE_SYSTEM** type, in px.

**Type:** [AvoidArea](arkts-arkui-window-avoidarea-i.md)

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager
