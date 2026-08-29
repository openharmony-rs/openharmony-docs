# isBadgeDisplayed（系统接口）

## 导入模块

```TypeScript
```

## isBadgeDisplayed

```TypeScript
function isBadgeDisplayed(bundle: BundleOption, callback: AsyncCallback<boolean>): void
```

获取指定应用的角标使能状态（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isBadgeDisplayed](arkts-notification-notificationmanager-isbadgedisplayed-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 获取角标使能状态回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let isBadgeDisplayedCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("isBadgeDisplayed failed " + JSON.stringify(err));
  } else {
    console.info("isBadgeDisplayed success");
  }
}
let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.isBadgeDisplayed(bundle, isBadgeDisplayedCallback);
```


## isBadgeDisplayed

```TypeScript
function isBadgeDisplayed(bundle: BundleOption): Promise<boolean>
```

获取指定应用的角标使能状态（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isBadgeDisplayed](arkts-notification-notificationmanager-isbadgedisplayed-f-sys.md)

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
| Promise &lt;boolean&gt; | 以Promise形式返回获取指定应用的角标使能状态。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.isBadgeDisplayed(bundle).then((data) => {
  console.info("isBadgeDisplayed success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`isBadgeDisplayed failed, code is ${err}`);
});
```
