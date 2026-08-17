# OnHttpAuthRequestEvent

定义收到HTTP认证请求时触发的回调信息，包括主机和域信息。适用于需要处理HTTP身份验证的场景，提升认证流程的灵活性和安全性。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare interface OnHttpAuthRequestEvent--><!--Device-unnamed-declare interface OnHttpAuthRequestEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: HttpAuthHandler
```

通知Web组件用户操作行为。

**类型：** [HttpAuthHandler](arkts-arkweb-httpauthhandler-c.md)

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnHttpAuthRequestEvent-handler: HttpAuthHandler--><!--Device-OnHttpAuthRequestEvent-handler: HttpAuthHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## host

```TypeScript
host: string
```

HTTP身份验证凭据应用的主机。

**类型：** string

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnHttpAuthRequestEvent-host: string--><!--Device-OnHttpAuthRequestEvent-host: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## realm

```TypeScript
realm: string
```

HTTP身份验证凭据应用的域。

**类型：** string

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnHttpAuthRequestEvent-realm: string--><!--Device-OnHttpAuthRequestEvent-realm: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

