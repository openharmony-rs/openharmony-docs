# OnGeolocationShowEvent

定义收到地理位置获取请求时触发的回调信息，包括源信息和地理对象。适用于需要处理地理位置权限的场景。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## geolocation

```TypeScript
geolocation: JsGeolocation
```

通知Web组件用户操作行为。

**类型：** [JsGeolocation](arkts-arkweb-jsgeolocation-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## origin

```TypeScript
origin: string
```

发起地理位置权限请求的网页源，用于标识特定网站的地理位置请求来源。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
