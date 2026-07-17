# isDistributedEnabled

## isDistributedEnabled

```TypeScript
function isDistributedEnabled(callback: AsyncCallback<boolean>): void
```

查询设备是否支持分布式通知（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isDistributedEnabled

<!--Device-notification-function isDistributedEnabled(callback: AsyncCallback<boolean>): void--><!--Device-notification-function isDistributedEnabled(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 设备是否支持分布式通知的回调函数。 |


## isDistributedEnabled

```TypeScript
function isDistributedEnabled(): Promise<boolean>
```

查询设备是否支持分布式通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isDistributedEnabled

<!--Device-notification-function isDistributedEnabled(): Promise<boolean>--><!--Device-notification-function isDistributedEnabled(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise方式返回设备是否支持分布式通知的结果。 |

