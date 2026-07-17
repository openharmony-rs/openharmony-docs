# getActiveNotificationByFilter（系统接口）

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getActiveNotificationByFilter

```TypeScript
function getActiveNotificationByFilter(filter: NotificationFilter, callback: AsyncCallback<NotificationRequest>): void
```

获取满足条件的普通实况通知信息。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function getActiveNotificationByFilter(filter: NotificationFilter, callback: AsyncCallback<NotificationRequest>): void--><!--Device-notificationManager-function getActiveNotificationByFilter(filter: NotificationFilter, callback: AsyncCallback<NotificationRequest>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [NotificationFilter](arkts-notification-notificationrequest-notificationfilter-i-sys.md) | 是 | 查询普通实况窗的过滤条件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<NotificationRequest> | 是 | 获取满足条件的普通实况通知信息的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationSubscribe } from '@kit.NotificationKit';

let bundleOption: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: notificationSubscribe.NotificationKey = {
    id: 11,
    label: ""
};
let filter: notificationManager.NotificationFilter = {
    bundle: bundleOption,
    notificationKey: notificationKey,
    extraInfoKeys: ['event']
}
let getActiveNotificationByFilterCallback = (err: BusinessError, data: notificationManager.NotificationRequest): void => {
    if (err) {
        console.error(`getActiveNotificationByFilter failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("getActiveNotificationByFilter success");
    }
}
notificationManager.getActiveNotificationByFilter(filter, getActiveNotificationByFilterCallback);

```


## getActiveNotificationByFilter

```TypeScript
function getActiveNotificationByFilter(filter: NotificationFilter): Promise<NotificationRequest>
```

获取满足条件的普通实况通知信息。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function getActiveNotificationByFilter(filter: NotificationFilter): Promise<NotificationRequest>--><!--Device-notificationManager-function getActiveNotificationByFilter(filter: NotificationFilter): Promise<NotificationRequest>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [NotificationFilter](arkts-notification-notificationrequest-notificationfilter-i-sys.md) | 是 | 查询普通实况窗的过滤条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<NotificationRequest> | 以Promise形式返回获取的满足条件的普通实况通知信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationSubscribe } from '@kit.NotificationKit';

let bundleOption: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: notificationSubscribe.NotificationKey = {
    id: 11,
    label: ""
};
let filter: notificationManager.NotificationFilter = {
    bundle: bundleOption,
    notificationKey: notificationKey,
    extraInfoKeys: ['event']
}
notificationManager.getActiveNotificationByFilter(filter).then((data: notificationManager.NotificationRequest) => {
    console.info(`getActiveNotificationByFilter success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getActiveNotificationByFilter failed, code is ${err.code}, message is ${err.message}`);
});

```

