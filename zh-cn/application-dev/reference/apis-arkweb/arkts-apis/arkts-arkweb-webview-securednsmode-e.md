# SecureDnsMode

Web组件使用HTTPDNS的模式。

**起始版本：** 10

**系统能力：** SystemCapability.Web.Webview.Core

## OFF

```TypeScript
OFF = 0
```

不使用HTTPDNS，可以用于撤销之前使用的HTTPDNS配置。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## AUTO

```TypeScript
AUTO = 1
```

自动模式，用于解析的设定DNS服务器不可用时，可自动回落至系统DNS。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## SECURE_ONLY

```TypeScript
SECURE_ONLY = 2
```

强制使用设定的HTTPDNS服务器进行域名解析。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
