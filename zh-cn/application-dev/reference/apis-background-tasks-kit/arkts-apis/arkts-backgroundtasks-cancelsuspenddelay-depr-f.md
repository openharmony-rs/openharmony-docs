# cancelSuspendDelay

## cancelSuspendDelay

```TypeScript
function cancelSuspendDelay(requestId: number): void
```

取消延迟挂起。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [cancelSuspendDelay](arkts-backgroundtasks-cancelsuspenddelay-f.md#cancelsuspenddelay-1)

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestId | number | 是 | 延迟挂起的请求ID。这个值通过调用[requestSuspendDelay](arkts-backgroundtasks-requestsuspenddelay-depr-f.md#requestsuspenddelay-1)方法获取。 |

**示例：**

```TypeScript
let delayInfo = backgroundTaskManager.requestSuspendDelay('test', () => {});
backgroundTaskManager.cancelSuspendDelay(delayInfo.requestId);

```

