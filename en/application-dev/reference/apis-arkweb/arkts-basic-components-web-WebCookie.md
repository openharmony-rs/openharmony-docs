# Class (WebCookie)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @xuefuzhang-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5191f5de3eca0919d8d5e44823dbef1bf6b74270 translatedAt=2026-11-04T11:33:50.776Z pushedAt=2026-11-04T11:50:24.540Z nl=1 -->

Manages behavior of cookies in **Web** components. All **Web** components in an application share a **WebCookie**. You can use the **getCookieManager** API in **controller** to obtain the **WebCookie** for subsequent cookie management.

> **NOTE**
>
> - This component is supported since API version 8. For new content in later versions, the version at which the content is introduced is marked separately with a superscript.
>
> - This class is supported since API version 8.
>
> - This API is supported since API version 8 and no longer maintained since API version 23. You are advised to use [WebCookieManager](./arkts-apis-webview-WebCookieManager.md) instead.
>
> - The sample effect is subject to the actual running on a real device.

## constructor<sup>(deprecated)</sup>

constructor()

Constructs a **WebCookie** object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 23. No API is provided for substitute.

**System capability**: SystemCapability.Web.Webview.Core

## setCookie<sup>(deprecated)</sup>

setCookie()

Sets the cookie. This API returns the result synchronously. **true** is returned if the operation is successful; otherwise, **false** is returned.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [setCookie](./arkts-apis-webview-WebCookieManager.md#setcookiedeprecated) instead.

**System capability**: SystemCapability.Web.Webview.Core

## saveCookie<sup>(deprecated)</sup>

saveCookie()

Saves the cookies in the memory to the drive. This API returns the result synchronously.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [saveCookieAsync<sup>9+</sup>](./arkts-apis-webview-WebCookieManager.md#savecookieasync) instead.

**System capability**: SystemCapability.Web.Webview.Core