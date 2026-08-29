# requestEnableNotification

## 导入模块

```TypeScript
```

## requestEnableNotification

```TypeScript
function requestEnableNotification(callback: AsyncCallback<void>): void
```

应用请求通知使能（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md)

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 应用请求通知使能的回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let requestEnableNotificationCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("requestEnableNotification failed " + JSON.stringify(err));
  } else {
    console.info("requestEnableNotification success");
  }
};

Notification.requestEnableNotification(requestEnableNotificationCallback);
```


## requestEnableNotification

```TypeScript
function requestEnableNotification(): Promise<void>
```

应用请求通知使能（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md)

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

Notification.requestEnableNotification().then(() => {
  console.info("requestEnableNotification success");
}).catch((err: Base.BusinessError) => {
  console.error(`requestEnableNotification failed, code is ${err}`);
});
```
