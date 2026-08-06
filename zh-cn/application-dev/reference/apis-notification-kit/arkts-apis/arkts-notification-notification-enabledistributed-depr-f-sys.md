# enableDistributed（系统接口）

## enableDistributed

```TypeScript
function enableDistributed(enable: boolean, callback: AsyncCallback<void>): void
```

设置设备是否支持分布式通知（Callback形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#setDistributedEnable

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function enableDistributed(enable: boolean, callback: AsyncCallback<void>): void--><!--Device-notification-function enableDistributed(enable: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否支持。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 设置设备是否支持分布式通知的回调函数。 |


## enableDistributed

```TypeScript
function enableDistributed(enable: boolean): Promise<void>
```

设置设备是否支持分布式通知（Promise形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#setDistributedEnable

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function enableDistributed(enable: boolean): Promise<void>--><!--Device-notification-function enableDistributed(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否支持。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

