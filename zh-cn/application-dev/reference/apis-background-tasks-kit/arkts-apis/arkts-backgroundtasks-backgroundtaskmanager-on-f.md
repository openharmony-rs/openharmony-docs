# on

## 导入模块

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

<a id="on"></a>
## on('continuousTaskCancel')

```TypeScript
function on(type: 'continuousTaskCancel', callback: Callback<ContinuousTaskCancelInfo>): void
```

注册长时任务取消的监听，使用callback异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

<!--Device-backgroundTaskManager-function on(type: 'continuousTaskCancel', callback: Callback<ContinuousTaskCancelInfo>): void--><!--Device-backgroundTaskManager-function on(type: 'continuousTaskCancel', callback: Callback<ContinuousTaskCancelInfo>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continuousTaskCancel' | 是 | 事件回调类型，固定取值为'continuousTaskCancel'，表示长时任务取消。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ContinuousTaskCancelInfo&gt; | 是 | 回调函数，返回长时任务取消原因等信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Callback parameter error;<br> 2. Register a exist callback type; 3. Parameter verification failed. |

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
      backgroundTaskManager.on('continuousTaskCancel', callback);
    } catch (error) {
      console.error(`Operation onContinuousTaskCancel failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};

```


<a id="on-1"></a>
## on('continuousTaskSuspend')

```TypeScript
function on(type: 'continuousTaskSuspend', callback: Callback<ContinuousTaskSuspendInfo>): void
```

注册长时任务暂停的监听，使用callback异步回调。注册该回调后，如果系统首次检测到应用未执行相应的业务，不会直接取消长时任务，而是将长时任务标记为暂停状态，如果连续检测失败，仍会取消长时任务。

长时任务处于暂停状态时，应用退后台会被挂起，回前台自动激活。

**起始版本：** 20

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

<!--Device-backgroundTaskManager-function on(type: 'continuousTaskSuspend', callback: Callback<ContinuousTaskSuspendInfo>): void--><!--Device-backgroundTaskManager-function on(type: 'continuousTaskSuspend', callback: Callback<ContinuousTaskSuspendInfo>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continuousTaskSuspend' | 是 | 事件回调类型，固定取值为'continuousTaskSuspend'，表示长时任务暂停。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ContinuousTaskSuspendInfo&gt; | 是 | 回调函数，返回长时任务暂停原因等信息。 |

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
      backgroundTaskManager.on('continuousTaskSuspend', callback);
    } catch (error) {
      console.error(`Operation onContinuousTaskSuspend failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};

```


<a id="on-2"></a>
## on('continuousTaskActive')

```TypeScript
function on(type: 'continuousTaskActive', callback: Callback<ContinuousTaskActiveInfo>): void
```

注册长时任务激活的监听，使用callback异步回调。应用回前台激活暂停的长时任务。

**起始版本：** 20

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

<!--Device-backgroundTaskManager-function on(type: 'continuousTaskActive', callback: Callback<ContinuousTaskActiveInfo>): void--><!--Device-backgroundTaskManager-function on(type: 'continuousTaskActive', callback: Callback<ContinuousTaskActiveInfo>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'continuousTaskActive' | 是 | 事件回调类型，固定取值为'continuousTaskActive'，表示长时任务激活。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ContinuousTaskActiveInfo&gt; | 是 | 回调函数，返回长时任务激活相关信息。 |

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
      backgroundTaskManager.on('continuousTaskActive', callback);
    } catch (error) {
      console.error(`Operation onContinuousTaskActive failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};

```

