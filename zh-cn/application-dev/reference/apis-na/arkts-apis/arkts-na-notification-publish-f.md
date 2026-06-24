# publish

## publish

```TypeScript
function publish(request: NotificationRequest, callback: AsyncCallback<void>): void
```

发布通知（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** publish

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | NotificationRequest | 是 | 用于设置要发布通知的内容和相关配置信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 发布通知的回调方法。 |


## publish

```TypeScript
function publish(request: NotificationRequest): Promise<void>
```

发布通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** publish

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | NotificationRequest | 是 | 用于设置要发布通知的内容和相关配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

