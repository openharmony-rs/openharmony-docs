# CacheMode

Enum type supplied to {@link cacheMode} for setting the Web cache mode.

**起始版本：** 8

<!--Device-unnamed-declare enum CacheMode--><!--Device-unnamed-declare enum CacheMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## Default

```TypeScript
Default = 0
```

优先使用未过期cache加载资源，无效或无cache时从网络获取。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CacheMode-Default = 0--><!--Device-CacheMode-Default = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## None

```TypeScript
None = 1
```

优先使用cache（含过期）加载资源，无cache时从网络获取。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CacheMode-None = 1--><!--Device-CacheMode-None = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## Online

```TypeScript
Online = 2
```

强制从网络获取最新资源，不使用任何cache。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CacheMode-Online = 2--><!--Device-CacheMode-Online = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## Only

```TypeScript
Only = 3
```

仅使用本地cache加载资源。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CacheMode-Only = 3--><!--Device-CacheMode-Only = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

