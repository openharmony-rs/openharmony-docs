# WebHttpCookie

cookie的相关字段。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## domain

```TypeScript
domain: string
```

指定哪些域名可以访问该cookie。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## expiresDate

```TypeScript
expiresDate: string
```

cookie的过期时间。时间格式详见[Date](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Reference/Headers/Date)。传入不符合该格式的时间字符串时，该cookie设置不生效。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## isHttpOnly

```TypeScript
isHttpOnly: boolean
```

标记该cookie是否只能通过HTTP请求访问。

true表示仅能通过HTTP访问，不能通过JavaScript访问，false表示可以通过JavaScript访问。

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## isSecure

```TypeScript
isSecure: boolean
```

标记该cookie是否只能通过HTTPS发送。

true表示仅能通过HTTPS发送，不能通过HTTP发送，false表示可以通过HTTP发送。

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## isSessionCookie

```TypeScript
isSessionCookie: boolean
```

标记该cookie是否是session cookie。

true表示是session cookie，false表示不是session cookie。

**类型：** boolean

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## name

```TypeScript
name: string
```

cookie的名称。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## path

```TypeScript
path: string
```

cookie的路径。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## samesitePolicy

```TypeScript
samesitePolicy: WebHttpCookieSameSitePolicy
```

cookie的同站策略。

**类型：** [WebHttpCookieSameSitePolicy](arkts-arkweb-webview-webhttpcookiesamesitepolicy-e.md)

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

## value

```TypeScript
value: string
```

cookie的值。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core
