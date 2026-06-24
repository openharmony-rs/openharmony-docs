# getSlotsByBundle（系统接口）

## getSlotsByBundle

```TypeScript
function getSlotsByBundle(bundle: BundleOption, callback: AsyncCallback<Array<NotificationSlot>>): void
```

获取指定应用的所有通知通道（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getSlotsByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| callback | AsyncCallback&lt;Array&lt;NotificationSlot&gt;&gt; | 是 | 获取通知通道回调函数。 |


## getSlotsByBundle

```TypeScript
function getSlotsByBundle(bundle: BundleOption): Promise<Array<NotificationSlot>>
```

获取指定应用的所有通知通道（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getSlotsByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;NotificationSlot&gt;&gt; | 以Promise形式返回获取指定应用的通知通道。 |

