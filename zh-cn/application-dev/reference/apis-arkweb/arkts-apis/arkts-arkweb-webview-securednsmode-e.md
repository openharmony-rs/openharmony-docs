# SecureDnsMode

Web组件使用HTTPDNS的模式。

**起始版本：** 10

<!--Device-webview-enum SecureDnsMode--><!--Device-webview-enum SecureDnsMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## OFF

```TypeScript
OFF = 0
```

不使用HTTPDNS， 可以用于撤销之前使用的HTTPDNS配置。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecureDnsMode-OFF = 0--><!--Device-SecureDnsMode-OFF = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## AUTO

```TypeScript
AUTO = 1
```

自动模式，HttpDns的用户设置用于DNS解析，若解析失败，则使用系统DNS进行解析。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecureDnsMode-AUTO = 1--><!--Device-SecureDnsMode-AUTO = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SECURE_ONLY

```TypeScript
SECURE_ONLY = 2
```

强制使用设定的HTTPDNS服务器进行域名解析。如果解析失败，将不会回退到系统 DNS，这将直接导致页面加载失败。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecureDnsMode-SECURE_ONLY = 2--><!--Device-SecureDnsMode-SECURE_ONLY = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

