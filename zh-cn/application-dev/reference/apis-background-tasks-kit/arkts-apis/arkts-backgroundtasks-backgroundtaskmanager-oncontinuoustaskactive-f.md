# onContinuousTaskActive

## onContinuousTaskActive

```TypeScript
function onContinuousTaskActive(callback: Callback<ContinuousTaskActiveInfo>): void
```

注册长时任务激活的监听，使用callback异步回调。应用回前台激活暂停的长时任务。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

<!--Device-backgroundTaskManager-function onContinuousTaskActive(callback: Callback<ContinuousTaskActiveInfo>): void--><!--Device-backgroundTaskManager-function onContinuousTaskActive(callback: Callback<ContinuousTaskActiveInfo>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ContinuousTaskActiveInfo](arkts-backgroundtasks-backgroundtaskmanager-continuoustaskactiveinfo-i.md)&gt; | 是 | the callback of continuous task active. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

function callback(info: backgroundTaskManager.ContinuousTaskActiveInfo) {
  console.info('continuousTaskActive callback id: ' + info.id);
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      backgroundTaskManager.onContinuousTaskActive(callback);
    } catch (error) {
      console.error(`Operation onContinuousTaskActive failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```

