# getSlotNumByBundle（系统接口）

## getSlotNumByBundle

```TypeScript
function getSlotNumByBundle(bundle: BundleOption, callback: AsyncCallback<number>): void
```

获取指定应用的通知通道数量（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getSlotNumByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function getSlotNumByBundle(bundle: BundleOption, callback: AsyncCallback<number>): void--><!--Device-notification-function getSlotNumByBundle(bundle: BundleOption, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 获取通知通道数量回调函数。 |


## getSlotNumByBundle

```TypeScript
function getSlotNumByBundle(bundle: BundleOption): Promise<number>
```

获取指定应用的通知通道数量（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getSlotNumByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function getSlotNumByBundle(bundle: BundleOption): Promise<number>--><!--Device-notification-function getSlotNumByBundle(bundle: BundleOption): Promise<number>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | 以Promise形式返回获取指定应用的通知通道数量。 |

