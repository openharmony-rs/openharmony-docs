# FloatViewState

Enumerates the states of the float view.

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

## STARTED

```TypeScript
STARTED = 1
```

The float view has been started and displayed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## HIDDEN

```TypeScript
HIDDEN = 2
```

The float view has been hidden. This event is triggered when the user swipes up to enter the multitasking screen or when the [setFloatViewVisibilityInApp](arkts-arkui-floatview-floatviewcontroller-i.md#setfloatviewvisibilityinapp) API is called to hide the float view when the application is in the foreground and the application is in the foreground.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## STOPPED

```TypeScript
STOPPED = 3
```

The float view has been stopped.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## IN_SIDEBAR

```TypeScript
IN_SIDEBAR = 4
```

The float view is in the sidebar.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## IN_FLOATING_BALL

```TypeScript
IN_FLOATING_BALL = 5
```

The float view is switched to the floating ball.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## ERROR

```TypeScript
ERROR = 6
```

An exception occurs in the float view.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
