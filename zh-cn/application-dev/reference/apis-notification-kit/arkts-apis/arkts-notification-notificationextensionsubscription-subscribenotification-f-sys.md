# subscribeNotification（系统接口）

## 导入模块

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## subscribeNotification

```TypeScript
function subscribeNotification(priorityStrategy?: number): Promise<void>
```

Subscribes to notifications based on the priority strategy. This API uses a promise to return the result.

**起始版本：** 26.1.0

**需要权限：** ohos.permission.NOTIFICATION_SYSTEM_SUBSCRIBER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationExtensionSubscription-function subscribeNotification(priorityStrategy?: int): Promise<void>--><!--Device-notificationExtensionSubscription-function subscribeNotification(priorityStrategy?: int): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priorityStrategy | number | 否 | Priority strategy for filtering the notifications. This parameter is obtained by performing a bitwise OR operation on the enums of PriorityStrategyStatus. After an application subscribes to a specific priority strategy, the system returns only notifications matching the corresponding strategy when the application publishes notifications. Subscribing to the default priority strategy **STATUS_SYSTEM_DEFAULT** means subscribing simultaneously to the following strategies: **STATUS_SYSTEM_RULE**, **STATUS_INTELLIGENT**, **STATUS_USER_DEFINED**, and **STATUS_APPLICATION_DEFINED**. When **priorityStrategy** is set to **0**, no priority strategy is applied, and all notifications published by the application can be received. <br>The value should be an integer. Default value: 0. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application to call the interface. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.The user does not exist. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-无效的包信息) | The application does not implement the NotificationSubscriberExtensionAbility. |

<!--Del-->
**示例**

```TypeScript
notificationExtensionSubscription.subscribeNotification(0).then(() => {
    console.info(`subscribeNotification successfully.`);
}).catch((err: BusinessError) => {
    console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

<!--DelEnd-->
