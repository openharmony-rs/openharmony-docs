# WindowStageLifecycleEventType

```TypeScript
enum WindowStageLifecycleEventType
```

Enumerates the lifecycle state types of a WindowStage.

**Since:** 20

<!--Device-window-enum WindowStageLifecycleEventType--><!--Device-window-enum WindowStageLifecycleEventType-End-->

**System capability:** SystemCapability.Window.SessionManager

## HIDDEN

```TypeScript
HIDDEN = 4
```

The WindowStage is running in the background, for example, when the application exists after swiping up or the application window is closed.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowStageLifecycleEventType-HIDDEN = 4--><!--Device-WindowStageLifecycleEventType-HIDDEN = 4-End-->

**System capability:** SystemCapability.Window.SessionManager

## PAUSED

```TypeScript
PAUSED = 3
```

The WindowStage is in the foreground but not interactive, for example, when the application is in the foreground and is entering the multitasking screen.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowStageLifecycleEventType-PAUSED = 3--><!--Device-WindowStageLifecycleEventType-PAUSED = 3-End-->

**System capability:** SystemCapability.Window.SessionManager

## RESUMED

```TypeScript
RESUMED = 2
```

The WindowStage is in the foreground and interactive, for example, when the application is open and can interact with the user.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowStageLifecycleEventType-RESUMED = 2--><!--Device-WindowStageLifecycleEventType-RESUMED = 2-End-->

**System capability:** SystemCapability.Window.SessionManager

## SHOWN

```TypeScript
SHOWN = 1
```

The WindowStage is shown in the foreground, for example, when launching from the application icon, triggered whether it is the first launch or resuming from the background.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-WindowStageLifecycleEventType-SHOWN = 1--><!--Device-WindowStageLifecycleEventType-SHOWN = 1-End-->

**System capability:** SystemCapability.Window.SessionManager
