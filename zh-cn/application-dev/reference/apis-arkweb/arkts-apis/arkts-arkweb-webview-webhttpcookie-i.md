# WebHttpCookie

Defines the Web's HTTPCookie.<p><strong>API Note</strong>:<br>The maximum length allowed for each attribute value in a cookie string is 1024.</p>

**起始版本：** 23

<!--Device-webview-interface WebHttpCookie--><!--Device-webview-interface WebHttpCookie-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## domain

```TypeScript
domain: string
```

获取cookie的域名

**类型：** string

**起始版本：** 23

<!--Device-WebHttpCookie-domain: string--><!--Device-WebHttpCookie-domain: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## expiresDate

```TypeScript
expiresDate: string
```

获取cookie的失效日期

**类型：** string

**起始版本：** 23

<!--Device-WebHttpCookie-expiresDate: string--><!--Device-WebHttpCookie-expiresDate: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isHttpOnly

```TypeScript
isHttpOnly: boolean
```

获取当前cookie是否被标记了HttpOnly

**类型：** boolean

**起始版本：** 23

<!--Device-WebHttpCookie-isHttpOnly: boolean--><!--Device-WebHttpCookie-isHttpOnly: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isSecure

```TypeScript
isSecure: boolean
```

获取当前cookie是否是secure cookie

**类型：** boolean

**起始版本：** 23

<!--Device-WebHttpCookie-isSecure: boolean--><!--Device-WebHttpCookie-isSecure: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isSessionCookie

```TypeScript
isSessionCookie: boolean
```

获取是否是session cookie

**类型：** boolean

**起始版本：** 23

<!--Device-WebHttpCookie-isSessionCookie: boolean--><!--Device-WebHttpCookie-isSessionCookie: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## name

```TypeScript
name: string
```

获取cookie的name

**类型：** string

**起始版本：** 23

<!--Device-WebHttpCookie-name: string--><!--Device-WebHttpCookie-name: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## path

```TypeScript
path: string
```

获取cookie的path

**类型：** string

**起始版本：** 23

<!--Device-WebHttpCookie-path: string--><!--Device-WebHttpCookie-path: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## samesitePolicy

```TypeScript
samesitePolicy: WebHttpCookieSameSitePolicy
```

获取当前cookie的samesite策略

**类型：** WebHttpCookieSameSitePolicy

**起始版本：** 23

<!--Device-WebHttpCookie-samesitePolicy: WebHttpCookieSameSitePolicy--><!--Device-WebHttpCookie-samesitePolicy: WebHttpCookieSameSitePolicy-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## value

```TypeScript
value: string
```

获取cookie的value

**类型：** string

**起始版本：** 23

<!--Device-WebHttpCookie-value: string--><!--Device-WebHttpCookie-value: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

