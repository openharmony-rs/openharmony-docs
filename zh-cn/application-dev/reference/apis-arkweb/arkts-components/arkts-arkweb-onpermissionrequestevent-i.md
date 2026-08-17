# OnPermissionRequestEvent

定义收到权限请求时触发的回调信息，包括请求详情。适用于需要处理权限授予的场景，提升权限管理的灵活性和安全性。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare interface OnPermissionRequestEvent--><!--Device-unnamed-declare interface OnPermissionRequestEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## request

```TypeScript
request: PermissionRequest
```

通知Web组件用户操作行为。

**类型：** [PermissionRequest](arkts-arkweb-permissionrequest-c.md)

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnPermissionRequestEvent-request: PermissionRequest--><!--Device-OnPermissionRequestEvent-request: PermissionRequest-End-->

**系统能力：** SystemCapability.Web.Webview.Core

