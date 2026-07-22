# NotificationSubscriberExtensionAbility

NotificationSubscriberExtensionAbility是通知订阅者扩展能力的基类，提供通知订阅的相关功能。三方穿戴类应用（如手表配套应用）通过继承此类实现回调逻辑，在本机发布通知时接收通知信息并通过蓝牙转发给穿戴设备，在本机通知被取消时接收取消通知的回调并转发给穿戴设备删除对应通知。

当穿戴类应用需要获取本机通知并同步到配对的穿戴设备时，使用本模块。本模块与notificationExtensionSubscription模块配合使用，本模块负责在回调中接收和处理通知数据，notificationExtensionSubscription模块负责授权、订阅和取消订阅等管理操作。
> **说明：**  
>  
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
> 本模块接口仅可在Stage模型下使用。

**起始版本：** 22

<!--Device-unnamed-declare class NotificationSubscriberExtensionAbility--><!--Device-unnamed-declare class NotificationSubscriberExtensionAbility-End-->

**系统能力：** SystemCapability.Notification.Notification

## 导入模块

```TypeScript
import { NotificationSubscriberExtensionAbility } from '@kit.NotificationKit';
```

## onCancelMessages

```TypeScript
onCancelMessages(hashCodes: Array<string>): void
```

取消通知时的回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSubscriberExtensionAbility-onCancelMessages(hashCodes: Array<string>): void--><!--Device-NotificationSubscriberExtensionAbility-onCancelMessages(hashCodes: Array<string>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hashCodes | Array&lt;string&gt; | 是 | 要取消的通知的哈希码列表。通过onReceiveMessage获取。 |

**示例：**

```TypeScript
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onCancelMessages(hashCodes: Array<string>): void {
    console.info(`${TAG} onCancelMessages. hashCodes: ${JSON.stringify(hashCodes)}`);
  }
}

```

## onDestroy

```TypeScript
onDestroy(): void
```

通知订阅扩展被销毁时的回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSubscriberExtensionAbility-onDestroy(): void--><!--Device-NotificationSubscriberExtensionAbility-onDestroy(): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**示例：**

```TypeScript
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onDestroy(): void {
    console.info(`${TAG} onDestroy`);
  }
}

```

## onReceiveMessage

```TypeScript
onReceiveMessage(notificationInfo: NotificationInfo): void
```

收到通知时回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSubscriberExtensionAbility-onReceiveMessage(notificationInfo: NotificationInfo): void--><!--Device-NotificationSubscriberExtensionAbility-onReceiveMessage(notificationInfo: NotificationInfo): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| notificationInfo | [NotificationInfo](arkts-notification-notificationinfo-i.md) | 是 | 通知订阅扩展能力中onReceiveMessage回调的通知信息。 |

**示例：**

```TypeScript
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onReceiveMessage(notificationInfo: notificationExtensionSubscription.NotificationInfo): void {
    console.info(`${TAG} onReceiveMessage. notificationInfo: ${JSON.stringify(notificationInfo)}`);
  }
}

```

## context

```TypeScript
context: NotificationSubscriberExtensionContext
```

NotificationSubscriberExtensionAbility的上下文环境。

**类型：** NotificationSubscriberExtensionContext

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSubscriberExtensionAbility-context: NotificationSubscriberExtensionContext--><!--Device-NotificationSubscriberExtensionAbility-context: NotificationSubscriberExtensionContext-End-->

**系统能力：** SystemCapability.Notification.Notification

