# @ohos.notificationExtensionSubscription (notificationExtensionSubscription模块)(系统接口)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

本模块提供管理通知扩展的能力，具体包括：打开通知扩展订阅设置界面、订阅和取消订阅通知扩展、获取和设置通知授权状态。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn和ArkTS-Sta。
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本页面仅包含本模块的系统接口，其他公开接口参见[notificationExtensionSubscription](./js-apis-notificationExtensionSubscription.md)。

## 导入模块

ArkTS-Dyn示例：
```ts
import { notificationExtensionSubscription } from '@kit.NotificationKit';
import { BusinessError } from '@kit.BasicServicesKit';
```

ArkTS-Sta示例：
```ts
import notificationExtensionSubscription from '@ohos.notificationExtensionSubscription';
```

## notificationExtensionSubscription.getAllSubscriptionBundles

getAllSubscriptionBundles(): Promise\<BundleOption[]\>

获取所有具有[ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification)权限并且实现了[NotificationSubscriberExtensionAbility](./js-apis-notificationSubscriberExtensionAbility.md)的应用列表。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<[BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)\>   | Promise对象，返回所有具有[ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification)权限并且实现了[NotificationSubscriberExtensionAbility](./js-apis-notificationSubscriberExtensionAbility.md)的应用列表。        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](errorcode-notification.md)。

| 错误码ID | 错误信息                                              |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied.     |
| 202      | Not system application to call the interface.                                      |
| 1600001  | Internal error.                                      |
| 1600003  | Failed to connect to the service.                    |

**示例：**

ArkTS-Dyn示例：
```ts
notificationExtensionSubscription.getAllSubscriptionBundles().then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getAllSubscriptionBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getAllSubscriptionBundles fail, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
notificationExtensionSubscription.getAllSubscriptionBundles().then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getAllSubscriptionBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`getAllSubscriptionBundles fail, code is ${error.code}, message is ${error.message}`);
});
```

## notificationExtensionSubscription.getUserGrantedState

getUserGrantedState(targetBundle: BundleOption): Promise\<boolean\>

查询指定应用的“允许获取本机通知”的开关状态。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 需要查询的目标应用信息。应用需要具有[ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification)权限，并且实现[NotificationSubscriberExtensionAbility](../apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md)，否则返回1600022错误码。|

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<boolean\> | Promise对象，返回true表示目标应用的“允许获取本机通知”状态已启用；返回false表示目标应用的“允许获取本机通知”状态未启用。 | 

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |
| 202      | Not system application to call the interface.                                      |
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |
| 1600022  | The specified bundle is invalid.                          |

**示例：**

ArkTS-Dyn示例：
```ts
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
  console.error(`getUserGrantedState fail, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
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
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`getUserGrantedState fail, code is ${error.code}, message is ${error.message}`);
});
```

## notificationExtensionSubscription.setUserGrantedState

setUserGrantedState(targetBundle: BundleOption, enabled: boolean): Promise\<void\>

设置指定应用的“允许获取本机通知”的开关状态。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 需要设置的目标应用信息。应用需要具有[ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification)权限，并且实现[NotificationSubscriberExtensionAbility](../apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md)，否则返回1600022错误码|
| enable   | boolean | 是   | 表示应用的“允许获取本机通知”的开关状态，true表示启用，false表示未启用。 |

**返回值：**

| 类型     | 说明        |
| ------- |-----------|
| Promise\<void\> |Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |
| 202      | Not system application to call the interface.                                      |
| 1600001  | Internal error.                     |
| 1600003  | Failed to connect to the service.          |
| 1600022  | The specified bundle is invalid.                          |

**示例：**

ArkTS-Dyn示例：
```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // 应改为开发者需要查询的目标应用信息
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.setUserGrantedState(targetBundle, true).then(() => {
  console.info(`setUserGrantedState successfully.`);
}).catch((err: BusinessError) => {
  console.error(`setUserGrantedState fail, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
  {
    // 应改为开发者需要查询的目标应用信息
    bundle: 'com.example.testnotification',
  };
notificationExtensionSubscription.setUserGrantedState(targetBundle, true).then(() => {
  console.info(`setUserGrantedState successfully.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`setUserGrantedState fail, code is ${error.code}, message is ${error.message}`);
});
```

## notificationExtensionSubscription.getUserGrantedEnabledBundles

getUserGrantedEnabledBundles(targetBundle: BundleOption): Promise\<BundleOption[]\>

获取指定应用中“已获取的本机通知”通知开关开启的应用列表。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 需要查询的目标应用信息。应用需要具有[ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification)权限，并且实现[NotificationSubscriberExtensionAbility](../apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md)，否则返回1600022错误码。|

**返回值：**

| 类型     | 说明        |
| ------- |-----------|
| Promise\<[BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)\>   | Promise对象，返回指定应用中“已获取的本机通知”通知开关开启的应用列表。        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied.     |
| 202      | Not system application to call the interface. |
| 1600001  | Internal error. |
| 1600003  | Failed to connect to the service. |
| 1600022  | The specified bundle is invalid. |

**示例：**

ArkTS-Dyn示例：
```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // 应改为开发者需要查询的目标应用信息
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.getUserGrantedEnabledBundles(targetBundle).then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
  {
    // 应改为开发者需要查询的目标应用信息
    bundle: 'com.example.testnotification',
  };
notificationExtensionSubscription.getUserGrantedEnabledBundles(targetBundle).then((data: notificationExtensionSubscription.BundleOption[]) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`getUserGrantedEnabledBundles fail, code is ${error.code}, message is ${error.message}`);
});
```

## notificationExtensionSubscription.setUserGrantedBundleState

setUserGrantedBundleState(targetBundle: BundleOption, enabledBundles: BundleOption[], enabled:boolean): Promise\<void\>

设置指定应用中“已获取的本机通知”的应用通知开关状态。使用Promise异步回调。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_CONTROLLER

**系统接口**：此接口为系统接口。

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                  | 必填 | 说明                 |
| -------- | --------------------- | ---- | -------------------- |
| targetBundle    | [BundleOption](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 需要设置的目标应用信息。应用需要具有[ohos.permission.SUBSCRIBE_NOTIFICATION](../../security/AccessToken/restricted-permissions.md#ohospermissionsubscribe_notification)权限，并且实现[NotificationSubscriberExtensionAbility](../apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md)，否则返回1600022错误码。|
| enabledBundles    | [BundleOption[]](./js-apis-inner-notification-notificationCommonDef.md#bundleoption)       | 是   | 被授权的应用信息列表。 |
| enabled    | boolean       | 是   | 表示“已获取的本机通知”的应用授权状态是否启用，true表示已启用，false表示未启用。 |

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<void\> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](errorcode-notification.md)。

| 错误码ID | 错误信息                            |
| -------- | ----------------------------------- |
| 201      | Permission denied. |
| 202      | Not system application to call the interface. |
| 1600001  | Internal error. |
| 1600003  | Failed to connect to the service. |
| 1600022  | The specified bundle is invalid. |

**示例：**

ArkTS-Dyn示例：
```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
  {
    // 应改为开发者需要设置的目标应用信息
    bundle: 'com.example.testnotification',
  };
let enabledBundles: notificationExtensionSubscription.BundleOption[] = [
  // 应改为开发者需要授权的实际应用
  { bundle: 'com.example.xxx', uid: 11111111 },
  { bundle: 'com.example.xxxx', uid: 11111111 },
  { bundle: 'com.example.xxxxx' },
];
notificationExtensionSubscription.setUserGrantedBundleState(targetBundle, enabledBundles, true).then(() => {
  console.info(`setUserGrantedBundleState successfully.`);
}).catch((err: BusinessError) => {
  console.error(`setUserGrantedBundleState fail, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
let targetBundle: notificationExtensionSubscription.BundleOption =
  {
    // 应改为开发者需要设置的目标应用信息
    bundle: 'com.example.testnotification',
  };
let enabledBundles: notificationExtensionSubscription.BundleOption[] = [
  // 应改为开发者需要授权的实际应用
  { bundle: 'com.example.xxx', uid: 11111111 },
  { bundle: 'com.example.xxxx', uid: 11111111 },
  { bundle: 'com.example.xxxxx' },
];
notificationExtensionSubscription.setUserGrantedBundleState(targetBundle, enabledBundles, true).then(() => {
  console.info(`setUserGrantedBundleState successfully.`);
}).catch((err: Error): void => {
  let error: BusinessError = err as BusinessError;
  console.error(`getUserGrantedEnabledBundles fail, code is ${error.code}, message is ${error.message}`);
});
```

## notificationExtensionSubscription.subscribeNotification

subscribeNotification(priorityStrategy?: number): Promise\<void\>

根据优先通知过滤条件订阅通知。使用Promise异步回调。

**起始版本**：26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Notification.Notification

**需要权限**：ohos.permission.NOTIFICATION_SYSTEM_SUBSCRIBER

**系统接口**：此接口为系统接口。

**参数：**

| 参数名               | 类型       | 必填 | 说明                 |
| ------------------- | ---------- | ---- | -------------------- |
| priorityStrategy    | ArkTS-Dyn: number<br/>ArkTS-Sta: int     | 否   | 优先通知过滤条件。默认为0。与[PriorityStrategyStatus](js-apis-notificationManager-sys.md#prioritystrategystatus23)的枚举进行按位或运算得到该参数。<br>订阅某条优先通知策略后，应用发布通知时，只返回符合对应策略的通知。<br>当订阅默认优先策略`STATUS_SYSTEM_DEFAULT`时,表示同时订阅优先规则`STATUS_SYSTEM_RULE`、智能识别`STATUS_INTELLIGENT`、用户自定义`STATUS_USER_DEFINED`和应用自定义`STATUS_APPLICATION_DEFINED`策略。<br>当`priorityStrategy`为0时，表示不过滤优先通知策略，可以收到应用发布的所有通知。|

**返回值：**

| 类型     | 说明        | 
| ------- |-----------|
| Promise\<void\> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[通知错误码](errorcode-notification.md)。

| 错误码ID | 错误信息                             |
| -------- | ----------------------------------- |
| 201      | Permission denied or current device not supported. |
| 202      | Not system application to call the interface.      |
| 1600001  | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.The user does not exist. |
| 1600002  | Marshalling or unmarshalling error. |
| 1600003  | Failed to connect to the service.   |
| 1600022  |  The application does not implement the NotificationSubscriberExtensionAbility.   |

**示例：**

ArkTS-Dyn示例：
```ts
notificationExtensionSubscription.subscribeNotification(0).then(() => {
  console.info(`subscribeNotification successfully.`);
}).catch((err: BusinessError) => {
  console.error(`subscribeNotification failed, code is ${err.code}, message is ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
notificationExtensionSubscription.subscribeNotification(0).then(() => {
  console.info(`subscribeNotification successfully.`);
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`subscribeNotification failed, code is ${error.code}, message is ${error.message}`);
});
```