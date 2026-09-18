# run

## Modules to Import

```TypeScript
import { startupManager } from '@kit.AbilityKit';
```

## run

```TypeScript
function run(startupTasks: Array<string>, config?: StartupConfig): Promise<void>
```

Runs startup tasks or loads .so files.

> **NOTE:** 
> 
> This API cannot be used to run startup tasks defined in a feature-type HAP. To run those tasks, use
> [startupManager.run](#run-1)
> .

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppStartup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startupTasks | Array&lt;string&gt; | Yes | Array of [StartupTask](arkts-ability-app-appstartup-startuptask-startuptask-c.md) names or names of .so files to be preloaded. |
| config | [StartupConfig](arkts-ability-app-appstartup-startupconfig-startupconfig-i.md) | No | Configuration for the timeout duration and listener of startup tasks in AppStartup. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [28800001](../errorcode-ability.md#28800001-startup-task-or-dependency-not-found) | Startup task or its dependency not found. |
| [28800002](../errorcode-ability.md#28800002-circular-dependencies-between-startup-tasks) | The startup tasks have circular dependencies. |
| [28800003](../errorcode-ability.md#28800003-error-occurs-during-task-startup) | An error occurred while running the startup tasks. |
| [28800004](../errorcode-ability.md#28800004-executing-the-startup-task-times-out) | Running startup tasks timeout. |

**Examples**

```TypeScript
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

```TypeScript
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


## run

```TypeScript
function run(startupTasks: Array<string>, context: common.AbilityStageContext, config: StartupConfig): Promise<void>
```

Runs startup tasks or loads .so files. You can specify [AbilityStageContext](arkts-ability-abilitystagecontext-c.md) for loading startup tasks. This API uses a promise to return the result.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppStartup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| startupTasks | Array&lt;string&gt; | Yes | Array of [StartupTask](arkts-ability-app-appstartup-startuptask-startuptask-c.md) names or names of .so files to be preloaded. |
| context | [common.AbilityStageContext](arkts-ability-common-abilitystagecontext-t.md) | Yes | AbilityStage context that executes the [StartupTask](arkts-ability-app-appstartup-startuptask-startuptask-c.md). It is passed as an input parameter to [init](arkts-ability-app-appstartup-startuptask-startuptask-c.md#init) of the task. |
| config | [StartupConfig](arkts-ability-app-appstartup-startupconfig-startupconfig-i.md) | Yes | Configuration for the timeout duration and listener of startup tasks in AppStartup. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [28800001](../errorcode-ability.md#28800001-startup-task-or-dependency-not-found) | Startup task or its dependency not found. |
| [28800002](../errorcode-ability.md#28800002-circular-dependencies-between-startup-tasks) | The startup tasks have circular dependencies. |
| [28800003](../errorcode-ability.md#28800003-error-occurs-during-task-startup) | An error occurred while running the startup tasks. |
| [28800004](../errorcode-ability.md#28800004-executing-the-startup-task-times-out) | Running startup tasks timeout. |

**Examples**

See [run](#run)
