# getNotificationSetting

## 导入模块

```TypeScript
import { notificationManager } from '@ohos.notificationManager';
```

## getNotificationSetting

```TypeScript
function getNotificationSetting(): Promise<NotificationSetting>
```

获取应用程序的通知设置。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NotificationSetting&gt; | Promise对象，返回此应用程序的通知设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../../errorcode-universal.md#1600001-Internal) | Internal error. |
| [1600002](../../errorcode-universal.md#1600002-Marshalling) | Marshalling or unmarshalling error. |
| [1600003](../../errorcode-universal.md#1600003-Failed) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getNotificationSetting().then((data: notificationManager.NotificationSetting) => {
    console.info(`getNotificationSetting success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getNotificationSetting failed, code is ${err.code}, message is ${err.message}`);
});

```

