# setDoNotDisturbDate（系统接口）

## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate, callback: AsyncCallback<void>): void
```

设置免打扰时间（Callback形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#setDoNotDisturbDate

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, callback: AsyncCallback<void>): void--><!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 免打扰时间选项。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 设置免打扰时间回调函数。 |


## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate): Promise<void>
```

设置免打扰时间（Promise形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#setDoNotDisturbDate

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate): Promise<void>--><!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 免打扰时间选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |


## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number, callback: AsyncCallback<void>): void
```

指定用户设置免打扰时间（Callback形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#setDoNotDisturbDate

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number, callback: AsyncCallback<void>): void--><!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 免打扰时间选项。 |
| userId | number | 是 | 设置免打扰时间的用户ID。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 设置免打扰时间回调函数。 |


## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number): Promise<void>
```

指定用户设置免打扰时间（Promise形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#setDoNotDisturbDate

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number): Promise<void>--><!--Device-notification-function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 免打扰时间选项。 |
| userId | number | 是 | 设置免打扰时间的用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

