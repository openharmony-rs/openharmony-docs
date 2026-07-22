# supportDoNotDisturbMode（系统接口）

## supportDoNotDisturbMode

```TypeScript
function supportDoNotDisturbMode(callback: AsyncCallback<boolean>): void
```

查询是否支持免打扰功能（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isSupportDoNotDisturbMode

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function supportDoNotDisturbMode(callback: AsyncCallback<boolean>): void--><!--Device-notification-function supportDoNotDisturbMode(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 查询是否支持免打扰功能回调函数。 |


## supportDoNotDisturbMode

```TypeScript
function supportDoNotDisturbMode(): Promise<boolean>
```

查询是否支持免打扰功能（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isSupportDoNotDisturbMode

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function supportDoNotDisturbMode(): Promise<boolean>--><!--Device-notification-function supportDoNotDisturbMode(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 以Promise形式返回获取是否支持免打扰功能的结果。 |

