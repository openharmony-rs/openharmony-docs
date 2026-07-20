# setDistributedEnableByBundles（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

<a id="setdistributedenablebybundles"></a>
## setDistributedEnableByBundles

```TypeScript
function setDistributedEnableByBundles(bundleEnableInfos: Array<DistributedBundleEnableInfo>, deviceType: string): Promise<void>
```

批量设置应用是否支持跨设备协同。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function setDistributedEnableByBundles(bundleEnableInfos: Array<DistributedBundleEnableInfo>, deviceType: string): Promise<void>--><!--Device-notificationManager-function setDistributedEnableByBundles(bundleEnableInfos: Array<DistributedBundleEnableInfo>, deviceType: string): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleEnableInfos | Array&lt;DistributedBundleEnableInfo&gt; | 是 | 需要设置的应用数组。 |
| deviceType | string | 是 | 设备类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600010](../errorcode-notification.md#1600010-分布式操作失败) | Distributed operation failed. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundle1: notificationManager.DistributedBundleEnableInfo = {
    bundleName: "bundleName1",
    uid: 1,
    enable: true
};
let bundle2: notificationManager.DistributedBundleEnableInfo = {
    bundleName: "bundleName2",
    uid: 2,
    enable: true
};
let bundles: Array<notificationManager.DistributedBundleEnableInfo> = [
    bundle1,bundle2
]

let deviceType: string = "liteWearable";
notificationManager.setDistributedEnableByBundles(bundles, deviceType).then(() => {
    console.info("setDistributedEnableByBundles success");
}).catch((err: BusinessError) => {
    console.error(`setDistributedEnableByBundles failed, code is ${err.code}, message is ${err.message}`);
});

```

