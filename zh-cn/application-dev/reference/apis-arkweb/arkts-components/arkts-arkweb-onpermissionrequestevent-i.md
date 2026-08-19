# OnPermissionRequestEvent

定义收到权限请求时触发的回调信息，包括请求详情。适用于需要处理权限授予的场景，提升权限管理的灵活性和安全性。

**起始版本：** 12

<!--Device-unnamed-declare interface OnPermissionRequestEvent--><!--Device-unnamed-declare interface OnPermissionRequestEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## request

```TypeScript
request: PermissionRequest
```

通知Web组件用户操作行为。

**类型：** [PermissionRequest](arkts-arkweb-permissionrequest-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnPermissionRequestEvent-request: PermissionRequest--><!--Device-OnPermissionRequestEvent-request: PermissionRequest-End-->

**系统能力：** SystemCapability.Web.Webview.Core

