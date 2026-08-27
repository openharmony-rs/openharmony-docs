# displayBadge（系统接口）

## 导入模块

```TypeScript
```

## displayBadge

```TypeScript
function displayBadge(bundle: BundleOption, enable: boolean, callback: AsyncCallback<void>): void
```

设定指定应用的角标使能状态（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [displayBadge](arkts-notification-notificationmanager-displaybadge-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| enable | boolean | 是 | 使能状态。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 设定角标使能回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let displayBadgeCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("displayBadge failed " + JSON.stringify(err));
  } else {
    console.info("displayBadge success");
  }
}
let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.displayBadge(bundle, false, displayBadgeCallback);
```


## displayBadge

```TypeScript
function displayBadge(bundle: BundleOption, enable: boolean): Promise<void>
```

设定指定应用的角标使能状态（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [displayBadge](arkts-notification-notificationmanager-displaybadge-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| enable | boolean | 是 | 使能状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.displayBadge(bundle, false).then(() => {
  console.info("displayBadge success");
}).catch((err: Base.BusinessError) => {
  console.error(`displayBadge failed, code is ${err}`);
});
```
