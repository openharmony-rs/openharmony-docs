# enableDistributedByBundle（系统接口）

## 导入模块

```TypeScript
```

## enableDistributedByBundle

```TypeScript
function enableDistributedByBundle(bundle: BundleOption, enable: boolean, callback: AsyncCallback<void>): void
```

设置指定应用是否支持分布式通知（Callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 应用的包信息。 |
| enable | boolean | 是 | 是否支持。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 应用程序是否支持分布式通知的回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let enableDistributedByBundleCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("enableDistributedByBundle failed " + JSON.stringify(err));
  } else {
    console.info("enableDistributedByBundle success");
  }
};

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};

let enable: boolean = true;

Notification.enableDistributedByBundle(bundle, enable, enableDistributedByBundleCallback);
```


## enableDistributedByBundle

```TypeScript
function enableDistributedByBundle(bundle: BundleOption, enable: boolean): Promise<void>
```

设置指定应用是否支持分布式通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 应用的包。 |
| enable | boolean | 是 | 是否支持。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let enable: boolean = true;

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};

Notification.enableDistributedByBundle(bundle, enable).then(() => {
  console.info("enableDistributedByBundle success");
}).catch((err: Base.BusinessError) => {
  console.error(`enableDistributedByBundle failed, code is ${err}`);
});
```
