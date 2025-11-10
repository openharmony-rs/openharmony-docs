# @ohos.notificationExtensionSubscription (notificationExtensionSubscription模块)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

本模块提供管理通知扩展的功能，包括打开设置界面、订阅和取消订阅通知、获取和设置通知授权状态、获取通知信息。

> **说明：**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
## 导入模块

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## notificationExtensionSubscription.openSubscriptionSettings

openSubscriptionSettings(context: UIAbilityContext): Promise\<void\>

打开应用的通知扩展订阅者设置页面，以半模态弹窗显示。用户可在该页面设置通知的启用状态及模式。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.SUBSCRIBE_NOTIFICATION

**参数：**

| 参数名   | 类型                     | 必填 | 说明                 |
| -------- | ------------------------ | ---- |--------------------|
| context | [UIAbilityContext](../../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | 是   | 通知设置页面绑定Ability的上下文。 |

**返回值：**

| 类型     | 说明 | 
| ------- |--|
| Promise\<void\> | Promise对象，无返回结果。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)、[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 1600001  | Internal error.                     |
| 1600018  | the notification settings window is already displayed.           |
| 1600023  | The application does not implement the NotificationSubscriberExtensionAbility.           |

**示例：**

```ts
import notificationExtensionSubscription from '@ohos.notificationExtensionSubscription'
import { common } from '@kit.AbilityKit';

try {
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  notificationExtensionSubscription.openSubscriptionSettings(context).then(() => {
    hilog.info(DOMAIN, 'testTag', `openSubscriberSettings success`);
  }).catch((err) => {
    hilog.error(DOMAIN, 'testTag', `failed to call openSubscriptionSettings ${JSON.stringify(err)}`)
  });
} catch (error) {
  hilog.error(DOMAIN, 'testTag', `failed to call openSubscriptionSettings ${JSON.stringify(error)}`)
}
hilog.info(DOMAIN, 'testTag', `openSubscriberSettings success`);
```

## notificationExtensionSubscription.subscribe

subscribe(info: NotificationExtensionSubscriptionInfo[]): Promise\<void\>

连接蓝牙地址，并实现[NotificationSubscriberExtensionAbility](../apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md)后方可订阅通知。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.SUBSCRIBE_NOTIFICATION

**参数：**

| 参数名     | 类型                                        | 必填 | 说明                                        |
| -------- | ------------------------------------------- | ---- | ------------------------------------------- |
| info  | [NotificationExtensionSubscriptionInfo[]](js-apis-inner-notificationExtensionSubscriptionInfo.md) | 是   | 订阅的信息列表（数组）。 |

**返回值：**

| 类型     | 说明 | 
| ------- |--|
| Promise\<void\> | Promise对象，无返回结果。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)、[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                                              |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied. |
| 1600001  | Internal error.                                      |
| 1600003  | Failed to connect to the service.                    |
| 1600023  | The application does not implement the NotificationSubscriberExtensionAbility.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let infos: notificationExtensionSubscription.NotificationExtensionSubscriptionInfo[] = [
  {
    addr: '01:23:45:67:89:AB', // 使用动态获取的蓝牙地址
    type: notificationExtensionSubscription.SubscribeType.BLUETOOTH
  }
];
notificationExtensionSubscription.subscribe(infos).then(() => {
  console.info("subscribe success");
}).catch((err: BusinessError) => {
  console.error(`subscribe fail: ${JSON.stringify(err)}`);
});

```

## notificationExtensionSubscription.unsubscribe

unsubscribe(): Promise\<void\>

取消通知的订阅。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.SUBSCRIBE_NOTIFICATION

**返回值：**

| 类型     | 说明 | 
| ------- |--|
| Promise\<void\> | Promise对象，无返回结果。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied. |
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationExtensionSubscription.unsubscribe().then(() => {
  console.info("unsubscribe success");
}).catch((err: BusinessError) => {
  console.error(`unsubscribe fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.getSubscribeInfo

getSubscribeInfo(): Promise\<NotificationExtensionSubscriptionInfo[]\>

获取当前应用的通知订阅信息。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.SUBSCRIBE_NOTIFICATION

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<[NotificationExtensionSubscriptionInfo[]](js-apis-inner-notificationExtensionSubscriptionInfo.md)\> | Promise对象，返回一个[NotificationExtensionSubscriptionInfo[]](js-apis-inner-notificationExtensionSubscriptionInfo.md)对象数组，表示应用的订阅信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied. |
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationExtensionSubscription.getSubscribeInfo().then((data) => {
  console.info(`getSubscribeInfo successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getSubscribeInfo fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.isUserGranted

isUserGranted(): Promise\<boolean\>

查询用户是否启用了通知扩展订阅功能。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.SUBSCRIBE_NOTIFICATION

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<boolean\> | Promise对象。返回ture表示功能被启用；返回false表示功能没有被启用。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)、[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                                              |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied. | 
| 1600001  | Internal error.                                      |
| 1600003  | Failed to connect to the service.                           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationExtensionSubscription.isUserGranted().then((isOpen: boolean) => {
  if (isOpen) {
    console.info('isUserGranted true');
  } else {
    console.info('isUserGranted false');
  }
}).catch((err: BusinessError) => {
  console.error(`isUserGranted fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.getUserGrantedEnabledBundles

getUserGrantedEnabledBundles(): Promise\<String[]\>

查询当前应用的通知扩展订阅功能，获取其授权接收的消息来源。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.SUBSCRIBE_NOTIFICATION

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<String[]\>   | Promise对象，返回被授权可接收哪些应用通知消息的应用名。        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

notificationExtensionSubscription.getUserGrantedEnabledBundles().then((data) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail: ${JSON.stringify(err)}`);
});
```

## NotificationExtensionSubscriptionInfo

type NotificationExtensionSubscriptionInfo = _NotificationExtensionSubscriptionInfo

用于描述通知扩展订阅的信息。

**系统能力**： SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_NotificationExtensionSubscriptionInfo](js-apis-inner-notificationExtensionSubscriptionInfo.md) | 用于描述通知扩展订阅的信息。 |

## SubscribeType

表示通知扩展订阅的类型。

**系统能力**：SystemCapability.Notification.Notification

**类型**：

| 名称                 | 值       | 说明       |
| -------------------- | -------- | ---------- |
| BLUETOOTH          | 0 | 通过蓝牙订阅通知。 |

## BundleOption

type BundleOption = _BundleOption

指定应用的包信息。

**系统能力**： SystemCapability.Notification.Notification

| 类型 | 说明 |
| --- | --- |
| [_BundleOption](js-apis-inner-notification-notificationCommonDef.md#bundleoption) | 指定应用的包信息。 |
