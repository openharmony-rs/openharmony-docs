# OnViewportFitChangedCallback

```TypeScript
type OnViewportFitChangedCallback = (viewportFit: ViewportFit) => void
```

网页meta中viewport-fit配置项更改时触发的回调。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| viewportFit | ViewportFit | 是 | 网页meta中viewport-fit配置的视口类型。 |

