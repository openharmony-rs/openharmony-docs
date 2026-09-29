# ProcessPriority

```TypeScript
export enum ProcessPriority
```

Specifies the child process priority.

**Since:** 17

<!--Device-backgroundProcessManager-export enum ProcessPriority--><!--Device-backgroundProcessManager-export enum ProcessPriority-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

## PROCESS_BACKGROUND

```TypeScript
PROCESS_BACKGROUND = 1
```

Compared with **PROCESS_INACTIVE**, **PROCESS_LOWER** has a more significant suppression effect and obtains fewer CPU resources. You are advised to set this priority when executing background child processes that cannot be perceived by users, such as background image-text pages.

**Since:** 17

<!--Device-ProcessPriority-PROCESS_BACKGROUND = 1--><!--Device-ProcessPriority-PROCESS_BACKGROUND = 1-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

## PROCESS_INACTIVE

```TypeScript
PROCESS_INACTIVE = 2
```

You are advised to set this priority when executing background child processes that can be perceived by users, such as audio playback and navigation.

**Since:** 17

<!--Device-ProcessPriority-PROCESS_INACTIVE = 2--><!--Device-ProcessPriority-PROCESS_INACTIVE = 2-End-->

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager
