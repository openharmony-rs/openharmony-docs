# requestSuspendDelay

## Modules to Import

```TypeScript
```

## requestSuspendDelay

```TypeScript
function requestSuspendDelay(reason: string, callback: Callback<void>): DelaySuspendInfo
```

Requests delayed suspension after the application switches to the background.

The default duration of delayed suspension is 3 minutes when the battery level is higher than or equal to the broadcast low battery level and 1 minute when the battery level is lower than the broadcast low battery level.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-f.md)

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | string | Yes | Reason for delayed transition to the suspended state. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Invoked when a delay is about to time out. Generally, this callback is used to notify the application 6 seconds before the delay times out. |

**Return value:**

| Type | Description |
| --- | --- |
| DelaySuspendInfo | Information about the suspension delay. |

**Examples**

```TypeScript
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import { BusinessError } from '@ohos.base';

// Set the reason for delayed suspension.
let myReason = 'test requestSuspendDelay';
// Request delayed suspension.
let delayInfo = backgroundTaskManager.requestSuspendDelay(myReason, () => {
    console.info("Request suspension delay will time out.");
})
// Print the delayed suspension information.
let id = delayInfo.requestId;
let time = delayInfo.actualDelayTime;
console.info("The requestId is: " + id);
console.info("The actualDelayTime is: " + time);
```
