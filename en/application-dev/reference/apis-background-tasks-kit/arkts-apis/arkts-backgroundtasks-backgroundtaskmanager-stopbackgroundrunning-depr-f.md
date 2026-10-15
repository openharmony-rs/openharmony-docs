# stopBackgroundRunning

## Modules to Import

```TypeScript
```

<a id="stopbackgroundrunning1"></a>

## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context, callback: AsyncCallback<void>): void
```

Requests to cancel a continuous task. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopbackgroundrunning1)(context: Context, callback: AsyncCallback&lt;void&gt;)

<!--Device-backgroundTaskManager-function stopBackgroundRunning(context: Context, callback: AsyncCallback<void>): void--><!--Device-backgroundTaskManager-function stopBackgroundRunning(context: Context, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md).<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

FA model (JS code is required for development):

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

stage model example:

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


<a id="stopbackgroundrunning2"></a>

## stopBackgroundRunning

```TypeScript
function stopBackgroundRunning(context: Context): Promise<void>
```

Requests to cancel a continuous task. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [stopBackgroundRunning](arkts-backgroundtasks-backgroundtaskmanager-stopbackgroundrunning-f.md#stopbackgroundrunning2)(context: Context)

<!--Device-backgroundTaskManager-function stopBackgroundRunning(context: Context): Promise<void>--><!--Device-backgroundTaskManager-function stopBackgroundRunning(context: Context): Promise<void>-End-->

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md).<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

FA model:

```TypeScript
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import featureAbility from '@ohos.ability.featureAbility';
import { BusinessError } from '@ohos.base';

// Cancel a continuous task.
backgroundTaskManager.stopBackgroundRunning(featureAbility.getContext()).then(() => {
  console.info('Operation stopBackgroundRunning succeeded');
}).catch((err: BusinessError) => {
  console.error(`Operation stopBackgroundRunning failed. code is ${err.code} message is ${err.message}`);
});
```
