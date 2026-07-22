# getUserGrantedEnabledBundles（系统接口）

## 导入模块

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## getUserGrantedEnabledBundles

```TypeScript
function getUserGrantedEnabledBundles(targetBundle: BundleOption): Promise<BundleOption[]>
```

获取指定应用中“已获取的本机通知”通知开关开启的应用列表。使用Promise异步回调。

**起始版本：** 22

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationExtensionSubscription-function getUserGrantedEnabledBundles(targetBundle: BundleOption): Promise<BundleOption[]>--><!--Device-notificationExtensionSubscription-function getUserGrantedEnabledBundles(targetBundle: BundleOption): Promise<BundleOption[]>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetBundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 需要查询的目标应用信息。应用需要具有ohos.permission.SUBSCRIBE_NOTIFICATION权限，并且实现[NotificationSubscriberExtensionAbility](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md)，否则返回1600022错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleOption[]&gt; | Promise对象，返回指定应用中“已获取的本机通知”通知开关开启的应用列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-无效的包信息) | The specified bundle is invalid. |

**示例：**

```TypeScript
let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // 应改为开发者需要查询的目标应用信息
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.getUserGrantedEnabledBundles(targetBundle).then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail: ${JSON.stringify(err)}`);
});

```

