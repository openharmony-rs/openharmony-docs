# WebHttpCookieSameSitePolicy

控制cookie在跨站请求中的发送行为。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

允许在跨站请求中携带cookie，但必须同时设置secure属性。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## LAX

```TypeScript
LAX = 1
```

允许特定的跨站请求携带cookie，如某些get请求的导航场景。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## STRICT

```TypeScript
STRICT = 2
```

禁止在跨站请求中携带cookie。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core
