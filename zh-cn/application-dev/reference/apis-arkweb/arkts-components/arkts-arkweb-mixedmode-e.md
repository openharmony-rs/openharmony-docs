# MixedMode

混合内容模式。默认设置为 MixedMode.None。

**起始版本：** 8

**系统能力：** SystemCapability.Web.Webview.Core

## All

```TypeScript
All = 0
```

宽松模式：允许加载HTTP和HTTPS混合内容。所有不安全的内容都可以被加载。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## Compatible

```TypeScript
Compatible = 1
```

兼容模式：混合内容兼容性模式，部分不安全的内容可能被加载。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## None

```TypeScript
None = 2
```

严格模式：不允许加载HTTP和HTTPS混合内容。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

