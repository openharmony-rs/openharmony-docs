# isNotificationEnabled（系统接口）

## 导入模块

```TypeScript
```

## isNotificationEnabled

```TypeScript
function isNotificationEnabled(bundle: BundleOption, callback: AsyncCallback<boolean>): void
```

获取指定应用的通知使能状态（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 获取通知使能状态回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let isNotificationEnabledCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("isNotificationEnabled failed " + JSON.stringify(err));
  } else {
    console.info("isNotificationEnabled success");
  }
}
let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.isNotificationEnabled(bundle, isNotificationEnabledCallback);
```


## isNotificationEnabled

```TypeScript
function isNotificationEnabled(bundle: BundleOption): Promise<boolean>
```

获取指定应用的通知使能状态（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md)

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
| Promise &lt;boolean&gt; | 以Promise形式返回获取指定应用的通知使能状态的结果。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.isNotificationEnabled(bundle).then((data) => {
  console.info("isNotificationEnabled success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`isNotificationEnabled failed, code is ${err}`);
});
```


## isNotificationEnabled

```TypeScript
function isNotificationEnabled(callback: AsyncCallback<boolean>): void
```

获取通知使能状态（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 获取通知使能状态回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let isNotificationEnabledCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("isNotificationEnabled failed " + JSON.stringify(err));
  } else {
    console.info("isNotificationEnabled success");
  }
}

Notification.isNotificationEnabled(isNotificationEnabledCallback);
```


## isNotificationEnabled

```TypeScript
function isNotificationEnabled(): Promise<boolean>
```

获取通知使能状态（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;boolean&gt; | 以Promise形式返回获取通知使能状态的结果。 |

**示例**

```TypeScript
import Base from '@ohos.base';

Notification.isNotificationEnabled().then((data: boolean) => {
  console.info("isNotificationEnabled success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`isNotificationEnabled failed, code is ${err}`);
});
```


## isNotificationEnabled

```TypeScript
function isNotificationEnabled(userId: number, callback: AsyncCallback<boolean>): void
```

获取指定用户ID下的通知使能状态。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 指定的用户ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 获取通知使能状态回调函数（true：使能，false：禁止）。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let isNotificationEnabledCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("isNotificationEnabled failed " + JSON.stringify(err));
  } else {
    console.info("isNotificationEnabled success");
  }
}
let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.isNotificationEnabled(bundle, isNotificationEnabledCallback);
```

```TypeScript
import Base from '@ohos.base';

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.isNotificationEnabled(bundle).then((data) => {
  console.info("isNotificationEnabled success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`isNotificationEnabled failed, code is ${err}`);
});
```

```TypeScript
import Base from '@ohos.base';

let isNotificationEnabledCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("isNotificationEnabled failed " + JSON.stringify(err));
  } else {
    console.info("isNotificationEnabled success");
  }
}

Notification.isNotificationEnabled(isNotificationEnabledCallback);
```

```TypeScript
import Base from '@ohos.base';

Notification.isNotificationEnabled().then((data: boolean) => {
  console.info("isNotificationEnabled success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`isNotificationEnabled failed, code is ${err}`);
});
```


## isNotificationEnabled

```TypeScript
function isNotificationEnabled(userId: number): Promise<boolean>
```

获取指定用户下的通知使能状态。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 指定的用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;boolean&gt; | 以Promise形式返回获取通知使能状态的结果（true：使能，false：禁止）。 |

**示例**

参见 [isNotificationEnabled](#isnotificationenabled)
