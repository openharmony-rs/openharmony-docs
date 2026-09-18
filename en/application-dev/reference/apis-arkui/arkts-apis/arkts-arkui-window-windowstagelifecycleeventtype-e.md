# WindowStageLifecycleEventType

Enumerates the lifecycle state types of a WindowStage.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## SHOWN

```TypeScript
SHOWN = 1
```

The WindowStage is shown in the foreground, for example, when launching from the application icon, triggered whether it is the first launch or resuming from the background.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## RESUMED

```TypeScript
RESUMED = 2
```

The WindowStage is in the foreground and interactive, for example, when the application is open and can interact with the user.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## PAUSED

```TypeScript
PAUSED = 3
```

The WindowStage is in the foreground but not interactive, for example, when the application is in the foreground and is entering the multitasking screen.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## HIDDEN

```TypeScript
HIDDEN = 4
```

The WindowStage is running in the background, for example, when the application exists after swiping up or the application window is closed.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
