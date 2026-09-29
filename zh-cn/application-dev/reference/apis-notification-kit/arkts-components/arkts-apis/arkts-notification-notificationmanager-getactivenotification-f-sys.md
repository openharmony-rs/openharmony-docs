# getActiveNotification（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getActiveNotification

```TypeScript
function getActiveNotification(hashCode: string): Promise<NotificationRequest>
```

根据通知的唯一标识hashCode获取当前未删除的通知信息。使用Promise异步回调。

**起始版本：** 26.2.0

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationManager-function getActiveNotification(hashCode: string): Promise<NotificationRequest>--><!--Device-notificationManager-function getActiveNotification(hashCode: string): Promise<NotificationRequest>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCode | string | 是 | 通知的唯一标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md)&gt; | 以Promise形式返回获取通知信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.The user does not exist. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |
