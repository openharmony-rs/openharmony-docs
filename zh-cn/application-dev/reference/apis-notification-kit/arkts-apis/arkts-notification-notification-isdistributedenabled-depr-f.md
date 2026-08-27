# isDistributedEnabled

## 导入模块

```TypeScript
```

## isDistributedEnabled

```TypeScript
function isDistributedEnabled(callback: AsyncCallback<boolean>): void
```

查询设备是否支持分布式通知（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md)

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 设备是否支持分布式通知的回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let isDistributedEnabledCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("isDistributedEnabled failed " + JSON.stringify(err));
  } else {
    console.info("isDistributedEnabled success " + JSON.stringify(data));
  }
};

Notification.isDistributedEnabled(isDistributedEnabledCallback);
```


## isDistributedEnabled

```TypeScript
function isDistributedEnabled(): Promise<boolean>
```

查询设备是否支持分布式通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md)

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise方式返回设备是否支持分布式通知的结果。 |

**示例**

```TypeScript
import Base from '@ohos.base';

Notification.isDistributedEnabled().then((data: boolean) => {
    console.info("isDistributedEnabled success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`isDistributedEnabled failed, code is ${err}`);
});
```
