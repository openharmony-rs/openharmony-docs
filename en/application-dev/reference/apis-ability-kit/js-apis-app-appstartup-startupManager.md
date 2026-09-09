# @ohos.app.appstartup.startupManager (AppStartup Management)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b49af0976afe6155e5bfe3169381b3e1f0a172f0 translatedAt=2026-09-03T10:48:25.214Z pushedAt=2026-09-07T08:50:32.473Z -->

This module provides the capability to manage startup tasks in the [application startup framework](../../application-models/app-startup.md), supporting task dependency scheduling, parallel execution, .so preloading, and task result management. It can be called only on the main thread.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module supports .so preloading since API version 18, which allows .so files to be loaded in advance during the application startup phase. When startup task results are cleared, the loaded .so files in the cache are not removed.
>
> The APIs of this module can be used only in the Stage model.

## Modules to Import

```ts
import { startupManager }  from '@kit.AbilityKit';
```

## startupManager.run
run(startupTasks: Array\<string\>, config?: StartupConfig): Promise\<void\>

Runs startup framework startup tasks or loads .so files. During the application startup phase, it can be used to trigger the execution of startup tasks or preload .so files.

> **NOTE**
>
> This API cannot be used to run startup tasks defined in a feature-type HAP (Harmony Ability Package). To use the related capability, call [startupManager.run](#startupmanagerrun20).
>
> This API supports only [application-level .so](../../application-models/ability-terminology.md#application-level-so) file loading, and does not support [system-level .so](../../application-models/ability-terminology.md#system-level-so) file loading.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| startupTasks | Array\<string\> | Yes | Array of the names of the startup tasks [StartupTask](js-apis-app-appstartup-startupTask.md) to be executed or the names of the preloaded so files. This API does not support startup tasks in feature-type HAPs. The names must be consistent with the name values configured in the startup_config.json configuration file. For details, see [Define Startup Task Configuration](../../application-models/app-startup.md#defining-startup-task-configuration) and [Define Preload so Task Configuration](../../application-models/app-startup.md#defining-so-file-preloading-task-configuration). |
| config | [StartupConfig](js-apis-app-appstartup-startupConfig.md) | No | Startup task configuration information, used to customize the behavior of the startup framework. Pass this parameter when a custom timeout period needs to be set or the startup task completion status needs to be listened for. If this parameter is not passed, the default configuration is used (the default timeout period is 10000 ms, and no startup task listener is set). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void\> | Promise object with no return result. |

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
        hilog.info(0x0000, 'testTag', 'StartupTest startupManager run then, startParams = %{public}s.', startParams.join(','));
      }).catch((error: BusinessError) => {
        hilog.error(0x0000, 'testTag', 'StartupTest promise catch failed, error code: %{public}d, error msg: %{public}s.', error.code, error.message);
      });
    } catch (error) {
      let errMsg = (error as BusinessError).message;
      let errCode = (error as BusinessError).code;
      hilog.error(0x0000, 'testTag', 'startupManager.run failed, err code: %{public}d, err msg: %{public}s.', errCode, errMsg);
    }
  }

  // ...
}
```

## startupManager.run<sup>20+</sup>

run(startupTasks: Array\<string\>, context: common.AbilityStageContext, config: StartupConfig): Promise\<void\>

Runs startup framework startup tasks or loads .so files. You can specify [AbilityStageContext](js-apis-inner-application-abilityStageContext.md) for loading startup tasks, and this context is used as the input parameter of the init method of the startup task. This API supports startup tasks in a feature-type HAP. This API uses a promise to return the result.

> **NOTE**
>
> This API supports only [application-level .so](../../application-models/ability-terminology.md#application-level-so) file loading, and does not support [system-level .so](../../application-models/ability-terminology.md#system-level-so) file loading.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name      | Type                                                        | Mandatory| Description                                                        |
| ------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| startupTasks | Array\<string\>                                              | Yes   | Array of the names of the startup tasks [StartupTask](js-apis-app-appstartup-startupTask.md) to be executed or the names of the preloaded so files. The names must be consistent with the **name** values configured in the startup_config.json configuration file. For details, see [Define Startup Task Configuration](../../application-models/app-startup.md#defining-startup-task-configuration) and [Define Preload so Task Configuration](../../application-models/app-startup.md#defining-so-file-preloading-task-configuration). |
| context      | [common.AbilityStageContext](js-apis-inner-application-abilityStageContext.md) | Yes  | AbilityStage context that executes the [StartupTask](js-apis-app-appstartup-startupTask.md). It is passed as an input parameter to [init](js-apis-app-appstartup-startupTask.md#init) of the task.|
| config       | [StartupConfig](js-apis-app-appstartup-startupConfig.md)   | Yes   | Startup task configuration information, including the startup framework timeout period and the startup task listener configuration. |

**Return value**

| Type           | Description                                  |
| --------------- | -------------------------------------- |
| Promise\<void\> | Promise object that returns no value. If the execution fails, the error cause can be obtained through the exception information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

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
    let onCompletedCallback = (error: BusinessError) => {
      if (error) {
        hilog.error(0x0000, 'testTag', `onCompletedCallback error code: ${error.code}, error msg: ${error.message}`);
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
      }).catch((error: BusinessError) => {
        hilog.error(0x0000, 'testTag', `startupManager.run promise catch error code: ${error.code}, error msg: ${error.message}`);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `startupManager.run catch error code: ${error.code}, error msg: ${error.message}`);
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
        hilog.error(0x0000, 'testTag', `StartupTask_001 promise catch failed, error code: ${error.code}, error msg: ${error.message}`);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `startupManager.run failed, error code: ${error.code}, error msg: ${error.message}`);
    }
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    startupManager.removeAllStartupTaskResults(); // Remove all startup task results.

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause error code: ${err.code}, error msg: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```


## startupManager.getStartupTaskResult

getStartupTaskResult(startupTask: string): Object

Obtains the execution result of a specified startup task or .so preloading task. After run() is called to execute the corresponding startup task, its execution result can be obtained through this API.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| startupTask | string | Yes | Name of the startup task [StartupTask](js-apis-app-appstartup-startupTask.md) or name of the preload so. The name must be consistent with the value of **name** configured in the configuration file startup_config.json. For details, see [Define Startup Task Configuration](../../application-models/app-startup.md#defining-startup-task-configuration) and [Define Preload so Task Configuration](../../application-models/app-startup.md#defining-so-file-preloading-task-configuration). |

**Return value**

| Type| Description|
| -------- | -------- |
| Object | When the input is a startup task name, returns the execution result of the [init](js-apis-app-appstartup-startupTask.md#init) method in the specified startup task.<br/>When the input is an so file name, undefined is returned. |

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
        hilog.error(0x0000, 'testTag', `StartupTask_001 promise catch failed, error code: ${error.code}, error msg: ${error.message}`);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `startupManager.run failed, error code: ${error.code}, error msg: ${error.message}`);
    }
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let result = startupManager.getStartupTaskResult('StartupTask_001'); // Manually obtain the startup task result.
    hilog.info(0x0000, 'testTag', 'getStartupTaskResult result = %{public}s', JSON.stringify(result));
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause error code: ${err.code}, error msg: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```


## startupManager.isStartupTaskInitialized

isStartupTaskInitialized(startupTask: string): boolean

Obtains whether a specified startup task or .so preloading task is initialized. After run() is called to execute the corresponding startup task, its initialization status can be queried through this API.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| startupTask | string | Yes | Name of the startup task [StartupTask](js-apis-app-appstartup-startupTask.md) or the preloaded so name. The name must be consistent with the value of **name** configured in the configuration file startup_config.json. For details, see [Define Startup Task Configuration](../../application-models/app-startup.md#defining-startup-task-configuration) and [Define Preload so Task Configuration](../../application-models/app-startup.md#defining-so-file-preloading-task-configuration). |

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns a boolean value. The value **true** indicates that the startup task or so preload task has been initialized, and **false** indicates that it has not been initialized. |

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
        hilog.error(0x0000, 'testTag', `StartupTask_001 promise catch failed, error code: ${error.code}, error msg: ${error.message}`);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `startupManager.run failed, error code: ${error.code}, error msg: ${error.message}`);
    }
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    let result1 = startupManager.isStartupTaskInitialized('StartupTask_001');
    let result2 = startupManager.isStartupTaskInitialized('libentry_001');
    if (result1) {
      hilog.info(0x0000, 'testTag', 'StartupTask_001 init successful');
    } else {
      hilog.info(0x0000, 'testTag', 'StartupTask_001 uninitialized');
    }
    if (result2) {
      hilog.info(0x0000, 'testTag', 'libentry_001 init successful');
    } else {
      hilog.info(0x0000, 'testTag', 'libentry_001 uninitialized');
    }
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause error code: ${err.code}, error msg: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```

## startupManager.removeStartupTaskResult

removeStartupTaskResult(startupTask: string): void

Removes the result of a specified startup task or .so preloading task.

- If a startup task name is passed, the result of that startup task is removed.

- If a .so file name is passed, the .so file is set to the unloaded state, but the loaded .so file in the cache is not removed.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| startupTask | string | Yes | Name of the startup task [StartupTask](js-apis-app-appstartup-startupTask.md) or the preloaded so name. The name must be consistent with the value of **name** configured in the configuration file startup_config.json. For details, see [Define Startup Task Configuration](../../application-models/app-startup.md#defining-startup-task-configuration) and [Define Preload so Task Configuration](../../application-models/app-startup.md#defining-so-file-preloading-task-configuration). |

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
        hilog.error(0x0000, 'testTag', `StartupTask_001 promise catch failed, error code: ${error.code}, error msg: ${error.message}`);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `startupManager.run failed, error code: ${error.code}, error msg: ${error.message}`);
    }
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    startupManager.removeStartupTaskResult('StartupTask_001');
    startupManager.removeStartupTaskResult('libentry_001');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause error code: ${err.code}, error msg: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}
```
<!--no_check-->