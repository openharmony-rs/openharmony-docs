# subscribeNotification（系统接口）

## 导入模块

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## subscribeNotification

```TypeScript
function subscribeNotification(priorityStrategy?: number): Promise<void>
```

根据优先通知过滤条件订阅通知。使用Promise异步回调。

**起始版本：** 26.2.0

**需要权限：** ohos.permission.NOTIFICATION_SYSTEM_SUBSCRIBER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-notificationExtensionSubscription-function subscribeNotification(priorityStrategy?: int): Promise<void>--><!--Device-notificationExtensionSubscription-function subscribeNotification(priorityStrategy?: int): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priorityStrategy | number | 否 | 优先通知过滤条件。与PriorityStrategyStatus的枚举进行按位或运算得到该参数。订阅某条优先通知策略后，应用发布通知时，只返回符合对应策略的通知。当订阅默认优先策略`STATUS_SYSTEM_DEFAULT`时,表示同时订阅优先规则`STATUS_SYSTEM_RULE`、智能识别`STATUS_INTELLIGENT`、用户自定义`STATUS_USER_DEFINED`和应用自定义`STATUS_APPLICATION_DEFINED`策略。当`priorityStrategy`为0时，表示不过滤优先通知策略，可以收到应用发布的所有通知。<br>取值限定为整数。默认值：0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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
