# SecureDnsMode

Defines the mode for using HttpDns.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-webview-enum SecureDnsMode--><!--Device-webview-enum SecureDnsMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## OFF

```TypeScript
OFF = 0
```

Do not use HttpDns, can be used to revoke previously used HttpDns configuration.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SecureDnsMode-OFF = 0--><!--Device-SecureDnsMode-OFF = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## AUTO

```TypeScript
AUTO = 1
```

By default, the user-settings of HttpDns is used for dns resolution, and if it fails, the system dns is used for resolution.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SecureDnsMode-AUTO = 1--><!--Device-SecureDnsMode-AUTO = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SECURE_ONLY

```TypeScript
SECURE_ONLY = 2
```

Use the user-settings of HttpDns for dns resolution. If it fails, it will not fall back to the system dns, which will directly cause the page to fail to load.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SecureDnsMode-SECURE_ONLY = 2--><!--Device-SecureDnsMode-SECURE_ONLY = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

