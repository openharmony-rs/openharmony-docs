# @ohos.app.appstartup.startupManager(AppStartup Management)

The module provides the capability to manage startup tasks in [AppStartup](../../../application-models/app-startup.md). The APIs of this module can be called only on the main thread.

> **NOTE:** 
> 
> This module supports .so file preloading since API version 18.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppStartup

## Modules to Import

```TypeScript
import { startupManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getStartupTaskResult](arkts-ability-startupmanager-getstartuptaskresult-f.md) | Obtains the execution result of a startup task or .so file preloading task. |
| [isStartupTaskInitialized](arkts-ability-startupmanager-isstartuptaskinitialized-f.md) | Checks whether a startup task or .so file preloading task is initialized. |
| [removeAllStartupTaskResults](arkts-ability-startupmanager-removeallstartuptaskresults-f.md) | Removes all startup task results. If there are preloading tasks for .so files, the corresponding .so files is set to the unloaded state. However,so files that have already been loaded in the cache will not be removed. |
| [removeStartupTaskResult](arkts-ability-startupmanager-removestartuptaskresult-f.md) | Removes the initialization result of a startup task or .so file preloading task. |
| [run](arkts-ability-startupmanager-run-f.md#run) | Runs startup tasks or loads .so files. |
| [run](arkts-ability-startupmanager-run-f.md#run-1) | Runs startup tasks or loads .so files. You can specify [AbilityStageContext](arkts-ability-abilitystagecontext-c.md) for loading startup tasks. This API uses a promise to return the result. |
