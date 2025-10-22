# @ohos.application.NotificationSubscriberExtensionAbility (通知订阅扩展能力)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

NotificationSubscriberExtensionAbility 是通知订阅者扩展能力的基类，提供通知订阅的相关功能。

> **说明：**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块接口仅可在Stage模型下使用。
> 本模块为系统接口。

## 导入模块

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import NotificationSubscriberExtensionAbility from '@ohos.application.NotificationSubscriberExtensionAbility'
import extensionSubscription from '@ohos.notificationExtensionSubscription';
```
```json5
{
    "name": "NotificationSubscriberExtAbility",
    "srcEntry": "./ets/notificationsubscriberextability/NotificationSubscriberExtAbility.ets",
    "type": "notificationSubscriber",
    "description": "$string:NotificationSubscriberExtAbility_desc",
    "icon": "$media:layered_image",
    "label": "$string:NotificationSubscriberExtAbility_label",
    "exported": true
}
```

## NotificationSubscriberExtensionAbility

### 属性

**系统能力**：SystemCapability.Notification.Notification


| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| context | [NotificationSubscriberExtensionContext](js-apis-application-NotificationSubscriberExtensionContext.md)  | 否 | 否 | NotificationSubscriberExtensionAbility的上下文环境。|


### onDestroy

onDestroy(): void

xtensionAbility生命周期回调在销毁时执行资源清理等操作。。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。


**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import NotificationSubscriberExtensionAbility from '@ohos.application.NotificationSubscriberExtensionAbility'
import extensionSubscription from '@ohos.notificationExtensionSubscription';

const DOMAIN = 0x0000;
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onDestroy(): void {
    hilog.info(DOMAIN, 'testTag', `${TAG} onDestroy`);
  }
}
```

### onReceiveMessage

onReceiveMessage(notificationInfo: NotificationInfo): void

当系统收到通知时回调。

**系统能力**：SystemCapability.Notification.Notification

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| notificationInfo |  [NotificationInfo](../apis-notification-kit/js-apis-inner-notification-notificationInfo.md) | 是 | 当前Extension相关的WantAgent信息，包括ability名称、bundle名称等。|
**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import NotificationSubscriberExtensionAbility from '@ohos.application.NotificationSubscriberExtensionAbility'
import extensionSubscription from '@ohos.notificationExtensionSubscription';

const DOMAIN = 0x0000;
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
    onReceiveMessage(notificationInfo: extensionSubscription.NotificationInfo): void {
    hilog.info(DOMAIN, 'testTag', `${TAG} onReceiveMessage. notificationInfo: ${JSON.stringify(notificationInfo)}`);
  }
}
```

### onCancelMessages

onCancelMessages(hashCodes: Array\<string>): void

取消通知时的回调。

**系统能力**：SystemCapability.Notification.Notification

**系统能力**：此接口为系统能力。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| hashCodes |  Array\<string\>| 是 | 要取消的通知的哈希码列表。|

**示例：**

```ts
import { hilog } from '@kit.PerformanceAnalysisKit';
import NotificationSubscriberExtensionAbility from '@ohos.application.NotificationSubscriberExtensionAbility'
import extensionSubscription from '@ohos.notificationExtensionSubscription';

const DOMAIN = 0x0000;
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
    onCancelMessages(hashCodes: Array<string>): void {
        hilog.info(DOMAIN, 'testTag', `${TAG} onReceiveMessage. hashCodes: ${JSON.stringify(hashCodes)}`);
    }
}
```