# stopBackgroundRunning

<a id="stopbackgroundrunning"></a>
## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context, callback: AsyncCallback<void>): void
```

向系统申请取消长时任务，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [stopBackgroundRunning(context:](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopbackgroundrunning-1)

<!--Device-backgroundTaskManager-function stopBackgroundRunning(context: Context, callback: AsyncCallback<void>): void--><!--Device-backgroundTaskManager-function stopBackgroundRunning(context: Context, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用运行的上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，取消长时任务成功时，err为undefined，否则为错误对象。 |

**示例：**

FA模型示例（需使用js代码开发）：

```TypeScript
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import featureAbility from '@ohos.ability.featureAbility';
import { BusinessError } from '@ohos.base';

const callback = (err: BusinessError, data: void) => {
  if (err) {
    console.error(`Operation stopBackgroundRunning failed. code is ${err.code} message is ${err.message}`);
  } else {
    console.info('Operation stopBackgroundRunning succeeded');
  }
}

backgroundTaskManager.stopBackgroundRunning(featureAbility.getContext(), callback);


```

Stage模型示例：

```TypeScript
import UIAbility from '@ohos.app.ability.UIAbility';
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import Want from '@ohos.app.ability.Want';
import AbilityConstant from '@ohos.app.ability.AbilityConstant';
import { BusinessError } from '@ohos.base';

const callback = (err: BusinessError, data: void) => {
  if (err) {
    console.error(`Operation stopBackgroundRunning failed. code is ${err.code} message is ${err.message}`);
  } else {
    console.info('Operation stopBackgroundRunning succeeded');
  }
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    backgroundTaskManager.stopBackgroundRunning(this.context, callback);
  }
};

```


<a id="stopbackgroundrunning-1"></a>
## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context): Promise<void>
```

向系统申请取消长时任务，使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [stopBackgroundRunning(context:](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopbackgroundrunning-1)

<!--Device-backgroundTaskManager-function stopBackgroundRunning(context: Context): Promise<void>--><!--Device-backgroundTaskManager-function stopBackgroundRunning(context: Context): Promise<void>-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | - 应用运行的上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例：**

FA模型示例：

```TypeScript
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import featureAbility from '@ohos.ability.featureAbility';
import { BusinessError } from '@ohos.base';

// 取消长时任务
backgroundTaskManager.stopBackgroundRunning(featureAbility.getContext()).then(() => {
  console.info('Operation stopBackgroundRunning succeeded');
}).catch((err: BusinessError) => {
  console.error(`Operation stopBackgroundRunning failed. code is ${err.code} message is ${err.message}`);
});


```

Stage模型示例：

```TypeScript
import UIAbility from '@ohos.app.ability.UIAbility';
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import Want from '@ohos.app.ability.Want';
import AbilityConstant from '@ohos.app.ability.AbilityConstant';
import { BusinessError } from '@ohos.base';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    // 取消长时任务
    backgroundTaskManager.stopBackgroundRunning(this.context).then(() => {
      console.info('Operation stopBackgroundRunning succeeded');
    }).catch((err: BusinessError) => {
      console.error(`Operation stopBackgroundRunning failed. code is ${err.code} message is ${err.message}`);
    });
  }
};

```

