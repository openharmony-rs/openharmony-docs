# getActiveNotificationCount

<a id="getactivenotificationcount"></a>
## getActiveNotificationCount

```TypeScript
function getActiveNotificationCount(callback: AsyncCallback<number>): void
```

获取当前应用未删除的通知数（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getActiveNotificationCount

<!--Device-notification-function getActiveNotificationCount(callback: AsyncCallback<number>): void--><!--Device-notification-function getActiveNotificationCount(callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 获取未删除通知数回调函数。 |


<a id="getactivenotificationcount-1"></a>
## getActiveNotificationCount

```TypeScript
function getActiveNotificationCount(): Promise<number>
```

获取当前应用未删除的通知数（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getActiveNotificationCount

<!--Device-notification-function getActiveNotificationCount(): Promise<number>--><!--Device-notification-function getActiveNotificationCount(): Promise<number>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 以Promise形式返回获取当前应用未删除通知数。 |

