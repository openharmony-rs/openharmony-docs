# SecurityLevel

当前网页的安全级别。

**起始版本：** 11

<!--Device-webview-enum SecurityLevel--><!--Device-webview-enum SecurityLevel-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

页面既不绝对安全，也不是不安全，即是中立。例如，部分scheme非http/https的URL。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityLevel-NONE = 0--><!--Device-SecurityLevel-NONE = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SECURE

```TypeScript
SECURE = 1
```

页面安全，页面使用的是HTTPS协议，且使用了信任的证书。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityLevel-SECURE = 1--><!--Device-SecurityLevel-SECURE = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## WARNING

```TypeScript
WARNING = 2
```

页面不安全。例如，使用HTTP协议或使用HTTPS协议但使用旧版TLS版本。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityLevel-WARNING = 2--><!--Device-SecurityLevel-WARNING = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DANGEROUS

```TypeScript
DANGEROUS = 3
```

尝试进行HTTPS连接但失败，认证未通过。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityLevel-DANGEROUS = 3--><!--Device-SecurityLevel-DANGEROUS = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

