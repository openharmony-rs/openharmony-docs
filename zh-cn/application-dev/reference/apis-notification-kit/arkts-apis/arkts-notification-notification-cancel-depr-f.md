# cancel

## cancel

```TypeScript
function cancel(id: number, callback: AsyncCallback<void>): void
```

取消与指定通知ID相匹配的已发布通知（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** cancel

<!--Device-notification-function cancel(id: number, callback: AsyncCallback<void>): void--><!--Device-notification-function cancel(id: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 通知ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |


## cancel

```TypeScript
function cancel(id: number, label: string, callback: AsyncCallback<void>): void
```

通过通知ID和通知标签取消已发布的通知（callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** cancel

<!--Device-notification-function cancel(id: number, label: string, callback: AsyncCallback<void>): void--><!--Device-notification-function cancel(id: number, label: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 通知ID。 |
| label | string | 是 | 通知标签。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 表示被指定的回调方法。 |


## cancel

```TypeScript
function cancel(id: number, label?: string): Promise<void>
```

取消与指定通知ID相匹配的已发布通知，label可以指定也可以不指定（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** cancel

<!--Device-notification-function cancel(id: number, label?: string): Promise<void>--><!--Device-notification-function cancel(id: number, label?: string): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 通知ID。 |
| label | string | 否 | 通知标签，默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

