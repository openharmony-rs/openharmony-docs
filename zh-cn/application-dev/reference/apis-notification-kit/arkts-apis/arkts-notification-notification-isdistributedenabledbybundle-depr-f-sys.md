# isDistributedEnabledByBundle（系统接口）

<a id="isdistributedenabledbybundle"></a>
## isDistributedEnabledByBundle

```TypeScript
function isDistributedEnabledByBundle(bundle: BundleOption, callback: AsyncCallback<boolean>): void
```

根据应用的包获取应用程序是否支持分布式通知（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isDistributedEnabledByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function isDistributedEnabledByBundle(bundle: BundleOption, callback: AsyncCallback<boolean>): void--><!--Device-notification-function isDistributedEnabledByBundle(bundle: BundleOption, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 应用的包。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 查询指定应用是否支持分布式通知的回调函数。 |


<a id="isdistributedenabledbybundle-1"></a>
## isDistributedEnabledByBundle

```TypeScript
function isDistributedEnabledByBundle(bundle: BundleOption): Promise<boolean>
```

查询指定应用是否支持分布式通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isDistributedEnabledByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function isDistributedEnabledByBundle(bundle: BundleOption): Promise<boolean>--><!--Device-notification-function isDistributedEnabledByBundle(bundle: BundleOption): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 应用的包。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise方式返回指定应用是否支持分布式通知的结果。 |

