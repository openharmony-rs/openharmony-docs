# getNotificationStatisticsByBundle（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

<a id="getnotificationstatisticsbybundle"></a>
## getNotificationStatisticsByBundle

```TypeScript
function getNotificationStatisticsByBundle(bundles: BundleOption[]): Promise<BundleNotificationStatistics[]>
```

批量获取指定应用列表的通知统计信息，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function getNotificationStatisticsByBundle(bundles: BundleOption[]): Promise<BundleNotificationStatistics[]>--><!--Device-notificationManager-function getNotificationStatisticsByBundle(bundles: BundleOption[]): Promise<BundleNotificationStatistics[]>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundles | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md)[] | 是 | 应用的包信息列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleNotificationStatistics[]&gt; | Promise对象。返回指定应用列表的通知统计信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundles: notificationManager.BundleOption[] = [
  { bundle:"com.example.test01" },
  { bundle:"com.example.test02" }
];
notificationManager.getNotificationStatisticsByBundle(bundles).then(
  (data: notificationManager.BundleNotificationStatistics[]) => {
  console.info(`getNotificationStatisticsByBundle success, data is ${JSON.stringify(data)}`)
}).catch((err: BusinessError):void => {
  console.error(`getNotificationStatisticsByBundle err: ${JSON.stringify(err)}`)
});

```

