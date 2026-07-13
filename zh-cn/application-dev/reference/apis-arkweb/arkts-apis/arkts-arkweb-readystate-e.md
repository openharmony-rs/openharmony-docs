# ReadyState

播放器的缓存状态。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## HAVE_NOTHING

```TypeScript
HAVE_NOTHING = 0
```

没有缓存。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## HAVE_METADATA

```TypeScript
HAVE_METADATA = 1
```

只缓存了媒体元数据。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## HAVE_CURRENT_DATA

```TypeScript
HAVE_CURRENT_DATA = 2
```

只缓存到当前的播放进度。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## HAVE_FUTURE_DATA

```TypeScript
HAVE_FUTURE_DATA = 3
```

缓存时长超过了当前的播放进度, 但是仍有可能导致卡顿。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## HAVE_ENOUGH_DATA

```TypeScript
HAVE_ENOUGH_DATA = 4
```

缓存了足够的数据，保证播放流畅。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

