# WebHttpCookieSameSitePolicy

Indicates whether to restrict cookies so that only requests sent back to the same site that created them can carry them.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-enum WebHttpCookieSameSitePolicy--><!--Device-webview-enum WebHttpCookieSameSitePolicy-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

Cookies marked as Secure are allowed to be carried in cross-site requests.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebHttpCookieSameSitePolicy-NONE = 0--><!--Device-WebHttpCookieSameSitePolicy-NONE = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## LAX

```TypeScript
LAX = 1
```

Allow specific cross-site requests to carry cookies.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebHttpCookieSameSitePolicy-LAX = 1--><!--Device-WebHttpCookieSameSitePolicy-LAX = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## STRICT

```TypeScript
STRICT = 2
```

Prohibit cross-site requests from carrying cookies.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebHttpCookieSameSitePolicy-STRICT = 2--><!--Device-WebHttpCookieSameSitePolicy-STRICT = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

