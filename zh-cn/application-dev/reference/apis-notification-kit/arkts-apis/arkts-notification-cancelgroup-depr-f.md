# cancelGroup

## cancelGroup

```TypeScript
function cancelGroup(groupName: string, callback: AsyncCallback<void>): void
```

取消本应用指定组下的通知（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** cancelGroup

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupName | string | 是 | 通知组名称，此名称需要在发布通知时通过[NotificationRequest](arkts-notification-requestenablenotification-depr-f.md#requestenablenotification-1)对象指定。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 取消本应用指定组下通知的回调函数。 |


## cancelGroup

```TypeScript
function cancelGroup(groupName: string): Promise<void>
```

取消本应用指定组下的通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** cancelGroup

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupName | string | 是 | 通知组名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

