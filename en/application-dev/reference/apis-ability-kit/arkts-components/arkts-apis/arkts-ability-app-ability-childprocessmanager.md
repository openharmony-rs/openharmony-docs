# @ohos.app.ability.childProcessManager(Child Process Management)

The childProcessManager module provides the child process management capability. Currently, it provides APIs to create and start a child process The created child process will exit when the parent process exits and cannot run independently.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getChildProcessInfos](arkts-ability-childprocessmanager-getchildprocessinfos-f.md) | Obtains the information about the child processes of the current application. This API uses a promise to return the result. The returned child processes include those created through [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md) (in APP_SPAWN_FORK mode), [startArkChildProcess](arkts-ability-childprocessmanager-startarkchildprocess-f.md), and [startNativeChildProcess](arkts-ability-childprocessmanager-startnativechildprocess-f.md). [OH_Ability_CreateNativeChildProcess] [OH_Ability_CreateNativeChildProcessWithConfigs] [OH_Ability_StartNativeChildProcess] [OH_Ability_StartNativeChildProcessWithConfigs] |
| [isArkChildProcessSupported](arkts-ability-childprocessmanager-isarkchildprocesssupported-f.md) | Checks whether the caller is allowed to create ark child processes on this device. Some devices may not support creating ark child processes, so it is recommended to use this interface to verify support beforehand. |
| [isNativeChildProcessSupported](arkts-ability-childprocessmanager-isnativechildprocesssupported-f.md) | Checks whether the caller is allowed to create native child processes on this device. Some devices may not support creating native child processes, so it is recommended to use this interface to verify support beforehand. |
| [startArkChildProcess](arkts-ability-childprocessmanager-startarkchildprocess-f.md) | Starts an [ArkTS child process](../../../application-models/ability-terminology.md#arkts-child-process). This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 801 is returned. |
| [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md#startchildprocess) | Starts an [ArkTS child process](../../../application-models/ability-terminology.md#arkts-child-process). This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 16000061 is returned. |
| [startChildProcess](arkts-ability-childprocessmanager-startchildprocess-f.md#startchildprocess-1) | Starts an [ArkTS child process](../../../application-models/ability-terminology.md#arkts-child-process). This API uses an asynchronous callback to return the result. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 16000061 is returned. |
| [startNativeChildProcess](arkts-ability-childprocessmanager-startnativechildprocess-f.md) | Starts a [native child process](../../../application-models/ability-terminology.md#native-child-process). This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 801 is returned. |

### Enums

| Name | Description |
| --- | --- |
| [StartMode](arkts-ability-childprocessmanager-startmode-e.md) | Enumerates the child process start modes. |

### Types

| Name | Description |
| --- | --- |
| [ChildProcessInformation](arkts-ability-childprocessmanager-childprocessinformation-t.md) | Defines the child process information. |
