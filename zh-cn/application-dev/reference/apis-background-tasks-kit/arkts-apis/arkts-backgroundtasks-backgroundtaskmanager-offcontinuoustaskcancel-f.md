# offContinuousTaskCancel

## offContinuousTaskCancel

```TypeScript
function offContinuousTaskCancel(callback?: Callback<ContinuousTaskCancelInfo>): void
```

解除长时任务取消的监听，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

<!--Device-backgroundTaskManager-function offContinuousTaskCancel(callback?: Callback<ContinuousTaskCancelInfo>): void--><!--Device-backgroundTaskManager-function offContinuousTaskCancel(callback?: Callback<ContinuousTaskCancelInfo>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ContinuousTaskCancelInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskcancelinfo-i.md)&gt; | 否 | the callback of continuous task cancel. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Callback parameter error; 2. Unregister type has not register; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

function callback(info: backgroundTaskManager.ContinuousTaskCancelInfo) {
  console.info('continuousTaskCancel callback id ' + info.id);
  console.info('continuousTaskCancel callback reason ' + info.reason);
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      backgroundTaskManager.offContinuousTaskCancel(callback);
    } catch (error) {
      console.error(`Operation offContinuousTaskCancel failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```

