# run

## run

```TypeScript
function run(startupTasks: Array<string>, config?: StartupConfig): Promise<void>
```

执行启动框架启动任务或加载so文件。 > **说明：** > > 本接口不支持执行feature类型HAP中的启动任务，如需要使用相关能力请调用 > [startupManager.run](#run) > 接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-startupManager-function run(startupTasks: Array<string>, config?: StartupConfig): Promise<void>--><!--Device-startupManager-function run(startupTasks: Array<string>, config?: StartupConfig): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startupTasks | Array&lt;string&gt; | 是 | 表示准备执行的启动任务 [StartupTask](arkts-ability-app-appstartup-startuptask-startuptask-c.md#StartupTask)的名称或预加载so名称的数组。 |
| config | [StartupConfig](arkts-ability-app-appstartup-startupconfig-startupconfig-i.md) | 否 | 表示启动任务配置信息，包含启动框架超时时间与启动任务监听器配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [28800004](../errorcode-ability.md#28800004-执行启动任务超时) | Running startup tasks timeout. |
| [28800003](../errorcode-ability.md#28800003-运行启动任务时发生错误) | An error occurred while running the startup tasks. |
| [28800002](../errorcode-ability.md#28800002-启动任务之间存在循环依赖关系) | The startup tasks have circular dependencies. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [28800001](../errorcode-ability.md#28800001-启动任务或其依赖项不存在) | Startup task or its dependency not found. |

## 示例

```TypeScript
import { AbilityConstant, UIAbility, Want, startupManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let startParams = ['StartupTask_001', 'libentry_001'];
    try {
      // 手动调用run方法
      startupManager.run(startParams).then(() => {
        console.info(`StartupTest startupManager run then, startParams = ${startParams}.`);
      }).catch((err: Error) => {
        let error = err as BusinessError;
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


## run

```TypeScript
function run(startupTasks: Array<string>, context: common.AbilityStageContext, config: StartupConfig): Promise<void>
```

执行启动框架启动任务或加载so文件。支持指定[AbilityStageContext](arkts-ability-abilitystagecontext-c.md#AbilityStageContext)用于启动任务的加载。使 用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-startupManager-function run(startupTasks: Array<string>, context: common.AbilityStageContext, config: StartupConfig): Promise<void>--><!--Device-startupManager-function run(startupTasks: Array<string>, context: common.AbilityStageContext, config: StartupConfig): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startupTasks | Array&lt;string&gt; | 是 | 表示准备执行的启动任务 [StartupTask](arkts-ability-app-appstartup-startuptask-startuptask-c.md#StartupTask)的名称或预加载so名称的数组。 |
| context | common.AbilityStageContext | 是 | 表示执行启动任务 [StartupTask](arkts-ability-app-appstartup-startuptask-startuptask-c.md#StartupTask)的AbilityStage上下文，作为入参传给启动任务的 [init](arkts-ability-app-appstartup-startuptask-startuptask-c.md#init)。 |
| config | [StartupConfig](arkts-ability-app-appstartup-startupconfig-startupconfig-i.md) | 是 | 表示启动任务配置信息，包含启动框架超时时间与启动任务监听器配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [28800004](../errorcode-ability.md#28800004-执行启动任务超时) | Running startup tasks timeout. |
| [28800003](../errorcode-ability.md#28800003-运行启动任务时发生错误) | An error occurred while running the startup tasks. |
| [28800002](../errorcode-ability.md#28800002-启动任务之间存在循环依赖关系) | The startup tasks have circular dependencies. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [28800001](../errorcode-ability.md#28800001-启动任务或其依赖项不存在) | Startup task or its dependency not found. |

## 示例

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
      // 手动调用run方法
      startupManager.run(['StartupTask_001', 'libentry_001'], this.context, config).then(() => {
        hilog.info(0x0000, 'testTag', '%{public}s', 'startupManager.run success');
      }).catch((err: Error) => {
        let error = err as BusinessError;
        hilog.error(0x0000, 'testTag', `startupManager.run promise catch error code: ${error.code}, error msg: ${error.message}`);
      })
    } catch (error) {
      hilog.error(0x0000, 'testTag', `startupManager.run catch error code: ${error.code}, error msg: ${error.message}`);
    }
  }
  // ...
}
```

