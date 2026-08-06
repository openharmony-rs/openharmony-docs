# remove（系统接口）

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.notificationSubscribe/notificationSubscribe#remove

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(    bundle: BundleOption,    notificationKey: NotificationKey,    reason: RemoveReason,    callback: AsyncCallback<void>  ): void--><!--Device-notification-function remove(    bundle: BundleOption,    notificationKey: NotificationKey,    reason: RemoveReason,    callback: AsyncCallback<void>  ): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定应用的包信息。 |
| notificationKey | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知键值。 |
| reason | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知删除原因。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 删除指定通知回调函数。 |


## remove

```TypeScript
function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>
```

删除指定通知（Promise形式）。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.notificationSubscribe/notificationSubscribe#remove

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>--><!--Device-notification-function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定应用的包信息。 |
| notificationKey | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知键值。 |
| reason | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知删除原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |


## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void
```

删除指定通知（Callback形式）。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.notificationSubscribe/notificationSubscribe#remove

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void--><!--Device-notification-function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCode | string | 是 | 通知唯一ID。可以通过[onConsume]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_回调的入参[SubscribeCallbackData]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取其内部[NotificationRequest]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_对象中的hashCode。 |
| reason | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知删除原因。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 删除指定通知回调函数。 |


## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason): Promise<void>
```

删除指定通知（Promise形式）。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** ohos.notificationSubscribe/notificationSubscribe#remove

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(hashCode: string, reason: RemoveReason): Promise<void>--><!--Device-notification-function remove(hashCode: string, reason: RemoveReason): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCode | string | 是 | 通知唯一ID。 |
| reason | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通知删除原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

