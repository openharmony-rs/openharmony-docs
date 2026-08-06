# isNotificationSlotEnabledByBundles（系统接口）

## isNotificationSlotEnabledByBundles

```TypeScript
function isNotificationSlotEnabledByBundles(bundles: Array<BundleOption>, type: SlotType): Promise<Map<BundleOption, boolean>>
```

批量获取多个应用的指定渠道类型的使能状态。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function isNotificationSlotEnabledByBundles(bundles: Array<BundleOption>, type: SlotType): Promise<Map<BundleOption, boolean>>--><!--Device-notificationManager-function isNotificationSlotEnabledByBundles(bundles: Array<BundleOption>, type: SlotType): Promise<Map<BundleOption, boolean>>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundles | Array&lt;BundleOption&gt; | 是 | 应用包信息数组。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_最大长度为1000且不能为空。 |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 渠道类型。所有应用共享同一个渠道类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Map&lt;BundleOption, boolean&gt;&gt; | 以Promise形式返回批量查询结果，key为应用包信息，value为渠道使能状态 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 批量查询多个应用的实况窗开关状态
const bundles: Array<notificationManager.BundleOption> = [
    { bundle: 'com.example.app1', uid: 10001 },
    { bundle: 'com.example.app2', uid: 10002 },
];

notificationManager.isNotificationSlotEnabledByBundles(
    bundles, notificationManager.SlotType.LIVE_VIEW).then((data) => {
    data.forEach((value: boolean, key: notificationManager.BundleOption) => {
        console.info(`bundle: ${key.bundle}, enabled: ${value}`);
    });
}).catch((err: BusinessError) => {
    console.error(`isNotificationSlotEnabledByBundles failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 批量查询多个应用的实况窗开关状态
const bundles: Array<notificationManager.BundleOption> = [
    { bundle: 'bundleName1', uid: 10001 },
    { bundle: 'bundleName2', uid: 10002 },
];

notificationManager.isNotificationSlotEnabledByBundles(
    bundles, notificationManager.SlotType.LIVE_VIEW).then((data) => {
    data.forEach((value: boolean, key: notificationManager.BundleOption) => {
        console.info(`bundle: ${key.bundle}, enabled: ${value}`);
    });
}).catch((err: Error): void => {
    let error: BusinessError = err as BusinessError;
    console.error(`isNotificationSlotEnabledByBundles failed, code is ${error.code}, message is ${error.message}`);
});
```

