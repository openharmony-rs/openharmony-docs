# off

## off('continuousTaskCancel')

```TypeScript
function off(type: 'continuousTaskCancel', callback?: Callback<ContinuousTaskCancelInfo>): void
```

解除长时任务取消的监听，使用callback异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continuousTaskCancel' | 是 | 取消长时任务，固定取值为'continuousTaskCancel'。 |
| callback | Callback&lt;ContinuousTaskCancelInfo&gt; | 否 | 需要取消监听的回调函数，未传入则取消所有注册回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Callback parameter error;<br> 2. Unregister type has not register; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

const callback = (info: backgroundTaskManager.ContinuousTaskCancelInfo) => {
  console.info('continuousTaskCancel callback id ' + info.id);
  console.info('continuousTaskCancel callback reason ' + info.reason);
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    try {
      backgroundTaskManager.off('continuousTaskCancel', callback);
    } catch (error) {
      console.error(`Operation offContinuousTaskCancel failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};

```


## off('continuousTaskSuspend')

```TypeScript
function off(type: 'continuousTaskSuspend', callback?: Callback<ContinuousTaskSuspendInfo>): void
```

取消长时任务暂停的监听，使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continuousTaskSuspend' | 是 | 事件回调类型，固定取值为'continuousTaskSuspend'，表示长时任务暂停。 |
| callback | Callback&lt;ContinuousTaskSuspendInfo&gt; | 否 | 需要取消监听的回调函数，未传入则取消所有注册的暂停回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

const callback = (info: backgroundTaskManager.ContinuousTaskSuspendInfo) => {
  console.info('continuousTaskSuspend callback continuousTaskId: ' + info.continuousTaskId);
  console.info('continuousTaskSuspend callback suspendState: ' + info.suspendState);
  console.info('continuousTaskSuspend callback suspendReason: ' + info.suspendReason);
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    try {
      backgroundTaskManager.off('continuousTaskSuspend', callback);
    } catch (error) {
      console.error(`Operation offContinuousTaskSuspend failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};

```


## off('continuousTaskActive')

```TypeScript
function off(type: 'continuousTaskActive', callback?: Callback<ContinuousTaskActiveInfo>): void
```

取消长时任务激活的监听，使用callback异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continuousTaskActive' | 是 | 事件回调类型，固定取值为'continuousTaskActive'，表示长时任务激活。 |
| callback | Callback&lt;ContinuousTaskActiveInfo&gt; | 否 | 需要取消监听的回调函数，未传入则取消所有注册的激活回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |

**示例：**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

const callback = (info: backgroundTaskManager.ContinuousTaskActiveInfo) => {
  console.info('continuousTaskActive callback id: ' + info.id);
}

export default class EntryAbility extends UIAbility {
  onCreate() {
    try {
      backgroundTaskManager.off('continuousTaskActive', callback);
    } catch (error) {
      console.error(`Operation offContinuousTaskActive failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};

```

