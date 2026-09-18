# @ohos.web.WebNativeMessagingExtensionAbility

WebNativeMessagingExtensionAbility is a base class for web native message communication extension provided by ArkWeb,
 inherited from ExtensionAbility. It allows web pages to establish a secure, bidirectional pipe communication channel
 with system native services through the Native Messaging mechanism. By inheriting this class and implementing its
 lifecycle callbacks (such as [onConnectNative](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md#onconnectnative),
 [onDisconnectNative](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md#ondisconnectnative), and
 [onDestroy](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md#ondestroy)), developers can detect connection establishment when
 a web page initiates a connection request, obtain the caller identity and bidirectional pipe file descriptors (see
 [ConnectionInfo](arkts-arkweb-web-webnativemessagingextensionability-connectioninfo-i.md)), and release resources when the connection is disconnected or the extension
 is destroyed. This capability is primarily used in scenarios where browser extensions communicate with apps, enabling
 efficient message passing and data exchange to enhance extension integration and functionality. The app side must
 manage pipe read/write operations, permission verification, and the Ability lifecycle on its own.



## Modules to Import

```TypeScript
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [WebNativeMessagingExtensionAbility](arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md) | Provides the web native messaging capability and is inherited from ExtensionAbility. |

### Interfaces

| Name | Description |
| --- | --- |
| [ConnectionInfo](arkts-arkweb-web-webnativemessagingextensionability-connectioninfo-i.md) | Represents the information object of the web native messaging connection. |
