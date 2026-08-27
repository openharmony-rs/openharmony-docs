# MixedMode

混合内容模式。

**起始版本：** 8

**系统能力：** SystemCapability.Web.Webview.Core

## All

```TypeScript
All = 0
```

宽松模式：允许加载HTTP和HTTPS混合内容。所有不安全的内容都可以被加载。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## Compatible

```TypeScript
Compatible = 1
```

兼容模式：允许部分HTTP内容在HTTPS页面中加载。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## None

```TypeScript
None = 2
```

严格模式：不允许加载HTTP和HTTPS混合内容。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
