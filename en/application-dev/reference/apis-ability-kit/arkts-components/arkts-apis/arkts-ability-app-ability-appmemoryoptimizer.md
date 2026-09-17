# @ohos.app.ability.appMemoryOptimizer(Application Memory Optimizer)

appMemoryOptimizer provides application memory optimization capabilities, including performing file page cache eviction on specified files, performing file page cache eviction on specified modules.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { appMemoryOptimizer } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [evictFilePages](arkts-ability-appmemoryoptimizer-evictfilepages-f.md) | Sends a request to the system to release file page cache of specified files. The system determines whether to actually perform the release based on the current memory status, and success is not guaranteed. |
| [evictModuleFilePages](arkts-ability-appmemoryoptimizer-evictmodulefilepages-f.md) | Sends a request to the system to release file page cache of specified modules. The system determines whether to actually perform the release based on the current memory status, and success is not guaranteed. The system reads the memory_optimizer.json configuration file of the corresponding module, obtains the evictFilePages array, and performs file page cache eviction on the files in the array. |
