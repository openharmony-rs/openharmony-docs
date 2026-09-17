# AcrossDisplayPresentation

Enum for across-display policy used when maximizing in the half-folded state of a foldable 2-in-1 device.

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

## FOLLOW_ACROSS_DISPLAY_SETTING

```TypeScript
FOLLOW_ACROSS_DISPLAY_SETTING = 0
```

Indicates following the current acrossDisplayPresentation. If the acrossDisplayPresentation has not been set, the default system policy applies: In the half-folded state of the device, the window enters single-screen maximization (i.e., when maximized, the window is displayed only on the upper or lower half of the screen). In the expanded state, the window is maximized and remains across-display mode (i.e., spanning across both the upper and lower displays) when folded back to the half-folded state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## ENTER_ACROSS_DISPLAY_MODE

```TypeScript
ENTER_ACROSS_DISPLAY_MODE = 1
```

In the half-folded state of the device, the window could directly enter the across-display mode. In the expanded state, the window is maximized and remains across-display mode when folded back to the half-folded state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## EXIT_ACROSS_DISPLAY_MODE

```TypeScript
EXIT_ACROSS_DISPLAY_MODE = 2
```

In the half-folded state of the device, the window exits across-display mode and enters single-screen maximization In the expanded state, the window is maximized and will exit across-display mode upon re-entering half-folded.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
