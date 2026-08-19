# SecurityLevel

Defines the security level for the page.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-enum SecurityLevel--><!--Device-webview-enum SecurityLevel-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

Unable to determine whether it is safe or not, the non-http/https protocol used.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-SecurityLevel-NONE = 0--><!--Device-SecurityLevel-NONE = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SECURE

```TypeScript
SECURE = 1
```

Indicates the HTTPS protocol used by the page and the authentication is successful.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-SecurityLevel-SECURE = 1--><!--Device-SecurityLevel-SECURE = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## WARNING

```TypeScript
WARNING = 2
```

The page is insecure. For example, the HTTP protocol is used or the HTTPS protocol is used but use an legacy TLS version.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-SecurityLevel-WARNING = 2--><!--Device-SecurityLevel-WARNING = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DANGEROUS

```TypeScript
DANGEROUS = 3
```

Attempted HTTPS and failed, the authentication is failed.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-SecurityLevel-DANGEROUS = 3--><!--Device-SecurityLevel-DANGEROUS = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

