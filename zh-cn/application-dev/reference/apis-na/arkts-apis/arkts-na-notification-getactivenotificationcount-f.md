# getActiveNotificationCount

## getActiveNotificationCount

```TypeScript
function getActiveNotificationCount(callback: AsyncCallback<number>): void
```

获取当前应用未删除的通知数（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getActiveNotificationCount

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;number&gt; | 是 | 获取未删除通知数回调函数。 |


## getActiveNotificationCount

```TypeScript
function getActiveNotificationCount(): Promise<number>
```

获取当前应用未删除的通知数（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getActiveNotificationCount

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 以Promise形式返回获取当前应用未删除通知数。 |

