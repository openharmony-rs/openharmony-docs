# setDoNotDisturbDate（系统接口）

## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate, callback: AsyncCallback<void>): void
```

设置免打扰时间（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setDoNotDisturbDate

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | DoNotDisturbDate | 是 | 免打扰时间选项。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 设置免打扰时间回调函数。 |


## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate): Promise<void>
```

设置免打扰时间（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setDoNotDisturbDate

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | DoNotDisturbDate | 是 | 免打扰时间选项。 |

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

**废弃版本：** 9

**替代接口：** setDoNotDisturbDate

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | DoNotDisturbDate | 是 | 免打扰时间选项。 |
| userId | number | 是 | 设置免打扰时间的用户ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 设置免打扰时间回调函数。 |


## setDoNotDisturbDate

```TypeScript
function setDoNotDisturbDate(date: DoNotDisturbDate, userId: number): Promise<void>
```

指定用户设置免打扰时间（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setDoNotDisturbDate

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | DoNotDisturbDate | 是 | 免打扰时间选项。 |
| userId | number | 是 | 设置免打扰时间的用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

