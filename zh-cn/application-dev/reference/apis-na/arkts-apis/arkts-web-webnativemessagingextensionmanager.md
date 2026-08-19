# @ohos.web.webNativeMessagingExtensionManager

webNativeMessagingExtensionManager模块是ArkWeb提供的Web原生消息扩展管理模块，用于在应用侧（调用方）发起并管理到 [WebNativeMessagingExtensionAbility](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md)的连接。开发者可通过 [connectNative](../../apis-arkweb/arkts-apis/arkts-arkweb-webnativemessagingextensionmanager-connectnative-f.md)方法指定目标扩展Ability并建立连接，通过返回的连接ID与 [WebExtensionConnectionCallback](../../apis-arkweb/arkts-apis/arkts-arkweb-webnativemessagingextensionmanager-webextensionconnectioncallback-i.md)监听连接建立、断开及失败 事件，也可通过[disconnectNative](../../apis-arkweb/arkts-apis/arkts-arkweb-webnativemessagingextensionmanager-disconnectnative-f.md)主动释放连接。该模块适用于浏览器扩展与应用通信的场景；使用前需申请 ohos.permission.WEB_NATIVE_MESSAGING 权限，且仅在Stage模型下可用。 > **说明：**> > 本模块接口仅可在Stage模型下使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace webNativeMessagingExtensionManager--><!--Device-unnamed-declare namespace webNativeMessagingExtensionManager-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [connectNative](arkts-na-webnativemessagingextensionmanager-connectnative-f.md) | 将当前Ability连接到指定的Web原生消息扩展Ability。 |
| [disconnectNative](arkts-na-webnativemessagingextensionmanager-disconnectnative-f.md) | 断开指定Web原生消息扩展连接。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConnectionNativeInfo](arkts-na-webnativemessagingextensionmanager-connectionnativeinfo-i.md) | 表示Web原生消息连接的连接信息。 |
| [WebExtensionConnectionCallback](arkts-na-webnativemessagingextensionmanager-webextensionconnectioncallback-i.md) | 作为连接网络原生消息扩展时的输入参数，它用于接收连接期间的状态变化。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NmErrorCode](arkts-na-webnativemessagingextensionmanager-nmerrorcode-e.md) | Native Messaging的错误列表。 |

