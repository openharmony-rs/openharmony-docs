# WebExtensionConnectionCallback

作为连接网络原生消息扩展时的输入参数，它用于接收连接期间的状态变化。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webNativeMessagingExtensionManager-interface WebExtensionConnectionCallback--><!--Device-webNativeMessagingExtensionManager-interface WebExtensionConnectionCallback-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## onConnect

```TypeScript
onConnect(connection: ConnectionNativeInfo): void
```

建立连接时的回调函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebExtensionConnectionCallback-onConnect(connection: ConnectionNativeInfo): void--><!--Device-WebExtensionConnectionCallback-onConnect(connection: ConnectionNativeInfo): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | [ConnectionNativeInfo](../../apis-arkweb/arkts-apis/arkts-arkweb-webnativemessagingextensionmanager-connectionnativeinfo-i.md) | 是 | 连接信息，包含连接ID、扩展应用包名、浏览器扩展源URL和扩展进程ID等信息。 |

## onDisconnect

```TypeScript
onDisconnect(connection: ConnectionNativeInfo): void
```

断开连接时的回调函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebExtensionConnectionCallback-onDisconnect(connection: ConnectionNativeInfo): void--><!--Device-WebExtensionConnectionCallback-onDisconnect(connection: ConnectionNativeInfo): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | [ConnectionNativeInfo](../../apis-arkweb/arkts-apis/arkts-arkweb-webnativemessagingextensionmanager-connectionnativeinfo-i.md) | 是 | 连接信息，包含连接ID、扩展应用包名、浏览器扩展源URL和扩展进程ID等信息。 |

## onFailed

```TypeScript
onFailed(code: NmErrorCode, errMsg: string): void
```

连接失败时的回调函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebExtensionConnectionCallback-onFailed(code: NmErrorCode, errMsg: string): void--><!--Device-WebExtensionConnectionCallback-onFailed(code: NmErrorCode, errMsg: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | [NmErrorCode](../../apis-arkweb/arkts-apis/arkts-arkweb-webnativemessagingextensionmanager-nmerrorcode-e.md) | 是 | 错误码。 |
| errMsg | string | 是 | 错误码对应信息。 |

