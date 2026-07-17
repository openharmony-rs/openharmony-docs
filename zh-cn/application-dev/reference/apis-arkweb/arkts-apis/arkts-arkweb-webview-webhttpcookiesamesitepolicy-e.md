# WebHttpCookieSameSitePolicy

指示是否将 cookie 限制为仅创建它的同一站点的请求可以携带。指示是否将 cookie 限制为仅创建它的同一站点的请求可以携带。

**起始版本：** 23

<!--Device-webview-enum WebHttpCookieSameSitePolicy--><!--Device-webview-enum WebHttpCookieSameSitePolicy-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

允许在跨站请求中携带cookie，但必须同时设置secure属性。

**起始版本：** 23

<!--Device-WebHttpCookieSameSitePolicy-NONE = 0--><!--Device-WebHttpCookieSameSitePolicy-NONE = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## LAX

```TypeScript
LAX = 1
```

允许特定的跨站请求携带cookie。

**起始版本：** 23

<!--Device-WebHttpCookieSameSitePolicy-LAX = 1--><!--Device-WebHttpCookieSameSitePolicy-LAX = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## STRICT

```TypeScript
STRICT = 2
```

禁止在跨站请求中携带cookie。

**起始版本：** 23

<!--Device-WebHttpCookieSameSitePolicy-STRICT = 2--><!--Device-WebHttpCookieSameSitePolicy-STRICT = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

