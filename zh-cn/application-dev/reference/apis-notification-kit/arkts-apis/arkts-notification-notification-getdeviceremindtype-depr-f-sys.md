# getDeviceRemindType（系统接口）

<a id="getdeviceremindtype"></a>
## getDeviceRemindType

```TypeScript
function getDeviceRemindType(callback: AsyncCallback<DeviceRemindType>): void
```

获取通知的提醒方式（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getDeviceRemindType

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function getDeviceRemindType(callback: AsyncCallback<DeviceRemindType>): void--><!--Device-notification-function getDeviceRemindType(callback: AsyncCallback<DeviceRemindType>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DeviceRemindType&gt; | 是 | 获取通知提醒方式的回调函数。 |


<a id="getdeviceremindtype-1"></a>
## getDeviceRemindType

```TypeScript
function getDeviceRemindType(): Promise<DeviceRemindType>
```

获取通知的提醒方式（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getDeviceRemindType

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function getDeviceRemindType(): Promise<DeviceRemindType>--><!--Device-notification-function getDeviceRemindType(): Promise<DeviceRemindType>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DeviceRemindType&gt; | Promise方式返回获取通知提醒方式的结果。 |

