# subscribe

## 导入模块

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## subscribe

```TypeScript
function subscribe(info: NotificationExtensionSubscriptionInfo[]): Promise<void>
```

订阅通知扩展。使用蓝牙模块相关接口获取蓝牙设备的唯一地址后方可订阅。使用Promise异步回调。

**起始版本：** 22

**需要权限：** ohos.permission.SUBSCRIBE_NOTIFICATION

<!--Device-notificationExtensionSubscription-function subscribe(info: NotificationExtensionSubscriptionInfo[]): Promise<void>--><!--Device-notificationExtensionSubscription-function subscribe(info: NotificationExtensionSubscriptionInfo[]): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NotificationExtensionSubscriptionInfo](arkts-notification-notificationextensionsubscriptioninfo-i.md)[] | 是 | 订阅的信息列表（数组）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied or current device not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600023](../errorcode-notification.md#1600023-应用未实现notificationsubscriberextensionability) | The application does not implement the NotificationSubscriberExtensionAbility. |

**示例：**

```TypeScript

let infos: notificationExtensionSubscription.NotificationExtensionSubscriptionInfo[] = [
  {
    addr: '01:23:45:67:89:AB', // 使用动态获取的蓝牙地址
    type: notificationExtensionSubscription.SubscribeType.BLUETOOTH
  }
];
notificationExtensionSubscription.subscribe(infos).then(() => {
  console.info(`subscribe success`);
}).catch((err: BusinessError) => {
  console.error(`subscribe fail: ${JSON.stringify(err)}`);
});


```

