# OnHttpAuthRequestEvent

定义通知收到http auth认证请求。

**起始版本：** 12

<!--Device-unnamed-declare interface OnHttpAuthRequestEvent--><!--Device-unnamed-declare interface OnHttpAuthRequestEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: HttpAuthHandler
```

通知Web组件用户操作行为。

**类型：** HttpAuthHandler

**起始版本：** 12

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnHttpAuthRequestEvent-realm: string--><!--Device-OnHttpAuthRequestEvent-realm: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

