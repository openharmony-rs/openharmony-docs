# WindowPostureMode

Enumerates of window posture mode.

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

## DESKTOP_MODE

```TypeScript
DESKTOP_MODE = 0
```

Desktop mode, when the following conditions are met:
1. The fold status of screen is half folded status (FoldStatus.FOLD_STATUS_HALF_FOLDED).
2. The width of creaseRects obtained via display.getLiveCreaseRegion is greater than its height.
3. The window status is WindowStatusType.FULL_SCREEN or WindowStatusType.MAXIMIZE.
4. The crease region is entirely winthin the window region.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
