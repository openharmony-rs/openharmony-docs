# removeGroupByBundle（系统接口）

## 导入模块

```TypeScript
```

## removeGroupByBundle

```TypeScript
function removeGroupByBundle(bundle: BundleOption, groupName: string, callback: AsyncCallback<void>): void
```

删除指定应用的指定组下的通知（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 应用的包信息。 |
| groupName | string | 是 | 通知组名称。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除指定应用指定组下通知的回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let removeGroupByBundleCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("removeGroupByBundle failed " + JSON.stringify(err));
  } else {
    console.info("removeGroupByBundle success");
  }
}

let bundleOption: Notification.BundleOption = {bundle: "Bundle"};
let groupName: string = "GroupName";

Notification.removeGroupByBundle(bundleOption, groupName, removeGroupByBundleCallback);
```


## removeGroupByBundle

```TypeScript
function removeGroupByBundle(bundle: BundleOption, groupName: string): Promise<void>
```

删除指定应用的指定组下的通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 应用的包信息。 |
| groupName | string | 是 | 通知组名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let bundleOption: Notification.BundleOption = {bundle: "Bundle"};
let groupName: string = "GroupName";
Notification.removeGroupByBundle(bundleOption, groupName).then(() => {
  console.info("removeGroupByBundle success");
}).catch((err: Base.BusinessError) => {
  console.error(`removeGroupByBundle failed, code is ${err}`);
});
```
