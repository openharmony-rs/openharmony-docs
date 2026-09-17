# startBackgroundRunning

## Modules to Import

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

## startBackgroundRunning

```TypeScript
function startBackgroundRunning(id: number, request: NotificationRequest, callback: AsyncCallback<void>): void
```

Requests a continuous task from the system. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [startBackgroundRunning](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md)

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Notification ID of the continuous task. |
| request | [NotificationRequest](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md) | Yes | Notification parameter, which is used to display information in the notification bar. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the continuous task is requested, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

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


## startBackgroundRunning

```TypeScript
function startBackgroundRunning(id: number, request: NotificationRequest): Promise<void>
```

Requests a continuous task from the system. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [startBackgroundRunning](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager-startbackgroundrunning-f.md)

**Required permissions:** ohos.permission.KEEP_BACKGROUND_RUNNING

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Notification ID of the continuous task. |
| request | [NotificationRequest](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-notificationrequest-i.md) | Yes | Notification parameter, which is used to display information in the notification bar. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. Promise that returns no value. |

**Examples**

See [startBackgroundRunning](#startbackgroundrunning)
