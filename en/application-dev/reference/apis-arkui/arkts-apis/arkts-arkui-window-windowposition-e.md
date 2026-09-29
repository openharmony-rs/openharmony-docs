# WindowPosition

```TypeScript
enum WindowPosition
```

Enumerates the target z-order to which the z-order of a main window can be adjusted.

**Since:** 26.0.1

<!--Device-window-enum WindowPosition--><!--Device-window-enum WindowPosition-End-->

**System capability:** SystemCapability.Window.SessionManager

## NOT_TOPMOST

```TypeScript
NOT_TOPMOST = -3
```

Not topmost, normal mode. Used as an independent action to cancel the global topmost state of a main window, and you need the ohos.permission.WINDOW_TOPMOST permission to cancel

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowPosition-NOT_TOPMOST = -3--><!--Device-WindowPosition-NOT_TOPMOST = -3-End-->

**System capability:** SystemCapability.Window.SessionManager

## TOPMOST

```TypeScript
TOPMOST = -2
```

Global topmost. To set this value, you need the ohos.permission.WINDOW_TOPMOST permission.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowPosition-TOPMOST = -2--><!--Device-WindowPosition-TOPMOST = -2-End-->

**System capability:** SystemCapability.Window.SessionManager

## BOTTOM

```TypeScript
BOTTOM = -1
```

Places the main window at the bottom of all application main windows,for a single adjustment.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowPosition-BOTTOM = -1--><!--Device-WindowPosition-BOTTOM = -1-End-->

**System capability:** SystemCapability.Window.SessionManager

## TOP

```TypeScript
TOP = 0
```

Places the main window at the top of all application main windows, for a single adjustment.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowPosition-TOP = 0--><!--Device-WindowPosition-TOP = 0-End-->

**System capability:** SystemCapability.Window.SessionManager
