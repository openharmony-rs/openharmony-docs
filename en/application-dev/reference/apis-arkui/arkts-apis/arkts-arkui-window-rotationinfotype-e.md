# RotationInfoType

Enumerates the types of rotation information.

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

## WINDOW_ORIENTATION

```TypeScript
WINDOW_ORIENTATION = 0
```

Window's screen orientation, based on how the Window module defines landscape/portrait modes.

Note that it maps to the **orientation** parameter in [RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md).

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

## DISPLAY_ORIENTATION

```TypeScript
DISPLAY_ORIENTATION = 1
```

Physical screen orientation, based on how the Display module defines landscape/portrait modes.

It maps to the **orientation** property of the [display](arkts-arkui-display-displaystate-e.md) object.

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager

## DISPLAY_ROTATION

```TypeScript
DISPLAY_ROTATION = 2
```

Physical rotation angle of the device's screen (in degrees, clockwise).

It maps to the **rotation** property of the [display](arkts-arkui-display-displaystate-e.md) object.

**Since:** 23

**System capability:** SystemCapability.Window.SessionManager
