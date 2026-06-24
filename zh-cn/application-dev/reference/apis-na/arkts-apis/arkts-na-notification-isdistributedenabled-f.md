# isDistributedEnabled

## isDistributedEnabled

```TypeScript
function isDistributedEnabled(callback: AsyncCallback<boolean>): void
```

查询设备是否支持分布式通知（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isDistributedEnabled

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 设备是否支持分布式通知的回调函数。 |


## isDistributedEnabled

```TypeScript
function isDistributedEnabled(): Promise<boolean>
```

查询设备是否支持分布式通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isDistributedEnabled

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise方式返回设备是否支持分布式通知的结果。 |

