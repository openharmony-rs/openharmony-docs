# remove（系统接口）

## 导入模块

```TypeScript
```

## remove

```TypeScript
function remove(
    bundle: BundleOption,
    notificationKey: NotificationKey,
    reason: RemoveReason,
    callback: AsyncCallback<void>
  ): void
```

删除指定通知（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [remove](arkts-notification-notificationsubscribe-remove-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| notificationKey | NotificationKey | 是 | 通知键值。 |
| reason | RemoveReason | 是 | 通知删除原因。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除指定通知回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let removeCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("remove failed " + JSON.stringify(err));
  } else {
    console.info("remove success");
  }
}
let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: Notification.NotificationKey = {
  id: 0,
  label: "label",
};
let reason: Notification.RemoveReason = Notification.RemoveReason.CLICK_REASON_REMOVE;
Notification.remove(bundle, notificationKey, reason, removeCallback);
```


## remove

```TypeScript
function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>
```

删除指定通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [remove](arkts-notification-notificationsubscribe-remove-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | BundleOption | 是 | 指定应用的包信息。 |
| notificationKey | NotificationKey | 是 | 通知键值。 |
| reason | RemoveReason | 是 | 通知删除原因。 |

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
let notificationKey: Notification.NotificationKey = {
  id: 0,
  label: "label",
};
let reason: Notification.RemoveReason = Notification.RemoveReason.CLICK_REASON_REMOVE;
Notification.remove(bundle, notificationKey, reason).then(() => {
  console.info("remove success");
}).catch((err: Base.BusinessError) => {
  console.error(`remove failed, code is ${err}`);
});
```


## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void
```

删除指定通知（Callback形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [remove](arkts-notification-notificationsubscribe-remove-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCode | string | 是 | 通知唯一ID。可以通过[onConsume](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#onconsume) 回调的入参[SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md)获取其内部 [NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md)对象中的hashCode。 |
| reason | RemoveReason | 是 | 通知删除原因。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 删除指定通知回调函数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let hashCode: string = 'hashCode';

let removeCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("remove failed " + JSON.stringify(err));
  } else {
    console.info("remove success");
  }
}
let reason: Notification.RemoveReason = Notification.RemoveReason.CANCEL_REASON_REMOVE;
Notification.remove(hashCode, reason, removeCallback);
```


## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason): Promise<void>
```

删除指定通知（Promise形式）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [remove](arkts-notification-notificationsubscribe-remove-f-sys.md)

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCode | string | 是 | 通知唯一ID。 |
| reason | RemoveReason | 是 | 通知删除原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let hashCode: string = 'hashCode';
let reason: Notification.RemoveReason = Notification.RemoveReason.CLICK_REASON_REMOVE;
Notification.remove(hashCode, reason).then(() => {
  console.info("remove success");
}).catch((err: Base.BusinessError) => {
  console.error(`remove failed, code is ${err}`);
});
```
