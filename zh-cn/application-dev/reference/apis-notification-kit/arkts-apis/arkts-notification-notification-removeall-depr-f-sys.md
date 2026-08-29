# removeAll（系统接口）

## 导入模块

```TypeScript
```

## removeAll

```TypeScript
function removeAll(bundle: BundleOption, callback: AsyncCallback<void>): void
```

删除指定应用的所有通知（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除指定应用的所有通知回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let removeAllCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("removeAll failed " + JSON.stringify(err));
  } else {
    console.info("removeAll success");
  }
}
let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.removeAll(bundle, removeAllCallback);
```


## removeAll

```TypeScript
function removeAll(callback: AsyncCallback<void>): void
```

删除所有通知（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除所有通知回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let removeAllCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("removeAll failed " + JSON.stringify(err));
  } else {
    console.info("removeAll success");
  }
}

Notification.removeAll(removeAllCallback);
```


## removeAll

```TypeScript
function removeAll(userId: number, callback: AsyncCallback<void>): void
```

删除指定用户下的所有通知（callback形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除指定用户所有通知回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

function removeAllCallback(err: Base.BusinessError) {
  if (err) {
    console.error("removeAll failed " + JSON.stringify(err));
  } else {
    console.info("removeAll success");
  }
}

let userId: number = 1;
Notification.removeAll(userId, removeAllCallback);
```


## removeAll

```TypeScript
function removeAll(userId: number): Promise<void>
```

删除指定用户下的所有通知（Promise形式）。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let userId: number = 1;
Notification.removeAll(userId).then(() => {
  console.info("removeAll success");
}).catch((err: Base.BusinessError) => {
  console.error(`removeAll failed, code is ${err}`);
});
```


## removeAll

```TypeScript
function removeAll(bundle?: BundleOption): Promise<void>
```

删除指定应用的所有通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeAll](arkts-notification-notificationsubscribe-removeall-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 否 | 指定应用的包信息。默认为空，表示删除所有通知。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

// 不指定应用时，删除所有通知
Notification.removeAll().then(() => {
  console.info("removeAll success");
}).catch((err: Base.BusinessError) => {
  console.error(`removeAll failed, code is ${err}`);
});
```
