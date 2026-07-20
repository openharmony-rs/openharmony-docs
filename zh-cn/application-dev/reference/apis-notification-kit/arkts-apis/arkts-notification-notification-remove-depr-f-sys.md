# remove（系统接口）

<a id="remove"></a>
## remove

```TypeScript
function remove(
    bundle: BundleOption,
    notificationKey: NotificationKey,
    reason: RemoveReason,
    callback: AsyncCallback<void>
  ): void
```

删除指定通知（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** remove

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(
    bundle: BundleOption,
    notificationKey: NotificationKey,
    reason: RemoveReason,
    callback: AsyncCallback<void>
  ): void--><!--Device-notification-function remove(
    bundle: BundleOption,
    notificationKey: NotificationKey,
    reason: RemoveReason,
    callback: AsyncCallback<void>
  ): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |
| notificationKey | [NotificationKey](arkts-notification-notificationsubscribe-notificationkey-i-sys.md) | 是 | 通知键值。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除指定通知回调函数。 |


<a id="remove-1"></a>
## remove

```TypeScript
function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>
```

删除指定通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** remove

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>--><!--Device-notification-function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |
| notificationKey | [NotificationKey](arkts-notification-notificationsubscribe-notificationkey-i-sys.md) | 是 | 通知键值。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |


<a id="remove-2"></a>
## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void
```

删除指定通知（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** remove

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void--><!--Device-notification-function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCode | string | 是 | 通知唯一ID。可以通过[onConsume](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#onconsume)回调的入参[SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md)获取其内部[NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md)对象中的hashCode。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除指定通知回调函数。 |


<a id="remove-3"></a>
## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason): Promise<void>
```

删除指定通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** remove

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(hashCode: string, reason: RemoveReason): Promise<void>--><!--Device-notification-function remove(hashCode: string, reason: RemoveReason): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCode | string | 是 | 通知唯一ID。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

