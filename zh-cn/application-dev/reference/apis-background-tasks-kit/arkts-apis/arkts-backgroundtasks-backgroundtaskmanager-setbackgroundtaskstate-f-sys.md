# setBackgroundTaskState（系统接口）

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## setBackgroundTaskState

```TypeScript
function setBackgroundTaskState(stateInfo: BackgroundTaskStateInfo): void
```

设置长时任务授权信息。

**起始版本：** 22

**需要权限：** ohos.permission.SET_BACKGROUND_TASK_STATE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-backgroundTaskManager-function setBackgroundTaskState(stateInfo: BackgroundTaskStateInfo): void--><!--Device-backgroundTaskManager-function setBackgroundTaskState(stateInfo: BackgroundTaskStateInfo): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stateInfo | [BackgroundTaskStateInfo](arkts-backgroundtasks-backgroundtaskmanager-backgroundtaskstateinfo-i-sys.md) | 是 | 授权的必要信息，包括用户ID、应用包名、应用分身ID等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    // 请开发者根据实际情况更新参数
    let backgroundTaskStateInfo: backgroundTaskManager.BackgroundTaskStateInfo = {
        userId: 100,
        bundleName: 'com.example.continuoustask',
        appIndex: 0,
        authResult: backgroundTaskManager.UserAuthResult.DENIED
    };
    backgroundTaskManager.setBackgroundTaskState(backgroundTaskStateInfo);
    console.info('Operation setBackgroundTaskState succeeded.');
} catch (error) {
    console.error(`Operation setBackgroundTaskState failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}

```

