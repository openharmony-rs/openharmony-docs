# StartupTask

The module provides capabilities related to startup tasks in [AppStartup](../../../application-models/app-startup.md).

**Since:** 12

**Decorator:** @Sendable

**System capability:** SystemCapability.Ability.AppStartup

## Modules to Import

```TypeScript
import { StartupTask } from '@kit.AbilityKit';
```

## init

```TypeScript
init(context: AbilityStageContext): Promise<Object | void>
```

Called when all the dependent startup tasks are complete. You can initialize the startup task in this callback. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppStartup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [AbilityStageContext](arkts-ability-abilitystagecontext-c.md) | Yes | Context environment of the [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Object &#124; void&gt; | Promise used to return the execution result. |

**Examples**

```TypeScript
import { StartupTask, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Sendable
export default class StartupTask_001 extends StartupTask {
  constructor() {
    super();
  }
  async init(context: common.AbilityStageContext) {
    hilog.info(0x0000, 'testTag', 'StartupTask_001 init.');
    // ...
    
    return 'StartupTask_001';
  }

  onDependencyCompleted(dependency: string, result: Object): void {
    // ...
  }
}
```

## onDependencyCompleted

```TypeScript
onDependencyCompleted?(dependency: string, result: Object): void
```

Called when the dependent startup task is complete.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppStartup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dependency | string | Yes | Name of the dependent startup task. |
| result | Object | Yes | Execution result of [init](#init) of the dependent startup task. |

**Examples**

```TypeScript
import { StartupTask, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Sendable
export default class StartupTask_001 extends StartupTask {
  constructor() {
    super();
  }

  async init(context: common.AbilityStageContext) {
    // ...
  }

  onDependencyCompleted(dependency: string, result: Object): void {
    hilog.info(0x0000, 'testTag', 'StartupTask_001 onDependencyCompleted, dependency: %{public}s, result: %{public}s',
      dependency, JSON.stringify(result));
    // ...
  }
}
```
