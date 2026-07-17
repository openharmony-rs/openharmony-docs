# setBadgeDisplayStatusByBundles（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setBadgeDisplayStatusByBundles

```TypeScript
function setBadgeDisplayStatusByBundles(badges: Map<BundleOption, boolean>) : Promise<void>
```

批量设置指定应用是否显示角标。使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function setBadgeDisplayStatusByBundles(badges: Map<BundleOption, boolean>) : Promise<void>--><!--Device-notificationManager-function setBadgeDisplayStatusByBundles(badges: Map<BundleOption, boolean>) : Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| badges | [Map](../../apis-arkts/arkts-apis/arkts-arkts-collections-map-c.md)<BundleOption, boolean> | 是 | 应用包名信息和角标显示状态的列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let badges = new Map<notificationManager.BundleOption, boolean>();
let bundle: notificationManager.BundleOption = {
    bundle: 'bundleName',
};
badges.set(bundle, true);

notificationManager.setBadgeDisplayStatusByBundles(badges).then(() => {
    console.info('SetBadgeDisplayStatusByBundles success.');
}).catch((err: BusinessError) => {
    console.error(`SetBadgeDisplayStatusByBundles failed, code is ${err.code}, message is ${err.message}`);
});

```

