# offBadgeNumberQuery（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## offBadgeNumberQuery

```TypeScript
function offBadgeNumberQuery(): void
```

取消应用角标数量查询回调。

**起始版本：** 22

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function offBadgeNumberQuery(): void--><!--Device-notificationManager-function offBadgeNumberQuery(): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
try{
    notificationManager.offBadgeNumberQuery();
} catch (err) {
    console.error(`OffBadgeNumberQuery failed, code is ${err.code}, message is ${err.message}`);
}

```

