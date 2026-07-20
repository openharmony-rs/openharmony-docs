# isStartupTaskInitialized

## 导入模块

```TypeScript
import { startupManager } from '@kit.AbilityKit';
```

<a id="isstartuptaskinitialized"></a>
## isStartupTaskInitialized

```TypeScript
function isStartupTaskInitialized(startupTask: string): boolean
```

获取指定启动任务或so预加载任务是否已初始化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-startupManager-function isStartupTaskInitialized(startupTask: string): boolean--><!--Device-startupManager-function isStartupTaskInitialized(startupTask: string): boolean-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startupTask | string | 是 | 启动任务[StartupTask](arkts-ability-app-appstartup-startuptask-startuptask-c.md)的名称或预加载so名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回布尔值，true表示该启动任务或so预加载任务已执行完成，false表示该启动任务或so预加载任务尚未执行完成。 |

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
    try {
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
        hilog.error(0x0000, 'testTag', `Failed to load the content. Cause error code: ${err.code}, error msg: ${err.message}`);
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
}

```

