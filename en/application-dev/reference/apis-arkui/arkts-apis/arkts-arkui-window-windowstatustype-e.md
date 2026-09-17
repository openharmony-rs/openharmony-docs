# WindowStatusType

Enumerates the window modes.

**Since:** 11

**System capability:** SystemCapability.Window.SessionManager

## UNDEFINED

```TypeScript
UNDEFINED = 0
```

The window mode is not defined by the application.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FULL_SCREEN

```TypeScript
FULL_SCREEN = 1
```

The application is displayed in full screen.

In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state, the window occupies the entire screen with no dock, title bar, or status bar displayed by default.

You can use [maximize()](arkts-arkui-window-window-i.md#maximize) and [setTitleAndDockHoverShown()](arkts-arkui-window-window-i.md#settitleanddockhovershown) to configure whether to display the title bar and dock upon hovering over the hot zone.

The last call takes precedence when both the **maximize()** and **setTitleAndDockHoverShown()** APIs are called.

In non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) state, the window occupies the entire screen with no title bar or dock displayed. You can use [setSpecificSystemBarEnabled()](arkts-arkui-window-window-i.md#setspecificsystembarenabled) to configure whether to display the status bar.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## MAXIMIZE

```TypeScript
MAXIMIZE = 2
```

The application window is maximized. In [freeform window](../../../windowmanager/window-terminology.md#freeform-window) state, the window occupies the entire screen, and the dock, status bar, and title bar are displayed without requiring a hover. This state is unavailable in non-[freeform window](../../../windowmanager/window-terminology.md#freeform-window) state.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## MINIMIZE

```TypeScript
MINIMIZE = 3
```

The application window is minimized.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FLOATING

```TypeScript
FLOATING = 4
```

The application is displayed in a floating window.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## SPLIT_SCREEN

```TypeScript
SPLIT_SCREEN = 5
```

The application is displayed in split-screen mode.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager
