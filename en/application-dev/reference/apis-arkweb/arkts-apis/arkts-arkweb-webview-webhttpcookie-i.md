# WebHttpCookie

```TypeScript
interface WebHttpCookie
```

Defines cookie-related fields.

**Since:** 23

<!--Device-webview-interface WebHttpCookie--><!--Device-webview-interface WebHttpCookie-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## domain

```TypeScript
domain: string
```

Domain names that can access the cookie.

**Type:** string

**Since:** 23

<!--Device-WebHttpCookie-domain: string--><!--Device-WebHttpCookie-domain: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## expiresDate

```TypeScript
expiresDate: string
```

Expiration time of the cookie. For details about the time format, see [Date](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Date). If the time string passed in does not conform to this format, the cookie setting does not take effect.

**Type:** string

**Since:** 23

<!--Device-WebHttpCookie-expiresDate: string--><!--Device-WebHttpCookie-expiresDate: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## isHttpOnly

```TypeScript
isHttpOnly: boolean
```

Whether the cookie can be accessed only through HTTP requests.

The value **true** means the cookie can be accessed only through HTTP, not through JavaScript; **false** means the cookie can be accessed through JavaScript.

**Type:** boolean

**Since:** 23

<!--Device-WebHttpCookie-isHttpOnly: boolean--><!--Device-WebHttpCookie-isHttpOnly: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## isSecure

```TypeScript
isSecure: boolean
```

Whether the cookie can be sent only through HTTPS.

The value **true** means the cookie can be sent only through HTTPS, not through HTTP; **false** means the cookie can be sent through HTTP.

**Type:** boolean

**Since:** 23

<!--Device-WebHttpCookie-isSecure: boolean--><!--Device-WebHttpCookie-isSecure: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## isSessionCookie

```TypeScript
isSessionCookie: boolean
```

Whether the cookie is a session cookie.

The value **true** indicates that the cookie is a session cookie, and **false** indicates the opposite.

**Type:** boolean

**Since:** 23

<!--Device-WebHttpCookie-isSessionCookie: boolean--><!--Device-WebHttpCookie-isSessionCookie: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## name

```TypeScript
name: string
```

Name of the cookie.

**Type:** string

**Since:** 23

<!--Device-WebHttpCookie-name: string--><!--Device-WebHttpCookie-name: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## path

```TypeScript
path: string
```

Path of the cookie.

**Type:** string

**Since:** 23

<!--Device-WebHttpCookie-path: string--><!--Device-WebHttpCookie-path: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## samesitePolicy

```TypeScript
samesitePolicy: WebHttpCookieSameSitePolicy
```

Same-site policy of the cookie.

**Type:** [WebHttpCookieSameSitePolicy](arkts-arkweb-webview-webhttpcookiesamesitepolicy-e.md)

**Since:** 23

<!--Device-WebHttpCookie-samesitePolicy: WebHttpCookieSameSitePolicy--><!--Device-WebHttpCookie-samesitePolicy: WebHttpCookieSameSitePolicy-End-->

**System capability:** SystemCapability.Web.Webview.Core

## value

```TypeScript
value: string
```

Value of the cookie.

**Type:** string

**Since:** 23

<!--Device-WebHttpCookie-value: string--><!--Device-WebHttpCookie-value: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
