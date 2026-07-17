# remove（系统接口）

## 导入模块

```TypeScript
import { notificationSubscribe } from '@kit.NotificationKit';
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

根据应用的包信息和通知键值，删除指定通知。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationSubscribe-function remove(
    bundle: BundleOption,
    notificationKey: NotificationKey,
    reason: RemoveReason,
    callback: AsyncCallback<void>
  ): void--><!--Device-notificationSubscribe-function remove(
    bundle: BundleOption,
    notificationKey: NotificationKey,
    reason: RemoveReason,
    callback: AsyncCallback<void>
  ): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |
| notificationKey | [NotificationKey](arkts-notification-notificationsubscribe-notificationkey-i-sys.md) | 是 | 通知键值。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 删除指定通知回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationManager } from '@kit.NotificationKit';

let removeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`remove failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("remove success");
  }
}
let bundle: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: notificationSubscribe.NotificationKey = {
  id: 0,
  label: "label",
};
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CLICK_REASON_REMOVE;
notificationSubscribe.remove(bundle, notificationKey, reason, removeCallback);

```


## remove

```TypeScript
function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>
```

根据应用的包信息和通知键值，删除指定通知。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationSubscribe-function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>--><!--Device-notificationSubscribe-function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md) | 是 | 指定应用的包信息。 |
| notificationKey | [NotificationKey](arkts-notification-notificationsubscribe-notificationkey-i-sys.md) | 是 | 通知键值。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationManager } from '@kit.NotificationKit';

let bundle: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: notificationSubscribe.NotificationKey = {
  id: 0,
  label: "label",
};
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CLICK_REASON_REMOVE;
notificationSubscribe.remove(bundle, notificationKey, reason).then(() => {
  console.info("remove success");
}).catch((err: BusinessError) => {
  console.error(`remove fail: ${JSON.stringify(err)}`);
});

```


## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void
```

通过通知的唯一ID，删除指定通知。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationSubscribe-function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void--><!--Device-notificationSubscribe-function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCode | string | 是 | 通知唯一ID。可以通过[onConsume](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#onconsume)回调的入参[SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md)获取其内部[NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md)对象中的hashCode。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 删除指定通知回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCode: string = 'hashCode';
let removeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`remove failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("remove success");
  }
}
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CANCEL_REASON_REMOVE;
notificationSubscribe.remove(hashCode, reason, removeCallback);

```


## remove

```TypeScript
function remove(hashCodes: Array<String>, reason: RemoveReason, callback: AsyncCallback<void>): void
```

批量删除指定通知。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationSubscribe-function remove(hashCodes: Array<String>, reason: RemoveReason, callback: AsyncCallback<void>): void--><!--Device-notificationSubscribe-function remove(hashCodes: Array<String>, reason: RemoveReason, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCodes | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<String> | 是 | 通知唯一ID数组集合。可以通过[onConsume](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#onconsume)回调的入参[SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md)获取其内部[NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md)对象中的hashCode。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 删除指定通知回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCodes: string[] = ['hashCode1', 'hashCode2'];
let removeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`remove failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("remove success");
  }
}
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CANCEL_REASON_REMOVE;
notificationSubscribe.remove(hashCodes, reason, removeCallback);

```


## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason): Promise<void>
```

通过通知的唯一ID，删除指定通知。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationSubscribe-function remove(hashCode: string, reason: RemoveReason): Promise<void>--><!--Device-notificationSubscribe-function remove(hashCode: string, reason: RemoveReason): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCode | string | 是 | 通知唯一ID。可以通过[onConsume](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#onconsume)回调的入参[SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md)获取其内部[NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md)对象中的hashCode。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-通知不存在) | The notification does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCode: string = 'hashCode';
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CLICK_REASON_REMOVE;
notificationSubscribe.remove(hashCode, reason).then(() => {
  console.info("remove success");
}).catch((err: BusinessError) => {
  console.error(`remove fail: ${JSON.stringify(err)}`);
});

```


## remove

```TypeScript
function remove(hashCodes: Array<String>, reason: RemoveReason): Promise<void>
```

批量删除指定通知。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationSubscribe-function remove(hashCodes: Array<String>, reason: RemoveReason): Promise<void>--><!--Device-notificationSubscribe-function remove(hashCodes: Array<String>, reason: RemoveReason): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCodes | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<String> | 是 | 通知唯一ID数组集合。 |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | 是 | 通知删除原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCodes: string[] = ['hashCode1','hashCode2'];
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CLICK_REASON_REMOVE;
notificationSubscribe.remove(hashCodes, reason).then(() => {
  console.info("remove success");
}).catch((err: BusinessError) => {
  console.error(`remove fail: ${JSON.stringify(err)}`);
});

```

