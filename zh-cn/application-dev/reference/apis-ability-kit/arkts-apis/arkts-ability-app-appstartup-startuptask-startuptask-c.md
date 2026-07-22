# StartupTask

The module provides capabilities related to startup tasks in [AppStartup](../../../application-models/app-startup.md).

**起始版本：** 12

**装饰器类型：** @Sendable

<!--Device-unnamed-declare class StartupTask--><!--Device-unnamed-declare class StartupTask-End-->

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

<!--Device-StartupTask-init(context: AbilityStageContext): Promise<Object | void>--><!--Device-StartupTask-init(context: AbilityStageContext): Promise<Object | void>-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [AbilityStageContext](arkts-ability-common-abilitystagecontext-t.md) | 是 | [AbilityStage](arkts-ability-app-ability-abilitystage-abilitystage-c.md)的上下文环境 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Object \| void&gt; | Promise used to return the execution result. |

**示例：**

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

    return "StartupTask_001";
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

当依赖的启动任务执行完成时该方法将会被调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupTask-onDependencyCompleted?(dependency: string, result: Object): void--><!--Device-StartupTask-onDependencyCompleted?(dependency: string, result: Object): void-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dependency | string | 是 | 依赖的启动任务名称。 |
| result | Object | 是 | 依赖的启动任务[init](arkts-ability-app-appstartup-startuptask-startuptask-c.md#init)返回的执行结果。 |

**示例：**

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

