# isNotificationEnabledSync

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## isNotificationEnabledSync

```TypeScript
function isNotificationEnabledSync(): boolean
```

同步查询当前应用通知使能状态。

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回查询通知使能状态的结果。返回true，表示允许发布通知；返回false，表示禁止发布通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
let enabled: boolean = notificationManager.isNotificationEnabledSync();
console.info(`isNotificationEnabledSync success, data is : ${JSON.stringify(enabled)}`);

```

