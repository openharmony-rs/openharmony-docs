# startBackgroundRunning

## 导入模块

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

## startBackgroundRunning

```TypeScript
function startBackgroundRunning(id: number, request: NotificationRequest, callback: AsyncCallback<void>): void
```

向系统申请长时任务。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [startBackgroundRunning](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-particleAbility-function startBackgroundRunning(id: number, request: NotificationRequest, callback: AsyncCallback<void>): void--><!--Device-particleAbility-function startBackgroundRunning(id: number, request: NotificationRequest, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 长时任务通知id号。 |
| request | [NotificationRequest](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-notificationrequest-t.md) | 是 | 通知参数，用于显示通知栏的信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当向系统申请长时任务成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { particleAbility, wantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import notification from '@ohos.notification';

function callback(error: BusinessError, data: void) {
  if (error && error.code !== 0) {
    console.error(`Operation failed error: ${JSON.stringify(error)}`);
  } else {
    console.info(`Operation succeeded, data: ${data}`);
  }
}

let wantAgentInfo: wantAgent.WantAgentInfo = {
  wants: [
    {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    }
  ],
  operationType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0,
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj) => {
  let id = 1;
  particleAbility.startBackgroundRunning(id, {
    content:
    {
      contentType: notification.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
      normal:
      {
        title: 'title',
        text: 'text'
      }
    },
    wantAgent: wantAgentObj
  }, callback);
});

```


## startBackgroundRunning

```TypeScript
function startBackgroundRunning(id: number, request: NotificationRequest): Promise<void>
```

向系统申请长时任务。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [startBackgroundRunning](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md#startbackgroundrunning-1)

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-particleAbility-function startBackgroundRunning(id: number, request: NotificationRequest): Promise<void>--><!--Device-particleAbility-function startBackgroundRunning(id: number, request: NotificationRequest): Promise<void>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 长时任务通知id号。 |
| request | [NotificationRequest](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-notificationrequest-t.md) | 是 | 通知参数，用于显示通知栏的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { particleAbility, wantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import notification from '@ohos.notification';

let wantAgentInfo: wantAgent.WantAgentInfo = {
  wants: [
    {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    }
  ],
  operationType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0,
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj) => {
  let id = 1;
  particleAbility.startBackgroundRunning(id, {
    content:
    {
      contentType: notification.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
      normal:
      {
        title: 'title',
        text: 'text'
      }
    },
    wantAgent: wantAgentObj
  }).then(() => {
    console.info('Operation succeeded');
  }).catch((err: BusinessError) => {
    console.error(`Operation failed cause: ${JSON.stringify(err)}`);
  });
});

```

