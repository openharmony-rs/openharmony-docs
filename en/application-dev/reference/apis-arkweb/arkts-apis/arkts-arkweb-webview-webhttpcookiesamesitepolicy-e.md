# WebHttpCookieSameSitePolicy

Enumerates the policies for sending cookies in cross-site requests.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

Cookies can be carried in cross-site requests, but the **secure** attribute must be set.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

## LAX

```TypeScript
LAX = 1
```

Cookies can be carried in specific cross-site requests, such as navigation scenarios of some GET requests.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

## STRICT

```TypeScript
STRICT = 2
```

Cookies cannot be carried in cross-site requests.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core
