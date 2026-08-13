# requestEnableNotification

## requestEnableNotification

```TypeScript
function requestEnableNotification(callback: AsyncCallback<void>): void
```

应用请求通知使能（Callback形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestEnableNotification)

<!--Device-notification-function requestEnableNotification(callback: AsyncCallback<void>): void--><!--Device-notification-function requestEnableNotification(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 应用请求通知使能的回调函数。 |


## requestEnableNotification

```TypeScript
function requestEnableNotification(): Promise<void>
```

应用请求通知使能（Promise形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestEnableNotification)

<!--Device-notification-function requestEnableNotification(): Promise<void>--><!--Device-notification-function requestEnableNotification(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

