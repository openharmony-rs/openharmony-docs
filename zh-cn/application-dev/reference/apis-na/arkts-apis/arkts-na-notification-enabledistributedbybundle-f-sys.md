# enableDistributedByBundle（系统接口）

## enableDistributedByBundle

```TypeScript
function enableDistributedByBundle(bundle: BundleOption, enable: boolean, callback: AsyncCallback<void>): void
```

设置指定应用是否支持分布式通知（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setDistributedEnableByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 应用的包信息。 |
| enable | boolean | 是 | 是否支持。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 应用程序是否支持分布式通知的回调函数。 |


## enableDistributedByBundle

```TypeScript
function enableDistributedByBundle(bundle: BundleOption, enable: boolean): Promise<void>
```

设置指定应用是否支持分布式通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setDistributedEnableByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 应用的包。 |
| enable | boolean | 是 | 是否支持。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

