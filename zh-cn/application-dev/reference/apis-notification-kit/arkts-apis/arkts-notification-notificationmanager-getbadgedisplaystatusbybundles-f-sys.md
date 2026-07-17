# getBadgeDisplayStatusByBundles（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getBadgeDisplayStatusByBundles

```TypeScript
function getBadgeDisplayStatusByBundles(bundles: Array<BundleOption>) : Promise<Map<BundleOption, boolean>>
```

批量获取应用角标显示状态。使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function getBadgeDisplayStatusByBundles(bundles: Array<BundleOption>) : Promise<Map<BundleOption, boolean>>--><!--Device-notificationManager-function getBadgeDisplayStatusByBundles(bundles: Array<BundleOption>) : Promise<Map<BundleOption, boolean>>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundles | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<BundleOption> | 是 | 待获取应用角标显示状态的应用包信息数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Map<BundleOption, boolean>> | Promise对象，返回应用包信息和显示角标状态的键值对集合的Promise对象 。 |

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

let bundles: Array<notificationManager.BundleOption> = [
    {
        bundle: 'bundleName',
    },
    {
        bundle: 'bundleName1',
    }
];
notificationManager.getBadgeDisplayStatusByBundles(bundles).then((data: Map<notificationManager.BundleOption, boolean>) => {
    data.forEach((value, key) => {
        console.info(`Bundle is ${key.bundle}, uid is ${key.uid}, badge status is ${value}.`);
    });
}).catch((err: BusinessError) => {
    console.error(`GetBadgeDisplayStatusByBundles failed, code is ${err.code}, message is ${err.message}`);
});

```

