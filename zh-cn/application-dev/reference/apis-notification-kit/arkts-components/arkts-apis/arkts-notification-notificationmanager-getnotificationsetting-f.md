# getNotificationSetting

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getNotificationSetting

```TypeScript
function getNotificationSetting(): Promise<NotificationSetting>
```

获取应用的通知设置，包括锁屏通知、横幅通知、桌面角标、振动、铃声等开关状态。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

**参见：**

[openNotificationSettings](arkts-notification-notificationmanager-opennotificationsettings-f.md) 拉起应用的通知设置界面。

[isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md) 获取指定应用的通知使能状态。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[NotificationSetting](arkts-notification-notificationmanager-notificationsetting-i.md)&gt; | Promise对象，返回此应用的通知设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.getNotificationSetting().then((data: notificationManager.NotificationSetting) => {
    console.info(`getNotificationSetting success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getNotificationSetting failed, code is ${err.code}, message is ${err.message}`);
});
```
