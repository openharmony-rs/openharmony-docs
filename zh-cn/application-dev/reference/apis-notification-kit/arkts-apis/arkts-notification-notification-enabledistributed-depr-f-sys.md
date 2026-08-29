# enableDistributed（系统接口）

## 导入模块

```TypeScript
```

## enableDistributed

```TypeScript
function enableDistributed(enable: boolean, callback: AsyncCallback<void>): void
```

设置设备是否支持分布式通知（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否支持。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 设置设备是否支持分布式通知的回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let enabledNotificationCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("enableDistributed failed " + JSON.stringify(err));
  } else {
    console.info("enableDistributed success");
  }
};

let enable: boolean = true;

Notification.enableDistributed(enable, enabledNotificationCallback);
```


## enableDistributed

```TypeScript
function enableDistributed(enable: boolean): Promise<void>
```

设置设备是否支持分布式通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否支持。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let enable: boolean = true;
Notification.enableDistributed(enable).then(() => {
  console.info("enableDistributed success");
}).catch((err: Base.BusinessError) => {
  console.error(`enableDistributed failed, code is ${err}`);
});
```
