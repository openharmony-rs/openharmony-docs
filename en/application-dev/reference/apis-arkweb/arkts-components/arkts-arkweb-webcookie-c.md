# WebCookie

Manages behavior of cookies in **Web** components. All **Web** components in an application share a **WebCookie**. You can use the **getCookieManager** API in **controller** to obtain the **WebCookie** for subsequent cookie management.

**Since:** 8

**Deprecated since:** 23

**Substitutes:** [WebCookieManager](../arkts-apis/arkts-arkweb-webview-webcookiemanager-c.md)

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **WebCookie** object.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 23. No API is provided for substitute.

**Since:** 8

**Deprecated since:** 23

**Substitutes:** [WebCookieManager](../arkts-apis/arkts-arkweb-webview-webcookiemanager-c.md)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## saveCookie

```TypeScript
saveCookie()
```

Saves the cookies in the memory to the drive. This API returns the result synchronously.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [saveCookieAsync](../arkts-apis/arkts-arkweb-webview-webcookiemanager-c.md#savecookieasync)

**System capability:** SystemCapability.Web.Webview.Core

## setCookie

```TypeScript
setCookie()
```

Sets the cookie. This API returns the result synchronously. **true** is returned if the operation is successful; otherwise, **false** is returned.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** setCookie

**System capability:** SystemCapability.Web.Webview.Core
