# removeStartupTaskResult

## 导入模块

```TypeScript
import { startupManager } from '@kit.AbilityKit';
```

<a id="removestartuptaskresult"></a>
## removeStartupTaskResult

```TypeScript
function removeStartupTaskResult(startupTask: string): void
```

删除指定启动任务或so预加载任务的初始化结果。

- 输入为启动任务名时，删除指定启动任务的初始化结果。  
- 输入为so文件时，将该so文件置为未加载，缓存中已加载的so文件不会被移除。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-startupManager-function removeStartupTaskResult(startupTask: string): void--><!--Device-startupManager-function removeStartupTaskResult(startupTask: string): void-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startupTask | string | 是 | 启动任务[StartupTask](arkts-ability-app-appstartup-startuptask-startuptask-c.md)的名称或预加载so名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

**示例：**

```TypeScript
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
        hilog.error(0x0000, 'testTag', `StartupTask_001 promise catch failed, error code: ${error.code}, error msg: ${error.message}`);
      });
    } catch (error) {
      hilog.error(0x0000, 'testTag', `StartupTask_001.run failed, error code: ${error.code}, error msg: ${error.message}`);
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

