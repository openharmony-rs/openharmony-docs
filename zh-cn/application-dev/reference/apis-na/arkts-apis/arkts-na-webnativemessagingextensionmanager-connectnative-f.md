# connectNative

## connectNative

```TypeScript
function connectNative(context: UIAbilityContext, want: Want, callback: WebExtensionConnectionCallback): int
```

将当前Ability连接到指定的Web原生消息扩展Ability。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WEB_NATIVE_MESSAGING

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-webNativeMessagingExtensionManager-function connectNative(context: UIAbilityContext, want: Want, callback: WebExtensionConnectionCallback): int--><!--Device-webNativeMessagingExtensionManager-function connectNative(context: UIAbilityContext, want: Want, callback: WebExtensionConnectionCallback): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | 是 | 调用方UIAbility的上下文。 |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动Ability的want信息，其parameters中需包含'ohos.arkweb.messageReadPipe'（读管道FD）、' ohos.arkweb.messageWritePipe'（写管道FD）和'ohos.arkweb.extensionOrigin'（插件URI）。 |
| callback | [WebExtensionConnectionCallback](../../apis-arkweb/arkts-apis/arkts-arkweb-webnativemessagingextensionmanager-webextensionconnectioncallback-i.md) | 是 | WebExtensionConnection状态的回调对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 连接的标识ID，由[connectNative]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

