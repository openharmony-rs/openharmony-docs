# openSubscriptionSettings

## 导入模块

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## openSubscriptionSettings

```TypeScript
function openSubscriptionSettings(context: UIAbilityContext): Promise<void>
```

打开应用的通知扩展订阅授权页面，以半模态弹窗形式显示。用户可在该页面授权“允许获取本机通知”开关与“已获取的本机通知”应用开关。使用Promise异步回调。

**起始版本：** 22

**需要权限：** ohos.permission.SUBSCRIBE_NOTIFICATION

<!--Device-notificationExtensionSubscription-function openSubscriptionSettings(context: UIAbilityContext): Promise<void>--><!--Device-notificationExtensionSubscription-function openSubscriptionSettings(context: UIAbilityContext): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | 是 | 通知设置页面绑定Ability的上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied or current device not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600018](../errorcode-notification.md#1600018-通知设置页面已经拉起) | The notification settings window is already displayed. |
| [1600023](../errorcode-notification.md#1600023-app-notificationsubscriberextensionability未实现) | The application does not implement the NotificationSubscriberExtensionAbility. |

**示例：**

```TypeScript
import { common } from '@kit.AbilityKit';

try {
  // 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  notificationExtensionSubscription.openSubscriptionSettings(context).then(() => {
    console.info(`openSubscriberSettings success`);
  }).catch((e:Error) => {
    let error = e as BusinessError
    console.error(`failed to call openSubscriptionSettings ${JSON.stringify(error)}`)
  });
} catch (error) {
  console.error(`failed to call openSubscriptionSettings ${JSON.stringify(error)}`)
}

```

