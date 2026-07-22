# removeAll（系统接口）

## removeAll

```TypeScript
function removeAll(bundle: BundleOption, callback: AsyncCallback<void>): void
```

删除指定应用的所有通知（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeAll

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function removeAll(bundle: BundleOption, callback: AsyncCallback<void>): void--><!--Device-notification-function removeAll(bundle: BundleOption, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除指定应用的所有通知回调函数。 |


## removeAll

```TypeScript
function removeAll(callback: AsyncCallback<void>): void
```

删除所有通知（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeAll

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function removeAll(callback: AsyncCallback<void>): void--><!--Device-notification-function removeAll(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除所有通知回调函数。 |


## removeAll

```TypeScript
function removeAll(userId: number, callback: AsyncCallback<void>): void
```

删除指定用户下的所有通知（callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removeAll

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function removeAll(userId: number, callback: AsyncCallback<void>): void--><!--Device-notification-function removeAll(userId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除指定用户所有通知回调函数。 |


## removeAll

```TypeScript
function removeAll(userId: number): Promise<void>
```

删除指定用户下的所有通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removeAll

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function removeAll(userId: number): Promise<void>--><!--Device-notification-function removeAll(userId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |


## removeAll

```TypeScript
function removeAll(bundle?: BundleOption): Promise<void>
```

删除指定应用的所有通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeAll

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function removeAll(bundle?: BundleOption): Promise<void>--><!--Device-notification-function removeAll(bundle?: BundleOption): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 否 | 指定应用的包信息。默认为空，表示删除所有通知。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

