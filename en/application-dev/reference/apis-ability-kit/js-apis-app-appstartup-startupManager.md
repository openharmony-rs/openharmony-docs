# @ohos.app.appstartup.startupManager (AppStartup Management)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module provides the capability to manage startup tasks in [AppStartup](../../application-models/app-startup.md). The APIs of this module can be called only on the main thread.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module supports .so file preloading since API version 18.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { startupManager }  from '@kit.AbilityKit';
```

## startupManager.run
run(startupTasks: Array\<string\>, config?: StartupConfig): Promise\<void\>

Runs startup tasks or loads .so files.

> **NOTE**
>
> This API cannot be used to run startup tasks defined in a feature-type HAP. To run those tasks, use [startupManager.run](#startupmanagerrun20).

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| startupTasks | Array\<string\> | Yes| Array of [StartupTask](js-apis-app-appstartup-startupTask.md) names or names of .so files to be preloaded.|
| config | [StartupConfig](./js-apis-app-appstartup-startupConfig.md) | No| Configuration for the timeout duration and listener of startup tasks in AppStartup.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

  | ID| Error Message|
  | ------- | -------------------------------- |
  | 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
  | 16000050 | Internal error. |
  | 28800001 | Startup task or its dependency not found. |
  | 28800002  | The startup tasks have circular dependencies. |
  | 28800003 | An error occurred while running the startup tasks. |
  | 28800004 | Running startup tasks timeout. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, startupManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let startParams = ['StartupTask_001', 'libentry_001'];
    try {
      // Manually call the run method.
      startupManager.run(startParams).then(() => {
        console.info(`StartupTest startupManager run then, startParams = ${startParams}.`);
      }).catch((error: BusinessError) => {
        console.error(`StartupTest promise catch failed, error code: ${error.code}, error msg: ${error.message}.`);
      });
    } catch (error) {
      let errMsg = (error as BusinessError).message;
      let errCode = (error as BusinessError).code;
      console.error(`Startup.run failed, err code: ${errCode}, err msg: ${errMsg}.`);
    }
  }

  // ...
}
```

## startupManager.run<sup>20+</sup>

run(startupTasks: Array\<string\>, context: common.AbilityStageContext, config: StartupConfig): Promise\<void\>

Runs startup tasks or loads .so files. You can specify [AbilityStageContext](js-apis-inner-application-abilityStageContext.md) for loading startup tasks. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name      | Type                                                        | Mandatory| Description                                                        |
| ------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| startupTasks | Array\<string\>                                              | Yes  | Array of [StartupTask](js-apis-app-appstartup-startupTask.md) names or names of .so files to be preloaded.|
| context      | [common.AbilityStageContext](js-apis-inner-application-abilityStageContext.md) | Yes  | AbilityStage context that executes the [StartupTask](js-apis-app-appstartup-startupTask.md). It is passed as an input parameter to [init](js-apis-app-appstartup-startupTask.md#init) of the task.|
| config       | [StartupConfig](./js-apis-app-appstartup-startupConfig.md)   | Yes  | Configuration for the timeout duration and listener of startup tasks in AppStartup.|

**Return value**

| Type           | Description                                  |
| --------------- | -------------------------------------- |
| Promise\<void\> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message                                          |
| -------- | -------------------------------------------------- |
| 16000050 | Internal error.                                    |
| 28800001 | Startup task or its dependency not found.          |
| 28800002 | The startup tasks have circular dependencies.      |
| 28800003 | An error occurred while running the startup tasks. |
| 28800004 | Running startup tasks timeout.                     |

**Example**

```ts
import { AbilityStage, startupManager, StartupListener, StartupConfig } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate(): void {
    hilog.info(0x0000, 'testTag', 'AbilityStage onCreate');
    let onCompletedCallback = (error: BusinessError<void>) => {
      if (error) {
        hilog.error(0x0000, 'testTag', 'onCompletedCallback error: %{public}s', JSON.stringify(error));
      } else {
        hilog.info(0x0000, 'testTag', 'onCompletedCallback: success.');
      }
    };
    let startupListener: StartupListener = {
      'onCompleted': onCompletedCallback
    };
    let config: StartupConfig = {
      'timeoutMs': 10000,
      'startupListener': startupListener
    };

    try {
      // Manually call the run method.
      startupManager.run(['StartupTask_001', 'libentry_001'], this.context, config).then(() => {
        hilog.info(0x0000, 'testTag', '%{public}s', 'startupManager.run success');
      }).catch((error: BusinessError<void>) => {
        hilog.error(0x0000, 'testTag', 'startupManager.run promise catch error: %{public}s', JSON.stringify(error));
      })
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'startupManager.run catch error: %{public}s', JSON.stringify(error));
    }
  }
  // ...
}
```

## startupManager.removeAllStartupTaskResults

removeAllStartupTaskResults(): void

Removes all startup task results.

If there are preloading tasks for .so files, the corresponding .so files is set to the unloaded state. However, .so files that have already been loaded in the cache will not be removed.

**System capability**: SystemCapability.Ability.AppStartup

**Example**

```ts
import { AbilityConstant, UIAbility, Want, startupManager } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    try {
      startupManager.run(['StartupTask_001', 'libentry_001']).then(() => {
        hilog.info(0x0000, 'testTag', 'StartupTask_001 init successful');
      }).catch((error: BusinessError) => {
        hilog.error(0x0000, 'testTag', `StartupTask_001 promise catch failed, error: %{public}s`,
          JSON.stringify(error) ?? '');
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `StartupTask_001.run failed, error: %{public}s`, JSON.stringify(error) ?? '');
    }
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    startupManager.removeAllStartupTaskResults(); // Remove all startup task results.

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```


## startupManager.getStartupTaskResult

getStartupTaskResult(startupTask: string): Object

Obtains the execution result of a startup task or .so file preloading task.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| startupTask | string | Yes| Name of the [StartupTask](js-apis-app-appstartup-startupTask.md) or name of the .so file to be preloaded.|

**Return value**

| Type| Description|
| -------- | -------- |
| Object | Execution result of [init](js-apis-app-appstartup-startupTask.md#init) of the startup task if a startup task name is passed.<br>undefined if a .so file name is passed.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID| Error Message|
  | ------- | -------------------------------- |
  | 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, startupManager } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    try {
      startupManager.run(['StartupTask_001']).then(() => {
        hilog.info(0x0000, 'testTag', 'StartupTask_001 init successful');
      }).catch((error: BusinessError) => {
        hilog.error(0x0000, 'testTag', `StartupTask_001 promise catch failed, error: %{public}s`,
          JSON.stringify(error) ?? '');
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `StartupTask_001.run failed, error: %{public}s`, JSON.stringify(error) ?? '');
    }
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let result = startupManager.getStartupTaskResult('StartupTask_001'); // Manually obtain the startup task result.
    hilog.info(0x0000, 'testTag', 'getStartupTaskResult result = %{public}s', result);
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```


## startupManager.isStartupTaskInitialized

isStartupTaskInitialized(startupTask: string): boolean

Checks whether a startup task or .so file preloading task is initialized.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| startupTask | string | Yes| Name of the [StartupTask](js-apis-app-appstartup-startupTask.md) or name of the .so file to be preloaded.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | boolean | Check result for whether the task is initialized. **true** if initialized, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID| Error Message|
  | ------- | -------------------------------- |
  | 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, startupManager } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    try {
      startupManager.run(['StartupTask_001', 'libentry_001']).then(() => {
      hilog.info(0x0000, 'testTag', 'StartupTask_001 init successful');
      }).catch((error: BusinessError) => {
        hilog.error(0x0000, 'testTag', `StartupTask_001 promise catch failed, error: %{public}s`,
          JSON.stringify(error) ?? '');
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `StartupTask_001.run failed, error: %{public}s`, JSON.stringify(error) ?? '');
    }
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let result1 = startupManager.isStartupTaskInitialized('StartupTask_001');
    let result2 = startupManager.isStartupTaskInitialized('libentry_001');
    if (result1) {
      console.info('StartupTask_001 init successful');
    } else {
      console.info('StartupTask_001 uninitialized');
    }
    if (result2) {
      console.info('libentry_001 init successful');
    } else {
      console.info('libentry_001 uninitialized');
    }

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```

## startupManager.removeStartupTaskResult

removeStartupTaskResult(startupTask: string): void

Removes the initialization result of a startup task or .so file preloading task.

- If a startup task name is passed, the initialization result of that startup task is removed.

- If a .so file is passed, the .so file is set to the unloaded state, but the loaded .so file in the cache is not removed.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| startupTask | string | Yes| Name of the [StartupTask](js-apis-app-appstartup-startupTask.md) or name of the .so file to be preloaded.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

  | ID| Error Message|
  | ------- | -------------------------------- |
  | 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, startupManager } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    try{
      startupManager.run(['StartupTask_001', 'libentry_001']).then(() => {
        hilog.info(0x0000, 'testTag', 'StartupTask_001 init successful');
      }).catch((error: BusinessError) => {
        hilog.error(0x0000, 'testTag', `StartupTask_001 promise catch failed, error: %{public}s`,
          JSON.stringify(error) ?? '');
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `StartupTask_001.run failed, error: %{public}s`, JSON.stringify(error) ?? '');
    }
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    startupManager.removeStartupTaskResult('StartupTask_001');
    startupManager.removeStartupTaskResult('libentry_001');

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```
