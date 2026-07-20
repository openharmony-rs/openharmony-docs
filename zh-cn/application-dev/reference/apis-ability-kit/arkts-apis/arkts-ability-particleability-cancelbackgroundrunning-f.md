# cancelBackgroundRunning

## 导入模块

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

<a id="cancelbackgroundrunning"></a>
## cancelBackgroundRunning

```TypeScript
function cancelBackgroundRunning(callback: AsyncCallback<void>): void
```

向系统申请取消长时任务。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [stopBackgroundRunning](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopbackgroundrunning-1)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-particleAbility-function cancelBackgroundRunning(callback: AsyncCallback<void>): void--><!--Device-particleAbility-function cancelBackgroundRunning(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当向系统申请取消长时任务成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback(error: BusinessError, data: void) {
  if (error && error.code !== 0) {
    console.error(`Operation failed error: ${JSON.stringify(error)}`);
  } else {
    console.info(`Operation succeeded, data: ${data}`);
  }
}

particleAbility.cancelBackgroundRunning(callback);

```


<a id="cancelbackgroundrunning-1"></a>
## cancelBackgroundRunning

```TypeScript
function cancelBackgroundRunning(): Promise<void>
```

向系统申请取消长时任务。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [stopBackgroundRunning](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopbackgroundrunning-1)

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-particleAbility-function cancelBackgroundRunning(): Promise<void>--><!--Device-particleAbility-function cancelBackgroundRunning(): Promise<void>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

particleAbility.cancelBackgroundRunning().then(() => {
  console.info('Operation succeeded');
}).catch((err: BusinessError) => {
  console.error(`Operation failed cause: ${JSON.stringify(err)}`);
});

```

