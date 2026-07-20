# @ohos.application.NotificationSubscriberExtensionAbility

## 导入模块

```TypeScript
import { NotificationSubscriberExtensionAbility } from '@kit.NotificationKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [NotificationSubscriberExtensionAbility](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md) | NotificationSubscriberExtensionAbility是通知订阅者扩展能力的基类，提供通知订阅的相关功能。三方穿戴类应用（如手表配套应用）通过继承此类实现回调逻辑，在本机发布通知时接收通知信息并通过蓝牙转发给穿戴设备，在本机通知被取消时接收取消通知的回调并转发给穿戴设备删除对应通知。  当穿戴类应用需要获取本机通知并同步到配对的穿戴设备时，使用本模块。本模块与notificationExtensionSubscription模块配合使用，本模块负责在回调中接收和处理通知数据，notificationExtensionSubscription模块负责授权、订阅和取消订阅等管理操作。 |

