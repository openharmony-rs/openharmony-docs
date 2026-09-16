# StartupTask

本模块提供[应用启动框架](../../../application-models/app-startup.md)任务的相关能力。开发者可继承StartupTask创建启动任务，并通过init执行初始化逻辑，通过onDependencyCompleted感知依赖任务完成。

> **说明：** 
> 
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> 本模块接口仅可在Stage模型下使用。

**起始版本：** 12

**装饰器类型：** @Sendable

**系统能力：** SystemCapability.Ability.AppStartup

## 导入模块

```TypeScript
import { StartupTask } from '@kit.AbilityKit';
```

## init

```TypeScript
init(context: AbilityStageContext): Promise<Object | void>
```

当所有依赖的启动任务都执行完成后，该方法将会被调用。开发者可以在该回调中执行该启动任务的初始化操作。使用Promise异步回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [AbilityStageContext](arkts-ability-abilitystagecontext-c.md) | 是 | [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md)的上下文环境 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Object &#124; void&gt; | Promise对象，用于返回启动任务执行结果对象或void。 |

**示例**

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

当依赖的启动任务执行完成时回调该方法，开发者可在该方法中处理依赖任务的执行结果。

> **说明：** 
> 
> 每当一个依赖任务完成时触发一次。该方法在[init](#init)方法之前被调用，可用于处理单个依赖任务的执行结果。
> init方法则在所有依赖任务都完成后被调用一次。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dependency | string | 是 | 依赖的启动任务名称。 |
| result | Object | 是 | 依赖的启动任务[init](#init)返回的执行结果。 |

**示例**

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
