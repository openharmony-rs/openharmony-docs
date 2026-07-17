# requestSuspendDelay

## requestSuspendDelay

```TypeScript
function requestSuspendDelay(reason: string, callback: Callback<void>): DelaySuspendInfo
```

后台应用申请延迟挂起。

延迟挂起时间一般情况下默认值为3分钟，低电量（依据系统低电量广播）时默认值为1分钟。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [requestSuspendDelay](arkts-backgroundtasks-backgroundtaskmanager-requestsuspenddelay-f.md#requestsuspenddelay-1)

<!--Device-backgroundTaskManager-function requestSuspendDelay(reason: string, callback: Callback<void>): DelaySuspendInfo--><!--Device-backgroundTaskManager-function requestSuspendDelay(reason: string, callback: Callback<void>): DelaySuspendInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 延迟挂起申请的原因。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<void> | 是 | 延迟即将超时的回调函数，一般在超时前6秒通过此回调通知应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DelaySuspendInfo](arkts-backgroundtasks-backgroundtaskmanager-delaysuspendinfo-i.md) | 返回延迟挂起信息。 |

**示例：**

```TypeScript
import backgroundTaskManager from '@ohos.backgroundTaskManager';

// 设置延迟任务挂起的原因
let myReason = 'test requestSuspendDelay';
// 申请延迟任务
let delayInfo = backgroundTaskManager.requestSuspendDelay(myReason, () => {
  console.info('Request suspension delay will time out.');
})
// 打印延迟任务信息
let id = delayInfo.requestId;
let time = delayInfo.actualDelayTime;
console.info('The requestId is: ' + id);
console.info('The actualDelayTime is: ' + time);

```

