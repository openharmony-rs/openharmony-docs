# WebNativeMessagingExtensionAbility

为开发者提供Web原生消息通信能力，继承自ExtensionAbility。

**继承/实现关系：** WebNativeMessagingExtensionAbility extends ExtensionAbility

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class WebNativeMessagingExtensionAbility--><!--Device-unnamed-declare class WebNativeMessagingExtensionAbility-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onConnectNative

```TypeScript
onConnectNative(info: ConnectionInfo): void
```

Web原生消息连接建立时回调此方法。在此回调中，可以获取连接信息，用于后续的消息通信处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebNativeMessagingExtensionAbility-onConnectNative(info: ConnectionInfo): void--><!--Device-WebNativeMessagingExtensionAbility-onConnectNative(info: ConnectionInfo): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [ConnectionInfo](arkts-na-web-webnativemessagingextensionability-connectioninfo-i.md) | 是 | 连接信息对象。 |

## onDestroy

```TypeScript
onDestroy(): void
```

WebNativeMessagingExtensionAbility销毁时回调。在此回调中，可以释放所有占用的资源，并完成最终的清理操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebNativeMessagingExtensionAbility-onDestroy(): void--><!--Device-WebNativeMessagingExtensionAbility-onDestroy(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onDisconnectNative

```TypeScript
onDisconnectNative(info: ConnectionInfo): void
```

Web原生消息连接断开时回调此方法。在此回调中，可以释放与该连接相关的资源，并完成必要的清理工作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebNativeMessagingExtensionAbility-onDisconnectNative(info: ConnectionInfo): void--><!--Device-WebNativeMessagingExtensionAbility-onDisconnectNative(info: ConnectionInfo): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [ConnectionInfo](arkts-na-web-webnativemessagingextensionability-connectioninfo-i.md) | 是 | Indicates connection information about new native connection. |

## context

```TypeScript
context: WebNativeMessagingExtensionContext
```

当前Web原生消息扩展Ability的上下文。

**类型：** [WebNativeMessagingExtensionContext](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensioncontext-webnativemessagingextensioncontext-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebNativeMessagingExtensionAbility-context: WebNativeMessagingExtensionContext--><!--Device-WebNativeMessagingExtensionAbility-context: WebNativeMessagingExtensionContext-End-->

**系统能力：** SystemCapability.Web.Webview.Core

