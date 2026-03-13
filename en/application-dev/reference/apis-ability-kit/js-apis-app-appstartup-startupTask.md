# @ohos.app.appstartup.StartupTask (AppStartup Task)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module provides capabilities related to startup tasks in [AppStartup](../../application-models/app-startup.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```js
import { StartupTask } from '@kit.AbilityKit';
```

## StartupTask

Provides capabilities related to startup tasks. It is decorated by [@Sendable](../../arkts-utils/arkts-sendable.md#sendable-decorator).

**Decorator**: \@Sendable

### onDependencyCompleted

onDependencyCompleted?(dependency: string, result: Object): void

Called when the dependent startup task is complete.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| dependency | string | Yes| Name of the dependent startup task.|
| result | Object | Yes| Execution result of [init](#init) of the dependent startup task.|

**Example**

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

  onDependencyCompleted(dependency: string, result: Object): void {
    hilog.info(0x0000, 'testTag', 'StartupTask_001 onDependencyCompleted, dependency: %{public}s, result: %{public}s',
      dependency, JSON.stringify(result));
    // ...
  }
}
```


### init

init(context: AbilityStageContext): Promise\<Object \| void\>

Called when all the dependent startup tasks are complete. You can initialize the startup task in this callback. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [AbilityStageContext](js-apis-inner-application-abilityStageContext.md) | Yes| Context environment of the [AbilityStage](js-apis-app-ability-abilityStage.md).|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Object \| void\> | Promise used to return the execution result.|

**Example**

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

  onDependencyCompleted(dependency: string, result: Object): void {
    // ...
  }
}
```
