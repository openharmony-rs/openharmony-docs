# removeGroupByBundle（系统接口）

## removeGroupByBundle

```TypeScript
function removeGroupByBundle(bundle: BundleOption, groupName: string, callback: AsyncCallback<void>): void
```

删除指定应用的指定组下的通知（Callback形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#removeGroupByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function removeGroupByBundle(bundle: BundleOption, groupName: string, callback: AsyncCallback<void>): void--><!--Device-notification-function removeGroupByBundle(bundle: BundleOption, groupName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用的包信息。 |
| groupName | string | 是 | 通知组名称。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 删除指定应用指定组下通知的回调函数。 |


## removeGroupByBundle

```TypeScript
function removeGroupByBundle(bundle: BundleOption, groupName: string): Promise<void>
```

删除指定应用的指定组下的通知（Promise形式）。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** ohos.notificationManager/notificationManager#removeGroupByBundle

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function removeGroupByBundle(bundle: BundleOption, groupName: string): Promise<void>--><!--Device-notification-function removeGroupByBundle(bundle: BundleOption, groupName: string): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用的包信息。 |
| groupName | string | 是 | 通知组名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

