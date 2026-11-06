# WorkSchedulerExtensionContext (Work Scheduler Callback Context) (System API)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1f52f7aac7b6f238f6e71771e1abacfe15a739f1 translatedAt=2026-11-03T03:37:21.347Z pushedAt=2026-11-03T07:38:33.561Z nl=1 -->

The **WorkSchedulerExtensionContext** module, inherited from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md), provides a context environment for the **WorkSchedulerExtensionAbility**. This module provides the context for deferred task scheduling and allows you to start or stop the **ServiceExtensionAbility** when a task is started or stopped.

WorkSchedulerExtensionContext can directly serve as the context for WorkSchedulerExtension and provides the capability to access resources specific to **WorkSchedulerExtensionAbility**.

> **NOTE**
> 
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs provided by this module are system APIs.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [WorkSchedulerExtensionContext (Work Scheduler Callback Context) (System API)](js-apis-WorkSchedulerExtensionContext.md).

## Modules to Import

```ts
import { WorkSchedulerExtensionAbility } from '@kit.BackgroundTasksKit';  
```

## How to Use

Obtain the context through a **WorkSchedulerExtensionAbility** child class instance.

```ts
import { WorkSchedulerExtensionAbility, workScheduler } from '@kit.BackgroundTasksKit';

class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStart(workInfo: workScheduler.WorkInfo) {
    let workSchedulerExtensionContext = this.context; // Obtain the WorkSchedulerExtensionContext
  }
}
```

## WorkSchedulerExtensionContext.startServiceExtensionAbility<sup>13+</sup>

startServiceExtensionAbility(want: Want): Promise\<void>

Starts the **ServiceExtensionAbility**. This API is used to start the associated service ability when a task is running in the background. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| Information about the **Want** used for starting an ability. This parameter must contain necessary fields such as **bundleName** and **abilityName**.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| Error Code ID| Error Message|
| ------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | [Async] Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000008 | The crowdtesting application expires. |
| 16000011 | The context does not exist.        |
| 16000012 | The application is controlled.        |
| 16000013 | The application is controlled by EDM.       |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { WorkSchedulerExtensionAbility, workScheduler } from '@kit.BackgroundTasksKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want : Want = {
  bundleName: 'com.example.workscheduler',
  abilityName: 'ServiceExtAbility'
}

export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStart(workInfo: workScheduler.WorkInfo) {
    console.info(`onWorkStart, workInfo = ${JSON.stringify(workInfo)}`);
      // Start the corresponding Service.
      this.context.startServiceExtensionAbility(want).then(() => {
        console.info('succeeded in starting ServiceExtensionAbility.');
      }).catch((err: BusinessError) => {
        console.error(`failed to start ServiceExtensionAbility. Code: ${err.code}, message: ${err.message}`);
      });
  }

  onWorkStop(workInfo: workScheduler.WorkInfo) {
    console.info(`onWorkStop, workInfo is ${JSON.stringify(workInfo)}`);
  }
}
```

## WorkSchedulerExtensionContext.stopServiceExtensionAbility<sup>13+</sup>

stopServiceExtensionAbility(want: Want): Promise\<void>

Stops the ServiceExtensionAbility. This API is used when the task running in the background is complete or the associated service capability is no longer needed. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Required | Information about the **Want** used for stopping an ability. This parameter must contain necessary fields such as **bundleName** and **abilityName**. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](../apis-ability-kit/errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | [Async] Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000006 | Cross-user operations are not allowed. |
| 16000011 | The context does not exist.        |
| 16000050 | Internal error. |
| 16200001 | The caller has been released. |

**Example**

```ts
import { WorkSchedulerExtensionAbility, workScheduler } from '@kit.BackgroundTasksKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want : Want = {
  bundleName: 'com.example.workscheduler',
  abilityName: 'ServiceExtAbility'
}

export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
  onWorkStart(workInfo: workScheduler.WorkInfo) {
    console.info(`onWorkStart, workInfo = ${JSON.stringify(workInfo)}`);
  }

  onWorkStop(workInfo: workScheduler.WorkInfo) {
    console.info(`onWorkStop, workInfo is ${JSON.stringify(workInfo)}`);
      // Stop the corresponding service.
      this.context.stopServiceExtensionAbility(want).then(() => {
        console.info('succeeded in stopping ServiceExtensionAbility.');
      }).catch ((err: BusinessError) => {
        console.error(`failed to stop ServiceExtensionAbility. Code: ${err.code}, message: ${err.message}`);
      });
  }
}
```