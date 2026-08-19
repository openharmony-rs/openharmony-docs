# offCheckNotification（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## offCheckNotification

```TypeScript
function offCheckNotification(
    callback?: (checkInfo: NotificationCheckInfo) => NotificationCheckResult
  ): void
```

通知监听回调。

**起始版本：** 23

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-notificationManager-function offCheckNotification(    callback?: (checkInfo: NotificationCheckInfo) => NotificationCheckResult  ): void--><!--Device-notificationManager-function offCheckNotification(    callback?: (checkInfo: NotificationCheckInfo) => NotificationCheckResult  ): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (checkInfo: NotificationCheckInfo) =&gt; NotificationCheckResult | 否 | 消息验证函数指针。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try{
    notificationManager.offCheckNotification();
} catch (err){
    let error: BusinessError = err as BusinessError
    console.error(`notificationManager.off failed, code is ${error.code}, message is ${error.message}`);
}
```

