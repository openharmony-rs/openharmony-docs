# @ohos.resourceschedule.backgroundProcessManager(Background Child Process Management)

The **backgroundProcessManager** module provides APIs for background child process management. You can use these APIs to suppress and unsuppress child processes to prevent child processes from occupying too many system resources and causing system stuttering. The APIs take effect only for the child processes created through [OH_Ability_StartNativeChildProcess](../../../reference/apis-ability-kit/c-apis/capi-native-child-process-h.md#oh_ability_startnativechildprocess).

**Since:** 17

**System capability:** SystemCapability.Resourceschedule.BackgroundProcessManager

## Modules to Import

```TypeScript
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getPowerSaveMode](arkts-backgroundtasks-backgroundprocessmanager-getpowersavemode-f.md) | Obtains the power saving mode of a process. This API uses a promise to return the result. |
| [isPowerSaveMode](arkts-backgroundtasks-backgroundprocessmanager-ispowersavemode-f.md) | Queries whether the process is in power saving mode. This API uses a promise to return the result. |
| [resetProcessPriority](arkts-backgroundtasks-backgroundprocessmanager-resetprocesspriority-f.md) | Unsuppresses the child process. In this case, the child process follows the scheduling policy of the main process. If the scheduling policy of the main process changes, for example, from the background to the foreground, the child process changes with the main process. The effect is the same as calling **resetProcessPriority**. |
| [setPowerSaveMode](arkts-backgroundtasks-backgroundprocessmanager-setpowersavemode-f.md) | Sets the power saving mode for a process. This API uses a promise to return the result. |
| [setProcessPriority](arkts-backgroundtasks-backgroundprocessmanager-setprocesspriority-f.md) | Sets the child process priority. After a child process is suppressed, the CPU resources that can be obtained will be limited. If the scheduling policy of the main process changes, for example, from the background to the foreground, the child process changes with the main process. To suppress the child process, call this API again. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [clearBackgroundApps](arkts-backgroundtasks-backgroundprocessmanager-clearbackgroundapps-f-sys.md) | One-tap background app cleanup |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [PowerSaveMode](arkts-backgroundtasks-backgroundprocessmanager-powersavemode-e.md) | Specifies the power saving mode. |
| [ProcessPriority](arkts-backgroundtasks-backgroundprocessmanager-processpriority-e.md) | Specifies the child process priority. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ClearType](arkts-backgroundtasks-backgroundprocessmanager-cleartype-e-sys.md) | The type of clearing background apps. |
<!--DelEnd-->
