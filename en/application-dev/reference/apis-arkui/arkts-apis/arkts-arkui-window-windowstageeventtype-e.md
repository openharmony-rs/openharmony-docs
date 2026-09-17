# WindowStageEventType

Enumerates the lifecycle event types of a WindowStage.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## SHOWN

```TypeScript
SHOWN = 1
```

The WindowStage is shown in the foreground, for example, when launching from the application icon, triggered whether it is the first launch or resuming from the background.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## ACTIVE

```TypeScript
ACTIVE = 2
```

The WindowStage gains focus, for example, the state of the application window after handling a click event, or the state after the application is launched.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## INACTIVE

```TypeScript
INACTIVE = 3
```

The WindowStage loses focus, for example, the state of the window that was in focus when a new application is opened or another window is clicked.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## HIDDEN

```TypeScript
HIDDEN = 4
```

The WindowStage is running in the background, for example, when the application exists after swiping up or the application window is closed.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## RESUMED

```TypeScript
RESUMED = 5
```

The WindowStage is in the foreground and interactive, for example, when the application is open and can interact with the user.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## PAUSED

```TypeScript
PAUSED = 6
```

The WindowStage is in the foreground but not interactive, for example, when the application is in the foreground and is entering the multitasking screen.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.WindowManager.WindowManager.Core
