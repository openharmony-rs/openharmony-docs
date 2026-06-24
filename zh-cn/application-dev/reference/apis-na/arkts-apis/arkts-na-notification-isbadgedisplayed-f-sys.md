# isBadgeDisplayed（系统接口）

## isBadgeDisplayed

```TypeScript
function isBadgeDisplayed(bundle: BundleOption, callback: AsyncCallback<boolean>): void
```

获取指定应用的角标使能状态（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isBadgeDisplayed

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 获取角标使能状态回调函数。 |


## isBadgeDisplayed

```TypeScript
function isBadgeDisplayed(bundle: BundleOption): Promise<boolean>
```

获取指定应用的角标使能状态（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isBadgeDisplayed

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
| Promise&lt;boolean&gt; | 以Promise形式返回获取指定应用的角标使能状态。 |

