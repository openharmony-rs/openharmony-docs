# @ohos.notificationExtensionSubscription (notificationExtensionSubscription模块)(系统接口)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->

本模块提供管理通知扩展的功能，包括打开设置界面、订阅和取消订阅通知、获取和设置通知授权状态、获取通知信息。

> **说明：**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本页面仅包含本模块的系统接口，其他公开接口参见[notificationExtensionSubscription](./js-apis-notificationExtensionSubscription.md)。

## 导入模块

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## notificationExtensionSubscription.getAllSubscriptionBundles

getAllSubscriptionBundles(): Promise\<BundleOption[]\>

获取所有已被用户授权的订阅应用列表。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<[BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)\>   | 返回所有启用了通知扩展订阅的应用包信息。        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)、[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                                              |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied.     |  
| 202      | Not system application to call the interface.                                      |  
| 1600001  | Internal error.                                      |
| 1600003  | Failed to connect to the service.                    |

**示例：**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

notificationExtensionSubscription.getAllSubscriptionBundles().then((data) => {
  console.info('getAllSubscriptionBundles successfully. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getAllSubscriptionBundles fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.getUserGrantedState

getUserGrantedState(targetBundle: BundleOption): Promise\<boolean\>

查询指定应用的通知扩展订阅功能是否已启用。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 需要查询的目标应用信息。 |

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<boolean\> | Promise对象。表示目标应用的订阅功能是否被启用。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 202      | Not system application to call the interface.                                      |  
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |
| 1600022  | The specified bundle is invalid.                          |

**示例：**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // 应改为开发者需要查询的目标应用信息
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.getUserGrantedState(targetBundle).then((isOpen: boolean) => {
  if (isOpen) {
    console.info('GrantedState true');
  } else {
    console.info('GrantedState false');
  }
}).catch((err: BusinessError) => {
  console.error(`getAllSubscriptionBundles fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.setUserGrantedState

setUserGrantedState(targetBundle: BundleOption, enabled: boolean): Promise\<void\>

设置指定应用的通知扩展订阅状态（启用或禁用）。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 需要设置的目标应用信息。 |
| enable   | boolean | 是   | 是否启用通知扩展订阅。 |

**返回值：**

| 类型     | 说明        |
| ------- |-----------|
| Promise\<void\> | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 202      | Not system application to call the interface.                                      |  
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |
| 1600022  | The specified bundle is invalid.                          |

**示例：**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // 应改为开发者需要查询的目标应用信息
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.setUserGrantedState(targetBundle, true).then((data) => {
  console.info('setUserGrantedState successfully. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`setUserGrantedState fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.getUserGrantedEnabledBundles

getUserGrantedEnabledBundles(targetBundle: BundleOption): Promise\<BundleOption[]\>

查询指定应用（targetBundle）的通知扩展订阅功能，获取其授权接收的消息来源。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 需要查询的目标应用信息。 |

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<[BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)\>   | Promise对象，其中包含被授权可接收哪些应用通知消息的应用列表。        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |  
| 202      | Not system application to call the interface.                                      |  
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |
| 1600022  | The specified bundle is invalid.                          |

**示例：**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // 应改为开发者需要查询的目标应用信息
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.getUserGrantedEnabledBundles(targetBundle).then((data) => {
  console.info('getUserGrantedEnabledBundles successfully. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail: ${JSON.stringify(err)}`);
});
```

## notificationExtensionSubscription.setUserGrantedBundleState

setUserGrantedBundleState(targetBundle: BundleOption, enabledBundles: BundleOption[], enabled:boolean): Promise\<void\>

设置指定应用（targetBundle）通知扩展订阅功能的授权应用列表。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 需要设置的目标应用信息。 |
| enabledBundles    | [BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 被授权的应用信息列表。 |
| enabled    | boolean       | 是   | 是否启用。 |

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<void\> | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](./errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied. |
| 202      | Not system application to call the interface.                                      |  
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |
| 1600022  | The specified bundle is invalid.                          |

**示例：**

```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundle: notificationExtensionSubscription.BundleOption =
  {
    // 应改为开发者需要设置的目标应用信息
    bundle: 'com.example.testnotification',
  };
let enabledBundles: notificationExtensionSubscription.BundleOption[] = [
  // 应改为开发者需要授权的实际应用
  {bundle: 'com.example.xxx',uid:11111111},
  {bundle: 'com.example.xxxx',uid:11111111},
  {bundle: 'com.example.xxxxx'},
];
notificationExtensionSubscription.setUserGrantedBundleState(targetBundle, enabledBundles, true).then((data) => {
  console.info('setUserGrantedBundleState successfully. Data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`setUserGrantedBundleState fail: ${JSON.stringify(err)}`);
});
```

## SubscribeType

表示通知扩展订阅的类型。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

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
