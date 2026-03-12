# @ohos.app.appstartup.StartupTask (启动框架任务)

本模块提供启动任务的相关能力。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```js
import { StartupTask } from '@kit.AbilityKit';
```

## StartupTask

### onDependencyCompleted

onDependencyCompleted?(dependency: string, result: Object): void

当依赖的启动任务执行完成时该方法将会被调用。

**系统能力**：SystemCapability.Ability.AppStartup

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| dependency | string | 是 | 依赖的启动任务名称。 |
| result | Object | 是 | 依赖启动任务执行的结果。 |

**示例：**

```ts
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

  onDependencyCompleted(dependence: string, result: Object): void {
    hilog.info(0x0000, 'testTag', 'StartupTask_001 onDependencyCompleted, dependence: %{public}s, result: %{public}s',
      dependence, JSON.stringify(result));
    // ...
  }
}
```

### onDependencyCompleted<sup>23+</sup>

onDependencyCompleted(dependency: string, result: Any): void

当依赖的启动任务执行完成时该方法将会被调用。

**系统能力**：SystemCapability.Ability.AppStartup

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型   | 必填 | 说明                     |
| ---------- | ------ | ---- | ------------------------ |
| dependency | string | 是   | 依赖的启动任务名称。     |
| result     | Any    | 是   | 依赖启动任务执行的结果。 |

**示例：**

```ts
// ArkTS-Sta示例
import { StartupTask, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class StartupTask_001 extends StartupTask {
  constructor() {
    super();
  }

  async init(context: common.AbilityStageContext) {
    // ...
  }

  onDependencyCompleted(dependence: string, result: Any): void {
    hilog.info(0x0000, 'testTag', 'StartupTask_001 onDependencyCompleted, dependence: %{public}s, result: %{public}s',
      dependence, JSON.stringify(result));
    // ...
  }
}
```

### init

init(context: AbilityStageContext): Promise\<Object \| void\>

启动任务执行的初始化业务。

**系统能力**：SystemCapability.Ability.AppStartup

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| context | [AbilityStageContext](js-apis-inner-application-abilityStageContext.md) | 是 | AbilityStage的上下文环境 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<Object \| void\> | Promise对象，返回启动任务执行结果对象。 |

**示例：**

```ts
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

  onDependencyCompleted(dependence: string, result: Object): void {
    // ...
  }
}
```

### init<sup>23+</sup>

init(context: AbilityStageContext): Promise\<Any> | Promise\<void>

启动任务执行的初始化业务。

**系统能力**：SystemCapability.Ability.AppStartup

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明                     |
| ------- | ------------------------------------------------------------ | ---- | ------------------------ |
| context | [AbilityStageContext](js-apis-inner-application-abilityStageContext.md) | 是   | AbilityStage的上下文环境 |

**返回值：**

| 类型                            | 说明                                    |
| ------------------------------- | --------------------------------------- |
| Promise\<Any> \| Promise\<void> | Promise对象，返回启动任务执行结果对象。 |

**示例：**

```ts
// ArkTS-Sta示例
import { StartupTask, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class StartupTask_001 extends StartupTask {
  constructor() {
    super();
  }
  async init(context: common.AbilityStageContext) {
    hilog.info(0x0000, 'testTag', 'StartupTask_001 init.');
    // ...

    return "StartupTask_001";
  }

  onDependencyCompleted(dependence: string, result: Any): void {
    // ...
  }
}
```
